---
title: "Ubuntu on 400mhz PC"
date: 2005-06-11
forum: Desktop Environments
---

### Post by NeoMayhem on 2005-06-11
I just installed ubuntu on an old 400mhz PC with 64mb of ram. Gnome is very slow, which I was expecting. What is a good window manager/desktop environment that would be a lot faster on this system? I am going to be running ssh, apache2, firefox and xmms on this system, probably nothing else.

Any other tips to make things faster?

If I have have to remove xorg, is there a way to get a higher resolution in text mode?

---

### Post by clb137 on 2005-06-11
[QUOTE=NeoMayhem]I just installed ubuntu on an old 400mhz PC with 64mb of ram. Gnome is very slow, which I was expecting. What is a good window manager/desktop environment that would be a lot faster on this system? I am going to be running ssh, apache2, firefox and xmms on this system, probably nothing else.

Any other tips to make things faster?

If I have have to remove xorg, is there a way to get a higher resolution in text mode?[/QUOTE]

If u need a X Session windows manager,  may i suggest you install XFCE

---

### Post by az on 2005-06-11
If you are running apache2 and ssh, I would reccommend you get rid of x.

Boot with the vga=791 (?) parameter to get higher resolution.   Look up the vga kernel boot options for a complete list of parameters... (google kernel boot options vga)

---

### Post by milosz on 2005-06-11
You have to slowe PC to use GNOME. Try XFCE, blackbox or sth else ;)

---

### Post by NeoMayhem on 2005-06-11
[QUOTE=azz]If you are running apache2 and ssh, I would reccommend you get rid of x.

Boot with the vga=791 (?) parameter to get higher resolution.   Look up the vga kernel boot options for a complete list of parameters... (google kernel boot options vga)[/QUOTE]

Yeah, thats what I am thinking. How can I disable X from loading at startup? I know its something simple, but I dont remember the right files to edit. I want to use a text based login as well.

---

### Post by joepotter on 2005-06-11
[QUOTE=NeoMayhem]Yeah, thats what I am thinking. How can I disable X from loading at startup? I know its something simple, but I dont remember the right files to edit. I want to use a text based login as well.[/QUOTE]

sudo apt-get remove gdm


Now, reboot the box into a wonderful text login.

---

