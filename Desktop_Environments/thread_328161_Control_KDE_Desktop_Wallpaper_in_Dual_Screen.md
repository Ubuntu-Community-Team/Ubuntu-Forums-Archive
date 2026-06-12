---
title: "Control KDE Desktop Wallpaper in Dual Screen"
date: 2006-12-30
forum: Desktop Environments
---

### Post by kebes on 2006-12-30
I'm running Kubuntu 6.06, and am using KDE 3.5.2. I have a dual-screen setup, with monitors spanned using the nvidia driver and "TwinView" enabled (in "/etc/X11/xorg.conf").

My problem relates to controlling the desktop background image (i.e. wallpaper). Originally I selected a group of wallpapers to run in "slide show" mode. In the configuration panel (right-click on desktop > Configure Desktop > Background) I had it set to: "All Desktops" and "On Each Screen".

The behavior was that it would randomly switch between different desktop images. At any given moment, however, it would be the *same* image on both the left and right screen.

Recently I added some images to the slide show list, and suddenly the behavior changed. Now, the desktop randomly switches, but it is a *different* random picture on the left and right screen!


I do not know which one is the "intended" behavior, but I would like to be able to control it rationally. In the configuration panel there does not appear to be any option to control whether the two screens are randomized independantly or not.

The settings for this panel appear to be in "~/.kde/share/config/kdesktoprc", however I am having trouble interpreting this file.

Does anyone know where I can find good documentation explaining "kdesktoprc"? Or does anyone know how to rationally control the behavior of wallpaper slideshows when using a dual screen setup?

Any help would be greatly appreciated.

---

### Post by kebes on 2006-12-31
Okay so this is what I did. I compared my "kdesktoprc" (located in "~/.kde/share/config/") with the default one, stored at:
/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdesktoprc

I then edited my "kdesktoprc" and deleted all the sections like [Desktop0] and [Desktop0Screen0] and so on (there were many of those, e.g. [Desktop3Screen1] and so on). I replaced these with the default "[Desktop0]" settings from the default file. Then I opened up the configuration panel and made changes. The behavior is now back to the "old way". (Left and right screen display same desktop wallpaper.)

So if the desired behavior is for the left and right screen to display the same (randomly changing) image, then revert to a default "kdesktoprc" state and make a minimal number of changes. If, on the other hand, you want the two screeens (Screen0 and Screen1) to be treated independantly, then you can specify separate settings for [Desktop0Screen0] and [Desktop0Screen1] in kdesktoprc.


Hope that helps someone else!

---

