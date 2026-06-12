---
title: "Error installing ubuntu in virtual machine"
date: 2009-09-21
forum: Desktop Environments
---

### Post by fzf22d on 2009-09-21
Hi,

I am new to Linux and I want to become more familiar with it as a possible alternative to Windows.   I am trying to start Ubuntu 9.04 on a virtual machine on Winows XP using Microsoft Virtual PC 2007 but I cannot get it started.  Here's what I have tried...

[LIST=1]
[*]downloaded the Ubuntu desktop edition 9.04.
[*]Created new virtual machine using Virtual PC 2007 & started virtual machine
[LIST=1]
[*]Attached to ISO image to boot to Linux
[/LIST]
[*]Upon start of Linux I select English as my language
[*]At the boot menu I select "Try Ubuntu without any change to your computer" using the safe graphic mode
[*]When I press ENTER I get what looks like a stack trace and at the end it says [end trace 4aa2a86a8e2da22]
[/LIST]
At that point the process just stops.  Ubuntu won't start.  I can't even select CTRL+ALT+DELETE to reboot the VM.  

Has anyone else run into this problem and found a solution?  If so I'd be very interested to know what the workaround is.

Thanks.

---

### Post by clonne4crw on 2009-09-27
Microsoft has made Virtual PC as Linux-unfriendly as they could. You're better off using VirtualBox. I use it and love it.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Lars Noodén on 2009-09-28
Like clonne4crw mentioned, the tool you are using seems designed to make working with other systems as tedious and impractical as possible.  I'm not even sure if it can be done.  Though I would suspect that Linux is probably singled out especially for the treatment, FreeBSD didn't fare much better in the incident I followed last year.  

I'd guess that the main purpose of the Microsoft Virtual PC is to ensure that time budgeted for 'linux' gets not only used unproductively but never gets outside of Windows.  

VirtualBox is quite good.  However, Windows itself is a liability and you'll really feel the weakness using it as a host system.  Virtualization uses a lot of memory, among other things.  

If you have a spare machine; I would **very** highly recommend installing Ubuntu on it and then running any legacy applications under WINE.  Then if any are remaining that don't run under WINE and there is no substitute for, only then try virtualization.

---

