---
title: "Permission on hard drive problem"
date: 2009-05-01
forum: General Help
---

### Post by xi_Slick_ix on 2009-05-01
Hi

I have ubuntu (8.04) installed on my desktop in a 20GB partition.  Its a 320GB Hard Drive, and the rest of the space was unpartitioned.  So I opened partition manager, and partitioned 200GB for a media drive.  The partitioning went fine, but I apparently don't have permission to write to the drive.  Tried making myself root and it still won't let me write to it.

Any suggestions?
Thanks

---

### Post by SentientFluid on 2009-05-01
Open Terminal and type ```
gksudo nautilus
```

You should have to enter your password.

In the window that opens find your new media drive.

Right click it and choose Properties.

Select Permissions tab.

Set all the permissions to Read and Write and make sure to apply to enclosed folders.

Close all windows and restart.

---

### Post by DGortze380 on 2009-05-01
> **xi_Slick_ix said:**
> Hi

I have ubuntu (8.04) installed on my desktop in a 20GB partition.  Its a 320GB Hard Drive, and the rest of the space was unpartitioned.  So I opened partition manager, and partitioned 200GB for a media drive.  The partitioning went fine, but I apparently don't have permission to write to the drive.  Tried making myself root and it still won't let me write to it.

Any suggestions?
Thanks

can you post the output of

```

cat /etc/fstab

```

```

fdisk -l

```

---

### Post by kernel_script on 2009-05-01
Additionally, if you want to learn more about permissions on GNU/Linux: [http://linux.about.com/od/linux101/a/desktop03b.htm](http://linux.about.com/od/linux101/a/desktop03b.htm)

---

### Post by spiderbatdad on 2009-05-01
You may be able to solve this problem without touching fstab. Try System >> Administration >> Login Window. Go to the security tab and check "Allow Local System Administrator Login."

---

### Post by xi_Slick_ix on 2009-05-01
Success! Thank You everyone!

```
gksudo nautilus
```

Worked wonderfully, Just fixed the permissions and restarted - copying about 160GB worth of data now...

---

### Post by SentientFluid on 2009-05-01
> **xi_Slick_ix said:**
> Success! Thank You everyone!

```
gksudo nautilus
```

Worked wonderfully, Just fixed the permissions and restarted - copying about 160GB worth of data now...


Glad it helped you out.  You can always create a launcher for it in case you need quick access as root.  You'll still need to enter your password each time of course, but you won't always need to open Terminal.

---

