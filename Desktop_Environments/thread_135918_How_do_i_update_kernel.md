---
title: "How do i update kernel"
date: 2006-02-24
forum: Desktop Environments
---

### Post by imiksu on 2006-02-24
Very simple guestion and i hope there is a simple answer as well :) 

How do i update the newest kernel?

---

### Post by bluevoodoo1 on 2006-02-24
Update to the newest Linux kernel? Or, simply one newer than linux-image-2.6.12-10-386?... Which kernel are you using now anyway? 

(if it's the one newer than linux-image-2.6.12-10-386 then....)

Synaptic.

I went from "linux-image-2.6.12-9-386" to "linux-image-2.6.12-10-386" but simply installing linux-image-2.6.12-10-386. Search Synaptic for "linux-image" and download the newest one that is right for your system. That is all you have to do.

EDIT: edited for grammatical flow

---

### Post by az on 2006-02-24
[QUOTE=imiksu]Very simple guestion and i hope there is a simple answer as well :) 

How do i update the newest kernel?[/QUOTE]
Why?

Want bleeding edge?  Dist-upgrade to Dapper.

Something not working?  Look for a patch.

Bored?  Compile your own.  Look on the wiki for the kernel building howto.

---

### Post by LateNighter on 2006-02-24
If you have an AMD based PC look in Synaptic for the K7 kernals that fit your Machine.  Theres a discription below each File telling you what their for.

 If yours is Intel Based look for the i386 or i686 Kernals that are right for your machine.:-D 

 See that was simple enough I think....:-k

---

### Post by imiksu on 2006-02-25
No i'm not going to compile my own kernel... Anyway i did an dist-upgrade to breezy. Now i've got the 2.6.12-10-386-kernel version. After reboot (or start anyway) it's spamming this after "Loading, please wait..." -text:

__RUNTIME__ = runtime on secs, i think =)
> 
[__RUNTIME__] irq 14: nobody cared (try booting with the "irqpoll" option.
[__RUNTIME__] handlers:
[__RUNTIME__] [<cc8984a0>] (ide_intr+0x0/xed [ide_core])
[__RUNTIME__] Disabling IRQ #14


Now i'm using for temporary the 2.6.10-6-386... Anyway if someone know how to help me on this make sure there is allways an option that i can use the working version of kernel :KS

---

### Post by az on 2006-02-25
[QUOTE=imiksu]No i'm not going to compile my own kernel... Anyway i did an dist-upgrade to breezy. Now i've got the 2.6.12-10-386-kernel version. After reboot (or start anyway) it's spamming this after "Loading, please wait..." -text:

__RUNTIME__ = runtime on secs, i think =)


Now i'm using for temporary the 2.6.10-6-386... Anyway if someone know how to help me on this make sure there is allways an option that i can use the working version of kernel :KS[/QUOTE]

Edit your menu.list and add this the the line:

sudo gedit /boot/grub/menu.list

# nonaltoptions=quiet splash irqpoll


Then run 
sudo update-grub

---

### Post by SigMtnDawg on 2006-02-25
sudo gedit /boot/grub/menu.lst only returns the message:
(gedit:11497) Gtk-WARNING **: cannot upen display:

meanwhile the 'nobody cared..."irqpoll"' comment scrolls over and over, virtually killing all effectiveness of the machine.

please help this newbie!!

---

### Post by imiksu on 2006-03-14
[QUOTE=SigMtnDawg]sudo gedit /boot/grub/menu.lst only returns the message:
(gedit:11497) Gtk-WARNING **: cannot upen display:

meanwhile the 'nobody cared..."irqpoll"' comment scrolls over and over, virtually killing all effectiveness of the machine.

please help this newbie!![/QUOTE]

If you are using terminal, you should try: sudo nano /boot/grub/menu.lst

---

