---
title: "linux-restricted-modules-2.6.22-14-server (I know again),"
date: 2007-11-13
forum: Desktop Environments
---

### Post by eDRoaCH on 2007-11-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/153011](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/153011) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I see this has been here on several topics, but I have an idea for this post that may stop future ones.

yes, I installed the server version of ubuntu 7.10 for the ease in setting up a lamp and mail server on my dev laptop, and now I get the message that I need:

linux-restricted-modules-2.6.22-14-server

which does not exist. I have a Linksys wireless G pcmcia nic model wpc54g and just want to know how to get it working. 

As an aside, i previously had 7.04 installed thru wubi and when i did the apt-get dist upgrade i ended up with NO network cards at all... incl my onboard lan.

If someone can post or link to a post with a howto on getting this card (or wireless in general) to work (I cant for the life of me find the one I originally used)  and maybe vid card drivers (will not help me but will help many others) we may be able to put this issue to bed, at least until the package gets fixed...

Thank you anyone who helps!

---

### Post by kaffe_02 on 2007-12-04
I ran into this problem as well with my laptop.  I upgraded from 7.04 to 7.10.  I tried to access the restricted driver manager to get my nvidia graphics card working and I kept on getting the "need to install linux-restricted-modules-2.6.22-14-server" error.

I rebooted and hit esc to get into the grub boot menu and saw that I was booting to a server kernel. I changed the option to boot to a generic kernel and I now I can access my restricted driver manager.

Hope that helps someone else out.

---

### Post by lns on 2008-02-08
Me too. Weird how there wouldn't be a server kernel package when there seems to be one for every other (generic, i386, etc.)

---

### Post by tcommbee on 2008-02-08
Usually things like accelerated drivers are obviously not required on real servers, which might be the reason maintainers don't bother building restricted modules for them. if you really need accelerated drivers, this may indicate that it's probably not a (dedicated) server what you are planning and you are better of with a desktop installation and setting up LAMP there by hand.

---

### Post by eDRoaCH on 2008-02-08
fair enough. I understand that in the interest of security servers dont get every bell and whistle. 

most of the reason i picked server is that 1 click (or enter in this case) lamp install. Is there a global 'apt-get install lamp' type command to replicate it on a desktop?

---

### Post by lns on 2008-02-08
It's more of the issue of having the "correct" driver installed and functional rather than playing video games on a server.

I'm using 6 HP Proliant ML370 G5 servers (2x dualcore Xeon, 8GB RAM), which require the server kernel for PAE (Physical Address Extension - for systems with >4GB RAM). I am also running Windows 2000 Server in VMWare. When I fullscreen, the screen becomes garbled and doesn't display correctly.

I was assuming the restricted video driver would fix this fullscreen VM issue, especially since when I rebooted (after the kernel upgrade), the Restricted Drivers manager popped up and told me I had to install the package for it to work. (Maybe the RDM should check to see which kernel is running before complaining about packages that don't exist?)

And just FYI, there are no major differences between the server and desktop Ubuntu installs, other than no GUI in the server version, the automated LAMP/etc installations and the server kernel being installed by default. This is coming straight from the #LTSP developers on Freenode. I actually have installed the desktop version because I use these boxes as LTSP servers for computer labs with 35-50 thin-clients connecting to them and that requires a full desktop installation. The only difference is that I'm using the server kernel to take advantage of my 8GB RAM.

For anyone who's interested, I've filed a bug report here:

[https://bugs.launchpad.net/restricted-manager/+bug/190330](https://bugs.launchpad.net/restricted-manager/+bug/190330)


Sincerely,
Jordan


> **tcommbee said:**
> Usually things like accelerated drivers are obviously not required on real servers, which might be the reason maintainers don't bother building restricted modules for them. if you really need accelerated drivers, this may indicate that it's probably not a (dedicated) server what you are planning and you are better of with a desktop installation and setting up LAMP there by hand.

---

### Post by tcommbee on 2008-02-08
i agree, this is definitely a problem in your case, however eDRoach, the original poster, uses a laptop and wireless, which is quite a different setup.

@eDRoach: there's no lamp package, but apache2 and mysql packages combined may be all you need

---

### Post by ftibo on 2008-02-13
> **kaffe_02 said:**
> I ran into this problem as well with my laptop.  I upgraded from 7.04 to 7.10.  I tried to access the restricted driver manager to get my nvidia graphics card working and I kept on getting the "need to install linux-restricted-modules-2.6.22-14-server" error.

I rebooted and hit esc to get into the grub boot menu and saw that I was booting to a server kernel. I changed the option to boot to a generic kernel and I now I can access my restricted driver manager.

Hope that helps someone else out.

When my distro upgraded from feisty to gutsy (7.04 to 7.10), it installed the server kernel which causes me great problems. Now, I can choose to boot on the generic kernel in grub. I would like to know what exactly did you do to change the options in grub so that you always boot on the generic kernel?

Can I even delete the server kernel and only keep on booting on the generic one?

---

### Post by ftibo on 2008-02-13
OK, i've found my way...
deleted the packages linux-image-...-server  in synaptic (the packages linux-headers, etc, were also removed)
so now ubuntu loads straight on the generic kernel.. no more problems with the server kernel.

---

### Post by badspell68 on 2008-03-20
Fix almost all My problems hitting ESC and Booting to Generic Kernel!!!

Thanks so much!

---

