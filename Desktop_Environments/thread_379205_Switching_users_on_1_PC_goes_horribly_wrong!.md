---
title: "Switching users on 1 PC goes horribly wrong!"
date: 2007-03-08
forum: Desktop Environments
---

### Post by robenroute on 2007-03-08
Hi there,

I've noticed something very strange and, in the end, utterly frustrating. I've got a PC that is used by 2 different people, each with their own account. When I login under my own account, do a few things and then logout (or just switch user), the other user signs in, but just after the welcome tune is played, the Ubuntu desktop splash screen (the bar in the middle of the screen, showing the different programs starting up (Nautilus, etc.)) just sits there and doesn't go away. With that bar sitting there, the user is not able to start OpenOffice for instance; he's not even able to log off/sign out. The whole desktop environment just hangs. Going to the command line (CTRL+ALT+F1), I can kill the desktop and go back to my (first user) desktop environment, where everything just works as usual.

This happens consistently. Only a complete reboot sorts it out. The second user can only log in to the system on a fresh system start-up. As soon as I (first user) have logged in (even after having logged out), the other user is not able to get onto the system (Gnome desktop environment).

Any ideas? Help would be much appreciated as this is a situation that's unworkable for the both of us.

Thanks a bunch!

---

### Post by robenroute on 2007-03-09
Not a single person with the same problem? Just create an extra user on your system, log on as your good self, switch users and hopefully you'll notice the same as me (or should I say, hopefully you won't notice the same....)

TIA

---

### Post by robenroute on 2007-03-30
After upgrading to the latest nVidia driver (1.0-9755), this problem hasn't cropped up. :-)

---

### Post by robenroute on 2007-04-23
> **robenroute said:**
> After upgrading to the latest nVidia driver (1.0-9755), this problem hasn't cropped up. :-)

....well, not true! Yesterday, it happened again. I think I'm on to something since this happens when I've got an application running/open that uses sound. I use Quod Libet (0.24.1 & Edgy) and I've noticed that even when QL isn't playing a song (just paused, because there is no stop/halt with QL!), switching users goes horribly wrong. As soon as I close QL entirely, no hassles with switching users.

Is there anyone out there that can confirm/reconize/coment on this?

Oodles of thanks....

---

### Post by Abandon on 2007-04-23
I don't have that problem, but something simular. When the 2nd user logs in and I wanno go back, the screen gets black. Nothing helps, only a ctr. alt backspace

---

### Post by sebbouckaert on 2007-08-08
> **Abandon said:**
> I don't have that problem, but something simular. When the 2nd user logs in and I wanno go back, the screen gets black. Nothing helps, only a ctr. alt backspace

I have exactly the same. I use the NVIDIA 7755 driver. Haven't found a workaround/solution yet :(

---

### Post by skiffler on 2007-11-18
> **sebbouckaert said:**
> I have exactly the same. I use the NVIDIA 7755 driver. Haven't found a workaround/solution yet :(
I have exactly the same problem as described by you both. My MB has onboard Nvidia 6150. Everything seems to work OK apart from this. Have the latest Nvidia drivers (updated a couple of days ago IIRC)

---

### Post by kadirmalak on 2007-12-16
I think you should read this [[COLOR="Sienna"]http://ubuntuforums.org/showthread.php?t=630017&highlight=user+switch+problem[/COLOR]]("http://ubuntuforums.org/showthread.php?t=630017&highlight=user+switch+problem")

---

