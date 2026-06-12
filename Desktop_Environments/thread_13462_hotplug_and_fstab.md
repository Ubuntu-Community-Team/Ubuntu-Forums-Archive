---
title: "hotplug and fstab"
date: 2005-01-31
forum: Desktop Environments
---

### Post by tripslip38 on 2005-01-31
When I first installed Ubuntu Warty, things like my Ipod would mount automatically when I plugged them in, after I added the appropriate line to my /etc/fstab. A nice icon would appear on the desktop and the nautilus window would pop up for the hotplugged drive (firewire Ipod.) Now, nothing. I have to sudo mount -a to get it to mount. It works but I am confused as to why the automounting doesnt work anymore. Now I have a USB external HD and I am revisiting this issue. 

Here is my fstab line:

/dev/sda1       /mnt/hotdrive   auto    auto,ro,uid=zane,gid=zane,sync  0      0

Before it seemed my fstab didnt have to be so granular as to the user permissions. It was quite general, and filesystems would mount upon hotplug with all permissions for whatever user was logged in to Gnome.  Any ideas?

Thanks.

---

### Post by tripslip38 on 2005-02-06
So I answered my own question.

Line in /etc/fstab must look like this:

/dev/sda2       /mnt/ipod       vfat    auto,rw,users,sync


The "users" option allows all users to mount the volume, which I think allows the option "Mount removeable hard drives when hotplugged" work.  Before, I had it locked down to my uid and gid, which then would only mount when I ran mount -a as  superuser. 

Z

---

### Post by r00 on 2005-02-28
.. i had something like that going on in another distro before i moved over to ubuntu.. but there was always this one problem, which seems to apply to ubuntu as well.. the two devices (ipod, external usb drive) will switch /dev 's   between /dev/sdc and /dev/sdd  .. sometimes..the ipod doesn't even show up at all and doesn't even try to get mounted.. hehe

if you have an idea as to how to fix this and automount them, it'd be greatly appreciated :P

btw.. chmod that mofo from root.. so anyone can use it :)  haha it worked for me in the other distro...

---

### Post by MattiasJow on 2005-10-23
I got the same problem here, my extern harddrive messes up with the automount on ipod, the harddrive automounts great.

---

### Post by dlai on 2005-11-28
hey maybe this how to will help! 

[http://ubuntuforums.org/showthread.php?t=91948](http://ubuntuforums.org/showthread.php?t=91948)

---

### Post by dudus on 2005-12-14
I don't know why but I don't even have this line in my fstab. But when I plug the ipod it pops up and the line is auto added into mtab (witch I presume lists the mounted devices). 
But sometimes if I connect and disconnect the ipod fast, it stops popping up, adn won't mount until I reboot the system.

I wanted to add this to fstab so I could manualy mount if it happens

---

