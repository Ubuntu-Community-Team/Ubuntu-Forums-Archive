---
title: "make a boot disk"
date: 2005-08-06
forum: Desktop Environments
---

### Post by michellembrodeur on 2005-08-06
I am trying to install kubuntu on a old system.

But I need a bootdisk. mkrboot and mkboot wants lilo stuff. I have grub.

So how do I make a boot disk to install kubuntu. It will not boot from CD. bios is too old.

thanks

---

### Post by varunus on 2005-08-06
Use "Smart Boot Manager" for this purpose, its a floppy that once you boot from it, will let you boot any drive in your computer.

[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

I've used it for an older computer.

---

### Post by michellembrodeur on 2005-08-06
[QUOTE=varunus]Use "Smart Boot Manager" for this purpose, its a floppy that once you boot from it, will let you boot any drive in your computer.

[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

I've used it for an older computer.[/QUOTE]

tried this. it does not see the cdrom. but win98 bootdisk does.

See the control card is a isa controller card for the cdrom and harddrive. ITs really old.

So the bios do not see anything, but the win98 bootdisk actually searches for drivers.

Seems that Smart Boot Manager read the bios and does not actually search. I can type int he Hex nubmer of the port, but what is the hex number of the cdrom? beats me.

is there a soemthing to type if I use the boot98 disk and see the cdrom to get it to start installing?

thanks

---

### Post by rogerdean on 2005-08-09
hey michelle
i have the same problem with smart boot manager. it starts fine but does not see my pcmcia cdrom (thinkpad 240 with external everything). did you find a solution to this?
allbest
roger

---

### Post by michellembrodeur on 2005-08-09
[QUOTE=rogerdean]hey michelle
i have the same problem with smart boot manager. it starts fine but does not see my pcmcia cdrom (thinkpad 240 with external everything). did you find a solution to this?
allbest
roger[/QUOTE]

I have not found one yet.

Seems no one on any forum, and I have asked on a lot of them, can solve this.

---

