---
title: "How do I change the login screen from terminal?"
date: 2009-03-20
forum: General Help
---

### Post by amadeus266 on 2009-03-20
I was killing some down time by checking out some gdm login screens from gnome-look.org and when I restarted I am no longer presented with a login screen at all. I can get to tty1 and login there but not with the xserver. I know this probably has been asked before but I really don't have time to search the forums. Thanks in advance.

Running 8.04 by the way.

---

### Post by LowSky on 2009-03-20
dont have time...

at terminal, just type 
startx

---

### Post by amadeus266 on 2009-03-20
Did that before I posted. I get the same results... the xserver is starting up, I get a busy mouse pointer but nothing more.

---

### Post by amadeus266 on 2009-03-20
Anyone?

---

### Post by amadeus266 on 2009-03-20
O.k., I fixed it. I did the following if anyone else has this problem...

1. press ctrl-alt-f2 and login to the terminal
2. enter sudo /etc/init.d/gdm stop
3. enter startx

now I can use the gui...

4. open synaptic and remove completely gdm (which will also remove the fast user switcher and ubuntu-desktop
5. reinstall gdm, fast-user-switch-applet, and ubuntu-desktop

a screen came up asking me which desktop manager I wanted to use but only offered kdm.

6 reboot. kdm loaded fine and i was able to login normally
7. open terminal and enter sudo dpkg-reconfigure gdm
8. select gdm display manager
9. entered sudo apt-get install ubuntustudio-gdm-theme (this forced a theme change I think)
10. rebooted

All was well at that point so I could now log in and go into system->admin->login window and remove the offending theme.

Posted this hoping that it could help someone else. thanks

---

