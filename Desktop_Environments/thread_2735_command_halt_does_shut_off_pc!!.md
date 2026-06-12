---
title: "command halt does shut off pc!!"
date: 2004-10-31
forum: Desktop Environments
---

### Post by -voldemort- on 2004-10-31
hi! 

i'm really a little noob in linux! so plz help me .. my ubuntu linux won't shut down if i insert the command "halt". he just make a restart!

so why is this goin on??? plz help!!

---

### Post by gualtrapa on 2004-12-15
I used gentoo normally, and yesterday I installed ubuntu. I have the same problem, halting from console or from gnome desktop

---

### Post by ubuntu_demon on 2004-12-15
This is a known problem. 

try this :

modprobe apm 
halt

If it works. Next time edit your /etc/modules and add :
apm

After the next reboot halt will always work.

If this doesn't work. Search the forums for "shutdown apm" or something. There are a lot of threads about this.

---

### Post by Lukano on 2004-12-15
Or you can use the shutdown command in it's entirety;

```

shutdown -h now * causes shutdown to halt immediately
shutdown -r now * causes shutdown to reboot immediately
shutdown -r timframe * causes shutdown to reboot in "timeframe

```

---

### Post by jdong on 2004-12-15
Use poweroff to power off ;)

---

### Post by SpaulS on 2005-01-21
Adding apm to /etc/modules fixed the power down function for my Athlon as well.

FYI,
Paul

---

### Post by alainhenry on 2005-01-22
As it did on mine!  

Alain

---

### Post by christgod on 2005-01-23
Not working here!
I get the following message:

modprobe apm
FATAL: Error inserting apm (/lib/modules/2.6.8.1-4-k7/kernel/arch/i386/kernel/apm.ko): No such device

Any ideas?

---

### Post by Buffalo Soldier on 2005-01-23
Used to have problems shutting down my PC. But after following a guide at [ubuntuguide.org](ubuntuguide.org) I manage to solve it. The direct link is [http://ubuntuguide.org/#acpipoweroff](http://ubuntuguide.org/#acpipoweroff)

---

### Post by az on 2005-01-23
"FATAL: Error inserting apm (/lib/modules/2.6.8.1-4-k7/kernel/arch/i386/kernel/apm.ko): No such device"


Can you enable apm in your bios?

---

