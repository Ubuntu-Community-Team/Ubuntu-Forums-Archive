---
title: "Roll back &quot;Screens and Graphics&quot; changes."
date: 2008-03-23
forum: Desktop Environments
---

### Post by dapaintballer331 on 2008-03-23
After changing my display settings in the Screen/Graphics GUI (Changed Plug-n-Play to Generic 1600x1200 Widescreen), I can't boot up ubuntu. It freezes after displaying "Running local boot scripts (/etc/rc.local)"

Using a Live CD, can I undo these changes? I restored a xorg.conf, but I still can't get past  "Running local boot scripts (/etc/rc.local)"

---

### Post by Wayoff on 2008-03-23
I am having the same problem. Thanks in advance for any help.

---

### Post by dapaintballer331 on 2008-03-23
I fixed it!

Restoring my old xorg.conf didn't work, I had a backup.

Anyways, here is what you do. On bootup, keep tapping cntrl-alt-F1 and cntrl-alt-F2. One of those (I think F1) will bring you to a command prompt. 

Once you login via the command prompt (after your screen stops flashing, thats what happened to me), type this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I found it elsewhere in the UbuntuForums for another problem.

Then reboot. There is a way to get it all working without a reboot.. but whatever :)

---

