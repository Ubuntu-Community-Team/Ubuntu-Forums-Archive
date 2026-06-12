---
title: "OpenOffice spreadhsheet to palm"
date: 2005-09-29
forum: Desktop Environments
---

### Post by rosslaird on 2005-09-29
This shouldn't be as difficult as I've found it to be. Actually, I've found it to be impossible so far:

I want to copy an OpenOffice spreadsheet to my palm and read the document in DocumentsToGo (version 5). How hard can that be?

OO doesn't save in Palm doc format, but Abiword does. However, Abiword crashes when I try to import and modify the spreadsheet file (as a table). I can also convert the file to a palm doc file using doc2pdb or whatever the script is called, but I don't know if the resulting file will be recognized or work as a spreadsheet on my palm. I have not tried copying a file (either pdb or xls) across directly, and I don't want to try that until I have a decent certainty that it won't mess anything up on the device.

I believe that more recent versions of DocsToGo and QuickOffice can read/write MS excel files directly, but those apps are not installable in Linux (they come as Windows exe installers, not prc files).

Suggestions are welcome.

Ross

---

### Post by Carandol on 2006-11-28
I've found it's possible to install DocsToGo (at least, version 6) using Wine (you need the latest version from the Wine repositories, not the one in the Ubuntu depositories). The DocsToGo software for Windows won't work, but you do end up with the .prc files extracted and therefore installable on your Palm.

Now do you have any tips for converting files produced by WordToGo into OOo files? OOo doesn't seem to want to read them, though it will read .pdb files produced by simpler Palm text editors.

---

### Post by tech-quilla on 2006-11-30
What version of Open office do you have and also what Palm are you running. I just install the file saved as a .xls format or save it from an email message.Doc2Go reads WinOffice file formats. I'm running a Palm TX , Doc2Go ver 7.xx and OPen office ver 2.

---

### Post by Carandol on 2006-11-30
I'm using OOo 2.0.2, a Palm Vx with OS 4.1, and Doc2Go 6.0. But I'm using J-Pilot, which refuses to install non-native file formats on the palm. Maybe that's where I'm going wrong? What do you use to transfer file?

---

### Post by wastrel on 2006-11-30
The only way to install non-native data formats onto the Palm is to either 
use a sync conduit or to put it on a removable memory card.  If you don't 
have a card reader you may be able to set the Palm work as a removable 
drive and access the card that way.

I believe Tungsten T and some Clies can do this natively.  You can also 
install the Card Export program on your Palm which will add this capability
to any device.

---

### Post by rioghal on 2006-12-11
I loaded a spreadsheet into OpenOffice.org calc (on my desktop PC), saved it as "Microsoft Excel 97/2000/XP", transfered it to my Palm T|X via an SD card, and it works great on my DocumentsToGo on my Palm T|X. It'll open as a MS compatible spreadsheet but you can save it as that or save as Sheet To Go.

---

### Post by pogo07 on 2008-04-11
After a 3+ month learning curve trying to transfer music, movie and data files from my Ubuntu desktop to my Palm TX I found a program called Cardexport.  There is a cost for it but it's great.  Transfer to my palm is simple. Install the Cardexport prc file to my palm and run it.  It mounts my palm as a separate drive.  Files can be transferred via drop and drag.  I use the Gnome desktop and added the gnome-pilot conduit icon to my taskbar.  You have to restart the computer before anything will work (Dell 5160).  I can drag and drop any .prc file to the icon, syncronize and presto the program works on my palm.

 I use FileZ to move the files around on my palm.  They seem to have to be in the DCIM directory to work.  I have to use Doc to Go to read the data files and they have to be saved on my desktop as Windows files for everything to work.  I would like to eliminate the need to use  Doc to Go at all but haven't figured out a way around this yet.

As a newbee, I am more impressed with Unubtu each day.

---

### Post by kencaudill on 2008-04-15
Has anyone tried the Addition4Palm software which is supposed to sync with Linux? I tried it but could not get it installed on my Ubuntu system. I did get the program installed on the Palm and it is a very nice spreadsheet and if it works for syncing with Ubuntu that would be wonderful.

---

