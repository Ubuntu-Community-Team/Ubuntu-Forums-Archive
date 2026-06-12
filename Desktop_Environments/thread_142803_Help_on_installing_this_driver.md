---
title: "Help on installing this driver"
date: 2006-03-11
forum: Desktop Environments
---

### Post by Jason7fd on 2006-03-11
It's a driver for Aztech DSL306U,I can't find a way to install it,please help me!

**Readme**
> This document describes the steps of installing the E2 or Hasbani on the Linux.
Driver Version Rel_1.11_4.1.0.20b_E.

A) Installing.

	1)	#rpm --rebuild USBENDPOINT-1.11-2.src.rpm
		if the command "rpm --rebuild" isn't supported by your 
		system, you can execute the following one:
		#rpmbuild --rebuild USBENDPOINT-1.11-2.src.rpm


	2)	#cd /usr/src/RPM/RPMS (Notes: the binary format RPM 
			should locate in one of its subdirectory according to your CPU type.)

		Find the binary RPM package, and execute the following command:
	3)	#rpm -e USBENDPOINT		----Remove the previous version
	4)	#rpm -i USBENDPOINT-1.11-2
	5)	#reboot

	The driver should be installed in directory "/usr/local/e2/". Finishing the installation,
	please reboot the PC to activate the driver.


B)Uninstalling
	1)	#rpm -e USBENDPOINT



**The files**
[http://rapidshare.de/files/15232647/USB_Endpoint_LINUX_REL_1.11_4.1.0.20b_E.zip.html]("http://rapidshare.de/files/15232647/USB_Endpoint_LINUX_REL_1.11_4.1.0.20b_E.zip.html")

---

