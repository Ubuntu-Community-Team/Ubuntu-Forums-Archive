---
title: "configure lxde desktop wallpaper and menus?"
date: 2009-08-18
forum: Desktop Environments
---

### Post by user sam on 2009-08-18
I know I tend to ramble, so I'll try to make this concise. I've got lxde and ubuntu on my old computer and have accidentally lost access to the menu that allows you to change the desktop wallpaper and change the right-click desktop options. could I launch the thing from the command line somehow? Can't find the command.
:confused:
Post #2 helped. And it gave me an idea to make my system better. thanks.:KS

---

### Post by mcduck on 2009-08-19
You can access the same menu through the file manager's settings (since it's the PCManFM file manager that handles the desktop wallpaper & icons in LXDE).

Just open the file manager and go to Edit/Preferences.

edit: to launch the same dialog from command line you can run "pcmanfm --show-pref=2"

---

### Post by XubuRoxMySox on 2009-08-19
In LXDE, just *right*-click the desktop. It opens up a menu, choose Desktop Settings and select your wallpaper from there.

You can add any wallpaper you like by putting it in *usr/share/lxde/wallpaper*.

-Robin

---

### Post by mcduck on 2009-08-19
> **dixiedancer said:**
> In LXDE, just *right*-click the desktop. It opens up a menu, choose Desktop Settings and select your wallpaper from there.

You can add any wallpaper you like by putting it in *usr/share/lxde/wallpaper*.

-Robin

The OP just said he has lost the access to that menu, probably by either disabling PCManFM from drawing the desktop, or by setting it to show the window manager's menu instead of the PCmanFM menu..

(and the wallpapers can be in any directory)

---

### Post by XubuRoxMySox on 2009-08-19
> **mcduck said:**
> The OP just said he has lost the access to that menu, probably by either disabling PCManFM from drawing the desktop, or by setting it to show the window manager's menu instead of the PCmanFM menu..

(and the wallpapers can be in any directory)

Ooopsie, you're right! I'm sorry...

The only quick and easy way I know to do it is to use Synaptic again, UNINSTALL LXDE, then Re-install it. It might restore whatever got lost.

If you still have your wallpapers, place in a separate folder so you can restore them to *usr/share/lxde/wallpaper* afterwards.

I've actually done that myself once, so I know it works if all else fails.

Let us know...

-Robin

---

### Post by yogieza on 2010-02-24
> **mcduck said:**
> You can access the same menu through the file manager's settings (since it's the PCManFM file manager that handles the desktop wallpaper & icons in LXDE).

Just open the file manager and go to Edit/Preferences.

edit: to launch the same dialog from command line you can run "pcmanfm --show-pref=2"

Thanx Bro :P , this is works in my PC.My right click mouse on desktop have back to normal. Once again Thanx a lot :P

---

### Post by mcook2 on 2011-05-27
Running LXDE remotely, it works for me as follows.

In LXDE .. PCFileMan/Edit/Preferences/Desktop/ .. under "General" .. unset "show menus provided by WM when desktop is clicked".

This is the reverse action?

Is that a bug or because I am running remotely?

Thanks,

---

### Post by mcudrc on 2011-11-14
Hello!

I've just had the same problem, but the menu id pcmanfm did not show "Desktop" tab. I found out, that it suffices to manually edit the following file, in case anyone has the same problem.

~/.config/pcmanfm/lubuntu/pcmanfm.conf

and change the one in
show_wm_menu=1
to 0.

I hope this helps, without having to reinstall the lxde manually.

Regards,
Mcudrc

---

### Post by raztus on 2011-12-12
For others who stumble on this thread:

I can confirm that in PCManFM 0.9.9 under Edit > Preferences, there is no "Desktop" tab.  However, in another thread I found the following pcmanfm argument that brings up the display configuration:

```
pcmanfm --desktop-pref
```

Thanks to [http://ubuntuforums.org/showthread.php?t=1884082](http://ubuntuforums.org/showthread.php?t=1884082)

**Update:** Attached is a shortcut for the lxde menu.  Simply remove the ".txt" from the end of the filename, and copy this to /usr/share/applications.  You'll then find it in Menu > Preferences > Desktop Preferences.

---

