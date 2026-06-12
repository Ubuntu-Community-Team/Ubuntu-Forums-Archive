---
title: "Problem with Composite with ATI Mobility radeon 9200"
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by pospam on 2007-05-24
Hi all:
After reading several post in the forum I cannot find how to fix my problem.
First I tried to use Desktop effects but I could not because It said "composite extension not avalaible"

I run this commands in the console I got this:

glxinfo | grep direct
direct redering: Yes

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)


So everything seemed to be o.k.Then after reading in the forums I changed the flag in my xorg.conf from 
Section "Extensions"
	Option		"Composite"	"0"
to
Section "Extensions"
	Option		"Composite"	"Enable"


I restart ubuntu and then when I try to use desktop effects I dont get the same message as before but I cannot enable them.
The strangest part is that when I run again the commands in the console I get:

glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

and

fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect

Can some one explain me why by enabling the composite extension ubuntu stops using the ATI drivers for my video card?
Thanks for your help
P.

---

### Post by Ub1476 on 2007-05-24
The composite option is to be "0" so you had that correct:) The reason you are getting the error message is that you are not running a session in XGL/AIXGL. Depending on your graphic card you need to install one of those.;)

Guide for both here: [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

I think your card works with both, but AIGXL gives better performance, and XGL gives better 3d effects.

---

### Post by kpolice on 2007-05-24
The Radeon 9200 works better with the open source driver in my experience.

---

### Post by misfitpierce on 2007-05-24
You can make a XGL session for ubuntu for an ATI card. Takes some configuring but you can google find it.

---

### Post by pospam on 2007-05-24
Hi guys thanks for your responses.
I am a linux noob so can you please tell me how to install either
AIXGL or XGL
I cannot seem to find the how to in the link you gave me.
P

---

### Post by Ub1476 on 2007-05-24
When you click on the link, you start right on the guide. The headline is how to install Beryl (ATI). If you don't know what Beryl is, take a search at youtube.com. You surely will want it;)

Follow the guide and STOP when it says something like: "How to install using closed source drivers". Closed source is XGL, but it seems like AIXGL (open source) works best for your card.

Good Luck

---

### Post by pospam on 2007-05-24
Hi guys:
I followed the guide and I now beryl works.
I have to say that I am amazed.
One thing though, everything seems to be o.k.
but when I run 

glxinfo | grep direct

I get

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

Any ideas?

By the way for
fglrxinfo I get the right output

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

Thanks all for your help.
P.

---

### Post by Ub1476 on 2007-05-24
Everything is ok for you now. Shows the same for me, and Beryl works like a charm:D

---

### Post by pospam on 2007-05-25
Hi again:
I have another question fro you guys.
In the guide I followed it says at the end this:

Congratulations! Hopefully, you have Beryl working now. You can now re-enable your universe repositories, but make sure you do not let it update anything related to Beryl. Hopefully, the Beryl apps in the universe repositories will soon work with the ATI cards without XGL

I did re-enable the universe repositories and there are 15 updates related to beryl and emerald.
I am afraid of installinf them and breaking the system.
Has any of you guys done this updagre and with what results?
Thanks
P.

---

### Post by Ub1476 on 2007-05-25
The updates doesn't work with XGL, not sure about AIGXL though. But if you happen to install them, and everything screws up, here's how to remove beryl and xgl (just reinstall):

```
sudo aptitude remove xserver-xgl beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
``` 

Just remove xgl (in the code) with aixgl if you got that installed.

Oh, and just to be safe, remove beryl as a startup program if you try the updates.

---

