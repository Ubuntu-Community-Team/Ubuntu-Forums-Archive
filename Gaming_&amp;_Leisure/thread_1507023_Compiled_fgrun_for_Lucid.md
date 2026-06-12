---
title: "Compiled fgrun for Lucid"
date: 2010-06-11
forum: Gaming &amp; Leisure
---

### Post by nidheeshdas on 2010-06-11
I've successfully compiled fgrun for lucid.

it requires fltk, openscenegraph etc
:lolflag:

---

### Post by scotty64 on 2010-07-05
Thanks a lot! Many people are missing fgrun in the repos - and I do not understand why such a sophisticated flight sim like FlightGear still has no proper and easy launcher like fgrun built in.

---

### Post by bluechile on 2010-07-17
I get the error below when I try and unzip it with archive manager.

```
Archive:  /tmp/fgrun_1.5.2-1_i386.deb.zip
[/tmp/fgrun_1.5.2-1_i386.deb.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of  /tmp/fgrun_1.5.2-1_i386.deb.zip or
          /tmp/fgrun_1.5.2-1_i386.deb.zip.zip, and cannot find  /tmp/fgrun_1.5.2-1_i386.deb.zip.ZIP, period.
```

---

### Post by nidheeshdas on 2010-07-20
i;m sorry;

i'll re-upload soon.

---

### Post by FokkerCharlie on 2010-08-07
Hi

Did you get around to re-uploading?  I would really like this!

Charlie

---

### Post by FokkerCharlie on 2010-08-07
Actually, scrub that... I'm now using fgo, which works great.

Charlie

[http://sites.google.com/site/erobosprojects/flightgear/add-ons/fgo](http://sites.google.com/site/erobosprojects/flightgear/add-ons/fgo)

---

### Post by ubudog on 2010-11-04
If it doesn't work, download it from sourceforge.net:
[http://fgrun.sourceforge.net](http://fgrun.sourceforge.net)

```
cd fgrun
```

```
./configure && make && sudo make install
```

---

### Post by yoda2031 on 2011-02-06
For those who can't unzip this, the reason is simple.  It's not a zip file, it's a .deb.

This was MUCH easier than compiling fgrun, hats off to the OP.  Thanks a million :)

EDIT: scratch that, dependency issues in Lucid.  Recommendation: use Fgo instead.

---

### Post by Sealbhach on 2011-02-07
I use Brisa's script to download and compile the latest Flightgear from Git. It also compiles FGRun for you as well.

[http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu](http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu)

It works pretty well, just download the script, make it executable, make a folder for it (called FlightgearGit or something) and then just run the script.

The only problem I have had sometimes is that when it downloads stuff from Git the connection sometimes hangs up, but I just run it again and it works.

.

---

### Post by yoda2031 on 2011-02-07
Brilliant, thanks a million Sealbhach.  That script does everything I need and more!

---

