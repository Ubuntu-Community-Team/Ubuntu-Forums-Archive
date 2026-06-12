---
title: "Changing Kopete's default browser?"
date: 2007-05-09
forum: Desktop Environments
---

### Post by MrNatewood on 2007-05-09
Hello,
I'm using Ubuntu FF, running GNOME and using Kopete for instant messaging.
When I click on a link in Kopete it opens in Konqueror instead of my default browser, Firefox.

It is my assumption that this is because Firefox is only defined as the default for GNOME applications and not KDE applications. However, Kopete&Konqueror are the only KDE application I have installed so I have no KDE control center or any way I know of to change the default browser of KDE.

Is there anyway to change the default browser of KDE from the terminal? Or should I install a package that would allow me to do that? Or any other way you could think of to make Kopete send the links to Firefox?

---

### Post by Jucato on 2007-05-09
Try going to the ~/.kde/share/config/ directory and edit the kdeglobals file. In that file there should be a part like this:

```

[General]
BrowserApplication=

```

Put "firefox" (without the quotes) after the = sign there.

Hope that helps.

---

### Post by hvbakel on 2007-05-09
If you don't feel comfortable editing config files you can also set the default browser through kcontrol:

start menu > run command > type: kcontrol > kde components > default applications > web browser

---

### Post by MrNatewood on 2007-05-10
Have not found both of what you described =\

This is the complete contents of kdeglobals:
```
[$Version]
update_info=kded.upd:kde3.0,mouse_cursor_theme.upd:kde3.4.99,kaccel.upd:kde3.3/r1,socks.upd:kde3.0/r1,klippershortcuts.upd:04112002,kwin.upd:kde3.2Xinerama

[KFileDialog Settings]
Automatically select filename extension=true
Height 1024=220
Height 768=220
LocationCombo Completionmode=5
PathCombo Completionmode=5
Recent URLs=$HOME/.kde/share/apps/kopete/globalidentitiespictures/,/media/windows/
Separate Directories=false
Show Bookmarks=false
Show Preview=false
Show Speedbar=true
Show hidden files=false
Sort by=Name
Sort case insensitively=true
Sort directories first=true
Sort reversed=false
View Style=Simple
Width 1024=700
Width 1280=707

[KKeyDialog Settings]
Dialog Size=512,307

[Paths]
Trash=$HOME/Desktop/Trash/
```
As you see there is no "BrowserApplication="

Nor is there a menu "default applications" in "kde components":

---

### Post by Jucato on 2007-05-10
If it's not there, try adding it.

Although I'm puzzled why you wouldn't have a Default Applications there in KControl.

---

### Post by MrNatewood on 2007-05-10
Well that worked :)
Thanks a bundle.

---

### Post by olafurg on 2008-01-16
> **Jucato said:**
> Try going to the ~/.kde/share/config/ directory and edit the kdeglobals file. In that file there should be a part like this:

```

[General]
BrowserApplication=

```

Put "firefox" (without the quotes) after the = sign there.

Hope that helps.

Thanks alot. That did it for me.

---

### Post by psylem on 2008-01-29
Click on "System Settings" from the start menu, "Default Applications" should also appear in there.

---

### Post by Jucato on 2008-01-29
@psylem: He's not on KDE/Kubuntu so he won't have System Settings installed.

---

### Post by samwyse on 2008-01-29
> **Jucato said:**
> Although I'm puzzled why you wouldn't have a Default Applications there in KControl.

It's a kde-systemsettings module, I tested it by removing the package and then it was gone from kcontrol.

---

