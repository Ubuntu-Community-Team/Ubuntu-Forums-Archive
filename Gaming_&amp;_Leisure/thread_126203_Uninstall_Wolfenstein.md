---
title: "Uninstall Wolfenstein?"
date: 2006-02-05
forum: Gaming &amp; Leisure
---

### Post by tblehr on 2006-02-05
How do I remove Wolfenstein: Enemy Territory?  I've installed the main program and the 2 upgrades, but I need to remove them.  I'd appreciate any help! :)

~Terrence~

---

### Post by frodon on 2006-02-06
Delete the folders or run the uninstall.exe. Did you install it using wine or cedega ?

---

### Post by tblehr on 2006-02-06
I just installed it from the .run file.  I can't remember where it installed the folders.  I'm using Ubuntu to run it.

~Terrence~

---

### Post by newuser111 on 2006-02-06
in /usr/local/games/enemy-territory there is an "uninstall" script, assuming thats where you installed it (the default install location)

---

### Post by tblehr on 2006-02-06
Ok, I looked there, but I didn't see anything about uninstalling it.  Sorry i'm a linux noob, trying to learn the ropes! :)  I tryed typing sudo /usr/local/games/enemy-territory uninstall  but this didn't work.  I opened the readme, but didn't say anything about unstalling either.  Thanks for your replys, hope this helps!

---

### Post by newuser111 on 2006-02-06
~/.etwolf

/usr/local/games/enemy-territory

/usr/local/bin/et (single file, not directory)

delete all of those, thats enemy territory

---

### Post by tblehr on 2006-02-06
[QUOTE=newuser111]~/.etwolf

/usr/local/games/enemy-territory

/usr/local/bin/et (single file, not directory)

delete all of those, thats enemy territory[/QUOTE]

I'd do that.  Thanks for everyone's help!

~Terrence~

---

### Post by NESFreak on 2006-03-23
thero also /usr/local/bin/etded and the debian menu entry ( yes et does create an icon) thoug i dont know where it's stored and there s i geas even more than that on your hd (it's installed as root thoug it creates files in your homedir, so i gues also in the homedir of others)
why is'nt there an easy way to do this?

---

### Post by CatKiller on 2006-09-18
> **NESFreak said:**
> thero also /usr/local/bin/etded and the debian menu entry ( yes et does create an icon) thoug i dont know where it's stored and there s i geas even more than that on your hd (it's installed as root thoug it creates files in your homedir, so i gues also in the homedir of others)
why is'nt there an easy way to do this?

I've just had to do this with RtCW (temporary hard drive space issue) and the menu entries are in

/usr/share/gnome/apps/Games/

and

/home/*user*/.local/share/applications/

as .desktop files. The /usr/ files and those in other users' home folders will need to be removed as root. If fact, I had to do **sudo su** to remove the other users' .desktop entries, since sudo doesn't magically overcome the read permissions.

As to why it isn't easier, for most things it is. UT includes an uninstall script. I guess when they were doing RtCW (and ET) they forgot. It's even possible that the install script has an uninstall option, but I couldn't work out which arguments to pass to it to make it do that.

I guess that's what this community is for.

---

