---
title: "How to apply WoW patch?"
date: 2007-05-23
forum: Gaming &amp; Leisure
---

### Post by KillMeh on 2007-05-23
I downloaded WoW-2.0.12.6546-to-2.1.0.6692-enGB-patch.exe, trying to install with cedega 6 or wine, but installer throws same error - sorry, the installer was unable to start up. you may be out of hard drive space. Tried to google, but found nothing. How to apply that patch?

---

### Post by lakersforce on 2007-05-23
Properly not very helpful, but you should be able to just run it.

---

### Post by Sammi on 2007-05-23
Can you try to launch it in a terminal with the wine command in front and then post the text output it produces here?

---

### Post by GIBson3 on 2007-05-23
I'm having the same issue, This is a 0.9.36 install of wine, when the Message box pops up nothing is said in the terminal.
Dialog box
[IMG]http://villainsrequiem.nrgservers.net/linux/wow-error-dlg.png[/IMG]

Terminal
[IMG]http://villainsrequiem.nrgservers.net/linux/wow-error-term.png[/IMG]

at first I thought maybe it was because I was running the patch from my desktop,  so I copied it over to the "c drive" directory for a second attempt, when that failed I came to look here on the forums, upon noticing I wasn't the only one, I tried a third time for the sake of a [screen shot]("http://villainsrequiem.nrgservers.net/linux/wow-2.0-2.1-error.png") (that's the full screen non forum friendly screen shot)

The Patch was downloaded from FileFront.com as the Blizzard Downloader hates me and my hardware. I'm currently copying the file to my local windows box to see if it work there.

---

### Post by cmon on 2007-05-23
> **GIBson3 said:**
> I'm having the same issue, This is a 0.9.36 install of wine, when the Message box pops up nothing is said in the terminal.
Dialog box
[IMG]http://villainsrequiem.nrgservers.net/linux/wow-error-dlg.png[/IMG]

Terminal
[IMG]http://villainsrequiem.nrgservers.net/linux/wow-error-term.png[/IMG]

at first I thought maybe it was because I was running the patch from my desktop,  so I copied it over to the "c drive" directory for a second attempt, when that failed I came to look here on the forums, upon noticing I wasn't the only one, I tried a third time for the sake of a [screen shot]("http://villainsrequiem.nrgservers.net/linux/wow-2.0-2.1-error.png") (that's the full screen non forum friendly screen shot)

The Patch was downloaded from FileFront.com as the Blizzard Downloader hates me and my hardware. I'm currently copying the file to my local windows box to see if it work there.

I had the same problem, but I fixed it by running the patch-file with:  sudo wine name_of_patch_file.exe

---

### Post by hikaricore on 2007-05-23
Though you shouldn't EVER have to run wine as root (with sudo) this is most likely caused by file permissions.

---

### Post by Sammi on 2007-05-23
You should make sure you have read and write permissions for all files and folders in you fake c drive. You should be able to do this very easily with Nautilus (the default file manager).

---

### Post by GIBson3 on 2007-05-23
That was my first thought, ls -l brings up "rw" on all files in my c, Program Files and World of Warcraft files/directories (directories are all drwx, as they should be.).

I'm going to try and find a solution without going the sudo route just so the cause is known, and since I don't believe in liberal use of root permissions :)  I'm far to much of a glutton for punishment :)

---

### Post by GIBson3 on 2007-05-23
Well a big part of my issue maybe that the installer didn't finish to download, the file was 174 of the 256 or so necessary. I'm redownloading it now.

---

### Post by justin whitaker on 2007-05-23
The update file needs to be in your Wine directory with the other patches.

---

### Post by GIBson3 on 2007-05-25
a quick up date.

1) Downloaded new patch file.
2) opened a term changed to the ~/Desktop dir and issued "Wine wow-Stupidly-long-executable-name-goes-here.exe"
3) went and got lunch
4) played WoW 2.1.0 for a while
5) exited to a "nonresponsive" WoW.exe
6) wineserver -k
7) back to work.

so now I'm at least where everyone else is. lol

and no you do not have to execute the patch from the wine directory unless you used the Blizzard downloader(pos that it is)

---

