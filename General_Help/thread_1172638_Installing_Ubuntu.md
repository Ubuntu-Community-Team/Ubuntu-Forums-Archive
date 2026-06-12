---
title: "Installing Ubuntu"
date: 2009-05-28
forum: General Help
---

### Post by Shomme on 2009-05-28
I keep getting stuck at 5% on ext# file system, Im installing it on a pentium 2, radeon 2700 plug and play i know this setup can work ive seen it done however i keep getting this error.



(Is a beginner), 
Yours Truly Shomme

---

### Post by Shomme on 2009-05-28
Does any know my problem or have a solution?

---

### Post by Shomme on 2009-05-28
Bump? I don't think anyone sees my thread, Also it keeps trying to reformat whats already formatted.

---

### Post by Shomme on 2009-05-28
> **Shomme said:**
> Bump? I don't think anyone sees my thread, Also it keeps trying to reformat whats already formatted.


Is anyone going to help me :KS

---

### Post by merlinus on 2009-05-28
You might try posting your complete system specs including processor speed, RAM, video card, hard disk size, and which version of ubuntu you are trying to install.

---

### Post by NewTooThis on 2009-05-28
> **merlinus said:**
> You might try posting your complete system specs including processor speed, RAM, video card, hard disk size, and which version of ubuntu you are trying to install.

Ye could you post the output to commands in terminal such as "lspci" or "lshw" (dont worry about the warning on this one) :p

---

### Post by Shomme on 2009-05-28
> **NewTooThis said:**
> Ye could you post the output to commands in terminal such as "lspci" or "lshw" (dont worry about the warning on this one) :p

I did post specs, 

Pentium2 (300MGHZ)
512MB Ram
Radeon 2700 (Plug&Play)

---

### Post by Shomme on 2009-05-28
> **Shomme said:**
> I did post specs, 

Pentium2 (300MGHZ)
512MB Ram
Radeon 2700 (Plug&Play)

Specs are here any suggestions?

---

### Post by merlinus on 2009-05-28
What version are you trying to install?  Here are the specs for ubuntu 9.04:

**Bare Minimum requirements**

 It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the *Alternate install CD* to attempt such an installation. 

[LIST]
[*]300 MHz x86 processor 
[*]64 MB of system memory (RAM) 
[*]At least 4 GB of disk space (for full installation and swap space) 
[*]VGA graphics card capable of 640x480 resolution 
[*]CD-ROM drive or network card 
[/LIST]
 
**Recommended minimum requirements**

 Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

[LIST]
[*]700 MHz x86 processor 
[*]384 MB of system memory (RAM) 
[*]8 GB of disk space 
[*]Graphics card capable of 1024x768 resolution 
[/LIST]
As you can see, you have the bare minimum, in terms of a processor, so you might wish to try xubuntu, or the text-based alternate install cd.

---

### Post by NewTooThis on 2009-05-28
> **Shomme said:**
> Specs are here any suggestions?

I suggest posting the output to the terminal commands, as this information is to minimal to understand your problem.

---

### Post by merlinus on 2009-05-28
I do not see how he can even get to a ubuntu terminal....

---

### Post by Shomme on 2009-05-28
Using the desktop version thanks for the replys 9.0.4

I don't have many ways to get other versions my connection isn't great i ordered this one free.

---

### Post by albinootje on 2009-05-28
> **Shomme said:**
> I keep getting stuck at 5% on ext# file system 

Are you installing from cdrom ? Did you burn the cdrom at low speed and did you verify the md5sum of the iso image, and verified the cdrom after burning ?
See here : [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by Shomme on 2009-05-28
> **albinootje said:**
> Are you installing from cdrom ? Did you burn the cdrom at low speed and did you verify the md5sum of the iso image, and verified the cdrom after burning ?
See here : [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)


Just said i ordered the free cd off the site

---

### Post by merlinus on 2009-05-28
Did you select the option to try ubuntu without changing anything from the opening menu?

---

### Post by Shomme on 2009-05-28
No not yet

---

### Post by merlinus on 2009-05-28
Give it a try, and if it will not run, then don't even try to install it from the cd you have.

---

### Post by albinootje on 2009-05-28
> **Shomme said:**
> Just said i ordered the free cd off the site

I've had some bad experience with the free-of-charge cdroms in the past (Hoary,Breezy), please verify it to see whether it is OK.

---

### Post by Shomme on 2009-05-28
I got it from UBUNTU's site directly

---

### Post by NewTooThis on 2009-05-28
> **merlinus said:**
> I do not see how he can even get to a ubuntu terminal....

your 100% correct, I totally misread and rushed through his first post haha, sorry about that shomme ;)

---

### Post by Shomme on 2009-05-28
The try out mode starts up by the way and works

---

### Post by Shomme on 2009-05-28
Anyone?

---

### Post by Shomme on 2009-05-28
Hello?

---

### Post by Pbethe on 2009-05-30
> **Shomme said:**
> The try out mode starts up by the way and works

OK, now you should be able to execute the commands that people suggested, like lshw.  Key Ctl+Alt+F1 to get a command line.  After that, Ctl+Alt+F7 gets you back to the desktop.  There should be a system log viewer on the menus.  That might give you an idea of what is going on.

---

