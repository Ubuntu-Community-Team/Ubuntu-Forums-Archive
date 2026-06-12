---
title: "auto login into ubuntu 8.10 with no monitor"
date: 2008-12-20
forum: General Help
---

### Post by Alden born on 2008-12-20
ok I'm sure this is not a driver issue but basically i want ubuntu to auto login with no monitor.  because when i boot up the computer and it detects that there is no monitor it sorta hangs with a error message, i plug one in to see whats happing and there is fail safe message it talks about configuring xorg.  I need a work around or a way to disable it so when i have to reboot the computer, i don't need to attach a monitor to the computer to get it to log in. FYI I'm using the computer as a file server. and i still want to use the VNC.

thanks

---

### Post by aktar on 2009-01-22
same here, I want ubuntu 8.10 desktop as server without monitor, Kb, mouse.

Still no solutions

---

### Post by sedawk on 2009-01-22
You can edit /boot/grub/menu.lst and append the word "text" at the
end of the "kernel" line(s) to boot into text mode only.

You can still run normal applications with your local display
when logging in via "ssh -X fileserver" or you can run
VNC on the "fileserver" - VNC uses a virtual desktop and
should perfectly work on an Ubuntu only booted to text mode.

---

