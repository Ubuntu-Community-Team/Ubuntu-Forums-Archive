---
title: "NWN problem"
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by bob2098 on 2006-11-07
After finally upgrading to a 64bit system running 6.10 I tried to install NWN but when I try to run it is fails saying

./nwn: 12: ./nwmain: not found

and if I try to run nwmain

bash: ./nwmain: No such file or directory

but the file is there and it finds it to copy it. I have tried reinstalling an I get the same problem.

Does anyone know what the problem is?

---

### Post by RoyArne on 2006-11-07
> **bob2098 said:**
> After finally upgrading to a 64bit system running 6.10 I tried to install NWN but when I try to run it is fails saying

./nwn: 12: ./nwmain: not found

and if I try to run nwmain

bash: ./nwmain: No such file or directory

but the file is there and it finds it to copy it. I have tried reinstalling an I get the same problem.

Does anyone know what the problem is?

Do you have the following libraries installed?

```
ia32-libs, ia32-libs-gtk, ia32-libs-sdl
```

Installing the above libraries fixed the same error for me.

---

### Post by bob2098 on 2006-11-07
thanks that fixed that, now it just seg faults

Fatal signal: Segmentation Fault (SDL Parachute Deployed)

do you know what to do for that?

---

### Post by RoyArne on 2006-11-07
> **bob2098 said:**
> Fatal signal: Segmentation Fault (SDL Parachute Deployed)

do you know what to do for that?

Sorry, I don't think so. What version of NWN are you running? I downloaded v1.68 before I tried it on Edgy, and I have the Hordes of the Underdark and Shadows of Undrentide extensions.

---

### Post by bob2098 on 2006-11-07
The same with CEP2

---

### Post by Perfect Storm on 2006-11-07
Remember to run the nwnmain from nwn directory.

Another possibility is removing the line in the nwn script that points it to use the libSDL that comes with nwn to the one you use on ubuntu.

---

### Post by PriceChild on 2006-11-07
You shouldn't use nwmain.... nwn gets the system ready to run nwmain.

I've always sorted out the segfaults by chowning the folder to me.

---

### Post by Perfect Storm on 2006-11-07
ops...yeah, just checked. it's nwn and not nwnmain.




If you solve the segfaults it's a good idea to making a launcher script for nwn so you don't have to be in nwn folder to start nwn;

```
cd /into/nwn/folder
nano StartNWN.sh
```

add:

[b]#!/bin/bash

cd /into/nwn/folder
./nwn[/b]

```
chmod +x StartNWN.sh
```

Now point the launcher to StartNWN.sh

---

### Post by bob2098 on 2006-11-10
Thanks it's sorted now.

---

