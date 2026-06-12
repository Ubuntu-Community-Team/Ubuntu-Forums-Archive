---
title: "Not sure what my problem is"
date: 2009-01-16
forum: General Help
---

### Post by Miilou Suede on 2009-01-16
Hey guys.  I'm trying to run both Ubuntu and XP.  Ubuntu is on my 200 GB IDE Seagate and XP is on my 500 GB SATA WD.  For some reason, I can't boot into XP. I checked everything in the BIOS  to make sure the WD had priority over the Seagate, but I consistently boot into the Ubuntu drive (Seagate).  

A buddy of mine suggested my MBR is broken, so I ran the "fixmbr" in the XP recovery console. I may have done that incorrectly, because I wasn't sure what to do after it and just hit "exit."

Anyone have any insight on what might be my problem?

---

### Post by kesre on 2009-01-16
I'm assuming you installed Ubuntu after XP with a CD
did you choose to install GRUB bootloader over the MBR? - it would have been an option towards the end of the setup (you might have overlooked it...)

Also, what happens when you boot up?

---

### Post by burnetbj on 2009-01-16
After your PC completes the post do you get a black screen listing Linux and Win XP installed. If so at that screen, down arrow till XP is highlighted and click enter if not. I would assume your is messed up. Although I havent experienced this I have seen many people talking about it. Just google fixing grub ubuntu and im sure you will find what your looking for

---

### Post by Miilou Suede on 2009-01-16
The buddy I mentioned was the one who installed it.  I doubt he made that mistake upon installation but it is possible.  Maybe I should reinstall.

When I boot up, I'm brought up to the Ubuntu "orange loading bar" and then directly into GRUB.  And at that point, I get the error message "gave up waiting for the root device." (I actually posted this in a thread about 2 months ago but I could never figure out the problem.)

---

### Post by kesre on 2009-01-16
Interesting... GRUB should precede Ubuntu loading bar, allowing you to choose between XP and Ubuntu. you could try reinstalling it, but I would wait for a bit and see if anyone else has better suggestions.

So your computer is loading the Seagate first, or does it give you an option to chose which harddrive to boot into?

---

### Post by Miilou Suede on 2009-01-16
Whoops, heh.  GRUB does precede the loading bar by giving the countdown but the boot menu does *not* provide a choice to boot to XP (only ubuntu, ubuntu recovery mode and memtest). Then it hits loading bar, and after that it "gave up waiting for root device."

It boots to the Seagate first, yes.

---

### Post by blazemore on 2009-01-16
From Ubuntu, go to Application -> Accesories -> Terminal

Type the following into the window that appears:
```
sudo update-grub
```

Hopefully that will fix your problem.
If not then I know what to do anyway.

---

### Post by Miilou Suede on 2009-01-16
Booting into Ubuntu with the live CD (which is my only way in), I try that command and get "No GRUB directory found."

---

### Post by jocko on 2009-01-16
> **Miilou Suede said:**
> Whoops, heh.  GRUB does precede the loading bar by giving the countdown but the boot menu does *not* provide a choice to boot to XP (only ubuntu, ubuntu recovery mode and memtest). Then it hits loading bar, and after that it "gave up waiting for root device."

It boots to the Seagate first, yes.

It sounds like grub is not properly configured. I'm not sure why ubuntu "gives up waiting for root device", but I think you probably need to fix whatever is causing that first.
Have you been able to boot ubuntu at all?
Can windows boot at all if you **remove** the drive with ubuntu on it from the boot order in bios? There should be an option to disable it instead of just changing the order.

If the ubuntu drive is not in the boot order at all, either windows will boot (which means the mbr still contains the windows boot loader), or you will get an "invalid system drive" error from bios or perhaps a grub error. Either way, fixmbr from a windows recovery console should fix it... never done it myself, so I can't tell you much more...

If you haven't been able to boot ubuntu at all, or haven't put in a lot of time setting it up just the way you want it, I would suggest you try to reinstall ubuntu as it's probably much quicker than finding out what the problem is and fixing it...
...Unless someone who reads this already think they know what's causing it...

And if/when you reinstall ubuntu, make sure the computer bios is set to boot from the drive with windows on it (this should make sure grub finds the windows install and makes an entry for it in the boot menu).
Or, if you want to be able to remove ubuntu without getting problems booting windows, you could set the drive with ubuntu on it as primary boot, which should make sure the windows boot loader stays in the mbr of the windows drive. Then you should be able to choose what to boot by switching the bios boot order, and by a little manual editing of the boot menu you should be able to add windows to grub.

---

### Post by jocko on 2009-01-16
> **Miilou Suede said:**
> Booting into Ubuntu with the live CD (which is my only way in), I try that command and get "No GRUB directory found."

You could try following this [guide for fixing grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). As ubuntu actually start to load, I don't think grub is your primary problem, but it will just take a few minutes to try it so do it before you try anything more time consuming (like my advice in the post above).

---

### Post by Miilou Suede on 2009-01-16
Okay, some eerie revelations here.  I pop open the case to disconnect the Ubuntu drive, but I accidentally disconnect my DVD burner.  Once I boot up, it *actually* lets me into Ubuntu.  I updated GRUB through the terminal but it didn't seem to fix anything.  I couldn't boot into XP through the GRUB OS choice menu but still, a piece of the puzzle may have been revealed.

When I disconnect the Ubuntu drive (or connect both it and the DVD burner) it gives me the GRUB error 17.

Just off the top of my head: is it possible a power cable may be damaged/loose on my XP drive? I'm no expert on how HDD's work (or even savvy for that matter)but I can still see the drive being detected in the BIOS and even when I manage to boot into Ubuntu I can look into it from there, but I can't actually boot with the drive.  I didn't know if power had anything to do with it but just throwing it out there.

---

### Post by Miilou Suede on 2009-01-16
Anyone else got any ideas?

---

### Post by fenian on 2009-01-16
Did you disconnect the Ubuntu drive and try to boot into XP?

---

### Post by Miilou Suede on 2009-01-17
Yeah, no dice. It gives me GRUB error 17.

---

