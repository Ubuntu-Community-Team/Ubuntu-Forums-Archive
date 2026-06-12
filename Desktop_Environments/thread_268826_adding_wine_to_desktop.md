---
title: "adding wine to desktop"
date: 2006-09-30
forum: Desktop Environments
---

### Post by lonelypauly on 2006-09-30
im working on my moms pc and she has an interactive dvd that she wants to use on her linux box (watchtower 2005, all reports are that this works fine under wine)
[http://appdb.winehq.org/appview.php?iVersionId=4154](http://appdb.winehq.org/appview.php?iVersionId=4154)

ive got the latest version of wine installed, however, i cant get this disk to open...it shows up on the desktop, but i dont know the best and easiest way for my mom to run her dvd.  i tried the alacarte menu editor and there is no wine in there...why are some programs not showing up in any of the menus?  i did the apt-get wine command and it tells me that wine 0.9.2.1 is installed so i know its there.

how do i add wine to the desktop?


can someone please help me?

thanks.

---

### Post by ropers on 2006-09-30
I don't really have a clue and I don't really remember things that well, but you probably want to use something like this from the Terminal:

wine /media/cdrom/watchtowerexecutable.exe

Then you could probably create a shortcut to that in some way, eg. by creating one of these horrid .desktop files. Eg. drag a favicon to the desktop from your browser and open that .desktop file with Text edit. Edit as appropriate to include the Wine comand instead of the webpage stuff and save.

---

### Post by djRobbieF on 2006-09-30
You say it's a DVD.  Do you mean it is video?  I'm confused, because that would be xine, not wine.

---

### Post by lonelypauly on 2006-09-30
it is not a movie...that is sort of why i put the link underneath it...anyway...i cant get wine to work...or more accurately, i dont know how to use wine. i copied the contents of this dvd to the hd and have been trying to figure out how to open this with wine...ive tried the "open with" command but when i type in "wine" i get nothing...its like its not installed, but i know it is because i just installed it...

---

### Post by djRobbieF on 2006-09-30
OH OH OH - sorry, I didn't see the link.  :)

go to your linux terminal and type:
```
wine --version
```

Does it say Wine 0.9.21?

---

### Post by ropers on 2006-09-30
-

---

### Post by lonelypauly on 2006-09-30
yes, it says wine 0.9.21

there is a setup.exe file in that dvd i copied to the hd...how do i get it to open or possibly install with wine?  i dont see wine ANYWHERE in the menu system/alacarte menu editor, etc...all i need is wine to work, yet it remains elusive.

---

### Post by djRobbieF on 2006-09-30
OK so that shows we've got wine installed (congrats!).

Now, just open the exe with wine.

SO - double click the exe.  It will bring up the list of current applications - but wine won't be there, because you haven't used it yet.

So browse using "use a custom command"

type:
```
/usr/bin/wine
```

That workie?

---

### Post by lonelypauly on 2006-09-30
i got this message:

[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/Screenshot-1.png[/IMG]

i checked the permissions on the parent directory and the file itself and all the permissions are checked...this is really annoying...but i greatly appreciate your help

---

### Post by CatKiller on 2006-09-30
In a terminal, type **winecfg**. This will allow you to setup drives and whatnot, and it will create a .wine directory in your Home folder. Wine doesn't really work until you've done this step.

EDIT: What I mean by it not working, is that the default pretend C: drive is inside the .wine directory. No .wine directory, no C: drive, no programs will install. HTH.

---

### Post by lonelypauly on 2006-09-30
thanks for that...do you happen to know where i can find instructions on how to configure wine properly?  i think i just made a new dir in home...

---

### Post by CatKiller on 2006-09-30
Not really. WineHQ is the only place I know of, other than the Ubuntu wiki and this forum, and you've been there already. I installed Wine from the budgetdedicated repository, and it just worked. Applications I've tried have either just worked or I gave up on them. At some point of me running Wine, possibly after the first time I ran it, I got an "Open with Wine Windows Emulator" menu item for all files of type "application/x-ms-dos-executable" which seems to work OK, but I don't really know how it happened. The people in the Gaming forum might know more. Sorry.

---

### Post by lonelypauly on 2006-09-30
im not crazy enough to try and game with linux...im just trying to set up my moms silly bible disk for her...wine is not cooperating at all on this computer...this sucks.

this is total garbage...i setup wine just fine on my computer...but apparently its not working on my moms pc, which is older of course, but has enough memory/cpu to handle the job...what a bunch of crap this is!

i guess its time to reinstall windows for her, since all she pretty much cares about it getting this stupid dvd working.

---

### Post by CatKiller on 2006-09-30
The reason I mentioned it is because the biggest class of Windows software for which there aren't Free alternatives is games. So the people that have most experience of tweaking Wine are gamers. The AppDB page that you linked to talks about wtlib, a Watchtower library. Have you looked into that at all?

---

### Post by lonelypauly on 2006-09-30
yes i have looked at it.  none of which address the permission problems im having...i just cant be bothered by this crap anymore.  thanks for helping though, i appreciate it.

---

### Post by CatKiller on 2006-09-30
I don't think that it's a permissions problem. Unless there's something else going on. I think the error message in your screenshot was because there wasn't a C: drive to write to at that time. Which, as far as the Windows Installer was concerned, is crazy-talk - so it **must** be that you don't have permission :rolleyes: 

So if you manually created a ~/.wine folder, delete it. Run **winecfg** in a terminal. This **should** open a window. Click on the Drives tab and make sure that there are entries for the C: drive and the DVD drive. If there are, close the window. If not, make appropriate entries, Apply them, and then close the window.

Then type ```
wine /cdrom/setup.exe
```. This is the basics of getting a Windows application to run in Wine - it's mostly invoked from the command line, which is why there isn't a menu item for it.

Once you've got that far, apparently the program will crash, and you'll probably have to sort out a replacement comctl32.dll.

---

### Post by ropers on 2006-10-01
> **lonelypauly said:**
> i just cant be bothered by this crap anymore.  

Hey! You've just solved the problem! You've successfully added whine to your desktop!
[(SCNR.)]("http://www.catb.org/jargon/html/S/SCNR.html") :-P

---

