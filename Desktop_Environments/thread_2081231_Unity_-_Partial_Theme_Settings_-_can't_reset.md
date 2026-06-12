---
title: "Unity - Partial Theme Settings - can't reset"
date: 2012-11-06
forum: Desktop Environments
---

### Post by jon_herr on 2012-11-06
I'm having a problem with 12.04 Unity "theme" settings.

I can't seem to set everything back to default.  The main symptom is that I can't see any of the items listed in certain applications such as the software center unless I select the item or change to a "inverse" theme.

I've tried reseting Unity using the "reset unity" command at a terminal to no avail.

I've also tried using 3rd party tools like Ubuntu Tweak and etc but I can't seem to change this behavior.

Is there a folder I can delete?  A theme I can install?

This is something I did to myself by updating from gnome to unity using the same home folder mount point.  There must be a legacy setting that I can't change.

Thanks,
Jon

---

### Post by 28c64 on 2012-11-06
The command to reset unity is..

```

unity --reset

```

---

### Post by stinkeye on 2012-11-06
unity --reset won't change your theme.

Should be able to change themes with **gnome-tweak-tool**.

**[SIZE="3"]or[/SIZE]**

If you don't want to install the gnome dependencies needed by gnome-tweak-tool,
install **unsettings** (graphical configuration program for the Unity desktop)
Very good App with lots of Unity specific settings.
```
sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install unsettings
```

**[SIZE="3"]or[/SIZE]**

this terminal command will load the default theme for Unity, Ambiance.
```
gsettings set org.gnome.desktop.interface gtk-theme Ambiance && gsettings set org.gnome.desktop.wm.preferences theme Ambiance
```

---

### Post by jon_herr on 2013-02-23
Thanks for the suggestions -

No matter what I do - the contrast between visible print and background in certain apps is terrible.

The best example I have is the software center - the only text I can see is the window bar and whatever application I have highlighted.

New user profiles don't have this problem so I'm pretty sure it's a latent setting in a folder from gnome that I can't find or delete.

---

### Post by stinkeye on 2013-02-23
What's your current gtk theme.
Terminal....
```
gsettings **get** org.gnome.desktop.interface gtk-theme
```
Default is **Ambiance**.

eg
> [COLOR="SeaGreen"]glen@Quantal:~$[/COLOR] gsettings get org.gnome.desktop.interface gtk-theme
**'Ambiance'**

If you get something else,run...
```
gsettings **reset** org.gnome.desktop.interface gtk-theme
```

and check again.

If that doesn't work look in you home folder for a hidden **.gtkrc** file
which will override your theme settings.
The old gnome-color-chooser and the new gtk-theme-config applications create such files.

Search in terminal...
```
locate .gtkrc*
```

---

### Post by jon_herr on 2013-04-20
My theme is set to 'Ambiance' using the method you indicated.   

I cannot find the .gtkrc folder

The contrast is still messed up.

:(

---

