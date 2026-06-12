---
title: "Return to Castle Wolfenstein MD5 file"
date: 2009-12-17
forum: Gaming &amp; Leisure
---

### Post by j3rryf4n on 2009-12-17
Hello,
I'm having problem with installing RtCW.
I downloaded it from: [ftp://ftp.idsoftware.com/idstuff/wolf/linux/old/](ftp://ftp.idsoftware.com/idstuff/wolf/linux/old/)
This version: wolfmp-linux-1.1-MP.x86.run


When I start try to run it then it says the following:

$ sudo sh wolfmp-linux-1.1-MP.x86.run
Verifying archive integrity...tail: ”+6” couldn't open to read: No such a file or directory
Error in check sums 2860345088 2466252757


I did MD5 check:

$ md5sum wolfmp-linux-1.1-MP.x86.run
e43f57bf8d8ff51e1f8abbbd3895ccbe  wolfmp-linux-1.1-MP.x86.run


I can't find any MD5 on the internet. What should I do?

---

### Post by j3rryf4n on 2009-12-17
> **kald2009 said:**
> [COLOR=#000000][FONT=Times New Roman][FONT=Arial]Thanks**[SIZE=3][]("http://www.google-add.co.cc")[/SIZE]**[/FONT][/FONT][/COLOR]
???

---

### Post by realzippy on 2009-12-17
Do you have the win32 Wolfenstein CD-ROM, or the Wolfenstein GOTY edition?
If Windows,you have to install single player first:

[http://zerowing.idsoftware.com/linux/wolf/INSTALL](http://zerowing.idsoftware.com/linux/wolf/INSTALL)

---

### Post by j3rryf4n on 2009-12-17
> **realzippy said:**
> Do you have the win32 Wolfenstein CD-ROM, or the Wolfenstein GOTY edition?
If Windows,you have to install single player first:

[http://zerowing.idsoftware.com/linux/wolf/INSTALL](http://zerowing.idsoftware.com/linux/wolf/INSTALL)
Yes, I've my original game. Thanks for the link.

---

### Post by realzippy on 2009-12-17
> **j3rryf4n said:**
> Yes, I've my original game. Thanks for the link.

well,it depends on *which* original....

---

### Post by j3rryf4n on 2009-12-17
> **realzippy said:**
> well,it depends on *which* original....
Wolfenstein 1.0 CD (the first retail), I bought it in 2001.

---

### Post by realzippy on 2009-12-17
> **j3rryf4n said:**
> Wolfenstein 1.0 CD (the first retail), I bought it in 2001.

..so here you go:

[http://ubuntuforums.org/showthread.php?t=54963](http://ubuntuforums.org/showthread.php?t=54963)

files:
[ftp://ftp.idsoftware.com/idstuff/wolf/linux/wolf-linux-1.41b.x86.run](ftp://ftp.idsoftware.com/idstuff/wolf/linux/wolf-linux-1.41b.x86.run)


run:

**chmod +x wolf-linux-1.41b.x86.run**

**sudo ./wolf-linux-1.41b.x86.run**

then run/install wine.Change to your CDROM directory and run:

**wine Setup.exe**  (*if error say "no"*)

pak0.pk3,sp_pak1.pk3,mp_pak0.pk3 have to be copied from
*~/.wine/drive_c/Programme/Return to Castle Wolfenstein/Main*
to
*/usr/local/games/wolfenstein/main*
(or wherever you installed to)
start game:
**wolfsp** or **wolfmp**

wine-wolf stuff can be deleted after installation.

---

