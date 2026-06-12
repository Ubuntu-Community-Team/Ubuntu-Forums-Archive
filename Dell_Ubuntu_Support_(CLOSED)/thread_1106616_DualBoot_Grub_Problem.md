---
title: "DualBoot Grub Problem"
date: 2009-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Slingshooter08 on 2009-03-25
I have 3 Hard disks, An external with 2 partitions, windows 55g, and Ubuntu 20g. When i boot my computer, Grub loads, i set the option on windows, it attempts to boot, but is unsucessful, it goes back to the grub menu. When i boot ubunutu, I can only see the smaller partition of my bigger external drive, when I usually see all of them. When I open Partiton manager, it sees them as if they are normal. I recently installed KGRUB editor on ubunutu to edit my grub menu. I may have made a mistake in resoring grub on all partitons and drives. I thought that mabe repairing windows would help, but the disk does not recognize that windows is installed and has me type EXIT. 

I need Windows and reinstalling it is almost not an option, i have the cd. i think this may be a simple GRUB fix or I made a big mistake

Thank you in advance
New Ubuntu User

---

### Post by lindsay7 on 2009-03-25
I am no expert at grub problems, but you may want to download "super Grub" from the internet and see if it can fix your problem so that you can windows and ubuntu working. If you just want to get windows working and fix the grub problem later, you can use the original windows install disk or down load a windows recovery disk (vista or xp, both are on the web). With either you can load them do a repair options and run fixmbr.  You can find the instructions on the MS web site, look for a write up on the web.

Hopefully someone who is an expert will look at you post and give you the short cut easy way to fix this.

Here are the web sites.

1.Fix mbr windows xp

[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

2.fix mbr windows vista

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)


3.Super Grub

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by Slingshooter08 on 2009-03-26
I just tried fixmbr alone, and it said it worked, the problem is not gone yet. I thik it said default drive, i have ubunutu set as default, so i will change  it to windows in kgrub, then try again.

---

### Post by lindsay7 on 2009-03-26
The way I understand it, is when you run fixmbr or which ever micrsoft tool it is in vista from the recovery disk for windows. It should set up the mbr again and that should over ride the grub setup.

---

### Post by Slingshooter08 on 2009-03-26
Sorry i did not sate, i have xp and ubuntu 8.10

When i [SIZE="6"]set my default drive to windows[/SIZE], and ran fixmbr, then rebooted the computer, the screen stated GRUB  ... I waited (went to school For several hours) then i got home and nothing had changed. I just restored the ubunut grub from a live cd through the terminal. I will reboot my computer and try opening in xp (if i fixed it)[SIZE="3"][/SIZE] then my next post will be my result.

---

### Post by Slingshooter08 on 2009-03-26
I fixed the Ubuntu not booting problem. But my windows does not boot. Instead of the screen trying to boot windows saying Grub (next line) starting up...  then cycling back to the OS selection screen, it just does not cycle now. I also do not know why the hd (external) is not displaying itself as connected... it can usually be acessed with both Operating Systems.

---

### Post by Slingshooter08 on 2009-03-26
after a long time googling, i fixed it. Here is how

I opened up the repair console... then typed fixboot c (c is the drive with windows on it) Then typed exit ... I restarted... grub loaded and i set to windows, the screen flashed then windows started loading.

Thank you for your help, this is a problem i now have experince fixing.

I am writing this from google chrome in my winodws partiton.

---

### Post by lindsay7 on 2009-03-26
Good for you!! That "fixmbr" is simple after you know how to do it.

---

### Post by Slingshooter08 on 2009-03-26
I just fixed my external drive.. and felt like adding openSUSE... now it is triboot lol

---

### Post by lindsay7 on 2009-03-26
.

---

