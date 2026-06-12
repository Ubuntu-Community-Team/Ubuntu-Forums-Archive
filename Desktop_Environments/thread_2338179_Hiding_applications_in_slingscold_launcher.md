---
title: "Hiding applications in slingscold launcher"
date: 2016-09-25
forum: Desktop Environments
---

### Post by ald2 on 2016-09-25
Running Ubuntu 14.04.5 LTS and have slingscold launcher.

I'm looking for a way to hide applications that the system uses, but I don't.  

Thank you.

---

### Post by deadflowr on 2016-09-25
Applications are typically stored in the folder /usr/share/applications.
They are stored as .desktop files.

Find the application you want to hide and for ease of editing,
copy the file from the /usr/share/applications folder into your personal applications folder located at ~/.local/share/applications.
Ex:
```
cp /usr/share/applications/some-app.desktop ~/.local/applications/
```

Then open your favorite text editor and open the file
(as .files, files/folder that begin with a dot, are hidden by default for most file managers and text editor, you need to enable any show hidden files settings.)

alternatively to enabling show hidden is to open the text file directly using a terminal command.
Ubuntu's default text editor is gedit, so in context:
```
gedit ~/.local/share/applications/some-app.desktop
```
will open some-app.desktop.

Now in the file add the line
```
NoDisplay=true
```
and save.

You can repeat this for any and all apps you want to hide.

It may require a logout to take affect.

The reason to copy the file is that the files in the /usr/share folder will get overwritten if an update for said package is updated.
But any file in your own applications folder will not, 
and also, the files in your personal folder override the files in the /usr/share folders.
So whatever the setting in the file you set, will be used, regardless of what the settings are in the /usr/share/* files are.

Hope it helps.

---

