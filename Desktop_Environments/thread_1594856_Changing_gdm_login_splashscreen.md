---
title: "Changing gdm login splashscreen"
date: 2010-10-12
forum: Desktop Environments
---

### Post by Alex22 on 2010-10-12
Hello Guys, I don't like the username/password default screen, but i like the ones in /usr/share/backgrounds.

I've been trying to change it for few hours. None of the advices on The Net work.

I tried:

1) gconf-editor and /apps/gnome-session/options/splash_image
gconf-editor /schemas/apps/gnome-session/options/splash_image

I set it to picture file path, or splash/filename.png or even copied the desired picture to /usr/share/pixmaps/splash/ubuntu-splash.png - no changes

2) gdmsetup has no such option for me 
3) also installed startupmanager - nothing as well.

No changes - purple sh.t wins so far!

It can be easily changed in Lubuntu's lxdm, but not here...

Please help

---

### Post by guildofghostwriters on 2010-10-13
You might have seen it already but in case you haven't, searching for a way to do what you're trying to do threw up this thread: [http://ubuntuforums.org/showthread.php?t=1594955&highlight=change+gdm](http://ubuntuforums.org/showthread.php?t=1594955&highlight=change+gdm)

---

### Post by Alex22 on 2010-10-13
Thanks, guildofghostwriters, i haven't seen that before.
This helped me: :)


> **Ctrl-Alt-F1 said:**
> Alternative method for those that don't want to install a program:  The ubuntu background wallpaper is in /usr/share/backgrounds/warty-final-ubuntu.png.

Moving any file to that location will change the image.  I don't know if it has to be a .png or not but I always convert them to .png just in case.

---

