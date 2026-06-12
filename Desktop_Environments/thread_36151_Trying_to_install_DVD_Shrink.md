---
title: "Trying to install DVD Shrink"
date: 2005-05-22
forum: Desktop Environments
---

### Post by YaAqoB on 2005-05-22
Hello.
I'm following the how to at this site...
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)
When its doing the wine setup up I got an error at the end even though it seemed to install ok. The error is as follows:

james@YaAqoB:~$ winesetup
CBase::AutoConf:GetWinInstalls: unable to grep /mnt/WindowsDrv/msdos.sys: child process exited abnormally
CBase::AutoConf:GetWinInstalls: unable to grep /mnt/WindowsApps/msdos.sys: child process exited abnormally

If I go to the next part and try to download the DVD Decrypter instead of having:
open with Wine(default) I have the following:
open with wine-safe(deafult)

I'm to chicken to go any further as I don't want to screw up the install.
This is my first attempt at emulation and don't really know what to do apart from follow the how to word for word.
Any help would be awsum :)

---

### Post by YaAqoB on 2005-05-22
I have reinstalled wine and winesetupk and how when I run the dvd decryptor it has "Open with wine(default)
But it tries to install it to C:\Program Files and thats on my NFTS Windows drive and hense don't work.
Any clues?

---

### Post by YaAqoB on 2005-05-22
I think the problem is that when I run the winesetup its not creating the fake windows part on my ext3 Linux partition.
Any ideas as to what I may be doing wrong here?

---

### Post by angrykeyboarder on 2005-05-22
[QUOTE=YaAqoB]I have reinstalled wine and winesetupk and how when I run the dvd decryptor it has "Open with wine(default)
But it tries to install it to C:\Program Files and thats on my NFTS Windows drive and hense don't work.
Any clues?[/QUOTE]

Have you considered somthing other than DVD Shrink, such as dvd:rip?

[http://www.exit1.org/dvdrip/index.cipp]("http://www.exit1.org/dvdrip/index.cipp")

---

### Post by YaAqoB on 2005-05-22
To tell you the truth I have not.
Does DVDRip compress it to fit on a 4.7gb dvd and keep menus inplace like dvd shrink.
I just really like the way DVDShrink works. Its kinda the last thing to keep me attatched to Windows :) Apart from the games :)
I'll give it a try.

---

### Post by Staesys on 2005-05-22
You might try winetools to help with your wine install.

---

### Post by BLTicklemonster on 2006-09-24
Bingo, Winetools. See the link in my sig about wine, and follow the instructions on winetools. It takes a while (you're installing windows, duh) but it's worth it to get stuff to work. Now if you want to rip dvds, (archiving your own personal dvds you own, no doubt), then try out ripit4me (google it) in wine and see what you think. You need dvdshrink and dvddecrypter installed first (pretty sure, I can't remember 5 minutes ago, so I can't say for sure, lol) then try and see what you think. New encryption means if you buy a dvd, and your kid tears it up, you have to buy a new one. Unless you archive it, then you just pop it in, make a new archive, and put the pristine one back in a safe place! And you need tools for that. Ripit4me works fine.

DVDRip? I have yet to get it to work.

---

