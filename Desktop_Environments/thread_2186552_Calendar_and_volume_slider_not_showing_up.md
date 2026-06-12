---
title: "Calendar and volume slider not showing up"
date: 2013-11-07
forum: Desktop Environments
---

### Post by Manimecker on 2013-11-07
I can't understand why my volume control and calendar are not showing on my top panel bar, with a fresh install of Ubuntu 13.10 x64, they were working until I installed GNOME 3.8, but somehow they are not working now...

Now the place on which the volume slider should appear, now shows up just like a blank space. And the calendar where you should see the day/month calendar just shows up with a '[calendar]' label.

[You can see the problem on the attachment]

Any idea how to fix this?

I have tried:
-Reset Unity Icons
-Reset compiz fussion settings
-Using GDM instead of lightdm

Also I have the AMD Catalyst drivers installed (not the open source).

I still have GNOME installed... so when I power on my computer, the splash screen shows the GNOME logo. But on the login screen, I see the default Ubuntu login screen.

Sorry for my bad english!

---

### Post by Manimecker on 2013-11-10
Whatever... I fix it!

How...?
Simply... reinstalling ubuntu. It wasn't any other way to work around.

I tried all of this:
Uninstall GNOME
Uninstall all extra software I installed
Restore Unity at full configuration
Uninstall all AMD Radeon private drivers...

With no luck, so I decided to reinstall and it worked (obvious).

But I found a similar problem like mine on the Launchpad bug platform, I attach the link below:
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1071250](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1071250)

And I report a new bug:
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1249481](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1249481)

I hope someone find out what's going on and fix it.

Get this thread closed please!
Thank you, guys! (you couldn't help me on this one, but you have on many others!).

---

