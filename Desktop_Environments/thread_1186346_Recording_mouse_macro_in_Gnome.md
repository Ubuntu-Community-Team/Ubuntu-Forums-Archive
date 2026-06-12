---
title: "Recording mouse macro in Gnome"
date: 2009-06-13
forum: Desktop Environments
---

### Post by Carmageddon on 2009-06-13
Hi, I am trying to record a series of keystrokes, to create a macro that would allow me to automatically open a bookmark, fill the login  details, then go and do few more things etc.

The idea is, to login into my VMware 2.0 server, then open the windows VM running on another computer from this old laptop, to open things that run really badly or not at all using Linux (such as special sites that only work on IE, or power point presentations that dont open in Open Office).
The user is my mom, for whom loggin into the VM is too complex as well.

I have attempted to use xmacro, using those instructions:
[http://ubuntuforums.org/showthread.php?t=108129](http://ubuntuforums.org/showthread.php?t=108129)

However it doesnt work.. I tried the recommended escape as exit trigger, and another button as well, all I get is this:

```
user@lappy:~$ xmacrorec2 > VMware.macro.txt
Server VendorRelease: 10600000
XRecord for server ":0.0" is version 1.13.


Press the key you want to use to end the application. This key can be any key, 
as long as you don't need it while working with the remote display.
A good choice is Escape.

The chosen quit-key has the keycode: 49
XQueryPointer returned: 1
Got Start Of Data
Skipping...
`````````^C
user@lappy:~$ 

```

I of course tried to record the procedure and break recording, it did nothing, and I had to use ctrl-c to stop the terminal... the Skipping thing shows up as soon as I chose the preferred break key.. so I duno, perhaps I do something wrong? or someone has another idea on how to do it?

I wouldn't mind using a shell script for all of the above automation, if I knew how to do that.. and really mouse macro is fastest way to be honest, I hope we can make it work guys!




Thanks! :popcorn:

---

### Post by PGScooter on 2009-07-25
Hi Carmageddon,

xmacrorec2 seems to be broken in Jaunty. I had the same problem as you. No one seems to be trying to fix it.

You should be able to theoretically write out the script just by looking at other xmacrorec2 scripts because xmacroplay still seems to be working so it could read the instructions just fine. But that would be annoying.

You could also try gnee, but I did not have success with it.

Best of luck and post here if you find a solution

---

