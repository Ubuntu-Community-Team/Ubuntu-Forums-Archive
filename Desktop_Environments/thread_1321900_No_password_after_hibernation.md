---
title: "No password after hibernation?"
date: 2009-11-10
forum: Desktop Environments
---

### Post by Mandarine on 2009-11-10
Hello,

I'm running UNR 9.10 on my eeePC 1000H with an encrypted Home Directory. Everything works fine.

The only thing that bothers me is, that after hibernation there is no password question at all. The PC just boots up and I can work ... for me that is a security issue.

Is there a way to set up a password after hibernation? I don't want to set a password for the screensaver (that's the only thing I found) ...

Any suggestions?

Sascha

---

### Post by Mandarine on 2009-11-12
Hi,

can't anybody help??

Sascha

---

### Post by Perturbed Penguin on 2009-11-17
I'm not sure what to tell you, I don't have much experience in that area. It may help you to know that I'm running UNR 9.10 on a Lenovo S10 and mine brings up the password dialog when it resumes? Hope you can find a solution! ;)

---

### Post by Perturbed Penguin on 2009-11-22
I just stumbled upon some settings in the configuration editor that may be useful for you. Changing these settings on my machine didn't seem to change anything but perhaps you have to update some kind of system file for the changed settings to take effect. Anyways if you open up the Gnome configuration editor (command: 'gconf-editor' if you wish to open it through the alt+f2 method) under apps/gnome-power-manager/lock there are some boolean(true/false) settings that seem like they could be related to your problem.

---

### Post by HeadHunter00 on 2009-11-22
open terminal by pressing ctrl+alt+f2, type in "sudo apt-get install kdm", after it's finished, type in " sudo dpkg-reconfigure gdm" and select kdm. Reboot.

---

### Post by HeadHunter00 on 2009-11-22
This problem is only in gdm.

---

