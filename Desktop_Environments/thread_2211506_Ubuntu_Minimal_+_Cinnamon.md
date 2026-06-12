---
title: "Ubuntu Minimal + Cinnamon"
date: 2014-03-16
forum: Desktop Environments
---

### Post by Tristan_Williams on 2014-03-16
I installed Ubuntu Minimal 13.10 on a spare HDD for playing around.

I want cinnamon on it, because I'm getting a little bored with Xfce

So I installed cinnamon, lightdm, and lightdm-gtk-greeter

Running 'cinnamon' returns an error.
Running 'lightdm' does nothing.
Running 'lightdm-gtk-greeter' goes to the login-screen, but when I log in, the screen goes black and nothing happens


How can I fix this?

---

### Post by sudodus on 2014-03-16
Try ```
sudo service lightdm start
```

or reboot and see what happens automatically :-)

---

### Post by Tristan_Williams on 2014-03-16
Nope. That does start lightdm-gtk-greeter, but cinnamon refuses to start.

I decided to purge cinnamon and go to gnome.

---

### Post by buzzingrobot on 2014-03-16
If you changed the DM your were using in XFCE, you may need to use dpkg-reconfigure to set things up to use the new DM.

---

### Post by tgalati4 on 2014-03-16
Try installing Linux Mint with Cinnamon.  The heavy-lifty has already been done.

---

