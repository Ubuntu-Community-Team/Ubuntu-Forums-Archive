---
title: "Problem with desktop effects, hibernation and user switching"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by lordfkiller on 2007-09-22
Hello.

I have 3 problems which I have listed, order by importance:

1- When I first enabled desktop effects, everything(windows transparency etc) was working. After a while, "workspaces on a cube" stopped working. I have only 1 workspace(can't add more). Also, if I create a new account, everything works well in the new one, including "workspaces on a cube".
2- When I logout, or want to switch users, a blank(blue and white or sth like this) screen appears and I have to use power button to turn my computer off. The screen is the same as what I got when I set a wrong resolution a week ago and used recovery mode to change it.
3- When I start from hibernate, I either get an error message telling that sth could not be saved(or maybe loaded), in which case it works well. Or after a while, I see the login screen and enter my username and password and I see a new desktop, as if I had not used hibernate.

Please use question numbers when writing your helpful answer.

ANY help would be appreciated.

Thanks.

---

### Post by pmoseley on 2007-09-22
1) If you're looking for window transparency I suggest you use windows vista. It seems as though you're more concerned about aesthetics of your GUI more than its practicality or functionality. Linux is not geared towards media and 'desktop effects'. Oh, btw, make sure you have the correct 3D acceleration/hardware driver installed for your GPU. If you have an ATI card I wouldn't bother as they are usually quite troublesome.

2) Switching users may cause problems if you've got a beryl type thing running. There could be many reasons for this.

3)From my own personal experience and from literature I've read about linux, hibernate either works or doesn't on most machines. For all of the machines I've tried it on I received errors and had to reboot.

---

### Post by lordfkiller on 2007-09-23
I found the solution!

First, I had to install fglrx driver. That solved the problem with user switching :D
After that, desktop effects stopped working completely. I enabled restricted driver for ATI for 3D acceleration and installed CompizFusion and XGL. That provided me with a lot of wonderful effects for my desktop.

Hibernate doesn't work as expected on Windows XP, too.
I don't think anyone here is going to switch to Windows Vista for its desktop effects. Because those effects are sth Linux users have had for a long time and I don't think anyone is surprised by Aero but people who have not seen any OS except Windows.

By the way, I faced a lot of problems installing XGL and CompizFusion because of bad how tos. Please follow the instruction [here]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") exactly if you want a working CompizFusion.

---

### Post by pmoseley on 2007-09-23
Well done, all that's a little above me...

I tend to think of Linux as reliable, ugly but productive and fast whereas I think of Vista being even uglier, too padded out, unreliable, insecure and slow.

---

### Post by st33med on 2007-09-23
You might want to follow [this HOWTO]("http://ubuntuforums.org/showthread.php?t=471855") to fix hibernation.

---

