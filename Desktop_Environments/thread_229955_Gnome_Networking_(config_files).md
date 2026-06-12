---
title: "Gnome Networking (config files)"
date: 2006-08-05
forum: Desktop Environments
---

### Post by voltagex on 2006-08-05
Hi Ubuntuans/ites
Where does the Gnome Networking applet store it's configuration? I can't get it to forget a certain IP address on my wireless interface.

I had a slight disaster where I accidentally set my IP address the same as the server at school. The server was not happy, the server administrator was not happy. Now I'm back at home I can't get it to forget that IP address - i.e. it keeps setting itself back to 10.1.1.1

Thanks in advance
--voltagex

---

### Post by jordilin on 2006-08-05
I would take a look at /usr/share/gnome-applets, if you don't find it there I would do 
```
locate nameoftheapplet
```
and you'll get a list of files with that name.

---

### Post by voltagex on 2006-08-05
Solved. The gnome network admininstration program (network-admin) stores its configuration in /etc/gnome-system-tools/network - the file is called profiles.xml

I also removed the settings out of /etc/network/interfaces because the static IP was also set in there. Note I wouldn't recommend you mess with this file unless you know what you're doing (I've had lots of experience with it)

On another note, that network-admin application really needs some work. Depending on your settings it can hang indefinately while trying to apply settings and the "Locations" stuff doesn't function as you'd expect it to. Where should I make suggestions about it (I'm not entirely sure the problems I've had are bugs)

Thanks again
--voltagex

---

