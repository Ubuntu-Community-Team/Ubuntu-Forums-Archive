---
title: "ksysgard konsole not launching after sudo repair"
date: 2015-01-16
forum: Desktop Environments
---

### Post by Trad_dog on 2015-01-16
Hi,

I removed myself from all groups yesterday while making the same mistake as in:
[http://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user](http://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user)
I have followed the steps in the previous thred and in: 
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
which are slightly outdated as the recovery mode is now accessible from the grub menue directly in advanced options. 
But the rest seems to work. 

Now, in kde when logging back I cannto launch a konsole or ksysgard or any update option. 
Any suggestion would be welcome

Best, 

Trad

---

### Post by vinnywright on 2015-01-16
what ver. of kubuntu ?

wile at the login screen press ctrl+alt+F6 you will get a TTY console ,type your user name and press enter ,type your password and press enter type, ```
groups
``` ,and press enter

you should see 
> vinny@vinny-Bonobo-Extreme:~$ groups
vinny adm cdrom sudo dip plugdev lpadmin sambashare libvirtdexept vinny should be your user name and you may/may-not have libvirtd depending on if you have KVM installed or not .

if you could not login to the TTY then maybe you are not in your group ,,,,, 

VINNY

---

### Post by Trad_dog on 2015-01-18
Hi Vinny

That did the trick and taught me something I did not know about groups. 

Much appreciated, 

Trad

---

