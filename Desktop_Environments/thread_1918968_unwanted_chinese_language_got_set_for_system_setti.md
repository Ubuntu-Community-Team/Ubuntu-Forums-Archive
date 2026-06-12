---
title: "unwanted chinese language got set for system settings"
date: 2012-02-02
forum: Desktop Environments
---

### Post by jamesbon on 2012-02-02
Hi,
yesterday I was discussing on ubuntu users list as how to type in libreoffice
in Hindi (Indic language) on the following thread
[https://lists.ubuntu.com/archives/ubuntu-users/2012-February/256944.html](https://lists.ubuntu.com/archives/ubuntu-users/2012-February/256944.html)
and a package installation problem
[https://lists.ubuntu.com/archives/ubuntu-users/2012-February/256922.html](https://lists.ubuntu.com/archives/ubuntu-users/2012-February/256922.html)
as suggested by some members I have been doing changing in system
settings.How ever today morning when I did a reboot
I am unable to see English as my default language.My system is showing
some Korean or Chinese language which I do not understand.
I had asked the question (that I just want to use libreoffice for a
particular document in Hindi) what happened is even gmail is opening
in chinese language.
The system settings folder etc is also opening in chinese I am unable
to use the system now.
Have uploaded the snapshots here please have a look upon a reboot
asked to rename all folders
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704405897276606450](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704405897276606450)
gmail opening in chinese
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704406102859334402](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704406102859334402)
this is how menu on my system looks half english and half chinese
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704407869479955202](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704407869479955202)
if you notice in third snapshot the calendar and menu is appearing in chinese.

I want the original US english menus folder names back.I just wanted
to type a document with Lohit Hindi font in Libreoffice.
Ubuntu 11.10 (I do not use Unity only Gnome desktop. I had installed
gnome-session-fallback long time back and had been using the same).

How do I get back to all english submenus and english folder names.I have a US English Keyboard and I use only US English.Some how this thing which is now set is unwanted.

---

### Post by bluexrider on 2012-02-02
Alt+F2 

```
gnome-language-selector
```

Choose your language and select apply system wide.

---

### Post by jamesbon on 2012-02-02
After your suggestion I openened the gnome-language-selector here are the snapshots.What I could not understand is what to do next here are the snapshots where I was stuck up
snap1 
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704443014619612178](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704443014619612178)

snap2 
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704443092135311202](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704443092135311202)

I feel I have done the steps you mentioned to apply system wide correctly but there was no change in subsequent reboots.
I noticed in my $HOME/.profile
```

export LANGUAGE="zh_CN:en"
export LC_MESSAGES="zh_CN.UTF-8"
export LC_CTYPE="zh_CN.UTF-8"
export LC_COLLATE="zh_CN.UTF-8"
```
which is wrong.

---

### Post by jamesbon on 2012-02-02
I noticed in files
/etc/environment
$HOME/.profile
following lines were present
> 
export LANGUAGE="zh_CN:en"
export LC_MESSAGES="zh_CN.UTF-8"
export LC_CTYPE="zh_CN.UTF-8"
export LC_COLLATE="zh_CN.UTF-8"

and in /etc/default/locale only US English line was present as you can
see this snapshot
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704438714062026210](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704438714062026210)

I went to those files and deleted these extra lines of Chinese
Language now I am able to resolve this problem and things are back on
track.
However specially want to mention that gnome-language-selector did not
helped at all.
Sharing this for future archives hope this solution will help some one
in future.

---

### Post by bluexrider on 2012-02-02
Interesting. For future reference check the local settings also apply system-wide and reboot.

---

