---
title: "switching from gui to console at login prompt"
date: 2012-05-03
forum: Desktop Environments
---

### Post by doctordruidphd on 2012-05-03
OK, I give up...

How do I switch from gui to console session at the login prompt?  Running in a virtual machine, so I can't use CTRL-ALT-F1, and the only session types available are "ubuntu" and "ubuntu 2d". 

Trying to set up ubuntu precise (I normally use kde, not real familiar with lightdm/unity) but I always do upgrades from the console.

Thanks.

---

### Post by mips on 2012-05-03
Is this from a existing install or a cd/image?

You could always login and then switch to console and stop lightdm,
ctrl-alt-f1
**sudo /etc/init.d/lightdm stop**  (substitute lightdm for gdm if you are using that)

 
Another option is editing grub, try **quiet splash text** options on the grub screen. Or use the recovery mode option in grub to drop you to a terminal.

---

### Post by doctordruidphd on 2012-05-03
Again, this is running in a virtual machine; if I use CTRL-ALT-F1 it switches the host, not the ubuntu vm. 

This is running from a "clean install" on the hard disk.

I tried doing a **sudo service lightdm stop** from a terminal inside ubuntu, and it did shut down the unity session, but I never got a login prompt, just a bsod.


Will try editing grub and doing update-grub.

Edit: fixing /etc/default/grub got me to a grub prompt at bootup, so now I can do this, but... Is it the case  that there is no way to get to a console session from the lightdm login screen?

---

### Post by Cheesemill on 2012-05-03
If you are using VirtualBox then it's HOSTKEY+F1 to switch to a virtual terminal.
If you haven't changed it then the HOST key is RIGHTCTRL by default.

There are similar key combinations for other VM solutions if you aren't using VirtualBox, just Google for 'virtual terminal vmware' for example.

---

### Post by doctordruidphd on 2012-05-03
> If you are using VirtualBox then it's HOSTKEY+F1 to switch to a virtual terminal.
If you haven't changed it then the HOST key is RIGHTCTRL by default.

Worked. Thanks.

---

