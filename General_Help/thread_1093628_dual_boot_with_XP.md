---
title: "dual boot with XP?"
date: 2009-03-11
forum: General Help
---

### Post by Hellstudios on 2009-03-11
Hi, I have an ATI graphics card which won't display 3D when im in wine. and my entire hard drive just has ubuntu on it, how do I Dual Boot with XP But Without Erasing Ubuntu? Cause I really wanna play My Steam games but I can't since I am on Ubuntu...

Well Since i dont really know how to write paragraphs ill rephrase the question here.

How do I Install XP Without Deleting Ubuntu?

I want like a 40gb Partition made for XP so i can play my games on it.... how would I do that?


Btw, I don't mind paying for an XP live CD.

---

### Post by LegendofTom on 2009-03-11
When you install Windows, use the partition manager to put windows and Ubuntu side by side.

---

### Post by anlag on 2009-03-11
You can use the the partition manager (gparted in Gnome) to resize one of your existing partitions in order to leave space for a new NTFS partition where you then install Windows XP. You should do backups on your system before doing this, as there is always the risk that something might go wrong. In addition I believe it's appropriate to do the repartitioning from a live CD, so that you don't need to be running from the same system whose disk space you're resizing.

You'll probably have some issues in the course of doing this. XP is an old system by now, and like your average Microsoft product doesn't like to interact with non-Microsoft stuff. When I did an XP installation on a disk sharing it with an existing Linux system, I had to re-do the booting procedures in order to get back the GRUB boot manager - and with it the possibility to boot into Ubuntu. In addition, since XP can't install on a logical partition (and the installer might not find SATA drives easily either), and since I had already "used up" all my primary partitions, I had to get rid of my swap partition (freeing up a primary partition slot - you can have maximum four, or three, depending) and later recreate it as a logical one.

Uhm, okay nevermind if all that didn't make sense. Just wanted to say, if you have the option of formatting the drive and installing Windows first and Ubuntu second, that will probably be significantly smoother, even if it will of course mean reinstalling Ubuntu (unless, I suppose, you make an exact copy of the entire system somewhere I suppose, but that's non-trivial.)

What you want to do is possible too though, just be sure to make your backups and if possible have another computer handy to google (or just search these forums) for help when you run into problems. Good luck. ;-)

---

