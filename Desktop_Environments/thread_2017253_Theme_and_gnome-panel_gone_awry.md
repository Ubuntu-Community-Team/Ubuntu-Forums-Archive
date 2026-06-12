---
title: "Theme and gnome-panel gone awry"
date: 2012-07-05
forum: Desktop Environments
---

### Post by TomAwezome on 2012-07-05
Though I have my theme set to Ambiance in the System Settings, recently my panel has turned entirely black (not the usual grey) and my theme has gone to something resembling a bad Clearlooks.

Here's what they look like: [http://imgur.com/Ckit5,up2Ie](http://imgur.com/Ckit5,up2Ie)

Any ideas?

---

### Post by lolpenguin on 2012-07-05
You set the theme to Adwaita, the default GNOME theme from 3.0 onwards. The panel is black in the said theme.

---

### Post by TomAwezome on 2012-07-05
[http://imgur.com/rbZmG,wPH6G](http://imgur.com/rbZmG,wPH6G)

The theme is set to Ambiance, yet it does not appear like it.
Also, bringing up a menu (as in right clicking) will either bring up a proper menu with the ambiance theme or a very ugly all white menu with dark text.
Any suggestions?

---

### Post by msammels on 2012-07-05
Let me understand this: you don't like the plan back bar at the top? OK, answer me this one please: Unity, Unity 2D, or GNOME 3?

---

### Post by TomAwezome on 2012-07-05
> **msammels said:**
> Let me understand this: you don't like the plan back bar at the top? OK, answer me this one please: Unity, Unity 2D, or GNOME 3?

Unity 2D. Only recently did the bar turn pure black.

---

### Post by msammels on 2012-07-05
Try this command, but it **will reset EVERYTHING to default**, and I take no responsibility.

```
sudo dconf reset -f /
unity --reset
```

---

### Post by TomAwezome on 2012-07-06
> **msammels said:**
> Try this command, but it **will reset EVERYTHING to default**, and I take no responsibility.

```
sudo dconf reset -f /
unity --reset
```

Neither of those did anything, and I don't have dconf installed. Should it be installed? Also, I've noticed that windows opened in sudo look correct. [http://imgur.com/FLPH9](http://imgur.com/FLPH9)

(Since I don't have dconf, I fished around in gconf to see if there was anything pointing to a different theme, and everything matched up with the root account's settings as well.)

---

### Post by kansasnoob on 2012-07-06
> **TomAwezome said:**
> Though I have my theme set to Ambiance in the System Settings, recently my panel has turned entirely black (not the usual grey) and my theme has gone to something resembling a bad Clearlooks.

Here's what they look like: [http://imgur.com/Ckit5,up2Ie](http://imgur.com/Ckit5,up2Ie)

Any ideas?

Uh, I clicked your link and get this:

[ATTACH]220764[/ATTACH]

Not sure at all if it'll be helpful but I listed some default settings in this post while playing with other themes:

[http://ubuntuforums.org/showpost.php?p=11993655&postcount=70](http://ubuntuforums.org/showpost.php?p=11993655&postcount=70)

In the future it'd be best to post screenshots using the forum tools ;)

---

### Post by lolpenguin on 2012-07-07
You seem to be getting a mix of Adwaita and Ambiance. As far as I can tell, your GTK+3 apps are in Adwaita, and GTK+2 are in Ambiance.
```
sudo apt-get install --reinstall light-themes gnome-themes-standard
```
This will reinstall your Ambiance, Radiance and Adwaita themes.

---

### Post by TomAwezome on 2012-07-14
Alright, so after a few days, I managed to fix this.
As far as I remember I checked *everything* in gsettings and gconf to ensure it was pointing to Ambiance, and not Adwaita. After that I used ```
sudo apt-get --auto-remove purge gnome-themes-standard light-themes
``` It said something about not deleting the folders in /usr/share/themes/Adwaita so I manually deleted those. After that I logged out. (This means that I was logging out with no themes installed.) After the logout I logged back in and was greeted to ugly windows (no theme, after all) and a panel that was greyish white. I then reinstalled light-themes and gnome-themes-standard, set Ambiance as my theme, and everything was back to normal. :)

---

