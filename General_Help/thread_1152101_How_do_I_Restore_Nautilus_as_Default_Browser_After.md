---
title: "How do I Restore Nautilus as Default Browser After Uninstalling KDE?"
date: 2009-05-07
forum: General Help
---

### Post by Penguin Guy on 2009-05-07
After installing, then removing KDE the directories in the 'Places' menu always try to open in Dolphin or whichever browser you used in KDE. I believe that Nautilus is still the default browser and this is only a problem with the places menu. The psychocat tutorial does not fix this problem.

I have since switched distro's so this is no longer an issue for me, however I believe [[COLOR="Blue"]narnie[/COLOR]]("http://ubuntuforums.org/member.php?u=268855") is also looking for a solution to this problem.

Thanks!

---

### Post by DeMus on 2009-05-07
> **Penguin Guy said:**
> So I tried KDE out for a while; didn't like it; removed it. But now I am left with Dolphin as my default browser - how can I switch back to nautilus? I've looked at options and searched through google and so far have found no way to change the default file browser - but surely this is a common and basic task? Do I really have to edit a text file (or worse reinstall) to switch file browsers?

If reinstalling is the only way to restore it then a command would be nice :P.

Thanks!

Open meny System - Preferences - Preferred apllications
On the 1st tab it says which browser is your favorite: choose Nautilus there.

---

### Post by kanikilu on 2009-05-07
Check out this page, near the bottom is a script you can download to restore nautilus as the default.

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by Penguin Guy on 2009-05-07
> **DeMus said:**
> Open meny System - Preferences - Preferred apllications
On the 1st tab it says which browser is your favorite: choose Nautilus there.
I believe that means web browser?
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=112820&stc=1&d=1241719128[/IMG]](http://ubuntuforums.org/attachment.php?attachmentid=112820&stc=1&d=1241719128)



> **kanikilu said:**
> Check out this page, near the bottom is a script you can download to restore nautilus as the default.

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)
That doesn't work - I've updated the first page with more info.

---

### Post by kanikilu on 2009-05-07
[QUOTE=Penguin Guy]The psychocat guide does not work - it is designed to restore from a backup file which is created by the other psychocat browser-switchers.[/QUOTE] Oops, sorry, missed the note at the end of that page.

I've attached the .desktop files mentioned in the script in a .zip file. You could just copy them to /usr/share/applications manually to see if that works (making backups before replacing any files, of course).

// Edit - I notice there's one other nautilus-related file that isn't listed in that script, nautilus-browser.desktop. If you need that, the contents of it on my machine are: ```
[Desktop Entry]
Encoding=UTF-8
Name=File Browser
Comment=Browse the file system with the file manager
TryExec=nautilus
Exec=nautilus --no-desktop --browser %U
Icon=system-file-manager
Terminal=false
StartupNotify=true
Type=Application
NoDisplay=true
Categories=GNOME;GTK;System;Utility;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
X-Ubuntu-Gettext-Domain=nautilus
```

---

### Post by Penguin Guy on 2009-05-07
Thanks, I'll try it and post back the results.
- Nope; it doesn't make a difference.

---

### Post by Penguin Guy on 2009-05-09
What I'm looking for is the file that says "Nautilus is the default file browser." rather than  "Nautilus should do this and that.". But thanks for the help anyway.

---

### Post by narnie on 2009-05-30
Bump

---

### Post by loell on 2009-05-30
with gconf.

```
gconf-tool --set "/desktop/gnome/applications/component_viewer/exec" --type string "nautilus %s"
```

---

### Post by narnie on 2009-05-30
Thanks so much for recommending this, but I checked out the value using gconf-editor before changing it to see it's default. It was already set to nautilus %s.

Any further ideas would be greatly appreciated. :)

Narnie

---

### Post by rynoprinsloo on 2009-07-24
> **loell said:**
> with gconf.

```
gconf-tool --set "/desktop/gnome/applications/component_viewer/exec" --type string "nautilus %s"
```

Thanks, it did the trick for me. :) 
(NOTE: In ubuntu 9.04 gconf-tool has been renamed to gconftool)


> **narnie said:**
> but I checked out the value using gconf-editor before changing it to see it's default. It was already set to nautilus %s.

I also did this before trying the command. It was the same but worked perfectly afterwards.

Ryno

---

### Post by Kungalm on 2010-01-09
I tried all of these solutions and non did actually work. My problem I did have was that when choosing a folder under the Places menu it kept opening them with Konqueror. I found the solution to be rather easy to fix this behaviour. Open **System->Preferences->System Settings **then choose **Default Applications->FileManager.  **Then you can choose the preferred application. Well that did the trick for me at least.

/Kungalm

---

### Post by Drendeldair on 2010-01-24
I had the same problem and found this link. It worked perfectly for me.

[http://www.ignition-project.com/articles/2009/01/08/fix-dolphin-hijacks-the-gnome-places-menu]("http://www.ignition-project.com/articles/2009/01/08/fix-dolphin-hijacks-the-gnome-places-menu")

---

