---
title: "MozActivX...what do I do?"
date: 2006-02-24
forum: Gaming &amp; Leisure
---

### Post by brinley on 2006-02-24
When ever I go to load BearShare.exe or GunZ:The Duel.exe I always get a message saying I need to install MozDirectX, I click OK, the download bar goes all the way accress then just freezes. When I look at the terminal I get this message, 'wine: could not load L"C:\\windows\\temp\\mozactivex" as Win32 binary' ...any help would be greatly appreciated, oh forgot to mention, I have been on Linux for 2 days, loving it, but it's a bit complicated :p

---

### Post by aljones15 on 2006-02-25
there's a bug in wine where it doesn't download mozcontrol correctly automatically. you need to d/l itself 

you can get it here:
[http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz]("http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz")

then go to your home directory
and move moz into your wine directy's program files (you might need
to tell ubuntu to make .wine visible it's hidden by default.)
cd .wine
cd drive_c
cd "Program Files"
and then I forget how to install it.
shit.
anyway, check winehq.com and their faqs.
I know the steam install faq mentions how
to install mozcontrol.
ok found it run

"#regsvr32 mozctlx.dll"

try that without the # sign and maybe
with wine 
peace,
A

---

### Post by brinley on 2006-02-25
This is what i get when i type it in [http://i1.tinypic.com/oj2wm0.png](http://i1.tinypic.com/oj2wm0.png)

---

### Post by aljones15 on 2006-02-26
never seen that before. are you in the directory where mozcontrol is?
it went fine with mine. have no idea. try asking on the winehq boards.
they might know.

peace,
A

---

### Post by aljones15 on 2006-02-26
also look at the wine boards steam install and scroll down.
apparently that mozcontrol I linked to has a virus.
there's a newer moz d/l
w/o it anx probably better instructions too.

-
A

---

