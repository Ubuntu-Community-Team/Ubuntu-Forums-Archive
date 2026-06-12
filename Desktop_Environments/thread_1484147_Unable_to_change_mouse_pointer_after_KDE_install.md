---
title: "Unable to change mouse pointer after KDE install"
date: 2010-05-15
forum: Desktop Environments
---

### Post by wolfandman on 2010-05-15
Hello,

I am using Ubuntu 9.10 for about three months now (I am a total greenhorn) . A few hours ago, I decided to add the KDE 4.4 desktop environment. I followed the procedure on this link. It was all in GUI, no terminal commands required. ([http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml](http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml))

Installed KDE and everything is fine except two problems. 

1. The KDE mouse pointer has become default in GNOME and I just can't change it. Tried everything, changing theme, customising theme and even downloaded the "mouse pointer" app from Software Centre. Nothing works.

2. I am not able to upgrade anything using Kpackagekit. It keeps telling me I don't have authorisation, without asking for my password.

Can anyone help??

Thanks in advance.

---

### Post by ariszlo on 2010-05-27
> **wolfandman said:**
> 1. The KDE mouse pointer has become default in GNOME and I just can't change it. Tried everything, changing theme, customising theme and even downloaded the "mouse pointer" app from Software Centre. Nothing works.

I experienced the same in Debian Sid and changed the mouse pointer  back in Appearance Preferences:
System/Preferences/Appearance/Customize/Pointer: DMZ (White)

---

### Post by hok00age on 2010-05-28
Run:
```
sudo gedit /etc/alternatives/x-cursor-theme
```

You'll get:
```
[Icon Theme]
Name = Oxygen White
Comment = Oxygen mouse theme. Oxygenize your desktop!
Inherits = oxy-white
```

Name = Cursor theme name (or fill as you want)
Comment = (optional)
Inherits = FOLDER NAME OF YOUR CURSOR THEME (usually saved in /usr/share/icons)

Now, change your cursor theme gnome-appearance-properties

Hope this will help you

---

### Post by puller on 2010-08-25
Changing oxy-white with DMZ-white didn't work for me.
I found another way that worked very well:

```
sudo update-alternatives --config x-cursor-theme
```

than select the desired cursor theme.

Source: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/415682](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/415682)

---

### Post by c_07 on 2011-01-01
> **puller said:**
> Changing oxy-white with DMZ-white didn't work for me.
I found another way that worked very well:

```
sudo update-alternatives --config x-cursor-theme
```

than select the desired cursor theme.

Source: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/415682](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/415682)

Thanks, this worked for me!

---

