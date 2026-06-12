---
title: "GEdit formats and Windows Notepad"
date: 2006-08-01
forum: Desktop Environments
---

### Post by fritz_monroe on 2006-08-01
I'm using Gedit to work with text files for a class I'm taking.  I'd be happy to save the files as Unicode, but the instructor insists that we submit all work in straight text that can be opened with Windows Notepad.  The problem is I don't know the format that I should be using.  I've added all the Western character coding, but nothing seems to seamlessly open in Notepad on my Win98 system.

Any suggestions as to how I should be saving these files?  Right now I have to open it with WordPad first and save it from there as text.  I don't want to use that Win98 system at all, so any help would be greatly appreciated.

F_M

---

### Post by 5-HT on 2006-08-02
When you open a file created by Gedit in notepad, is it all one line?
If so, the problem is in the way Windows and Linux treat new lines in ASCII text-files and the following thread might be of some help: [http://ubuntuforums.org/showthread.php?t=224873](http://ubuntuforums.org/showthread.php?t=224873).

An easy fix may be to use NEdit (or vi[m], or any other text editor that supports the feature) and save the files in a dos-friendly format, or to convert text files to such a format using [I]tofrodos.

[/I]Hope this helps.

---

### Post by fritz_monroe on 2006-08-02
I really like GEdit, so don't want to stop using it.  I was hoping to avoid another step to convert.  I know there is a unix2dos app, I'll have to take a look at tofrodos but I'll keep looking as well.  Thanks

---

### Post by 5-HT on 2006-08-02
AFIAK, gedit does not have such ability. I suggested nedit as it's fairly similar to gedit (though a little lighter on resources and has more options).
If you'd like to keep on using gedit, tofrodos (same thing as unix2dos) would be your best bet.

HTH

---

### Post by msandersen on 2006-08-03
The new Gedit does support Python plugins though, so it is possible with some knowledge of Python to make one that either does it on its own, or interfaces with Tofrodos. Maybe you could post a request somewhere.

---

### Post by msandersen on 2006-08-03
Actually, I just had a look at the plugins: 
**Edit -> Preferences -> Plugins tab**
There's a plugin called **External Tools** which can do what you want in combination with ***tofrodos*** or similar. Enable it by clicking the box, highlight the line, then click **Configure Plugin**.
Here you can add 2 new commands in the Tools pane: **todos** and **fromdos** (assuming Tofrodos is installed).

todos: 
Description: Convert text to Windows format
Command: todos
Input: Corrent document
Output: Replace current document

fromdos: 
Description: Convert DOS text format to UNIX format
Command: fromdos
Input: Corrent document
Output: Replace current document

Done. Close the Config windows, and the two commands will appear under Tools in Gedit.
Actually I think Gedit converts Windows format on it's own, so you may not need **fromdos**.  
I haven't tested it in Windows Notepad yet.

---

### Post by 5-HT on 2006-08-03
[quote=msandersen]Actually, I just had a look at the plugins: 
**Edit -> Preferences -> Plugins tab**
There's a plugin calle **External Tools** which can do what you want in combination with ***tofrodos*** or similar. [/quote]

Nice find! :)

[quote=msandersen] I think Gedit converts Windows format on it's own, so you may not need **fromdos**.  [/quote]

+1. Gedit appears to open text files with CRLF line terminators created in windows just fine for me.

---

### Post by msandersen on 2006-08-03
Gedit beats the hell out of NotePad. But then, it doesn't appear they've done anything with it since they made it. A bit like that shitty paint program or to an extent Windows Explorer. Personally, unless you're on very old hardware, I cannot understand why anyone would choose to install Windows 98. Maybe if you were given a secondhand computer without an OS, and you had nothing else. I suppose if you play some very old DOS games. I've got DOSbox for that, though.
Gnome has been moving away from all the 'G'-named apps and coming up with some better names, like Epiphany etc, so hopefully we'll see some easier to pronounce sexy names in future from both Gnome *and* KDE.
Gnome *could* play a pun and call it *Geddit* :grin:

---

### Post by fritz_monroe on 2006-08-03
The Win98 machine is my old computer.  About the **only** thing that I use it for now is to open the text file in WordPad and save it as a text file that the instructor can open in NotePad.

Thanks for the plugin info, I'll set up the plugin.

F_M

---

### Post by msandersen on 2006-08-04
How pathetic is that, having a whole operating system just to run WordPad!!

Is it some sort of progamming or other Tech course, and if so, surely the instructor should be savvy enough to know of WordPad versus NotePad! He'd have the same problem from Mac users, surely.

---

### Post by msandersen on 2006-08-04
I just made some tests on an ntfs partition and booted into Windows to test the before and after in Notepad. Works great.

---

