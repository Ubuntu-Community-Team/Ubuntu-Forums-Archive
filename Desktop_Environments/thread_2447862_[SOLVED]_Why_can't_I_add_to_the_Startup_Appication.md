---
title: "[SOLVED] Why can't I add to the Startup Appications?"
date: 2020-07-27
forum: Desktop Environments
---

### Post by extraspecialbitter2 on 2020-07-27
I've been trying to add conky and xscreensaver to my list of startup applications via the GUI. It appears to fairly straightforward:

[ATTACH=CONFIG]286565[/ATTACH]

However, after selecting "Close", my additions disappear. I am running Ubuntu 20.04.

---

### Post by Dennis N on 2020-07-27
Try this to get xscreensaver going. Make a text file containing:

```
[Desktop Entry]
Type=Application
Name=X Screensaver
Comment=Use real screensavers
Icon=preferences-desktop-screensaver
Exec=xscreensaver -nosplash
NoDisplay=true

```
and save it as **xscreensaver.desktop** in **~/.config/autostart**

Restart and it should start monitoring for inactivity upon login.

---

### Post by monkeybrain20122 on 2020-07-27
This is yet another way that gnome devs make the desktop experience frustrating for users. In gnome shell you have go through the extra step to create a .desktop file for a command or a user script in order to make it autostart (see Dennis N's post above). I am using unity on 20.04 and all I have to do is type in the command in startup applications like before.

---

### Post by ActionParsnip on 2020-07-27
I've always done it this way. Works universally so doesn't matter the desktop environment. Do you have full access to the autostart folder as your user?

---

### Post by extraspecialbitter2 on 2020-07-27
> **Dennis N said:**
> Try this to get xscreensaver going. Make a text file containing:

```
[Desktop Entry]
Type=Application
Name=X Screensaver
Comment=Use real screensavers
Icon=preferences-desktop-screensaver
Exec=xscreensaver -nosplash
NoDisplay=true

```
and save it as **xscreensaver.desktop** in **~/.config/autostart**

Restart and it should start monitoring for inactivity upon login.

Thanks for the reply! At the moment, ~/.config/autostart is a flat file:

```

nitrogen --restore &
compton --config ~/.config/compton.conf &
lxpanel &
conky &

```

Given that conky is not being started up automatically, I'm guessing it's not being used, so I'm tempted to save it off somewhere and try out your suggestion.

---

### Post by extraspecialbitter2 on 2020-07-28
> **ActionParsnip said:**
> I've always done it this way. Works universally so doesn't matter the desktop environment. Do you have full access to the autostart folder as your user?

I'm not sure what you mean by "autostart folder". I navigated to the "Startup Applications" icon on the "Activities" bar.

[ATTACH=CONFIG]286564[/ATTACH]

---

### Post by slickymaster on 2020-07-28
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by extraspecialbitter2 on 2020-07-28
> **slickymaster said:**
> Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

Thanks for the guidance and for modifying my post accordingly.

---

### Post by deadflowr on 2020-07-28
> At the moment, ~/.config/autostart is a flat file:
```
nitrogen --restore &
compton --config ~/.config/compton.conf &
lxpanel &
conky &
```
Given that conky is not being started up automatically, I'm guessing it's not being used, so I'm tempted to save it off somewhere and try out your suggestion.
Based on the image in the next post nothing in that file is running.

~/.config/autostart is a folder not a file, and needs to have .desktop file formatted files like Dennis N's example in order to utilize them.
Perhaps try making the folder and then see what happens.

---

### Post by CatKiller on 2020-07-28
> **extraspecialbitter2 said:**
> At the moment, ~/.config/autostart is a flat file

I'm pretty sure it should be a directory with .desktop files in.

---

### Post by extraspecialbitter2 on 2020-07-28
> **CatKiller said:**
> I'm pretty sure it should be a directory with .desktop files in.

I'm not sure why there was an autostart file in my ~/.config directory, but I've moved it to a temporary directory for safe keeping and have created an autostart directory in its place. In addition to the xscreensaver.desktop file suggested by Dennis N., I've created the following conky.desktop file in the same directory:

```

[Desktop Entry]
Type=Application
Name=Conky
Comment=Conky Display
Icon=preferences-desktop-monitor
Exec=conky -d
NoDisplay=true

```

I'm happy to report that upon the next reboot, it all worked as expected. Thank you for all of the help!

Paul (Extra Special Bitter)

---

### Post by deadflowr on 2020-07-28
> I'm not sure why there was an autostart file in my ~/.config directory,
Looking at the file content posted was this either an upgrade or fresh install while keeping the home folder?
The current desktop in the posted image is clearly gnome, but the autostart file is for starting lxde(maybe lxqt).
Or did you try installing the lxXX session on to the current desktop?

---

### Post by SeijiSensei on 2020-07-28
This is one area where Kubuntu appears easier than GNOME-based flavors.  In KDE, you right click on the start button equivalent and choose Edit Applications. Or you can just select an application, right-click it and choose "Add to Favorites."

---

