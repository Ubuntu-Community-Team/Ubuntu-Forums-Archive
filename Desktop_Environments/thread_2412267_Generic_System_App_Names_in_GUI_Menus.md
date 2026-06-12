---
title: "Generic System App Names in GUI Menus"
date: 2019-02-10
forum: Desktop Environments
---

### Post by DrewT on 2019-02-10
I've been using Ubuntu since 2008 (Kosmic), and I love it, though I lack the expertise to make it sing just the way I'd like it to. One recurring annoyance is how certain system apps -- notably Nautilus and Gedit -- show up in the GUI menus by purely generic names ("Files" and "Text Editor," respectively). I kinda hate Nautilus, so I've been using Nemo for a long time. And lately I've been thinking of adding Thunar to my system because of its vaunted file-renaming powers. But each of these file managers shows up (or will show up) in my GUI menu as simply "Files." If I want to open one other than the default, I can't be sure of picking the one I want from the GUI without opening it to see.

I know of some workarounds. Of course I can open them from terminal using their real names. And I have set Nemo as the default for most purposes, and set the Files icon in the sidebar menu to open Nemo instead of Nautilus. But what I'd like is for Nemo and Nautilus (and Thunar if I add it) (and Gedit for that matter) to show up in the GUI menus by their specific names and not their generic-system-function names. 

I have searched for a way to do this, but it's hard to formulate an appropriate query and so far I haven't found anything useful. 

Am I the only user who's bugged by this "feature"?

---

### Post by oldfred on 2019-02-10
I am using fallback/gnome-panel
And in Applications in top panel, I can right click to Edit Menus.
Then under properties of each entry is a way to edit name. 
Not then sure how to get to those entries from default gnome.

---

### Post by CatKiller on 2019-02-10
The name that gets displayed in the menu for each application is specified in that application's desktop file. They are just text files.

---

### Post by DrewT on 2019-02-10
> **CatKiller said:**
> The name that gets displayed in the menu for each application is specified in that application's desktop file. They are just text files.

Here's my desktop file for Nemo (in /usr/share/applications):

> [Desktop Entry]
Type=Application
Name=Nemo
Comment=Start Nemo desktop at log in
Exec=nemo-desktop
OnlyShowIn=X-Cinnamon;
AutostartCondition=GSettings org.nemo.desktop show-desktop-icons
X-GNOME-AutoRestart=true
NoDisplay=true

But what shows in my menus is just "Files." That name appears three times:  Once for Nemo and twice for Nautilus. Can I edit their respective desktop files to make them show "Nemo" and "Nautilus"?

---

### Post by DrewT on 2019-02-10
Thanks for those clues oldfred. Working on them ...

---

### Post by oldfred on 2019-02-10
Do a search for alacarte

I signed out and signed in with Ubuntu, not flashback and searched for alacarte. That gave me the same menu as edit menus did in flashback.
Under Accessories were files and properties seemed to be editable. I did not change mine.

---

### Post by CatKiller on 2019-02-11
> **DrewT said:**
> Here's my desktop file for Nemo (in /usr/share/applications):

No, that's **one of** the desktop files used by Nemo - specifically the one that starts Nemo at login. That is /usr/share/applications/nemo-autostart.desktop.

The one that is used for the menu entry is /usr/share/applications/nemo.desktop, which is very different.

You should note that the file browser displays the localised Name field rather than the filename when showing .desktop files.

---

### Post by again? on 2019-02-11
Create your own Nemo launcher in **~/.local/share/applications**
User .desktop files in this location will override system launchers in /usr/share/applications
 
Copy the system Nemo launcher
```
cp /usr/share/applications/nemo.desktop ~/.local/share/applications/
```

Then edit to your liking.
eg my ~/.local/share/applications/nemo.desktop with quicklist items to open other File managers.
```
[Desktop Entry]
Name=Nemo
Comment=Access and organize files
Exec=nemo --no-desktop %U
Icon=/home/glen/Pictures/icons/coloured_folders/user-home.png
Terminal=false
Type=Application
StartupNotify=false
#OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Utility;Core;
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nemo
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=1.7.2
#NoDisplay=true

Actions=Thunar;nautilus;recent;Clear-recent;

[Desktop Action Thunar]
Name=Thunar
Exec=thunar
Icon=thunar

[Desktop Action nautilus]
Name=Nautilus
Exec=nautilus
Icon=nautilus

[Desktop Action recent]
Name=Recent
Exec=nemo recent:///
Icon=history

[Desktop Action Clear-recent]
Name=Clear Recent
Exec=/home/glen/scripts/clear-recent-confirm.sh
```

This pic shows xfce with plank and my custom nemo launcher.
Gnome-shell will also display quicklists but not the quicklist menu icons.
[ATTACH=CONFIG]282458[/ATTACH]

In gnome-shell, for gedit you may have to copy over and edit both of the "Text Editor" files in /usr/share/applications
I don't use gnome-shell but, testing it appeared to be the case.
Easiest just to use the file manager to copy and paste.
I also, in gnome-shell had to reboot after editing the files.
[ATTACH=CONFIG]282460[/ATTACH] [ATTACH=CONFIG]282459[/ATTACH] [ATTACH=CONFIG]282461[/ATTACH]

---

