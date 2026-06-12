---
title: "Open office 3.2 crashes"
date: 2010-03-27
forum: Desktop Environments
---

### Post by ramsrambo on 2010-03-27
[FONT="Century Gothic"][SIZE="4"]When I am using oowriter and I select Tools ---> option menu option I get this error message " X-Error: BadAlloc (insufficient resources for operation)
	Major opcode: 53 (X_CreatePixmap)
	Resource ID:  0x40004d2
	Serial No:    7106 (7106)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging" Please let me how can I fix this ?:popcorn:[/SIZE][/FONT]

---

### Post by n0dix on 2010-03-27
Try disabling visual effects.

---

### Post by ramsrambo on 2010-03-29
nOdix,

Can you please describe disabling visual effects.

I disabled the visual effects in display settings to none and tried running from terminal prompt it still crashes.

If it is disabling gdm I feel writer will not work at all.

Ravi

---

### Post by n0dix on 2010-03-29
Ok, How much memory Ram do you have? Give some specifications. 
Do you try reinstalling the Open Office? Do you use the packages in repositories?
Do you have installed the video driver well, with direct rendering?

---

### Post by ramsrambo on 2010-03-29
> **n0dix said:**
> Ok, How much memory Ram do you have? Give some specifications. 
Do you try reinstalling the Open Office? Do you use the packages in repositories?
Do you have installed the video driver well, with direct rendering?

How much memory Ram do you have? 1.5 GB of RAM
I will need to try reinstalling it
I used lsshw to list all the devices with drivers and the Video driver seems to be alright
Can u specify what exactly  u mean to say direct rendering?

---

### Post by n0dix on 2010-03-29
I mean:
```
$ glxinfo | grep "direct" 
```

---

### Post by ramsrambo on 2010-03-30
nOdix,

Here is the O/p of the above command 
$ glxinfo | grep "direct"
direct rendering: Yes

I tried re-installing the writer pkg it crashed once again as before
Ram

---

### Post by n0dix on 2010-03-30
Edit the file /etc/X11/Xorg.conf. Reach the section "device" and add those lines:
```
Option "Videoram" "65536"
```

```
Option "Cachelines" "1980" then halt and restart x server
```

---

### Post by ramsrambo on 2010-03-30
nOdix,

If you refer to this url it says it has been depreciated 

[http://ubuntuforums.org/archive/index.php/t-253689.html](http://ubuntuforums.org/archive/index.php/t-253689.html)

Please clarify me on this.

Also I am unable to locate the file  /etc/X11/Xorg.conf let me know as to where to find this file

Ram

---

### Post by n0dix on 2010-03-30
Yes, but the error you have is very weird. And the only information i find is about 2 years ago.

---

### Post by pcardout on 2010-05-07
I had this problem too and I followed the advice from 

[http://www.uluga.ubuntuforums.org/showthread.php?t=450008&page=7]("http://www.uluga.ubuntuforums.org/showthread.php?t=450008&page=7")

Specifically:
```
apt-get remove openoffice.org-gtk
```

There were complaints it made openoffice "Ugly".  I didn't really notice,
but my crash on Tools/Options in OOwriter and ALSO  in Custom animation in OOImpress both went away.

I am using OpenOffice 3.2 in Ubuntu Karmic Koala 9.1 ... just like the
original poster.

---

