---
title: "Unity &quot;Keep in Launcher&quot; stores files...where?"
date: 2012-01-06
forum: Desktop Environments
---

### Post by gamblor01 on 2012-01-06
I'm just trying to figure out where Unity stores the .desktop files when you have an application running in the launcher and then right-click and execute "Keep in Launcher".  I assumed it would go to ~/.local/share/applications but it does not.  I even checked /usr/share/applications but the .desktop file does not exist there either (which is no surprise since my user cannot write files there unless I sudo).  So where in the heck is the file?  It must be on disk somewhere (as opposed to memory) because the entry is persistent after a reboot.

Yes, I know that I can manually create .desktop files and drag them into the launcher (I have done it many times), I'm just curious where Unity puts the files that are saved using the "Keep in Launcher" icon.  Anybody know?

---

### Post by mc4man on 2012-01-06
It doesn't 'put' them anywhere, a list is maintained in gsettings, usually <whatever>.desktop for .desktops, (apps) in /usr/share/applications  & full path to <whatever>.desktop for .desktops installed & or stored by you elsewhere.

To see current list run 
```
gsettings get com.canonical.Unity.Launcher favorites
```

---

### Post by gamblor01 on 2012-01-09
> **mc4man said:**
> It doesn't 'put' them anywhere, a list is maintained in gsettings, usually <whatever>.desktop for .desktops, (apps) in /usr/share/applications  & full path to <whatever>.desktop for .desktops installed & or stored by you elsewhere.

To see current list run 
```
gsettings get com.canonical.Unity.Launcher favorites
```

Thanks.  This seems to work for everything except Java programs.  I run a Java program from the terminal and that causes it to put an icon into the launcher.  So then I just right-click on that and click "Keep in launcher" and it stays there.  When I run the command

```
gsettings get com.canonical.Unity.Launcher favorites
```


it does not show any new entry for the launcher that I just created.  This appears to be caused by the following bug:

[https://bugs.launchpad.net/unity/+bug/757991](https://bugs.launchpad.net/unity/+bug/757991)


In other words, it is supposed to show the new .desktop file in the favorites list, but fails to do so due to this bug.  If I pin another application that is NOT a Java application (for example, calculator) then I do see the new entry (gcalctool.desktop) and it works fine.  Since gcalctool.desktop has no preceding path it must assume that it resides in /usr/share/applications I guess.


I am trying to pin jprofiler (which is a Java application) to my launchbar.  Ultimately what I wound up doing was just creating my own .desktop file for it, using xprop to determine the WM class, and assigning it appropriately in the .desktop file so that everything works.

The only difference is, I have to supply an icon to it, so I just found one that works and set it.  However, when I start jprofiler from the command line, there is an icon that appears in the launcher for it.  I was curious where it was storing that icon (in memory somewhere?).  When I click to keep it in the launcher it maintains that icon, but of course the entry doesn't work due to the above bug.  I thought that if I could see where it writes the .desktop file, then I could see which icon file it is referencing but apparently the .desktop file doesn't exist!

---

