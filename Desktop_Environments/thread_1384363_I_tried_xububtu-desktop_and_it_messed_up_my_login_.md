---
title: "I tried xububtu-desktop and it messed up my login splash screens"
date: 2010-01-18
forum: Desktop Environments
---

### Post by ClintSwiney on 2010-01-18
Hi everyone,

This may be a no brainer but I was fiddling and thought I'd try XCFE. I found an easy way to do this in Karmic 64 bit with a quick Google search:

```

apt-get install xubuntu-desktop
```

So I did it blindly thinking "cool I can check XCFE out without having to reinstall"

It did what it was supposed to and installed it as an option on the login screen, but it also changed the login splash screen and the boot up splash screens. I like the animated atom Xububtu thing just fine but I'm not running Xubuntu! So I have been trying to change the splash screens back to the standard Ubuntu Karmic screens without success.

I tried to remove the xubuntu-desktop package

```
apt-get remove xubuntu-desktop

```

and

```
apt-get purge xubuntu-desktop
```

But the splash screens are still Xubuntu!

So I tried reinstalling ubuntu-desktop

```
apt-get remove ubuntu-desktop
```

then

```
apt-get install ubuntu-desktop

```

No dice... At this point I am lost... Can anyone help or did I FUBAR my splash screens and login themes forever? 

BTW: This is not affecting my session once logged in, all is well, it's just the login theme and splash screens.

Thanks in advance for some help!

---

### Post by dje on 2010-01-18
Ok run:
```
sudo update-alternatives --config usplash-artwork.so
```
and follow the instructions to change the boot artwork, then run:
```
sudo update-initramfs -u
```

hope that helps,
dje

---

### Post by ClintSwiney on 2010-01-18
dje:  Thanks for the reply... However:

I did that and I get this:

> There are 2 choices for the alternative usplash-artwork.so (providing /usr/lib/usplash/usplash-artwork.so).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/usplash/usplash-theme-xubuntu.so  55        auto mode
* 1            /usr/lib/usplash/usplash-theme-ubuntu.so   10        manual mode
  2            /usr/lib/usplash/usplash-theme-xubuntu.so  55        manual mode

Press enter to keep the current choice[*], or type selection number: 1


So I entered 1 and ran the second command:

```
sudo update-initramfs -u
```

But it did not take???? The screens are still set to the Xubuntu theme for login and initial login animated splash.

Any other tricks up your sleeve?

Also is it OK to just delete the Themes in /usr/lib/usplash if I want to remove them from the system or is there a proper way to uninstall them?

---

### Post by VCoolio on 2010-01-18
For the login screen, try
sudo dpkg-reconfigure gdm

and choose gdm from the options. Or edit (sudo nano or gksudo gedit)
/etc/X11/default-display-manager 
and make sure it contains this one line: /usr/sbin/gdm .

---

### Post by ClintSwiney on 2010-01-18
Vcoolio:

Tried that and....

```

dpkg-reconfigure gdm
``` 

did not give me any options it just went to a blank line for about 20 seconds then back to the bash prompt.

I edited the default-display-manager mentioned and it already contained the line 

> /usr/sbin/gdm

Regardless the splash screens are all still set to the Xubuntu versions.

---

### Post by XubuRoxMySox on 2010-01-18
Seriously, if that's the only issue, why does it matter? I like the Xubuntu fireflies or whatever that way-kewl graphic thingy is... since it still boots into Gnome after the splash screen which is only displayed for a few seconds, I think if it were my 'puter I'd leave well enough alone.

If you are worried that the splash screen is a sign that something *else* may be messed up, you can use Synaptic and uninstall **usplash-theme-xubuntu** and make sure that **usplash** and **usplash-theme-ubuntu **are installed. It's safe to completely remove usplash.

-Robin

---

### Post by ClintSwiney on 2010-01-18
dixiedancer
> Seriously, if that's the only issue, why does it matter? I like the Xubuntu fireflies or whatever that way-kewl graphic thingy is... since it still boots into Gnome after the splash screen which is only displayed for a few seconds, I think if it were my 'puter I'd leave well enough alone.

Point taken. I understand but in the interest of learning new things about Linux and my incessant need to know how things work I simply want to know that I can do this. I find that if I pursue a little thing like this I end up learning something that could prove valuable in the future. It's how I'm teaching myself Linux. Although this is purely an Ubuntu issue it's still in the pursuit of something Linux and to that end I will run.

---

### Post by ClintSwiney on 2010-01-18
I found this:

> 
1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

It lets me change the background, fonts etc but the splash and "theme" are all still Xubuntu.

---

### Post by VCoolio on 2010-01-18
> **ClintSwiney said:**
> I found this:
It lets me change the background, fonts etc but the splash and "theme" are all still Xubuntu.

Ah, so you do have gdm, only a xubuntu theme in it? Try the following commands to modify gdm:

Background picture
current setting:
sudo -u gdm gconftool-2 --get /desktop/gnome/background/picture_filename
set new:
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /path/to/bg.jpg 

Gtk-theme
current setting:
sudo -u gdm gconftool-2 --get  /desktop/gnome/interface/gtk_theme 
set new (from /usr/share/themes ):
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/interface/gtk_theme Redmond 

Icon theme
current setting:
sudo -u gdm gconftool-2 --get /desktop/gnome/interface/icon_theme 
set new (from /usr/share/icons ):
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/interface/icon_theme Tangerine

---

### Post by ClintSwiney on 2010-01-18
Ya I got that.. I can change those elements but I want to change the Splash Screen...


This is Karmic Ubuntu 9.10... I think something is different about the splash system in Karmic, Don't know if changes are possible. But I have a suspicion that they are because xubuntu-desktop changed it! I just want to change it back to Ubuntu!

---

### Post by ClintSwiney on 2010-01-18
Update:


I may have solved my own problem....

There does not appear to be one way to make changes to the Splash screen settings in Karmic. It's a combination of things. 

1. The background and appearance can be changed by using any of the methods above
2. To change the Splash screen you have to replace the files located here:

```
/usr/share/images/xsplash
```

I found an archive on the web that had the default files in it and replaced all of the files in this folder with the files in the archive and the Splash screen was back to the default.

I have attached the file that contains the original artwork to this post.
I also found this which is very helpful:

[http://ubuntuforums.org/showthread.php?t=1333683]("http://ubuntuforums.org/showthread.php?t=1333683")

There may be a better way but this works.

---

