---
title: "Special characters in konsole - across ssh"
date: 2006-04-19
forum: Desktop Environments
---

### Post by bistrototal on 2006-04-19
I use Kubuntu 5.10 and use som speciale characters in my language (æøå). They work fine locally on my computer. 

When i ssh to my dreamhost account, something strange happens: Apparently it works fine when i type for example ø at the command line, but when i delete the character, then press enter, i get:
```
-bash: &#65533;: command not found
```
where &#65533; is a square. It is actually possible to backspace twice, after typing one of these characters. 

When i try to read mail with mutt all the special characters is replaced by a square.

I had the same problem when i used putty in Kubuntu and Terminal on a Mac, but it worked fine with putty in Windows.

---

### Post by hayalci on 2006-08-12
This is a problem with the locale settings, does your dreamhost machine support unicode and variables like LC_ALL, LANG are all set to use unicode ?

---

### Post by nilou on 2007-05-18
I have, on release date, upgraded my edgy eft to fiesty fawn.

I'm mainly using my laptop for mail, internet and office applications.

I have expirienced excatly the same "black square with questionmark".  It appears in evolution, in firefox and even nautilus.

It seems like some localisation code is missing in fiesty fawn.  Maybe in gnome?

I'm looking foreward to receiving an upgrade to fix the error.

Kind regards,
Michael Nilou

---

### Post by hayalci on 2007-05-27
You should check for locale and encoding settings, and adjust them according to your language.

---

