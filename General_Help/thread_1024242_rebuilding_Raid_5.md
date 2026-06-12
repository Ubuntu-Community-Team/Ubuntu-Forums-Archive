---
title: "rebuilding Raid 5"
date: 2008-12-28
forum: General Help
---

### Post by calvarymanagua on 2008-12-28
I had a Raid 5 with 4 drives using Fedora Core 6. My drive with my operating system failed, (not part of the Raid). So I installed Ubuntu on a new drive and am trying to rebuild the array. From what I have researched, it looks like it should go like this: (my drives are /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1)

1) mdadm --create /dev/md0 --level=5 --raid-devices=4 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1
2) mdadm --assemble /dev/md0 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1
3) mount /dev/md0 /mnt/Temp

Does this look like the correct way to go about it?

(I only want to build it once and mount it to get the data off of the array).

Thanks

---

### Post by fjgaude on 2008-12-29
No, no. I wouldn't do the --create... that will destroy all the data in the array.

Many have had troubles coming from Red Hat, Fedora, to Ubuntu with **mdadm** arrays.

Here's what I would do and see if it works. Just like this: delete or re-name /etc/mdadm/mdadm.conf. Then remove mdadm from the system using apt-get. Re-boot. Re-install mdadm and then use the command:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be generated and the array should mount to your mountpoint that you previously created.

---

