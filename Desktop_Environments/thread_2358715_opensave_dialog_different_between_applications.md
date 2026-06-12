---
title: "open/save dialog different between applications"
date: 2017-04-16
forum: Desktop Environments
---

### Post by kellyvotrenom on 2017-04-16
New install of Lubuntu and I am confused as to why the file manager looks and acts differently in various applications/ programs. This is for my computer at work made from various parts and it's working great except for the FM situation

The default file manager appears to be pcmanfm.  But when I try to save something in qpdfview or libre calc, for instance, the file manager UI looks completely different.  My bookmarks are missing, the usual home folders are not there either.  I have to navigate up to the root folder, open the media folder, open the user, open the drive, navigate thru the folders and finally save it to the proper location.  The desktop file manager has shortcuts to my most used folders to prevent me from having to do all this searching.  I have spent a lot of time googling for info but I am not certain what to ask.  Is there another file manager taking over from the desktop FM?  Is it due to the way the app interfaces with the FM? Would installing another FM (like Nemo) resolve this?

I have tried different desktops and the results are the same.  I have installed over a dozen various distros the past few years and, while I seem to remember encountering this once before, I don't remember how I solved it.

The machine I was using previous to this had LXLE installed and all the FM UIs looked the same, I have Xubuntu with Cinnamon desktop at home with Nemo and all the UIs are the same and have Peppermint installed on another machine at work and the FM UI looks uniform on it as well.  I have Debian installed on a backup computer at home, all the FM interfaces look the same.

I have troubleshot plenty of much more complicated Linux problems, but this one has me confused - mostly because I can't even figure out exactly what's happening.  If somebody could just explain what I am seeing, I could resolve the problem.

Thanks

Mark Springer

---

### Post by howefield on 2017-04-16
Perhaps it would help others to help you if you could screenshot the file manager in the different guises it takes ?

---

### Post by Dennis N on 2017-04-16
Different save dialogs appearance are determined by the toolkit the application uses (gtk2, gtk3, qt, etc). The dialogs aren't provided by the file manager. 

A few examples from Lubuntu 17.04:

**gtk2**:  leafpad, gimp, geany
**gtk3**:  mousepad (a different save dialog; not default app in Lubuntu) 
**qt5**:    qpdfview (a different save dialog; not default app in Lubuntu) 

libreoffice: not gtk, can use a plugin for gnome, kde or other integration; not default app in Lubuntu

My bookmarks are showing in the sidepane of both the gtk2 and gtk3 versions of the save file dialog in Lubuntu 17.04, as well as in the file manager.

---

### Post by kellyvotrenom on 2017-04-16
I will post some screenshots tomorrow after I grab them from the work computer.  However, the term I was looking for was "open/save dialog".  Thanks for that! So yes, what I mean is the open/save dialogs are not the same

I think I get the graphics toolkit reason, however why does my home computer not suffer from the same issue?  I use pretty much the same apps at home and work so I would expect to see the same behaviour.

Thanks again

---

### Post by vasa1 on 2017-04-16
OP, I've edited the title of the thread to reflect the issue involved. If you want to have something else, you can edit the title by using Edit > Go Advanced.

---

### Post by kellyvotrenom on 2017-04-18
I took some screenshots of the various applications I am using.  While all the File Open Save Dialogs are not the same, some are missing most of the locations in the sidebar.

After more reading, I think there is a fix by redirecting the gtk bookmarks but I may be way off the mark.

I have attached the screenshots.  Again, if anyone can point me in the right direction it would be much appreciated.

---

### Post by Dennis N on 2017-04-18
#1 is typical for gtk3 apps.
#2 is typical for gtk2 apps.
#3 probably can be improved. This is Libre Office default. Install the package **libreoffice-gtk3** and your dialog will be the same as #1. It will improve the tool bar appearance as well.
#4 is the PCManFM window, not a save dialog. What you see here depends on the 'Widget' theme selected in Preferences > Customized Look and Feel. I suggest Lubuntu Default or Lubuntu dark panel (if you have a dark panel).
#5 is qt5 dialog. There was a way to configure qt to be the same or similar to gtk. I will look and see if I still have that somewhere.

---

### Post by kellyvotrenom on 2017-04-18
Thanks for your reply and advice.  I forwarded your reply to my work computer and will implement the libreoffice-gtk3 package tomorrow.  I also found this post about Qt apps under Gkt. Perhaps this is what you were thinking of?

[https://askubuntu.com/questions/51166/how-to-make-qt-programs-look-good-under-xfce](https://askubuntu.com/questions/51166/how-to-make-qt-programs-look-good-under-xfce)

---

### Post by Dennis N on 2017-04-19
> **kellyvotrenom said:**
> Thanks for your reply and advice.  I forwarded your reply to my work computer and will implement the libreoffice-gtk3 package tomorrow.  I also found this post about Qt apps under Gkt. Perhaps this is what you were thinking of?

[https://askubuntu.com/questions/51166/how-to-make-qt-programs-look-good-under-xfce](https://askubuntu.com/questions/51166/how-to-make-qt-programs-look-good-under-xfce)

I looked at my Lubuntu 14.04 where that was installed. Then, it was named **qt4-qtconfig**. It is probably the same package as in the askubuntu question - just a newer version. That utility was for qt4. qt5 apparently works differently, and there is no equivalent tool. You can read all about this here if you want:

[https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications](https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications)

I think you will be happy with the appearance of Libre Office after that libreoffice-gtk3 package is installed. It looks pretty bad without it. Be sure to install it before starting Libre Office.

Eventually, as gtk3 becomes predominant, some of the inconsistent appearance we see will go away. Other things in the design will not. Gnome likes a certain style, others do not.

---

### Post by &amp;KyT$0P# on 2017-04-19
> **Dennis N said:**
> qt5 apparently works differently, and there is no equivalent tool.
qt5ct.  It's not in the standard repositories though, and it requires a little manual setup.

For Ubuntu 17.04 I think you would need to compile qt5ct yourself from [source]("https://sourceforge.net/projects/qt5ct/files/").

---

### Post by kellyvotrenom on 2017-04-19
Installing **libreoffice-gtk3 **solved the libre- office open save dialog problem (and made it look a whole lot better!) Installing **libqt5libqgtk2 **(from this post [https://askubuntu.com/questions/706528/qt-apps-stopped-inheriting-gtk-themes](https://askubuntu.com/questions/706528/qt-apps-stopped-inheriting-gtk-themes)) solved the qpdfview open save dialog problem. While there are still some inconsistencies in the overall look, they all function the same now.

Thanks for all your help.  I will mark this post as solved

---

