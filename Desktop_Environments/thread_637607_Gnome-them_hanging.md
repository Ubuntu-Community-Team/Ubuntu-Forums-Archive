---
title: "Gnome-them hanging"
date: 2007-12-11
forum: Desktop Environments
---

### Post by sandipan on 2007-12-11
Hi
    I use ubntu 7.10 , all were working, yesterday i install gnome-theme 20.21.2 by creating deb pkg from tarball.
Now Apperance (to change the background, theme etc.0 is not working, it's hanging.
I wan't to solve it or else put back the original 7.10 gnome theme
How will I do that
Any help???????????

thanks
sandipan
:confused:

---

### Post by gazj on 2007-12-11
press ctrl+alt+f1 to get to a terminal

login as usual

issue the following commands (note this will put your whole gnome settings back to there defaults)

```
rm -Rv .gnome*
rm -Rv .gtk*
```

then

```
exit
```

to logout

press ctrl+alt+f7 to return to the gdm login screen

---

### Post by sandipan on 2007-12-11
HI Thanks for the suggestion, but it's didn't work. can any one suggest how to fix it?
may be re-installing original gnome from ubuntu 7.10 or use other like kde?

---

