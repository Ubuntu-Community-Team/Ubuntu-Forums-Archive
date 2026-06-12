---
title: "Removed Compiz, but $KDEWM still points to it"
date: 2009-01-14
forum: General Help
---

### Post by Sarteck on 2009-01-14
All right, I am by no means a Linux genius, and had to use some tutorial I found on here a year or so ago in order to get Compiz working.  I've decided that I don't really need/want the frills, so I removed Compiz by loading Adept and searching for and uninstalling anything a search on "compiz" revealed.

Unfortunately, this gave me some problems upon logging in afterwards.  See, I got rid of Compiz because I found myself Going to "Run Command" and typing "kwin --replace" all the time upon login.  Now, I -HAVE- to run "kwin --replace" or else I have no window borders, no title bars, etc.

I remember having a similar problem when I was first installing Compiz, but I didn't think I'd have it upon removing it.

After doing a bunch of searching, I found that typing "echo $KDEWM" yields "**/usr/bin/compiz**", even though no such file exists on my computer.

Someone help this poor fool?

---

### Post by BryanFRitt on 2010-06-19
> **Sarteck said:**
> echo $KDEWM" yields "**/usr/bin/compiz**", even though no such file exists on my computer.
Did you ever figure out how to change this?

---

### Post by Chame_Wizard on 2010-06-19
Did you remove everything concerning Compiz?

```
sudo aptiude search compiz
```
If there is an *i* before a package,it's still installed.

---

### Post by BryanFRitt on 2010-06-19
You can do a 'find'(in dolphin or whatever) and look for files containing the text 'KDEWM'
I found mine in 
[FONT="Courier New"]/etc/X11/Xsession.d/25enable-compiz[/FONT]
You can look at the files that it finds with a text editor and figure out what to do next.

---

