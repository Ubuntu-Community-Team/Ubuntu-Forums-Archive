---
title: "Strange problem with Eternal Lands"
date: 2005-05-11
forum: Gaming &amp; Leisure
---

### Post by AndyAWS on 2005-05-11
This is probably something simple but being a Linux Newbie I don't know what's up.

I installed Eternal Lands in /usr/local/share/games/el/.

I can run the game only if I navigate to that directory and type "**./**el.x86.linux.bin"
If I leave off the "**./**" I get 'command not found'. If I try to add it to the menu (with Smeg) using "/usr/local/shar/el/el.x86.linux.bin" as the Command, nothing happens.

I had to make a Bash Script that "cd"s to the directory and runs "**./**el.x86.linux.bin".

my question is: Why do i need the leading **./** to run the file. The file permissions are set to 775, and if I check it's properties it says MIME Type: application/x-executable.

If I double click it from the file browser I get an error:

> Cannot open el.x86.linux.bin

The filename "el.x86.linux.bin" indicates that this file is of type "unknown". The contents of the file indicate that the file is of type "executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 


If I change the filename to el.x86.linux.exe it works...but this seems a bit windowsish...Is there another proper way to fix it?

---

### Post by AndyAWS on 2005-05-12
Can a linux guru just tell me how I can run the executable without the leading **./**, or tell me why it's needed for some executables but not others.

Sorry to sound like a nag but it seems like something someone here would be able answer.

---

### Post by AndyAWS on 2005-05-12
Never mind - I found the answer elsewhere...if a file is not in the system's 'Path' then you must navigate to the directory and run it with ./ (since even the 'current directory' is not considered to be in the 'path' (unlike DOS). 

So my question is: Is there a way to create a menu entry to such a program?

---

### Post by T. G. Cid on 2005-05-14
> 
I had to make a Bash Script that "cd"s to the directory and runs "./el.x86.linux.bin".


Move the script to /usr/bin.  Some games (i.e. Enemy Territory) drop a script into /usr/bin to launch themselves if they have this problem, not sure why Eternal Lands didn't.

---

