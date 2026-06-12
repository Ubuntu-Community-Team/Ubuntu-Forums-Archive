---
title: "Hotplug &amp; fstab..."
date: 2005-08-06
forum: Desktop Environments
---

### Post by mozz on 2005-08-06
Hi,

this is kinda hard to explain, but I hope I can do it...

I have 2 devices: an **external HD** and my **camera**

If I start the HD and AFTERWARDS the camera, the *hd* is recognized as *sde* and the *cam* as *sdf*...
If I run _only_ the camera gets listed as sde.

In both cases hotplug works  and I'm having no problems at all, so far...

Now I have to make an entry in fstab so I can unmount /dev/sde (the hd) without root permissions (because of some shell script...):
> /dev/sde1	/media/exthd_ext2	ext2	noauto,users	0	0

Now if I start the harddisk it works as it should (on sde) and if I start the camera afterwards it gets automatically mounted as sdf-

but (and thats what yall've been waiting for...): If I just run the camera without the harddisk, it doesnt get mounted at all!
In /var/log/messages it reads something like: "camera found on **sde**" but nothing happens...same thing with any other USB storage (USB stick...)

If I kick the sde entry out of the fstab it works again...

So, how can I keep the entry for the external hd and get other devices to work with hotplug?
My idea would be, reserve sde for the external hd and force all other medias to mount in sdf,...but I dunno how to do that.

Hope someone reads this and knows how to help - thx a thousand times

---

### Post by mozz on 2005-08-06
And another question: why does the system start at sde? The only other USB device I have is my mouse...

in /dev/ there are sda-d listed but I can't mount them ("No media found")...very strange

---

### Post by varunus on 2005-08-06
The fact that you can't unmount the HD without root permissions is a little strange...right clicking its icon and choosing "Unmount" in GNOME doesn't work?  Weird...Is this the user you created during the Ubuntu install?

I think the problem with your fstab line is that you have the filesystem set to ext2, and that is probably not the one of the camera.  Try changing the "ext2" below to "auto" in your fstab; then, both the camera and HD will get mounted at that mountpoint depending on which one gets plugged in first.

I still don't see why you can't unmount it though if you just plug it in...What error do you get if you try?

---

### Post by mozz on 2005-08-06
> I still don't see why you can't unmount it though if you just plug it in...What error do you get if you try? 

If I want to completly unmout it without the fstab entry "umount /dev/sde1" says:

umount: /dev/sde1 is not listed in fstab (only root can umount it) [translated from german]

Edit: I can unmount everything from the GNOME menu but not from the terminal, I need a root-terminal for that to work

> [...] depending on which one gets plugged in first 

Thats my problem :) Only the hd should be sde (because the script I mentionend above tries to unmount the hd under sde) and every other device should get the chars f-z..

---

### Post by cwaldbieser on 2005-08-06
[QUOTE=mozz]
umount: /dev/sde1 is not listed in fstab (only root can umount it) [translated from german]

Edit: I can unmount everything from the GNOME menu but not from the terminal, I need a root-terminal for that to work
[/QUOTE]

I think you can use "pmount" & "pumount" without having to have the /etc/fstab entry.

---

### Post by mozz on 2005-08-06
Oh wonderful, that pmount thing works :)

But then I'm still having the problem that the external hd isn't bound to sde, and so I would've to rewrite the script and change the /dev/ path everytime I exectue it :(

Thanks so far

---

### Post by varunus on 2005-08-06
The HD should get the same mount point each time, right?  Its always in /media/something, right?

Can't you make your script execute "pumount /media/mountpoint" instead of the device name?

---

### Post by mozz on 2005-08-06
Yeah but that wouldn't completely unmount it, just one mountpoint...so any other mountpoints would stay active and I would've to change the path everytime I change the mountpoint :)

I'm not easy to satisfy, I know ;)

---

### Post by sneax on 2007-08-22
Hey I have kinda of the same problem! Here is what happened: Everything used to be fine! When I pluggin in my usb hard disk it would load as /media/Iomega and show icon on desktop. When I plugin my usb stick it would loadn as /media/K750i (it's part of my phone) and show icon on desktop called 'K750i'. Perfect!

However, I installed ntfs-3g and ntfs-config, I think the latter overwrite my /etc/fstab and now none of these devices automount anymore! I can mount them as superuser but the command takes a long time and it makes nautilus crash :(

All I know is that ntfs-config changed my /etc/fstab, and I would like it back the way it used to be. Only thing I would have to edit is that my usb harddisk shouldn't load with 'auto' as filesystem but with 'ntfs-3g' and that's it.

**But how do I get back my original fstab that I had when I installed Ubuntu?**

---

