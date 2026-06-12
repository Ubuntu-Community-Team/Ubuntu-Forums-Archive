---
title: "&quot;Gnome-Do&quot; preferences uses foreign language/characters"
date: 2009-03-16
forum: General Help
---

### Post by ubnewbie2 on 2009-03-16
I have added the repositories and installed  the latest gnome-do as per the website at 

[http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu](http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu)

It installs and runs, but the preferences dialog is using a foreign looking character set and language.  Any suggestions on how to fix it would be welcome.

---

### Post by kermiac on 2009-03-17
I also updated the gnome-do plugins today & am experiencing the same issue. I went to the gnome-do IRC channel & the problem is that the "en_AU.po" file was translated wrong. It is currently being worked on/ fixed. It will effect **ALL** people using gnome-do using "**en_AU.UTF-8**" locale.

To see what locale you are using type the following into a terminal

```
echo $LANG
```

If it is **en_AU.UTF-8**, then you will be effected by this. It is currently being worked on (not by me - by the devs)

---

### Post by ubnewbie2 on 2009-03-17
Thanks for the quick advice - look forward to the fix.

---

### Post by nonanano on 2009-05-20
Thanks for letting us know. Do you know where the bug report is so I can vote on it?

BTW.
Trying to change the language to English (US) via
System > Administration > Language Support
and then restarting the session does not have any effect. I actually don't know how to work around this issue, but I though I'd save others the hassle of trying that.

---

### Post by nonanano on 2009-05-20
Here are screenshot that I believe show what the english options are. I found them helpful and I think they are correct:

[IMG]http://opensourcemuse.com/assets/images/gnomedo/preferences.png[/IMG]

[IMG]http://images.maketecheasier.com/2009/02/gnome-do-pref.jpg[/IMG]

---

