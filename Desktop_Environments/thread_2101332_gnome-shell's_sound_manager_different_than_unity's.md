---
title: "gnome-shell's sound manager different than unity's"
date: 2013-01-04
forum: Desktop Environments
---

### Post by dashman on 2013-01-04
Hello, everyone
I'd like to know if there's a way to get unity's sound manager

[[IMG]http://pix.toile-libre.org/upload/img/1357305237.png[/IMG]]("http://pix.toile-libre.org/upload/original/1357305237.png")

to look like gnome-shell's

[[IMG]http://pix.toile-libre.org/upload/img/1357305309.png[/IMG]]("http://pix.toile-libre.org/upload/original/1357305309.png")
I'd really like to have that connector selector thingy in unity


any idea ?

---

### Post by jbicha on 2013-01-04
Run
```
XDG_CURRENT_DESKTOP=GNOME gnome-control-center
```
to get the GNOME version.

---

### Post by grahammechanical on 2013-01-04
It is there in Raring Ringtail development version. It is moved to the bottom of the sound utility in Ubuntu. Whereas it is at the top in Gnome Remix.

Regards.

---

### Post by dashman on 2013-01-05
> **jbicha said:**
> Run
```
XDG_CURRENT_DESKTOP=GNOME gnome-control-center
```to get the GNOME version.
Thanks Jeremy but shouldn't I put the XDG_CURRENT_DESKTOP=GNOME bit in ~/.bashrc or some other config file to make it permanent ?

---

### Post by zombifier25 on 2013-01-05
It goes in .profile.

---

### Post by dashman on 2013-01-05
Alright
thank you

---

### Post by markbl on 2013-01-05
> **zombifier25 said:**
> It goes in .profile.
But you will likely break heaps of things if you set it globally like that.

---

### Post by dashman on 2013-01-06
> **markbl said:**
> But you will likely break heaps of things if you set it globally like that.
so what should I do Mark ? is ~/.pam_environment a better choice ?

---

### Post by markbl on 2013-01-06
> **dashman said:**
> so what should I do Mark ? is ~/.pam_environment a better choice ?
I understand you want to run a normal Unity environment but activate the gnome sound manager rather than the Unity version? Well then just edit the corresponding desktop file and add that environment variable (e.g. [http://askubuntu.com/questions/144968/set-variable-in-desktop-file](http://askubuntu.com/questions/144968/set-variable-in-desktop-file)).

---

