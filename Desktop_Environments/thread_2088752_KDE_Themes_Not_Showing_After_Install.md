---
title: "KDE Themes Not Showing After Install"
date: 2012-11-27
forum: Desktop Environments
---

### Post by Maleificus on 2012-11-27
Hello. So I go in to Application Launcher ->  Applications -> Settings -> System Settings -> Workspace Appearance -> Desktop Theme and then I click on the button that says "_G_et New Themes...". Then I install a theme.

Now the problem I have is that the theme now does not show as a theme under the "_T_heme" tab under "Desktop Theme". Can someone help me fix this issue? I am running Kubuntu 12.10

---

### Post by ankspo71 on 2012-11-27
This happens sometimes when themes fail to get extracted by the theme installer.

The downloaded theme package should still be in a temporary directory within your hidden ~/.kde configuration folder. Look for it there. 

/home/username/.kde/tmp-folder/theme.tar.gz

When you find it, extract the theme package, then place the contents of that theme package in:

/home/username/.kde/share/apps/desktoptheme/

Now you will be able to go to System Settings -> Workspace Appearance -> Desktop Theme and find and select the theme.

Themes can also be downloaded with your web browser from kde-look.org too.
Look for the section called Plasma Themes to get desktop themes.

---

### Post by Maleificus on 2012-11-27
Thank you, that worked!

---

