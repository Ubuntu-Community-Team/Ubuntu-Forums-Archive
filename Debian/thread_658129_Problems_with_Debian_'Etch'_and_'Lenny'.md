---
title: "Problems with Debian 'Etch' and 'Lenny'"
date: 2008-01-04
forum: Debian
---

### Post by cprofitt on 2008-01-04
I am trying to install Debian on my desktop which uses a DP965LT motherboard.

When I install 'Etch' I have issues with the sound card - I get no HDA Intel audio... I assume I am missing a driver. I also have a very strange result from using network tools to look at my NIC. It gives me results that it is inactive and that it is using a -754193532 MTU.

When I install 'Lenny' the two issues above go away, but when I try to change the desktop background by right-clicking on the desktop and selecting 'Change Desktop Background' nothing pops up. When I use the Desktop | Preferences | Theme and change the theme I get a delayed loading of the background and then right clicking on the desktop no longer pops up any menu.

So...

After much google searching I had decided to come and ask some questions here in my favorite community.

How does one 'add' a driver (for my sound card) or do I need to upgrade 'alsa' or 'oss'?

What would cause the problem with themes on Debian 'Lenny'?

I have stayed away from using Ubuntu due to wanting to dig deeper and having a boot issue unless I remove 'quite' and 'splash' options from the menu.lst for grub.

I have been told using LILO would prevent that... how do I set Ubuntu up to use LILO at the time of install?

Thanks

---

### Post by danillo on 2008-01-04
Hello.
I'm fairly new to linux in general and debian in particular and am using etch right now. I tested lenny but had the same experience as you with both desktop and sound. To get sound in etch with my nvidia mcp61 I had to upgrade the alsa module. 
I did this: First I downloaded the alsa-source 1.0.15-3_all.deb. Then I used synaptic to install bzip2, debconf-utils, debhelper, module-assistant and gcc-4.1. Then in terminal: dpkg -i alsa-source 1.0.15-3_all.deb. Then: m-a a-i alsa. I then rebooted and ran alsaconf.

Oh, and I had no network connection using the onboard chip, but I "solved" this issue by getting a (cheap) realtek RTL-8139.

---

### Post by kellemes on 2008-01-04
> **PrivateVoid said:**
> (..) when I try to change the desktop background by right-clicking on the desktop and selecting 'Change Desktop Background' nothing pops up. When I use the Desktop | Preferences | Theme and change the theme I get a delayed loading of the background and then right clicking on the desktop no longer pops up any menu.

I have stayed away from using Ubuntu due to wanting to dig deeper and having a boot issue unless I remove 'quite' and 'splash' options from the menu.lst for grub.

I have been told using LILO would prevent that... how do I set Ubuntu up to use LILO at the time of install?

Thanks


Are you having an up to date system?
I had the same issue with Gnome, right-click not working properly.. It went away after some upgrades as I remember.

I wonder what your problem is with Grub, I think it's a much better bootloader then Lilo.
Can you explain your Grub-issue please?

---

### Post by cprofitt on 2008-01-04
My problem with GRUB in Ubuntu (6.10, 7.04, 7.10) is the following:

> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a44483d8-1078-4266-a250-51fe06a5f3af ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


That does not boot -- it just sits at a black screen forever.

> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a44483d8-1078-4266-a250-51fe06a5f3af ro
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


By removing both quiet and splash from the menu entry everything boots up fine.

---

