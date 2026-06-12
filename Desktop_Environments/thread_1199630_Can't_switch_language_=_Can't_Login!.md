---
title: "Can't switch language = Can't Login!"
date: 2009-06-29
forum: Desktop Environments
---

### Post by Geordino on 2009-06-29
I have Ubuntu 8.10 along with Windows XP installed on my PC.
On Ubuntu I have 2 languages(English and Arabic), English is the default language.

yesterday I was working on Ubuntu, but today out of the sudden, when I start Ubuntu, the default language in the login screen is Arabic.

The problem is that I can't change the language  which means I can't enter my user name and password which are in English.

I tried Alt+Shift, I tried "Select language.." from the login screen menu.. but nothing changes, Ubuntu is stuck to Arabic.

the strange thing is that I didn't touch the language settings yesterday, I didn't install anything.. I was just on the internet and using some editors!

How can I fix this? 
If I can't get it to work, can I get my files which are stored in Ubuntu file system back?

thank you

---

### Post by scrooge_74 on 2009-06-29
Try reconfiguring locales

[http://www.justlinux.com/forum/showthread.php?t=150007](http://www.justlinux.com/forum/showthread.php?t=150007)

Also from command line (to get there press press CTRL + ALT + F1)

sudo apt-get instal language-pack-en language-pack-gnome-en

---

