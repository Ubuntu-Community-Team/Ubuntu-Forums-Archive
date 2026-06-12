---
title: "Dpkg-reconfigure tools in Debian"
date: 2008-05-28
forum: Debian
---

### Post by 67GTA on 2008-05-28
Is the ```
dpkg-reconfigure xserver-xorg
``` command still in Debian Sid? I was just curious, because it was taken out in Ubuntu Hardy.

---

### Post by kerry_s on 2008-05-28
not sure about sid, but it's still in lenny.

---

### Post by 67GTA on 2008-05-28
Cool. I'm trying to figure out when it left, and who removed it. I think Debian removed it to work with the new Xorg hot plugging feature. It uses dbus, hal, and randr to set this info now. I am trying to find suitable workarounds for when hot plugging does not work.

---

### Post by kerry_s on 2008-05-28
it's the 2.6.2* kernel, i use the etch 2.6.18 kernel and it works fine, moving up to 2.6.2* kernels a lot of stuff breaks, for me it's every thing from hotplug to sound, it's not a software issue. i don't even use dbus or hal, there not installed.

---

### Post by 67GTA on 2008-05-28
I have actually been annoying a couple of the Debian devs via IRC about this. The old dpkg tools were made obsolete by the newest xorg. The traditional xorg.conf is almost useless now, except for maybe res modelines. You can actually delete the xorg.conf file and the system will never know it. 

PS
No dbus or hal !!! How do you live? :lolflag:

---

### Post by kerry_s on 2008-05-28
lol, my stuff works just fine.

---

### Post by Raven_Oscar on 2008-05-29
Well in testing dpkg-reconfigure <name of the package> is still working. As far as in sid. 
In case of xserver-xorg it works a little bit strange for me. But it seems to be connected with xorg only.

---

### Post by maybeway36 on 2008-05-30
dpkg-reconfigure xserver-xorg is the same in Hardy and Lenny/Sid. I had to write my xorg.conf manually to get 1280x1024 to work, but it's a one-time deal.

---

### Post by p_quarles on 2008-05-31
> **maybeway36 said:**
> dpkg-reconfigure xserver-xorg is the same in Hardy and Lenny/Sid. I had to write my xorg.conf manually to get 1280x1024 to work, but it's a one-time deal.
Yeah, you can't "remove"
```
dpkg-reconfigure xserver-xorg
```
without upending dpkg itself, which is the very basis for Ubuntu's package management system. All the latest Debians and any derivatives worth the name can run that command.

---

### Post by 67GTA on 2008-05-31
The command is still there, but it won't configure gfx card/monitor. It only asks about using framebuffer, and keyboard. The rest has been disabled.

---

### Post by p_quarles on 2008-05-31
> **67GTA said:**
> The command is still there, but it won't configure gfx card/monitor. It only asks about using framebuffer, and keyboard. The rest has been disabled.
Perhaps the default priority was changed? Try:
```
# dpkg-reconfigure plow xserver-xorg
```

---

### Post by JeffElkins on 2008-05-31
> **p_quarles said:**
> Perhaps the default priority was changed? Try:
```
# dpkg-reconfigure plow xserver-xorg
```

That 'plow' doesn't work for me...8.04 doesn't seem to recognize it. This change blows for me. I'm setting 8.04 up on a HTPC and the 60" LCD/Mac mini combo requires special modelines and the intel video drivers. I'm currently stuck with 1024x768.

---

### Post by 67GTA on 2008-05-31
It just says plow isn't installed. Is this something Debian specific? I know for a fact that the dpkg-reconfigure xserver-xorg command has been depreciated in Hardy due to the new auto configuration. It is no longer an option. You can even delete xorg.conf and boot without it now. If your hardware isn't correctly detected by dbus, hal, and xrandr, you are left with manually editing xorg.conf.

---

### Post by JeffElkins on 2008-05-31
> **67GTA said:**
> It just says plow isn't installed. Is this something Debian specific? I know for a fact that the dpkg-reconfigure xserver-xorg command has been depreciated in Hardy due to the new auto configuration. It is no longer an option. You can even delete xorg.conf and boot without it now. If your hardware isn't correctly detected by dbus, hal, and xrandr, you are left with manually editing xorg.conf.

apt-get install plow fails as well, with all repositories enabled. Anyway I tried dpkg-reconfigure --priority= and that had no effect. As far as editing xorg.conf manually, that doesn't work either. I replaced xorg.conf with a working conf with modelines and drivers specified, and it was ignored. Perhaps there's a way to force it, but I don't know what it is.

Back to 7.10 for this box. You don't take away the HTPC from an angry wife :)

---

### Post by p_quarles on 2008-05-31
"plow" is an argument for dpkg-reconfigure, not a separate package. If the argument doesn't work, the alternate syntax would be:
```
# dpkg-reconfigure --priority=low xserver-xorg
```

---

### Post by 67GTA on 2008-05-31
That still starts at the framebuffer option. It has been intentionally disabled to skip the gfx/monitor setup.

---

### Post by FSHero on 2008-06-07
[QUOTE=67GTA]The command is still there, but it won't configure gfx card/monitor. It only asks about using framebuffer, and keyboard. The rest has been disabled.[/QUOTE]

Damn... this is so annoying. dpkg-reconfigure xserver-xorg was a beautiful way to add resolutions, in my opinion! I miss Feisty now...

---

### Post by 67GTA on 2008-06-07
You can use xrandr to change the res/refresh rates. Just be sure your monitor/hardware supports them, or you will be greeted with the "Ubuntu is running in low graphics mode" at the next boot. Try xrandr -help in a terminal to see the arguments.

---

### Post by fudoki on 2008-06-26
> **67GTA said:**
> You can use xrandr to change the res/refresh rates. Just be sure your monitor/hardware supports them, or you will be greeted with the "Ubuntu is running in low graphics mode" at the next boot. Try xrandr -help in a terminal to see the arguments.

As a user of *nix since the early '80's I am reminded of a strange concept that seems to have gone out of style called DOCUMENTATION.  If folks are going to arbitrarily change the way things have worked for several years THEY MIGHT HAVE THE COURTESY TO TELL FOLKS OUT LOUD AND UP FRONT.

This situation is like trying to get answers about Winblows, and the move toward double secret, undisclosed, undocumented, "automatic" configurations THAT DON'T WORK AT ALL is a bad move.

This will make the third machine I have had a failed "upgrade" (it's not an upgrade if your machine is turned into a boat anchor by the process) and need to just re-install.

I AM RE-INSTALLING DEBIAN AND IT IS WORKING WELL.

Sadly, six of my clients have chosen to re-install Windows and find other sources of support than me thanks to the "Upgrade Now" button beckoning them to fly into the trees and get a broken computer.

THANKS UBUNTU!

Dr. W. T. Wilkinson

---

### Post by stream303 on 2008-06-28
Assuming you can get to some sort of usable screen temporarily, this trick might help by bringing back the old "screens and graphics" utility that is deprecated in Gnome (afaik)

You reenable it in the Gnome menu (Preferences > Main Menu) , and in the left-hand pane, highlight "Other".  Check "Screens and Graphics".

Now you should be able to bring up the older configuration utility that appears in Gnome's main menu, that will allow you to change your driver, resolution, etc like in the good old days. :)

YMMV.

---

