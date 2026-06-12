---
title: "help grub menu"
date: 2008-12-08
forum: General Help
---

### Post by naresh6188 on 2008-12-08
my grub menu has many versions-- how to make it simple with ubuntu latest kernel version and winxp in the list. and hoe to make default as xp

here is my menu.lst


## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=83d51eb6-e4e3-4e71-93f2-5805097d18fd ro vga=769 splash quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=83d51eb6-e4e3-4e71-93f2-5805097d18fd ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=83d51eb6-e4e3-4e71-93f2-5805097d18fd ro vga=769 splash quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=83d51eb6-e4e3-4e71-93f2-5805097d18fd ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


--thanks in advance

---

### Post by PocketDog on 2008-12-08
<snip>

---

### Post by theDaveTheRave on 2008-12-08
Hi all,

If memory serves me correctly...

the first entry is the default... allthough I seem to recall that you can set a default value somewhere and it can grab that stansa for bootup.

If you want to loose the systems you don't want, my advice would be..

Creat a copy of your menu.list

Edit the menu.list

Test to see if it works how you want.

This is from a post I made on another thread, I've tried to remove the stuff that isn't GRUB related.... also I'm sure I've seen other threads on GRUB editing, but can never seem to find them now!


> **theDaveTheRave said:**
> so this is for everyone, but in particular for ibomb... information and instructions for changing the kernel boot parameters.... ie GRUB and stuff;;;;

I found a readme, and this said to look into the info file... so now <info grub> has given me that.

reading this told me that....

so ever onwards I did the folowing....



the above is only  shortened version of the file.... Obviously the line that starts <kernel> is the important one for booting.

There are further stanzas in the file that hold information for booting into other kernels, or for the mem test or the rescue system.

At the top of the file there is the line

default = 0

This is the first line that isn't commented out with the # character. It determines the "default" option for booting into... in my instance this is the first one that occurs after the < ## ## End Default Options ## > (obviously the stanzas are "zero indexed"!)

so I've decided to edit my file

So as not to damage my installs I've made a few changes.....

First there is a timeout before the "default" system is booted... it occurs after the < default = 0 > option. I've changed mine to give myself plenty of time if I've killed my system... also it will easily tell me if the changes have occured.

So I've changed

so as it now reads


so now to the "fun" part, and breaking your system... or hopefully not!

I've copied the first stanza, that reads as the one pasted in above... but it now reads


so hopefully that should solve my booting issues..... so I'm about to reboot and see what happens...

Back soon

Dave

Edit.

so first attempt wasn't a success, I tried the <noapic> option and there was no re-boot!
so I changed to <apic=off>, for a second boot up failure! so on investigation I decided that a "space" was required after the option and before the next line... so I changed to <apic=off > and I was OK to boot... success... or so I thought!

I've tried my normal lots of programs being open on mutliple desktops, and it still goes slow once I get to about 4 or 5 windows? but I don't understand why this should be?

I'm now begining to think it is something to do with the window manager?.... investigations to continue....


Edit 2...

OK so now I'm begining to think it may be a "firefox" problem? as the issue of re-drawing multiple windows only exists in the instances of using the preferences or history windows in Firefox.... so now I have to ask "HOW wierd is that"

what have the guys at mozilla changed?

Appart from the fact that boot times are still amazingly slow... and shutdown doesn't function properly (screen remains powered up like it has only gone to a "hibernate")

Sorry, I know that is a lot to digest, hope it helps...

David

---

