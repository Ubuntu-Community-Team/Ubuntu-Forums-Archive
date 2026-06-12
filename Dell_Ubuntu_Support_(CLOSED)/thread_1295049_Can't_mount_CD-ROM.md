---
title: "Can't mount CD-ROM"
date: 2009-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arnievonderborg on 2009-10-19
Hello fellow Linux users,

I resort to post because I am running out of options:

My CD-ROM used to be present in "places" but it has now moved to "my computer" and cannot be mounted in any way.
I have tried everything from all sorts of mount commands to modifying the /etc/fstab file
without success.
I don't believe it's hard-ware failure but more a change of setting- I have been using Sun virtual box and maybe... any how, help would be greatly appreciated on this one
Cheers

Errors I get after trying to mount the device:*  mount: special device /dev/scd does not exist*

---

### Post by coffeeaddict22 on 2009-10-21
At a guess, the CD is available in the VirtualBox?  If it's mounted in that, it'll be unavailable to your Linux OS.  You need to unmount it in the guest OS.

---

### Post by arnievonderborg on 2009-10-21
Dear coffeeaddict22,

Thanks for your reply. This problem occurred on a Dell optiplex 280 and I just did what I should have done in the first place, which is to check if the actual hardware was faulty! and it was!
As soon as I replaced the CD/DVD ROM, everything worked!

Thanks for your reply

hardware failure signs were : 

[LIST]
[*] would not eject with CD ROM switch
[*]would not eject with software command
[*]still present logically but could not be mounted
[/LIST]

---

