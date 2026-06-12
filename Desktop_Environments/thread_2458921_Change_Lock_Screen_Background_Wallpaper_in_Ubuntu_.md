---
title: "Change Lock Screen Background Wallpaper in Ubuntu 20.04"
date: 2021-03-06
forum: Desktop Environments
---

### Post by zeezam on 2021-03-06
Tried to change lock screen background in Ubuntu 20.04 but it seems not to work. :(

Followed this guide: [https://ubuntuhandbook.org/index.php/2020/05/lock-screen-background-ubuntu-20-04/](https://ubuntuhandbook.org/index.php/2020/05/lock-screen-background-ubuntu-20-04/)

Installed gir1.2-clutter-1.0.
Installed chrome-gnome-shell.
Installed Gnome Tweaks.

Launched Gnome Tweaks and changed lock screen image. Closed Gnome Tweaks. Still the same default lock screen image.

---

### Post by zeezam on 2021-03-07
This guide worked but the bg picture got all stretched out.
Tried change size of the image but same problem.

[https://ubuntuhandbook.org/index.php/2020/05/login-screen-background-ubuntu-20-04/](https://ubuntuhandbook.org/index.php/2020/05/login-screen-background-ubuntu-20-04/)

Also tried this but my gdm3.css is empty.

[https://linuxhint.com/ubuntu_login_screen_background/](https://linuxhint.com/ubuntu_login_screen_background/)

---

### Post by Holger_Gehrke on 2021-03-07
Are you talking about the **lock** screen or the **login** screen ? Those may look similar but are different things and different programs produce them. The lock-screen is what you get when you select 'Lock' in the system menu. It's meant for situations where you leave your computer and don't want other people to use it while you're away. While the lock screen is shown you're still logged in and applications continue to run. The login screen is shown before your actual session begins by the greeter, which is called by the display manager, and allows to select a user account, enter the password and log in.

Since the tutorial that *almost* works is about changing the login screen I'll assume that's what you want to change.

The last of the three tutorials you posted links for is for older versions of Ubuntu / Gnome 3. One of the new things in current Gnome is the increased use of gresource-files for themes (they were also used before, but now almost everything is inside one of those) . These are a kind of archive containing all the files necessary for the theme. The gdm3.css file is not there because it's inside a gresource-file.

The script from the second tutorial uses a tool that should be installed already to pull all the files out of the gresource file, creates a new css file for the login screen and reassembles the gresource. It sets the property 'background-size' to a value of 'cover' which means the image is scaled to fill the area. If the aspect ratio of the image is different from that of the screen the image will appear distorted. So there's two ways to fix the problem: either use an image with the right aspect ratio (16:9 or 16:10 for most modern displays) or change the script focalgdm3 to produce different css. focalgdm3 is a shell script. That means it's just a file full of text that gets interpreted as commands by the shell. You can open that file in any editor. Look for a line that says: 'background-size: cover;' (should be line 165; the part that creates the CSS starts in line 161 with an echo command and ends in line 166 with an output redirection to send the CSS to the file gdm3.css). For possible values for background-size you can look in [https://www.w3schools.com/cssref/css3_pr_background-size.asp](https://www.w3schools.com/cssref/css3_pr_background-size.asp) , I think 'contain' should work.

Holger

---

### Post by zeezam on 2021-03-09
> **Holger_Gehrke said:**
> Are you talking about the **lock** screen or the **login** screen ? Those may look similar but are different things and different programs produce them. The lock-screen is what you get when you select 'Lock' in the system menu. It's meant for situations where you leave your computer and don't want other people to use it while you're away. While the lock screen is shown you're still logged in and applications continue to run. The login screen is shown before your actual session begins by the greeter, which is called by the display manager, and allows to select a user account, enter the password and log in.

Since the tutorial that *almost* works is about changing the login screen I'll assume that's what you want to change.

The last of the three tutorials you posted links for is for older versions of Ubuntu / Gnome 3. One of the new things in current Gnome is the increased use of gresource-files for themes (they were also used before, but now almost everything is inside one of those) . These are a kind of archive containing all the files necessary for the theme. The gdm3.css file is not there because it's inside a gresource-file.

The script from the second tutorial uses a tool that should be installed already to pull all the files out of the gresource file, creates a new css file for the login screen and reassembles the gresource. It sets the property 'background-size' to a value of 'cover' which means the image is scaled to fill the area. If the aspect ratio of the image is different from that of the screen the image will appear distorted. So there's two ways to fix the problem: either use an image with the right aspect ratio (16:9 or 16:10 for most modern displays) or change the script focalgdm3 to produce different css. focalgdm3 is a shell script. That means it's just a file full of text that gets interpreted as commands by the shell. You can open that file in any editor. Look for a line that says: 'background-size: cover;' (should be line 165; the part that creates the CSS starts in line 161 with an echo command and ends in line 166 with an output redirection to send the CSS to the file gdm3.css). For possible values for background-size you can look in [https://www.w3schools.com/cssref/css3_pr_background-size.asp](https://www.w3schools.com/cssref/css3_pr_background-size.asp) , I think 'contain' should work.

Holger

Sorry for the confusion.
I want to change the lockscreen image. I see know that I have linked to login screen also. I think i will fix loginscreen also after lockscreen is completed.
Thanks for info.

---

