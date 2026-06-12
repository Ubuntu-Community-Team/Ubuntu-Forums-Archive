---
title: "no xorg.conf file"
date: 2006-07-13
forum: Desktop Environments
---

### Post by shane_on_u on 2006-07-13
I just installed ubuntu on my other machine. This one has been giving me problems for months. It has an ATI x850 card which I think is the reason for all my problems.

Anyway, as I was saying, I just installed Ubuntu on that machine. The install went fine without any problems. I try to boot Ubuntu but I get "failed to start xserver" or something to that effect. I boot into recovery mode, install the ati driver "apt-get install linux-restricted......xorg-driver-fglrx". I then realize that I don't have an xorg.conf file in /etc/X11/xorg.conf. I've been through the install process twice and same issue. Anyone have any ideas as to what I need to do?

I currently cannot boot my system into anything other than the command line. Please help!

---

### Post by shane_on_u on 2006-07-13
I should probably add that I can't do "sudo dpkg-reconfigure xserver-xorg". It tells me that "Package xserver-xorg is not installed and no info is available."

---

### Post by taurus on 2006-07-13
Did you install the desktop version or the server version???

---

### Post by shane_on_u on 2006-07-13
It's the desktop version. I don't know why it didn't install xserver, I had to install it manually: sudo apt-get install xserver-xorg.

It's working now.

---

### Post by taurus on 2006-07-13
So, your machine boots directly into a console!  See what happens when you type this command at the prompt?

```

startx

```

---

