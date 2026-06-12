---
title: "Computer freezes"
date: 2007-11-05
forum: Dell  Ubuntu Support
---

### Post by alexjohnc3 on 2007-11-05
When I use the Ubuntu 7.10 Live CD, it boots up fine, but when I try to connect to a wireless router my computer freezes. However, when I'm booting from the hard drive (which is Ubuntu 7.10 also), I can't even log in before it freezes. Basically, I want to know why it's freezing and how to stop it from doing so.

I'm using a Dell Inspiron 531 with 1 GB of RAM. Tell me what other specs you need to know to help me. Thanks!

---

### Post by alexjohnc3 on 2007-11-06
Sorry, I really need to bump this.

---

### Post by Linicks on 2007-11-06
It could be anything, but looks like wireless.

So to start, turn off wireless in the BIOS, see if the machine boots at least.

Other than that, you will have to debug it somehow.

Nick

---

### Post by alexjohnc3 on 2007-11-06
> **Linicks said:**
> It could be anything, but looks like wireless.

So to start, turn off wireless in the BIOS, see if the machine boots at least.

Other than that, you will have to debug it somehow.

Nick
Well, it only freezes when I try to connect to the wireless network when I'm using the Live CD. When I boot it from the hard drive it usual freezes at the login screen, so I don't think it's a wireless problem.

---

### Post by Triptol on 2007-11-06
Might still be a wireless / NetworkManager problem. NetworkManger starts as a service. I think it is started between the Ubuntu boot logo disappearance and the arrival of the Logon screen.

Turning it off would definitely comfirm this.

Personally I have a freezing keyboard / mouse click problem after a 'certain' time. I think it has to do with ACPI since it only seems to happen when I am not actively using my computer.

---

### Post by alexjohnc3 on 2007-11-06
> **Triptol said:**
> Might still be a wireless / NetworkManager problem. NetworkManger starts as a service. I think it is started between the Ubuntu boot logo disappearance and the arrival of the Logon screen.

Turning it off would definitely comfirm this.
How would I do this exactly? Sorry, I'm really new to Linux and even newer to Ubuntu.

---

### Post by groovete on 2007-11-06
I had a similar problem with my Inspirion 1720. I solved it by unistalling the network-manager and installing wicd instead: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)
Now it works fine.

---

### Post by dacap06 on 2007-11-06
While it could be the network manager, I don't think that's it.  These kinds of freezing problems can happen with nonstandard or incorrectly implemented interrupt hardware.  It causes a timing problem and is surprisingly common.  The faster that interrupts occur (such as when the wireless network is active), the more likely a freeze becomes.  Interrupts  are routed through the Advanced Programmable Interrupt Controllers.  

In some custom hardware, the advanced features aren't implemented correctly in the APICs. The best way to handle hardware variability like that is configure the system not to use the advanced features.  You do that by passing the appropriate kernel parameters to the kernel at boot time.  That task is done by GRUB.  You can change the GRUB configuration by following this procedure:

1.  From the menu entry saying Run Command ...  enter "gksudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.orig" but without the quotes.  This will allow you to recover easily if something goes terribly wrong.

2.  From the menu entry saying "Run Command ...." enter "gksudo gedit /boot/grub/menu.lst but without the quotes.  This should bring the file into a symple editor.  If you like some other editor besides gedit, use it instead.

3.  At the bottom of the file, you will find the menu entries for Ubuntu.  Add the words in bold as shown on the line below in every line that is not a comment and begins with the word "kernel." Once you have done that, save the file and reboot.

kernel    /boot/vmlinuz-2.6.20-16-generic root=UUID=4f146ca4-8f7f-47c4-a72e-e19e101288cd ro **noapic nolapic** quiet splash

Note:  if your computer has a multicore CPU, look closely at its use.  I am unsure whether turning off the LAPIC will disable use of the second core.

---

