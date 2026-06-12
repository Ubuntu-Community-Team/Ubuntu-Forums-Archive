---
title: "Dual Boot Fedora 9/Kubuntu"
date: 2008-10-14
forum: Fedora/RedHat and derivatives
---

### Post by G-Dub on 2008-10-14
Hey Guys,

I am happily running Kubuntu 8.04. I absolutely love it. But I am really curious to try Fedora 9. Last time i tried installing it, it overwrote Kubuntu's GRUB. How can I install with out this problem?

---

### Post by djhyland on 2008-10-14
Kubuntu's grub should be restorable.  If Fedora overwrites it again when you install it (and I think it will, since it always has for mine), try this to recover it:

Bring up a terminal as root, and use the grub command.  Once in the grub interface (signified by the "grub>" prompt), type:

```
root (hdX,Y)
setup (hd0) 
quit
``` 

Where (hdX,Y) is the partition you have Kubuntu installed (I assume that you've installed grub itself to the boot sector of your first hard drive, (hd0)). This will point grub to use the grub stages on your Kubuntu partition instead of your Fedora partition.  If you don't know which partion your Kubuntu install is on, you can use the grub command ```
find /boot/grub/stage1
``` to see which partitions have grub stages on them.  

You should now have your Kubuntu grub back.  Still, since you installed Fedora after Kubuntu, Kubuntu's grub stages will likely not have any information for booting Fedora.  To fix this, mount your Fedora partition and open it's /boot/grub/menu.lst file as root.  Copy the entry for whichever kernel you'd like...it should look like this:

```
title 		Fedora 9 (kernel 2.6.26.5-45.fc9.x86_64)
root 		(hd0,6)
kernel 		/boot/vmlinuz-2.6.26.5-45.fc9.x86_64 ro root=UUID=3098ce72-0732-4aef-97db-939251066e38 rhgb quiet
initrd 		/boot/initrd-2.6.26.5-45.fc9.x86_64.im
```

Then, unmount Fedora's partition and open up Kubuntu's /boot/grub/menu.lst file as root, and paste in the entry for Fedora into the bottom of the file.  Save, reboot, and you should see your Kubuntu's grub with an option to boot Fedora.

The problem with the above method is that you'll likely have to repeat it with the new grub entry for every new kernel that Fedora installs, at least if you wish to use them.  Since Kubuntu sticks with just one kernel, I paste the entry for that into Fedora's /boot/grub/menu.lst and use Fedora's grub.  Less work, but again, it uses Fedora's grub.

Good luck!

---

### Post by igknighted on 2008-10-15
Just want to emphasize what was said at the bottom of the previous post: Fedora will update the kernel often (roughly every other week IIRC).  Each time you will need to update GRUB manually if you are only using Kubuntu's grub.  K/Ubuntu might update the kernel once or twice during the life of a release, so if you use just one GRUB, Fedora's is the one you should use.

There is an option to use both.  You can install GRUB to a specific partition instead of the MBR (Master Boot Record), and instead of using the root, kernel, initrd commands to load the system, you would use 'chainloader' instead.  This is basically a handoff from one GRUB to another.

See here for more details: [http://forums.debian.net/viewtopic.php?t=3506](http://forums.debian.net/viewtopic.php?t=3506)

---

### Post by G-Dub on 2008-10-15
Great! Thank you both!

---

