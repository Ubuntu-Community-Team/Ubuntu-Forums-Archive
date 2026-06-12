---
title: "Gnome theme disappears after reboot"
date: 2009-02-23
forum: Desktop Environments
---

### Post by n8wood on 2009-02-23
Occasionally when I reboot my 0810 system, the Gnome theme doesn't display. I get a standard gray theme until I open Preferences > Appearance. As soon as the Appearance window opens, the theme gets applied immediately without any interaction.

Any ideas what could be causing this? I'm developing a VM for students and want to make sure their first Linux/Ubuntu experience isn't riddled with weird bugs.

thanks.

---

### Post by n8wood on 2009-02-25
I have rebuilt my 0810 VM and I am still seeing this problem. I have installed a standard Ubuntu desktop, with the only added package being msttcorefonts, cabextract. Once I change the default fonts, this behavior starts. I reboot and the Gnome theme gets reset. Once I open the Appearance window, the settings switch back immediately.

---

### Post by trestevenson on 2009-03-13
Ditto.  I'm having the exact same problem as well.  It's not a huge inconvenience, but it's annoying nonetheless.

---

### Post by riden on 2009-05-22
Hi folks,

I had similar problem, I found how to fix it. Go to *System -> Settings -> Startup applications* and check on *GNOME settings daemon*. Text labels are not exact, because I use Russian localization ;)

---

### Post by Aea on 2011-01-31
That doesn't actually fix it (for me), here's what I've observed: 

In my situation this happens if: 
- I have 3rd Party Restricted Drivers 
- I change the wallpaper

Here's how I fixed it (nearly vanilla Ubuntu 10.10 install on a Dell 6500). 

"The Easy Fix"
$ cd ~
$ rm -rf .gconfd
(logout)

If you change your wallpaper, you'll need to repeat the procedure. If that doesn't work you can try this (warning: you will lose your gnome config, including panel changes, possible wifi login details, etc)

"The Take a Hammer to It"
- Boot to Login Screen
- CTRL - ALT - F2
- $ cd ~
- $ rm -rf .gconfd .gconf .nautilus
- $ mv .gnome2 .gnome2.bak
- CTRL - ALT - F7

You will then need to login again, this should fix the problem. Any wallpaper (and potentially other gnome changes) will cause the problem to reoccur, but you shouldn't lose your gnome settings if you try the first approach. 

Let me know if this helps.

**Edit:** Sorry, I think I necroed this thread, thought I was in another location.

---

