---
title: "Where are my programs?"
date: 2009-01-30
forum: General Help
---

### Post by jan23778 on 2009-01-30
Hi Everyone,

I have a quick question. Before I ask it though, please bear in mind I am still new to Ubuntu and linux in general. I have found that on occasion when I add programs from synaptics or the add/remove program, I cant seem to find where they go. Is there an easy way to find them? I recently added 2 FTP client programs because I am having troubles using Nautilus but I dont know where they are!!

Any help would be appreciated

---

### Post by Neural oD on 2009-01-30
sometimes the best way to start them is from the command line.
Just type in the name of your app - and it should start.
If u want to click to start - just create a launcher - try right clicking on the desktop - the launcher is fairly straight forward

---

### Post by hyper_ch on 2009-01-30
if they are cli programs then you won't get a menu entry for those programs.

---

### Post by oldos2er on 2009-01-30
Synaptic can show you where each file in a package is installed. Right-click on an installed package (with a green box), Properties, Installed Files. Most executables wind up in /usr/bin.

---

### Post by drs305 on 2009-01-30
If you can't find them in the gui menus, you can create a launcher. If you need to know the location of the app, you can type this into a terminal:
```

which <appname>  # Example: which gimp
*returns:*
/usr/bin/gimp

```
Of course, you need to know the exact name of the app in the above example and spelling and case are important. 

If you don't know the exact spelling of the app:
Type "which " and then the first few letters, then hit the tab key twice. All the available possibilities will be displayed.  Example:
```

which ca  # then tab twice
*returns this:*
cabextract    case    calendar   card

```

Once you know the name and path to the run command, you can right click on a panel, "Add to Panel". If you can't find the app after clicking "Application Launcher", you can select "Custom Application Launcher" and insert the start command you found using the previous commands.

---

