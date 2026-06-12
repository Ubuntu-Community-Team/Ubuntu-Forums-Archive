---
title: "Adobe mozilla plugin not working in firefox"
date: 2006-06-04
forum: Desktop Environments
---

### Post by 18nikko on 2006-06-04
Hi I installed adobe and the adobe mozilla plugin. If I go to a link that is a pdf
I get a blank page. I checked and there is a link to nppdf.so in /usr/lib/firefox/plugins. However under prefrences->downloads->download actions there is no entry for pdf. I have tried reinstalling everything. anyone else having this problem?

Thanks
Nicholas

---

### Post by tonyr on 2006-06-04
I don't know why yours isn't working, but I have the **mozilla-acroread** package 
installed and I see **nppdf.so** in several places:

/usr/lib/netscape/plugins-libc6/nppdf.so
/usr/lib/mozilla-snapshot/plugins/nppdf.so
/usr/lib/mozilla-firefox/plugins/nppdf.so
/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
/usr/lib/mozilla/plugins/nppdf.so

EDIT:   Type **about: plugins**  in the URL window and see what it says
(no space between **:** and **p**.

---

### Post by Toddy on 2006-06-04
The nppdf.so file appears to be broken with Firefox 1.5.  This thread tells you how to correct it:

[http://www.ubuntuforums.org/showthread.php?p=951277#post951277]("http://www.ubuntuforums.org/showthread.php?p=951277#post951277")

---

### Post by tonyr on 2006-06-04
...and here's another thread about how to fix it...
[http://www.ubuntuforums.org/showthread.php?t=187973]("http://www.ubuntuforums.org/showthread.php?t=187973")

---

### Post by 18nikko on 2006-06-04
Thanks,
That is probably my problem. I wonder why those didn't come up when I searched, hmmm.

Nicholas

---

### Post by Hugo Magic on 2006-06-12
Hi! I have the new nppdf.so file , but when I try to put it in place of the old nppdf.so file, it just does not allow me to do anything. I looked at the properties of the old nppdf.so file, and the permissions are all in gray, so I'm unable to replace it for the new one. 
Is there a way around it? 
I'm usin xubuntu 6.06 
Cheers!

---

### Post by Hugo Magic on 2006-06-14
Hi guys!  I found out already how to replace that nppdf.so file. I had to put this in the terminal 'sudo thunar' otherways I would not be able to delete that file. I hope this helps someone else who is a newbie like me.

Cheers!

---

