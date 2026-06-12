---
title: "Installing loads of Desktop Envirnoments/Window Managers... Bad choice?"
date: 2007-06-26
forum: Desktop Environments
---

### Post by kombucha on 2007-06-26
I'm wondering if it's a bad idea to install a multitude of desktop environments and window managers on top of Kubuntu. Actually... I'm not entirely sure DEs are possible? I'm pretty sure they are... I think I remember installing Kubuntu on top of Ubuntu back in the day, but now I'm thinking more along the lines of Xubuntu over Kubuntu, and then window managers from Fluxbox to IceWM to XFWM and others I can play around with. Will I be losing any system performance or resources other than hard drive space by installing all of these? Also, when I finally settle on one or two, how easy will it be to uninstall the others without leaving too many fragments? Basically I've tried reading all I can about which setup is the best balance of speed, functionality and aesthetics, but it seems nothing will appease me except to give them a whirl myself.

And if anyone has any decent guides for what I'm planning, I'd be much obliged.

Thanks for the advice!

---

### Post by rillip on 2007-06-27
Some care should be taken, but what you're proposing is possible.  I have Gnome installed after KDE right now.  In theorey they can all play along, but the more you have the more difficult it's probably going to be to fix if something screws up.  Just something to keep in mind.  And no, no performance hits other than disk space, only one runs at a time.

Uninstalling will be relatively easy if you JUST install xfce or the like. If you go for xubuntu-desktop, a LOT of programs get placed on that you'll have to remove.  There was a very helpful guide that a member pointed me to here on the forums on how to remove xfce afterward, it was just a giant list of xfce specific programs to remove with apt-get, simple copy paste, but if you don't find something like that, ugh, I pitty you.

So, if you just install the DEs/WM, fine.  If you install the whole metapackage, you kick up the dificulty a knotch. (BAM!)

---

### Post by kombucha on 2007-06-27
So it wouldn't be as simple as just uninstalling the entire xubuntu-desktop package with a single command if I go that route?

---

### Post by merlinus on 2007-06-27
If you use
```

sudo aptitude install xubuntu-desktop

```
then you can get rid of it with
```

sudo aptitude remove xubuntu-desktop

```

-merlin

---

### Post by maybeway36 on 2007-06-27
Using aptitude is definitely the way to go.
As for installing another DE, if you install Xubuntu over Kubuntu I suggest using gdm, as it remembers your default instead of defaulting to the last one you used. The login screen will say "xubuntu" however.

---

### Post by RedSquirrel on 2007-06-27
> **maybeway36 said:**
> Using aptitude is definitely the way to go.
As for installing another DE, if you install Xubuntu over Kubuntu I suggest using gdm, as it remembers your default instead of defaulting to the last one you used. The login screen will say "xubuntu" however.

The theme of the login screen can be changed. You could go back to the regular Ubuntu "Human" gdm theme or you could install some other ones. Tropic (package: tropic-gdm-theme) is nice (if you like orange, that is ;)).

EDIT:

In Ubuntu and Xubuntu, there is a menu item called "Login Window" or "Login Screen" which is used to change the gdm theme.

In other environments/window managers, try Apps -> System -> GDM Setup.

---

### Post by kombucha on 2007-06-30
Alright, I finally installed xubuntu-desktop today with Aptitude, and so far I really like it. I got Compiz Fusion running on it very well on my aging hardware, even if it costs me some speed. But even before I added desktop effects, it wasn't quite as speedy at launching programs as I might have hoped. I understand that programs like AmaroK take longer because they also have to load KDE components, but even Firefox, which I think is GTK-based?, took five or six seconds. That's not awful, but not exactly flying, either.
Since I installed xubuntu-desktop on top of an original Kubuntu setup, is using aptitude to remove kubuntu-desktop an option? Is it a good idea, in that it will speed things up? Or will it just cost me all of the KDE-designed programs like AmaroK? Any other advice on how to get this baby to scream? :P Would simply redownloading the Xubuntu iso and wiping the drive be a good option (good enough to warrant the hassle)? I guess I just want the color settings and default basic programs from KDE gone... like right now KWrite is the default and it has color issues, I'd love for Xubuntu to do its thing. I'm actually coming to the conclusion that wiping may be a great idea, but you tell me.
Thanks, as always.

---

### Post by diggity on 2007-07-01
It really doesn't matter how many window managers you have installed as you only run one at a time. The only thing that might be a problem is if you have limited hard disk space. I currently have KDE, Gnome, IceWM and Fluxbox installed. I'm currently using IceWM (and am really diggin' it) and haven't had any problems at all. IMHO I think it's a good thing to try out several different WMs to see which one you want to use.

---

### Post by kombucha on 2007-07-01
Well... are you sure it applies to desktop environments as well?
It all just seems so muddled right now, I don't really want to leave it as is. I'm just wondering between uninstalling KDE, wiping it and starting fresh, or some other option.

---

### Post by diggity on 2007-07-01
Yes. Window Managers and Desktop Environments are basically the same thing. I would recommend installing them at the same time, deciding which one(s) you want to use and then do a clean install with the one you have decided upon. I'd do that myself, but I kind of like switching back and forth every once in a while to keep things fresh. I haven't noticed any performance issues (other than wm's tend to be much faster due to the limited functionality).

---

### Post by kombucha on 2007-07-01
Alright then, I think I'm going to go ahead and wipe the drive, then reinstall Xubuntu Gutsy Tribe 2 on it, then work on reconfiguring everything. Thanks for the advice so far :D

---

### Post by RedSquirrel on 2007-07-01
It sounds like you're satisfied with Xubuntu, but I just thought I'd mention that you could do a barebones install if you really want to make the most of your system:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I skimmed this thread again and didn't see your system specs but if it's old a barebones install might be a good idea.

Bear in mind that applications like Firefox are quite resource-intensive and they usually take a bit of time to start.

Good luck.

---

### Post by kombucha on 2007-07-01
Yeah, Firefox is doing better now, but you're right that I shouldn't expect it to open as rapidly as I had imagined under any circumstances.

I guess I was downplaying my specs a bit... I just wanted a major speed boost, and I consider my computer aging, but certainly not barebones-worthy:

Athlon XP 2000+
512 MB RAM
ATI Radeon 9000

:D

---

