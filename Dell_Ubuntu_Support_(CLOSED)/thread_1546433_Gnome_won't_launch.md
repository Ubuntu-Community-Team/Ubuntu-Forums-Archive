---
title: "Gnome won't launch"
date: 2010-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dan.hofer@abellatech.com on 2010-08-05
I'm attempting to install Ubuntu desktop 10.04 LTS 32 bit as a VMWare image under VMWare workstation 6. The host OS is Windows 7 enterprise 64 bit on a Dell Inspiron 1564 with an intel i3 processor with 4 mb of RAM. 

The 64 bit version installs fine but the 32 bit version won't work well. It installs and takes me to a command prompt for login. This works. When I run startx to invoke gnome it won't work. 

The message displayed basically says 'illegal instruction'. I believe that I'm dealing with a video driver issue. 

What is weird to me is the 64 bit version works but not the 32.

Any ideas?

---

### Post by dan.hofer@abellatech.com on 2010-08-05
Additionally, the log /var/log/Xorg.0.log shows a failure loading the 'VGAHW' module.

---

