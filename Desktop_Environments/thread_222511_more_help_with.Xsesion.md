---
title: "more help with/.Xsesion"
date: 2006-07-25
forum: Desktop Environments
---

### Post by LORD_PoLvO on 2006-07-25
hiya i have go xgl installed and have tpo makje this file so that it runs or w/e and i have done this


daniel@daniel-desktop:~$ sudo gedit /home/daniel/.Xsession



the file i made looks like this


#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &.
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME 
exec gnome-session




now i havenmt saved or closed the file yet because i have one more question to ask i have to make the file so its +x'd/executable with chmod +x ~/.Xsession.



how i do this??

---

### Post by ardchoille on 2006-07-25
The proper way to make a file executable is with:

```

chmod u+x /path/filename

```
The "u" means user. u = user, g = group, o=other
However, if you created that file with sudo, you'll need to use sudo to chmod it.

---

### Post by philippe_carlo on 2006-07-25
Note also, that you should not edit the file as superuser. X will not start if the file turns out to be owned by root an not thus readable.

---

### Post by LORD_PoLvO on 2006-07-25
its still confusing so what do i actually have to do ??

---

### Post by ardchoille on 2006-07-25
Which part of "chmod u+x /path/filename" did you not understand? I'd be happy to help if you can explain which part you didn't understand :)

---

### Post by LORD_PoLvO on 2006-07-25
well the tutuorial says 

"Now make sure it's +x'd/executable with chmod +x ~/.Xsession."


and i dont knwo how i am mean tto do this??

is it simply

chmod u+x /home/daniel/.Xsession



??

---

### Post by ardchoille on 2006-07-25
Yes. chmod u+x /home/daniel/.Xsession  will do it.

If you get a permission denied error, it may be that you created that file using sudo. You can do:

```

ls -lha /home/daniel/.Xsession

```
to see some info about the file, including who owns that file. If root owns the file, you need to do:

```

sudo chown daniel:daniel /home/daniel/.Xsession

```

to change the ownerships back to you, then:

```

chmod u+x /home/daniel/.Xsession

```
to make it executable.

---

### Post by LORD_PoLvO on 2006-07-25
root@daniel-desktop:/home/daniel# chmod u+x /home/daniel/.Xsession
root@daniel-desktop:/home/daniel#



OMG TY SO MUCH youve been a great help im glad that there are ppl like you who can help ppl to learn to use this great os thnx so much uve been gr8 help :)

---

### Post by ardchoille on 2006-07-25
You're very welcome :) I learned most of my Linux skills from the great folks at ubuntuforums.org

---

### Post by LORD_PoLvO on 2006-07-25
umm i need help again 



it didnt work i restrted x and went to log in i got an erro rsaying something like the sesion only lasted less than 10 seconds and that there is a problem with some install ??? i had to log in as failsafe gnome so it didnt load xsession


can u plz help lol??

---

### Post by ardchoille on 2006-07-25
Are you logging in via gdm (graphical login screen)? If so, I don't think you need "exec gnome-session" in your ~/.Xsession file since gdm will start gnome anyway. Try removing "exec gnome-session" from that file and log in again. And I think it should be DISPLAY=:0 instead of DISPLAY=:1 but I could be wrong about this because I don't use XGL.

---

### Post by LORD_PoLvO on 2006-07-25
ok ty disregard mi pm lol i didnt see there was 2 pages :0 lol ty ill try that now :)

---

### Post by LORD_PoLvO on 2006-07-25
fraggle it ... kk that didnt owrk so im back in failsafe gnome lol


well i managed to find out what the error is but buggered if i know how to fix it lol the output says that 

/home/daniel/xsession

line 4 filename argument required

usage filename [arguments]


this is my xsession atm



#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &.
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:0
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME

---

### Post by ardchoille on 2006-07-25
Sounds like you need the full path to XGL.. I'm not sure what the pathis but something like /path/to/XGL or some such.

So, instead of [COLOR="Red"]Xgl :1 -fullscreen -ac -accel xv:fdo -accel glxbuffer &.[/COLOR]  you need [COLOR="Red"]/path/to/Xgl :1 -fullscreen -ac -accel xv:fdo -accel glxbuffer &[/COLOR] (make sure those options are correct since the forums created a smiley somewhere in there)  and remove the "." at the end of that line also. You might need the full path to compiz in line 9 also.

---

### Post by ardchoille on 2006-07-25
Have you tried getting XGL/Compiz help in the #ubuntu channel on the freenode IRC network? There are a lot of folks in there who use XGL/Compiz. I hear there is a #xgl chat channel on that network as well.

---

### Post by LORD_PoLvO on 2006-07-25
ah that i dont knwo the paths i used apt-get install to get xgl etc umm i used the command 


apt-get install xserver-xgl compiz gnome-compiz

dunno where the patsh would be then i dont really know much where they go after that




so mi xsession should look like this??




#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
path/to/Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:0
# Start Compiz window manager
gnome-window-decorator &
path/tocompiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME

---

