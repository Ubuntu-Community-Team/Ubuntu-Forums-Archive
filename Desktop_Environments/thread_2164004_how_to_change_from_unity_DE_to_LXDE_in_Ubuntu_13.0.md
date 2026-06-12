---
title: "how to change from unity DE to LXDE in Ubuntu 13.04"
date: 2013-07-20
forum: Desktop Environments
---

### Post by hotwaxdripping on 2013-07-20
I did a wubi.exe install of Ubuntu 13.04 on a windows xp computer and I really like Linux over windows.  But I'm trying to squeeze a little faster performance out of my computer (Dell Optiplex 745 with Core 2 duo 2.13ghz cpu and 8Gb of DDR2.) by switching to LXDE.   I tried ```

sudo apt-get install lubuntu-desktop
```

I asked me for the CD I used, but I used and extracted winrar file.  the exact response I get in terminal is ```
Media change: please insert the disc labeled
 'Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)'
in the drive '/media/cdrom/' and press enter
```

am I having problems because I did a wubi.exe install?  How do I switch to the lighter weight LXDE desktop?  Thanks for your support (the Linuc community is great!)

---

### Post by snowpine on 2013-07-20
You should uncheck the box for the CD-ROM in your Software Sources so that your Software Center can download the packages from the internet. 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by mysteriousdarren on 2013-08-09
I'd do a clean install of Lubuntu and go from there. Wubi can run into problems and has not worked for me very many times.

---

