---
title: "[SOLVED] Help! Firefox messed up my text completely! URGENT"
date: 2008-12-10
forum: General Help
---

### Post by Fzang on 2008-12-10
Look at the attachment:

What the heck?? Why and how? It just happened a while ago

---

### Post by Zorael on 2008-12-10
Dirty Dane!

Do you have a **~/.fonts.conf** file? If so, try renaming it to something else and restart Firefox.

---

### Post by Fzang on 2008-12-10
Heh, I'm joking around :p

Well, I looked and I didn't find any .fonts.conf anywhere

I'm on 8.10 if that matters

Should I do a complete removal of firefox?

---

### Post by fooman on 2008-12-10
second time today i've seen a thread for this.

see if you have "pango-graphite" installed.  if so...remove it.  in a terminal,  type or copy/paste the following:

```
sudo apt-get remove pango-graphite
```


edit: close firefox before running the command or it may not work.

---

### Post by josemaster2228 on 2008-12-10
> **fooman said:**
> second time today i've seen a thread for this.

see if you have "pango-graphite" installed.  if so...remove it.  in a terminal,  type or copy/paste the following:

```
sudo apt-get remove pango-graphite
```


edit: close firefox before running the command or it may not work.

i tried your code it didn't work i installed the 6760 font package 
[http://www.gnome-look.org/content/show.php/6%2C760+Fonts?content=9883](http://www.gnome-look.org/content/show.php/6%2C760+Fonts?content=9883) 
when i remove the fonts from my .fonts Firefox goes back to normal put them back in this happens having all those fonts is not necessary but it is cool

---

### Post by Fzang on 2008-12-15
Yup, found the pango-graphite somewhere on google as well

Strange... anyways, it's fixed now :D sorry for the late reply

---

