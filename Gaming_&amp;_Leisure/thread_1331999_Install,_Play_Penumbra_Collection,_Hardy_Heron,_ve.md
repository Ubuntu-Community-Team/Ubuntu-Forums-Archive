---
title: "Install, Play Penumbra Collection, Hardy Heron, ver. 8.04.1"
date: 2009-11-19
forum: Gaming &amp; Leisure
---

### Post by helmcken on 2009-11-19
[FONT="Century Gothic"][SIZE="3"]ALSO POSTED ON FRICTIONALGAMES FORUM- 
  Hello!  I don't use terminal commands and am a 45 year young kid who just likes playing games! The Penumbra game demo ran beautifully, although I don't remember now whether I played the Windows or Linux version.
  I downloaded the collection of games, but know nothing of md5sums, so am unable to verify the integrity of the download over my jumpy internet! 3 files landed on my desktop: PenumbraCollection-1.0.sh at 892.5 mB; CustomLayout.aspx_files at 24.2kB and CustomLayout.aspx.html at 13.7kB. 
  I emailed support, but have received no reply. I really need help to get this game installed and running! Here's what I've done so far (other than reading post after post, thread after thread, here and on Ubuntu!): 
  I read on a post that installing was easy.  (Apparently, the .sh ending is the Ubuntu installer! That's news!)  Point mouse cursor over PenumbraCollection-1.0.sh and right click to bring up Properties. On Properties, select the Permissions tab. Put a check mark in the radio box that says Allow executing file as program. Close window. Put mouse cursor back over the PenumbraCollection-1.0.sh icon and double click with left mouse button. That is supposed to install the games. At this point, I restarted the computer.
  The install appeared to run smoothly. Even got to a window where I entered the serial number. At the end, the window announced Penumbra was successfully installed. Under Applications > Games, the 3 games were listed with their distinctive icons.
  But, when I left clicked on one, (didn't matter which), the game did not launch. Immediately following my click, there would be like a "blink" of the desktop, like the system was receiving/acknowledging my request. But nothing more happened.
  When reading in the forum, output of the hpl.log is always requested. Using the SEARCH of my files, the computer says no such file/folder exists! So, I cannot provide the hpl.log output, even if I did know what that means... In fact, I couldn't even find a folder called frictionalgames or Penumbra!
  The game appears not to be installed. What do I do next? Please tailor response to an absolute beginner level or I'll be lost. My laptop is a HP Pavilion dv8320ca, Intel Centrino Duo Processor T2050, 1.6GHz, 2MB L2 cache, 533MHz FSB, 160GB of storage on dual hard drives and 30.4GB available disk space. I'm running an nVidia graphics card which utilizes the legacy version of the nVidia drivers on this Ubuntu side. (I've a bootloader with Windows XP on the other side, which I use exclusively for games. Everything else, especially internet browsing, I do on this Ubuntu side.). Other programs run smoothly. The Ubuntu OS is commonly known as Hardy Heron, version number 8.04.1.  PLEASE HELP!! :confused: [/SIZE][/FONT]

---

### Post by cariboo on 2009-11-19
First off welcome to the forums, this thread really isn't inthe right sub-forum, so I will move it to Gaming & Leisure.

Please use more white space to make your easier to read.

---

### Post by Brebs on 2009-11-20
> **helmcken said:**
> hpl.log
The file is ~/.frictionalgames/Penumbra/Overture/hpl.log

> Using the SEARCH of my files, the computer says no such file/folder exists!
I assume that the search function is using an out-of-date cache.

---

### Post by helmcken on 2009-11-20
When you say "The file is ~/.frictionalgames/Penumbra/Overture/hpl.log" what is the pathway *before* frictional games? I just tried again, using SEARCH FOR FILES and entered **hpl.log** in NAME CONTAINS and **File System** for LOOK IN FOLDER, but still got no results. I then tried *every* folder, but no difference.
Yet, the original 3 files are still on my desktop, since I didn't know whether to delete the desktop icons or not after the (supposedly successful) install. Also, the 3 icons and listings are still in APPLICATIONS > GAMES.
What to do?

---

### Post by 569874123 on 2009-11-20
> **helmcken said:**
> When you say "The file is ~/.frictionalgames/Penumbra/Overture/hpl.log" what is the pathway *before* frictional games?
/home/username/.frictionalgames/Penumbra/Overture/hpl.log

in username i mean your username in ubuntu, if you do not know, by going to places->home you could determine it by checking the "location" bar, right of the pencil icon.

---

### Post by helmcken on 2009-11-20
Okay, here's something! When I use file browser and open home, then my file, there are the usual several folders like documents and pictures. But there **is** also a folder called PenumbraCollection!
  So, it ***is there***. It is also separate on my desktop, if I open that. If I simply open the folder PenumbraCollection, I can see two folders (Overture and Black Plague), one black page called Collectionkey, and three gear-looking icons (blackplague, overture and requim). So, it looks like enough stuff is there. Is one of those the equivalent of a Windows .exe to make the game run?
  When I left-click on one of the Penumbra game listings under Applications > Games, the whole screen blinks like it is trying to execute the command but getting terminated immediately. Since it **is** there, what is going on? :confused:

---

### Post by helmcken on 2009-11-21
[FONT="Century Gothic"][SIZE="3"]:confused: Still need help, please! Frictional Games' Support responded with this: 

[FONT="Comic Sans MS"][I][COLOR="Navy"]The problems you have with launching the game from the start menu is due to an error in the installation file, which is being worked on. To get the games to launch correctly you can do the following:
[/COLOR][/I][/FONT]

 I am attaching the terminal's output after trying their suggestion to enter this command: **[COLOR="Navy"]~/PenumbraCollection/Overture/penumbra[/COLOR]**  

[B][COLOR="DarkRed"]heathcliff@heathcliff-laptop:~$ ~/PenumbraCollection/Overture/penumbra
Segmentation fault
Penumbra: Overture exited unexpectedly, please check
/home/heathcliff/.frictionalgames/Penumbra/Overture/hpl.log
for any error messages
Also try running
ulimit -c unlimited
And re-running Penumbra and try and recreate the error
then submit the generated core file or stack trace
heathcliff@heathcliff-laptop:~$ [/COLOR][/B]
 
When I did that, the whole screen "blinked" again. 
[B][I][SIZE="4"]What is the computer asking me to do in the ulimit line, please?
[/SIZE][/I][/B]
I tried *again* to find a folder called **hpl.log**. Search says it does not exist. Tried to find a folder called **.frictionalgames** but it does not exist either. Now, I **know** where my home folder is. The only folders in it are: desktop, documents, examples, music, pictures, public, templates, videos, the gear-shaped icon labelled AdobeFlash10,test, a solid-black page icon labelled brasero-session.log ***and the folder PenumbraCollection ***(containing 13,990 items, totalling 2.1GB - which sounds about right).
***[SIZE="4"][COLOR="Red"]What next, please?[/COLOR][/SIZE]***
[/SIZE][/FONT] :confused:

---

### Post by del_diablo on 2009-11-21
.folder = hidden folder
folder = non-hidden folder

Just hit ctrl+h in the file manager to toogle the ability to se hidden folders.

---

