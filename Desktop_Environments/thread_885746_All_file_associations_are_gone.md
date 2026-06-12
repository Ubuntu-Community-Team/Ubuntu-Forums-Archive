---
title: "All file associations are gone"
date: 2008-08-10
forum: Desktop Environments
---

### Post by cyrus_the_virus on 2008-08-10
Hi,

In my ubuntu 8.04 installation the file associations are broken for basically every filetype. If I double click on a file (a jpg for example) it says there's no applications installed for this file type. When right click on the file and do a open with...-> image viewer it works and remembers it. But nautilus doesn't show any preview of picture or video files (not even after I restored the file association with 'open with')
Also I noticed all mp3 files have a executable icon instead of the usual mp3 icon in nautilus.

I tried to create a new user account and login under that but I have the same problem then.

Any ideas what could cause this and how to fix it? 

Thanks,
Marty

---

### Post by cyrus_the_virus on 2008-08-11
I have noted some other 'weird things' that might be related to the problem:
- If I drag an program from the applications menu to my desktop I get a .desktop file on the desktop with a textfile icon instead of a normal shortcut with an application icon
- On my ntfs partition a lot of files are executables
- All files have default text file or exe icons instead of an icon that fits the file type (picture have picture icons...etc). Also there a no previews available in nautilus (I have set nautilus to make *always* previews of files up to 100 MB)


Can anybody help me?  I'm using ubuntu 8.04 64 bit and I have installed all updates.

Thanks,
Marty

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by SoccerCore11 on 2008-08-31
I have this exact same problem, any help would be greatly appreciated.

---

### Post by lvlo on 2008-08-31
I had problem like this some time ago, for more info see [**this thread**]("http://ubuntuforums.org/showthread.php?t=868218").

Run this in terminal:```
sudo update-mime-database /usr/share/mime
```
and maybe one more command:```
update-mime-database ~/.local/share/mime/
```

---

### Post by kleskjr on 2009-11-03
have the same problem but this solution doesnt work for me. Did what lvlo said but nothing happened

---

### Post by lvlo on 2009-11-03
If you are running Karmic, check these threads:

[http://ubuntuforums.org/showthread.php?t=1284721](http://ubuntuforums.org/showthread.php?t=1284721)
[http://ubuntuforums.org/showthread.php?t=1284510](http://ubuntuforums.org/showthread.php?t=1284510)

---

