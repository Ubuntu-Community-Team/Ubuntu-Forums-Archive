---
title: "My Default Account Lost Admin Rights"
date: 2006-10-05
forum: Desktop Environments
---

### Post by Srirangan on 2006-10-05
A few days bck, I downloaded Ubuntu Desktop 6.06 and installed it on my PC. Installation went fine but the ethernet network was buggy.

I f'd around with the hostnames and other settings in Admin -> Networking. I ended up using hte Mozilla Firefox hack (about:config IPV6) to get my Mozilla working.

But during this process (presumably while playing with Networking settings) my default account (that was created while installation) has lost all admin rights and permissions).

Anything that I can do to fix the problem? Or is it a full reinstall for me? Thanks!

- Sri

---

### Post by scotty32 on 2006-10-05
sorry if i misunderstood but....

accounts in Ubuntu dont have Admin rights, but you can gain tempary rights by doing 'sudo ....' 

and you use your accounts password...


if ive read it wrong, and you cant do the sudo thing - then sorry i cant help as am a linux newbie

i cant imagine you getting it back as that would be kind of unsecure.

---

### Post by ajgreeny on 2006-10-05
If you mean sudo is not working any more have a look at this web page which has a few fixes for the situation using recovery mode from boot-up, usually the second boot line in your grub menu.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

This will allow you to put your user name back into the list of people who can sudo to root privileges. Good luck.

---

### Post by Srirangan on 2006-10-05
> **ajgreeny said:**
> If you mean sudo is not working any more have a look at this web page which has a few fixes for the situation using recovery mode from boot-up, usually the second boot line in your grub menu.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

This will allow you to put your user name back into the list of people who can sudo to root privileges. Good luck.
I tried this but it hasn't worked.

---

### Post by Srirangan on 2006-10-05
srirangan@:~$ id
uid=1000(srirangan) gid=1000(srirangan) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(srirangan)

---

### Post by Srirangan on 2006-10-05
srirangan@:~$ gksudo nautilus

(gksudo:5215): Gdk-WARNING **: locale not supported by Xlib

(gksudo:5215): Gdk-WARNING **: cannot set locale modifiers
sudo: unable to lookup  via gethostbyname()

---

### Post by nikhilk on 2006-10-05
Kindly check if the hostname in the files "/etc/hosts" and "/etc/hostname" agree.

---

### Post by Srirangan on 2006-10-05
I ended up reinstalling 6.06 :)

---

