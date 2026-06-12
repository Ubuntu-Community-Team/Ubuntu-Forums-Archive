---
title: "Firefox Fonts Problem"
date: 2008-12-10
forum: General Help
---

### Post by Thura on 2008-12-10
Well,I messed up my firefox ...
Now firefox is not displaying fonts correctly ..
Take a look at the picture ...

[IMG]http://img262.imageshack.us/img262/4526/fuckga6.png[/IMG]

Now, I wanna get my firefox back with default settings ...
I have tried removing firefox completely including settings ...
and reinstalled ...
But, it is the same ...
I also tried removing ubufox, xulrunner firefox-gnome-support ... and reinstall again ...
It is the same ...

I installed any other firefox-based browsers, like abrowser, galleon ..
They displayed the same ...

I deleted eveything , folders and files, named firefox, by searching with locate ... /etc/firefox ... /etc/firefox-3.0-4 ..... /var/fire ... ~/.firefox ...
I deleted everything with the name "firefox" ...
Then I reinstalled firefox ...
It is the same ...

Now, I am using Opera ...
But I need firefox  !!!
Any idea ?

---

### Post by fooman on 2008-12-10
to get firefox back to defaults (first back up your bookmarks!)...close any firefox that is open,  then go to places > home folder

in the toolbar, click "view" and put a check next to "show hidden folders"

find the .mozilla folder,  right click on it and choose "move to trash".

open firefox.  hope that helps.

---

### Post by Thura on 2008-12-10
I already tried that before ...
But the same ..
And my problem is that firefox is displaying large gaps between fonts ...
I can't change fonts ...

Thanks anyway ...

---

### Post by fooman on 2008-12-10
almost looks like some sort of composting setting...have you tried turning off desktop effects if they are on?

system > preferences > appearance > visual effects ....try setting to "none".

---

### Post by Thura on 2008-12-10
Still the same ..
I also changed the system font for applications ...
So, firefox changed its fonts ..
The only problem is that firefox is displaying large gaps between each word ...

---

### Post by fooman on 2008-12-10
does this seem similar:

[http://ubuntuforums.org/showthread.php?t=839221](http://ubuntuforums.org/showthread.php?t=839221)

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/247129](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/247129)

...try removing "pango-graphite" if it is installed (close firefox first):

```
sudo apt-get remove pango-graphite
```

---

### Post by Thura on 2008-12-10
Wow !!!
You are a life-saver ...
I was planning a sucide if firefox is not gonna work ...
Thanks a lot ...

---

