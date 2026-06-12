---
title: "Desktop Effects Troubles on Ubuntu 8.10"
date: 2009-03-03
forum: Desktop Environments
---

### Post by LeonBlade on 2009-03-03
Hello everyone,

I'm sure you are all sick of seeing these kinds of posts but I'm having some trouble with enabling Desktop Effects.

When I had 8.04 LTS I was able to enable Desktop Effects after installing my graphics driver, NVIDIA accelerated graphics driver (version 96).

The only problem was that it limited my resolution tremendously, but I was able to use full desktop effects just fine.

After upgrading to 8.10, I cannot use desktop effects.  My resolution is back up to 1600x1024 though, so that is a plus.

My driver IS installed and enabled, but for some reason I cannot get Desktop Effects to work for me.

So, if anyone can help me out with my problem it would be well appreciated. 

Thanks in advance,
Leon Blade

---

### Post by Wallies on 2009-03-04
I met the same issue. :(

---

### Post by LeonBlade on 2009-03-04
Does anyone know what my problem is?

---

### Post by LeonBlade on 2009-03-05
Bumping this topic.

---

### Post by Therion on 2009-03-05
> **LeonBlade said:**
> My driver IS installed and enabled, but for some reason I cannot get Desktop Effects to work for me.
Which driver though?  Are you sure you have the nVidia Restricted Driver installed and running?  You've checked?

If so, what happens when you try to enable desktop effects?  Do you have the option available and nothing happens, is it greyed out, what?

Have you tried installing **compizconfig-settings-manager** via Synaptic and enabling the effects that way?

---

### Post by ellalan on 2009-03-05
Try to install simple-ccsm in synaptics and it might solve your problem. There are new drivers for nvidia and you could try them as well.

---

### Post by LeonBlade on 2009-03-08
> **Therion said:**
> Which driver though?  Are you sure you have the nVidia Restricted Driver installed and running?  You've checked?

If so, what happens when you try to enable desktop effects?  Do you have the option available and nothing happens, is it greyed out, what?

Have you tried installing **compizconfig-settings-manager** via Synaptic and enabling the effects that way?

Alright, I downloaded Compiz and as soon as I did I tried to use it and got the error.
[IMG]http://i20.photobucket.com/albums/b213/LeonandMyMom/desktopeffectsproblem.png[/IMG]

After having to reinstall Ubuntu, don't ask, the driver isn't coming up at all...

Anyone know how I can get this working?

Thanks,
LeonBlade

---

### Post by zeldarocks on 2009-03-08
I'm having this exact same problem, the effects won't enable

---

### Post by StaticIp on 2009-03-14
I have another problem, I got the driver enabled (dont ask it just worked) and whenever its enabled the desktop effects work but some programs, amarok, wine and openoffice just to name a few are screwing up. I cant see anything in the settings boxes in any of them. The window looks blank, any suggestions?

---

### Post by prariedogn on 2009-03-16
Good morning all, I have a problem with my distro's desktop. I am using dual NVidia XFX 250 mb 8600 graphics cards. I attempted to enable desktop effects after installing Ubuntu 8.10. I downloaded the recommended NVidia driver, but now when I attempt to boot into the OS, I get what looks like a command line screen. Does anyone have any thoughts on what to do? I cannot get into my desktop at all. Many Thanks, hope someone can help.

---

### Post by mhgsys on 2009-03-16
> **prariedogn said:**
> Good morning all, I have a problem with my distro's desktop. I am using dual NVidia XFX 250 mb 8600 graphics cards. I attempted to enable desktop effects after installing Ubuntu 8.10. I downloaded the recommended NVidia driver, but now when I attempt to boot into the OS, I get what looks like a command line screen. Does anyone have any thoughts on what to do? I cannot get into my desktop at all. Many Thanks, hope someone can help.

in recovery modes:


you might want to backup the original xorg.conf so you can easily compare the 2 so you can put back some settings (like video drivers etc)

```

sudo nano /etc/X11/xorg.conf

```

and save it like xorgbackup.conf or something like that.

then

```

sudo dpkg-reconfigure xserver-xorg

```
to reset xorg.conf

then reboot or start gdm again with
```

sudo /etc/init.d/gdm restart

```

---

