---
title: "ANyway having problems with IE6 install with Wine Tools?"
date: 2006-03-12
forum: Desktop Environments
---

### Post by whodat_5 on 2006-03-12
I think Winetools has worked great so far, but for some reason the install screen for Internet Explorer 6 freezes up and the install fails.

I'm using WIne 0.9.9

I have a 566 mhz processor with 512 megs of Ram. My hard drive has a Windows XP with service pack 1 partition, and an Ubuntu 5.1 Breezy Badger partition (along with a small swap partition).

I've been trying to load the Internet Explorer 6 with Wine Tools in order to get a piece of software working, from [www.worldchessnetwork.com](www.worldchessnetwork.com)

The software in question is heavily Microsoft Windows dependant. Normally, a file called wcnweb.exe loads up, looks for updates for the chess software, then allows the file wcnchess.exe to work from a button called Play Chess.

Normally, the wcnweb.exe loads up WCN's home page as well, but all I get is the screen with no information, so I think it's a browser issue.

wcnchess.exe won't load up properly, as I get OLE errors from the Play Chess button; and it says it can't find certain DLL files when trying to implement a "wine wcnchess.exe" in the terminal window.

All the simple things like mshearts.exe and sol.exe work fine.

Perhaps there's some experts out there who could give this software a try and see what they think. I'm pretty sure it's an IE6 issue, but I'm not 100% sure.

Any advice would be helpful. I've been trying this off and on for 5 days and keep running into roadblocks.

Thanks....

---

### Post by jdonat on 2006-03-13
[http://ubuntuforums.org/showthread.php?t=132508&highlight=internet+explorer+wine](http://ubuntuforums.org/showthread.php?t=132508&highlight=internet+explorer+wine)

---

### Post by whodat_5 on 2006-03-15
I did manage to get ies4linux installed and working.

It works fine, but the problem still persists with the World Chess Network software.

I've even added all the dll and dlp files to the Libraries section in winecfg for all the exe files involved with WCN.

The Wine DB has it listed as working, as of January of 2005, but WCN has done some changes in it's software since then.

I'm still stuck.

---

### Post by Sef on 2006-03-15
If you like playing chess, go to redhotpawn.  I play it there on firefox under Ubuntu and have no problems.

[http://www.redhotpawn.com]("http://www.redhotpawn.com")

---

