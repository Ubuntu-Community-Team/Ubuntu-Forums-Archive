---
title: "How to install Xfce on Jaunty"
date: 2009-08-20
forum: Desktop Environments
---

### Post by mukul_s on 2009-08-20
Hi,

I recently installed Ubuntu Jaunty and Gnome was installed as default DE. I wanted to get rid of Gnome and install Xfce.
By mistake before installing Xfce, I uninstalled some Gnome libraries and packages. So now I am not able to login to Desktop or anything. System boots shows gdm and then nothing works.


Now how can I install Xfce4?

---

### Post by snowpine on 2009-08-20
Give this a try (under "Removing Gnome"):

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by enli on 2009-08-20
When system completely boots, press key combination Ctrl+Alt+F1 and enter your account details.

Type,
```

sudo aptitude update && sudo aptitude install xubuntu-desktop -y

```

After that restart gdm with (just in case if xfce option doesnt get listed at gdm screen)
```

sudo /etc/init.d/gdm restart

```

Press Ctrl+Alt+F7 to go back to gdm screen. At the gdm screen choose your session and select as make it default.

Alternatively if you want to fix your gnome desktop,
```

sudo aptitude install ubuntu-desktop

```

---

### Post by mukul_s on 2009-08-20
Hey,

I don't want to go back to Gnome. So to remove Gnome completely is the link mentioned in post #2 enough??

---

### Post by enli on 2009-08-21
Yes it is enough. But before removing gnome, install XFCE as I don't know if you still get GDM for login screen if you don't.

---

