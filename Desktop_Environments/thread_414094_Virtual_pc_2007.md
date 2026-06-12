---
title: "Virtual pc 2007"
date: 2007-04-19
forum: Desktop Environments
---

### Post by kismeras on 2007-04-19
Can the new version 7.04 be installed on MS virtual pc 2007?

---

### Post by openix on 2007-04-22
Ditch that rubbish and use [VMWare]("http://www.vmware.com/products/free_virtualization.html") - Feisty should work fine with this.

---

### Post by dshale on 2007-04-23
I was able to get 6.06 and 6.10 to work by the alt cd iso. 7.04 has installed but, I am having issuse with the mouse.  Here are the steps if you want to try:
during boot hit [esc] to enter the grub menu and choose recovery mode.
go to the /etc/X11 directory
edit the xorg.conf file
find the line that reads defaultdepth 24
change 24 to 16
save
reboot

I hope this helps as far as install goes.

---

### Post by Loki-uk on 2007-04-23
Yes 7.04 can be installed but the mouse issue is a bit hit and miss on some PC the mouse doesn't respond. This seems to be a kernel issue and nothing to do with VPC. VMWare as well as legacy users are reporting this too.....

:(

Loki

---

### Post by indianabeck on 2007-04-23
I'm having the same problem. Looks like lots of people are having mouse problems.

---

### Post by Daveski on 2007-04-24
I have the same problem with the mouse. My virtual Edgy install worked OK, but I upgraded to Feisty via the Update Manager and now the mouse does not work.

The Virtual PC software does not appear to 'capture' the mouse pointer when you click on the virtual machine. Normally the windows pointer disappears and the virtual machine pointer starts to move (but is trapped inside the virtual machine). You must release the pointer by pressing a magic key. It seems it is the capture process that is not working which suggests to me that the Virtual PC software does not think that the hosted machine has mouse support.

---

### Post by indianabeck on 2007-04-24
Yes, it's the Right Alt key. Your assessment seems correct to me. The Ubuntu Kernal does not map the mouse driver in such a way that VPC understands it. Although other people running off of the CD or on non-Virtual machines have mouse problmes. If you look at the number of mouse issues that have been posted since the most recent upgrade, there are definately some Ubuntu issues.

I fell back to 6.10, it works fine in the same Virtual Machine.

---

### Post by Daveski on 2007-04-24
> **indianabeck said:**
> Although other people running off of the CD or on non-Virtual machines have mouse problmes. If you look at the number of mouse issues that have been posted since the most recent upgrade, there are definately some Ubuntu issues.

Seems to be a bug in the 2.6.19 kernel and later - other distros are reporting the same sort of mouse problems.

---

### Post by Loki-uk on 2007-04-25
Yes it is a kernel issue I have been helping with bug reports and the kernel team need more info. They are currently looking into it. THIS IS NOT A VIRTUAL PC ISSUE

Loki

---

### Post by ArcaneCode on 2007-04-25
In one of the many other threads, I saw where someone suggested turning on accessibility features to let your numeric keypad act as a mouse. I tried this under VPC 2007 and while it's not the greatest experience in the world it does work. I blogged the steps at [http://shrinkster.com/ocx](http://shrinkster.com/ocx). 

By the way, if someone notices the original post with the suggestion please let me know, I'd like to make sure to give the original poster credit. 

   Arcane

---

### Post by mwexler on 2007-06-03
The trick appears to be using a kernel parameter.  From [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87262](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87262) which points to [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=223606](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=223606), they say to include the kernel parameter i8042.noloop on the boot. This can be done manually each time on the liveCD (Press “f6” for additional options at the boot screen, and hand type it in on that text line) or if you install it, you can manually add this to the boot config file. On my tests with VirtualPC, this allowed the mouse to work as expected!

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) tells how to edit the boot config file.

Hope this helps, and hope that a newer version of Ubuntu fixes this bug.

---

