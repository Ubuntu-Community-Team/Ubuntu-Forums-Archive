---
title: "Boot issues tries to load Ubuntu"
date: 2009-07-11
forum: Desktop Environments
---

### Post by AlanR8 on 2009-07-11
Hi all

Long time Kubuntu user, Jaunty now. All has been well and the machine is fully up to date.

This week I've not rebooted the machine, just closed the lid to hibernate and it works well. However, last night I did a reboot and weird stuff happened!

It tried to boot into UBUNTU, low graphics mode! Also, when I get to the login screen I have to select Kubuntu as the session type otherwise Ubuntu loads, not very well!

The machine is fully up to date and the only new install was last weekend when I installed dropbox from getdropbox.com. This is a remote storage site where you can synch files etc but it had to have Nautilus installed.

Is there a quick and dirty way to get rid of the gnome desktop files so the problem will go away?

---

### Post by coffeecat on 2009-07-11
If you have to have Nautilus installed, then there is no way, clean or dirty, to uninstall the gnome desktop files. Nautilus is more than just a file manager and must have brought in most of gnome as dependencies.

At the login screen, when you select kde, there should be a way of setting kde as the default.

**Edit:** when you say that it's trying to boot into Ubuntu, do you mean you are getting the orange-brown Ubuntu usplash rather than the blue Kubuntu one? If so, you can change this with the instructions in the link below. Go from step 3.

[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

---

### Post by AlanR8 on 2009-07-11
Thanks for the quick reply! 

Once grub has done it's bit, I get the Kubuntu splash screen then a warning in UBUNTU colours that it will start in low graphics mode. I then click OK and I get to the Kubuntu login screen.

Very strange and what annoys me is that I have to intravene in the boot process.

I seem to remember that when I look at the session type the default is now Ubuntu so I had to select Kubuntu to proceed. Oh by the way, when this first happened I had to re-activate the Nvidia driver...

---

### Post by coffeecat on 2009-07-11
I haven't anything sensible to add except that it sounds as though you had two issues cropping up together: the default desktop login problem, and a video driver problem which was causing the low graphics message.

Has reactivating the nvidia driver solved the graphics issue?

---

### Post by AlanR8 on 2009-07-11
it has coffeecat

---

### Post by prshah on 2009-07-11
> **AlanR8 said:**
> but it had to have Nautilus installed.

Is there a quick and dirty way to get rid of the gnome desktop files so the problem will go away?

When you installed and first ran Nautilus, did you use just double click the icon? In that case, it will attempt to (and usually succeed with ugly results) to take over your desktop.

For the future, create a launcher icon to launch nautilus with the command```
nautilus --no-desktop
```

For now, at the login screen, press F10, and choose a KDE session. When prompted, choose to set that as your default. If you are already using a KDE session and/or things don't come back to normal, kill any running nautilus processes.```
sudo killall nautilus
```

---

### Post by AlanR8 on 2009-07-11
> When you installed and first ran Nautilus, did you use just double click the icon? In that case, it will attempt to (and usually succeed with ugly results) to take over your desktop.


That's exactly what happened! Noticed when I unplugged my Nokia mobile that the screen went a horrible brown colour for a moment or two until the KDE desktop came back.

So, now I know what's happened, is there anything that can be done?

---

