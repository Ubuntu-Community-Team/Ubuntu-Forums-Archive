---
title: "After disabling xdm service, can't start ubuntu problem"
date: 2008-12-14
forum: General Help
---

### Post by staspinar on 2008-12-14
I'm using Ubuntu 8.10.

For using the login window preferences , I tried to change my default display manager from xdm to gdm by disabling the xdm service.

But the system crashed.

Can Anyone can help me to solve this problem.

After booting messages displayed are like below:

boot from (hd0,0) ext3
starting up
loading ,please wait...
19+0 records in
19+0 records out
kinit : name_to_dev_t ...
kinit : trying to resume from /dev/disk/by-uuid/...
kinit : No resume image, doing normal boot ...
[....] usb 2-1 : device not accepting address 10, error -71
[....] hub 2-0 : 1.0 : unable to enumerate USB device on port 1

Ubuntu 8.10 selahattin-laptop tty1

selahattin-laptop login : [....] ata5.00 : exception Emask 0x0 Sact 0x0 SErr 0x0 action 0x6 frozen
[....]
[....]
[....]

login : 

I can loggin with my account but the system doesn't start and want login from me again

---

### Post by staspinar on 2008-12-14
After rebooting with recovery option , choosing root option and entering root password I can use startx command.

After executing startx the system is started but I'm getting now another error:
"User Switcher" has quit unexpectedly
If you reload a panel object, it will automatically be added back to the panel.

and the keyboard isn't work...

I can reboot using Ctrl+Alt+Delete

---

### Post by staspinar on 2008-12-14
On booting system I also got a warning message, after gdm service :

* Not starting GNOME Display Manager (gdm); it is not the default display manager.

---

### Post by staspinar on 2008-12-14
I can also start xdm using command : 

sudo /etc/init.d/xdm start

But after displaying login screen , I am not able to enter my account and password, because the keyboard is not working.

---

### Post by staspinar on 2008-12-14
After reconfiguring gdm by command :

sudo dpkg-reconfigure gdm

and setting gdm as default display manager and rebooting computer in normal mode

After entering user and password, I'm getting authentication error...

---

### Post by staspinar on 2008-12-14
details of xsession-errors file

/etc/gdm/Xsession : beginning session setup ...
/etc/profile : 30 : /bin : permission denied
/etc/profile : 34 : save : not found

---

