---
title: "Boot to Shell"
date: 2009-01-28
forum: General Help
---

### Post by echo8413 on 2009-01-28
I've been trying the basic steps to boot directly to the shell.

sudo rm /etc/rc3.d/S13GDM

it says I don't have this file, so I moved to the next step

gksu gedit /etc/inittab

gksu is not found so I can't even edit the file in order to do this is there any other possible way to boot straight to the shell.

---

### Post by echo8413 on 2009-01-28
also I've observed when I go into the /etc directory through the GUI that the inittab file isn't even there?

---

### Post by sedawk on 2009-01-28
Temporarily:
Interrupt the boot process and edit the boot entry. Edit the line
starting with "kernel" append the word "text" at the end of the line
and then boot.

Permanently:
Edit the kernel line(s) in /boot/grub/menu.lst and append the
word "text" to the end of the line. As you need to be root to
edit that file try "sudo gedit /boot/grub/menu.lst" or
"sudo vi /boog/grub/menu.lst", depending on your favourite editor.
Keep in mind that this change will be gone when menu.lst is recreated,
or you overwrite menu.lst during upgrades.
(You can create your own boot entries by cloning existing ones and
 but them outside the AUTOMAGIC block in menu.lst)

---

### Post by oldos2er on 2009-01-28
> **echo8413 said:**
> also I've observed when I go into the /etc directory through the GUI that the inittab file isn't even there?

 Ubuntu uses the upstart system now, so no inittab. Though I've read on this forum that if you create an inittab, Ubuntu will respect it.

---

### Post by echo8413 on 2009-01-28
how would I go about creating an inittab?

---

### Post by oldos2er on 2009-01-28
sudo nano /etc/inittab

---

### Post by icanfly0307 on 2009-01-28
okay, i'm guessing that you want to boot to a shell prompt whenever your computer boots up. here's what to do:

1. sudo apt-get install sysv-rc-conf
2. sudo sysv-rc-conf
3. scroll down and unselect the GDM 'X's from all runlevels
4. reboot and you should be dropped directly to a shell login prompt.

---

### Post by mb_webguy on 2009-01-28
> **sedawk said:**
> Temporarily:
Interrupt the boot process and edit the boot entry. Edit the line
starting with "kernel" append the word "text" at the end of the line
and then boot.

Permanently:
Edit the kernel line(s) in /boot/grub/menu.lst and append the
word "text" to the end of the line. As you need to be root to
edit that file try "sudo gedit /boot/grub/menu.lst" or
"sudo vi /boog/grub/menu.lst", depending on your favourite editor.
Keep in mind that this change will be gone when menu.lst is recreated,
or you overwrite menu.lst during upgrades.
(You can create your own boot entries by cloning existing ones and
 but them outside the AUTOMAGIC block in menu.lst)

I'd like to second this as being the easiest way to boot into a console.  I just did it myself, copying the regular Ubuntu menu item outside of the Automagic kernels list, then adding "text" to the kernel line and changing the title to indicate that it was a console boot, and it worked perfectly -- no need to mess with runlevels or delving into obscure files and commands.  Just a simple edit of GRUB does the job.

Of course now I'm going to have to change my motd, but c'est la vie. ;)

---

