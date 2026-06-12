---
title: "How to add items to main menu of LXDE?"
date: 2008-08-21
forum: Desktop Environments
---

### Post by jittopjose on 2008-08-21
hello friends,
i installed lxde on top of Ubuntu hardy. lxde provides a default main menu. but calculator is missing from the list. there is an edit menu option on right clicking main manu icon. but its disabled. i dont know how to add items to menu. presently i use gcalctools command in terminal for invoking calculator.
anybody have any idea about this?
thanks,
jittos....

---

### Post by jolx on 2008-08-21
i would also like to this  :-k

---

### Post by corvuscorux on 2008-08-21
I think this would be a very useful piece of information:  How to customize (add and remove applications/features) from the LXDE menu.

---

### Post by cmittle on 2008-08-26
I have two answers for you.  

1.  To add a menu item using the terminal or whichever file browser you like navigate to /usr/share/applications/.  Here you will find all kinds of files that end with .desktop.  If you want to add a new program copy this file and name it newprogramname.desktop.  Open this file and near the bottom it should contain something like this:
Exec=gcalctool
Icon=accessories-calculator
OnlyShowIn=GNOME; XFCE
Type=Application
etc...

The Exec says what command or file should be executed.
The Icon says what the icon should be.  I'm not familiar with the acceptable typed names like above, but you can make a .png and point to that file location using Icon=/location/of/file/for/icon.png

Now for the second answer; the gcalctool.desktop file has an option OnlyShowIn=GNOME; XFCE.  If you comment this out (change to ##OnlyShowIn...) it will now show up on your LXDE accessories menu.


Cory

---

### Post by eriqjaffe on 2008-08-26
Just as a side note, be aware that you need to be root to write to /usr/share/applications - PCManFM has an option to open the current directory as root.  Alternately, you can use run "gksu pcmanfm" to launch PCManFM as root in the first place.

---

### Post by cile87 on 2011-04-22
Hi all. I created a project called lxmed on [https://sourceforge.net/projects/lxmed/](https://sourceforge.net/projects/lxmed/) intended for this use. The work is still in beta, but you can try and download this gui tool for customizing your main menu under LXDE.

---

### Post by cogitordi on 2011-07-02
> **cile87 said:**
> Hi all. I created a project called lxmed on [https://sourceforge.net/projects/lxmed/](https://sourceforge.net/projects/lxmed/) intended for this use. The work is still in beta, but you can try and download this gui tool for customizing your main menu under LXDE.

Thanks for creating this utility. I have just used it and it works well.

---

### Post by cdaringe on 2012-02-20
cyle87: i also downloaded your app.  Install was quick and easy, and i had my apps added in no time.  Thank you!

---

### Post by cdaringe on 2012-02-20
cile87*, my apologies

---

### Post by rbaleksandar on 2012-07-21
From: [http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu)

Menu entries are stored in **~/.local/share/applications** or **/usr/share/applications** (in my case it was the first one only). A menu entry is simply a text file with the extension **.desktop**. The basic structure of an entry is:

```

[Desktop Entry]
Encoding=<used encoding for example UTF-8>
Exec=<path of a binary or script used to start the programm>
Icon=<path to the icon for the entry for example PNG>
Type=<type for example Application>
Terminal=<true|false to start in terminal>
Name=<displayed name in the menu>
GenericName=<description of the entry>
StartupNotify=<true|false for startup notification>
Categories=<category>

```

The given example:

```

[Desktop Entry]
Encoding=UTF-8
Exec=warsow
Icon=/home/USER/my/icons/wsw-icon_80x80.png
Type=Application
Terminal=false
Name=Warsow
GenericName=warsow
StartupNotify=false
Categories=Game

```

I tried to use **xmp** for an icon but so far only PNG has worked out. Notice also that category's name might be different from what you see in the menu. A vivid exception is the category **Programming**, which is actually **Development** in the desktop entry (found this out while trying to add Eclipse (not from the repositories) and it always landed either in the nothingness or in **Others**).

The wiki also states that root privileges are needed but this only applies, if you are editing the desktop entries in **/usr**.

Although I like the idea behind the **LXMED**-tool, I don't like the fact that it is written in Java. Not all people have Java installed (for some reason). Ncurses and/or GTK+ (lxde is using GTK+ so it's already there) interface would be much better.

---

