---
title: "Launchers"
date: 2018-09-13
forum: Desktop Environments
---

### Post by gweinstein on 2018-09-13
I have a 4K screen on my Lenovo YOGA laptop. Some apps run scaled, but not all, which makes menus and buttons impossible to use. I found the script run_scaled ([https://github.com/kaueraal/run_scaled](https://github.com/kaueraal/run_scaled)) which seems to be working ok. Now I could be running everything from a terminal like a mench, but I am a sucker for GUI, so I made a few launchers and placed them on my desktop. Drawback, they don't show up on the application menu (e.g. with Super+A) and either I cannot put them on the launch bar, or if I do (e.g. with add to favorites) I get the usual launcher (not the scaled one). I have a feeling that this could be solved but perhaps only individually (i.e. per app). Any ideas?

Thanks in advance.

---

### Post by again? on 2018-09-13
Place them in ~/.local/share/applications
You can copy and edit launchers to this location to override the original.
See this post which deals with quicklists but also relates to just changing the "Exec=" command.
[https://ubuntuforums.org/showthread.php?t=2400629&p=13799449#post13799449](https://ubuntuforums.org/showthread.php?t=2400629&p=13799449#post13799449)

---

### Post by gweinstein on 2018-09-13
Thanks! Should I name them with the name of the original application? They're currently named Desktop.JabRef (for example).

---

### Post by again? on 2018-09-13
The display name as set in the .desktop file doesn't matter.
But this can be different than the actual file name.

The file name should be the same if you want to override the corresponding file in /usr/share/applications
It can be a bit confusing because .desktop files in /usr/share/applications show as the display name in the file browser, but the actual file name will be [COLOR="#696969"]xxxxx[/COLOR].desktop
The actual file name can be found with ls in terminal.
```
ls /usr/share/applications
```

or drag and drop into a text editor.
[ATTACH=CONFIG]281061[/ATTACH]

However, files in ~/.local/share/applications will show as the file name unless they have execute permissions.
[ATTACH=CONFIG]281063[/ATTACH]

---

### Post by gweinstein on 2018-09-13
Didn't work. :-(

Here is the output of ls -l in ~/.local/share/applications/

```
-rwxr-xr-x 1 gilbert gilbert 167 Sep 13 18:17 jabref.desktop

```

Here is the jabref.desktop file:

```
[Desktop Entry]Version=1.0
Type=Application
Terminal=false
Exec=run_scaled jabref
Name=jabref.desktop
Comment=JabRef
Name[en_US]=jabref.desktop
Comment[en_US]=jabref

```

And here is the output of ls /use/share/applications/jabref.desktop

```
-rw-r--r-- 1 root root 312 Apr  6 20:54 /usr/share/applications/jabref.desktop
```

I ran jabref from the command line and it runs non-scaled.

What am I missing?

---

### Post by gweinstein on 2018-09-13
Although in Applications (e.g. Super+A) I now get only the file in the local folder (and of course it does start scaled).

---

### Post by again? on 2018-09-13
So it works from applications?
I don't use gnome-shell.
You may need to logout or restart the shell and possibly repin to the launcher.

[COLOR="#FF0000"]**Edit:**[/COLOR]
I just tested this in gnome-shell dock and it doesn't work.
Why? Stuffed if I know.

If you install a simple dock like "plank", you can drag and drop the launcher on it and it works.
gnome-shell is bloated crap.
[ATTACH=CONFIG]281064[/ATTACH]

---

### Post by gweinstein on 2018-09-16
Indeed, doesn't work on the gnome-shell dock. 

I installed dash-dock to hide the dock as per this: [https://askubuntu.com/questions/979732/how-can-i-hide-the-dock-in-gnome](https://askubuntu.com/questions/979732/how-can-i-hide-the-dock-in-gnome).

I also installed Plank and can add my launchers from ~/.local/share/applications to Plank.

One comment which stumped me for a while. Some of the launchers had the extension Filename.Desktop which Plank didn't like (treated it as a text file and opened in gedit) although the file browser did treat it as a launcher. Comparing it with one of the other launchers which did work on Plank, I noticed that the difference was the extension Filename.desktop. Now everything works! Thanks for the help.

---

### Post by again? on 2018-09-16
No problem.
If you didn't know... ctrl+right mouse on plank for preferences
This github page has a collection of themes you can download as a zip file.
Extract and place the theme folders in ~/.local/share/plank/themes
[https://github.com/erikdubois/plankthemes](https://github.com/erikdubois/plankthemes)

---

### Post by gweinstein on 2018-09-18
Ctrl+Right Click does not work for me. Instead I used "plank -- preferences" in terminal. Ctrl+Scroll does (for scaling icons). Can I close this thread?

---

### Post by again? on 2018-09-18
> **gweinstein said:**
> Ctrl+Right Click does not work for me. Instead I used "plank -- preferences" in terminal. Ctrl+Scroll does (for scaling icons). Can I close this thread?

Use thread tools.

---

