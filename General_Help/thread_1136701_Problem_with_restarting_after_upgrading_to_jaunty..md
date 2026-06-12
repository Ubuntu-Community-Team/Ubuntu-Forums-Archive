---
title: "Problem with restarting after upgrading to jaunty."
date: 2009-04-25
forum: General Help
---

### Post by mysticalzero on 2009-04-25
Ok. I have successfully upgraded to Jaunty from Intrepid. Everything is running great except for one thing. Restarting my computer from within Ubuntu does not really restarts the PC. Rather, it's more like it only restarts Ubuntu. For example, I would not be brought back to the grub menu after the restart. Also, POST and the BIOS splash screen are even skipped. It just boots straight into Ubuntu. This is really annoying. If say I would like to boot into another OS, I would need to shutdown from within Ubuntu and manually power up the PC again. 

So, in summary, my PC boots directly into Ubuntu on the next restart instead of presenting me with the grub menu. 

Anyone care to enlighten me on this problem? :confused:

Any help will be much appreciated. :)

---

### Post by soro2005 on 2009-04-25
You are aware of the fact that there's the "Log out" dialog and the "Shutdown" dialog? The full restart in the "Shutdown" dialog does not work? You could try out what happens if you open a terminal window, and enter:
```
sudo reboot now
```
This should restart the computer. What you describe sounds like it's only Gnome (the graphical desktop environment) that's going down, not even the system. This would happen if you "log out," as opposed to "restarting."

With regard to the Bios: I find it absolutely difficult to believe that a Jaunty install could possibly have caused a change there. Depending on your system, frenetically hitting the f keys and/or <del> and <esc> while powering up should get you into the BIOS setup. It depends a little on the model, but I think that f1, f2 and <del> are good candidates.

You can edit the delay during which the Grub menu is being shown to you in /boot/grub/menu.lst. You need to be superuser to edit this file. The timeout setting should be toward the beginning of the file.
```
gksu /boot/grub/menu.lst
```
Be *absolutely careful* when you edit this file (and keep a backup). If you screw it up, you won't be able to start any of your operating systems without some additional recovery steps.

---

### Post by mysticalzero on 2009-04-26
Sorry for not being clear. Let me illustrate this using an example:

1) Select "Restart" from the drop down menu located at the right side of gnome-panel.

2) Gnome quits and the Ubuntu usplash is shown.

3) Screen blacks out and after a few seconds, I'm being presented with the Ubuntu usplash followed by the GDM login screen.

What I would expect is after the screen blacks out as in (3), I would be shown the BIOS splash screen followed by the Grub menu. However, this is not the case.

Also, previously I have commented out the timeout line from menu.lst so that the grub menu will be there indefinitely until I select an OS.
By the way, I forgot to mention that I have tried both "sudo shutdown -r now" and "sudo reboot now" but to no avail. 

My menu.lst is as attached.

Note: I have never encountered this problem in 8.10.

---

### Post by ryokea on 2009-04-27
I have this exact same issue and I did a clean install minus whatever settings were on the partition my home directory is stored on. This really wouldn't be much of an issue if I didn't have a dual-boot system and other than the weird static with Pidgin sounds this is the only glitch left in Jaunty for me.

---

### Post by malegria on 2009-05-01
I am having the exact same issue.

---

### Post by o1e9 on 2009-05-16
The same issue with my fresh Jaunty install.  I guess it is something with NVIDIA support of switching between graphics to text or I do not know.

Trying to remove *quiet splash* from [FONT="Courier New"]menu.lst[/FONT], it may help ...

---

