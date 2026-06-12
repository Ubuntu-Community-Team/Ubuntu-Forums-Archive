---
title: "ubuntu default runlevel"
date: 2011-02-16
forum: Desktop Environments
---

### Post by ubun2warrior on 2011-02-16
hi

i do not want the graphical boot in ubuntu and want to change my default runlevel to 3(i suppose that is correct...) 

i am using ubuntu 10.10.

i have tried /etc/inittab its not working here.

plz tell me how should i do it.

rgds
ubun2warrior

---

### Post by inobe on 2011-02-16
more specific way but it's in there.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ubun2warrior on 2011-02-16
hi 

i want a more simple way of doing this. all i want is that the default runlevel is 3 and if i want to revert back i can do so easily.
actually i don't want the ubuntu splash screen and the ubuntu log in screen.

rgds

---

### Post by sisco311 on 2011-02-16
Ubuntu uses [Upstart]("http://upstart.ubuntu.com/"). Runlevels are still emulated, but just like in Debian, by default, runlevels 2,3,4, and 5 are the same.

If you want to disable the display manager, then use the **text** kernel parameter. Edit the file **/etc/default/grub** and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"** and generate a new Grub config file:
```
sudo update-grub
```

---

### Post by ubun2warrior on 2011-02-22
> **sisco311 said:**
> Ubuntu uses [Upstart]("http://upstart.ubuntu.com/"). Runlevels are still emulated, but just like in Debian, by default, runlevels 2,3,4, and 5 are the same.

If you want to disable the display manager, then use the **text** kernel parameter. Edit the file **/etc/default/grub** and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"** and generate a new Grub config file:
```
sudo update-grub
```

hi

thanks a lot this just did what i wanted !!!

rgds

---

