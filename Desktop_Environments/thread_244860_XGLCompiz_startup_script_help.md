---
title: "XGL/Compiz startup script help"
date: 2006-08-27
forum: Desktop Environments
---

### Post by summersab on 2006-08-27
I'm a novice Linux user - I know enough to get myself into trouble.

I have so far followed 2 tutorials on XGL/Compiz and previously have had success with each. One is found at 
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916) (my preferred method)
and the other at
[http://www.ubuntuforums.org/showthread.php?t=219336](http://www.ubuntuforums.org/showthread.php?t=219336) (my alternate method)

Each method has worked for me before on other computers, including this one with an x600 ATI Radeon. However, after a clean install, I cannot get either method to work. I have tinkered with each method and rearranged the execution order of the operations. I have even added the startup files (whether it be startxgl.sh, startcompiz, or .Xsession) to my /usr/share/xsessions/gnome.desktop and xgl.desktop files. No luck.

Here is what I have gotten to work. Using the second method, I can get XGL to come up fine - blue screen and checkerd pattern and all. Then, I have to manually execute startcompiz from the shell. That is pretty sucky. What I would prefer would be have startcompiz execute as gnome loads - let the Gnome splash wobble and all. I tried putting Exec=/ . . . /startcompiz in my /usr/. . . /gnome.desktop and xgl.desktop files, but it doesn't start. I tried putting exec startcompiz in the startxgl.sh file. No luck. Yes, I have chmod +x'd the files.

Basically, I have these questions - how do I run a command (whether startcompiz or any other bash command, such as xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server") at startup by adding a line to a startup script?

As in the first method (which calls for the creation of ~/.Xsession), do files in /home/username run automatically on startup?

Please - advanced user gods and godesses - I implore you! Help me!

---

### Post by BitTorrentBuddha on 2006-08-27
To run a command at startup (in GNOME) add it to "Startup Programs" tab under System -> Preferences -> Sessions.

---

### Post by summersab on 2006-08-27
Yes, I know how to do that. That's GUI related, though. I want to add a line to a startup script. Something potentially more permanent and concrete. Nothing that a friend whose computer I set up could delete. That is what I want to do. I want a *.sh file that executes as gnome logs in that starts up compiz.

---

