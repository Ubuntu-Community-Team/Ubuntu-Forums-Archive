---
title: "can i create a minimal ubuntu desktop as server"
date: 2009-02-24
forum: General Help
---

### Post by GreenDance on 2009-02-24
Hi, I'm new to Ubuntu, I would like to know please if this is possible, I would like to create my own minimal ubuntu-based distro, i would like it to be desktop based, when i turn my white-box pc on i would like it to boot into my distro and automatically be live online with Apache, PHP, MySQL and PHPMyAdmin, I don't need anything else that I know of, security is important. I would like to create it into an ISO as well.

I know of ubuntu server edition but i would like to run my own ubuntu-based distro,

Thank You ):P

---

### Post by liamnixon on 2009-02-24
You might could start here, if you haven't already checked it out. ;)
[URL="https://help.ubuntu.com/community/Installation/MinimalCD"]
https://help.ubuntu.com/community/Installation/MinimalCD[/URL]

EDIT:Wait, I overlooked the "desktop based" part.  Oops!

---

### Post by GreenDance on 2009-02-25
I forgot to mention sorry, I would like to include Firefox as well. Thank you ):P

---

### Post by adult swim on 2009-02-25
i was looking to do this the other day and ended up just installing the server.  using the minimal install cd no matter what, i was going to end up with kde-desktop, or gnome-desktop.  i think if you dont want to use the server edition, the best thing would be to use arch or something similar that you have to build from the ground up.

---

### Post by GreenDance on 2009-02-25
I hope no one minds, I would like to bump my question up, thanks ):P

---

### Post by sej7278 on 2009-02-25
> **GreenDance said:**
> I hope no one minds, I would like to bump my question up, thanks ):P

i'd be interested too.

i'm going to build a 8.04 LTS fileserver, i was going to use the server edition, but i need xorg and gimp for my scanner so was going to go with desktop release instead.

maybe server plus gnome would be better than trying to strip down desktop.

---

### Post by jimmyhacker on 2009-02-25
install ubuntu server,connect internet,then type sudo apt-get install xorg xfce4 php apache phpmyadmin gtk-2 python-2.5 and initrd your installation and put vmlinuz in cd make a dir into cd named pool and put ubuntu-server and your packets.

---

