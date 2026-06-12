---
title: "Ubuntu 8.10 on Dell Inspiron 8200 - graphics problem"
date: 2008-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ingvald on 2008-12-22
I have a problem when I install Ubuntu 8.10 on my Dell INspiron 8200. I have tried to install both the alternate and full version of ubuntu 8.10.
I am a newie when it comes to linux, but it seems like there is problems with the screen/display driver, or maybe the graphics card driver is correct to say. 

The display gets unreadable during the installation for desktop version, and using the alternate ubuntu version the display gets unreadable when I try to start up the ubuntu. Is there some tricks that I can do to overcome this problem? 
Should I rather go for another Linux distrubution.

I really just want to have some sort of Linux distr. on my laptop since I will try to make it work as an filesharing server. It will be a simple sharing server that different windows vista clients can connect to (with samba), and a remote control option using VNC/SSH. I haven't read so much about this yet, but will go for help when I get there. WHat I MUST have is a Linux distro with a good GUI, that works with my laptop inspiron 8200, and have the abillity of remote control with vista clients, samba etc....

So anyone that can show me some tricks to fix my ubuntu installation issue? 
Or maybe I should go for another distrubution? 
Someone that has experience with Ubuntu 8.10 on Dell Inspiron 8200? 

Regards,
ingvald

---

### Post by DieB on 2008-12-22
next time u boot and get to login screen press Ctr-Alt-F1, login there and type lspci - give us the printout of that. and we can go on cause [this]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron8200") says there are some with nvidia and some with ati/amd graphic cards.

but for an server u might not need no graphical user interface. all could be done via console. but we will help u get your graphics running ;)

---

### Post by ingvald on 2008-12-22
I had to reinstall ubuntu 8.10 (alternate version) to give this input. 
I have written the command as DieB proposed. How can I transfer this information to you? Anyone that has some step-by step suggestions for this? I feel very lost now just looking on the black terminal window, with a lot of text, and no scroll buttons and no SnagIt to use :P

If not I might have to use my digital camera to take pictures of the screen and attach to this reply, but then again how can I scroll down to see the text continuation in terminal window:P

Regards,
Ingvald

---

### Post by DieB on 2008-12-22
simply tell us those parts were u find something like VGA-compatible and/or nvidia and/or amd/ati, we for the first ain't need no detailed transcription, so leave the first parts with digits away.

sorry for not thinking about this in the first.

to get around the issue of to less space use the command as followed:
lspci | less
(you switch "pages with space, you get out of the view by hitting q)
or if u like to print the output to a file use "lspci > lspci.txt"
u afterwards can read it with nano by typing "nano lspci.txt".

sorry once again.

---

### Post by ingvald on 2008-12-23
> **DieB said:**
> simply tell us those parts were u find something like VGA-compatible and/or nvidia and/or amd/ati, we for the first ain't need no detailed transcription, so leave the first parts with digits away.

sorry for not thinking about this in the first.

to get around the issue of to less space use the command as followed:
lspci | less
(you switch "pages with space, you get out of the view by hitting q)
or if u like to print the output to a file use "lspci > lspci.txt"
u afterwards can read it with nano by typing "nano lspci.txt".

sorry once again.

Hey, and thanks again for a quick answer. You cant remember everything, difficult to know what newbies know :-) 

Well, here is some more info:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeoForce 4 440 Go] (rev a3)

I used the link that you gave me, and when I typed the following command
sudo apt-get install nvidia-glx 

I got the following message: 
Package nvidia-glx is not avaialbe, but is referred to by another pacakge. THis may mean that the package is missing, has been obsoleted , or is only available from another source E: Package nvidia-glx has no installation candiate

Any suggestions how to proceed?
Regards,
Ingvald

---

### Post by DieB on 2008-12-23
As for the Ibex being intrepid, they changed alot, so u would have to type:

sudo aptitude install nvidia-glx-96 nvidia-96-kernel-source nvidia-96-modaliases

this should also install the dependencies. afterwards do:

nvidia-xconfig

then type

sudo shutdown -rn now

this will reboot the machine and hopefully .... it will work.

---

### Post by ingvald on 2008-12-23
> **DieB said:**
> As for the Ibex being intrepid, they changed alot, so u would have to type:

sudo aptitude install nvidia-glx-96 nvidia-96-kernel-source nvidia-96-modaliases

this should also install the dependencies. afterwards do:

nvidia-xconfig

then type

sudo shutdown -rn now

this will reboot the machine and hopefully .... it will work.

When I try this I receive the following message:
Couldn't find any package whose name or description matched "nvidia-glx-96"
Couldn't find any package whose name or description matched "nvidia-96-kernel-source"

No packages will be installed.....etc....

By the way:
I have also found the xorg.conf (nano xorg.conf , under etc/X11), my brother suggested that I could check the screen resolution, maybe needed to do some adjustment. However, when I am looking at the window which I assume is the editor, GNU nano 2.07 it is said, there is no text to modify.

Any further suggestions?

---

### Post by alex_mayorga on 2009-04-18
ingvald,

I think you're another victim of [this bug]("https://bugs.launchpad.net/bugs/146706").

---

