---
title: "anyone else got thei nvidia driver screwed by last update?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by louis_nichols on 2006-06-03
My X server doesn't start, because it says (something like) there's an API missmatch between the glx extensin, which is at version 8756, and the kernel module, which is at version 8762.

hasn't anyone else encountered this?

---

### Post by tseliot on 2006-06-03
Try removing all the packages:
```
sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r` linux-restricted-modules-common
```

then
```
sudo apt-get --purge remove nvidia-glx-legacy nvidia-xconfig nvidia-settings linux-restricted-modules-`uname -r` linux-restricted-modules-common
```

then install the nvidia driver:
```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

and reboot

---

### Post by McLoud on 2006-06-03
I was using the nvidia proprietary drivers, after the update, they got uninstalled, and the X couldn't start since it didnt found the driver. Reinstalling it solved, but I think that this is less than desired behaviour, I know how to make it work, but how about the poor n00bs?](*,)

---

### Post by louis_nichols on 2006-06-03
[QUOTE=tseliot]Try removing all the packages:
```
sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r` linux-restricted-modules-common
```

then
```
sudo apt-get --purge remove nvidia-glx-legacy nvidia-xconfig nvidia-settings linux-restricted-modules-`uname -r` linux-restricted-modules-common
```

then install the nvidia driver:
```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

and reboot[/QUOTE]

Thanks for the answer. Sorry I forgot to mention, but I had tried that and, surprisingly, I get the same result. :(

---

### Post by tseliot on 2006-06-04
Try my script (the one for driver **8756** ):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by LordMau on 2006-06-04
[QUOTE=louis_nichols]My X server doesn't start, because it says (something like) there's an API missmatch between the glx extensin, which is at version 8756, and the kernel module, which is at version 8762.

hasn't anyone else encountered this?[/QUOTE]

Also happened here. After latest to this date update. Followed tseliot's first advice to purge the reinstall but still no go. Used the scripts supplied by tseliot later on (specifically 8762 not 8756)to X, but i lost the use of XGL, error here is a combination of something with GLX, lack composite extension and the meta key. Now just using xfce's window manager.

Any more ideas? Will try 8756 script, but i hope we can get s solution using dapper's own repos.

Thanks.!

---

### Post by louis_nichols on 2006-06-04
[QUOTE=LordMau]Also happened here. After latest to this date update. Followed tseliot's first advice to purge the reinstall but still no go. Used the scripts supplied by tseliot later on (specifically 8762 not 8756)to X, but i lost the use of XGL, error here is a combination of something with GLX, lack composite extension and the meta key. Now just using xfce's window manager.

Any more ideas? Will try 8756 script, but i hope we can get s solution using dapper's own repos.

Thanks.![/QUOTE]

I got the exact same symptoms: manual installation of nvidia 8756 package works, but no xgl. Purging and re-installing debs, as I said, doesn't work either. :confused: 

I'll install the nvidia driver back from their package. But I hate the situation.

---

### Post by LordMau on 2006-06-04
I've now made it work. Keys to my own success:

** follow tesliot's advice thoroughly. Key was to REBOOT after all the purging and reinstallation of drivers.

** PRIOR to rebooting it helped that I temporarily disabled XGL and used xfwm4 (for gnome its metacity right?) as WM. Once it successfully logged on as 8762, I doubled check the running compiz and found got a "No GLXFBConfig for default depth" error. So I first reinstalled libGL1-mesa, after which I set up the XGL gdm.conf and compiz commands. Now xgl is going smoothly with nvidia 8762.

** HTH. But it still begs the question why those initial erros though considering its now the official release lol.

---

### Post by tseliot on 2006-06-04
[QUOTE=LordMau]I've now made it work. Keys to my own success:

** follow tesliot's advice thoroughly. Key was to REBOOT after all the purging and reinstallation of drivers.

** PRIOR to rebooting it helped that I temporarily disabled XGL and used xfwm4 (for gnome its metacity right?) as WM. Once it successfully logged on as 8762, I doubled check the running compiz and found got a "No GLXFBConfig for default depth" error. So I first reinstalled libGL1-mesa, after which I set up the XGL gdm.conf and compiz commands. Now xgl is going smoothly with nvidia 8762.

** HTH. But it still begs the question why those initial erros though considering its now the official release lol.[/QUOTE]
It shouldn't happen on a fresh install

---

