---
title: "My computer failed to boot normally owe to a lame script located at /etc/init.d"
date: 2009-01-15
forum: General Help
---

### Post by tzury on 2009-01-15
By mistake,

I added a python script to /etc/init.d/ and link to it at /rcS.d
Now, every time I boot my computer the script takes control and prevent other services to be loaded. And I get myself, left over with the screen where the cript is running and cannot be stopped (ctrl+c/ctrl+z/ctrl+d don't stop it).

From the GRUB menu I choose the recovery option but everything is the same.

---

### Post by mssever on 2009-01-15
Boot from the live CD, mount your hard disk, and delete the file/link.

---

### Post by wolfen69 on 2009-01-15
> **mssever said:**
> Boot from the live CD, mount your hard disk, and delete the file/link.

just do ```
sudo su
```then ```
nautilus
```then you can navigate to the file and delete it or whatever. or do ```
rm /etc/init.d/whatever_file
```

---

### Post by tzury on 2009-01-15
Guys,
Live CD becomes un-bootable once Ubuntu is installed.
It seems like Grub is identifiying it and redirects the boot to (hda0,0 - ext3).

I tried this on two laptops and got the same results.

Is there a way to press a key during boot (as in Win and Mac) and avoid startup services?

---

### Post by wolfen69 on 2009-01-15
usually F12 as soon as the computer starts will bring up a quick boot menu that will allow you to choose which device to boot from. but it could be another key.

F1, F2, F10 or delete at bootup will get you into the BIOS that will allow you to change the boot order of your machine. press all 4 quickly 1 at a time as soon as the computer boots.

---

### Post by tzury on 2009-01-15
It is f12 on ThinkPad and f10 on Compaq.

Did that my friend and yet, got the boot from HD.

---

### Post by mssever on 2009-01-15
If you can't boot from the live CD even after explicitly telling the BIOS that you want to boot from the CD, then your hardware is screwy and your problem is likely irreparable until the hardware problems are solved.

---

### Post by mssever on 2009-01-15
> **tzury said:**
> Is there a way to press a key during boot (as in Win and Mac) and avoid startup services?
Recovery mode is for that purpose. But you probably symlinked your script into rc1.d. The whole system uses init files to boot, so if you disabled all of them, booting wouldn't be possible.

---

### Post by tzury on 2009-01-15
> **mssever said:**
> If you can't boot from the live CD even after explicitly telling the BIOS that you want to boot from the CD,

I don't think this is the case. See, it is not likely that two laptops on my desktop are suffering from the same problem which I was not aware of especially where one was installed just **yesterday** using the very same CD and CDROM drive.

What I suspect is that since the CD itself is booting using Grub. Grub is not booting from the CD but redirecting to the HD.

Try it yourself and see it happening.
[B]
You simply cannot boot from Ubuntu CDRom once Ubuntu is installed.[/B]

---

### Post by mssever on 2009-01-15
> **tzury said:**
> **You simply cannot boot from Ubuntu CDRom once Ubuntu is installed.**
Yes, you can. I've done it many times.

And if for some reason you're having trouble with your live CD, you can try another one. Any Linux-based live CD will do the trick. You don't specifically need the Ubuntu live CD.


EDIT: Are you trying the alternate install CD instead of the live CD? That might explain your problems.

---

### Post by tzury on 2009-01-15
> **mssever said:**
> Yes, you can. I've done it many times.

And if for some reason you're having trouble with your live CD, you can try another one. Any Linux-based live CD will do the trick. You don't specifically need the Ubuntu live CD.


EDIT: Are you trying the alternate install CD instead of the live CD? That might explain your problems.
> EDIT: Are you trying the alternate install CD instead of the live CD? That might explain your problems.
I am trying to use the default 8.10 iso image.
Is there any other?

---

### Post by tzury on 2009-01-15
Finally SOLVED!!!!
wolfen69 and MSSever - I would love to thank you for your time and attention.

I used Xubuntu CD for the rescure.

---

