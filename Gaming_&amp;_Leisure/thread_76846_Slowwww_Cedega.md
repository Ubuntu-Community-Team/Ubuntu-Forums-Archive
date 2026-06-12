---
title: "Slowwww Cedega"
date: 2005-10-15
forum: Gaming &amp; Leisure
---

### Post by Niroth on 2005-10-15
I have been a dual boot linux / windows er for quite some time and just switched my linux over to Ubuntu 5.10 last week (had tried a number of other distros previously).. needless to say I have been so impressed that I would love to try and reduce the number of times i need to boot into windows as much as possible.

I have been trying to get cedega to work for game emulation but am having some trouble.  I have an ATI card which I know is bad 9800 XL with ATI drivers 8.18.06 installed (at least I think.. ran the installer and the config program to make the new xorg.conf and it seemed to go without a hitch).  I installed the latest wine with apt-get and cedega 4.4.3 from a tgz file.  I am able to get some games such as warcraft 3 to run but they are only running at about 1 fps at best.  I know ATI has a bad rep for Linux Drivers but I'm guessing they can't be 1 fps in warcraft 3 bad.   The performance seems to be the same wether i do a "cedega war3.exe" or a "cedega war3.exe -opengl"

Anyone have any suggestions for what i might be doing wrong?  Like I said warcraft III looks and sounds just like War3 just very slow (although the sound  goes without a hitch).

Also of note is i am running this from a readonly mounted NTFS drive, could this possible have something to do with it?  I might have to delete some things but perhaps converting it back to FAT32 would be better?

Thanks

---

### Post by jecos on 2005-10-15
ALWAYS copy the game from the read-only ntfs drive to a writable drive, your asking for problems when you don't allow the game to write to its own files..  Cedega should be able to run it fine with -opengl cmd on a 9800(PRO or XT).  I havent tried it on 4.4.3-1 but It should work on the previous version.

---

### Post by Niroth on 2005-10-15
Yeah I knew that it would eventually need to be able to write to the drive for saved and things like that but figured for a performance test it would be ok.. 

One thing i found odd was when i ran Point2Play it lists my video card as Mesa Project - Mesa GLX Indirect with a driver of 1.2 (1.5 Mesa 6.2.1) and it fails the "3D Acceleration Test".. does this mean the ATI Driver install didn't take?

---

### Post by Hairy_Palms on 2005-10-15
sounds like you need to change your xorg.conf

---

### Post by jeffreyvergara.NET on 2005-10-15
try to reinstall your ATI Driver.

---

### Post by Niroth on 2005-10-16
I tried reinstalling the ATI driver and noted that the xorg.conf file was time stamped properly and says it was created by the ATI installer.. but same dice on all fronts, any other ideas, what is this MESA thing it thinks my video card is?

---

### Post by e^e on 2005-10-16
Mesa is the default library that comes with xorg to provide opengl functionality. But you wont get hardware 3d acceleration from it, ie only software rendering. That's why 
the proprietary ATI driver is needed instead.  so when you install the drivers , write this in a terminal:-

 glxinfo | grep render
 
 it should display something like "direct rendering : Yes"

---

### Post by Niroth on 2005-10-16
Hmm:

$ glxinfo | grep render
direct rendering: No
    GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect

---

### Post by TLE on 2005-10-16
It's definitely the ATI driver installation that's the problem. This has given a lot of people a lot of problems. The drivers you download from the ATI web-sit doesn't install properly. But as far as I know the solutions posted in the following threads has worked for some people, including me. If you're running the 64 bit version of Ubuntu 5.10 it is somewhat worse, I don't think there's any solution for that, yet. Anyway try and have a look:
[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=mlomker]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=mlomker")
[http://www.ubuntuforums.org/showthread.php?t=65276&highlight=mlomker]("http://www.ubuntuforums.org/showthread.php?t=65276&highlight=mlomker")
[http://www.ubuntuforums.org/showthread.php?t=76057&highlight=mlomker]("http://www.ubuntuforums.org/showthread.php?t=76057&highlight=mlomker")
[http://www.ubuntuforums.org/showthread.php?t=76116&highlight=mlomker]("http://www.ubuntuforums.org/showthread.php?t=76116&highlight=mlomker")

And if that doesn't do it try and search the forum for "how to ati fglrx"
Good luck

---

### Post by mismis on 2005-10-17
[QUOTE=Niroth]I have been a dual boot linux / windows er for quite some time and just switched my linux over to Ubuntu 5.10 last week (had tried a number of other distros previously).. needless to say I have been so impressed that I would love to try and reduce the number of times i need to boot into windows as much as possible.

I have been trying to get cedega to work for game emulation but am having some trouble.  I have an ATI card which I know is bad 9800 XL with ATI drivers 8.18.06 installed (at least I think.. ran the installer and the config program to make the new xorg.conf and it seemed to go without a hitch).  I installed the latest wine with apt-get and cedega 4.4.3 from a tgz file.  I am able to get some games such as warcraft 3 to run but they are only running at about 1 fps at best.  I know ATI has a bad rep for Linux Drivers but I'm guessing they can't be 1 fps in warcraft 3 bad.   The performance seems to be the same wether i do a "cedega war3.exe" or a "cedega war3.exe -opengl"

Anyone have any suggestions for what i might be doing wrong?  Like I said warcraft III looks and sounds just like War3 just very slow (although the sound  goes without a hitch).

Also of note is i am running this from a readonly mounted NTFS drive, could this possible have something to do with it?  I might have to delete some things but perhaps converting it back to FAT32 would be better?

Thanks[/QUOTE]
can u plz tell me where i can get cedega for freee.

---

### Post by seethru on 2005-10-17
[QUOTE=mismis]can u plz tell me where i can get cedega for freee.[/QUOTE]
Piracy isn't something we support around here, especially when it involves a product that deserves your money. I too wish Cedega was open source, I believe the development would move a bit quicker then, HOWEVER, these guys are talented and more than deserve the $15 for 3 months of access.

---

### Post by glaze on 2005-10-17
[QUOTE=seethru]Piracy isn't something we support around here, especially when it involves a product that deserves your money. [/QUOTE]
There is a free legal version of Cedega, that can be downloaded with CVS.

---

### Post by seethru on 2005-10-17
[QUOTE=glaze]There is a free legal version of Cedega, that can be downloaded with CVS.[/QUOTE]
yes there is, which is something I forgot to mention. CVS can be a pita as far as cedega goes though.

---

