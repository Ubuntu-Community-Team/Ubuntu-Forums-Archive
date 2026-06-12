---
title: "XF86 Config question"
date: 2009-02-25
forum: General Help
---

### Post by timofthec on 2009-02-25
Ok, well, they say that a little knowledge can be dangerous and I have very little in the way of knowledge ;)

About 3 weeks ago I was trying to solve a graphics problem with Regnum online and installed Envy, which completely screwed up the graphics.  I have managed to recover the problem (following posts on the forums) but something still isn't correct about it.

I have therefore done a little (and I mean a little) research about X-Windows and have found my way to /etc/X11/XF86Config, where there is a config backup as well as other Xorg.conf files, each with 14 numbers after them, all commencing with 2009.  Are these files all backups of the Config file and if I change the names, can I set the config file back to what it was prior to the changes that gave me problems - is it really that simple????

Any pointers apprciated.

---

### Post by dajasc on 2009-02-25
Yes it is really that simple.  The one named xorg.conf gets used.  The older ones don't.

---

### Post by timofthec on 2009-02-25
> **dajasc said:**
> Yes it is really that simple.  The one named xorg.conf gets used.  The older ones don't.

Brilliant - thanx dajasc.

I'll rename them then and revert to an earlier config file and then re-start in a bit.

---

### Post by timofthec on 2009-02-25
hmm, ok, so how do I rename a file when I am told that I do not have permission to do it?

Edit - do I have to stop X before I can rename the files?

---

### Post by oldos2er on 2009-02-25
Use sudo to give yourself temporary admin privileges:
```
sudo cp xorg.conf.backup xorg.conf
```
for example.

---

### Post by ryan.nabinger on 2009-02-25
careful not to overwrite, sudo can be very powerful.  Also of use may be:

```
diff xorg.conf.backup xorg.conf
```

this will help you see what has actually changed between the backups.

---

### Post by timofthec on 2009-02-25
ok, managed to rename the files using sudo mf.  Trouble is, it seems the oldest backup of the config I have is right in the middle oy my original troubles!

Is there any way to completely reset x-windows?

---

