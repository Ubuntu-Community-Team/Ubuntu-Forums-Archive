---
title: "Corrupted ICO files causing missing Icons in Ubuntu (autorun.inf related on usb)"
date: 2011-01-20
forum: Desktop Environments
---

### Post by sambartle on 2011-01-20
I've just installed Ubuntu for the first time on my laptop (I've used Gentoo for years but not with anything fancy like X)..

Every time I plug a USB device in, it gets auto mounted and appears on the desktop, however the Icon is just a plain text file logo. (not even the standard usb logo it seems)

I believe this is because Ubuntu is trying to read the Autorun.inf file and assign the .ico file that I have created for each drive in Windows (which would be great if it worked)

In windows all these ICO's work fine, and from a Google search it appears the same should be the case in Ubuntu.. however my fresh installed and patched Ubuntu doesn't seem to support reading my ICO files. (Which is why I said corrupted. although in windows they are fine)

If I browse to the device in file manager and try to open the file (which appears a a black preview in the file manager) it opens Eye of Gnome and says: Image Loading Failed.

Can anyone tell me: 

a) should these windows ico files be supported (it seems they should since it try's to load them)

b) why cant they be loaded? Do I need to do something special to make them linux/Ubuntu friendly? (I created them all using IcoFX in windows if that helps)

c) what format ICO files can Ubuntu load?

Thanks,
Sam

---

### Post by sambartle on 2011-01-20
After doing some more research I think this issue may be related: [https://bugs.launchpad.net/ubuntu/+bug/670599](https://bugs.launchpad.net/ubuntu/+bug/670599)

It looks like a possible problem in EOG.. But i wonder does this work for anyone?

If so maybe we could figure out whats up with my ICO's.

---

### Post by sambartle on 2011-01-20
I think this: [https://bugzilla.gnome.org/show_bug.cgi?id=581838](https://bugzilla.gnome.org/show_bug.cgi?id=581838) is the root cause of the issue.

If you have icons with 256x256 'vista' style icons in them they are actually a bit of extra data in PNG format added to the end of the ICO file, gdk-pixbuf cannot cope with that and instead of just reading what it can it fails.

I've not found a way to resolve this yet, but I'm going to look at creating some icons with some older software to see if it doesn't write this Vista specific part of the file.

Otherwise I will try to force Ubuntu not to load the custom icons and just display the standard USB disk icon instead as I don't want to remove the icons as they work on my Windows boxes just fine.

I guess someone can mark this Solved if you like as I think I've figured it out myself. (although it is a bug definitely)
Might be useful for someone in the future.

---

