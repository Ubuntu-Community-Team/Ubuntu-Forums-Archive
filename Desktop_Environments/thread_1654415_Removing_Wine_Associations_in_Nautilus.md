---
title: "Removing Wine Associations in Nautilus"
date: 2010-12-28
forum: Desktop Environments
---

### Post by gerowen on 2010-12-28
I just removed wine, I want it completely removed from my system.  I installed it and removed it using the Software Center.  However I still have associated options in the Nautilus context menu.  For example when I right click any text file I have "Open With notepad" as an option.  It's easy enough to right click that file, go to the open with tab, and remove notepad from the list of options.  However it's apparently associated with certain types of files because the option was there for bash scripts I'd written with no extension, files with the .txt extension, etc.  So this is apparently some file associations that wine installed and didn't take out.  I've searched the xml files in /usr/share/nautilus/ui and none of those contained the word "notepad" so I'm guessing that's not where I need to be focusing my attention.  I've done some googling and nobody seems have a definitive answer that I can find.  Also, I found a "how to uninstall" on Wine's website where it basically just had me remove $HOME/.wine and some gnome association settings, and I did that and have even rebooted and that option was still there.  I've removed it for those two types of files, but I want to know where it's stored so I can get rid of all traces.

---

### Post by Dave_L on 2010-12-28
I recently had to fix some file associations (not wine-related), and the relevant configuration files were in ~/.local/share/applications/.

---

### Post by karthick87 on 2010-12-28
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

---

### Post by gerowen on 2010-12-28
> **karthick87 said:**
> [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

[QUOTE=Wine FAQ]**5.3. How do I uninstall Wine?**

If you installed Wine with your distribution's package manager, use the package manager again to uninstall Wine. (If you installed Wine from source, then use make uninstall in the source directory to remove it.)

This won't uninstall your Windows apps, though; see above for that.
[/QUOTE]

I did a bit more googling and didn't really find anything except [this.](http://art.ubuntuforums.org/showthread.php?t=1259080)  After reading I gave it a whirl:

```
sudo update-mime-database /usr/share/mime
```
```
rm -rf .local/share/mime
```

Logged off, logged back on, option is still there.  I've removed it manually by just taking it out of the "Open With" tab, but this affected both user accounts on the computer, and removing the local mime settings for each user did not help.  Restarting nautilus (killall nautilus) afterward didn't help either.  I'll create temporary guest accounts to continue experimenting until I remove the "Open With notepad" option from the "System" and not just an individual user's profile.

---

### Post by stinkeye on 2010-12-28
Have you looked at ```
 ~/.local/share/applications/wine
```

---

### Post by sairuk on 2011-02-18
I wanted to remove the "Open in Notepad" in XFCE, I was successful by:

1.) Editing mimeinfo.cache
```
nano ~/.local/share/applications/mimeinfo.cache
```
2.) Comment out
```
text/plain=wine-extension-txt.desktop
```
3.)Save file

---

### Post by -ijk- on 2011-05-29
> **stinkeye said:**
> Have you looked at ```
 ~/.local/share/applications/wine
```
thanks :)

```
rm ~/.local/share/applications/wine-extension-txt.desktop 

update-desktop-database #this updates mimeinfo.cache
```

---

### Post by maverick280857 on 2011-05-29
I removed wine using

```
sudo apt-get remove wine wine1.2 wine1.2-gecko
```

(I had to run sudo apt-get autoremove afterwards)

But the Ubuntu menu in Cairo Dock and also the system menu still contain entries for Wine. How do I get rid of them? Usually if I uninstall anything using apt-get, the icons are also removed.

I also did 

```
rm -rf $HOME/.wine
```

---

### Post by Krytarik on 2011-05-29
maverick280857, for Wine, all the launchers/menus and mimetypes get stored in the user's home directory, that's why a removal of Wine itself doesn't change anything in that aspect.

Remove the concerning files/dirs from these directories, listed in the order of the directory tree (there may be even more, although probably less important):

~/.config/menus/applications-merged
~/.local/share/applications
~/.local/share/applications/wine
~/.local/share/desktop-directories
~/.local/share/icons
~/.local/share/mime
~/.wine/drive_c/users/Public/Desktop
~/.wine/drive_c/users/Public/Start Menu/Programs
~/.wine/drive_c/users/<USER>/Desktop
~/.wine/drive_c/users/<USER>/Start Menu/Programs

Greetings.

---

### Post by maverick280857 on 2011-05-29
> **Krytarik said:**
> 
~/.config/menus/applications-merged
~/.local/share/applications
~/.local/share/applications/wine
~/.local/share/desktop-directories
~/.local/share/icons
~/.local/share/mime


Thanks Krytarik! Deleting the contents of the above-mentioned folders has solved the problem.

(PS -- If one just wants to remove the icons, one can use 'alacarte'. This is for OPs who may visit this page.)

---

