---
title: "Feisty locks up after switch user"
date: 2007-05-02
forum: Desktop Environments
---

### Post by EmmAytch on 2007-05-02
Hi

Please don't shoot me down if I'm doing this the wrong way, but has anyone else had this problem with Feisty?

It works fine, then if I switch to another user (ie any of my kids go to their accounts) it works fine up to when they log out.  Then the system locks completely.  Nothing works (caps lock etc) and you can do nothing but hit the reset button.  Can't even restart X.  It makes no difference which accounts are logged into - or the order.

The screen will show the last thing it managed to display - usually the orange wallpaper of the logging out screen.  

I've used ubuntu in the same way since Hoary and not had anything similar.  I did a completely fresh install of Feisty as previously I'd been running Dapper 64bit.  This is 32bit Feisty on a new drive.

Hardware is AMD Athlon 3500, ECS mobo, Radeon 7000 graphics, 1G RAM.

Thanks

---

### Post by EmmAytch on 2007-05-03
Just to be even more specific........

It locks up when you have switched to another user and then log off that new user.  If you use "switch user" instead of log off, it doesn't crash.

---

### Post by gcha on 2007-05-08
I have exactly the same problem. 

I run a Dell Inspirion 6400 with a fresh Feisty install

I am looking for a solution.

---

### Post by tbook on 2007-05-08
Same problem - it locks on log out.

See:

[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/108475](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/108475)
[https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)

---

