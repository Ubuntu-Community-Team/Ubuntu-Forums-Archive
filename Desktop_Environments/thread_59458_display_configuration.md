---
title: "display configuration"
date: 2005-08-24
forum: Desktop Environments
---

### Post by nkrust on 2005-08-24
hey  everyone 

i am not able get any resolution other than 600x480. the system has a GeForce 4 MX and the monitor is a 17 " philips. the conf file has all the resolutions supported by my monitor written and the default depth is set at 24. but all that the display screen is showing is 600x480. 

i've tried dpkg-reconfigure xserver-xorg and removed all the other resolutions and only kept 1200x1024 and 1024x786 but then the xserver refused to start showing a big list of error msg. that i'm finding cryptic. can anyone show me how to work around it.

regards

---

### Post by ubuntme on 2005-08-24
what does your xorg.conf look like?
cat /etc/X11/xorg.conf

---

### Post by nkrust on 2005-08-24
[QUOTE=ubuntme]what does your xorg.conf look like?
cat /etc/X11/xorg.conf[/QUOTE]
 if u are asking me to send me the whole xorg.conf file, if thats the case then i shall post it here in a day or two.

and if u are asking about the display section, all the resolutions from 1200x1024 to 400x300 are there, usually ubuntu picks up the highest resolution supported by the system but which should be 1200x1024 but all that i get is 600x480.

regards.

---

### Post by YoG%*@ on 2005-08-24
hi! 

try this: 
[http://www.ubuntuforums.org/showthread.php?p=314681#post314681](http://www.ubuntuforums.org/showthread.php?p=314681#post314681) 
may help.

mux

---

### Post by ubuntme on 2005-08-25
yeah,

I was also interested in what depths and refresh rates.  Also are you using ubuntu drivers? or nividia/ATI etc?

I have had a similar problem before (on Gentoo).

I can't remember exactly what fixed it, but you can try deleteing the lower resolutions, or turn down the default depth.  Not an elegant solution but it worked in the past.

good luck.

---

### Post by snpz on 2005-08-26
Set correct H-Sync and V-sync for your monitor in xorg.conf and write in resolution u whant in the same file!;) Save this file and restart x-server (Ctrl+Alt+Backspace)

---

