---
title: "Any good experiences w/ system restore software?"
date: 2009-03-03
forum: General Help
---

### Post by shateredsoul on 2009-03-03
I'm trying to find a reliable system restore method.. I'd prefer a program that rather than trying to put home on another partition (or any of those complicated methods).

Has anyone had positive experiences with a system restore program?  

Are home user restore and home user back up any good?

Thank you for your time

-shatered

---

### Post by shateredsoul on 2009-03-03
I also found simple backup config and restore... it has 4 stars instead of 3.  Does that mean it's better?

---

### Post by jerrrys on 2009-03-03
there are a lot of popular backup/restore utilities, here are some:

[http://www.clonezilla.org/introduction.php](http://www.clonezilla.org/introduction.php)
[http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)
[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)    to name a few

some in this forum will also say freeNAS is the way to go for simple backup   [http://www.freenas.org/](http://www.freenas.org/)

and im sure others will come along with more suggestions, like
[http://digiwanderlust.blogspot.com/2008/05/howto-backup-and-restore-configuration.html](http://digiwanderlust.blogspot.com/2008/05/howto-backup-and-restore-configuration.html)

and a how to   [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

which is best? they all work...its just more like which one you like..

---

### Post by binbash on 2009-03-03
Partimage is a good one

---

### Post by HavocXphere on 2009-03-03
> **shateredsoul said:**
> I'm trying to find a reliable system restore method.. I'd prefer a program that rather than trying to put home on another partition (or any of those complicated methods).

Has anyone had positive experiences with a system restore program?  

Are home user restore and home user back up any good?

Thank you for your time

-shatered
If you're looking for a backup program, then perhaps rdiff-backup(/one of its GUIs). If you want a "complete" backup solutions, then perhaps something like the acronis suite (not free). Or a whole disk backup like Clonezilla.

Not quite sure what you want to do.

---

### Post by shateredsoul on 2009-03-03
Cool thanks everyone! I've decided to give clonezilla a go.

---

### Post by shateredsoul on 2009-03-03
Wait! I forgot to ask... has anyone used any of these? I would like to know if anyone has had to restore their system to a previous point and how was was your experience with these programs if you had to do this?

---

### Post by renebs on 2009-03-03
Jerrys,
That is a great repply, but let me ask one thing, related to the use of rsync in general:

"but can be effectively used to synchronize local directories and supports remote targets in a limited way."

This was taken from the Grsync link you gave.
Is it "OK" to use FUSE+rsync (i.e. mount locally using ssh and use rsync "locally") for backups? 
I am asking that because I have been using rsync for backup of my media library and a very annoying problem is occuring, namely, some files being backed up have "duplicates" with 0kb in the following way:
nameofthefile.mp3
I also get a 
.nameofthefile.mp3
This is very annoying since these .nameofile.mp3, in general, are recognized by media library players (e.g. amarok) but, of course, won't play...

So to make things clear doe anyone have any advice on:
- Can one use FUSE mount+rsync, or that's just bad practice/stupid?
- Any idead how to not have .files after a backup?

---

### Post by hexanol on 2009-03-03
Clonezilla is not the most user-friendly software. First, its documentation is rather on the poor side. Then, it has somehow a good amount of options (fortunately, you can usually leave the defaults one). I'm using it, I find it quite useful, but I had to do some tests to be sure I would be capable of restoring a file-system/partition exactly like it was before (by default, it restore it correctly but it mess a bit with grub if you don't change the default options). That's what I had to say.

Also, if I use clonezilla, it's to save the image of a Windows OS. I personally don't use it on my Linux-based OS, since those are free (with free software in it) and easy to reinstall. On those partitions, I only save the files in my /home directory with rsync actually.

My backup strategy might not be perfect, but hey, it's better than nothing, and I know I can actually restore my data if something fails, so at the end, it's fine.

---

### Post by jerrrys on 2009-03-03
Jerrys,
That is a great repply, but let me ask one thing, related to the use of rsync in general:

"but can be effectively used to synchronize local directories and supports remote targets in a limited way."

cant help you on that one bud, dont use it.  and yes, Clonezilla is a pain to figure out, but once you figure out that..and also freeNAS; im looking into this one, check this out..[http://www.freenas.org/downloads/docs/user-docs/FreeNAS-SUG.pdf](http://www.freenas.org/downloads/docs/user-docs/FreeNAS-SUG.pdf)

---

### Post by shateredsoul on 2009-03-03
What's a good way to test clonezilla out? Maybe installing ubuntu on virtual box and then seeing if I can restore the same system with setting on virtual box?

---

### Post by ibuclaw on 2009-03-03
Probably in a VM would be best to test out, yes...
I remember doing the near exact same thing when I came about practicing imaging a hard drive in a VM before doing it for real on my family's old desktop.


On a side note:
I prefer Remastersys myself ... setup my system, and back it up to a bootable/installable DVD.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

Regards
Iain

---

### Post by shateredsoul on 2009-03-04
I have a question.. I installed simple backup config from the add/remove option on Ubuntu.  I tried to set it up to save it to a dvd.... and clicked back up... nothing happened.  I then tried to change it to a folder on the desktop I made.. nothing happened.

It said it was running in the background. So I figured that maybe it was running but I just couldn't tell.  So I left it on overnight.  I wake up this morning check the folder and it's empty.

I tried downloading that last program that was mentioned (where you have to edit the file to download the program), but I couldn't edit that file because I am not root.  Is there any advice on how to download that program (remaster system) without having to edit any files? If not, how can I make it so I can save changes to /etc/apt/sources.list ?

-shatered

---

