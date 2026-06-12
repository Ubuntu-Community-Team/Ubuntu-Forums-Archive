---
title: "How to mount captured USB HDD in kububtu guest"
date: 2008-12-19
forum: General Help
---

### Post by sheoshanker on 2008-12-19
I have a installed kubuntu as a guest system in OpenSUSE host with VirtualBox.

After days of worrying and googling, I now have the shared folders working, my guest kubuntu system recognizes the host USB storage and I can capture them in the guest (there is x mark in those usb devices in the guest kubuntu & its state is shown as captured). Doing sudo lsub in the Kubuntu guest identifies the host USB Seagate Mass storage device as:

Bus 2 Device 3: ID 0bc2:0500 Seagate RSS LLC

However, even after two days of frantic searching for any help or advice on the Internet + VirtualBox site, I am unable to see the contents of those drives. I do not know how to mount them or how (by what name) to use them or to list them and copy files. I tried to mount it, following the case of virtual folder, using the name seagate (as the host devic). This the name that was given to this while creating the USB filters. That did not work. Then I tried mounting using the ID 0bc2:0500 (as the device to be mounted). This too did not work. THe problem seems to be that I do not knowto what /dev has kubuntu guest associated the "Bus 2 Device 3: ID 0bc2:0500 Seagate RSS LLC" and what do do in either the /etc/fstab or with xxx entry in

mount -t vfat -o [option] xxxxx /mnt/captured-usb

Thus I am lost. Please help. Internet search is going nowhere in this matter.

Thanks again., Sheo

---

