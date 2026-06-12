---
title: "Stuck in login loop on Xubuntu 12.04"
date: 2013-05-06
forum: Desktop Environments
---

### Post by jgannon on 2013-05-06
I have a reasonably fresh install of Xubuntu 12.04 64-bit. Today when  I tried to log in via the graphical interface, it appears to accept my  password, then the screen flashes black, and I end up right back at the  login screen.
  I was able to google a few other people having this sort of problem,  but they mostly seem to be related to either being out of disk space  (I'm not), or having permissions issues on /tmp (I don't). I also tried  reinstalling xubuntu-default-settings, to no avail.
  There isn't anything suspicious in Xorg.0.log, but there are a lot of  errors and warnings in my .xsession-errors file. Again, I've tried  googling lots of these lines, but nothing I've seen seems to relate to  my issue. Here is the entirety of .xsession-errors:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0

(polkit-gnome-authentication-agent-1:22146): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:22146): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-OdeGXf/pkcs11: No such file or directory
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:22221): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:22221): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:22221): Indicator-Application-WARNING **: Unable to get application list: Operation was cancelled

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_double: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_DOUBLE)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_double: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_DOUBLE)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_double: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_DOUBLE)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(xfce4-indicator-plugin:22221): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:22221): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(polkit-gnome-authentication-agent-1:22146): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

blueman-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(nm-applet:22190): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


(update-notifier:22158): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```

Is any of this likely to be responsible, or do I need to keep digging? Thank you.

---

### Post by dentaku65 on 2013-05-06
Try to clean the files of Xfce of your user

```
mv $HOME/.config/xfce4 $HOME/.config/xfce4.SAVE
```
and, if I recall well in 12.04 also:
```
mv $HOME/.config/xfce4.session $HOME/.config/xfce4.session.SAVE
```
Reboot.

If you can get in, you can safe delete
```
rm -rf $HOME/.config/xfce4.SAVE
rm -rf $HOME/.config/xfce4.session.SAVE

```

---

### Post by jgannon on 2013-05-06
> **dentaku65 said:**
> Try to clean the files of Xfce of your user
Nope, no luck there. I had .config/xfce4, but no .config/xfce4.session. I moved it and rebooted, but I'm still seeing the same behavior. Interestingly enough, the xfce4 directory didn't get regenerated after I tried to log in again, which suggests to me that it's not even making it that far in the process before choking.

---

### Post by dentaku65 on 2013-05-07
Seems that your Xubuntu is not complete installed in some way; the fact that the under your $HOME the system do not re-create .xfce4 portion is an indication of incomplete or corrupted installation. Try to reinstall Xubuntu metapackages and its dependecies:
```
sudo apt-get install &#8211;reinstall xbuntu-desktop
sudo apt-get build-dep xbuntu-desktop
```

---

### Post by jgannon on 2013-05-07
> **dentaku65 said:**
> Seems that your Xubuntu is not complete installed in some way; the fact that the under your $HOME the system do not re-create .xfce4 portion is an indication of incomplete or corrupted installation. Try to reinstall Xubuntu metapackages and its dependecies
Nope, that didn't do it either. I was previously able to log in, so I don't think it's an issue of incompleteness. What's the next step?

---

### Post by dentaku65 on 2013-05-07
Sorry I did not understand if you tried to reinstall or not.
If not try it, if yes what happening launching this command?
```
startx
```

---

### Post by hil4vitkutin on 2013-05-07
Hi, would you post the content of your */var/log/messages.log* file? It might contain some useful information.
 
Sure there's nothing suspicious in* /var/log/Xorg.0.log*?

+ Can you log in as "Guest"? ;P

---

### Post by jgannon on 2013-05-08
> **dentaku65 said:**
> Sorry I did not understand if you tried to reinstall or not.
If not try it, if yes what happening launching this command?
```
startx
```
Yes, I reinstalled those packages, but it didn't fix anything. *startx* just complains that X is already running.
> **hil4vitkutin said:**
> Hi, would you post the content of your */var/log/messages.log* file? It might contain some useful information.
I don't have one of those. Were you looking for /var/log/dmesg, maybe?
> **hil4vitkutin said:**
> Sure there's nothing suspicious in* /var/log/Xorg.0.log*?
Yeah, it's unfortunately pretty boring.
> **hil4vitkutin said:**
> + Can you log in as "Guest"? ;P
Gahhh, can't believe I didn't try that sooner. Yes, the guest login works fine. That leads me to believe there's something broken in my home directory... what else is there to nuke other than ~/.config/xfce4?

---

### Post by hil4vitkutin on 2013-05-08
> **jgannon said:**
> -- That leads me to believe there's something broken in my home directory... what else is there to nuke other than ~/.config/xfce4?

Yes, I think this is pretty much the case.

You could try the following, but it is not very likely to fix your problem (I'm looking for better workarounds at the moment :P )
```


