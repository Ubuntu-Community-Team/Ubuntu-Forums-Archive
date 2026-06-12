---
title: "GNOME 3 - Automatic login"
date: 2011-05-27
forum: Desktop Environments
---

### Post by Fisher_ on 2011-05-27
Hey all,

i've installed GNOME3 in my Ubuntu 11.04 , but i can't manage to get the automatic login working. 

With gnome2 there was no problem, but now i can't. 
I've tried to remove my password , disabling the list other users and checked the option in login screen to login automatically.

Either way, it always hangs at the GDM.

Is anybody having a similiar problem?

---

### Post by 23dornot23d on 2011-05-27
Mine works ok ..... is this happening after an upgrade or is that a fresh install  ....  ?

If I get problems with gdm .....

I replace it with kdm ....

---

### Post by Fisher_ on 2011-05-27
It is a fresh install and it worked fine before :x

How do you replace gdm for kdm?

---

### Post by 23dornot23d on 2011-05-27
To install kdm ....

The way I do it ....

apt-get update
apt-get install aptitude

aptitude update
[B]aptitude install kdm
[/B] 
Choose kdm when it asks you to ......

and if you do not like it to remove it is 

aptitude remove kdm

choose gdm when it asks you ....

---

### Post by Fisher_ on 2011-05-27
Just tried that, but it just breaks my desktop environment ( panels disappear ) so i reverted to gdm..

---

### Post by nafik on 2011-07-06
I have same issue. Fresh install of 11.04 with Gnome 3 (ubuntu gnome remix ppa). I can set auto login (enable it) for my account in settings window, however when I close this windows and reopen it I can see old settings (disabled auto login). 
Is there in gnome 3 something like gconf-tool in gnome2? That would be way for me to set auto login perhaps.

---

### Post by Mechaphoenix25 on 2011-08-07
Mostly solved!  Simply add any user to the nopasswdlogin group, and that user will no longer be asked for their password on login.  It's not a completely automatic solution (and I don't know how secure it is) but it worked for me.  Some more documentation available here: [http://library.gnome.org/admin/gdm/3.0/gdm.html](http://library.gnome.org/admin/gdm/3.0/gdm.html)

The command I used to do it was: 

sudo gpasswd -a YourUserNameHere nopasswdlogin

---

