---
title: "What happened to ctrl alt backspace?"
date: 2009-05-14
forum: General Help
---

### Post by Holonet on 2009-05-14
What the title says.  In recent months I've noticed this no longer kills X and restarts it.  At first I thought it might be a bug, but it's not working on either the last version or a fresh install of 9.04.  What happened to it?  Is there another key combo for it now?...and if so, why?

---

### Post by Locutus_of_Borg on 2009-05-14
add
        Option "DontZap" "false"
to ServerLayout section of xorg.conf, then restart X with sudo killall X

---

### Post by binbash on 2009-05-14
[http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html](http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html)

---

### Post by LoneWolfJack on 2009-05-14
How can someone accidentally push three buttons at once? 

I find it odd that the "fix" was to disable a useful function and to ask people who would like it back to mess with a core file that can leave your system crippled if edited in the wrong way.

---

### Post by WIGGMPk on 2009-05-14
Lame + 1

What is more lame is the people that "accidently" press three very specific buttons so many times that its become a "problem" for "average" users.

If you dont feel comfortable editing the xorg.conf file, you can follow these steps instead:

```
sudo apt-get install dontzap
```
than just do this:
```
sudo dontzap --disable
```

---

### Post by khelben1979 on 2009-05-14
> **LoneWolfJack said:**
> How can someone accidentally push three buttons at once? 

I find it odd that the "fix" was to disable a useful function and to ask people who would like it back to mess with a core file that can leave your system crippled if edited in the wrong way.

If I were an Ubuntu user myself, I would probably switch to another Linux distribution if there wasn't a way to reverse this fix.

---

### Post by Locutus_of_Borg on 2009-05-14
> **khelben1979 said:**
> If I were an Ubuntu user myself, I would probably switch to another Linux distribution if there wasn't a way to reverse this fix.
this isnt an ubuntu thing

this was implemented by the Xorg devs

---

### Post by khelben1979 on 2009-05-14
> **Locutus_of_Borg said:**
> this isnt an ubuntu thing

this was implemented by the Xorg devs

I see.

---

### Post by dcstar on 2009-05-14
> **Locutus_of_Borg said:**
> this isnt an ubuntu thing

this was implemented by the Xorg devs

Hey, never lets the facts get in the way of a whinge about a distro..... ;)

Funny how 2 minutes reading the 9.04 release notes would have had someone seeing this "issue" listed and the simple solution provided as well.

---

### Post by cmost on 2009-05-14
If you don't want to fiddle around with the dontzap crap, you can always use the alternative key sequence:  ALT + 'Sys Req' + K

Works a treat!  :-)

---

### Post by khelben1979 on 2009-05-15
> **cmost said:**
> If you don't want to fiddle around with the dontzap crap, you can always use the alternative key sequence:  ALT + 'Sys Req' + K

Works a treat!  :-)

Then maybe they will disable this too in a future release, then. :-$

---

