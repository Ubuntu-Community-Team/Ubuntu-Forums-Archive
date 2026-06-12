---
title: "A drop-down launcher for favorite files"
date: 2009-08-22
forum: Desktop Environments
---

### Post by taslinux on 2009-08-22
If you like a clean, tidy Gnome desktop, you probably don't want it littered with file shortcut icons. Wouldn't it be nice to have a drop-down (or drop-up) file menu in one of the Gnome panels, from which you could select and launch your frequently used documents, spreadsheets, images, etc?

You can build just this kind of launcher menu with your stock-standard Gnome desktop - no extra applets or applications need to be downloaded.

This little bit of Ubuntu DIY is based on the ability of Gnome panel launchers to open *locations* as well as *applications*. The drop-down feature is already in the Drawer applet.

Here's what you do:

1. Right-click on a panel and choose *Add to Panel...*

2. In the *Add to Panel* window, select the Drawer applet, choose *Add*, then *Close* the window.

3. Move the Drawer icon to a handy place on the panel.

4. Right-click on the Drawer icon and choose *Add to Drawer...*

5. In the *Add to Drawer* window, choose *Custom Application Launcher* and choose *Add*.

6. A *Create Launcher* window appears. Here's where you going to choose the favorite file you want to launch.

a. From the *Type* drop-down list, choose *Location*.
b. In the *Name* box, type a shortcut name for the file, e.g. 'Finance'
c. In the *Command* option, click on *Browse* and navigate to the file of interest in the *Choose a File...* window. Highlight the file and choose *Open*.
d. Back in the *Create Launcher* window, you can add a *Comment*, too, e.g. 'Household budget'
e. Choose *OK*.

7. Repeat from step 4 to add another file.

After you've added your favorite files, click on Drawer to open it, and you'll see a stack of icons. Hover your mouse over an icon and two lines of text will appear: the top line is from Name and the bottom line from Comment. Click on the icon and the selected file will open in the default application for that file type.

Now for the tweaks and issues:

1. To preserve the vertical order of file launch icons in Drawer, you need to lock the icons in position by right-clicking each one and choosing *Lock to Panel*.

2. You can have a different icon for each file launcher. Right-click on an icon and choose *Properties*. A *Launcher Properties* window opens. Click on the icon image at top left, and a *Browse Icons* window opens. Icons are displayed from the folder /usr/share/icons/hicolor/scalable/apps/. There are other nice scalable icons in the various folders at /usr/share/icons/gnome/scalable, which you can get to by choosing *Browse...* in the *Browse Icons* window.

To save time, you can create an 'Icons' folder in your home folder, and copy to it the icons you like best. You can preview the installed icons in Ubuntu and do the copying to that new folder using your Nautilus file browser. Cool icons from the Web can be downloaded and put in your Icons folder, too. Navigate to this new Icons folder to choose icons for the launchers in Drawer.

3. Be sure to choose *Location* in step 6a, above. If you leave the choice of *Type* as *Application*, you'll get an error message, because the application doesn't live at the address you specified in 6c.

---

