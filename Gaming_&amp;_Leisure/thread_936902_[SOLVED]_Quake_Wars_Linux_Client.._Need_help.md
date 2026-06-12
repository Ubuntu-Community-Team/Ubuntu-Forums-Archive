---
title: "[SOLVED] Quake Wars Linux Client.. Need help"
date: 2008-10-03
forum: Gaming &amp; Leisure
---

### Post by Sugi on 2008-10-03
I want to install the linux client of Quake Wars, but I am unsure what version of the linux client I should install.  I am also unsure of what version my dvd is.  It's probably 1.1 or 1.0, but I can't say for sure.

So, my question is:  So should I just install the latest version of Quake War (I think 1.5) or should I install the linux client for Quake Wars 1.0 or 1.1?

Link in here:
[http://zerowing.idsoftware.com:6969/](http://zerowing.idsoftware.com:6969/)

Notice the only full version of Quake War Linux Client is 1.5 and the rest is updates.  Which one should I install?


Thanks,
Sugi

---

### Post by compiledkernel on 2008-10-03
1.5 of course, dvd versioning doesnt matter much.

---

### Post by Sugi on 2008-10-03
Thanks

---

### Post by Sugi on 2008-10-03
When I try to run quake war linux client I get the following error:
```
sudo sh ETQW-client-1.5-full.x86.run 
ETQW-client-1.5-full.x86.run: 1: Syntax error: "(" unexpected
```
I tried it with sudo and without.  I had the Linux Clint within the same folder as Quake War.

Any ideas?


Thanks,
Sugi

---

### Post by Perfect Storm on 2008-10-03
[http://gaming.gwos.org/doku.php/guides:64bit:etqw](http://gaming.gwos.org/doku.php/guides:64bit:etqw)

ignore "sudo aptitude install ia32-libs" if you're using 32-bit of Ubuntu.

---

### Post by Sugi on 2008-10-03
The chmod +x command works.  Thanks.

---

### Post by Sugi on 2008-10-03
How do i uninstall Quake Wars?

---

### Post by Perfect Storm on 2008-10-03
Removing the files. If you installed it by default (/usr/local/games/etqw)

```
cd /usr/local/games
sudo rm -rf etqw
cd /usr/local/bin
sudo rm -rf etqw
cd
rm -rf .etqwcl
```

---

### Post by Sugi on 2008-10-03
I installed it to /home/sugi/.games/
if i just cd to it and rm -rf.  Would It delete everything?  Or would I have to remove something else?

---

### Post by Perfect Storm on 2008-10-03
also .etqwcl
(it's where it store your user prefs.)

If it's in ~/.games you can just do it by point'n'click

---

### Post by Sugi on 2008-10-03
I could not locate the .etqwcl file it's self.  Where would my prefs be? hahah

Sugi

---

### Post by fatality_uk on 2008-10-03
Also a tip for getting more from ETQW under Linux & XP ;)
Maybe an old tip but I just found it so...

From the console, type 
> com_unlockFPS "1"
> com_unlock_timingMethod "0"

That will allow your PC to run as fast as it can under ETQW.
I am now getting 1280x1024x2AA all setting HIGH/Ultra and still get 110fps+

---

### Post by Perfect Storm on 2008-10-04
> **Sugi said:**
> I could not locate the .etqwcl file it's self.  Where would my prefs be? hahah

Sugi

It's hidden.
When a folder or file have a dot infront of its name, it's hidden.

---

### Post by Sugi on 2008-10-06
Artificial Intelligence, I used the search feature, but still nothing.  I kinda just gave up.

Thanks though,
Sugi

---

### Post by Perfect Storm on 2008-10-06
> **Sugi said:**
> Artificial Intelligence, I used the search feature, but still nothing.  I kinda just gave up.

Thanks though,
Sugi

If you didn't start the game, it isn't there.

---

### Post by 3177 on 2011-02-02
I realize this is an old thread, but, I successfully installed ETQW and after creating a profile and trying to start a game, it cuts to the console screen(quakes) and says that no textures can be loaded. Whats going on here?

---

