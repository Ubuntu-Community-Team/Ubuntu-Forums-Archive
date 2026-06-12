---
title: "Installing games with multiple CDs"
date: 2007-07-04
forum: Gaming &amp; Leisure
---

### Post by azraelck on 2007-07-04
I tried to install Call of Duty, and I was unable to get the CD to eject. I copied the files directly to my desktop; and tried to install from there; and it would not read the second disc. On openSuSE, I could eject the disc and insert the 2nd one, but it would not read it. I use Wine 0.9.39, which I don't believe actually works for a multiple disc install. It was the same as before; except openSuSE let me eject the disc; and Ubuntu refuses to do so. 

How do I get Ubuntu 7.04 to let me eject a disc when going through multiple CDs? Does Wine actually work on a multiple CD install? I know it works on single-disc installs perfectly fine; and will run most anything I put into it. But this doesn't help me with Call of Duty, or Wizardry 8. Thank you.

---

### Post by cogadh on 2007-07-04
First off, when you run the install, don't navigate to the install directory and run from there. Since the CD itself is being accessed by the terminal or file browser, that can sometimes prevent a clean unmount/eject. Instead open a terminal in your home directory and run it like this:
```
wine /media/cdrom0/install.exe
```
Obviously, change the cdrom and .exe reference to match your system and the game. If that doesn't let you eject the CD, then open a seperate terminal and run this:
```
wine eject d:
```
Again, modify the drive reference to match you CD-ROM drive's entry in winecfg. That should force the disk to eject. You may have to manually mount the second disk once you put it in.

---

### Post by manco on 2010-01-24
Thank you so much!

I was thinking I'd never install my Indiana Jones game

I'd like to add that I didn't have to manually mount the CD #2 after ejecting CD #1

---

