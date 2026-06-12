---
title: "Ubuntu 10.10 problem with adjusting screen brightness"
date: 2010-10-12
forum: Desktop Environments
---

### Post by Gniewko on 2010-10-12
Hi,

I have just upgraded my Sony Vaio VGN-BZ21VN to run Ubuntu 10.10. Unfortunately I have noticed that the screen brightness/back-light is no longer controllable by using the key bindings Fn+F5/F6 for brightness down/up, respectively.
Has anyone experienced this after upgrade? It used to work on 10.04 (the best distribution I have ever used). In the meantime I found this fix for it

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/524967](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/524967)

and it seems to do the job. However, the nice bar indicating the strength of the brightness (equivalent to the one you get when adjusting volume) does not show up.

Does anyone have the full solution to this problem? Would be greatly appreciated :)

---

### Post by ikiini on 2011-01-04
What is your drive? if its nvidia, you will need to add the following to your device section of your /etc/X11/xorg.conf file.

'Option "RegistryDwords" "EnableBrightnessControl=1"'


I got this fix from:
[http://www.nvnews.net/vbulletin/showthread.php?p=2204839#post2204839](http://www.nvnews.net/vbulletin/showthread.php?p=2204839#post2204839)


Hope this helps.

---

### Post by Mudar Asbahi on 2011-03-04
good night :)
I have the same problem - when I define my Nvidia Gforce 105m the brightness controller don't work- in my Ubuntu and i was try to write on that's file (xorg.conf) as you tell us ,but it's read only file
so what should I do ??
thanks and sorry for my English if not clear :(................

---

### Post by kcxzero on 2011-03-08
I'm not sure if this solution works. I'm having problems with my screen brightness as well (different vaio model). But to change that read only file you will need to change the permissions of it.

Execute the following command while in the etc/X11/ directory
```
sudo chmod 777 xorg.conf
```

Edit the file carefully, save. Change the permissions of the file back by replacing 777 with 644. Note, be extremely careful editing anything in the xorg file as it could result in losing the GUI. Going by your post it sounds like you are a pretty new user and it may be difficult for you to restore the GUI through the terminal.

---

