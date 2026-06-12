---
title: "Set default Login Screen Theme"
date: 2014-06-20
forum: Desktop Environments
---

### Post by ren2 on 2014-06-20
Hi Ubuntu users,

First of all I hope this is the right forum for my question. If not feel free to move it.

I had lubuntu-desktop installed and removed it, because I didn't like it. Everything looks like the default Ubuntu except for the login screen which you can find attached.

How can I make it look the Ubuntu way again?

---

### Post by xc3RnbFO8P on 2014-06-20
This way:
> sudo gedit /etc/lightdm/lightdm.conf

change this line: **greeter-session=lightdm-gtk-greeter**

to: **greeter-session=unity-greeter**

---

### Post by ren2 on 2014-06-21
Thanks a lot =)
It works like a charm.

---

