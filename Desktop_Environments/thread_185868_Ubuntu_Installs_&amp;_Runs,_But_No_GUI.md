---
title: "Ubuntu Installs &amp; Runs, But No GUI???"
date: 2006-06-01
forum: Desktop Environments
---

### Post by mbmccormick on 2006-06-01
I can get Ubuntu to install and boot, but it won't start the GUI. It locks up. I see the startup screen, and it runs through boot procedures and network, etc. But it finishes and won't load the login screen or any graphical user interface at all. What should I do? Is this hardware or software? I am running a NVidia eVGA graphics card. If I were to install drivers how would I do this without a command line?

---

### Post by PriceChild on 2006-06-01
Does it properly crash to xserver and say there's a fault?

At the end can you "Ctrl+alt+F1" to command line?

---

### Post by Altrego on 2006-12-29
this is the same problem I'm having. I have 6.06 with ubuntu-desktop installed. I get the splash screen where everything loads, it finishes, and locks up. I get a blank screen with a cursor at the top that freezes. 

Any ideas? At the point it freezes, you can't input anything in the keyboard that works. I assume the login screen should follow.

---

### Post by b0le on 2006-12-29
Do you get any sound (when the login screen should be) - I had the same problem (but I had sound), which I fixed by booting in recovery mode, running "sudo dpkg-reconfigure xserver-xorg" and changing the  display driver to VGA (8 bit colour depth) - for some reason ATi and VESA drivers didn't work (I have an x800) - then downloaded fglrx (ATi proprietry drivers) in order to get proper colour depth and resolution (resolution was stuck at 320x200)

---

### Post by Altrego on 2006-12-29
no sound. But I will give it a try..

---

### Post by Altrego on 2006-12-29
ok.. so the problem seems to be related to the ATI board that is integrated on the motherboard. I haven't used it in so long that I didn't even think about it.

Ubuntu can see my NVidia card (when I lspci) but when I reconfigure, it says that I am entering an invalid busid (PCI:02:0b:0). 

For now I have the onboard card working. Any howto's on switching video cards? I'd much rather use the PCI card.

---

