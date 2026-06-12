---
title: "Need some help with these 3 problems"
date: 2006-03-14
forum: Desktop Environments
---

### Post by Mykas0 on 2006-03-14
First, I wanted to remove the image that appears when ubuntu is loading but I can't seem to do it. I removed "usplash" in Synaptic but that screen still seems to appear for the first 3~4 lines, then it disappears and I get the terminal-like screen, which is what I want to use. Any ideas on how to fully remove it?

Second, I am unfortunately running Ubuntu from VMware, and I installed the VM tools in there. It fully installed, but now when running their software I don't seem to get all their tabs, I mean, I don't get the sharing folders one... any ideas on what I may have done wrong?

Finally, any ideas on how to auto-mount an USB drive? I want it to be recognized each time I add a pen or any USB device...

---

### Post by kaamos on 2006-03-14
[QUOTE=Mykas0]First, I wanted to remove the image that appears when ubuntu is loading but I can't seem to do it. I removed "usplash" in Synaptic but that screen still seems to appear for the first 3~4 lines, then it disappears and I get the terminal-like screen, which is what I want to use. Any ideas on how to fully remove it?[/quote]
Applications->Accessories->Terminal.
"sudo gedit /boot/grub/menu.lst" and remove all instances of "splash".
[QUOTE=Mykas0]Finally, any ideas on how to auto-mount an USB drive? I want it to be recognized each time I add a pen or any USB device...[/QUOTE]
It is probably conflict with your host OS. Meaning that the guest (ubuntu) can't automount the drives because the host already has claimed them. Ubuntu does automount them and add to the desktop in a normal install.

---

### Post by Mykas0 on 2006-03-14
What do you mean by "remove all instances of 'splash'"? I seem to have "#nonaltoptions =quiet splash" and "kernel /boot/[more things here] ro quiet splash" as lines in there, should I just remove the "splash" word from there?

About the second one, does anyone know?

As for the third, my main problem is that it only mounts them SOMETIMES... >_<

---

### Post by ardchoille on 2006-03-17
Yes, remove the word "splash". I did this and there is now no splash image when booting - exactly the way I like it.

---

