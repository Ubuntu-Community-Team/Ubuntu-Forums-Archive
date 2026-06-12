---
title: "Can I use cedega to play previously installed games?"
date: 2006-02-19
forum: Gaming &amp; Leisure
---

### Post by rogeriovinhal on 2006-02-19
I have a dual boot machine with Windows and Ubuntu, and all my games are installed in a Windows FAT32 partition.

When I use Wine, I can run some games in my windows partition in Linux, but in Cedega I can only run games I installed in it.

Is there a way to run my games from my Windows partition without having to uninstall them?

---

### Post by jnthornh on 2006-02-19
You can run executables directly with cedega from the command line.

---

### Post by rogeriovinhal on 2006-02-19
Can I?

I just tried and it opened the cedega menu and nothing happenned...
Then I included the ".exe" to the command, and it said this:

/home/roger/.cedega/.winex_ver/winex-5.0.3/winex/bin/wine: can't exec 'moh_Breakthrough.exe': error=21

This happens to all games I try to run...

---

### Post by rogeriovinhal on 2006-02-21
up.

---

### Post by rogeriovinhal on 2006-02-22
up

---

### Post by Perfect Storm on 2006-02-22
Try

man cedega

and

cedega --help

To get the command line options.

---

### Post by LordBug on 2006-02-22
Error 21 is a common and known error from Cedega.  I would suggest reading the Transgaming forums for troubleshooting this one.

As for running pre-installed, it should work fine from commandline.  Only issue I can see is games looking for information in the now-nonexistant Registry.  Even that can be fixed, it just requires a fair amount of file editing.  So far, I haven't had any serious issues with this.

---

### Post by NicePics13 on 2006-02-22
Error 21 appears when you don't have the partition mounted with the *exec* option or just mounted with the defaults.
You can change this in your ***/etc/fstab*** file.

_Example_

I have a Windows FAT32 partition for my games mounted like this:

[COLOR="RoyalBlue"]**/dev/hdd1       /media/hdd1     vfat         rw,user,noauto,exec   0       0**[/COLOR]

---

### Post by flapane on 2006-06-08
i used /dev/sdb1 /media/sdb1 ntfs uid=1000,gid=1000,nls=utf8,auto,ro,exec,users 0 0

but with cedega 5.1:
flapane@a64:/media/sdb1/Programmi/Diablo II$ cedega Game_c                         rk.exe
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq                          failed: No such file or directory
/home/flapane/.cedega/.winex_ver/winex-5.1.4/winex/bin/win                         e: can't exec 'Game_crk.exe': error=21

---

### Post by flapane on 2006-06-16
bump

---

### Post by chadk on 2006-06-16
I haven't had any luck running anything that was already installed (and not linux native) without first installing it through cedega.. except City of Heroes but those results are still in debate.

---

### Post by flapane on 2006-06-16
in your opinin where could the problem be located?

---

### Post by justin whitaker on 2006-06-16
[QUOTE=flapane]in your opinin where could the problem be located?[/QUOTE]

Well, looking through the Cedega forums, it seems like mounting a drive to execute the game doesn't really work. Also, Cedega is a bit dumb: it seems to looks in the same drive you are executing for things like ALSA. That may be why it is throwing all those errors. 

Here's what I would do: copy the entire game folder over to your linux partition, and try to execute it there.

---

### Post by wishyjr on 2006-09-11
hey guys, do any of you guys know if there are any means to say add in reg keys into the 'fake' registry on cedega? that would be handy.

i've quite a few pre installed games working with cedega but some (i.e. FFVII) give me a 'can't find reg key' error. thanks

---

