---
title: "Networking Dilema"
date: 2006-04-06
forum: Desktop Environments
---

### Post by indytim on 2006-04-06
I'm at the point where I could use some expert advice on how to proceed.

I'm in the process of getting my wife's new-build pc (P4) up and running with Ubuntu (Breezy 5.10).  The area that I'm having great difficulty with is in mounting a windows share folder on my principal PC (WIN2000 SP4).  I have samba installed and running.  I have been able to access the network printer connected to the Win2000.  I have a development box (P3) with Ubuntu Breezy 5.10 connected through the same router and it's able to mount the windows folders without any difficulty.  What I get after going through the Connect to Server utility, is an error message "Can't open the folder" when accessing the mounted folder on the desktop.

Using iconfig, I get an ip of 192.168.1.102 on both boxes running Ubuntu.  I checked the firewall (ZoneAlarm on the Win2K) and the ip is a trusted site.  I suspect something is amiss with a setup on the new box.  I'm attaching the fstab below as it is a usual question on newtworking problems that I've seen posted on the boards.

Thanks in advance for the help.

IndyTim


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by ranf on 2006-04-07
[QUOTE=indytim]
Using iconfig, I get an ip of 192.168.1.102 on both boxes running Ubuntu.[/QUOTE]

Two computers in the same subnet with identical IP address? That won't work.

---

### Post by indytim on 2006-04-07
Thanks ranf,

That makes sense.  When I set up the pc orginally, it was on a different port on the router (where the dev box is currently).  

My question at this point is, is there any way to "force" ubuntu to identify the current ip.  Otherwise, I'm probably faced with a clean-sweep and re-install (which is no biggee).

Thanks,

IndyTim

---

### Post by ranf on 2006-04-07
[QUOTE=indytim]
My question at this point is, is there any way to "force" ubuntu to identify the current ip.  
[/QUOTE]
I don't understand what you mean here.

Do you use static IPs or are they assigned via DHCP (from the router)?

[QUOTE=indytim]
Otherwise, I'm probably faced with a clean-sweep and re-install (which is no biggee).
[/QUOTE]
For simply changing the IP you won't have to reinstall.

---

### Post by indytim on 2006-04-08
The final word... it was Firestarter;)   I just took the firewall down and was able to establish a connection with the Win2K box. Now to selectively restart Firestarter and find the correct options to allow everything to stay happy.

IndyTim

---

