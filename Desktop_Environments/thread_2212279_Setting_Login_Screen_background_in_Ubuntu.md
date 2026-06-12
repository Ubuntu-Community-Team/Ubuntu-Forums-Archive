---
title: "Setting Login Screen background in Ubuntu"
date: 2014-03-20
forum: Desktop Environments
---

### Post by foberle on 2014-03-20
Hi:

I'm using 64 bit Ubuntu 12.04 LTS with the standard Unity desktop, and I've set up a background screen using the normal Right-Click|Change Desktop Background. I've also done this using System Settings|Appearance, and using Ubuntu Tweak. This of course works the same with all these methods.

I tried setting a Log-In screen background using Ubuntu Tweak (Tweaks Tab > Startup | Login Settings > Click the button to change the login screen background). This sets the login screen settings for all users EXCEPT mine, which uses the same background screen as when I'm already logged in.

There is another button right below the one I just described which is marked "Set the same background as the current desktop background." I'm thinking that while experimenting I may have pressed that button and forced some override, and there is no command to unlink that. I've searched around but can't find any appropriate config file to edit and change/reverse that.

I've found many, many posts on many, many sites discussing how to set the screen backgrounds, but none of them seem to be appropriate for my system (i.e. they refer to config files that don't exist, etc). I've also attempted using a variety of third-party setup tools to do this, but can't find any appropriate settings in any of them.

I would like to have the login background screen setting completely independent of the desktop screen setting. Does anyone know how to do this? What config files to edit and where they are located, and so forth?

Also, I'm pretty sure the answer is "no," but is there any way to have different background screens for the various different workspaces available?

Thanks much for any advice or pointers.

---

### Post by steeldriver on 2014-03-20
can you post the output of these commands please?

```

sudo -u lightdm dbus-launch --exit-with-session gsettings get com.canonical.unity-greeter background

sudo -u lightdm dbus-launch --exit-with-session gsettings get com.canonical.unity-greeter draw-user-backgrounds

```

---

### Post by foberle on 2014-03-20
sudo -u lightdm dbus-launch --exit-with-session gsettings get com.canonical.unity-greeter background
GIVES:
No protocol specified
No protocol specified
'/home/foberle/Pictures/Rochester_Trimmed.png'

sudo -u lightdm dbus-launch --exit-with-session gsettings get com.canonical.unity-greeter draw-user-backgrounds
GIVES:
No protocol specified
No protocol specified
true

I'm guessing therefore I need to make that last entry false and add a file name, but where do I do that?

Thanks much for the response.

---

### Post by steeldriver on 2014-03-20
you can either do 'set *blah blah blah* whatever' or (probably easier in this case) just change 'get' to 'reset'

```

sudo -u lightdm dbus-launch --exit-with-session gsettings **reset **com.canonical.unity-greeter background

sudo -u lightdm dbus-launch --exit-with-session gsettings **set **com.canonical.unity-greeter draw-user-backgrounds **false**

```

If reset doesn't work for some reason, the default background should be '/usr/share/backgrounds/warty-final-ubuntu.png' I think

---

### Post by foberle on 2014-03-20
Where does one find this stuff? I did "man lightdm" and that had nothing  useful. /etc/lightdm/lightdm.conf had only a few lines, and so forth. I  feel dumb having to ask these questions, but I'm not sure what I would  even google to figure this out.

Any pointers?

And again - thanks for the speedy response.

---

### Post by foberle on 2014-03-20
SteelDriver:
I just logged out and back in again and can confirm that the reset command you gave me solved my problem. So thanks much, but I'm still interested in finding out where all those settings are stored. I promise not to mess with them. Really. I'm just curious.

---

### Post by mcduck on 2014-03-21
They are stored in GSettings/dconf, just like most of your other desktop and application settings are. However since it's the lightdm login screen the options are not in *your user's * gsettings but the *lightdm* user's instead.

For performance reasons dconf keys are stored in a binary database file, so you won't find them in any of the hidden text config files in your home.

---

### Post by steeldriver on 2014-03-21
As mcduck says, the extra 'woo' is only necessary because those particular settings belong to lightdm not the the regular user account. For *your own* settings you can install the graphical dconf editor (the containing package is called **dconf-tools** I think) and then browse to your heart's content. There is a 'reset' button so it's hard to do too much damage ;)

If you are happier with the command-line, then one thing I find useful dumping out ALL the settings and using grep to see if there's anything that sounds like what I want to change. For example to find how I might go about changing the number of workspaces:

```

$ gsettings list-recursively | grep workspaces
org.gnome.shell.overrides dynamic-workspaces true
org.gnome.shell.overrides workspaces-only-on-primary true
org.gnome.desktop.wm.preferences num-workspaces 4
org.gnome.desktop.wm.keybindings toggle-on-all-workspaces @as []
org.gnome.mutter dynamic-workspaces false
org.gnome.mutter workspaces-only-on-primary false

```

---

### Post by foberle on 2014-03-21
mcduck and steeldriver:

Thanks - now I'm like a kid on Christmas morning, and can't wait to  (likely) toast my system playing with all these things I didn't know  were there.

I really appreciate the responses. By the way, is  mutter "org.gnome.mutter" the German word for Mother, or is is it a verb  for something?

Frank

---

### Post by mcduck on 2014-03-24
> **foberle said:**
>  By the way, is  mutter "org.gnome.mutter" the German word for Mother, or is is it a verb  for something?

According to the project page: "Mutter (a contraction of "Metacity Clutter")", which makes sense since it's a replacement to Gnome's old window manager Metacity, using Clutter graphics library...

---

