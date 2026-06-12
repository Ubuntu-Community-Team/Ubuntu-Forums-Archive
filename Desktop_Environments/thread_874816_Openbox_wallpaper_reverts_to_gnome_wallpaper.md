---
title: "Openbox wallpaper reverts to gnome wallpaper"
date: 2008-07-30
forum: Desktop Environments
---

### Post by triphazard on 2008-07-30
Hi folks,

I've recently updated to Hardy from Feisty and am an Openbox user.  My home directory is stored on a separate drive and is mounted in fstab so things like .config etc are exactly the same as they were before the upgrade meaning, for the most part, my Openbox setup remains identical to how it was before.

When I log in to Openbox the wallpaper is as it should be until I open an application...this can be Firefox, Audacious, whatever.  Upon doing this the wallpaper instantly switches to whatever wallpaper is set in gnome!  I can change it back easily enough (I use feh) and from there on in it remains as it should be until I log out and back in again.

This isn't a major problem and I know I can change the gnome wallpaper to match the openbox one but I'd rather get to the bottom of this and find out what the heck is going on  :)

Thanks in advance for any help.

---

### Post by triphazard on 2008-07-31
Anybody?  (bump)

---

### Post by urukrama on 2008-07-31
Do you use gnome-settings-daemon? It now also sets the wallpaper.

---

### Post by andrewjoy on 2008-08-01
If you do not use any of the other functions of the gnome-settings-daemon then you can slop openbox form loading it, then it will not be able to change the wallpaper.

WARNING! 

Do NOT remove the following lines instead comment them out so just incase you need to change it back you can do.

Navigate to 

```
/etc/xdg/openbox
```

with sudo rights and open the file "autostar.sh"

and change 

```

# Make GTK apps look and behave how they were set up in the gnome config tools
if which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
fi
```

to 

```

# Make GTK apps look and behave how they were set up in the gnome config #tools
#if which gnome-settings-daemon >/dev/null; then
#  gnome-settings-daemon &
#fi
```


this will stop the gnome-settings-daemon form loading

A good replacement for the gnome file manager is PCmanFM i am currently using this file manager with openbox ( running on Ubuntu 8.04 x64)and i am finding it a vv fast simple and efficient little file manager, currently with the above edit to the openbox autostart.sh it will pop up a message about the icon themas not being set i am currently looking for a workaround for this.

EDIT: Dont forget that without the gnome-settings-daemon usb stuff wont automount i am also currently looking for another way to automount usb/firewaire devices so i can turn the gnome-settings-daemon off again as i dont like to use the console just for stuff like that

---

### Post by urukrama on 2008-08-02
> **andrewjoy said:**
> WARNING! 

Do NOT remove the following lines instead comment them out so just incase you need to change it back you can do.

It is easier and better to copy that file to your home directory (~/.config/openbox) and make the necessary changes in that file.

To mount things you can use thunar-volman with Thunar or ivman.

---

### Post by DocYoung on 2008-08-03
From a limited user, it seems to me that the two biggest pains while in fluxbox or openbox, are gnome-settings-daemon and nautilus.

nautilus Is an easy fix with -no--destop.

gnome-settings is another story, and alot of work.

---

### Post by sayakb on 2008-08-03
Try setting the wallpaper using feh: [http://kmandla.wordpress.com/2007/04/28/browse-and-set-wallpaper-in-openbox-with-feh/](http://kmandla.wordpress.com/2007/04/28/browse-and-set-wallpaper-in-openbox-with-feh/)

---

### Post by andrewjoy on 2008-08-03
The gnome-settings-daemon wallpaper function overrides feh.

urukrama you are a lifesaver thank you. Ivman is exactly what i am looking for, i could even remove gnome now and the unused apps and go for a oubuntu type of distro with openbox as the main fount end

---

### Post by wilhelmtell on 2008-08-08
Try gconf-editor.

/apps/gnome_settings_daemon/plugins/background

Set "active" to false.

---

### Post by Merijn on 2008-10-03
> **wilhelmtell said:**
> Try gconf-editor.

/apps/gnome_settings_daemon/plugins/background

Set "active" to false.

This works best for me. Thank you.
because I don't want to replace all mount and other programs only for a wallpaper problem.

---

### Post by MedellinManDem on 2009-02-18
> **andrewjoy said:**
> If you do not use any of the other functions of the gnome-settings-daemon then you can slop openbox form loading it, then it will not be able to change the wallpaper.

WARNING! 

Do NOT remove the following lines instead comment them out so just incase you need to change it back you can do.

Navigate to 

```
/etc/xdg/openbox
```

with sudo rights and open the file "autostar.sh"

and change 

```

# Make GTK apps look and behave how they were set up in the gnome config tools
if which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
fi
```

to 

```

# Make GTK apps look and behave how they were set up in the gnome config #tools
#if which gnome-settings-daemon >/dev/null; then
#  gnome-settings-daemon &
#fi
```



Mine looked like this but with an added line which (I think) said make it look like XFCE if the gnome test doesn't work.

Anyway, I commented them both...and now I cannot get into Ubuntu at all. I just get a black screen. 

Can anyone help?

---

### Post by box_open on 2009-05-10
Go back to normal (you might have to choose a gnome-session from your start screen option dialog) and just do the following command of "urukrama" from a terminal:
gconftool-2 --set /apps/gnome_settings_daemon/plugins/background/active --type bool False
Restart your openbox session and all should be OK. For more information check out "urukrama" great site:
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Good luck

---

