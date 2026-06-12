---
title: "Wine .doc file association?"
date: 2007-10-22
forum: Desktop Environments
---

### Post by appye on 2007-10-22
I cannot find information on this anywhere.  I want to be able to double-click on a .doc file and have it open up in Microsoft Word, not in Openoffice Writer.  I do have Word working under Wine, and can open .doc files with File>Open.

I know how to change file associations through right click > properties, but the best I can get is for a double-clicked .doc file to launch Word.  This is as far as it gets, however, it does not actually open the file.

Does this need to be scripted somehow?  The wife, who could care less about Linux, is not very happy about this.  Please don't let her badger me into putting Windows on her laptop!

I am currently using the regular Gnome version of Feisty, and am going to install Gutsy perhaps this evening.  Also, If this is something that cannot be done under Gnome, but can be accomplished using KDE, please let me know.

---

### Post by ice60 on 2007-10-22
you could try putting this in the custom command

wine "C:\Program Files\path\to\exe" %f

i've no idea if it will work though :confused:

---

### Post by appye on 2007-10-22
I will give that a try, thanks.  I find it surprising that there aren't more people asking about this.

---

### Post by appye on 2007-10-22
Unfortunately, this did not work.  Any other ideas?

---

### Post by TeaSwigger on 2007-10-23
Wouldn't mind knowing that myself. All I do know in that respect is that one can launch a file using WINE's file manager... but I doubt using that'd cut the mustard. No harm in taking a look, command to open it is winefile.

---

### Post by ice60 on 2007-10-25
you can use nautilus-actions to put things in the right-click menu, i'm not sure if you're saying you can already do that though, so sorry if you can.

but, that command should work with nautilus-actions -
wine "C:\Program Files\path\to\exe" %f

---

### Post by TeaSwigger on 2007-10-25
Looked a bit more into it. No idea how to use it, but wine has a utility called winepath, which translates unix paths to windows paths by use of a -w option. Now if one could have the file manager first send the (unix) file name to winepath and then pipe the output (windows) path as the file name passed to wine [program], seems that would allow one to open files in wine apps from a unix file manager. I don't know how to do that though. Anyone handy with a script or commands?

---

### Post by appye on 2007-10-26
> **ice60 said:**
> you can use nautilus-actions to put things in the right-click menu, i'm not sure if you're saying you can already do that though, so sorry if you can.

but, that command should work with nautilus-actions -
wine "C:\Program Files\path\to\exe" %f

I am able to add things to the right click menu in gnome easily enough, but that does not work any better than double clicking.  This "nautilus-actions" does something different?  Honestly, I am unable to figure out how to associate any kind of file with any windows program running in wine.  It really surprises me that this is not already a feature in wine.  Any wine forums I can post these questions to?  I did not see any at winehq...  

TeaSwigger, I like the scripting idea, now all we need is a bash scripting guru to show us how to do things.  I am a decent batch and VB scripter, but bash is new to me.  I can give it a try.  Let me know if you find anything out.

---

### Post by iulianov on 2007-11-18
Here is the way that I do this:
Create a shell script called 'winword' in '/home/user/bin' with the following line in it:
```
wine "C:\program files\microsoft office\office\winword.exe" `winepath -w "$@"`
```
Make the script executable by typing "chmod +w /home/user/bin/winword" in a terminal.
Then right click on a .doc file and select properties
Click on "Open With" tab
Click "Add"
Click on "Custom Command"
enter the path to the script ( /home/user/bin/winword)
Click "Add"
Click on the radio button in front of "winword" in the list of programs
Click close.

Now all your word documents should open with Microsoft Word
Note: the script can be placed in any directory you like
To do the same for Excel and PowerPoint just replace the winword.exe in the script with the required program.

---

