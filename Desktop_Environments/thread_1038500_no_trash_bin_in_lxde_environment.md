---
title: "no trash bin in lxde environment"
date: 2009-01-12
forum: Desktop Environments
---

### Post by mabtifro2 on 2009-01-12
ive been using lxde environment for quite some time now but i've always been a little annoyed with the fact that there is no trash bin to be found. it appears that when you delete a file, it's gone for good, no second chances. does anyone know if there is a way to add a trash bin to lxde?

---

### Post by adamlau on 2009-01-13
Is this an Ubuntu Minimal + LXDE, or Ubuntu + LXDE install? You can typically right click on a panel to bring up a list of supported applets, of which the trash bin ought to be one.

---

### Post by mabtifro2 on 2009-01-15
it's ubuntu + lxde install, and unfortunately, the trash bin is not an option on the list of icons or apps when i right click the panel in the lxde environment

---

### Post by snowpine on 2009-01-15
Have you tried using a different file manager (such as thunar) in place of pcmanfm?

---

### Post by mabtifro2 on 2009-01-15
no, i haven't tried changing file managers.

so is this an issue of file managers?

---

### Post by adamlau on 2009-01-16
What is the output of:

```
ls -aFC ~/.local/share/Trash/files
```

Files are only gone for good (outside of forensic and recovery applications and techniques) if you clicked and held down Shift before clicking Delete.

---

### Post by kerry_s on 2009-01-16
pcmanfm doesn't have trash support.

---

### Post by adamlau on 2009-01-16
I believe mabizeid may be referring to the deletion of files on the desktop and the addition of a trash applet on a panel.

---

### Post by kerry_s on 2009-01-16
maybe try this->
[http://bbs.archlinux.org/viewtopic.php?pid=477174](http://bbs.archlinux.org/viewtopic.php?pid=477174)

---

### Post by adamlau on 2009-01-16
Since LXDE maps application launchers to .desktop files, perhaps you could hack one out to point to the Trash folder.

---

### Post by kerry_s on 2009-01-16
i've always hated the trash, makes you delete stuff twice.
the trash is just a folder/directory that stuff gets moved to, a little cut & paste you can do the same thing, just don't delete it if you think you might want it or move it and wait till your sure you don't want it.
we have a saying around here "make a backup first!".

---

### Post by adamlau on 2009-01-16
Exactly why I use an rm -rf %F Thunar UCA instead of Shift+Delete, no need for an extra, wasteful step.

---

### Post by mabtifro2 on 2009-01-19
> **adamlau said:**
> What is the output of:

```
ls -aFC ~/.local/share/Trash/files
```

Files are only gone for good (outside of forensic and recovery applications and techniques) if you clicked and held down Shift before clicking Delete.

my output is;

./  ../

thats it

---

### Post by amjjawad on 2011-09-07
For those who will search and find this thread, please be informed that PCManFM Latest Version is "PCManFM 0.9.9" and it's the default FM in Lubuntu 11.04 and **it has** Trash.

---

