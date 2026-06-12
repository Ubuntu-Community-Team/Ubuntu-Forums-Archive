---
title: "Can't login to desktop"
date: 2015-05-04
forum: Desktop Environments
---

### Post by drewtam on 2015-05-04
AMD64, Ubuntu 14.10
HD1 = part: Win7, part:Home directory
SSD = Ubuntu OS

It was running great, but I wanted to see if I could get better game performance with proprietary graphics drivers (AMD Radeon). On restart, login is looping back to login. Installed gdm and selected it default, but now it won't show even the login screen. Selecting run session in low graphics mode just recycles back to recovery menu.

1 - how do I undo the gdm install & default for login?
2 - how do I undo the graphics drivers selection and get this system working again? (That kayran isn't going to slay itself.)

Tools available:
win 7 boot
ubuntu on a usb stick

---

### Post by dino99 on 2015-05-05
into a terminal: > sudo dpkg-reconfigure lightdm and select lightdm. If that fails again, then try purging them both, and reinstall lightdm, gdm, unity-greeter

---

### Post by drewtam on 2015-05-05
Thanks. Can you clarify how I purge them both?

For install, it should look like this, right?
sudo apt-get install lightdm 
" "                       gdm
" "                       unity-greeter

---

### Post by drewtam on 2015-05-05
I tried:
> sudo apt-get --purge remove lightdm
as well as gdm and unity-greeter.

I get this error each time:
> sudo: unable to open /var/lib/sudo/drew/tty1: No such file or directory
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened

---

