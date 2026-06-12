---
title: "Kde4"
date: 2008-01-30
forum: Desktop Environments
---

### Post by giraf on 2008-01-30
Hi ,
After installing KDE4 I get blue screen , any ideas ?
Thanks

---

### Post by roderick on 2008-01-30
how did you install it? kde4-core package?

when do you get the blue screen? Upon login, and is it via a KDE3 or KDE4 session?

did you install kdm4 and set it as default? If you did, you can try and remove it and use kdm3 as default instead (it will work).

---

### Post by giraf on 2008-01-30
yes , kde4core package , yes upon login , I didn't have kde3 but gnome ,  not sure about the default . 
How should  I  install it ?

---

### Post by roderick on 2008-01-30
Hmmm... not sure about using KDE4 from a Gnome install. I am pure KDE here.

Maybe it's possible to uninstall kdm4 and simply use gdm and start a kde4 session.

Try that. I know I had issues with kdm4 and had to revert to kdm3, so in theory, gdm should work equally well.

One thing, what does the blue screen look like? Is it a plain blue or a blue wallpaper image with a pattern? Maybe plasma failed to start and therefore the widgets failed... which is something entirely different than what I was suggesting about in troubleshooting.

---

### Post by kugn on 2008-01-30
do you see a konsole shell along with the blue screen? if so it's a problem with kdm-kde4. you can revert back to using gdm by 

sudo dpkg-reconfigure gdm

---

