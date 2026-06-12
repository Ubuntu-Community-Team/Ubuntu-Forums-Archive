---
title: "No Keyboard in GDM"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Ubuntu_User on 2005-04-14
Ok, i've tried the search and asked in #ubuntu, but no solution so far.
Following problem:

1. The computer was working fine with Warthy
2. Did an upgrade to Hoary
3. System boots fine to runlevel 3, GDM comes up.
[COLOR=Red]4. Keyboard is not working (even pressing Numlock doesn't light the LED)[/COLOR]. Mouse is working fine.
4. I can login from a different system with ssh and "sudo /etc/init.d/gdm restart"
5. GDM restarts, system is working normal, i can login und use the computer.
(6. until next reboot  :neutral: )

What i've tried so far:
1. Reinstall different packages (gdm, ubuntu-desktop,...)
2. dbpk-reconfigure xserver-xorg (write a new xorg.conf
3. Staring at the output from "dmesg" and with a remote connection to "tail -f /var/log/syslog" . No hint. (no different output on first (no keyboard) or second (Keyboard)  gdm start.)

Thanks in advance for any hint!

---

### Post by Valavien on 2005-04-14
Do you have a wireless usb keyboard?

I had a problem where I could not use the keyboard at certain times of boot up but it would work in whatever OS I was using.  There was a setting in the BIOS I changed.  Sorry I can't remember what it is.

---

### Post by TMiegel on 2005-04-14
No, it's a standard cable PS/2 Keyboard. (wireless-less)

---

### Post by csanchezotero on 2005-04-16
I have this problem after just doing a upgrade to hoary?  I have a PS/2 keyboard as well.

Any suggestions?

---

### Post by csanchezotero on 2005-04-16
My Ipod Shuffle seem to have been the problem. I unplugged it and all is well. It must have got confused some how!! Strange.

Anyways all is ok now!

---

### Post by TMiegel on 2005-04-19
The problem still exists.

I've tried to unplug all USB-devices (Mouse, Scanner) before booting but still keyboard doesn't work the first time GDM comes up after boot.

 :neutral:

---

### Post by kedde on 2008-05-14
I had the same problem, but when i disabled the ndiswrapper from a root terminal, I was able to login again. ( my card is a Asus wl 138g)

ndiswrapper -r <card>

---