mv ~/.cache/xfce ~/.cache/xfce.back


```


EDIT:
I would recommend you to backup the files from your home folder (personal documents, some folders containing application configs in case you don't want to set up them all over again) and just create a new account when logged in as guest and delete the "corrupted" account. This way you would end up with at least a clean home folder.

If you end up with this solution, be sure to remember your old password, because I guess you'll still going to need it when executing tasks as root :D (or simply just use the same password as you did before).

---

### Post by steeldriver on 2013-05-08
have you checked the simple stuff?

```
ls -l ~/.Xauthority
```

---

### Post by jgannon on 2013-05-08
> **steeldriver said:**
> have you checked the simple stuff?

```
ls -l ~/.Xauthority
```
Well... that's embarassing.  ](*,) 

Yes, somehow root had taken ownership of my .Xauthority file. I have no idea how that would have happened, nor why that doesn't show up explicitly in .xsession-errors. In any case, thank you to steeldriver, hil4vitkutin, and dentaku65 for your help!

---

### Post by xjohnthomasx on 2013-06-20
> **jgannon said:**
> Well... that's embarassing.  ](*,) 

Yes, somehow root had taken ownership of my .Xauthority file. I have no idea how that would have happened, nor why that doesn't show up explicitly in .xsession-errors. In any case, thank you to steeldriver, hil4vitkutin, and dentaku65 for your help!


I'm having same issue - but root does NOT have ownership of .Xauthority! What else could one try?

---

### Post by Toz on 2013-06-20
After an unsuccessful login attempt, try going to the first tty (Ctrl+Alt+F1) and try logging into the console (text) session. If you get in (good news), try running the following commands:

1. To see if you've run out of disk space:
```
df -h
```
2. Check the end of this log file for any relevant information as to why the gui login failed:
```
cat $HOME/.xsession-errors
```

---

### Post by xubuntu84 on 2013-10-24
I realize this is a semi-old thread, but I wanted to post for completeness.  I had the same login loop issue after performing some random package upgrades, and google found this forum post.  My .Xauthority was still owned by me (not root), as well as the .ICEauthority.  Each time I tried to login, it changed .Xauthority from -rw-rw-r-- to -rw-----.  I did mv .Xauthority .Xauthority.bak, and the same with .ICEauthority, and tried to login in again, this time successfully.  Thanks for pointing me in the right direction, I just had to come about a fix a bit differently.

---

### Post by neutron68 on 2013-10-29
I just diagnosed and fixed this problem on a Mythbuntu 12.04 system.
[http://ubuntuforums.org/showthread.php?t=2183812](http://ubuntuforums.org/showthread.php?t=2183812)
From what I've deduced, this is a bug in lightdm.

I found that BOTH the owner and group of the .Xauthority file were changed to root.
I SSHed into the machine and changed the owner AND group to the username (as it is in a normally working system)

> cd /home/username
chown username:username .Xauthority

I wonder if you reset BOTH the owner and group of your .Xauthority to the username:
> ls -la /home/username

---

### Post by koskal on 2014-02-21
Thanks man. This was the solution for me.Thank you again.

---

### Post by koskal on 2014-02-21
> **benmctee said:**
> I realize this is a semi-old thread, but I wanted to post for completeness.  I had the same login loop issue after performing some random package upgrades, and google found this forum post.  My .Xauthority was still owned by me (not root), as well as the .ICEauthority.  Each time I tried to login, it changed .Xauthority from -rw-rw-r-- to -rw-----.  I did mv .Xauthority .Xauthority.bak, and the same with .ICEauthority, and tried to login in again, this time successfully.  Thanks for pointing me in the right direction, I just had to come about a fix a bit differently.

Thanks man.This was the solution for me.Thank you again

---

