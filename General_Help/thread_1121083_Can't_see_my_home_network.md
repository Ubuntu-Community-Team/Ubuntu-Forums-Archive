---
title: "Can't see my home network"
date: 2009-04-09
forum: General Help
---

### Post by Mr. Hacku on 2009-04-09
I installed Wubi on my Toshiba Satellite laptop as well, I can't see my home network to connect to the wifi.

Thanks!

---

### Post by paradigm2 on 2009-04-09
> **Mr. Hacku said:**
> I installed Wubi on my Toshiba Satellite laptop as well, I can't see my home network to connect to the wifi.

Thanks!

Hello. We need more details about your configuration.  Such as:

1. Is this computer running samba?
2. What platform are the other computers (Windows XP Home, XP Pro, Vista, Ubuntu, etc)
3. If using Samba, what have you done if anything?  Can you post your smb.cfg or smb.conf file?

OR 

I get the feeling maybe you are just saying you cannot connect to your WIFI at all?  

Do you know what wifi adapter you have in there?

---

### Post by Mr. Hacku on 2009-04-09
The home network is on XP, and am trying to run the Toshiba that has Vista.  The wireless card on the Toshiba is turned on.

---

### Post by paradigm2 on 2009-04-09
> **Mr. Hacku said:**
> The home network is on XP, and am trying to run the Toshiba that has Vista.  The wireless card on the Toshiba is turned on.

Hello. 
Is the issue that you cannot connect to the internet at all over the WIFI adapter in Ubuntu or is it that you can but that you can not view samba shares on the XP machine(s) ?

---

### Post by Mr. Hacku on 2009-04-09
I cannot connect to the internet at all over the Wifi adapter in Ubuntu because I cannot see any networks to connect to.  I know they are there though.  What is samba shares?

---

### Post by lisati on 2009-04-09
The wired and wireless connections on both my Toshiba laptops work without hassle through Ubuntu. Have a look at the top panel for an icon that looks like two computers - click on that to discover which networks you can connect to, and click on the network name to connect.

A "samba share" lets Ubuntu share files and folders with other computers. The tutorial I used to get my 4 machines talking to each other can be found at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by paradigm2 on 2009-04-09
> **lisati said:**
> The wired and wireless connections on both my Toshiba laptops work without hassle through Ubuntu. Have a look at the top panel for an icon that looks like two computers - click on that to discover which networks you can connect to, and click on the network name to connect.

A "samba share" lets Ubuntu share files and folders with other computers. The tutorial I used to get my 4 machines talking to each other can be found at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Also if you have an ethernet cable plugged in to a wired adapter, unplug it from the computer to see the WiFI.  I went a full two days without realizing my wireless adapter was detected and set up automatically during the install.  That's because my wired connection was always plugged in. :)

---

