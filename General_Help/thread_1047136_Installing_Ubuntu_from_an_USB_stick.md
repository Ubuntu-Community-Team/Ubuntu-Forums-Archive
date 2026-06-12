---
title: "Installing Ubuntu from an USB stick?"
date: 2009-01-22
forum: General Help
---

### Post by bigpilot on 2009-01-22
I have just received a netbook computer which has a hard disk but no CD-ROM drive. I would like to install Kubuntu or Xubuntu on it (it has 1GB of RAM). Is there a way to install Kubuntu from a flash drive? Is it possible to write the .iso to a flash drive and boot from it?

---

### Post by SteveDee on 2009-01-22
> **bigpilot said:**
> I have just received a netbook computer which has a hard disk but no CD-ROM drive. I would like to install Kubuntu or Xubuntu on it (it has 1GB of RAM). Is there a way to install Kubuntu from a flash drive? Is it possible to write the .iso to a flash drive and boot from it?

On a working version of Ubuntu 8.10 you can create a bootable USB stick via System > Administration > Create a USB startup disk....not sure what you have available on the other 'buntus though.

---

### Post by Archmage on 2009-01-22
> **SteveDee said:**
> Create a USB startup disk.

I think you need to install the package usb-creator, if you didn't find it.

---

### Post by bigpilot on 2009-01-26
I found usb-creator, thanks. But I also found out it only seems to work for Ubuntu. Is there a similar way to do this for Xubuntu and or Kubuntu?

I tried Xubuntu (xubuntu-8.10-alternate-i386.iso), but as soon as I select the .iso the flash drive adds a 'Stop' sign to in front of the drive's name. I reckon it only works for Ubuntu.

---

### Post by boof1988 on 2009-01-26
> **bigpilot said:**
> I found usb-creator, thanks. But I also found out it only seems to work for Ubuntu. Is there a similar way to do this for Xubuntu and or Kubuntu?

I tried Xubuntu (xubuntu-8.10-alternate-i386.iso), but as soon as I select the .iso the flash drive adds a 'Stop' sign to in front of the drive's name. I reckon it only works for Ubuntu.

My (very limited) experience has been that the iso has to be one that has a Live-Desktop or similar feature.  So, from my experiance, the USB-Creator will not work with the Alternative-Install iso file.  Maybe USB-Creator (for now) only supports the Live-Desktop type of environments?

HTH...

---

### Post by Stefanie on 2009-01-26
have a look at unetbootin. i have used this to install intrepid, ubuntu eee and arch on my eee. for me it worked very well but i had to format my usb stick to fat 32.

---

### Post by boof1988 on 2009-01-26
> **Stefanie said:**
> have a look at unetbootin. i have used this to install intrepid, ubuntu eee and arch on my eee. for me it worked very well but i had to format my usb stick to fat 32.

+1 for Unetbootin... I have had a lot of success with it.

---

### Post by bigpilot on 2009-02-19
I just tried Unetbootin but it doesn't work. It creates the USB flash drive but when I try to boot from the USB flash drive I get the error message:

'Cannot find NTLDR'

The laptop has FreeDOS on it and I'm trying to install Xubuntu on it. 

Any ideas?

---

