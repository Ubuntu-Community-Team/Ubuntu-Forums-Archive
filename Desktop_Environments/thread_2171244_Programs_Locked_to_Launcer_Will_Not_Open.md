---
title: "Programs Locked to Launcer Will Not Open"
date: 2013-08-29
forum: Desktop Environments
---

### Post by jacob5 on 2013-08-29
Hi,

I have noticed that sometimes, when I lock programs to the launcher, they will not open from there. For example, I have recently installed the Eclipse IDE in my home folder, but when I lock the program to the launcher it will not open when I click on the launcher icon. I have to open it from the /eclipse directory. Something similar also happened when I installed IDLE and tried to lock it to the launcher. However, IDLE opens from the launcher fine now, but I am not sure what happened to make it open. That was a long time ago.

Any insight into this would be greatly appreciated. :)

---

### Post by stinkeye on 2013-08-29
Drag the eclipse icon from the dash (not the launcher) into an open gedit window
and look at the Exec= line.

---

### Post by jacob5 on 2013-08-29
> **stinkeye said:**
> Drag the eclipse icon from the dash (not the launcher) into an open gedit window
and look at the Exec= line.

Hi,

Thanks for your reply. I cannot seem to find the Exec= line.

---

### Post by stinkeye on 2013-08-29
Don't use so installed eclipse.(I'm on 13.04)
```
gksudo gedit /usr/share/applications/eclipse.desktop
```
opens the  .desktop file which shows...
```
[Desktop Entry]
Type=Application
Name=Eclipse
Comment=Eclipse Integrated Development Environment
Icon=eclipse
**Exec=eclipse**
Terminal=false
Categories=Development;IDE;Java;
```
Launcher works fine.

If I start eclipse in terminal with **/usr/bin/eclipse** or with the launcher
System monitor shows the start commands full path to be...
```
/usr/lib/eclipse/eclipse
```

Test that in terminal and edit the .desktop file if it works. ...
 ```
Exec=/usr/lib/eclipse/eclipse
```

---

### Post by jacob5 on 2013-08-30
> **stinkeye said:**
> Don't use so installed eclipse.(I'm on 13.04)
```
gksudo gedit /usr/share/applications/eclipse.desktop
```
opens the  .desktop file which shows...
```
[Desktop Entry]
Type=Application
Name=Eclipse
Comment=Eclipse Integrated Development Environment
Icon=eclipse
**Exec=eclipse**
Terminal=false
Categories=Development;IDE;Java;
```
Launcher works fine.

If I start eclipse in terminal with **/usr/bin/eclipse** or with the launcher
System monitor shows the start commands full path to be...
```
/usr/lib/eclipse/eclipse
```

Test that in terminal and edit the .desktop file if it works. ...
 ```
Exec=/usr/lib/eclipse/eclipse
```

Thank you for your reply. When I open the .desktop file it is blank.

---

### Post by stinkeye on 2013-08-30
Just reread your first post and you said you installed eclipse to your home directory so
I doubt you will have a /usr/share/applications/eclipse.desktop file.

I installed the highlighted (see pic) eclipse package in software centre.
which installed the .desktop file.
> [COLOR="#008000"]glen@Raring:~$[/COLOR] **which eclipse**
/usr/bin/eclipse
Does eclipse start by running "eclipse" in terminal?

You can create your own launcher.
Launchers placed in **~/.local/share/applications** override launchers of the same name in **/usr/share/applications**
```
gedit ~/.local/share/applications/eclipse.desktop
```
Copy and paste in...
```
[Desktop Entry]
Type=Application
Name=Eclipse
Comment=Eclipse Integrated Development Environment
Icon=eclipse
Exec=eclipse
Terminal=false
Categories=Development;IDE;Java;
```

You can edit the Exec= line to whatever starts your program in terminal. Use the full path if necessary.
Then search for eclipse in the dash and drag and drop on the launcher 
or 
go to **~/.local/share/applications** in the file browser and drag and drop **eclipse.desktop** to the launcher.
May need to log out/in for the first method.

---

