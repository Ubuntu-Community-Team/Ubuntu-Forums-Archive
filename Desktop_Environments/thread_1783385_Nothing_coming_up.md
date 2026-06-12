---
title: "Nothing coming up"
date: 2011-06-15
forum: Desktop Environments
---

### Post by mbrowning2000 on 2011-06-15
Hi, I just installed Gnome 3 on ubuntu 11.04 and Unity started messing up, so I disabled it. then when I rebooted I have nothing but my wallpaper come up and I cant start terminal or nothing. ALT F2 dont work. idk what to do at this point. I have it on Auto login (like an idiot) so i cant choose a session.

please help :confused:

EDIT: its Fixed, but i cant mark it as fixed. Dont know how :facepalm:

---

### Post by dodo3773 on 2011-06-15
> **mbrowning2000 said:**
> Hi, I just installed Gnome 3 on ubuntu 11.04 and Unity started messing up, so I disabled it. then when I rebooted I have nothing but my wallpaper come up and I cant start terminal or nothing. ALT F2 dont work. idk what to do at this point. I have it on Auto login (like an idiot) so i cant choose a session.

please help :confused:

Can you get to a console session by hitting 
ctrl+alt+f1 or f2 f3 whatever? If so you should be able to fix it from there. Are you using gdm for your login manager? If so, there should be a file somewhere (at least there used to be) in

/etc/gdm/custom.conf

Where you may be able to change

AutomaticLoginEnable=true

to 

 AutomaticLoginEnable=false


If you are using lightdm there should be a file here as well

/etc/lightdm.conf

---

### Post by mbrowning2000 on 2011-06-16
Well, i got it fixed....some how. I typed "sudo apt-get upgrade" and it let me pick a session. I picked Gnome. Gnome 3 pulls up just fine, and so far is running good. Thanks for the info dodo3773.

---

### Post by dodo3773 on 2011-06-16
> **mbrowning2000 said:**
> Well, i got it fixed....some how. I typed "sudo apt-get upgrade" and it let me pick a session. I picked Gnome. Gnome 3 pulls up just fine, and so far is running good. Thanks for the info dodo3773.

Glad you figured it out. Did you log in to a tty? Is that how you handled it?

---

### Post by mbrowning2000 on 2011-06-16
Yea, I hit ctrl+alt+f6 and it got me in to a shell.

---

