---
title: "System -&gt; READ-ONLY"
date: 2006-08-16
forum: Desktop Environments
---

### Post by ahamino on 2006-08-16
Hi all,

I am using ubuntu from a while now. seriously it was awesome until recently my computer repeatedly changes to read only mode where i can't write anything to the harddisk even in my home dir (when i reboot it works fine for a short while then repeat again).
 
When i execute any program in read only state for example gmone-rdp the output is

---------------------------------

** (/usr/lib/gnome-rdp/gnome-rdp.exe:11743): CRITICAL **: _wapi_shm_file_open: shared file [/home/ahamino/.wapi/shared_data-ahamino-desktop-Linux-i686-308-10-0] open error: [COLOR="Red"]Read-only file system[/COLOR]

-------------------------------

when i had a look at my kern.log I found that following

-------------------------------

Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: status error: status=0x00 { }
Aug 17 02:04:55 localhost kernel: [17191003.484000] ide: failed opcode was: unknown
Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: drive not ready for command
Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: status error: status=0x00 { }
Aug 17 02:04:55 localhost kernel: [17191003.484000] ide: failed opcode was: unknown
Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: drive not ready for command
Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: status error: status=0x00 { }
Aug 17 02:04:55 localhost kernel: [17191003.484000] ide: failed opcode was: unknown
Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: drive not ready for command
Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: status error: status=0x00 { }
Aug 17 02:04:55 localhost kernel: [17191003.484000] ide: failed opcode was: unknown
Aug 17 02:04:55 localhost kernel: [17191003.484000] hda: DMA disabled
Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: DMA disabled
Aug 17 02:04:55 localhost kernel: [17191003.484000] hdb: drive not ready for command
Aug 17 02:04:55 localhost kernel: [17191006.796000] ide0: reset: success
Aug 17 02:06:51 localhost kernel: [17191122.896000] hdb: status error
-------------------------------------------

I am in a state of a panic, I am afraid it might be a hardware failure and i lose my data.

Please someone HELP!
regards,
Ahamino

---

### Post by cptnapalm on 2006-08-16
If it can be mounted read-only, then all is not lost on the data loss front.  Didn't mean to make a pun.  If you have a burner, CD or DVD or have a way to copy files over a network to another machine, *now* would be the time to do it.

---

### Post by ahamino on 2006-08-18
then, what is happening to my computer? IS this error a result of faulty hardware or is it a problem with the kernel

---

