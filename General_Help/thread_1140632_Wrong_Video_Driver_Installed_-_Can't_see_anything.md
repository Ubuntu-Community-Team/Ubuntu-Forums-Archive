---
title: "Wrong Video Driver Installed - Can't see anything"
date: 2009-04-27
forum: General Help
---

### Post by brodiek on 2009-04-27
Hello,

I'm hoping someone here can help me with a stupid mistake I made. I was having some video issues with Ubuntu 9.04 so I tried installing a new video driver for my Intel Integrated graphics card.

After installing it and rebooting, I can no longer see anything on my screen except for some static (that doesn't move).

How can I uninstall the video card driver without being able to see what I'm actually doing? I'm new to Ubuntu so I'm not really familiar with any shortcuts. I just want to roll back to the default driver that Ubuntu came installed with.

Any ideas?
I'd really appreciate any advice on this.

Thanks :)

---

### Post by glefty on 2009-04-27
Seems like there's an issue with fglrx.  I had the same issue

[http://ubuntuforums.org/showthread.php?t=1138184](http://ubuntuforums.org/showthread.php?t=1138184)

Check this thread, it worked for me.

Good Luck

---

### Post by Kareeser on 2009-04-27
fglrx is used for ATi cards.

brodiek, boot up into the recovery mode (press ESC at the GRUB timeout), and run the following command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by brodiek on 2009-04-27
Kareeser - thx for that. I tried it but that did not resolve it.

glefty - I then followed your thread and it worked! Thanks, everything appears to be back to normal now.

Thanks for your input guys! :)

---

