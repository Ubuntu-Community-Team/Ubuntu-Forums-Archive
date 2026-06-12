---
title: "[SOLVED] acces right changed after FAT--&amp;gt;NTFS"
date: 2008-11-29
forum: Desktop Environments
---

### Post by sksbir on 2008-11-29
hello

I use an external disk formerly formatted in FAT32, and recently reformatted in NTFS.

When it was FAT32, this disk was mounted by nautilus when plugged in, and the acces right were : UId=1000, Gid=1000, umask=077

Now it is NTFS, and the disk is still mounted by nautilus, but acces right are : Uid=root,Gid=root, and umask=000

This is a real problem for me because I'm using unison to synchronise data on this disk.

If somebody have an idea how to control the behaviour of nautilus, It would be great.

thanks :)

---

### Post by hiflyer on 2008-11-29
looks like you need to modify /etc/fstab mounting this drive out of there with the options you wish. The options can be found in man mount.

---

### Post by sksbir on 2008-11-29
> **hiflyer said:**
> looks like you need to modify /etc/fstab mounting this drive out of there with the options you wish. The options can be found in man mount.

Thank you for your quick response :).

But I have nothing specified in /etc/fstab. My problem is about external disk which is plugged in after ubuntu is started, and mounted by Nautilus and not at boot time.

I know that it's possible to add some specification in /etc/fstab, but I use several external disks, and thus, the device name will change from one time to another.

Ok, I know that it's possible to specify an UUID instead of device name, but..wow.. it's like killing a fly with a machine gun :D ... I'd prefer to know where the problem exactly come from.
I consider it like a regression : having an umask of 000 for the default behaviour is not a really good idea. You don't think so ? ;)

Out of that, I don't want to change my fstab every time I have a new disk :)

---

### Post by sksbir on 2008-11-30
back with the solution.

1/ plug the volume
2/ right clic on it
3/ clic on properties
4/ clic on "volume"
5/ clic on "parameters"
6/ add on "mount option" line the parameters you want to.
I added this options : umask=077,uid=1000,gid=1000
7/ unplug and plug the external disk again for the new parameters to be activated.

Just for you knowledge : 
This action add a new directory in your profile:
~/.gconf/system/storage/volumes/_org_freedesktop_Hal_devices_volume_uuid_A88A492E8A48FA78  ( the uuid is the one from my disk )

In this folder,I find a file: %gconf.xml

```
<?xml version="1.0"?>
<gconf>
        <entry name="mount_options" mtime="1228076516" type="list" ltype="string">
                <li type="string">
                        <stringvalue>umask=077,uid=1000,gid=1000</stringvalue>
                </li>
        </entry>
</gconf>
```

Works great.

---

