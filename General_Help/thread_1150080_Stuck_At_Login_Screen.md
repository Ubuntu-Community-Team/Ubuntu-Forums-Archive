---
title: "Stuck At Login Screen"
date: 2009-05-05
forum: General Help
---

### Post by eatmorehippo on 2009-05-05
I'm using Ubuntu 9.04 on my MacBook with the virtual machine Parallels supporting the OS.

My problem is that whenever I install Ubuntu and then load it up I get "stuck" at the login screen. It says "andrew (my name) logging in in 30 seconds" or something to that effect and allows me to enter in my user name and password. This works fine but once I enter in my password and such it goes into the OS and I can see the desktop for about 2 seconds before I'm thrown back to the login screen from a few seconds ago.

I don't touch anything or alter anything before it just sends me back and I don't have enough time to try to do anything. Anyone know what the problem is?

---

### Post by maheshasolkar on 2009-05-05
Is there a way you can access these files on your linux are and share their contents?
```

  /etc/X11/xorg.conf
  /var/log/Xorg.0.log
```

Can you Alt+Ctrl+F2 (or its Mac-equivalent) and get to a tty? You may be able to access those files if you can log in via tty.

---

### Post by eatmorehippo on 2009-05-06
I started linux using safe terminal and entered in
exec su - "$username"
to try to log in but it had the same effect as before.

As far as accessing those files goes I can't seem to access any files at all.

One strange thing I noticed is that linux doesn't mount a desktop image (to make it seem like a new hardrive) which is unlike XP, is this normal?

---

