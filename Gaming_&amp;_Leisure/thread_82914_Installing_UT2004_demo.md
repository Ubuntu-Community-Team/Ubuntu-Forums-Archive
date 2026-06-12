---
title: "Installing UT2004 demo"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by JurB on 2005-10-27
Hi,
I downloaded the UT2004 demo and got a .run.gz file.
How do i install this?

tnx
JurB

---

### Post by JurB on 2005-10-27
Apparently the file i downloaded from the Atari server was a bad one.
I got it somewhere else and everything worked great.

---

### Post by axlpxl on 2005-10-28
Where did you find the proper one? Im having the same problem.

---

### Post by JurB on 2005-10-28
[http://www.3ddownloads.com/linuxgames/ut2k4/demo/](http://www.3ddownloads.com/linuxgames/ut2k4/demo/)

Here you go!

---

### Post by rokknroll on 2006-09-12
anywhere without  await :) BTW anyone figure out what the original archive has wrong with it?

---

### Post by Perfect Storm on 2006-09-12
```
cd /distination
sudo sh XXXXXXXXXXXX.run.gz
```

Exit the installer. Do not hit the start button. Then write ut2004 in the terminal.

---

### Post by rokknroll on 2006-09-12
Thanks Ai :)
Im not sure if its the archive i d/led, but i get an cannot execute binary file error on this, ive treid two different source, the version of the demo im trying is UT2004-LNX-Demo3334.run.gz.
Crazy thing is i had UT2k3 running under my old mandrake 9 as easy as if it was a winbox, but im a bit linux rusty as of late, so im probably missing something really obvious...

---

### Post by rokknroll on 2006-09-12
sorry should mention i did extract the .gz archive first...:p

---

### Post by rokknroll on 2006-09-12
sorry for semi-spam:  i figured it out...
i made a noob mistake-Had the filename in the wrong case for one letter :(

---

### Post by myname on 2007-04-19
I just downloaded the UT2004 demo (version 3334) from here:
[http://www.3ddownloads.com/linuxgames/ut2k4/demo/](http://www.3ddownloads.com/linuxgames/ut2k4/demo/)

and when I execute the following command:

~/download/linux$ sudo sh UT2004-LNX-Demo3334.run.gz

I get the following error:
UT2004-LNX-Demo3334.run.gz: 1: Syntax error: ")" unexpected

Is there something I am doing wrong?

--Kevin

---

### Post by Perfect Storm on 2007-04-19
Try open the file in the editor (if possible), how's the first line?

---

### Post by myname on 2007-04-20
I extracted the file first, then ran the sudo sh command and it's installing as I type this.

[EDIT]
Spoke too soon.  The game appears to install, and now from the Konsole, I get the following when I try to launch the game:

> ~/download/linux$ ut2004
open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual


---

