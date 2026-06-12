---
title: "Really screwed up, Stuck in Command line without any way out"
date: 2009-03-05
forum: General Help
---

### Post by morellib on 2009-03-05
Ok, so I was trying something I'd ready earlier to try and get Compiz functional again but I was unable to get it to work. I have an Intel graphics card but I can't seem to find any drivers on my computer for it, and I can't seem to get ubuntu to find any either. So I was reading around and someone somewhere suggested entering in this command line prompt. (It begins with an 'en' I think, but I can't be sure because I can't find the post now.)

I tried that, it seemed to work. It gave me options of either installing a nvidia driver or an ati driver. I chose nvidia, the newest one it had available. It then requested that I restarted my computer. I agreed. 

Once my computer was restarted it booted to GRUB as per usual. I chose my kernel version then it booted to the Ubuntu slidy bar (as I call it). After that it was all pure command line. I logged in via command line, and then it only gave me command line options after that. 

I like to think I know a bit more about the command line now that I've been using ubuntu for almost a year, but I certainly have no clue what I'm doing to try and navigate my way out of this one. 

PLEASE! Someone help me out of this! I have a ton of stuff on my computer and was just able to jump over to my Windows side so I could post this!

Thanks!

---

### Post by Crafty Kisses on 2009-03-05
Have you tried starting X from the command line?
```
startx
```

---

### Post by morellib on 2009-03-05
Just tried it, it responded with

"Fatal Error. No Screens Found"

which is obviously a lie as I'm using a monitor to read it.

---

### Post by wfp on 2009-03-05
You could try sudo reboot from the command line. Then once you get back to your grub menu > choose recovery option> Now from the recovery option menu choose> try to repair x-server

---

### Post by utnubuuser on 2009-03-05
lo - don't know if this can help, but you could try > [http://ubuntuforums.org/showthread.php?t=1060406]("http://ubuntuforums.org/showthread.php?t=1060406")

---

### Post by morellib on 2009-03-05
It looks like repairing xserver really worked! Thanks so much. Now if anyone has any hints on how to make compiz work again I'd appreciate that. But if not that's cool too. I'm just happy to be back in my ubuntu!

Thanks so much wfp!

And everyone else as well!

---

### Post by avtolle on 2009-03-05
You have an Intel graphics card; which model (because depending upon its chipset, the drivers provided within Ubuntu won't support compiz as I understand it)?

---

### Post by avtolle on 2009-03-05
For example: [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards) (not saying this applies to your particular situation).

---

### Post by morellib on 2009-03-05
I'm not sure how to tell what model I have... how do I check that?

I was using compiz fine, 3d cube, etc. Then an update a week or two ago and I lost all of my effects. I tried re-enabling them and it said "Desktop effects could not be enabled" after it tried searching for "available drivers"

Any ideas?

---

### Post by morellib on 2009-03-05
Actually, just ran compiz-check. Here was my output if that helps at all:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

Ok, now any ideas?

---

### Post by wfp on 2009-03-06
So it looks like you have intels 945GM mobile chipset, so have you tried System>preferences>Administration>Hardware drivers>It should show you which driver you need just enable it.

---

### Post by morellib on 2009-03-06
I actually did just try that (sorry for taking so long to get back to you), and all the hardware drivers section says is:

"No proprietary drivers are in use on this system."

And there are a few blank boxes. I'm guessing this isn't how it's supposed to look?

---

### Post by morellib on 2009-03-07
What's really throwing me through a loop right now is that it appears that I ought to be able to do this without a problem at all. Everyone seems to think that Intel 945 should be working just fine. My real issue here is that xgl can't work. I can't find it on synaptic to download. I've downloaded every package that comes up when I search xgl and nothing seems to work. This is really mind boggling...

Then to top all of this off I've been getting some "Error 18", something about exceeding the BIOS in my grub menu when it tries to boot the new version of the kernel it downloaded the other day. Maybe that version has my xgl fixed, but I can't check of course haha. Plus every thread I find about this error 18 seems to end without a direct answer of what to do. 

Ugh. I can't get ahead haha.

---

