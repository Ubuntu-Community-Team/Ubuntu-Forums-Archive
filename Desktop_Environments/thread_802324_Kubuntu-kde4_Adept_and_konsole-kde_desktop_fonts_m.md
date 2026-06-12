---
title: "Kubuntu-kde4 Adept and konsole-kde desktop fonts mismatch or are larger"
date: 2008-05-21
forum: Desktop Environments
---

### Post by jaxxed on 2008-05-21
(Sorry for incorrect category posting)

kubuntu-hardy-rc1 kde4 remix:

I'm having a problem with setting fonts in kde4.  Different applications open up with different font settings. Thanks to ubuntuforums for the information required to fix the gtk (firefox) applications, but I think that my kde3 applications are now using a different set of font sizes than my kde4 apps.

Please see the attached screenshot.

Here you can see three windows.  Two are using much larger fonts than the third (which is using my specified fonts.)
The konsole window on the right is the 'konsole-kde3' application, and the other is the adept-updater (the whole adept suite uses this setting.)

I'm tempted to think that this is either a problem of kde3 using different fonts from kde4, or the root user using different fonts, or both,
Regardles of if I'm right or wrong, can anybody suggest a route to sync everything again?

J

---

### Post by pilat on 2008-05-21
> **jaxxed said:**
> I'm tempted to think that this is either a problem of kde3 using different fonts from kde4, or the root user using different fonts, or both,
Regardles of if I'm right or wrong, can anybody suggest a route to sync everything again?
The same problem. Need good solution how to sync font settings between kde4's control panel and kde3 applications..

---

### Post by jaxxed on 2008-05-29
you can install kcontrol (kde3) and run it to get access to the kde3 control panel.

/> sudo apt-get install kcontrol

/> kcontrol

It doesn't fix adept but it fixes many of the other applications

---

### Post by jaxxed on 2008-05-29
of course, adept runs as root, so you have to change the root fonts for it:

```
kdesu kcontrol
```

( I got this from another ubuforums page, but just lost the link.  Sorry

---

### Post by wmaddler on 2008-09-08
Not exactly a "prompt answer", but I've just installed KDE4 and giving it a try.
Linking .kde4 to .kde seems to work out the fonts issue here (Debian Lenny). Dunno if it could cause any other issue as of now.

---

