---
title: "any help on that strange update ?"
date: 2013-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abdorefky on 2013-04-22
i just made recovery because of jupiter program changed some of my power options ,, even after i uninstalled it ;/

i am making the ubuntu update and suddenly that showed up !

first this ..
[IMG][[IMG]http://img12.imageshack.us/img12/1481/screenshotat20130422133.png[/IMG]]("http://imageshack.us/photo/my-images/12/screenshotat20130422133.png/")

i made replace since its a libre and packet tracer 
**now it stoped here !!**

[IMG][URL="http://imageshack.us/photo/my-images/708/screenshotat20130422140.png/"]
[IMG]http://img708.imageshack.us/img708/3390/screenshotat20130422140.png[/IMG][/URL] 
i just dont want to overwrite some dell setting .. 
this ubuntu el customized by dell , looks at this link 
[http://ubuntuforums.org/showthread.php?t=2136677](http://ubuntuforums.org/showthread.php?t=2136677)
 
what should i do now with default.list 

and i dont want to delete original ell setting

---

### Post by oldfred on 2013-04-22
I do not know Jupiter.

And just recently someone was discussing Sputnik and I did not know what that was. I gather it is a ppa for all the fixes needed for Dell systems. And second thread mentions that 13.04 now includes all the changes that the ppa has. 
 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

I normally do clean installs now, but in the past it used to offer to update maintainer's files. I learned I had to make sure I backed up any thing I manually edited that was a system configuration file. Sometimes system would only work with the new version, and sometimes I needed  my changes even in the new version.

---

### Post by schragge on 2013-04-22
Both [dpkg-maintscript-helper](http://manpages.ubuntu.com/manpages/quantal/en/man1/dpkg-maintscript-helper.1.html) and [ucf](http://manpages.ubuntu.com/manpages/quantal/en/man1/ucf.1.html) preserve backup copies of configuration files. No matter how you answer the question (Y/I or N/O), you'll find the other version of the config file in question as one of
```

/etc/gnome/defaults.list.dpkg-new
/etc/gnome/defaults.list.dpkg-old
/etc/gnome/defaults.list.dpkg-backup
/etc/gnome/defaults.list.dpkg-bak
/etc/gnome/defaults.list.dpkg-remove
/etc/gnome/defaults.list.ucf-new
/etc/gnome/defaults.list.ucf-old
/etc/gnome/defaults.list.ucf-dist
/etc/gnome/defaults.list.merge-error

```

---

### Post by abdorefky on 2013-04-23
i did Yes . 

thx for responding oldfred and schragge

---

