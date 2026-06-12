---
title: "A newbie question about a boot CD"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Delp3 on 2005-07-02
I downloaded Kubuntu and copied the extracted files onto a CD.  Even though I was able to view and install various components by opening the drive from the desktop I can't get my computer to boot from the CD drive.

I looked around and found out how to configure the BIOS for a disk boot but that didn't work either. I followed the instructions from this [site](http://www.windowsnetworking.com/j_helmig/bootcd.htm) and changed the boot disk sequence so it would read from the CD drive first.  

Am I missing something?  After installing Firefox and loving it I am excited to see the rest of what I've been missing.

Thanks

---

### Post by Stemp on 2005-07-02
You'll have to create a cd from the iso (image) you've downloaded.
And not to copy the files.
Then your cd will be bootable.

---

### Post by Delp3 on 2005-07-02
I thought that's what I did.  Shouldn't the .iso file be included with the unzipped files?  I just used Nero to make the CD so I figured that's all I had to do.  Are there addtional steps when dealing with .iso files? I've never messed with them before.

---

### Post by Feanor on 2005-07-02
You must do `burn cd image` o something similar (I don't remember nero since I use k3b  :)  ) then select the .iso file

---

### Post by t2kburl on 2005-07-02
In Nero burning ROM ... select Recorder menu ... then burn image to disc ... then select the ISO you downloaded ... then burn away.

Have fun  \\:D/

---

### Post by Delp3 on 2005-07-02
Sorry to keep asking seemingly idiotic questions but...

I found the Create Boot Disk option in Nero and burned the only .iso file I could find in the folder.  It's called Kubuntu-5.04.2-i385-live.  It's listed as a WinRar archive in Windows but I also saw it listed as an .iso.  

When I reboot with the disk in the drive it brings me to DrDos at an A: prompt.  I brought up the D: drive  and looked at the directory and it had the .iso file on it.  

I am stumped.

I appreciate all the advice - I am getting there and can't wait to try it out.

---

### Post by Stemp on 2005-07-02
```
Sorry to keep asking seemingly idiotic questions but...
```
Not idiotic at all, If you created a boot disk, you shouldn't see any .iso file.
It must be a bootable disk with folder and files, but NO .iso file.
PS : sorry I don't remember Windows (and Nero) enough to help you

---

### Post by datu on 2005-07-02
What version of nero are u using? I am using Reloaded and i just burned the iso with nero yuesterday . .  . i think i can help u.

---

### Post by t2kburl on 2005-07-02
using the create bootable disc in Nero is useful only for creating CDs that would not otherwise be bootable.
The ISO you downloaded is bootable as is.
When you open Nero burning ROM just cancel the wizard.
This will bring you to the burning rom screen
Choose the Recorder menu, select burn image to disc, then select your downloaded ISO and burn it.

I burn all my ISOs this way

also I recomment deselecting ISO from the file association list of winRAR

if you download something as an ISO it it meant to be burned to disc as an ISO, not extracted by winrar.

ISO is an image of the CD. Nero also uses .nrg which is the same as an ISO

Good luck

---

### Post by datu on 2005-07-02
From Nero start smart

select make data CD

after the window opens choose

Recorder > Burn Image

you get a dialog box so u can navigate to where u saved ur Ubuntu ISO

then click burn and you should be good to go with the default Nero Burn settings

---

### Post by Delp3 on 2005-07-02
Thank you all so much.   I was finally able to burn the image onto a disc and got it to work.

 \\:D/ 

You've all been a great help and I'll visit here again (because I'm sure I'll run into problems again.)

---

