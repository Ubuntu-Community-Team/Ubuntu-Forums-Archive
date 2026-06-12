---
title: "Accessing Windows RAID1"
date: 2009-04-22
forum: General Help
---

### Post by j_freeman on 2009-04-22
I'm in the process of migrating to Ubuntu as my main OS, but there's only one last thing left: being able to access my Windows RAID (mirror) from Ubuntu.

I've probably researched this 6 hours, yet I haven't come up with a solid solution. I know you can create a new RAID from within the alternate installation, but I haven't found a way to access an existing Windows RAID.

I don't mind having Ubuntu manage the RAID, as long as 1) I can keep my data and 2) can access the RAID from Windows now and then.

The RAID is a software RAID provided by the Intel ICH10R chipset on **[this]("http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2916&ProductName=GA-EP45-UD3R")** motherboard.

Any ideas?

---

### Post by fjgaude on 2009-04-23
Well, a program called **dmraid** lets you do just what you wish. Do a goggle on it and see if it will.

---

### Post by j_freeman on 2009-04-24
fjgaude, thanks but I had researched dmraid for hours, but I didn't have any luck with that.

I decided just to move my RAID over to a FreeNAS server and access it over SMB from all my computers. Probably a better solution in the long run anyway.

I know this isn't the venue for suggestions, but it sure would be nice if Ubuntu had an idiot-proof pretty GUI to setup and manage software RAIDs (existing and new). Maybe one day. ;)

---

### Post by fjgaude on 2009-04-24
Here's some links, many use dmraid to access Windows raid arrays:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://users.telenet.be/mydotcom/how...skfakeraid.htm](http://users.telenet.be/mydotcom/how...skfakeraid.htm)

Good luck with whatever you do.

Here's a shot at linux software raid using mdadm:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

---

### Post by ronparent on 2009-04-24
Just a quick note. 'dmraid -ay' worked if you have the directory /dev/mapper/. Therein you would find all of your raid1 windows partitions (the symbolic links at any rate). You need merely to attach them to mount point in /etc/fstab you have created in the file system for that porpose. I initially struggled with this problem for some time until I finally hit upon this solution. I can provide particulars if you need.

---

