---
title: "I lost my gnome :("
date: 2006-07-20
forum: Desktop Environments
---

### Post by boyprodigy on 2006-07-20
I was trying to get RAR support yesterday in Ubuntu and I think I may have installed the wrong package from the Synaptic Package Manager because after I closed it (the Synaptic Package Manager) I got a funny error. I thought to myself "oh well whatever, I won't read it. I'll just press OK". So, I reboot my computer and low and behold, ubuntu can't bring up Gnome anymore. 

Now I only have the command line! To someone with experience this is fine, but for me it's hell. I'm new to linux and the last time I used something like this was in 1993 to play DOOM in DOS. Now I know I can reinstall and everything will be fine, but I need those RAR files I was trying to extract. Anyone have any suggestions on how to get those RAR files or get gnome back?

I think the package was called unrar, but I'm not 100% sure.

---

### Post by kaamos on 2006-07-20
Hello!

Log in to the console (the DOS-thingy) and type:
```
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

If you get any errors, please post them here.

Hope this helps.

---

### Post by Thund3rstruck on 2006-07-20
You should be able to type

$startx

to see where the xserver is failing. That will at least give you an idea of why gdm is not loading. Usually there's a backup copy of the xserver config (xorg.conf) in /etc/X11/ that you can restore

---

