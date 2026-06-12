---
title: "rc.local, start things on boot up"
date: 2005-04-28
forum: Desktop Environments
---

### Post by flightcrank on 2005-04-28
um where is the ect/rc.local file in ubuntu ? im guessing it has none, but im sure is has a equvilant.

there is a appliation i want to start on boot up, and the documentation for this application ask's to add a line to /ect/rc.local.

any ideas ?

---

### Post by DJ_Max on 2005-04-28
[QUOTE=flightcrank]um where is the ect/rc.local file in ubuntu ? im guessing it has none, but im sure is has a equvilant.

there is a appliation i want to start on boot up, and the documentation for this application ask's to add a line to /ect/rc.local.

any ideas ?[/QUOTE]
 The directory is **/etc**. What app are you talking about.

---

### Post by flightcrank on 2005-04-28
its the no-ip client from [www.no-ip.com](www.no-ip.com),

it dosn't matter what app it is any way ! 

so any one know if there is a ubuntu equvilant for a /etc/rc.local ?

---

### Post by speedman on 2005-04-28
/etc/init.d/bootmisc.sh


Regards,

SM

---

### Post by DJ_Max on 2005-04-28
[QUOTE=flightcrank]its the no-ip client from [www.no-ip.com](www.no-ip.com),

it dosn't matter what app it is any way ! 

so any one know if there is a ubuntu equvilant for a /etc/rc.local ?[/QUOTE]
 Actually it does if you want proper help. :roll:

---

### Post by alastair on 2005-04-28
No rc.local, it's a different style of initscripts.

But - it is very easy to set up something similar - there is even a "skeleton" init script (/etc/init.d) that you can copy to "local" (or whatever), modify for your specific use and have run at boot.

Get the script ready and look into "update-rc.d" (man update-rc.d).

---

### Post by valnar on 2005-05-24
Can anyone give us a reason why the Gods of ubuntu saw fit to remove the rc.local file?

Robert

---

### Post by speedman on 2005-05-24
[QUOTE=valnar]Can anyone give us a reason why the Gods of ubuntu saw fit to remove the rc.local file?[/QUOTE]

There is no rc.local used in Debian.  Considering Ubuntu is based on Debian nothing has been removed - it's just a different style of init scripts as noted above.

You can always add entries to the end of /etc/init.d/bootmisc.sh to achieve a similar effect to editing the rc.local file on other versions of Linux, but when that script is upgraded you will be prompted to take action with regards to it being replaced if you have a made modifications.

Using the skel example - also noted above - is really the proper way to provide a boot time init script for a non Debian/Ubuntu package.


Regards,

SM

---

