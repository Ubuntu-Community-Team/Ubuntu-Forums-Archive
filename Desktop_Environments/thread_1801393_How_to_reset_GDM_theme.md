---
title: "How to reset GDM theme"
date: 2011-07-10
forum: Desktop Environments
---

### Post by Luke.Hoersten on 2011-07-10
How do I reset my GDM theme to the default. I've had this install for a while and customized it at some point. I'd just like to reset it.

---

### Post by Luke.Hoersten on 2011-07-13
bump

---

### Post by DoubleClicker on 2011-07-14
Logout of your current session and return to the GDM
 Switch to the tty command line prompt using Ctrl-Alt-F1
Login using your normal login/password
at the command line prompt type: export DISPLAY=:0.0
then type: sudo -u gdm gnome-appearance-properties
 Switch back to the gdm screen using Ctrl+ALT+F7 (sometimes it's Ctrl+ALT+F8 )
 In appearances you can change your GDM&#8217;s font, theme and background image.

---

### Post by Luke.Hoersten on 2011-07-14
Failed with:

> GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Detailsl - 1: Failed to get connection to session: Error connecting: Connection refused)

---

### Post by Krytarik on 2011-07-14
To simply reset the settings of GDM's appearance, you can run commands like this, to 'unset' the concerning Gconf keys:
```
sudo -u gdm gconftool-2 --unset /desktop/gnome/interface/gtk_theme
```
These are the involved keys:

[LIST]
[*]GTK theme -> "/desktop/gnome/interface/gtk_theme"
[*]colors -> "/desktop/gnome/interface/gtk_color_scheme"
[*]window borders -> "/apps/metacity/general/theme"
[*]window button order -> "/apps/metacity/general/button_layout"
[*]background image -> "/desktop/gnome/background/picture_filename" and other associated ones
[*]icon theme -> "/desktop/gnome/interface/icon_theme"
[/LIST]
Obviously, some of them you won't usually see having an effect on the appearance of GDM, specifically the window borders/buttons.

If you want to set them to different ones again, please see this guide:
[http://ubuntu4beginners.blogspot.com/2011/05/customize-gdm-plymouth-grub2.html](http://ubuntu4beginners.blogspot.com/2011/05/customize-gdm-plymouth-grub2.html)

Greetings.

---

### Post by Luke.Hoersten on 2011-07-20
That didn't seem to do it. I reset the theme with no luck =/

---

### Post by Krytarik on 2011-07-20
> **Luke.Hoersten said:**
> That didn't seem to do it. I reset the theme with no luck =/
Are you actually meaning the theme of the login screen, thus GDM, or your own theme, when logged in to the desktop?

If the latter, the commands would be like this:
```
gconftool-2 --unset /desktop/gnome/interface/gtk_theme
```
After running them, better relogin.

---

### Post by Luke.Hoersten on 2011-07-20
Yeah I'm actually talking about the login, GDM screen. I must have set it with some tool a while ago (I remember the "Login Screen Settings" having a theme option) and now the Ubuntu preferences don't support changing it anymore so it's stuck as the 10.04 version or something.

---

### Post by Krytarik on 2011-07-20
Obviously, it would help to know what exactly is different from the default, and what you expect to revert!?

But please check with the method described in the guide I linked to what is currently selected as all those various Appearance options.

And, it can also be that the method you used created directories in GDM's profile which are overriding the directories in "/usr/share/icons" and/or "/usr/share/themes", though the latter is rather uncommon, if done at all.

To delete any possibly created directories, run these commands:
```
sudo rm -rf /var/lib/gdm/.icons
sudo rm -rf /var/lib/gdm/.themes
```

---

### Post by Luke.Hoersten on 2011-07-20
> **Krytarik said:**
> Obviously, it would help to know what exactly is different from the default, and what you expect to revert!?

Like I said, the GDM theme is from [9.04]("http://www.linuxnewbieguide.org/userfiles/xsplash-3.png") and not the [11.04]("http://3.bp.blogspot.com/-78xX5VAI7dM/Tbz9Q46V0gI/AAAAAAAAAvo/nmqtKl7MsAE/s1600/Screenshot.png") login screen.

I think because I update to the RCs before the official Ubuntu releases, it doesn't actually update my gdm login theme.

I just want to run whatever Ubuntu runs on an update to refresh the login screen.

Examples:

[IMG]http://www.linuxnewbieguide.org/userfiles/xsplash-3.png[/IMG]
[IMG]http://3.bp.blogspot.com/-78xX5VAI7dM/Tbz9Q46V0gI/AAAAAAAAAvo/nmqtKl7MsAE/s1600/Screenshot.png[/IMG]

---

### Post by Krytarik on 2011-07-20
So, you are finally mixing:

[LIST]
[*]Ubuntu versions -as stated- 9.04, 10.04, 11.04
[*]XSplash boot screen from Ubuntu 9.10
[*]GDM login screen
[*]installed packages -which would be definitely upgraded-
[*]and -which is suspectedly the culprit- settings/profile
[/LIST]
So, please follow my suggestions in my previous post, at first.

---

### Post by Luke.Hoersten on 2011-07-20
I'm sorry I didn't follow your last post. Can you clarify?

Also, I've tried all your suggestions thus far with no luck.

Thanks, Luke

---

