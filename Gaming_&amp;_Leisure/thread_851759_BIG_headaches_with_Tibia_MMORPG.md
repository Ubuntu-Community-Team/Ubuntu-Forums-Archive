---
title: "BIG headaches with Tibia MMORPG"
date: 2008-07-07
forum: Gaming &amp; Leisure
---

### Post by napolperro on 2008-07-07
Hey.

I have been trying almost since I first installed Ubuntu to get this working, but for some strange and weird reason I cannot.

First I tried on my lappy, an Inspiron 6400 with an Intel chipset, Tibia would close immediately after opening, the error it gave in terminal was something of a X error of failed request, or something like that, then if I tried the windows version under WINE, it would overheat the laptop and I had to kill wineserver because it crashed, with the new WINE that doesn't happen, but the problem is that it seems the only way to get Tibia working with WINE is with version 0.9.15 I think, which is the one that overheated it.

Then I read that you could only run Tibia in an ATI or NVidia card, as my desktop has an ATI Radeon 9250, I gave it a go.

First it gave me the same error as in the laptop, then I updated the drivers and it gave me another error:
```

ulises@ulises-desktop:~/Escritorio/Tibia$ ./Tibia
Fallo de segmentación

```

Segmentation fault.

So this is what I asking you, could someone please tell me how do I get rid of this segmentation fault?
(I have tried running it with sudo, chmodded it... asked in the Tibia forums like crazy but no one could answer :()

---

### Post by scragar on 2008-07-07
segment faults are caused by attempting to access(read or write) from memory that doesn't exist, so it's not something you can normaly fix yourself. if you get a segfault with said program every time you run it then I would attempt to reinstall it, incase it is corrupt and thus causing the error, other than that though I'm out of ideas.

---

### Post by napolperro on 2008-07-07
I'm gonna give that a shot, could it also be that i'm screwing up when unpacking the file?

---

### Post by scragar on 2008-07-07
not very likly. After looking at the site it appears that you need libc6, so just check that's installed```
sudo apt-get install libc6
```however mostly likly you would have recived a more accurate error message than an attempt to continue without it.

Again, no idea's why you would recive a segfault unless either there's a problem with the game build or a problem with your ram(and since this is a localised problem it's definatly the game)

---

### Post by napolperro on 2008-07-07
Thanks, I looked up libc6 and it says I have the most recent version installed.

Maybe the only thing remaining is a mail to the Tibia customer support.. 

:mad:

Thank you anyway xD

---

