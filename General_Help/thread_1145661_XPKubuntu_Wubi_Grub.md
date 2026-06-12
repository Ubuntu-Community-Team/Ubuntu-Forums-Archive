---
title: "XP/Kubuntu Wubi Grub"
date: 2009-05-01
forum: General Help
---

### Post by mschraier on 2009-05-01
I installed 9.04 via Wubi.  I haev done this on previous releases but not in a while.  After messing up OpenOffice, I decided to reinstall and do it over.  I removed 9.04 via XP Add/Remove and then used my MS Win CD to do a fixmbr.  That issue is that I still have the Grub menu created by Wubi.  How else do I get rid of it?

:KS  :KS  :KS

---

### Post by caljohnsmith on 2009-05-01
The Ubuntu boot entry you see on start up is a line inside your Windows C:\boot.ini file. To edit that file, go to Start > Control Panel > System, click the "Advanced" tab, hit "Settings" under "Startup and Recovery", and then under "System Startup", press "edit" and that will pull up boot.ini in Notepad so you can edit it. Then remove the following line in the boot.ini file:
```
C:\wubildr.mbr="Ubuntu"
```
And you should be good to go. Let me know how it goes or if you run into problems.

Cheers,
John

---

### Post by mschraier on 2009-05-02
worked perrfectly.  I am in Kubuntu running Firefox.  This time I did a full normal install.  If I may ask some other questions?  How do I set Kaffeine to be my defauly video play and to autostart when a DVD is inserted? Is it possible to receive Hotmail in Kmail? I will say that this is the best release I have seen.  i have been playing around with Ubuntu/Kubuntu since Fiesty Fawn.  Wifi was a breeze, the prompt for missing plugin and so forth is wonderful.

:guitar:   :guitar:   :guitar:

---

### Post by caljohnsmith on 2009-05-02
Glad to hear that did the trick. About your other questions, I haven't used KDE since its 3.5 version, so I don't think I can be of much help. I would imagine that your questions are common enough (I'm sure others have wanted to do the same thing) that if you search the forums you will find an answer. If not, you of course can always start a new thread. Anyway, cheers and enjoy your new Kubuntu install. :)

John

---

