---
title: "Confused handlling of file associations"
date: 2017-02-04
forum: Desktop Environments
---

### Post by pwabrahams on 2017-02-04
I'm running Kubuntu 14.04 and also Dropbox.  I encountered what seemed to be a problem with Dropbox but really is a problem with how Unbuntu handles file associations.

The precipitating event was when I used the Dropbox icon at the bottom of the screen (the taskbar, perhaps?) to open the Dropbox folder.  It immediately opened *the easytag program*!  After poking around I discovered someone had had a similar problem, not involving Dropbox, with audacity being inappropriately invoked to view a directory.

My understanding of these matters is fuzzy, but not quite so fuzzy that I couldn't fix my specific problem myself.  The question at hand is, "given a file type (which might be a directory), what is the correct program to open it?"  The obvious answer would be to look in System Settings/File Associations.  But there's another bunch of settings that also come into play, and are not acccessible via System Settings: the ones in **.local/share/applications/mimeapps.list**.  These are manipulated with the program **mimeopen** or other similar programs.  By modifying that file I was able to fix the problem and get Dropbox to invoke **Dolphin** rather than **easytag**.

So there seem to be two hands on the same control knob.  That is not a good situation and ought to be fixed.

---

### Post by TheFu on 2017-02-05
I don't know the answer, but perhaps a little background can help?

Linux doesn't have file associations.  The CLI/shell doesn't have file associations.  Bash has an extension called "bash-completion" which does look at extensions trying to help make the shell more efficient to use.  None of this help you now, except to aid with troubleshooting.

Anything that appears as a "file association" is due to a GUI specific thing. GUIs are not the OS, they are just an interface, which can be swapped in about 3 minutes.

So, first is to determine which program is actually causing the issue.  It is likely some GUI tool and since you are running KDE, it probably begins with a "k" in the process name.  If you don't know the actual name of the program, the best way to determine that is to run it and in another window open a terminal and look at the process table. It is likely to be near the **top** (using most of the CPU) relative to other.  Top is the normal program for that.  Just cause the program to do something, even a refresh and it should move to the top of the list inside "top."

Different GUI programs will have different "file associations" - or things that appear to be file associations.  Linux doesn't normally look at file extensions, it uses something called a "magic number" - found in the header of every file.  Use the "**file**" program to see those.  I realize this can be confusing for someone coming for other OSes. [http://www.linfo.org/magic_number.html](http://www.linfo.org/magic_number.html) explains more.

A DE (desktop environment) might have a way to globally control which magic numbers open which files.  Part of the confusion  is that there are 
* magic numbers
* extensions
* mime-types
All three don't need to be consistent, which is confusing because different programs use different methods. IMHO, mime-types are used by web browsers and GUI email programs, but almost nobody else. Extensions are used by programs that were written by people coming from MS-Windows.  Extensions are handle for humans too. ;)  Magic numbers have been used by Unix systems for over 45 years.

Some DEs use XDG ... as a way to control how data files are sent to specific programs.  There are helper programs like 
```
xdg-desktop-icon          xdg-mime                  xdg-user-dir
xdg-desktop-menu          xdg-open                  xdg-user-dirs-gtk-update
xdg-email                 xdg-screensaver           xdg-user-dirs-update
xdg-icon-resource         xdg-settings              
```

These have a way to set and query the specific settings.  I'm not on KDE, so they might use different tools.  The xdg-mime and xdg-settings tools appear to have some control about this stuff.

Anyway, none of this is a solution, but might be helpful in finding where the issue lies and how to solve it.  Also, don't forget that file types can also be system-wide - those settings would be in /etc/ or /usr/local/ somewhere.

Sorry I can't help.  Did a google with KDE and found this: [https://askubuntu.com/questions/788043/where-to-change-how-xdg-open-opens-urls-sync-with-kde-open](https://askubuntu.com/questions/788043/where-to-change-how-xdg-open-opens-urls-sync-with-kde-open) - don't know if it helps or not.

---

### Post by pwabrahams on 2017-02-05
Thanks to The Fu for lots of useful information.  The context here is apparent misbehavior by a program (Dropbox) I didn't write.  I naturally expected that "Open Dropbox Folder" would do just that.  I had to figure out what mistake Dropbox was likely making to see if I could counteract it. 

It appears that Dropbox uses XDG to decide what program to use in order to display the Dropbox folder.  What confuses the issue is that at the user level as indicated by the File Associations section of Systems Setting,  for KDE and hence Kubuntu, file extensions are what counts.   A Kubuntu user has no way of knowing that some programs like Dropbox use the XDG values, while others are guided by System Settings.  In fact, until I ran into this problem I didn't even know that XDG existed.  Had I understood all of this I could have used **xdg-mime** to fix the problem.  An extra complication is that a directory isn't obviously a file type, but is described by *inode/directory*.

There must be a lesson here to be learned, but I don't know what it is.

---

### Post by TheFu on 2017-02-06
> **pwabrahams said:**
>  There must be a lesson here to be learned, but I don't know what it is.

Programs created and maintained by thousands of unrelated people around the world will behave differently and have different expectations as to what the "right way" to do anything is.

Oddly, something similar happens with programs created by a single company, just over different periods of time, dependent on the most-used interface.  MS-Windows doesn't provide the same interfaces. Which works or not is dependent on whether you use the shell or GUI.  For example, "libraries" only work if you use a GUI on Windows, but not the file system.

---

