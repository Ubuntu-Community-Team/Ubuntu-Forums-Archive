---
title: "can't boot gutsy after kde 4.0 disaster"
date: 2008-01-13
forum: Desktop Environments
---

### Post by maya9 on 2008-01-13
Having a terrible time. Mayday!

Installed KDE 4 last night on top of Gutsy. When it came time to start things up, I got a half screen of snow, then a blue screen with an off center box saying "Welcome to Debian" and a log in. I tried logging in using every option (gnome, kde, kde 4.0) and it always took me to a flat blue screen with a terminal window.

So I restart in recovery mode to a command line, do sudo gdm, and get a ubuntu login screen with system options. I try the kde 4.0 and it runs, though VERY buggy. At this point I just want to get it OFF my system and get back to my lovely gutsy. Restart in similar manner and choose gnome and things are good (except I can't go online).

I then try various remove strategies,
sudo aptitude remove kubuntu-desktop
sudo apt-get remove kubuntu-desktop
going into synaptic and searching for kde files

Sorry, I don't know enough to know what I'm doing.
Anyway, restarting now takes me past the grub screen and then to a half screen of stripy zig-zag lines and then a BLANK BLACK screen and then nothing more. Just black. I have to hold the button down to get it to turn off.

 I can still reboot in recovery mode as I did before and it appears that KDE is gone--it isn't showing up in the login screen's options. What happened? How do I get a normal start up into gutsy?

KDE looked really cool and sexy but it did NOT work at all on my system.

Thanks!

---

### Post by TBerben on 2008-01-13
Removing kubuntu-desktop will not result in removing KDE 4 from your computer as kubuntu-desktop depends on the KDE 3 packages. To remove KDE 4 remove the KDE 4 ppa repository from /etc/apt/sources.list and run:
```
sudo aptitude remove kde4-core kdm-kde4
```

that should remove the KDE 4 core packages, to make sure you've got everything gone run:
```
aptitude search kde4
```

And make sure that none of the packages with 'kde4' in the name have an i in front of their names.

Then run:
```
sudo dpkg-reconfigure gdm
```

To give you the menu in which you can choose your session manager

---

### Post by maya9 on 2008-01-13
Thank you so much for replying!!!!

I did as you suggested and, indeed, was able to boot into Ubuntu without recovery mode.  Yeah!

However, the boot takes an incredibly long time now, includes a long period of black screen, and several moments of 3/4 snow/zig-zag lines, red dots at the top, and other screen madness.

Something is still not right, though I am thrilled that it is booting at all.  Booting in used to be extremely quick and painless with no craziness on the screen.

Do you know how to improve whatever is going on now?

Thank you again!

Maya

---

