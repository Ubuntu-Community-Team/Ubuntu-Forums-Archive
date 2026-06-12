---
title: "Problem changing desktop wallpaper in Ubuntu/GNOME"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by wirawan0 on 2007-08-16
I might have stumbled at another bug of Ubuntu here, but before posting a bug report, let me ask you (other fellow users). I use Ubuntu 7.04 here, on a Pentium M laptop (Dell Inspiron 600m).

When I tried to change wallpaper via desktop right click, it opened the window titled "Desktop Background Preferences" (program name: gnome-background-properties). But when I choose any of the wallpapers shown there (or an additional one as added by me), the desktop would not change. Puzzling. On some occasion the wallpaper was updated properly, but on another, it was not. Let me tell you how I used this laptop. I typically don't boot up every time; rather, I use the "suspend to RAM" feature, which thank to many people's labor, has worked quite flawlessly on my laptop. I suspect that the problem has something to do with this, somehow.

Here are several diagnostic tests that I made:

* If I change the desktop background using gconftool-2 (see, e.g. [http://ubuntuforums.org/showthread.php?t=289248](http://ubuntuforums.org/showthread.php?t=289248) ), then the wallpaper would be updated immediately. So it's not the problem with gconf or the wallpaper itself.

* Then I watch the /desktop/gnome/background section of the "registry" via gconf-editor. I noted that the change done via gnome-background-properties was not reflected in the gnome "registry". The "picture_filename" entry is not changed when we choose a different picture via  gnome-background-properties above. Weird.

* BUT, if I start the  gnome-background-properties from command line (from gnome terminal or xterm), then the wallpaper is updated as soon as I choose a different picture.

* BUT (again!) if I start the  gnome-background-properties via "Run Applications" (a shortcut of GNOME desktop that I mapped to Winkey+R), then the wallpaper fails to update again.

So what's wrong here? This is so weird. Has anyone experienced a similar problem?

Thanks,
Wirawan

---

