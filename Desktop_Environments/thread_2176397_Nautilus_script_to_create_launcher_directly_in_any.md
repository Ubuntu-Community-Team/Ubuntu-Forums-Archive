---
title: "Nautilus script to create launcher directly in any folder in Ubuntu 12.04"
date: 2013-09-24
forum: Desktop Environments
---

### Post by stevecook on 2013-09-24
Steve Cook calling. 

Although I am, overall, very happy with Ubuntu, one thing that has bugged me (with the Unity interface in particular) is the issue with generating shortcuts/launchers. Pre-Unity, this could only be done on the desktop (you could then copy and paste it to a location of choice). But, since Unity, even this feature has been disabled. To fix this, I have included instructions for generating a bash script, below, that can then be acessed by a mouse right-click on the desktop, in any folder on the desktop and anywhere within the home folder and will generate a shortcut or launcher in that location. In other words, it's not just restricted to creating them on the desktop as with pre-Unity versions of Ubuntu.
[B]
I should state, here, that whilst the following solution was implemented in Ubuntu  12.04 using the Classic Gnome interface, i have since checked it out with 12.04-Unity and it works equally well in that interface as well. I should think it will also work in all previous versions of entirely Gnome-based Ubuntu as well.[/B]

-------------------------------------------------------------------------

1) Open up a simple text editor like *"Gedit" *or *"Text Editor"*. In the Gnome interface, it's usually in the "Accessories" menu.

Type the following into it:

**gnome-desktop-item-edit ./ --create-new**[I]

The command, above is what is needed to open a launcher dialog box.
[/I]
Save the text file as "launcher.sh" to your home folder. We use the "sh" extension to tell Ubuntu this is a bash script.



2) Open up a terminal. Again, this is usually found in the "accessories" menu in the Gnome interface. The terminal will, by default, open in your home folder. If you type "ls" you should see a list of all of the files and folders in your home folder. If you saved your "launcher.sh" file to your home folder as instructed, you will now see it listed in your terminal.

Type the following into your terminal and press the enter key:

**chmod +x launcher.sh**

The above command makes the "launcher.sh" bash script executable.

Close the terminal by typing "exit" and pressing the Enter key



3) Open up the standard GUI home folder, where you should br able to see "launcher.sh" file. Right click your mouse on the file and choose "cut" (or "copy" if you wish to keep a second copy of the "launcher.sh" file for safe keeping)

On the menu, while still in your home folder, choose "View/Hidden files"

You will now see a series of folders and/or files that were previously hidden. They are the ones prefixed by a ".". One of them will be called ".gnome2". Go into that folder. Inside there is another folder called "nautilus-scripts". Go into that folder. now right click your mouse and choose "paste". A copy of the "launcher.sh" file is now in that folder.

Close the GUI file manager.

----------------------------------------------------------------------

Now, whenever you are on the Desktop, inside a folder on the Desktop or anywhere in your home folder you should be able to right click your mouse and find an option called "scripts". If you choose the sub-menu of "scripts", you will find that one of the sub-menu options is called "launcher.sh". If you choose that, it will give you a dialog box allowing you to fill in the relevant details of the application you wish to launch or folder location on you wish to shortcut to.

If you are having difficulty in working out the correct command to put in the launcher dialog box for a given application, one solution is to do the following:

Right click your gnome menu and select the "edit menu" option. Inside there you can navigate to the application menu item in question and double click it. A dialog box will open that includes the command used to launch the application. If you copy this and use it in your launcher dialog box in the appropriate command field, this will be the correct command.

There is one qualification to the above:

You won't be able to use the above launcher script in a system folder without some fiddling about with sudo-permisions in the system "visudo" file. I am not going to go into how to do that here unless asked because, in the hands of a beginner, messing about with the "visudo" file can completely knacker your system (I know cos I've done precisely that before). But, it should never really be necessary to create launchers in system folders anyway. The only places you'll ever really want or need them is directly on your desktop, inside folders on your desktop or somewhere inside your home folder. For any of the above locations, this solution works fine.

---

### Post by deadflowr on 2013-09-25
Sidenote, the removal of the launcher option is a gnome3 design feature and has nothing to do with Unity.
Unity just uses what the gnome3 packages gives it.

That said, with unity if you want a launcher on the desktop, then change the placement option from ./ to ~/Desktop.

---

### Post by stevecook on 2013-09-25
> **deadflowr said:**
> Sidenote, the removal of the launcher option is a gnome3 design feature and has nothing to do with Unity.
Unity just uses what the gnome3 packages gives it.

That said, with unity if you want a launcher on the desktop, then change the placement option from ./ to ~/Desktop.

The Unity developers could have re-implemented that feature in the Unity interface, though. In other words, irrespective of the Gnome functionality, the lack of a simple launcher facility in Unity is clearly a design policy choice by the Unity developers and a poor one, in my judgement.

I have just re-checked Unity and, the Nautilus script, I am happy to say, works in Unity a well as in Gnome. Also, as with Gnome, you don't need to replace "./" with a specific path in the bash-script I have provided because "./" simply means the *current directory.* For example, if you are on the Desktop when you pull up this script with the mouse right-click, the current directory *is* the Desktop. Thus, the launcher will appear on the Desktop when the dialog box has been completed. In other words, the advantage of this script using "./" instead of a specific path is that "./" is *non-contextually applicable*. Wherever you are (in your home folder or the Desktop), if you activate the "launcher.sh" script with a mouse right-click and then fill in the launcher dialog box, the launcher will appear in *that* location.

---

### Post by hamiljf on 2014-05-01
This is something that has caused much grief to many and really should be implemented in some way, some where, in Unity.  The above description is excellent, but there are a couple of additional points to make.
First, check out [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html) for details on the permitted and/or required contents of the .desktop file (if there is a later version of this standard, would someone please post a reference).
Second, note the path= keyword: something that is not set up in the gnome utility and I have found essential.
Finally, note that copying a shortcut to the launcher seems to use symbolic link: do not delete the source file.  There also seem to be problems with copying the shortcut to /usr/share/applications.  On the desktop, executable permission seems to be required.  In /usr/share/applications it seems not to be required.  More research is needed on this (using 14.04).

---

