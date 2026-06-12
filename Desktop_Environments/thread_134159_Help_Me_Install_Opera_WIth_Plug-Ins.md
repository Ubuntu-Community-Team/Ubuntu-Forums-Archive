---
title: "Help Me Install Opera WIth Plug-Ins"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Mark76 on 2006-02-21
I've tried following the other threads but either I'm extremely stupid or they're way above me, technically.

It's best if you start by assuming the former

:rolleyes:

---

### Post by Mark76 on 2006-02-21
It'd be nice if I could use the wizard :(

Hint

---

### Post by kaamos on 2006-02-21
Hello!

Since I'm not an Opera user (have it installed, not just a fan of it) I'm not shure what plugins you are referring to.

If you are talking about opera 9, here is how you can install. Open a terminal (Applications->Accessories->Terminal) and copy&paste these commands there.
```
wget http://snapshot.opera.com/unix/9.0-Preview-2/intel-linux/opera-static_9.0-20060206.1-qt_en_i386.deb
```
That downloads opera (I assume you are not on a mac, that version wont work there).
```
sudo dpkg -i opera-static_9.0-20060206.1-qt_en_i386.deb
```
That installs it. You can now start the program with
```
opera
```

---

### Post by JimS on 2006-02-21
...

I just installed Opera successfully
using Automatrix by arnieboy.
see
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
Arnieboy's instructions for installing Automatrix
are fairly easy to follow.
After Automatrix is installed, I checked the Opera box
and it installed.
I don't know about Plug-ins.
I had tried a direct install, but it called for my Ubuntu CD
and my drive had died, so no go there.
I recommend Automatrix.
Check the URL and see if it suites your taste.
[COLOR="Blue"]
JimS
Prostate Cancer Aware
[/COLOR]
...

---

### Post by Mark76 on 2006-02-21
Hmm

mark-williams@ubuntu12345:~$ sudo dpkg -i automatix_5.4-3_i386.deb
Selecting previously deselected package automatix.
(Reading database ... 71826 files and directories currently installed.)
Unpacking automatix (from automatix_5.4-3_i386.deb) ...
Setting up automatix (5.4-3) ...
mark-williams@ubuntu12345:~$ automatix
bash: automatix: command not found
mark-williams@ubuntu12345:~$

---

### Post by Mark76 on 2006-02-21
[QUOTE=Mark76]Hmm

mark-williams@ubuntu12345:~$ sudo dpkg -i automatix_5.4-3_i386.deb
Selecting previously deselected package automatix.
(Reading database ... 71826 files and directories currently installed.)
Unpacking automatix (from automatix_5.4-3_i386.deb) ...
Setting up automatix (5.4-3) ...
mark-williams@ubuntu12345:~$ automatix
bash: automatix: command not found
mark-williams@ubuntu12345:~$[/QUOTE]

Ah!  AutomatRIX! :lol:

---

### Post by Mark76 on 2006-02-21
Boo

mark-williams@ubuntu12345:~$ automatrix
bash: automatrix: command not found
mark-williams@ubuntu12345:~$

---

### Post by arrizaba on 2006-02-21
If you have Automatix installed, just look under "Applications>System Tools>Automatix"
Automatix should be there.
It will also allow you to install very useful multimedia programs which are either difficult of lengthy to install.

---

### Post by Mark76 on 2006-02-21
I just looked and it's not there,  Do I have to restart before the new settings take effect?

---

### Post by TrendyDark on 2006-02-21
You have to download it, here from the forum. (see this thread: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563))

Using Automatix, it's really easy to install Firefox 1.5 and Opera, but the plugins for Opera, unfortunately, are not easy to install, you must place them yourself and such. I love Opera over firefox, because it's faster, but it's too damn much effort to install plugins for it, so I use Firefox 1.5.

---

### Post by Mark76 on 2006-02-21
What's the linux equivalent of a .dll?

---

