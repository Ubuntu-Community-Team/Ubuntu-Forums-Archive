---
title: "Problems editing Applications Menu in Gnome/Edgy"
date: 2006-12-21
forum: Desktop Environments
---

### Post by ftmichael on 2006-12-21
I'm running Ubuntu Edgy.  I installed some games (woo Codebreaker!) that I can run through the terminal, but would like to have them in my Applications menu under Games with the others.  I right-click on Applications and go into Edit Menus, but it will not allow me to add anything new; I can only uncheck boxes to remove things that are already there.  (It also won't let me change any icons, which is another frustration.)  There is no File menu - there is no menu but Help - so I can't go to File-->New Entry or whatever, which is what I've seen advised in a few other threads.  Using Applications-->Add/Remove obviously doesn't give me what I need.  And there is no System-->Preferences-->Menu Layout, which I've also seen advised in other threads.  There's just Menus & Toolbars, which isn't what I need at all.  apt-get says I have the newest version of **gnome-app-install**.

Thoughts?

Michael

---

### Post by bapoumba on 2006-12-22
Hi,
have you installed **gnome-app-install** ?

---

### Post by ftmichael on 2006-12-22
Yep, I just tried to install it with apt-get and it says I already have the newest version.

Michael

---

### Post by bapoumba on 2006-12-22
System > Preferences > Menu Layout ;)

---

### Post by ftmichael on 2006-12-23
There is no Menu Layout in my System-->Preferences.

Michael

---

### Post by mechanic on 2006-12-23
> **ftmichael said:**
> There is no Menu Layout in my System-->Preferences.

Michael
Hmmm, there is in mine but it doesn't do anything - or rather a box appears in the lower panel for a second or so "trying to start menu layout" then closes with no error messages visible.

Regds, m.

---

### Post by bapoumba on 2006-12-25
Are you running xgl and Co ? There are some problems with the menus :/

---

### Post by ftmichael on 2006-12-26
I don't think so; not if it's part of the Beryl set-up.  I don't have that.

How can I double-check that I don't have it?  I'm still relatively new to working with the terminal.

Michael

---

### Post by mannheim on 2006-12-26
The application used for editing the gnome menus is called "alacarte". You could see if it is installed by trying to run it using Alt-F2 and typing "alacarte" (or enter "alacarte" in the terminal).

It *should* appear (as discussed above) as System-->Preferences-->Menu Layout. If it's not there, maybe you could reinstall it with
```
sudo apt-get install --reinstall alacarte
```
but I don't know.

---

### Post by mrashley on 2006-12-26
When I try to run alacarte this is my error. I have reinstalled alacarte and gnome-app-install.

```
~$ alacarte 
ImportError: could not import pango
ImportError: could not import pango
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in ?
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.4/site-packages/Alacarte/MainWindow.py", line 19, in ?
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
ImportError: cannot import name Widget from gtk

```

Any clues what might be wrong?

---

### Post by ftmichael on 2006-12-27
alacarte was indeed not installed.  I did the reinstall per your instructions and now have Menu Layout!  There's still a problem, though: it won't let me change icons for folders.  It changes it when I tell it to, then immediately changes it back.

Michael

---

### Post by bapoumba on 2006-12-28
Hi, this may be your theme. Have you tried when using default Human theme ?

---

### Post by ftmichael on 2006-12-29
I haven't, but I'm just using Clearlooks ... that shouldn't be causing issues, I'd think.

Michael

---

### Post by bapoumba on 2006-12-29
[http://www.ubuntuforums.org/showthread.php?p=1189203]("http://www.ubuntuforums.org/showthread.php?p=1189203")
Part 3 tells you how to change icon sets or icons for a single folder (right click on folder).
Is that what you are trying to do ?

---

### Post by ftmichael on 2006-12-31
No; I'm not trying to change the icon theme.  I have subfolders in the folders in the Applications menu; their icon is a plain folder.  (This is regardless of the theme; it's just that theme's equivalent of the same thing.)  The applications themselves all have nice icons.  In Dapper, I could assign a nice icon from /usr/share/pixmaps/ (or elsewhere, if I wanted) to any application *or folder/subfolder*.  It still lets me change the icons for applications to whatever I want, but does not accept the changes when I try to do that for the subfolders.

Michael

---

