---
title: "taking the &quot;dual&quot; out of dual boot"
date: 2009-01-15
forum: General Help
---

### Post by coolethan on 2009-01-15
i tried out kubuntu and i thought i liked it pretty good from the live cd so i installed it but now i don't really want it that much any more. how do i uninstall kubuntu from my system?

---

### Post by BlackLLama on 2009-01-15
install something else over it

---

### Post by Shazaam on 2009-01-15
You could do as previously posted OR install ubuntu-desktop through Synaptic. That should pull in the Gnome desktop environment (Ubuntu). After install and a reboot, when you get to the login screen go to Sessions (lower left) and choose Gnome.

---

### Post by coolethan on 2009-01-15
is there some way of using a partition editor to do this? I already have Ubuntu on my system and Kubuntu is only using 25% of my hard drive. installing over top of it would not really solve much except i have to re-setup all the crap and install the updates all over again

---

### Post by blazemore on 2009-01-15
So wait, you had Ubuntu.
Then you installed a TOTALLY SEPERATE Kubuntu?
You'll have to boot to Ubuntu, format the Kubuntu drive, run update-grub, and somehow use the leftover space (Is there a way to merge ext3 partitions)

---

### Post by coolethan on 2009-01-15
> **blazemore said:**
> So wait, you had Ubuntu.
Then you installed a TOTALLY SEPERATE Kubuntu?
You'll have to boot to Ubuntu, format the Kubuntu drive, run update-grub, and somehow use the leftover space (Is there a way to merge ext3 partitions)

isn't that the definition of "dual boot"? ya i have ubuntu and then i just wanted to see what kubuntu was all about and realized once i had it it's confusing as hell and kinda pointless as i already had a perfectly setup ubuntu. how do i go about formatting the Kubuntu drive.

---

### Post by blazemore on 2009-01-15
```
sudo apt-get install gparted -y && sudo gparted
```
That will install and run gparted.

Make sure the correct drive is selected from the drop down list on the top right.

Select the partition in question, and delete/format it using right-click.

Click Apply.

I accept no responsibility for any consequences of you choosing the wrong drive or partition.

---

### Post by blazemore on 2009-01-15
Now, if someone else could let us know if ext3 will easily expand into the space, EVEN IF IT IS NOT "NEXT TO" IT, that would be very useful, since I've been wanting to know that.

---

### Post by coolethan on 2009-01-15
ok well i'm trying to determin which of the partitions are the ones containing the Kubuntu. there are 3 little ones all in red which i think are the ones that are for kubuntu. also when i start my computer the default OS changed from Ubuntu to Kubuntu, why would it do that, Ubuntu is using 75% of the hard drive and it was the first one there. i'm thinking of making a usb startup disc, does that just take your system and make an iso of it so you can install it exactly the way you had it before with the updates and stuff?

---

### Post by blazemore on 2009-01-16
The way to check is to look at the mount points.
The mount points are where in the file-tree the disk is located.

The installation you are currently in (ie Ubuntu) will be mounted as / , so keep that one.
You also want to keep the Swap file (probably the smallest).

It's fine to delete the other one, but you must click Apply, and then run sudo update-grub after!

---

### Post by kesre on 2009-01-16
> **blazemore said:**
> Now, if someone else could let us know if ext3 will easily expand into the space, EVEN IF IT IS NOT "NEXT TO" IT, that would be very useful, since I've been wanting to know that.

From when I've done it (shrinking partitions then adding it to another one next to it), I had to increase the partition in between by the desired amount at the one side, then shrink it the same amount on the other, then add the free space to the intended partition

There may be another, better way to do it, and you might not need to do that for ext3, but it does work...

what gparted will do is shift all the data - which can take a LOT of time depending on partition size and use.

---

### Post by ajcham on 2009-01-16
> **coolethan said:**
> isn't that the definition of "dual boot"? ya i have ubuntu and then i just wanted to see what kubuntu was all about and realized once i had it it's confusing as hell and kinda pointless as i already had a perfectly setup ubuntu. how do i go about formatting the Kubuntu drive.

The reason for Blazemore's incredulity was that it really wasn't necessary to install Kubuntu separately.  Ubuntu and Kubuntu are the same system underneath, just with different Desktop Environments (and associated apps).  You could have tried out Kubuntu on your existing Ubuntu installation by simpy installing the kubuntu-desktop package.  You would then have been able to select KDE, rather than GNOME, at login time.

---

### Post by kesre on 2009-01-16
Yes, thats true.

But less RAM is used if you don't have to put KDE on top of GNOME and vice versa.
Plus the original configuration of each is a bit different - menus, place names,etc.

---

### Post by blazemore on 2009-01-16
I disagree, the RAM is the same, IF you don't have all your Gnome services running at startup.
It certainly takes up less hard-disk space, time and hassle than installing a whole new system!
You also could try it in a virtual machine if you just wanted to mess around with KDE4 (Since you can't actually USE it for anything... flame war anyone?)

---

### Post by coolethan on 2009-01-17
frick man i didn't do the update grub thing so then when i rebooted my system i got system error 22 or whatever. i suppose i could have used the live cd and the terminal on that to type the command but at that point i haden't checked back here so i didn't know of that code. anyways ya i reinstalled. i stored all the things i wanted to keep on my second hard drive so that i wouldn't lose anything.

---

