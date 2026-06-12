---
title: "Getting rid of the &quot;gOS&quot; boot screen"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by Elkenfugel on 2007-12-26
i'm trying to get rid of that ugly green boot screen that came on that 200 wal-mart computer.
just got it for christmas and i must say **linux is the best**
i have changed my /boot/grub/menu.lst to load up a custom image that fits grub's boot image requirements but it still loads that stupid gOS thing.
i changed devoption=quiet splash
to devoption=
and it went away, but the second i broght it back, even with GRUB pointing to the custom image, the green gOS screen came up.

any thoughts?

[IMG]http://thinkgos.com/images/header_logo_left.jpg[/IMG]
(stupid logo i hate)

---

### Post by tgilber1 on 2007-12-26
> **Elkenfugel said:**
> i'm trying to get rid of that ugly green boot screen that came on that 200 wal-mart computer.
just got it for christmas and i must say **linux is the best**
i have changed my /boot/grub/menu.lst to load up a custom image that fits grub's boot image requirements but it still loads that stupid gOS thing.
i changed devoption=quiet splash
to devoption=
and it went away, but the second i broght it back, even with GRUB pointing to the custom image, the green gOS screen came up.

any thoughts?

[IMG]http://thinkgos.com/images/header_logo_left.jpg[/IMG]
(stupid logo i hate)

If you haven't already, install startupmanager, which will allow you to manage usplash as well as your GRUB bootup.

sudo apt-get install startupmanager

After installing, you can startup by clicking the following #System#Administration#Startup-Manager

or 

from the terminal

sudo startupmanager

---

