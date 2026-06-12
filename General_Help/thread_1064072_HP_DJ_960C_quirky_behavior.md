---
title: "HP DJ 960C quirky behavior"
date: 2009-02-08
forum: General Help
---

### Post by mk4mzid on 2009-02-08
Having issues with my printer, HP Deskjet 960c. Works fine under WinXP and somewhat works under Xubuntu 7.10.
I can print documents via cmd line with $ lp file.txt, but it's kind of hokey...prints a line, then pauses a few seconds, then prints another line, then pauses again, etc. But it does print the doc.
If I go to the file in Thunar and open the file with Mousepad, click File > Print, the Xfprint screen pops up, but when I click print, it doesn't do anything. Doesn't print, and the Xfprint window hangs, have to kill the process.
Also at times when I try to print something, the print/pause issues happens, then my mb beep goes on a constant tone and my whole pc locks up forcing a hard reboot.
This morning I installed the latest HPLIP ([http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)) and was able to print the test page no problem, no weird print/pause issues.
I also played around with CUPS via [www.cups.org](www.cups.org) and printed a good test page from there as well.

Any ideas what might be the issue or where I can start troubleshooting? I must admit, printing is NOT my strong suit.
When I installed HPLIP it also updated several pkgs, so that had my hopes up, but the problems persist.

Thanks for your time!
mk

---

### Post by mk4mzid on 2009-02-14
So I came across bug 211335, [https://bugs.launchpad.net/ubuntu/dapper/+source/xfprint4/+bug/211335]("https://bugs.launchpad.net/ubuntu/dapper/+source/xfprint4/+bug/211335")
and saw I didn't have a2ps installed. I installed that and now I can print from mousepad...the xfprint windows connects. 
However it's not wrapping lines, even though I deselected 'cut long lines' in the xfprint input tab. It just cuts off the end of sentences. Will keep playing with it...and try to get my HP Laserjet 4 Plus set up.

---

