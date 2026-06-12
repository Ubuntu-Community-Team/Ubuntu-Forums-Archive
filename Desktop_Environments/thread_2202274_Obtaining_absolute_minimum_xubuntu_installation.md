---
title: "Obtaining absolute minimum xubuntu installation"
date: 2014-01-28
forum: Desktop Environments
---

### Post by mdlueck on 2014-01-28
I desire to obtain a minimal xubuntu installation. I thought this morning to start with the minimum Ubuntu Server installation, then added xubuntu-desktop.

Unfortunately doing so installed all of the "suggested / recommended" packages which xubuntu-desktop thought helpful.

Is there a way to specifically take xubuntu-desktop and only its requirements to work, not all of the suggested / optional packages?

---

### Post by sudodus on 2014-01-28
One way is from the mini-iso and install only XFCE
```

sudo apt-get install xfce4
```

and then manually add whatever you want.

---

### Post by The Cog on 2014-01-28
Try:
```
sudo apt-get install --no-install-recommends xubuntu-desktop
```

---

### Post by sudodus on 2014-01-28
Another way is

```
sudo apt-getinstall --no-install-recommends xubuntu-desktop
```

See ```
man apt-get
```

---

### Post by ibjsb4 on 2014-01-28
Here's a breakdown on both.

[http://packages.ubuntu.com/precise/xubuntu-desktop](http://packages.ubuntu.com/precise/xubuntu-desktop)

[http://packages.ubuntu.com/precise/xfce4](http://packages.ubuntu.com/precise/xfce4)

---

### Post by mdlueck on 2014-01-28
Thank you for pointing out --no-install-recommends switch to apt-get. That sounds like what I was seeking.

Now, is there another method to arrive at a text install of Ubuntu other than using the server install? I am pulling down the Ubuntu Alternate image right now to see if that allows for a small footprint text only install. With a thin Ubuntu, then I will add the xubuntu-desktop via the suggested syntax.

Thank you all again.

---

### Post by mörgæs on 2014-01-28
The [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") is what you are looking for.

---

### Post by sudodus on 2014-01-28
> **mdlueck said:**
> Thank you for pointing out --no-install-recommends switch to apt-get. That sounds like what I was seeking.

Now, is there another method to arrive at a text install of Ubuntu other than using the server install? I am pulling down the Ubuntu Alternate image right now to see if that allows for a small footprint text only install. With a thin Ubuntu, then I will add the xubuntu-desktop via the suggested syntax.

Thank you all again.

See post #2. You can also install the [One Button Installer - text]("http://ubuntuforums.org/showthread.php?t=2172971") itself. It is a small text only install.

---

### Post by mdlueck on 2014-01-28
Aaahhh, minimal is where they hide the functionality, not in the alternate ISO. Thank you so much. I got the minimal text only Ubuntu install completed, chose the virtual kernel since I was installing in a VirtualBox environment, then added the xubuntu-desktop without all of the needless extras. Boots up nice and quickly. Thank you all for your assistance.

---

### Post by mörgæs on 2014-01-29
Good, please mark the thread 'solved'.

---

