---
title: "Grub does not see my new Ubuntu 64"
date: 2009-03-26
forum: General Help
---

### Post by Old and Rusty on 2009-03-26
I have three sata drives.

sda    has a windows xp os
sdb    has a fresh install of Ubuntu 64
sdc    has an old install of Ubuntu 8.10

Grub sees the installs on sda and sdc and starts them. I can't get the new install on sdb to appear on the grub  menu.

I have messed with a lot of things and may have a peculiar setup.  All partitions and drives show from inside the old ubuntu on sdc. I can't get UB64 to start.

---

### Post by absolutezero1287 on 2009-03-26
Why not edit the menu.lst file manually?

---

### Post by Old and Rusty on 2009-03-26
I am trying that right now but finding it a bit complex.

Must one provide all of the information for the new listing or can I just copy one of the 'sample' listings and modify it for my drive and partition?

---

### Post by absolutezero1287 on 2009-03-26
Just copy your existing entry for Ubuntu and modify it to your needs.

---

### Post by Old and Rusty on 2009-03-27
I copied the menu.lst from the new install into the one which grub seemed to be using and got instant access to Ubuntu 64 bit which grub did not see at all, formerly.  However the windows and old install of Ubuntu standard have problems.  XP just does not load and Ubuntu loads and seizes up with some references to video issues as it loads. I have looked through the menu.lst file and it looks ok but what do I know.

I love Ubuntu and will continue with it.  I would hate to have to format and reinstall and thereby lose all of the mods which this site has helped me build in.   Up till now standard Ubuntu 8.10 has been crisp and stable and full of goodies. 

I know I have tried enough things to get grub and my drives all muddled and I certainly do not blame the os or the community for my woes.

---

### Post by absolutezero1287 on 2009-03-27
> **Old and Rusty said:**
> I copied the menu.lst from the new install into the one which grub seemed to be using and got instant access to Ubuntu 64 bit which grub did not see at all, formerly.  However the windows and old install of Ubuntu standard have problems.  XP just does not load and Ubuntu loads and seizes up with some references to video issues as it loads. I have looked through the menu.lst file and it looks ok but what do I know.

I love Ubuntu and will continue with it.  I would hate to have to format and reinstall and thereby lose all of the mods which this site has helped me build in.   Up till now standard Ubuntu 8.10 has been crisp and stable and full of goodies. 

I know I have tried enough things to get grub and my drives all muddled and I certainly do not blame the os or the community for my woes.

Everyone's set up is different so naturally people are going to encounter issues. This is true for any OS.

With GRUB's menu.lst file you have to make sure that its pointing to the right stuff. In other words if you're kernel is in hd0,0 make sure that it is specified as such.

---

### Post by Old and Rusty on 2009-03-27
Thanks.  You have given me some interesting avenues to pursue. I'll let you know how things go.

---

### Post by Old and Rusty on 2009-03-27
I may have fixed a few items which may help but I don't know how to get terminal  and gedit to edit a protected file on another drive for the standard Ubuntu (which I can't get to start right NOW) 

I can edit but not save the changes. Terminal should let me do this but I simply don't know how to describe the path to the other drive. All I get is a blank file which means I have not found the appropriate path to say, "menu.lst"

 I know I will have some success in booting the other systems if I unplug some drives but that seems to cause other problems later on.
Hmmm.  Maybe I will try it and see.  You have given me a better understanding of what is going on and it may work now.

---

### Post by drs305 on 2009-03-27
If you are running ubuntu from the live cd, to gain access to your system fstab you need to create a mount point (or use an existing one) and mount your normal system partition onto it. Here is an example from the livecd Desktop. Open a terminal window and:
```

sudo mkdir /mnt/temp  # if it doesn't exist
sudo mount /dev/sdXX /mnt/temp  # replace sdXX with the actual location of your system partition, e.g. sdb1
cd /mnt/temp
gksudo gedit etc/fstab   # note no "/" before "etc"

```

Your *real* fstab should now appear. Make the changes, save and reboot.

---

### Post by Old and Rusty on 2009-03-27
This also will come in handy.  Thanks!

---

