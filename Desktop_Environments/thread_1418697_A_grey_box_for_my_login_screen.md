---
title: "A grey box for my login screen"
date: 2010-02-28
forum: Desktop Environments
---

### Post by dennymathews on 2010-02-28
Check out: [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html"). The login screen that I want or that I originally had is the first pic on that post. My problem is that instead of the black background for the user logins, I have a grey background with a Computer logo instead of the ubuntu logo.

I already tried changing it using:
System->Preferences->Login screen setting

Following the above post, I thought that I could be able to change the GDM config screen to fit the old types, so I followed the instructions. Unfortunately, I got a few errors and I wasn't able to change the background. Here are the errors that I received: (within quotes)
```
"** (gnome-control-center:19640): WARNING **:
error raised: [libslab_get_gconf_value: error getting /desktop/gnome/applications/main-menu/lock-down/user_modifiable_apps]

** (gnome-control-center:19640): WARNING **:
error raised: [load_xbel_store: couldn't load bookmark file [NULL]

** (gnome-control-center:19640): WARNING **: get_actions_list() - PROBLEM - Can't load gtk-theme-selector.desktop

** (gnome-control-center:19640): WARNING **: get_actions_list() - PROBLEM - Can't load gnome-cups-manager.desktop"
```

Then the cursor just blinks. I don't see a prompt or anything. When I press <Alt> + <F7>, the "Login Screen" settings are still the same.

I only have a Linux installation on my desktop.  So, there is no dual boot with Windows.  It's just Ubuntu 9.10 installation.  The following is what I retrieved from using a session through LiveCD.
```
 sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a227a22

   Device Boot Start End Blocks Id System
/dev/sda1 * 1 23971 192547026 83 Linux
/dev/sda2 23972 24321 2811375 5 Extended
/dev/sda5 23972 24321 2811343+ 82 Linux swap / Solaris
```

Any idea what might be causing this?

Denny.

---

