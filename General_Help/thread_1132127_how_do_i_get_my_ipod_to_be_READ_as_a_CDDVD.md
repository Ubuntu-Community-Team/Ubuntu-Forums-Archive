---
title: "how do i get my ipod to be READ as a CD/DVD"
date: 2009-04-21
forum: General Help
---

### Post by Ozzy0sbourne on 2009-04-21
im really kinda new at this.
my computer won't burn dvd's btw.
and im not trying to install ubuntu.
im already running ubuntu 8.10

ALSO the reason i want my ipod to be read as a CD/DVD is so that i can burn a .ISO to it.

i know i could just put the .ISO on it, but if i use a cd/dvd burner, then the burner would put the necessary autorun files... (since on the .ISO i can't tell what the install file is.)

so again. how do i get my ipod to be read as a CD/DVD.

thanks.





BTW!!!!!!!!: (also the .ISO to the operating system i am trying to install is a legal backup that i obtained by extracting the .ISO from the backup disc that they gave me when i got my computer. and now i have lost that backup disc. so i am forced to use the .ISO)

also i have no DVD burner...

---

### Post by Ozzy0sbourne on 2009-04-21
bump this is of the highest URGENCY to me... im on a timeframe here ><

---

### Post by Bakon Jarser on 2009-04-21
I don't think what you are trying to do is possible.  If you are trying to get your ipod to be read as a cd while booting it won't.  But modern machines support booting from usb drives.  If you are just trying to get some os to autolaunch the .iso that shouldn't be a problem.  You just need to mount the image (daemon tools in windows, gmount in linux).  If it doesn't autolaunch you can find out what autolaunch is supposed to do.  All it is is a text file labeled autolaunch.ini in the top level of the .iso.  Open it with a text editor and you will see what it does.  You can explore .iso images with winrar in windows or I think package archiver in ubuntu.

---

### Post by Ozzy0sbourne on 2009-04-21
> **Bakon Jarser said:**
> I don't think what you are trying to do is possible.  If you are trying to get your ipod to be read as a cd while booting it won't.  But modern machines support booting from usb drives.  If you are just trying to get some os to autolaunch the .iso that shouldn't be a problem.  You just need to mount the image (daemon tools in windows, gmount in linux).  If it doesn't autolaunch you can find out what autolaunch is supposed to do.  All it is is a text file labeled autolaunch.ini in the top level of the .iso.  Open it with a text editor and you will see what it does.  You can explore .iso images with winrar in windows or I think package archiver in ubuntu.

i dont want it to be read as a cd WHILE booting

i only want it to be read as a CD so i can burn an .ISO to it...

(if i burn the iso, the programs always put the autorun.inf file in it. which is what i want.)

---

### Post by Bakon Jarser on 2009-04-21
So, like I said, just mount the cd image with a program like gmount or daemon tools.  It already has the autorun.inf file in it and these programs will mount an image like it is a cd.

---

### Post by Ozzy0sbourne on 2009-04-21
> **Bakon Jarser said:**
> So, like I said, just mount the cd image with a program like gmount or daemon tools.  It already has the autorun.inf file in it and these programs will mount an image like it is a cd.

this iso doesn't have autorun.inf in it... i looked. even turned on hidden files and still it doesn't have it. so what i need is some way to make my ipod be read like a disc would in the CD/DVD drive. ive used some programs to make it be read as a usb drive. so... i need help x_x

TRUST ME on the fact that there is no autorun.inf in the iso >.<

---

### Post by Bölvaður on 2009-04-21
ubuntu has a tool to create live cds from iso files (that are live cd) on usb sticks.

System &#8594; Administrator &#8594; Create a USB startup disk

that should work for all live cd linux isos.

if you have something else like bds or solaris, please go to their forums for their help

---

### Post by Ozzy0sbourne on 2009-04-21
> **Bölvaður said:**
> ubuntu has a tool to create live cds from iso files (that are live cd) on usb sticks.

System &#8594; Administrator &#8594; Create a USB startup disk

that should work for all live cd linux isos.

if you have something else like bds or solaris, please go to their forums for their help


no im not trying to install or burn a linux live cd.
hence the...

> **Ozzy0sbourne said:**
> im really kinda new at this.
my computer won't burn dvd's btw.
**and im not trying to install ubuntu.**
im already running ubuntu 8.10


---

### Post by prem1er on 2009-04-21
You said you already had Ubuntu 8.10 installed.  That is what he is suggesting.

---

### Post by Bakon Jarser on 2009-04-21
Burning this image to disk (or ipod) is not going to create autorun features.  Mounting the image with gmount or daemon tools is almost exactly like burning the image to a disk and then sticking the disk in the drive.

---

### Post by pickboy87 on 2009-04-21
I'm very confused on what exactly the OP is trying to do. You want to burn the CD so that you can reinstall the Operating System back to it's original default, but use your ipod to load the image during boot?

Edit: You don't have a DVD Burner, do you have a CD burner? If the image is under 700 megs, you can use a CD instead of a DVD.

---

### Post by Ozzy0sbourne on 2009-04-21
> **Bakon Jarser said:**
> Burning this image to disk (or ipod) is not going to create autorun features.  Mounting the image with gmount or daemon tools is almost exactly like burning the image to a disk and then sticking the disk in the drive.

i know that now.
all i need to do now is create "autorun.inf" and put it to the setup exe file... all i have to do is find it.

---

