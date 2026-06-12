---
title: "How do you switch off the monitor?"
date: 2005-12-28
forum: Desktop Environments
---

### Post by harisund on 2005-12-28
I am running Gnome on my relatively old laptop. 

At times when I am leaving the computer for more than a certain length of time, I switch of the hard disk using hdparm -Y /dev/hda. However, I want to switch of the monitor as well. How do I do that? Right now, there is a blank screen saver that comes on. I don't want a blank screen saver, I want the entire screen switched off.. is there a way to do that? 

Thanks !

---

### Post by cylon359 on 2005-12-28
Under System->Preferences->Screensaver

If you select the advanced tab, do any of the "Display Power Management" options work for what you want?

---

### Post by harisund on 2005-12-28
ok thanks.. I will have a look.. configure it for some short time, and will wait an see if it works .. thanks again !

UPDATE: ```
xset dpms force off
``` seems to work great ..

---

### Post by art on 2005-12-28
UPDATE: ```
xset dpms force off
``` 

Great tip, I was looking for this! Thanks!

---

### Post by theclaw on 2005-12-31
[QUOTE=harisund]
UPDATE: ```
xset dpms force off
``` seems to work great ..[/QUOTE]

Wonderful. [img]http://img530.imageshack.us/img530/6728/emotglomp7bu.gif[/img] Thanks!

Edit:
Hah, you can do this over ssh if you add in -display :0 [img]http://img530.imageshack.us/img530/1736/emotv9te.gif[/img]

---

### Post by harisund on 2005-12-31
Wow ! Thanks a lot for the SSH tip.. comes in handy for me ..

---

### Post by chimera on 2005-12-31
With a sledgehammer.

---