### Post by TeaSwigger on 2007-11-19
Ah I'd lost this thread! I have a link of interest:
[http://ubuntuforums.org/showthread.php?t=565571](http://ubuntuforums.org/showthread.php?t=565571)

This method is working for me to open KeyNote files in KeyNote via wine in Kubuntu by clicking the file in the file manager. I haven't tried this in ubuntu, only kubuntu. The file type is associated to open with the script like so:

```
/home/MYUSER/.wine/scripts/keynote %f
```

I hardly understand a letter of it, but here is the working script as I have it:

```
#!/bin/sh
        rm -f ~/.wine/iprog3 ~/.wine/iprog2 ~/.wine/iprog

        echo ---
        echo Loading $1- into KeyNote.
        echo Warm up them philangies!
        echo ---

        echo -n env WINEPREFIX=/home/MYUSER/.wine WINEDEBUG=-all wine /home/MYUSER/.wine/drive_c/Program\\ Files/KeyNote/keynote.exe\ >> ~/.wine/iprog 

        echo -n "\\042" >> ~/.wine/iprog
        winepath -w "$1" |tr 'c:' 'C:' | tr 'd:' 'D:' >> ~/.wine/iprog  
        echo -n "\\042" >> ~/.wine/iprog

        less ~/.wine/iprog | tr -d '\n'   >> ~/.wine/iprog2

        sh ~/.wine/iprog2

        rm -f ~/.wine/iprog3 ~/.wine/iprog2 ~/.wine/iprog
```

Hope this helps.

---

### Post by gilf on 2007-11-28
I have the same problem, though I set up a workaround that is acceptable for my own wife. 

It isn't a .doc file association, but an easy way to find and open wine/MSWord documents

To make things easier I set up a link to MSWord on the desktop (shortcut). Then went into Word, clicked on Tools, then Options then went to the File Locations tab, and set the Documents directory to:

**Z:\home\*username*\Documents**

In operation, you simply open Word (with the shortcut) then click File/Open, Your whole Ubuntu user's Documents directory is displayed in word. You can open your document easily by clicking on it. 

This doesn't take any more work than going to the titlebar "Places" in Ubuntu, then "Documents" then navigating to a document and clicking on it to open Word because of the .doc association. Actually, it's a better procedure, and it tends to keep people from opening multiple instances. It also makes it easier to open several documents in a single Word session.

This also maintains the OpenOffice .doc association for occasions when you may not want to always open MSWord. In fact my wife doesn't mind using Open Office Writer for documents that don't require "Track Changes" -- she's a copyeditor, and unfortunately OpenOffice's "Change Record" does not work well enoughfor group editing when compared with MSWord. But for other purposes she would like to use Open Office.In fact, if Open Office improved this one feature, she would make the switch. 

I realize this doesn't exactly answer the question, but it may be a handy enough workaround for others to try.

---

### Post by simon_6162 on 2008-01-24
I know this thread is quite old but here is my solution that works as you all seemed to want. I've only tried kde though.

```
#!/bin/bash

#check this path below is pointing to your word executable
EXECUTE_STRING=$HOME"/.wine/drive_c/Program Files/Microsoft Office/OFFICE11/WINWORD.EXE"
#this is what / is mapped to in wine in my case its z:
ROOT_DRIVE_MAPED_TO="z:"
#convert unix path to windows path
newname=${ROOT_DRIVE_MAPED_TO}`echo "$1" | sed 's/\//\\\/g'`

"$EXECUTE_STRING" "$newname"


```

Save the script above to a file called something like wordlaunch and put it in your executable path e.g. /usr/local/bin
then make the script executable 
```
chmod 755 /usr/local/bin/wordlaunch
```

Edit the script so that the executable string var points to your winword.exe file 
Edit the root drive mapped to var so that it matches your wine setup this is how wine finds / 

Then associate .doc files with it and you should be good. all it does is switch the path you get from kde/gnome to a format windows/wine can use. 
you can just rename the file and change the EXECUTE_STRING for ppt and excel.

---

### Post by sql on 2008-01-28
> **simon_6162 said:**
> I know this thread is quite old but here is my solution that works as you all seemed to want. I've only tried kde though.

```
#!/bin/bash

#check this path below is pointing to your word executable
EXECUTE_STRING=$HOME"/.wine/drive_c/Program Files/Microsoft Office/OFFICE11/WINWORD.EXE"
#this is what / is mapped to in wine in my case its z:
ROOT_DRIVE_MAPED_TO="z:"
#convert unix path to windows path
newname=${ROOT_DRIVE_MAPED_TO}`echo "$1" | sed 's/\//\\\/g'`

"$EXECUTE_STRING" "$newname"


```

Save the script above to a file called something like wordlaunch and put it in your executable path e.g. /usr/local/bin
then make the script executable 
```
chmod 755 /usr/local/bin/wordlaunch
```

Edit the script so that the executable string var points to your winword.exe file 
Edit the root drive mapped to var so that it matches your wine setup this is how wine finds / 

Then associate .doc files with it and you should be good. all it does is switch the path you get from kde/gnome to a format windows/wine can use. 
you can just rename the file and change the EXECUTE_STRING for ppt and excel.

i have done as wroted above. and it was succesfull. thank you! :)

---

### Post by fatbuttlarry on 2008-01-29
Don't mean to take any credit away from the nice scripts you've all written, but has anyone tried this?

```
wine start /path/to/file.doc
```

I'm actually looking to do the opposite, ironically.  I'd like all .doc's to open with OpenOffice natively, even if I'm using Wine.  Let me know if anyone's done this easily.  I know its possible, because a good portion of wine (Sound, 3D Graphics) already talk to the native OS.  Cheers!


-Tres

---

### Post by s021677 on 2008-02-17
Thanks iulianov, great help.
However I had to add this:

#!/bin/bash
wine "C:\program files\microsoft office\office11\winword.exe" [COLOR="Red"]"[/COLOR]`winepath -w "$@"`[COLOR="Red"]"[/COLOR]

:)

---

