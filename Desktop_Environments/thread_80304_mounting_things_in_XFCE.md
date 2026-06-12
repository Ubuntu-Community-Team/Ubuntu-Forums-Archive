---
title: "mounting things in XFCE"
date: 2005-10-21
forum: Desktop Environments
---

### Post by chickengirl on 2005-10-21
I played around with XFCE in Mandriva before my poor computer *sniff* died *sniff* and I really liked it so I installed xubuntu-desktop on this computer I'm playing with that's running Breezy.

If someone can help me solve this problem, I will love you and XFCE forever and ever and ever.

I've got a flash drive. It's a Memorex, 256MB, and it has a write-protect / unprotect slider on it (felt I should mention that in case it's throwing a wrench into the works).

It automounts perfectly in gnome. It does not automount in XFCE (does anything automount in XFCE?). The fstab mount manager that xubuntu comes with doesn't see it. (It does see, and can mount, but does not automount, my CD-ROM. Just for comparison.)

If I try to mount it myself, I can only get it read-only. I can't seem to get it mounted so that I have write permission as a user. I can do it with root/sudo, but I don't *want* to have to do it that way. (edit to clarify: I can write to it as root/sudo, but as a user I can only read.)

I have tried to mount it like this:

**sudo mount /dev/sda1 /home/cassie/flashdrive**

and like this:

**sudo mount -t vfat /dev/sda1 /home/cassie/flashdrive**

Both give me the same result: I can read but not write.

So, does someone know what I'm *supposed* to be doing, or what I should do instead?

---

### Post by chickengirl on 2005-10-21
Yikes, this forum moves fast. Bump.

---

### Post by recce101 on 2005-10-22
***It does not automount in XFCE (does anything automount in XFCE?). The fstab mount manager that xubuntu comes with doesn't see it.***

Does your /etc/fstab file show "rw,user" (delete "noauto" if it's there) as options for the devices you're trying to automount? I'm using XFCE with Ubuntu 5.04 (haven't managed to get 5.10 installed yet) and my FAT32 Windows partitions will automount just fine as long as /etc/fstab is set up for it. I edit the fstab file directly and don't use a mount manager. The only device I would like to automount but can't is my usb external drive. It seems the fstab file is being called before the usb drive is fully configured in the startup routine, so it won't automount , but I can manually mount it read-write as soon as the system is up and running. I could probably fix that if I knew a bit more about the startup process.

Sorry, I can't help you with the flash drive or write-protect slider question.

---

### Post by ranf on 2005-10-22
[QUOTE=chickengirl]
It automounts perfectly in gnome. It does not automount in XFCE (does anything automount in XFCE?). The fstab mount manager that xubuntu comes with doesn't see it.[/QUOTE]
As I can see in aptitude xubuntu-desktop uses `ivman' for automounting. Here is its description:
```
daemon to auto-mount and manage media devices
ivman is a daemon that acts as a policy agent on top of HAL. It
listens to HAL events and reacts with user-configurable
actions. Currently it supports automount of new media and hot-plugged
devices, autorun, autoplay for CDs and DVDs, and automatic camera
management.
```
No mention of USB sticks. Not ready yet most likely.

But AFAIK you can still run the Gnome thingie (from a terminal):
```
gnome-volume-manager &
```

---

### Post by sameat on 2005-10-23
gnome-volume-manager &

will work (I know from experience).

Alternatively, when I mounted my usb drives manually, I used:

sudo mount /dev/sdc1 /mnt/xxx -t vfat -o umask=000

---

### Post by linuxnomad on 2005-10-24
I have been reading up on ivman at its site and it is suppost to mount usb sticks :
"What is Ivman?

Ivman is an extremely flexible desktop independent frontend to HAL ([http://freedesktop.org/wiki/Software_2fhal)](http://freedesktop.org/wiki/Software_2fhal)), the userspace Hardware Abstraction Layer for Linux ([http://en.wikipedia.org/wiki/Linux)](http://en.wikipedia.org/wiki/Linux)). It can be used to execute arbitrary commands when devices are added to or removed from your system, when device properties change, or when devices emit conditions. Any properties of the new or changed device can be included within the executed command.
So what can I do with it?

    * insert CDs, DVDs, **_USB sticks_** and have them automatically mounted with permissions only for you if you are logged on, or for everyone if you are not
    * start CD player or ripper or anything else you like when an audio CD is inserted
    * start Xine or MPlayer or anything else you like when a video DVD is inserted
    * run commands when a specific CD or DVD is inserted (e.g. immediately eject a Windows XP CD :-)
    * run commands when your network interfaces are activated or deactivated
    * have nice little popups appear on your desktop when new hardware is attached
    * hibernate your laptop when the lid is closed
    * bind commands to all the ACPI buttons on your machine (including many Fn keys on laptops)
    * automatically run a script to, e.g., connect to a VPN when you insert a wireless card within the range of a particular network, and then disconnect when you remove the card
    * pretty much anything else you can think of, as long as your hardware is supported by HAL. "

I just installed Xubuntu after a server install. My usb sticks don't auto mount and I am having trouble, like so many other people, getting write permissions set up. I am going to have to check and see if ivman is included with the Xubuntu package and how to get itfunctional. 
I have only been using Xubuntu for about 3 days and I like it expect for the removable media issues. I'm really like the easy with which everything and be configured.
Oh here's a link to the ivman site if you want more info about it:
[http://ivman.sourceforge.net/](http://ivman.sourceforge.net/)

Matthew

---

### Post by oliwer on 2005-10-24
There is also **xfce4-mount-plugin**, a plugin for the panel which allow you to mount any media (internal or external) very easily. It worked fine on hoary but I didn't manage to compile it on breezy (I think the package xfce4panel-dev is corrupted).

---

### Post by linuxnomad on 2005-10-25
I have been playing around with the automounting and non-automounting methods to try and get usb sticks to mount in XFCE and I have had no lucky so far. ivman,pmount, and hal are installed with Xubuntu, but doesn't seem to work properly, also tried a package called usbmount with out any success. I would have to guess there is a problem with Xubuntu and usb, but its just a guess.

I didn't relize XFCE had a mounting plugin. I guess I will give that a try next. If someone figures this out please let us know. This is driving me nuts. I have never had this much trouble configuring fstab or running automounting software.



Matthew

---

### Post by oliwer on 2005-10-25
linuxnomad> you mean that when you put your usb, it doesn' appear in /media/ ? ivman does it pretty well.

---

### Post by linuxnomad on 2005-10-25
oliwer, my usb stick doesn't mount with I plug it into my computer. I have only been able to get it to mount by editing fstab. Even then I have to mount it as root and I don't have write permissions. 

Matthew

---

### Post by ozorba on 2006-03-23
[QUOTE=oliwer]There is also **xfce4-mount-plugin**, a plugin for the panel which allow you to mount any media (internal or external) very easily. It worked fine on hoary but I didn't manage to compile it on breezy (I think the package xfce4panel-dev is corrupted).[/QUOTE]

Has anyone managed to locate xfce4-mount-plugin in the repositories?

I have everything working in xfce4 except auto plug-ins such as USB memory stick etc.

Thanks,
OZ

--

---

### Post by aysiu on 2006-03-23
Somewhere mentioned earlier in the thread *gnome-volume-manager*--I've found that to be far more reliable than *ivman*.

---

### Post by red devil on 2006-03-24
I've just come back to Ubuntu after using Zenwalk 2.2 and had to manually set up mounting for removable usb stick in Xfce.
All you need is an entry for usbstick in your Fstab, another entry in mount (I think, in Ubuntu, you'd need to put it in 'dev' - I'm at work now so can't check my machine to verify this).
Xfce does have a panel plugin for mounting/unmounting devices - right click on the panel, select 'Add new item' and you should get the option to scroll down and select the removable drives plugin.
Once that's in your panel, click once on it and then click once again on the name of the drive you want to mount - you can configure the plugin so that it mounts the device AND opens your file browser so you can browse the contents.
To unmount the drive, just click it once again - and that's it.
HTH:)

---

### Post by barnz on 2006-04-29
I have found [this website ]("http://gauvain.tuxfamily.org/repos/")for the mount plugin, but having followed the instructions, I can't seem to get it to install. 

apt-get responds with this:

> Package xfce4-mount-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://gauvain.tuxfamily.org](http://gauvain.tuxfamily.org) breezy/backports Packages (/var/lib/apt/lists/gauvain.tuxfamily.org_repos_dists_breezy_backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gauvain.tuxfamily.org](http://gauvain.tuxfamily.org) breezy/contrib Packages (/var/lib/apt/lists/gauvain.tuxfamily.org_repos_dists_breezy_contrib_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package xfce4-mount-plugin has no installation candidate

I get an xfce4-mount-plugin then in synaptic, but it's "broken", and I have no plugin to add.

I tried using the source edition, but got the same errors that others have reported here.

This mount thing is the only main issue I have with xubuntu.

---

### Post by barnz on 2006-04-29
Hello all,

Just an update - I successfully installed xfce4-mount-plugin.

With thanks to Gauvain, the maintainer of that repository, I downloaded the .deb file from [http://gauvain.tuxfamily.org/repos/dists/breezy/contrib/binary-i386/xfce4-mount-plugin_0.3.3-0ubuntu1_i386.deb](http://gauvain.tuxfamily.org/repos/dists/breezy/contrib/binary-i386/xfce4-mount-plugin_0.3.3-0ubuntu1_i386.deb)
and installed with dpkg (sudo dpkg -i xfce4-mount-plugin_0.3.3-0ubuntu1_i386.deb)

It's very handy. 

Good luck

---

### Post by missmoondog on 2006-04-30
well, that's a step in the right direction anyway. i quit using xfce almost immediately when i saw how "goofy" mounting things was. didn't seem to be any faster on this old, tired 600mhz cpu either, which was my main reason for trying it.

---

### Post by carney1979 on 2006-05-14
Uisng ivman to automount USB sticks works well, but how do you unmount them??

David

---

### Post by larry on 2006-06-16
I am experiencing a different problem (Xubuntu 6.06, I am a newbie).
Xubuntu casts an sda1 icon on the desktop when I plug in my memory stick, then I can mount it easily, but somehow only as a read-only thing!
A sysadmin I have heard of was able to fix it by chmod 777 plus something else I do not know!
He did not reformat anything and he fixed the permission problems.
Unfortunately, every time I try to fix things with sudo chmod 777, Xubuntu complains as the filesystem is read-only.
Any suggestion is really appreciated.
Cheers

Larry

---

### Post by Stabat on 2006-06-16
I'm not new to the [Ll]unix shell but I am new to using it as I would the Windows box; I've escaped and now see the world through my own eyes (not without difficulties).

I've encountered a similar hurdle with mounting a Pocketec usb drive.  
Thanks to this forum I was able to mount it but only read only. The command I used was (as root)

(Added this at the end of /etc/fstab):
/dev/sdb1      /media/usb      auto    rw,user         0       2
(Your /dev/* and /media/* may differ)

Mounted it:
mount /dev/sdb1 /mnt/usb -t ntfs -o umask=000 
(also tried umask=777, umask=111, umask=0000)

Verified it:
/dev/sdb1              38G   37G  907M  98% /mnt/usb
:KS 

I can view it but it's still read-only. :(

---

### Post by kokas on 2006-06-18
Hi there. I just switched from Ubuntu to Xubuntu and in Ubuntu all my partitions appeared ok but now in Xubuntu they don't show in the desktop neither in the file manager. And when I looked at my fstab it has a error message....Any one can help me to see my Fat32 ?

Here's my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by larry on 2006-06-18
[QUOTE=kokas]Hi there. I just switched from Ubuntu to Xubuntu and in Ubuntu all my partitions appeared ok but now in Xubuntu they don't show in the desktop neither in the file manager. And when I looked at my fstab it has a error message....Any one can help me to see my Fat32 ?

Here's my fstab
[/QUOTE]

This sounds a bit off-topic.
However, it looks like many users are experiencing problems with the USB memory sticks on Xubuntu.
I also have toyed with the Fstab file and the rw permissions, but I only mount my memory stick as a read-only device.
I wonder if this is a bug in Xubuntu...installing Gnome volume manager did not help me.

Larry

---

### Post by fortran01 on 2006-10-30
My problem is the opposite. I want to disable all automounting of external media entirely. Is this possible? Thank you.

---

### Post by Auric_Falc0n on 2006-10-31
Just as a quick question - I didn't see this mentioned above - what file system is the jump-drive?

---

