---
title: "ctrl-alt-f2 gives blank screen"
date: 2008-09-14
forum: Desktop Environments
---

### Post by r.stiltskin on 2008-09-14
(Ubuntu Hardy)

I can't get a tty terminal prompt outside of x windows -- ctrl-alt-f2 just gives me a blank screen.

lsmod tells me that the fbcon module is installed.  I'm guessing that maybe fbcon is incompatible with my (nvidia geforce 6200 video card (although the Ubuntu splash comes up correctly).  I tried disabling the splash by modifying /boot/grub/menu.lst, but still got no terminal prompt.  Any ideas as to what else might solve this?

---

### Post by ChongZx14o on 2008-09-14
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by mali2297 on 2008-09-14
Have you seen [this thread](http://ubuntuforums.org/showthread.php?t=585454)?

---

### Post by r.stiltskin on 2008-09-14
No, my search didn't find that thread.  Thanks.  That gives me a few ideas that might work.  I'll play around with it some more next time I'm at that machine - in a couple of days.

---

### Post by r.stiltskin on 2008-09-18
What a mess.  I tried to add a post to that thread, but it is closed.  Too bad.

What a mess.

I have 2 machines running Hardy, both using GeForce6200 video cards.  One has a Samsung LED display -- on that one the splash and TTYs work fine with default configuration (fbcon is loaded, and no other framebuffer driver is loaded).

The other one has an old Viewsonic CRT monitor.  On this one the default configuration gave me the splash, quiet bootup but inoperable ttys.  I tried various "fixes" suggested in the thread you mentioned with varying degrees of success -- none fully successful, i.e. I can have ttys or splash but never both.

I have deleted the "quiet" parameter from the grub boot command, to see the bootup messages.

I can get the ttys with either vesafb or vga16fb if I specify an appropriate vga=... parameter in the grub boot command, but doing this disables the splash and most of the bootup messages (when the splash parameter is included).

I noticed something very strange: if I DO specify an allowable vga=... parameter in the grub boot command and do NOT put the splash parameter on that command line, vesafb is loaded even though it is blacklisted  (I DEFINITELY ran update-initramfs -u -k all after blacklisting it).  This is clearly a bug, but in this case, it boots with no splash, full bootup messages, and functional ttys.  So I guess it's a good bug. :)

In other words, it seems unnecessary to do any editing of the default /etc/modprobe.d/blacklist-framebuffer file or the /etc/initramfs-tools/modules file; just edit the /boot/grub/menu.lst deleting the "splash" and adding "vga=[...]" (where [...] is one of the values from the table posted by the OP of [http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)).  This seems to enable normal tty functionality (but of course eliminates the splash screen).

---

