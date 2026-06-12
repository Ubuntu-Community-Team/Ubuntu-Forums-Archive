---
title: "Unreal Tournament 2004 linux-installer.sh error"
date: 2006-06-03
forum: Gaming &amp; Leisure
---

### Post by truenemesis on 2006-06-03
when I mount the installer cd, and then i do this command
cd /media/cdrom0
./linux-installer.sh

i get this message.

bash: ./linux-installer.sh: /bin/sh: bad interpreter: Permission denied

can someone help me? I would like to play UT 2004 again woon.

---

### Post by jgoguen on 2006-06-03
I had this problem too.  Run instead:
```
sudo sh ./linux-installer.sh
```

---

### Post by Rosenrot on 2006-06-21
i have the same error but i try the code jgoguen posted and i just get

sh: ./linux-installer.sh: No such file or directory



im a newbie and just barely installed linux yesterday with no prior linux use.

could anyone help me please?

---

### Post by Perfect Storm on 2006-06-21
Open the CD (so you can see the files).

Open the terminal and write:
```
sudo sh 
```
and drag the **linux-installer.sh** into ther terminal.

When installed **Don't hit the play button**. But exit it. Then write **ut2004** in the terminal to start it. If you the start button after installing it with adminstration enable, you'll face permission problems.

---

### Post by Rosenrot on 2006-06-21
i tried that and i got

b@b-desktop:~$ sudo sh
sh-3.1# /home/b/Desktop/linux-installer.sh
sh: /home/b/Desktop/linux-installer.sh: Permission denied
sh-3.1#


i don't understand what is going wrong

---

### Post by Perfect Storm on 2006-06-21
close the terminal and start a new one up, then:

```
sudo sh /home/b/Desktop/linux-installer.sh
```

---

### Post by handy on 2006-06-21
I could be missing stuff because I didn't really read the thread.

When I installed UT2k4, I just copied the ***Linux-installer.sh*** file on to the desktop, & ran it from there.  After that the UT2k4 disks were in control.

---

### Post by Rosenrot on 2006-06-21
thank you it works now

---

### Post by Rosenrot on 2006-06-21
i tried just copieing linux-installer.sh to the desktop and running it but terminal kept giving me errors : /

i know how to use comand prompt in windows but im new to the linux file system and had no idea where to start lol

---

### Post by Rosenrot on 2006-06-21
after i installed i didn't  press 'play now' and then i exited from terminal
from there i went to applications>other>UT2004

after that all i got was a splash screen for about a second and it disappeared
i tried it numerous times


then i tried many commands in terminal to try to start ut2004

the only command i did that gave me more than 'directory or file not found' was
this

...

b@b-desktop:~$ sudo /usr/local/games/ut2004/ut2004
open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error

...

im guessing the error took place at the splash screen but i don't understand how exactly to fix the error

---

### Post by Perfect Storm on 2006-06-21
Looks like you havn't installed the Driver for your graphic card.

---

### Post by Rosenrot on 2006-06-21
I installed my video card driver and now im getting this

...

b@b-desktop:~$ sudo /usr/local/games/ut2004/ut2004
Password:
WARNING: ALC_EXT_capture is subject to change!


](*,)

---

### Post by Perfect Storm on 2006-06-21
It's because you start ut2004 up as adminstrator (sudo). A simple:
```
ut2004
```

is all what you need :)

sudo = superuser do

---

### Post by Rosenrot on 2006-06-21
well now i scrwed up X server by trying to install my driver again
and to test X server I pressed: Ctrl+Alt+Backspace
which brought me to a black scrren followed by a screen with screwed up fuzzy colors

so i restarted my computer

and

all i have is command prompt

and 

i get the error 
...
Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

<Yes>    <No>
...

i select yes and i get this underneath system version build date etc.

...

(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 21 15:28:04 2006
(==) Using config file: '/etc/X11/xorg.conf'
(WW) NVIDIA: No matching Device section for instance (BusID PCI:2:0:0)
found
(EE) No devices detected.

Fatal server error:
no screens found

...


](*,)  ](*,)  ](*,) 



if i knew the solution to my problem was so simple i wouldn't of tried to do that -_-

---

### Post by Rosenrot on 2006-06-21
also

after i get those x server errors

I get the messege

The X server is now disabled.  Restart GDM when it is configured correctly

and i also still have a fully functional command prompt

i just don't know how to configure x server

---

### Post by Perfect Storm on 2006-06-21
Do you have command line availble? If not boot ubuntu into failsafe then:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Rosenrot on 2006-06-21
i have command line available and ill try the code

---

### Post by Rosenrot on 2006-06-21
i used your code and ive gotten to the point where its asking for my video card's bus identifier

im not sure whether to just accept it as being

PCI:2:0:0

or not because im not sure what it is on my system

idk if there is a code i need to find that aswell

---

### Post by Rosenrot on 2006-06-21
i just left my video card port at 2:0:0

now im at the point where it asks me

"select the X.Org server modulees that should be loaded by default."

[x] bitmap
[ ] dbe
[x] ddc
[x] dri
[x] extmod
[x] freetype
[x] glx
[x] int10
[ ] record
[x] type 1
[ ] v41
[x] vbe

*the boxes with x's are what was selected by default once i got to this screen
but im unsure which ones should be selected

---

### Post by Perfect Storm on 2006-06-21
Which card do you have?

Edit: ahh a nvidia card I see. Just continue till it ask for card driver.

---

### Post by Perfect Storm on 2006-06-21
Must of it, it remember for the last xorg.conf so must of it is okay. The thing you might change is card driver to nvidia.

---

### Post by Rosenrot on 2006-06-21
ok i finished reconfiguring

i restarted the system and it booted up correctly

AND

i had the Nvidia splash screen appear as its sopposed to (according to tutorials ive used)

so now ill try to run ut2004

---

### Post by Rosenrot on 2006-06-21
ut 2004 works now : D


but i have no sound : |

ive searched on the forum for an answer but all i could find was disableing esd in gnome and then starting ut2004

but that didn't work

and i found putting

sleep 5

underneath

#Prefs the users starting preferences

in the ut2004 shell executable

but i have no idea what that is or how to modify it
or if this would even work

---

### Post by Rosenrot on 2006-06-21
[QUOTE=Artificial Intelligence]Must of it, it remember for the last xorg.conf so must of it is okay. The thing you might change is card driver to nvidia.[/QUOTE]


i changed that to nvidia at the very beginning from nv being to the driver to nvidia

 can run ut2004 ok now just i have no sound

---

### Post by Perfect Storm on 2006-06-21
It's this:

> open /dev/[sound/]dsp: Device or resource busy

You might start a new thread about it. So people who have the solution can help you. I'm not sure how to solve that problem. Well you could try kill alsa thet same way you killed esd.

---

### Post by Rosenrot on 2006-06-21
ill do that

and thanks for all the help!
I almost though i had to reformat for awhile there.

---

### Post by Perfect Storm on 2006-06-21
There's always a way when using linux ;)
It's just a matter of how :KS 

I'm sure someone outthere knows how to solve the sound problem (over 110.000 member on the forum)

---

