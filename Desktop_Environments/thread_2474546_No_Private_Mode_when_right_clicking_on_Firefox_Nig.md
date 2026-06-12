---
title: "No Private Mode when right clicking on Firefox Nightly"
date: 2022-05-02
forum: Desktop Environments
---

### Post by TechnoJunky on 2022-05-02
I've had a persistent home drive for several years (just remount home without format). This has kept all my desktop settings the same no matter what version of Ubuntu I install. I just upgraded to Kubuntu 22.04 and decided to have a completely clean profile by creating a new home directory. I prefer using Firefox Nightly instead of the default installed version. I add it to the application menu, using the command "~/MyApps/Nightly/firefox" and then Add to Panel. On my old desktop, I could right click on the Nightly icon, either on the panel or in the menu, and select Open in Private Mode (or something very similar). I can't do that on this new desktop. When I right click on the icon, I get Properties, Add Widget and Enter Edit Mode. Can someone assist in configuring the option to run in private mode?

---

### Post by Holger_Gehrke on 2022-05-02
Since I'm neither a user of KUbuntu nor of KDE this is just an informed guess; but I assume that "Add to Panel" creates a .desktop file for an application. It *should* be in ~/.local/share/applications/ which is the default place for user specific desktop files and you don't mention having to enter your password into pkexec or something like that to allow you to write to the system directory for desktop files '/usr/share/applications/'. 
Open a terminal, change to the directory with 'cd ~/.local/share/applications/' and run 'grep firefox *.desktop'. If it finds a file, open it in an editor. Context menu items are normally created from Actions defined in the desktop file for a program, so you have to add an action to the file. Add this at the end of the file
```

Actions=Private;

[Desktop Action Private]
Exec=firefox --private-window
Name=Open Private Window

```
If the file already had other Actions defined (unlikely, but ...), leave out the first line and add 'Private;' to the existing 'Actions='-line. More details on desktop files can be found at [https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/)

Holger

---

### Post by TechnoJunky on 2022-05-02
That worked.  Thank you so much Holger.

---

