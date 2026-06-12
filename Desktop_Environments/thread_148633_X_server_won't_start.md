---
title: "X server won't start"
date: 2006-03-22
forum: Desktop Environments
---

### Post by Capilano on 2006-03-22
Hello people

I have this situation where Xserver wil not automatically start. After the initial start up, it tells me taht it caanot start X. However, once I log in I can have access to X with the following command:

mount -n -o remount -t ext3 /dev/hda1 /

After that, X starts as usual. I have search forums but cannot pinpoint the answer. Please if you can hel

---

### Post by Ramses de Norre on 2006-03-22
How does your /etc/fstab look like? Seems like your root filesystem gets mounted incorrectly.

---

### Post by Capilano on 2006-03-22
Thank you Ramses de Norre.

Here is my /etc/fstab file:

/dev/hda1      	 			/               		ext3    defaults,errors=remount,ro 	0       1
/dev/hda5      	 			none            		swap    sw              		0       0
/dev/hdc        			/media/cdrom0   		udf,iso9660 user,noauto     		0       0
192.168.0.102:/shares/hdc1		/mnt/storage1			nfs    	rw	 			0       0
192.168.0.102:/shares/hdd1		/mnt/storage2			nfs    	rw	 			0       0
192.168.0.102:/shares/hdd3		/mnt/storage3			nfs    	rw	 			0       0
192.168.0.102:/shares/hde1		/home/serge/windows1		vfat    rw	 			0       0
192.168.0.102:/shares/hde5		/home/serge/windows2		vfat    rw	 			0       0
192.168.0.102:/shares/hdh1		/mnt/storage4			nfs    	rw	 			0       0
192.168.0.102:/shares/hdh2		/mnt/storage5			nfs    	rw	 			0       0
192.168.0.102:/shares/hdh3		/mnt/storage6			nfs    	rw	 			0       0
/dev/fd0				/media/floppy			auto	rw,noauto,user,sync		0 	0

---

### Post by claes on 2006-03-22
[QUOTE=Capilano]Thank you Ramses de Norre.

Here is my /etc/fstab file:

/dev/hda1      	 			/               		ext3    defaults,errors=remount,ro 	0       1
[/QUOTE]

That line should be changed so it looks like this:
/dev/hda1      	 			/               		ext3    defaults,errors=remount-ro 	0       1

And then it should work.

Claes

---

### Post by Capilano on 2006-03-22
Thank you kindly Claes.

---

### Post by claes on 2006-03-23
Glad I could help.

Claes

---

