---
title: "setting windows-learned shortcuts in Ubuntu - how?"
date: 2008-02-09
forum: Desktop Environments
---

### Post by sindyr on 2008-02-09
Since moving to Ubuntu from windows, would like to set up several shortcuts that are already familiar to me:

Windows-R to give me the run line that Alt-F2 does
Windows-E to give me Nautilus (or maybe Thunar)

I am in the gconf-editor, in apps/metacity/global_keybindings, but can't find the alt-f2 or the nautilus.

And above all, some way where I can double click on the icon in the upper LEFT of a window, and the window will close/terminate.  I want to leave double clicking on the title bar itself as the Maximize/Restore toggle it is now.

Thanks.

---

### Post by sindyr on 2008-02-09
OK I figured out one thing - how to place a wanted command into /apps/metacity/keybinding_commands, and to then link to that from the shortcut area.

What are the command line ways to start or run:

-the alt-f2 program?
-the program called "Search for files..." under the Places menu?

Thanks.

---

### Post by sindyr on 2008-02-09
> **sindyr said:**
> -the program called "Search for files..." under the Places menu?

ok turns out this is equal to "gnome-search-tool" from the run line.

Now all I need is how to launch the alt-f2 program from a command line?

---

### Post by light50 on 2008-02-09
from [https://help.ubuntu.com/community/MappingWindowsKey](https://help.ubuntu.com/community/MappingWindowsKey) :

Create a .xstartup file

We will need to edit your /home/user/.xstartup file. If you have one, edit it (with whatever text editor you work best with). If it does not exist, simply create it. Easiest way to do this is to open Text Editor (under Applications, Accessories) and then save the file as /home/user/.xstartup

Paste the following in the file:

# Make the Windows key a useable mod key:
xmodmap -e "remove mod4 = F13"
xmodmap -e "keycode 115 = Super_L"
xmodmap -e "add mod4 = Super_L"

Note: You can type the three commands directly in a terminal window to test them. If the first command spits out commandline:1: bad remove modifier keysym list (empty), then simply delete it or add a # before it to comment it out.

Source of this code: [WWW] Click Here
Map Keys

In order to create your key shortcuts, you will need to open the Keyboard Shortcuts window from the System / Preferences menu. Click on the shorcut you want to create, then make your key combination. For example, if you want to copy the "Run" dialog box from Windows (Win+R), just click on Show the panel run application dialog, then press WIN+R at the same time.
Common Win Shortcuts

Key
	

Keyboard Shortcuts Name
	

Windows equivalent

Win+R
	

Show the panel run application dialog
	

Run dialog

Win+E
	

Home Folder
	

Windows Explorer (or My Documents)

Win+L
	

Logout
	

Shutdown

Win+F
	

Search
	

Search Files or Folders

Win+M
	

Hide all windows and focus desktop
	

Show Desktop

---

