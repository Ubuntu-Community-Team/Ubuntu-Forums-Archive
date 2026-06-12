---
title: "Palm tungsten syncro"
date: 2009-02-21
forum: General Help
---

### Post by fabio61 on 2009-02-21
I have been trying to synchronize my tungsten T3 with my desktop all day now, but nothing works, no jpilot, no evolution, no gnome-pilot.
I completed the procedure I used successfully on other computers but here does not work.
My operative system is ubuntu 8.04. Here is what I have done so far:


		# /sbin/modprobe uhci_hcd
		# /sbin/modprobe ehci_hcd

		# /sbin/modprobe usbserial
		# /sbin/modprobe visor

a lsmod includes:

Module                  Size  Used by
visor                  18572  0 
usbserial              35688  1 visor
lp                     12324  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 


then I created the inodes with:

		# /bin/mknod /dev/ttyUSB0 c 188 0
		# /bin/mknod /dev/ttyUSB1 c 188 1

and gave them permissions with:

		# /bin/chmod 0666 /dev/ttyUSB?

however when I hit the sync button I get an error message stating that the connection is not possible. After several attempts I went into /dev and I found out that the devs ttyUSB0 and ttyUSB1 are not there!

any suggestion?

---

