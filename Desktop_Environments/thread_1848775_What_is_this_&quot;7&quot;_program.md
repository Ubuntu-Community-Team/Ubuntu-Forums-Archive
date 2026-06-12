---
title: "What is this &quot;7&quot; program?"
date: 2011-09-23
forum: Desktop Environments
---

### Post by Acharn on 2011-09-23
I've got a .zip file containing a Windows executable I want to install on Wine. I already installed an earlier version of the program which had a Windows Installer version and Wine installed it as expected (the program is Ares Galaxy, if that matters, but I don't think it does).

My memory isn't what it used to be, but I thought I had downloaded 7Zip Windows version and installed it under Wine, but Wine says it can't find the program and it's not listed in the Wine uninstaller, so I guess I didn't. When I click on the Applications menu and type in "7" it brings up a 7Zip icon, and when I click on that it runs a program that looks like a Windows program running under Wine, but it can't find the zip file on the simulated "C:\" drive. If I type in "7zip" or even "7z" it doesn't show me any icon, indication there isn't any such program installed. When I tried right-clicking on the icon nothing happened -- I was hoping to be able to get a "Properties" display.

OK, the thing is I don't like this program and would like to uninstall it, but I can't find out what the program's real name is. Ubuntu Software Center indicates there is a native 7Zip program (actually p7Zip) and that it is not installed. I tried "sudo /usr/bin/7*" and it did not find anything. How can I track this thing down and get rid of it?

---

### Post by Frogs Hair on 2011-09-23
7 zip is integrated into the file roller program when installed and it is for extracting and compressing files of different formats. The Linux version doesn't have a GUI like the Windows version.  

You should be able to right click the Archive and extract it . The program appears as 7zip in my software center , but you  could look in the Synaptic Package manager to make sure it's gone .

---

### Post by Krytarik on 2011-09-23
I'm quite sure that all Wine-related files are solely in the home directory of the respective user.

Wine menus/launchers/mimetypes are stored in these directories, maybe even more, listed in the order of the directory tree:

~/.config/menus/applications-merged
~/.local/share/applications
~/.local/share/applications/wine
~/.local/share/desktop-directories
~/.local/share/icons
~/.local/share/mime
~/.wine/drive_c/users/Public/Desktop
~/.wine/drive_c/users/Public/Start Menu/Programs
~/.wine/drive_c/users/<USER>/Desktop
~/.wine/drive_c/users/<USER>/Start Menu/Programs

And reg. the actual program directory, are you sure it isn't in here?:

~/.wine/drive_c/Program Files

Greetings.

---

### Post by 3Miro on 2011-09-23
Whenever you have a Linux and Windows programs with same or almost the same functionality, you should use the native Linux program. Wine should be an option only when there are no other options.

While Linux's p7zip doesn't come with a GUI of its own, it integrates with xarchiver and the various file managers. I can create and extract p7zip archives from Thunar with just right-click extract or create archive. Nautilus should be able to do the same.

If you don't have p7zip installed, look it up in the repos.

Uninstalling windows program installed with wine can be tricky. Wine keeps all of its file in .wine (or some other user specified folder), then it puts a shortcut in the Linux menu. Furthermore, depending on how wine is setup, you may have disabled wine's access to anything outside of .wine (while it can be bothersome, it is generally a good idea).

I like to keep separate versions of .wine for each program that I use. Although for something like 7zip, this is quite an overkill.

You can uninstall everything that you have with wine by deleting .wine (Ctr+H in Nautilus to see the hidden folders). This will uninstall 7zip, but it will also zap everything else that you have installed with wine.

What I would do in your shoes is to try Krytarik's folders and find and delete the 7zip entry. This will not uninstall the program, but the program is so small that it shouldn't matter. The install p7zip and use it from within Nautilus.

---

