---
title: "[SOLVED] Booting entries. Lots of 'em"
date: 2008-12-12
forum: General Help
---

### Post by GrimmReaperVI on 2008-12-12
Guys, I've got a small problem for you O:)
Every time I update my ubuntu, another entry pops out in the booting screen. Kind of like :
"Ubuntu version, date of update"
Well, i'm sick of it!!
Any idea how to fix this from happening and removing the spare entries?

---

### Post by pedro_orange on 2008-12-12
Try:

```
gksudo gedit /boot/grub/menu.lst
```

That should have all your kernel updates in. Just comment them out if you don't want them to appear when you boot up.

---

### Post by GrimmReaperVI on 2008-12-12
Well, I can see the updates. How exacly do I "comment them out"?

---

### Post by drs305 on 2008-12-12
I have an easy solution which won't require manually editing the menu.lst. Install StartUp-Manager and then you can specify how many kernels to view and which one to start up by default. StartUp-Manager will allow you to safely tweak many more grub options.

Here is the tutorial:
[Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Although I recommend StartUp-Manager, in answer to the previous post, you comment them out by placing a # symbol at the start of the line. Note that unlike many other files, there are lines in grub which begin with a ***single*** # that ARE acted upon - those within the "### BEGIN AUTOMAGIC KERNELS LIST" to the end of the section.

To comment out an entire choice, you would place a single # symbol at the start of each line in the section, for instance:
```

#title		Xubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb10)
#root		(hd1,5)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=27419546 ro #noapic vga=769  
#initrd		/boot/initrd.img-2.6.27-7-generic
#boot


```

---

### Post by Elfy on 2008-12-12
You can stop it happening by not letting the kernel update - but I wouldn't recommend it. Each time that the kernel is updated the new kernel is added to your menu list.

I like to keep at least one old one there, in that way if there is any problem with the new kernel you can still use the previous.

Commenting them out in the menu list removes them from the menu list but doesn't actually remove them from the system - you can find all the kernels you have installed - search in synaptic for linux-image - if you remove them there then menu list is updated as part of the process.

You can use any of the editing apps to edit the file, gedit in ubuntu, kate in kubuntu, leafpad in xubuntu, but you need to have root rights to do so - in ubuntu

```
gksudo gedit /boot/grub/menu.lst
```

Putting a # at the start of a line will comment it - it will no longer appear in the list

It is a good idea to backup files before you edit them - if you make a mistake it's not necessarily easy to get it sorted.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.1212
```

would copy the file to a new one named menu.lst.1212

It is also possible to use start up manager to look after your menu and kernels - I personally prefer to do so myself, but the information for it can be found here

[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

### Post by GrimmReaperVI on 2008-12-12
Thanks guys! The start-up manager sloved my problem completely and got rid of that pesky memtest as a bonus! Problem sloved!

---

