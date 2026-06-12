---
title: "Cant start Xubuntu"
date: 2008-01-28
forum: Dell  Ubuntu Support
---

### Post by cf_linux on 2008-01-28
I just installed Xubuntu on my Inspiron 2600. However, when I boot the system, the progress bar loads and then I get a black screen with random vertical lines. How do I fix this?

---

### Post by cf_linux on 2008-01-28
Will someone please help? Do I need to go to another forum?

---

### Post by ikkepjo on 2008-01-28
> **cf_linux said:**
> Will someone please help? Do I need to go to another forum?
Can you try to indicate where it stalls? In the grub menu, hit e and then e again on the line of the kernel you're starting up, edit the line to say "noquiet nosplash" instead of "quiet splash" and see what happens .... 

Or try maybe the safe mode?

By the sound of it it seems an X configuration issue, did you edit your /etc/X11/xorg.conf? Do you have special (nvidia?) hardware for which drivers got not installed ?

Sorry, more questions than answers ...

Peter

---

### Post by cf_linux on 2008-01-28
I tried the "noquietsplash" in the first line of the command in the grub menu, and nothing happened, which is a change because there were odd patterns coming up on the screen before.

---

### Post by cf_linux on 2008-01-28
Here is the order of events as they happen when I try to boot:

1. I press the power button. The DELL logo screen appears briefly.
2. The "GRUB starting..." screen appears, with an option to go to the menu. After two seconds this text disappears.
3. "Starting up..." and "Loading, please wait..." briefly appear at the top of the screen. Then the screen goes blank for a short while and then a strange pixelated array of colors comes up on the screen for a while. Eventually the screen goes black. If I press a key at this point, a dark lattice of colored lines appears.
4. If I press the power button, a page of code breifly appears, and the system shuts down.

---

### Post by jojopumpkin on 2008-03-30
What I have found on this issue isn't much What I do know is that Xubuntu IS fully installed on the system and when you get the blank screen Xubuntu is running behind it. There seems to be an issue with the "i830" chipset, the particular LCD used in this machine and/or X that is preventing the screen to display properly or at all. I too am having issues with this. There is no support that I have found for the "i830" chipset and I've combed countless pages for a solution and sadly only found unanswered questions such as yours.

The live disks do work when you have an external monitor attached and I'm trying to install and manipulate it with that arrangement as I post this.

I have only been successful with DSL (Damn Small Linux) and it's display efforts were lacking as compared to it on my desktop systems.

---

### Post by jojopumpkin on 2008-03-31
[Downgrade your BIOS and edit xorg.conf]("http://http://www.apfrod.com/works/2008/03/15/ubuntu_8_04_hardy_heron_on_dell_inspiron_2600") click for more info.

This guy figured it out. I would assume it would work just the same with Xubuntu. It ws a bit tricky doing the BIOS only because I didn't have a floppy disk but I managed it. I am now running Ubuntu 8.04 Beta on my Inspirion 2600 and I can see it!:KS

---

