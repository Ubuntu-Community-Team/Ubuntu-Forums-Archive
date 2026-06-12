---
title: "nvidia drivers not &quot;remaining&quot; after reboot?"
date: 2005-09-05
forum: Desktop Environments
---

### Post by guice on 2005-09-05
I'm having a really odd issue here.

I installed the nVidia drivers from nVidia's own site. But for some reason everytime I reboot xorg hangs and the drivers are "lost" per say.

Here's the steps; I install the nVidia drivers as root. After doing so, I can start up kdm just fine. If I reboot what happens is kdm does not start up, correctly. It hangs at a blank screen until I push a key. When I push a key, I'm at console login.

I log in and check out the logs and see no error, but it's not "done" loading (ie; still missing a dozen lines I normally see in the logs). kdm currently running, and /tmp/.X0-lock exists.

I stop kdm via /etc/init.d/kdm and the .X0-lock does not get removed. From this point forward, the symptons are rense and repeat; start kdm, blank screen until key press, lock file, incomplete logs, process running, stopping doesn't remove lock file.

It keeps happening until I re-install the nVidia drivers from nVidia's installer. Once I do that (and overwrite currently "installed" drivers) kdm starts up without a flintch.

Apt-get nvidia packages do not work anymore for me. I've done so much with troubleshooting of this and odd opengl problems, I don't think any of them are working anymore. nvidia-glx-config also will not work simply cause I've done a number of manual tweeks to the xorg.conf file. From what I get in it's stdout message, all it does is change nv to nvidia which I've already done a while back.

Any idea as to what's causing my problem? Why won't my nvidia drivers remain after reboot? Why do I have to reinstall them *every time* I reboot my system?

Thanks

And some config info: 
nVidia 5950SE. 
Kernel: 2.6.10-5-k7. 
Using nvidia installer: NVIDIA-Linux-x86-1.0-7676-pkg1.run

---

### Post by MrCheese on 2005-09-06
[QUOTE=guice]I'm having a really odd issue here.

I installed the nVidia drivers from nVidia's own site. But for some reason everytime I reboot xorg hangs and the drivers are "lost" per say.

Here's the steps; I install the nVidia drivers as root. After doing so, I can start up kdm just fine. If I reboot what happens is kdm does not start up, correctly. It hangs at a blank screen until I push a key. When I push a key, I'm at console login.

I log in and check out the logs and see no error, but it's not "done" loading (ie; still missing a dozen lines I normally see in the logs). kdm currently running, and /tmp/.X0-lock exists.

I stop kdm via /etc/init.d/kdm and the .X0-lock does not get removed. From this point forward, the symptons are rense and repeat; start kdm, blank screen until key press, lock file, incomplete logs, process running, stopping doesn't remove lock file.

It keeps happening until I re-install the nVidia drivers from nVidia's installer. Once I do that (and overwrite currently "installed" drivers) kdm starts up without a flintch.

Apt-get nvidia packages do not work anymore for me. I've done so much with troubleshooting of this and odd opengl problems, I don't think any of them are working anymore. nvidia-glx-config also will not work simply cause I've done a number of manual tweeks to the xorg.conf file. From what I get in it's stdout message, all it does is change nv to nvidia which I've already done a while back.

Any idea as to what's causing my problem? Why won't my nvidia drivers remain after reboot? Why do I have to reinstall them *every time* I reboot my system?

Thanks

And some config info: 
nVidia 5950SE. 
Kernel: 2.6.10-5-k7. 
Using nvidia installer: NVIDIA-Linux-x86-1.0-7676-pkg1.run[/QUOTE]


Sounds like the nvidia kernel module is not loading at boot time (I had this problem with Mandrake, however the Ubuntu nvidia package works flawlessly unlike other distros cludgy methods) - try putting it into modules.conf. You can test this out before editing anything by "modprobe nvidia" then manually "startx".

---

### Post by McAviti on 2005-09-06
Ahoj!

I've got exactly the same problem. It is not, by the way, that the nvidia module could not be loaded, at least with me. I can see it with lsmod, and also the xorg log file (as far as it gets) states that nvidia driver is loaded and glx activated.
I posted this issue as well in the nvnews forums - if I receive a hint there I'll also post it here.

McA

---

### Post by daller on 2005-09-06
Have you modified xorg.conf to use "nvidia" instead of "nv"?

("sudo vi /etc/X11/xorg.conf")

Alternatively run: "sudo dpkg-reconfigure xserver-xorg"

---

### Post by McAviti on 2005-09-06
Yop, the nvidia driver has been entered (by whoever) into the xorg.conf file. Anyway, according to the log file, the loading of the nvidia kernel module including glx support seems to be successful.

---

### Post by guice on 2005-09-06
[QUOTE=daller]Have you modified xorg.conf to use "nvidia" instead of "nv"?

("sudo vi /etc/X11/xorg.conf")

Alternatively run: "sudo dpkg-reconfigure xserver-xorg"[/QUOTE]
 Yeah, did change that, as I stated in my first post. I think my problem is exactly the same as McAviti's. It does load the nVidia drivers, but something it stopping xorg from loading fully, not being able to "fix" w/out re-installing the nVidia drivers.

I'll try the other suggestion(s) when I get the chance.

---

### Post by McAviti on 2005-09-06
hi guice!

i got advice in the nvnews forum - and it worked for me. i quote ivan from there:
> The problem is that ubuntu pré-install a driver. Do a dpkg -l | grep nvidia and remove everything that shows there. Then, go to /etc/init.d/ and remove any file that starts with nv (usually, nvidia-glx, nvglx or nvdriver, something like that). Then reinstall the nvidia driver and reboot. This should work!
For reference,
[http://www.nvnews.net/vbulletin/showthread.php?t=55555](http://www.nvnews.net/vbulletin/showthread.php?t=55555) 
during installation i got some complaints about missing mesa files, but now kdm starts up at boot anyway. hope this works for you too. :)

bye,
McA

---

