---
title: "problems with X server and nvidia"
date: 2005-05-23
forum: Desktop Environments
---

### Post by 1000i1 on 2005-05-23
Well I installed ubuntu about 2 months ago, and since today all was working perfectly, but today when I've started my computer an error message has appeared saying that there was a problem with my X server and it couldn't initialize or something like this. so this is what I've done:

- Reinstall X server and nvidia drivers.
- Confiugre x using xf86config several times until it has worked.

X running again, what I can't do:

- anything involving glx (games in my case).

The problem comes when I try to run "nvidia-glx-config" it says:
      "Error: /etc/X11/XF86Config-4 or /var/lib/xfree86/XF86Config-4.md5sum
       are missing from your system. Please be sure that your xserver package is
       installed correctly."

So I've run dpkg-reconfigure xserver-xfree86 and it doesn't create the XF86Config-4, it creates the XF86Config but not the one I need, I've tryed renaming it and runing the nvidia-glx again and it says it works, but nothing really happens. I don't know what else to do, any ideas?? Thanks.

---

### Post by 1000i1 on 2005-05-25
Please somebody help me, I don't have any clue on how to solve this problem, I'm seriously thinking about reinstalling ububntu, but I don't want to. Please, nobody???

---

