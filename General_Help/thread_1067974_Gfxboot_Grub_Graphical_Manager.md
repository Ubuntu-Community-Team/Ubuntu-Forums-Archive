---
title: "Gfxboot Grub Graphical Manager?"
date: 2009-02-12
forum: General Help
---

### Post by archeryguru2000 on 2009-02-12
Hello all, I was wondering if anybody was aware of an application to manage (i.e. create, install, modify, etc.) gfxboot graphics?  I was hoping there would be something on the lines of **_[Gsplashy]("http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25")_** for splashy management.  I have created a few gfxboot images, but trying to make them work properly and then rebooting to view them, then make some more modifications (and repeat!) is a tedious task.  It would be nice if somebody would have (or is willing to) create a GUI (or CLI for all I care) application that would display the gfxboot menu (as it is during boot-up) to check for errors/obstacles/modifications/etc.  Also, from a CLI (with splashy) one could simply type "splashy test" to check for errors.  Please let me know if anybody knows of anything like this.  I would also appreciate knowing if anybody is even working on something like this.

Thanks,
~~archery~~

---

### Post by archeryguru2000 on 2009-02-18
bump, anybody?


~~archery~~

---

### Post by archeryguru2000 on 2009-02-18
OK, I've found [**_this page_**]("http://en.opensuse.org/Gfxboot") on openSUSE's web-site.  This page states that the command gfxboot --preview will give the user a preview of the boot menu in operation.  However, here's what is displayed when I issue the command.
```

$: gfxboot --help
bash: gfxboot: command not found
$: gfxboot --preview
bash: gfxboot: command not found
$: gfxboot --test
bash: gfxboot: command not found

```
With or without super user privileges.  I wonder if there is some reference missing somewhere.  :-k  Does anybody have any ideas.  Can anybody verify if they can issue any of these commands.  Thanks for any assistance.

~~archery~~

---

### Post by archeryguru2000 on 2009-02-19
This is quite interesting.  I have gfxboot installed... works just fine... but the return on this command is puzzling!?!  
```

$: man gfxboot
No manual entry for gfxboot

```
Shouldn't there be some sort of man pages associated with this program?  I'm sure somebody out there must know what I'm talking about... right?  Anybody out there?

~~archery~~

---

### Post by grndslm on 2009-02-19
Clearly, "bash: gfxboot: command not found" was a hint that it wasn't installed yet.

I'm not sure about the man page, but not all apps have them.  Sometimes there's a help switch built in, like -h or --help ... so, try:

gfxboot --help

---

### Post by UbNewbie on 2009-02-20
> **archeryguru2000 said:**
> This is quite interesting.  I have gfxboot installed... works just fine... but the return on this command is puzzling!?!  
```

$: man gfxboot
No manual entry for gfxboot

```
Shouldn't there be some sort of man pages associated with this program?  I'm sure somebody out there must know what I'm talking about... right?  Anybody out there?

~~archery~~

Hi Archery,

As far as I know and also reading the Opensuse link, you need gfxboot-devel package for that. Unfortunately that package is not available for ubuntu/debian.

So the only way to test it is just include your /boot/grub/message.* in your menu.lst and reboot your machine.. BTW you need first to install the approriate grub-gfxboot for that. Normal grub doesn't support that.

Hope this help.

Regards,

H2T

---

### Post by archeryguru2000 on 2009-02-23
> **grndslm said:**
> Clearly, "bash: gfxboot: command not found" was a hint that it wasn't installed yet.

I'm not sure about the man page, but not all apps have them.  Sometimes there's a help switch built in, like -h or --help ... so, try:

gfxboot --help

Actually, that hint failed.  I have gfxboot installed... and it works great.  I'm just hoping that I could create a couple of newer boot-up screens (which I have several already, but customization is what I'm truly after) and then view the changes without having to reboot the machine.  I'm not necessarily against rebooting my computer... but let's face it, that's one of the reasons (one of the many) that I dumped Windoze for Linux.  Another reason was the customization capabilities.  However, thanks for the suggestions on the -h and --help.  However, neither of those produced any real results either.

~~archery~~

---

### Post by archeryguru2000 on 2009-02-23
> **UbNewbie said:**
> Hi Archery,

As far as I know and also reading the Opensuse link, you need gfxboot-devel package for that. Unfortunately that package is not available for ubuntu/debian.

So the only way to test it is just include your /boot/grub/message.* in your menu.lst and reboot your machine.. BTW you need first to install the approriate grub-gfxboot for that. Normal grub doesn't support that.

Hope this help.

Regards,

H2T

Thank you very much for this input.  I didn't even notice the -devel package requirement on the openSUSE webpage.  Dang-it!  ](*,)  I appreciate the heads-up on that however.  I may try to find a way to manually install that devel package from the openSUSE directory.  [-o<  I'll keep you all posted of my progress.

~~archery~~

---

