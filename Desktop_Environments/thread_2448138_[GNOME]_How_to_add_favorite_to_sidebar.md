---
title: "[GNOME] How to add favorite to sidebar?"
date: 2020-08-02
forum: Desktop Environments
---

### Post by pupscout on 2020-08-02
Typically, when I launch an application, I can right-click on its sidebar icon and click **Add to Favorites. **However, some applications lack this option. Is there any workarounds to add them to the sidebar?

---

### Post by deadflowr on 2020-08-02
> However, some applications lack this option. 
Which applications?

---

### Post by pupscout on 2020-08-02
Specifically I just started using Standard Notes:

[https://standardnotes.org/](https://standardnotes.org/)

---

### Post by deadflowr on 2020-08-02
It's an appimage so you probably need to create desktop launcher for it,
Look over these and see they help: 
[https://askubuntu.com/questions/902672/registering-appimage-files-as-a-desktop-app]("https://askubuntu.com/questions/902672/registering-appimage-files-as-a-desktop-app")
[https://docs.appimage.org/reference/desktop-integration.html]("https://docs.appimage.org/reference/desktop-integration.html")

---

### Post by pupscout on 2020-11-29
> **deadflowr said:**
> It an appimage so you probably need to create desktop launcher for it,
Look over these and see they help: 
[https://askubuntu.com/questions/902672/registering-appimage-files-as-a-desktop-app](https://askubuntu.com/questions/902672/registering-appimage-files-as-a-desktop-app)
[https://docs.appimage.org/reference/desktop-integration.html](https://docs.appimage.org/reference/desktop-integration.html)

Hi there, thank you for the info! This was a very helpful first step for me. I created a "Standard Notes.desktop" file, linking to the appimage file and the icon however I'm getting an error: "Failed to execute child process (No such file or directory)". I think it's getting hung up on finding the executable binary file. Probably because, I think, I don't have one of those? I have an AppImage file, so I linked to that instead.

What am I missing?

---

### Post by Dennis N on 2020-11-29
Has the program been working when you double click on the .appimage file?
If you post the .desktop file you made, perhaps an error will be seen.

---

### Post by pupscout on 2020-11-29
> **Dennis N said:**
> Has the program been working when you double click on the .appimage file?
If you post the .desktop file you made, perhaps an error will be seen.

Yes, the program works normally if I just double-click on the .appimage file. This is what I'm using for my .desktop file:

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/media/scout/5b08b33b-1011-4ff8-abbb-f77978ddc8ec/Standard Notes/standard-notes-3.5.11-linux-x86_64.AppImage
Name=Standard Notes
Comment=Standard Notes
Icon=/media/scout/5b08b33b-1011-4ff8-abbb-f77978ddc8ec/Standard Notes/standard-notes-icon.png
```

---

### Post by CelticWarrior on 2020-11-30
The problem is the space in "Standard Notes" and the easiest way to avoid the problem is not to have that space.

---

### Post by pupscout on 2020-11-30
> **CelticWarrior said:**
> The problem is the space in "Standard Notes" and the easiest way to avoid the problem is not to have that space.

Aha, thanks! Removing the space makes the .desktop file work.

However, the underlying program still does not have the "Keep in Dock" option that my other programs have, nor does it appear when I search for it in my app launcher. :(

I'm trying to avoid having to keep a file on my desktop for this program (whether that's an appimage file or a .desktop file doesn't really matter to me), or avoid having to use a terminal or file explorer to navigate to a file just to launch a program. I would much prefer to quickly launch the program from my desktop's dock.

---

### Post by Dennis N on 2020-11-30
Yes, Linux does not like spaces in paths to file locations. 

Does the program's icon appear in the "Show Applicatiions" grid? 

The /media location you are using is for temporary mounting - like USB drives. If you have the program files on a removable drive, that might make a difference in your options. I would move the program and icon files into your home folder. 

I place all AppImages in one folder, ~/appimages.

---

### Post by ActionParsnip on 2020-11-30
You can escape the space by changing
```

Exec=/media/scout/5b08b33b-1011-4ff8-abbb-f77978ddc8ec/Standard Notes/standard-notes-3.5.11-linux-x86_64.AppImage

```
to
```

Exec=/media/scout/5b08b33b-1011-4ff8-abbb-f77978ddc8ec/Standard\ Notes/standard-notes-3.5.11-linux-x86_64.AppImage

```

Note the character after "Standard" ;)

---

### Post by pupscout on 2020-11-30
> **Dennis N said:**
> Yes, Linux does not like spaces in paths to file locations. 

Does the program's icon appear in the "Show Applicatiions" grid? 

The /media location you are using is for temporary mounting - like USB drives. If you have the program files on a removable drive, that might make a difference in your options. I would move the program and icon files into your home folder. 

I place all AppImages in one folder, ~/appimages.

Oh interesting, that is the path to my 1TB internal hard drive where I keep my personal data haha. Maybe I don't have that set up quite properly. Anyway, I've moved the directory where the appimage and icon files are, under my personal dir. (/home/scout in this case)

When I run the updated .desktop file, I still get the same "failed to execute child process" error.

---

### Post by Dennis N on 2020-12-01
Get rid of the top line in your .desktop file. I downloaded the AppImage and made a basic .desktop file to be sure it works. It does. In the dock, the "add to favorites" option is in the right-click menu.  No icon could be found so I just used 'text editor' to get a working icon.
```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/home/dmn/appimages/standard-notes-3.5.11-linux-x86_64.AppImage
Name=Standard Notes
Icon=text-editor

```
See screenshots.

---

