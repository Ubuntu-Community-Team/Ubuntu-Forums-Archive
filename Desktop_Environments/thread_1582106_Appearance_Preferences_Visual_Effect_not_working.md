---
title: "Appearance Preferences Visual Effect not working"
date: 2010-09-26
forum: Desktop Environments
---

### Post by Wins2LinX on 2010-09-26
Hi,

I use Linux Lucid 10.04. 
System by default logs me in to visual effects "None". when I tried to make a change to "Normal" or "Extra", I get couple of flickers in the monitor and get an error message "Desktop effect could not be enabled".

Any helpful thoughts regarding this is appreciated.

Thanks..

---

### Post by mrhhug on 2010-09-26
prolly a driver issuse,,, do you have nvidia hardware???

please post output of ```
lspci | grep VGA
```

---

### Post by sikander3786 on 2010-09-26
Agree with mrhhug. Drivers issue. Post the output of the command mentioned in the above post.

I doubt if you even installed drivers for your graphics card from System > Administration > Hardware Drivers. Did you? If yes see which version is activated there?

---

### Post by Wins2LinX on 2010-09-26
mrhhug - Win2LinX@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]

Sikandar3786 - I cant see the Hardware Drivers option in the system > Admin list. I searched in the preference list too, but no luck.

What I should do next?

---

### Post by sikander3786 on 2010-09-26
So you haven't installed the drivers. Have you seen this page?

[http://www2.ati.com/drivers/linux/linux_8.24.8.html](http://www2.ati.com/drivers/linux/linux_8.24.8.html)

---

### Post by Wins2LinX on 2010-09-26
Thanks for you immediate response Sikander.

I have installed the ATI driver already. 

When I tried to change the ATI setting through "ATI Catalyst Control Center" I get an error message. (Please see attached doc for the screenshot of the error.

I thank you for your continues support on regarding this issue. I appreciate it.

---

### Post by mrhhug on 2010-09-26
that error is pretty clear "ATI driver not functioning properly", how did you install your current driver? 

have you seen this thread??? [http://ubuntuforums.org/showthread.php?t=1491346&page=2](http://ubuntuforums.org/showthread.php?t=1491346&page=2)

---

### Post by Wins2LinX on 2010-09-27
To give you the full story, I have attached another posting " [http://ubuntuforums.org/showthread.php?t=1581793](http://ubuntuforums.org/showthread.php?t=1581793) " of mine, regarding ATI installation. I think they both are related to this issue.

May be this info would help to understand the mistakes I made.

Regarding the ATI driver installation, I downloaded the file from the ATI link and uninstalled the [SIZE=2]ATI Linux Proprietary Driver and then installed the "ati-driver-installer-10-9-x86.x86_64.run" file in 'Automatic' option. there was no error or even warning while installation.

After the installation, it not working properly.
[/SIZE]

---

### Post by mrhhug on 2010-09-27
here is a link to the exact same graphics driver installation 

[http://ubuntuforums.org/showthread.php?t=1491346](http://ubuntuforums.org/showthread.php?t=1491346)

this is well documented all over the ubuntuforums and google searching should find you a wealth of information (which will be way faster than waiting for us to repost every time)

---

### Post by OGalekos on 2010-10-06
Can anyone help me with my drivers settings?

alekos@alekos-pc:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Device 689e
alekos@alekos-pc:~$

---

### Post by OGalekos on 2010-10-06
> **OGalekos said:**
> Can anyone help me with my drivers settings?

alekos@alekos-pc:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Device 689e
alekos@alekos-pc:~$


I actually run an i686, and I cannot load up desktop cube right or shown.

---

