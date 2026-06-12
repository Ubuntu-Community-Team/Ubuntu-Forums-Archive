---
title: "Boot directly to tty1 after removing KDE desktop"
date: 2020-02-14
forum: Desktop Environments
---

### Post by andreberg on 2020-02-14
I installed Ubuntu 18.04 a few months ago and started trying it out. A while ago I decided to try out the KDE desktop environment (plasma).

Now, here's my fault. I can't remember how I installed it. What I do remember is that I tried to install only the Plasma Desktop environment, not the full KDE suit. I did get however a lot of additional applications from KDE (Konsole, Kscan, and so on). It was annoying in the beginning but I learned to live with it as I could try out other applications like Dolphin file manager.

One feature I love from Gnome (GDM3) is Night Light so I was quite frustrated after finding out that Plasma for Ubuntu 18.04 does not have the feature and that there was no way to upgrade from Plasma 5.12 to 5.6 which supposedly does have the feature enabled. Also, I found that sometimes some applications would open Dolphin and other would default to Nautilus. As well, when booting up the PC, the splash screen showed Kubuntu instead of Ubuntu. I did not give much thought to this at all at the moment, but now believe it might shed some light on my issue.

In the end I decided to purge the KDE desktop and stick with GDM3. As I didn't quite remember how I installed KDE -although I do remember it was through terminal and I did not use taskel- I browsed the net searching for a way to uninstall. I decided to go with what seemed proper
```
sudo apt uninstall kde-desktop
```
It did work and got rid of most of the files. I had to manually remove some applications (e.g. Konsole), and finished up with
```
sudo apt autoremove
```
Got a squiky clean system, or so I thought.

Rebooted and lo and behold, the Kubuntu splash screen still appears after grub (this is a dual boot system) and ends up sending me to tty1. My system was way too squiky clean!

I found a way to get back to the Gnome desktop environment after trying various solutions, namely, CTRL+Alt+F7 and CTRL+ALT+Fn+F7 (which did not work, although I could move from ttys 1 through 6), reinstalling gnome-desktop, ubuntu-desktop, gnome-session and finally sending
```
sudo /etc/init.d/gdm3 restart
```
which got me back to the GDM3 login splash.

However, I must type this command everytime I boot up the system.

The last thing i checked was this post
[https://ubuntuforums.org/showthread.php?t=2390296](https://ubuntuforums.org/showthread.php?t=2390296)

I found out that my /etc/systemd/system/display-manager.service was symlinked to /lib/systemd/system/sddm.service which is a non-existent file. I broke the link and established a new one to /lib/systemd/system/gdm3.service which does exist, but to no avail.

The default display manager in /etc/X11/default-display-manager is /usr/sbin/gdm3.

I know my issue has something to do with the Kubuntu splash screen at boot, but my Linux knowledge is not that deep.

Thanks for the help!

---

### Post by CatKiller on 2020-02-14
You seem to have broken things quite thoroughly in your attempts to fix them.

There are a lot of things - like the Plymouth theme, or the display manager - where you can have several installed but can't actually use more than one at a time. You choose which one of those alternatives you wish to use with the *alternatives* system; you just need to run update-alternatives for whichever thing it is that you want to use. That creates the symlinks and updates config files and so on. 

You could, strictly speaking, go through each of the things that are now broken and update the alternatives, and reinstall/uninstall packages to make that possible, but - realistically - a reinstall takes maybe 20 minutes.

---

### Post by andreberg on 2020-02-15
Thanks for the answer CatKiller.

I'm trying to salvage my personal configs as much as possible. As well, the original installation took me quite a bit to get working due to the specifics of my laptop's BIOS/UEFI settings.

Where can I find a list of the things I should be looking into to fix? Would that be too extensive? Or is there a way to salvage my personal configs during a total reinstall of the OS?

Thanks

---

### Post by CatKiller on 2020-02-15
> **andreberg said:**
> Where can I find a list of the things I should be looking into to fix? Would that be too extensive? 

For the two things you've mentioned, ```
sudo dpkg-reconfigure gdm3
``` should rerun the install scripts for GDM to get that back in good shape. 

```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
``` should change which Plymouth theme you're using. 

I don't know what state everything else might be in. 

> Or is there a way to salvage my personal configs during a total reinstall of the OS?

That depends on how you set it up in the first place. All your personal configs are in /home. If you made that a separate partition then reinstalling without formatting that partition will mean that you have the same settings after a reinstall. Otherwise you could create a new partition now, transfer your /home to that partition, and then reinstall, to have the same outcome. Or backup your /home somewhere, reinstall, then restore /home from your backup.

---

### Post by andreberg on 2020-02-15
Thanks. I did create a separate partition for /home during install, so that´s taken care of.

Will try first your other recommendations. If it still does not work, then I´ll go for the re-install option.

Thanks
---------------------
EDIT

i ran the commands suggested and finally everything seems to be working OK, perhaps a bit slower than originally. Will give a thought over night on reinstalling the system once I'm back home with a fast internet connection.

Thanks for your quick response and guidance.

---

### Post by CatKiller on 2020-02-15
> **andreberg said:**
> i ran the commands suggested and finally everything seems to be working OK, perhaps a bit slower than originally. Will give a thought over night on reinstalling the system once I'm back home with a fast internet connection.

Thanks for your quick response and guidance.

No problem. 

20.04, the next Long Term Support release, will be released in April. If everything's working OK you can do a fresh install (rather than an upgrade) then for peace of mind that there aren't any misconfigurations hanging around.

---

### Post by andreberg on 2020-02-15
That's a pretty good idea, in fact. I'll hang on in here and wait for the 20.04 LTS release.

---

### Post by CatKiller on 2020-02-15
When you do your fresh install, it might be worth trying out both Gnome and KDE (and any of the other [Ubuntu flavours](https://ubuntu.com/download/flavours) that take your interest) first, from a live USB. I personally find KDE *much* nicer to use than Gnome, and the things that you didn't like about it seem to be largely from having both desktop environments installed at the same time - which can get messy - as well as missing a feature that's in later versions of Plasma/KDE than the one that came with 18.04. Just a thought.

---

