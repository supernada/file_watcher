# file_watcher
This program has the sole objective of copying a specific file from a folder to another folder - but this file appears randomly and needs to keep being watched - 
if it appears, it makes a copy and rename the original so it doesn't messes up the next files

The folder is a fixed name so you can't define it - but you can change the server number - well you can change the code - but I mean the program itself as intended
config.txt must have a number to proceed

Context:
It was created to solve an inconvenient problem. Basically, there's a system responsible for communicating with all equipments to update the store prices. Let's call  it BGM8 But sometimes, it wasn't updating.
The file it imports is generated on a mapped folder - and sometimes this BGM8 wouldn't catch the file. Something on the server is creating .bak versions of this file and the BGM8 wouldn't import the prices

I sent a report to the higher IT support, they just said it's normal. I didn't get any real - which was frustrating. Then I decided to try to bring a solution - remove this file ASAP from 
that mapped folder so it wouldn't be affected by any means. The BGM8 would be redirected to import from the local folder C:\watcher.

It also has an option the input the server number because it can be shared/used by many other servers with the same input.

That's where this all started - and officially my first real Rust project. I needed it to be quick, reliable and safe. I didn't know these words were costy, though. The code is getting much
longer whan I would actually expect.

How it works:

First it checks if there's another instance running on Windows -
if it's already running, a pop-up message returns informing the system is already running - it would be a mess to have more than one watcher. 

It checks for the server number on config.txt if it's a number, it returns error on logs if it's not. (WIP - Still working on it - sometimes it doesn't call the error and I don't know why.)
It checks if the folder is really a folder/directory

All set, it calls the watcher. If it identifies the file on folder, it already makes the copy and change the original to .bak extension

then it keeps watching undefinitely as it should
Any problem with the copy it returns info on logs

The logs register the time it happened based on local time

Basically that's all - and I wouldn't really expect this complexity. But it works, and is already running at production. 
