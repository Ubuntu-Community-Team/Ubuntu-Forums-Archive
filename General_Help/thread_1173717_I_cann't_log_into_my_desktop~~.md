---
title: "I cann't log into my desktop~~"
date: 2009-05-30
forum: General Help
---

### Post by KING^2 on 2009-05-30
hi, yesterday i have changed  some configs ,and now i cannot get into my desktop, i could see the boot up interface ,i could also see the loading picture, when these are done, what i see is a mess of bad colours, and no response nomatter what i do. has any guys met this problem before ?  
PS: i have use the recovery mode to recover the graphic problem, it didn't work however. how frustrating:(
any suggestion would be appriciated ~ thx in advance !

---

### Post by juancarlospaco on 2009-05-30
Backup configs?

Go to terminal and reinstall the desktop

**sudo apt-get --reinstall install ubuntu-desktop**

---

### Post by KING^2 on 2009-05-30
> **juancarlospaco said:**
> Backup configs?

Go to terminal and reinstall the desktop

**sudo apt-get --reinstall install ubuntu-desktop**
Thx!
Not the backup; It's the display setting i have configured. And after reconfiguring the graphic settings , i can't get into the desktop. i don't want to reinstall the system. Any ideas?

---

### Post by alberto ferreira on 2009-05-30
Which display setting?
/etc/X11/xorg.conf ?

Have you run the command that **juancarlospaco** gave you?[B] It will fix your problem I believe and it's not a full reinstall, and it's fully automatic.
[/B]

---

### Post by KING^2 on 2009-05-30
> **alberto ferreira said:**
> Which display setting?
/etc/X11/xorg.conf ?

Have you run the command that **juancarlospaco** gave you?[B] It will fix your problem I believe and it's not a full reinstall, and it's fully automatic.
[/B]
haven't yet, but I've worked it out, using the command line interface to login as the root role, and input these actions: 
apt-get install xserver-xorg
dpkg-recongure xserver-xorg
startx
After all , thank you guys!;)

---

