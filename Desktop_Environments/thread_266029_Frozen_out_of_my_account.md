---
title: "Frozen out of my account"
date: 2006-09-26
forum: Desktop Environments
---

### Post by sysyphus on 2006-09-26
On my ACER TravelMate 2310 running Ubuntu 6.06 laptop parts of my keyboard have stopped
working.  It's fairly random ie: keys such as "1", capslock, commer, "c", "x" and down
arrow.

I was making some changes to the apache2 server on my last login so I'm guessing (hoping)that's my problem.

Unfortunatly my login requires some of the keys, I can loging using my partners login but she only has limited access and cannot alter files below her home directory.

I was hoping I could login to my account via the command line using copy/paste functions to paste the parts of my login/pw).

That didin't work for my password.](*,) 

Anyone got any idea on how I can get into my account or disable the changes I made to the apache server for a limited account?

---

### Post by Ocxic on 2006-09-26
try going through "sudo dpkg-reconfigure server-xorg".(u may have to reboot)

Befor you run that command backup your origonal file(/etc/X11/xorg.conf), just in case it messes somthing up. if something does happen, you can copy the origonal file back, and all will be well after a reboot.

edit: if you can't get root access to the machien then reboot and when it says "press esc to enter grub menu" do it and enter recovery mode. this will boot your computer into single user mode as root, and you can runn the commands i gave you.

---

### Post by whizbaby on 2006-09-26
Don't know if apache is the root of your problem, but if you start from liveCD and do (assume your new password will be u3un1u)
openssl passwd u3un1u
and copy-paste the result to replace your old key in /etc/shadow (somewhere behind your username) on your HD: voila, a new password is set. Choose one composed of working keys.

---

### Post by sysyphus on 2006-09-26
After some advice form my friendly local LUG (plug in an external keyboard) I've worked out it's a hardware issue.

So I'm hoping installing ubuntu somehow hasn't invalidated my warranty

---

