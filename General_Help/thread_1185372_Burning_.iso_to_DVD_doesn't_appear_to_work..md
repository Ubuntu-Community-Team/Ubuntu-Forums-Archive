---
title: "Burning .iso to DVD doesn't appear to work."
date: 2009-06-12
forum: General Help
---

### Post by krusadr on 2009-06-12
Hi, I'm trying to burn an .iso onto a dvd (Windows 7 ~ 2.5GB); I right click on the .iso and select write to disk which then opens up a seperate window and allows me to start burning the iso to the DVD.

This appears to work without any problems, but once the operation is complete the DVD appears to be empty, and when I attempt to install Windows 7 (restart > boot to CD) nothing happens. 

I've mounted the ISO using 
```
sudo mount -o loop -t auto file.iso /mount/iso
```
Which has worked, and I can see all the files so I know the .iso file is okay.

Any help would be greatly appreciated.

*Note ~ I'm attempting to dual boot; I'm not replaceing Ubuntu ;)

---

### Post by colau on 2009-06-12
> **krusadr said:**
> Hi, I'm trying to burn an .iso onto a dvd (Windows 7 ~ 2.5GB); I right click on the .iso and select write to disk which then opens up a seperate window and allows me to start burning the iso to the DVD.

This appears to work without any problems, but once the operation is complete the DVD appears to be empty, and when I attempt to install Windows 7 (restart > boot to CD) nothing happens. 

I've mounted the ISO using 
```
sudo mount -o loop -t auto file.iso /mount/iso
```
Which has worked, and I can see all the files so I know the .iso file is okay.

Any help would be greatly appreciated.

*Note ~ I'm attempting to dual boot; I'm not replaceing Ubuntu ;)

Probably this is the command
```

mount -t iso9660 /path/to/Fedora10.iso /mnt/point -o loop

```

---

### Post by sedawk on 2009-06-12
I hope you have a hardware firewall (e.g. inside your DSL router),
otherwise installing beta software like Win7 is a bad idea - wait
for Service Pack 2 ;-)

If you want to have a look at Win7 I recommend to do it inside
a virtual PC, e.g. have a look at VirtualBox.

With a virtual PC you do not need to burn the DVD, you can directly
use the iso image.

But back to your DVD problem: have a look at the "backside" of your
DVD - does it look like it is half full of data?
Or does it still look like an unused one?.
(If you enter the DVD - do you still get the "blanc disc inserted
 pop-up message or not?).

---

### Post by krusadr on 2009-06-12
I think I'll probablly end up running it inside a virtual machine; I've already used the beta but I wanted to dual boot with Windows 7 and Ubuntu; It was only once I'd formated my hard drive that I realised I'd already written over the DVD I had of Windows 7.

A side note on using a virtual machine then; Is it possible to install Windows 7 onto a seperate partiton using a virtual machine? (Does that make sence :p) 

Basically I've already partitioned my hard drive into 2 parts (each 40GB) so If I install VMWare (or whatever) can I use the second partition to install Windows to, and then access it from within the VM?

---

### Post by krusadr on 2009-06-12
> **sedawk said:**
> 
But back to your DVD problem: have a look at the "backside" of your
DVD - does it look like it is half full of data?
Or does it still look like an unused one?.
(If you enter the DVD - do you still get the "blanc disc inserted
 pop-up message or not?).

It looks as if data has been written to it, but when I insert the DVD it shows it as empty with no files (although I can't then use the DVD).

** Edit **

Sorted, I'm not sure exactly what the problem was but I think it's because I'd downloaded the .iso in windows and then stored in my external hard drive before trying to burn it in ubuntu. I've then re-downloaded the windows 7 iso and it worked perfectly. The only problem was I wasn't thinking straight and installed Ubuntu first, then Windows 7 so I'm currently sorting out Grub xD

---

