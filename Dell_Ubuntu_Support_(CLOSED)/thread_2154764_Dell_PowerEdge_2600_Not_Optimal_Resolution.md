---
title: "Dell PowerEdge 2600 Not Optimal Resolution"
date: 2013-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rikitheshadow on 2013-06-15
Having trouble with installing ubuntu 12.04 server on a Dell Poweredge 2600. I step through the installer with no problems, partitioned it manually using an online guide, installer finishes with grub and I reboot. After bios and everything on startup clears I get a white object that falls down to the bottom right corner of the screen, object is similar to video diagnostic check. And then I get my monitor telling me this is not an optimal resolution..... I know other people get this after installing a gui but I don't even get a terminal prompt after a fresh install.... Any advice?

I ran Dell's diagnostic cd and all the hardware clears tests with no errors.

---

### Post by newbie-user on 2013-06-16
Install OpenSSH during installation. Then you should be able to ssh into the server even with no monitor output. Add the "nomodeset" option to the /etc/default/grub file

Change:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

then reload grub:
```
update-grub
```

and restart.

---

### Post by rikitheshadow on 2013-06-16
I thought ahead about SSH and had it pre-installed when it asked for packages in the OS installer. I logged on via PuTTy on my windows desktop and attempted to reconfigure the grub config file like you said. However, after updating and rebooting I still got the same result. Determined to find a quick solution I went all over google looking for an option to adjust the screen resolution and ended settling on this one guy's method for configuring the grub file.

This is what he set

```
GRUB_GFXMODE=800x600
GRUB_CMDLINE_LINUX_DEFAULT="915.modeset=0 nomodeset"
```

After that it worked perfectly and I could see the terminal page. Didn't even get that weird white image running across the screen anymore.

---

