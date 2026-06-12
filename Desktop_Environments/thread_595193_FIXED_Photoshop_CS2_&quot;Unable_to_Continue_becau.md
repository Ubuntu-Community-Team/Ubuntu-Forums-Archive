---
title: "FIXED Photoshop CS2 &quot;Unable to Continue because of a Hardware or System Error.&quot;"
date: 2007-10-28
forum: Desktop Environments
---

### Post by zergling on 2007-10-28
Hi everyone,
I just made a script that help to prevent the message : 
"Unable to Continue because of a Hardware or System Error."

Just create a new file and open it up with your favorite text editor and copy this:

#!/bin/sh 

cd /home/user_name/.wine/drive_c/windows/profiles/user_name/Application\ Data/Adobe/Photoshop/9.0/Adobe\ Photoshop\ CS2\ Settings/
rm Adobe\ Photoshop\ CS2\ Prefs.psp 

QUICKPARLOCATION="c:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0

close the editor and save it.

To make the file executable use the comand

chmod +x your_file

Please let me know if you have found this script helpful

Have a nice editing :):roll:
Ciao!

---

### Post by Pevichaey5 on 2007-11-04
hi

i suppose it makes photoshop open :D but i have no side panels with the editing tools, but i have all the menu's which i needed access to

how can i get the side bars and stuff back

cheers

---

### Post by SyCo123 on 2008-01-30
tanks for takin the time to write a script to help with this however your script hasn't fixed it, im geting this error message.

```
simon@master:~/Documents$ ./adobehelp 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

```

Are you're still supporting this? Any idea what to try next?

---

### Post by JangMunho on 2008-02-15
Thank you. This script fixed my problem!
But I wonder how you found the solution?

---

### Post by BrownieBoy on 2008-03-14
Installing Winetricks fixed this error message for me.  Type the commands below into a terminal window  to download and install it:

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks corefonts vcrun6

It seems to install some extra Windows fonts.  I found this via a post on another board at:

[http://inertz.org/nightshift/2008/02/13/re-wine-photoshop-cs-2-hardware-error/](http://inertz.org/nightshift/2008/02/13/re-wine-photoshop-cs-2-hardware-error/)

I didn't need to "blow away" my Wine then reinstall it though.  The installation worked against my existing Wine.

Brownie

---

### Post by Malvazar on 2008-04-20
> **zergling said:**
> Hi everyone,
I just made a script that help to prevent the message : 
"Unable to Continue because of a Hardware or System Error."

Just create a new file and open it up with your favorite text editor and copy this:

#!/bin/sh 

cd /home/user_name/.wine/drive_c/windows/profiles/user_name/Application\ Data/Adobe/Photoshop/9.0/Adobe\ Photoshop\ CS2\ Settings/
rm Adobe\ Photoshop\ CS2\ Prefs.psp 

QUICKPARLOCATION="c:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0

close the editor and save it.

To make the file executable use the comand

chmod +x your_file

Please let me know if you have found this script helpful

Have a nice editing :):roll:
Ciao!

Okay I did exactly what you told me to do. I created the text file exactly. Then I typed in the code in terminal with my file name, but it just keeps telling me that there is no such file or directory!? Where did I go wrong?

---

### Post by wclement7 on 2008-04-23
I am assuming you saved the file in a different directory than the terminal is in. I saved my text file to the desktop and ran the command and it did not work, moved it to the home folder and it did.

I then ran the file and it did not work. 
I get the same error as before. I now did both things listed in this thread to fix the problem, and neither worked. Anything else I should try?

---

### Post by wclement7 on 2008-04-23
fixed it! 
feel special now since i am a linux newb :)

i found this link via a google search: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1815](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1815)

on that page there is a "how-to" with a link to a sourceforge page.
download the file and run it with wine. 
All is working now!

---

### Post by tmccleve on 2008-06-09
Very helpful script. Thank you!

---

### Post by jaems-kun on 2008-07-13
Hope this thread isn't too old for me to nag in.

I've tried all the methods suggested in this thread and I still get the same error message.

I have photoshop 8.0, I hope that doesn't change much.  I adjusted the locations in the script and it ran the exe properly, but the error was still the same.  I installed windows fonts with winetricks, reinstalled both photoshop and wine, but the error is the same.

Is there anything else to try?


edit:  apparently I can avoid this error by deleting my settings file every time (shift+ctr+alt while starting pshop), but that's a pain in the ****.  What the heck changes in my settings between the first and second run?


Final edit:  Kay, it works now.  Note for other noobs who stumble upon this fix: install cabextract before blindly copy/pasting winetricks terminal commands.

---

