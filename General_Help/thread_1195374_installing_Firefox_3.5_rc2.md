---
title: "installing Firefox 3.5 rc2"
date: 2009-06-23
forum: General Help
---

### Post by geovino on 2009-06-23
How to install Firefox 3.5 rc2 ? 

Its a .tar.bz2 file.

---

### Post by TheLions on 2009-06-23
extract it somewhere (eg. /home/user) and run firefox by double click. 

if you really want to completely integrate you'll need to install it by compilation or some other method that I'm not aware of.

And change shorcuts in your menus

---

### Post by geovino on 2009-06-23
> **TheLions said:**
> extract it somewhere (eg. /home/user) and run firefox by double click. 

if you really want to completely integrate you'll need to install it by compilation or some other method that I'm not aware of.

And change shorcuts in your menus


won't let me extract to home/usr.

And it won't open in downloads folder either. I've done this before. I can't see why it won't work this time.

I'll just wait until Ubuntu has it in their repos. 

I'm running it on my other PC running Fedora 11 and it's very good. Hope Ubuntu can get it soon.

---

### Post by TheLions on 2009-06-24
> **geovino said:**
> won't let me extract to home/usr.

And it won't open in downloads folder either. I've done this before. I can't see why it won't work this time.

I'll just wait until Ubuntu has it in their repos. 

I'm running it on my other PC running Fedora 11 and it's very good. Hope Ubuntu can get it soon.

don't extract to home/usr, you must extract it to '/home/<your_username>/firefox/' where <your_username> is a name which you picked while installing Ubuntu, also jou can see it in Terminal. It has this format: <your_username>@<your_computer_name>:~$

---

### Post by geovino on 2009-06-24
It is in my home/davek directory. but when I click on what I think it its run file, nothing happens. what file do I click on to open it?

---

### Post by jdeppel on 2009-06-24
Firefox 3.5 RC2 is also available in the repositories.
firefox-3.5

---

### Post by geovino on 2009-06-24
> **jdeppel said:**
> Firefox 3.5 RC2 is also available in the repositories.
firefox-3.5

Thanks. That solves the problem. :)

It's listed as Shiretoko

---

### Post by lovinglinux on 2009-06-24
> **jdeppel said:**
> Firefox 3.5 RC2 is also available in the repositories.
firefox-3.5

Firefox 3.5 form the repositories is actually 3.5b4pre, not rc2.

There is an easy way to install the rc2 and keep it updated with latest releases, which is to install [Swiftfox](http://getswiftfox.com/index.htm). It uses the latest version of Firefox and has it's [own repository](http://getswiftfox.com/deb.htm). Swiftfox is installed side-by-side with Firefox, but shares the user profiles.

---

