---
title: "startup problem"
date: 2005-12-09
forum: Desktop Environments
---

### Post by darth_geekus on 2005-12-09
On bootup, I get an error message after I log in. It says:
Could not look up internet address for quarkie. This will prevent GNOME from operating corredctly. It may be possible to correct the problem by adding quarkie to the file /etc/hosts.  Log in Anyway           Try again

If I hit try again, the computer thinks for a few seconds and then pops up the error again. If I hit log in anyway, the system finishes booting, but it won't open up the networking under system adminstration. It switches to the 'working' mouse pointer for a few seconds, then goes back the normal pointer, without opening it.

I believe that the problem is stemming from some setting I got wrong when I was trying to get my wireless card working at home, becuase 'quarkie' is my laptop's name, and I was trying to make sure I had it set to that so that my wireless router would recognize the laptop (I am using MAC address/system name security on my router)

My problem has been that my wireless networking works at school, but not at home, under Ubuntu. It does work under win 2k, however, so I thought the problem was that my system name under Ubuntu was not the same as under windows, but now I can't get into networking to check it out!

Any clue how I can correct this?

Chris

---

### Post by pieboy314 on 2006-01-05
hey dude,

did you ever solve this? I am working through the same error. 

most fixes I find require me to log in as root, which I am unable to do, so now I have two problems I am working on...

---

### Post by zoiks on 2006-01-05
[QUOTE=darth_geekus]On bootup, I get an error message after I log in. It says:
Could not look up internet address for quarkie. This will prevent GNOME from operating corredctly. It may be possible to correct the problem by adding quarkie to the file /etc/hosts.  Log in Anyway           Try again
[/QUOTE]

I don't know if this helps, but..

Do you also get this message when trying to open things like "System|Administration|Networking"?  If so, I can reproduce behavior like this if I delete the host name from the first line of /etc/hosts.

127.0.0.1       localhost.localdomain   localhost      [host-name-deleted]

---

### Post by pieboy314 on 2006-01-05
[QUOTE=zoiks]I don't know if this helps, but..

Do you also get this message when trying to open things like "System|Administration|Networking"?  If so, I can reproduce behavior like this if I delete the host name from the first line of /etc/hosts.

127.0.0.1       localhost.localdomain   localhost      [host-name-deleted][/QUOTE]

yes, I now believe my problem is that I am missing the host name from the first line of /etc/hosts.

my real problem is that I believe it is this missing host name that also gives me this error,
*sudo: unable to lookup via gethostbyname()*
when running sudo commands and I am unable to edit the /etc/hosts file in anything but sudo...

ho hum, a catch-22

---

### Post by amohanty on 2006-01-05
Try logging into the recovery console. That drops you in as root. There you wont need to do an sudo.

HTH

PS: You can re-run the installer in expert mode, set the name, and do _nothing_ else and reboot.

---

### Post by pieboy314 on 2006-01-05
[QUOTE=amohanty]Try logging into the recovery console. That drops you in as root. There you wont need to do an sudo.

HTH

PS: You can re-run the installer in expert mode, set the name, and do _nothing_ else and reboot.[/QUOTE]


cool. thanks, I will try these methods.

---

### Post by pieboy314 on 2006-01-05
[QUOTE=amohanty]Try logging into the recovery console. That drops you in as root. There you wont need to do an sudo.

HTH

PS: You can re-run the installer in expert mode, set the name, and do _nothing_ else and reboot.[/QUOTE]

I tried logging in to "failsafe" mode but it does not help. what is recovery console?

thanks

---

### Post by amohanty on 2006-01-05
When grub pops up prompting you to choose a kernel, select the one that says recovery at the end.

That will drop you down to the command line and ask you for your password. 

HTH
AM

---

