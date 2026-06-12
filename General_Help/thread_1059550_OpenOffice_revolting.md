---
title: "OpenOffice revolting?"
date: 2009-02-03
forum: General Help
---

### Post by phantom3113 on 2009-02-03
Greetings. I was hoping someone could shed some light on this rather peculiar issue I'm having. Recently (as in a few hours ago) OpenOffice 3.0 began to crash whenever I tried to open any file that opened into openoffice. After running Writer in a terminal, I find this returned when it crashes:

```
(soffice:7285): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated


```

I'm currently working on reinstalling OpenOffice hoping that it stops this since I need it to continue my work, but I wanted to know what's going on so I can prevent this from happening again.

---

### Post by phantom3113 on 2009-02-03
So, I may have dug myself into a deeper hole. I just did a complete wipe and reinstall of OpenOffice 3.0 using the .deb files from the download site and any instance of openoffice I try to open whether I'm opening a file or just OpenOffice itself, I get this:

```
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

```

Someone please help me!

---

### Post by gackt on 2009-02-04
tru to uninstall it with purge argument. i mean completely remove it from the system. Log uot and reinstall it

---

### Post by phantom3113 on 2009-02-04
I'll try that as soon as I get home today. However, could you clarify a bit on the purge command? I know it's "sudo apt-get purge" but what should follow that? The deb package that I installed had a different package name than what openoffice originally was. For example, if I wanted to run openoffice from terminal, it had been "ooffice" or "ooffice -writer" etc. whereas now it's "openoffice.org3" or "openoffice.org3 -writer".

---

### Post by LowSky on 2009-02-04
sudo apt-get --purge remove openoffice*

that should do the trick, remember the "*"

---

### Post by phantom3113 on 2009-02-04
Ok, thanks. I'll let you know how it goes.

---

### Post by phantom3113 on 2009-02-04
Ok, so I just purged OpenOffice, logged off, logged on, and then reinstalled via the .deb files. However, it kept doing the exact same thing it was doing. Based on that, I think it may have been something with the .deb package, but that was only half the problem. Currently I'm working on downloading and reinstalling the openoffice package from the repositories. Check that, I just finished and it all works as it should have! Huzzah! Well, now that this nightmare is (hopefully) over, does anyone know why this went haywire in the first place? I want to figure out what happened so it NEVER happens again.

---

### Post by Hagar Delest on 2009-02-05
Sometimes, just resetting the OOo profile works (renaming the ~/.openoffice.org folder). If you had a previous version, importing the personal data when asked by the welcome process might be a bad idea, former configuration can corrupt the new profile.

NB: I've always used the .deb version from OOo web site from 2.0 without any problem.

---

### Post by phantom3113 on 2009-02-07
I never imported anything to OOo. 8.10 had vers. 2.4 on it and I upgraded it to 3.0 through the repositories. It just started giving me problems when I tried to open a file to work on for homework.

---

### Post by ptn107 on 2009-02-07
You should just think about using openoffice 2.4.1 if it works, unless you have an absolute need for openoffice 3.

---

