---
title: "screen resolution"
date: 2008-03-27
forum: Desktop Effects &amp; Customization
---

### Post by irishdude on 2008-03-27
I recently installed Ubuntu on a computer with a Compag V55 monitor and when I tried to set the correct driver and resolution for that monitor it scrambled the picture. How can I re-adjust the resolution without seeing the on-screen menu????

---

### Post by Living2007 on 2008-03-27
What is your GPU (graphics Driver)

---

### Post by irishdude on 2008-03-28
ATI Rage Pro Turbo 2X AGP with 4MB SGRAM

---

### Post by Living2007 on 2008-03-28
Have you looked at "Screens and Graphics" in the Admin Menu?

Because from there, you can choose you monitor, Resoution, and Graphics Card Type.

This should help

---

### Post by gwoodruff on 2008-03-28
Reboot the pc and when grub is loading hit esc. 
Choose the restore option.
 This will bring you to a command prompt for login. 
Enter your name and password as prompted. 

Type ```
dpkg-reconfigure xserver-xorg
```Follow the prompts. 
It should redetect and get you back to a desktop where you can reconfigure if needed.

---

### Post by irishdude on 2008-03-29
Thanks for the help...was able to reboot and start over.

---

