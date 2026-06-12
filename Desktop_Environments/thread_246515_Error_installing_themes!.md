---
title: "Error installing themes!?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by roots on 2006-08-29
hi there,

i'm already feeling totally stupid about it, but can anyone tell me what to do? when trying to install a new theme in gnome under dapper drake, whatever theme archive file i choose, i do get

Error: The file format is invalid.

any suggestions?!!?


thx in advance,
roots

---

### Post by infoseeker on 2006-08-29
I DO know that you have to extract the downloaded theme before you can install it. I find the easiest way to do this is by using mc (midnight commander). With mc you can create a folder in your home directory. On the left pane select the archive and click enter. This will open (extract) the archive into memory (tab switches between left and right panes).  On the right pane enter the directory you just created (themes, or whatever), and then select the extracted archive on the left and press F5 (copy) to copy the extracted theme files to the newly created directory.  Navigate to these extracted files when installing the theme.
Good luck.

---

### Post by roots on 2006-08-29
yep, that's how i was used to do it and i also tried that first this time - with the same result!

don't know what to do!?

---

### Post by Robopop on 2006-08-29
I have the same problem. Been Searching the forums without finding any solution.

A solution to the problem is very welcome:)

---

### Post by mgmiller on 2006-08-29
I have installed many themes in Dapper and I do not have to extract them first.  Open your themes manager (System>Preferences>Theme)  Then, just take the tar.gz package that you downloaded and drag it onto the window of the theme manager.  It will install, and you can start using it right away.

---

### Post by Robopop on 2006-08-30
> **mgmiller said:**
> I have installed many themes in Dapper and I do not have to extract them first.  Open your themes manager (System>Preferences>Theme)  Then, just take the tar.gz package that you downloaded and drag it onto the window of the theme manager.  It will install, and you can start using it right away.

The problem is that when you press the "install theme" button you get an error message: "Error: The file format is invalid.". I've tried alot of themes, get that message all the time. Nobody knows whats wrong?

---

### Post by mcduck on 2006-08-30
The easiest way to install GTK, Metacity and icon themes is to just drag&drop the archive to the theme settings window. (don't unzip them)

If that doesn't work, the maker of the theme might have packaged it in the wrong way, ot the archive contains several different themes. Then your best bet is to unzip the archive and copy all contents to ~/.themes directory (a hidden dir inside your home directory) or ~/.icons (if it's icon theme).

If you are trying to install a GDM theme, it's for your login screen and you need to open System/Administration/Login Window and install it there :)

---

