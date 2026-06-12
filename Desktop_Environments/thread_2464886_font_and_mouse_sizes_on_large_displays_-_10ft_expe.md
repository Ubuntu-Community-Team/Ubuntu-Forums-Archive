---
title: "font and mouse sizes on large displays - 10ft experience"
date: 2021-07-15
forum: Desktop Environments
---

### Post by jfaberna on 2021-07-15
This is my setup:
Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.8.0-59-generic
OS Type: 64-bit
Processors: 8 × 11th Gen Intel® Core™ i7-1165G7 @ 2.80GHz
Memory: 15.0 GiB of RAM

I have a UHD 4K 60" TV that I'm viewing from 10-12 ft. So I've set the display config to 3840x2160@60 with a Global Scale factor of 200%.

This generally works except for the mouse cursor. When I have applications open and the mouse cursor within that windows the mouse is the right size. Same for the Panel at the bottom. However, if no windows are open and it's just the desktop, the mouse cursor is so small I have trouble finding it.

This can be fixed if I set the Display config to 1920x1080@60 with 100% scale factor, but then I can't see 4K videos, etc. 

Any ideas on how to solve this?

---

### Post by him610 on 2021-07-15
Does Kubuntu do mouse trails?
Can you configure Kubuntu to highlight the mouse if you press Ctrl?
Can you go to Settings->Mouse and Touchpad, tab Theme to increase the size of your mouse?

I don't use Kubuntu, but those are things I have done in the past with other *buntu flavors.
You might want to read this article [https://itectec.com/ubuntu/ubuntu-is-there-a-mouse-trail-option/]("https://itectec.com/ubuntu/ubuntu-is-there-a-mouse-trail-option/")

---

### Post by jfaberna on 2021-07-15
> **him610 said:**
> Does Kubuntu do mouse trails?
Can you configure Kubuntu to highlight the mouse if you press Ctrl?
Can you go to Settings->Mouse and Touchpad, tab Theme to increase the size of your mouse?

I don't use Kubuntu, but those are things I have done in the past with other *buntu flavors.
You might want to read this article [https://itectec.com/ubuntu/ubuntu-is-there-a-mouse-trail-option/]("https://itectec.com/ubuntu/ubuntu-is-there-a-mouse-trail-option/")Ctrl does not highlight the mouse cursor and settings has no size option.  I hesitate to install mouse trails until I've exhausted other options.

Thanks.

---

### Post by Autodave on 2021-07-15
In Xubuntu, it is under Settings ->Mouse -> Themes -> Cursor Size

---

### Post by irv on 2021-07-15
I am running Ubuntu with Gnome desktop and I make my mouse pointer red and big so I can find it. Try running the command
```
gsettings set org.gnome.desktop.interface cursor-size 50
```
you can make the size whatever you want. I have this command in my startup applications so it runs when the pc is started.
EDIT: you will have to change the command to whatever desktop you are running.

---

### Post by jfaberna on 2021-07-15
> **Autodave said:**
> In Xubuntu, it is under Settings ->Mouse -> Themes -> Cursor SizeCursor size doesn't exist in Kubuntu

---

### Post by jfaberna on 2021-07-15
> **irv said:**
> I am running Ubuntu with Gnome desktop and I make my mouse pointer red and big so I can find it. Try running the command
```
gsettings set org.gnome.desktop.interface cursor-size 50
```
you can make the size whatever you want. I have this command in my startup applications so it runs when the pc is started.
EDIT: you will have to change the command to whatever desktop you are running.

I do have the schema org.gnome.desktop.interface and I can change the cursor-size to different sizes, but it changes nothing on the screen that I can see.

Kubuntu must be different

---

### Post by deadflowr on 2021-07-15
Kubuntu mouse settings default allows for only 3 size changes.
In Settings >> Cursor go down to the dropdown option Resolution Dependent.
In there it should list sizes like  24 36 and 48.
Choose a size and when set click Apply to set it as the size.

Fwiw, you can also create custom cursors with custom sizes, I guess,
See: [https://userbase.kde.org/Create_your_own_mouse_cursor_theme]("https://userbase.kde.org/Create_your_own_mouse_cursor_theme")

Also, I have no idea if any of this works within the *plasma on wayland *option. 
I can't see it not working but as wayland can be such a fickle beast nothing can be certain.

---

### Post by jfaberna on 2021-07-15
> **deadflowr said:**
> Kubuntu mouse settings default allows for only 3 size changes.
In Settings >> Cursor go down to the dropdown option Resolution Dependent.
In there it should list sizes like  24 36 and 48.
Choose a size and when set click Apply to set it as the size.

Fwiw, you can also create custom cursors with custom sizes, I guess,
See: [https://userbase.kde.org/Create_your_own_mouse_cursor_theme]("https://userbase.kde.org/Create_your_own_mouse_cursor_theme")

Also, I have no idea if any of this works within the *plasma on wayland *option. 
I can't see it not working but as wayland can be such a fickle beast nothing can be certain.
I'm running plasma X11 and if I change the cursor setting to 48, it only changes the cursor size within a window and not on the desktop.  I can find my cursor easily withing an open window, just not on the desktop.  The size on the blank desktop is always the smallest until I mouse over to a windows.

---

### Post by deadflowr on 2021-07-15
I had that issue.
But for some reason after a reboot it took the correct setting across the desktop as well as the app windows.
Though I am not sure if I toggled something on or off and some point.

---

### Post by him610 on 2021-07-15
> Cursor size doesn't exist in Kubuntu
Maybe it's time to consider other *buntu flavors.

---

### Post by jfaberna on 2021-07-15
> **him610 said:**
> Maybe it's time to consider other *buntu flavors.

I've tried all the *ubuntu's and Fedora, Arch, and Manjaro.  All have major issues with the way I use a PC connected to  UHD 4K TV.

I'm down to KDE Plasma and Cinnamon. So Kubuntu and Linux Mint are what I'm working with. I like that they are both using Ubuntu as the core.

Xubuntu maybe worth a test again. I haven't tried that since 14.04.

---

### Post by jfaberna on 2021-07-15
I have a solution that seems to be stable at the moment. I downloaded the latest Ubuntu 20.04.2  Desktop ISO and installed that.  Even though the kernel is 5.8, it seems to have the drivers for the 11th gen GFX and lan chip.

As was stated above Ubuntu allowed the setting of the mouse size that worked everywhere including the blank desktop.

I was able to get the Display set to UHD 4K with 200% scale and that works for me at 10'.

However,I still have to solve the login screen for GDM being too small. I need it to have the same scaling as my display.This was a feature that Kubuntu had that I liked.

Any ideas?

---

### Post by jfaberna on 2021-07-18
I found something that might be helpful to others. The solution for me appears to be Ubuntu 21.04, but I could not install it until today. Problem was my UHD TV has a setting for  HDR and HDMI 2.0 that doesn't work well with the Linux install process. 

So to get it installed I turn off that TV setting, do the complete install, do the updates, and then turn that feature back on. Without  the HDMI 2.0 feature I can't  play 4K videos. Ubuntu 21.04 has the kernel, 5.11.0-22-generic so all my hardware now has up to date drivers.

And  I can now have my BIG mouse cursor.

---

