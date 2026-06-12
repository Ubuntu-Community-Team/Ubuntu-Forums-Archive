---
title: "How to start GUI program without desktop"
date: 2008-12-06
forum: Desktop Environments
---

### Post by jiunhsien on 2008-12-06
We usually use GDM/KDM login, then use GNOME/KDE desktop. We run the openoffice.org/firefox/xterm ..etc..

In the run level 3, I login the console without GDM/KDM.

Could I start openoffice.org(GUI) under the command line? 

It like startx, but no GNOME/KDE. Just only run openoffice.org.

I just run only one program(openoffice.org, firefox) at once.

It may save more memory and cpu at my low performance computer.

Could you tell me how to do? Many thanks!

---

### Post by kerry_s on 2008-12-06
why not just install a simple window manager instead of a desktop?
what kind of specs are we talking here? 
openoffice is demanding, but there are lighter alternatives, so you can use a gui normally.

i'm using a old 450mhz 256mb laptop, i'm a running debian lenny custom install, just installed the base and built up from there.

---

### Post by snova on 2008-12-06
I suggest to use a lighter desktop environment (Xubuntu for example) or a standalone window manager.

Alternatively, run this:

```
startx <program>
```

It starts the X server with <program> as the root window.

---

### Post by jiunhsien on 2008-12-07
Thank you for your suggestion.

the > startx <program> really work!

I will try the 2 ways

 1. xfce + gnumeric/abiword

 2. startx openoffice.org

---

### Post by snova on 2008-12-07
"startx openoffice.org" won't work, just to make sure. 'oowriter' or 'oocalc' are the commands, as an example for Writer and Calc.

---

