---
title: "Storage space - How to delete root trash?"
date: 2009-04-10
forum: General Help
---

### Post by ed-koala on 2009-04-10
I'm having a problem with root trash.  The properties of the folder tell me it's taking up 250+ gb.

I tried to delete the files using sudo nautilus, but all that happens is I get another copy to replace it with its extension lengthed (ie 6.2 becomes 6.2.2).

Is this really taking up that much space?  and how do I make it delete or use less space?

---

### Post by pavel989 on 2009-04-10
dont exactly remember the dir, but do a google search for the root trash dir, cd over there nd remove everything

should be something like rm --preserve-root -r ./dir

or u can check out shred.

---

### Post by utnubuuser on 2009-04-10
Hi -- I think in order to get the root nautilus, you do "Alt+F2", then run: gksu, then nautilus. (gksu is used for running graphical apps in root mode).

Also, you can add a "delete" function to your right click by going through Nautilus>>Edit>>Preferences>>Behaviour>>Add "delete" to menu.

---

### Post by drs305 on 2009-04-10
I wrote a guide about the trash system that should answer your questions:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")
It also details other space-hogging items and ways to troubleshoot them.

What you are probably doing is just hitting DELETE, which moves it to .... the trash. Use SHIFT-DELETE to wipe it out completely. Be careful - anything deleted with SHIFT-DELETE is not recoverable, especially important when using sudo/gksudo.

---

### Post by khelben1979 on 2009-04-10
If you open up a graphical shell with super user priviliges, then you just need to go inside this path:

```
trash:/
```

and remove the files. (works with KDE, but there should be something similar with Gnome)

---

### Post by glotz on 2009-04-10
It's exactly the same in GNOME.

---

### Post by khelben1979 on 2009-04-10
> **glotz said:**
> It's exactly the same in GNOME.

Aha! I thought so, but wasn't sure. :)

---

### Post by ed-koala on 2009-04-10
Thank you one and all!  Using SHIFT-DELETE worked fine.  Almost 3000 files, now the big question ... WHY is this garbage not getting deleted (by ubuntu, it's certainly an obvious flaw).

---

### Post by CatKiller on 2009-04-10
> **ed-koala said:**
> WHY is this garbage not getting deleted (by ubuntu, it's certainly an obvious flaw).

Because you're running Nautilus as root far too much and you keep sending things to the Deleted Items folder?

---

