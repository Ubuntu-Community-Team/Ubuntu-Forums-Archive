---
title: "Deleted loginscreen (GDM thing)"
date: 2008-08-17
forum: Desktop Environments
---

### Post by lefsaker on 2008-08-17
Hello there!

I just installed a GDM theme from gnome-look.org, and selected it as the default theme.

When I restarted X (ctrl+alt+backspace), I got a default blue theme that comes with Ubuntu.
I went back into the settings menu, and deleted every loginscreen I could see there, exept from the default brown-thing, and the new one that I have downloaded.
I made the new one default, and restarted X again.

The new loginscreen doesn't show up, and I'm unable to login.
The only thing I see, is a solid-colored light-brown background with the spinning mouse inside it, like it's constantly loading.

Is it possible to undo the changes? :P

---

### Post by lefsaker on 2008-08-17
Do I have to reinstall Ubuntu?
Cuz I spent like 5-6 hours getting everything to work on my MacBook :P

---

### Post by carlinuxlearner on 2008-08-17
I don't know how to fix your problem, but I can tell you that you will NOT have to reinstall Ubuntu.

C@RL

---

### Post by lefsaker on 2008-08-17
> **carlinuxlearner said:**
> I don't know how to fix your problem, but I can tell you that you will NOT have to reinstall Ubuntu.

C@RL

Great to hear :D

---

### Post by DemonBob on 2008-08-17
If i remember right, try this.  

Try ctrl+alt+f2 or f3 to get a text based login screen. Login. Then "sudo apt-get reinstall ubuntu-gdm-themes"

Then edit "sudo nano /etc/gdm/gdm.conf" 

Find GtkTheme=whatever, make sure it list "GtkTheme=Human"

Then reboot and give it a try.

---

### Post by lefsaker on 2008-08-17
> **DemonBob said:**
> If i remember right, try this.  

Try ctrl+alt+f2 or f3 to get a text based login screen. Login. Then "sudo apt-get reinstall ubuntu-gdm-themes"

Then edit "sudo nano /etc/gdm/gdm.conf" 

Find GtkTheme=whatever, make sure it list "GtkTheme=Human"

Then reboot and give it a try.


Didn't work. It's still looping with a light-brown BG.

Btw. the GtkTheme was already set to Human :confused:

---

### Post by lefsaker on 2008-08-18
I managed to quit X, and login as root in shell.
From there, I started X, and my desktop appeared.

I'm able to open the "Login Window" preferences tab, and modify the theme there :)


Problem solved <3

---

