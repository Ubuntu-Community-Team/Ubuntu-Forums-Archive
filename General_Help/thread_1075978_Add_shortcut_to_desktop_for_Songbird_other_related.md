---
title: "Add shortcut to desktop for Songbird/ other related apps?"
date: 2009-02-20
forum: General Help
---

### Post by jellylogix on 2009-02-20
I downloaded Songbird, and you can extract the tarball, and then simply click the file called songbird to  open songbird. This is the case for other applications I have as well (BlueJ for example). I was wondering how I can put these files in another folder, and then create a shortcut to run this file when I click on a shortcut on the desktop. 

I would also like to know how I can get this file to run without having to click "run" everytime when it asks if I want to run the program.

By the way, the file is a shell script (application/x-shellscript) if that helps you help me.

Thanks ahead of time.

- Ryan

---

### Post by trlkly on 2009-02-20
Ok. I think I understand you. You've installed these programs to your desktop, and now you want to move them to a different folder, but still keep an icon on the desktop, right?

Your best bet is to create a .desktop file.

Open gedit (Applications > Accessories > Text Editor) or your favorite text editor.

Copy the following into the file:


```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=
Name=Songbird
Icon=

```

Now save that file as ~/Desktop/Songbird.desktop

You've just created a launcher. Right-click and choose properties. In the Launcher tab, add the info you want. Make sure the Command field contains the entire path to the songbird file, eg. /home/trlkly/songbird/songbird

Oh, and you can click on the icon to pick an icon for it. You can use any gif, jpeg, png, or ico on your disk.


All this should do what you want. You shouldn't even have to click run. 

As far as I know, Ubuntu does not have a program that makes launchers. It should, but it doesn't. 

Oh, and if you create a different launcher, be sure to change the Name attribute in the .desktop file.

---

### Post by Yashiro on 2009-02-20
Or just right click. Select Create Launcher. Browse to the file. There's your windows style shortcut done.

As for not running when executed.
the command for you launcher should be, for example 
> /opt/Songbird/songbird

Also make sure you have set the songbird file to be executable by right clicking on it and altering the settings in the permissions tab.

---

### Post by trlkly on 2009-02-20
Huh. I could have sworn that wasn't there the last time I checked. Leave it to me to miss the obvious.

---

### Post by jellylogix on 2009-03-16
Thanks.

This will help me a lot.

---

