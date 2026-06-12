---
title: "ubuntu graphical boot problems"
date: 2009-05-07
forum: General Help
---

### Post by sansa dude on 2009-05-07
when I boot it will go past the splash screen then after it tells me.

" Could not start the X server(your graphical environment) due to some internal error. Please contact your system administrator. in the mean time this display will be disabled. please restard GDM when the problem is corrected." 

i get that then it tells me to login and when i do i get some writing about ubuntu and then it says 

-bash: no job control in this shell

i had no problems getting to the login screen before this. any ideas on how to fix it? i REALLY don't want to re-install again.

---

### Post by colau on 2009-05-07
> **sansa dude said:**
> when I boot it will go past the splash screen then after it tells me.

" Could not start the X server(your graphical environment) due to some internal error. Please contact your system administrator. in the mean time this display will be disabled. please restard GDM when the problem is corrected." 

i get that then it tells me to login and when i do i get some writing about ubuntu and then it says 

-bash: no job control in this shell

i had no problems getting to the login screen before this. any ideas on how to fix it? i REALLY don't want to re-install again.

From the log in prompt being root
[html]
aptitude update
aptitude install xserver gnome gdm
[/html]
Then type 
[html]
startx
[/html]
If it does not work type
[html]
gdm start
[/html]

---

### Post by Rarensu on 2009-08-07
I had the same exact error, the following thread has good information:

[http://ubuntuforums.org/showthread.php?t=1195129](http://ubuntuforums.org/showthread.php?t=1195129)

I ran

sudo dpkg-reconfigure xserver-xorg

As far as know, the program froze (I eventually got bored and rebooted), but then when the system loaded again, everything magically worked  and I have my desktop now.

---

