---
title: "Questions about ut2004 install"
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by BlueStreak on 2006-07-14
I've been browsing the ut2004 threads and it seems most everyone installs it from a terminal using sh.

I simply put the install cd in and clicked autorun.  It installed just like installing Windows software.  Was it a bad idea to do it this way?

By default the game installed in C:/UT2004.  This bothers me as there are no drive letters in linux.  It would not accept a directory path without a drive letter.  Also doing a search of the file system finds NOTHING except the desktop shortcut.  Despite this the game runs.

The real reason I'm questioning these things and searching the forums is that the game runs just fine except my mouse movements are extremely jerky.  Everything else is smooth and the mouse works fine in any other app.  It's bad enough to make it unplayable.

I posted this mouse problem earlier but didn't get any response.

---

### Post by vem0m on 2006-07-14
first question how the HELL? there is no auto run for ut2004 in linux and no there isn't a C:\ drive and i have no clue in hell how u installed it was it thu an emu? as u know there is a native version hence the linux installer on the CD heh hmmmmm

---

### Post by xeta on 2006-07-14
> **vem0m said:**
> first question how the HELL? there is no auto run for ut2004 in linux and no there isn't a C:\ drive and i have no clue in hell how u installed it was it thu an emu? as u know there is a native version hence the linux installer on the CD heh hmmmmm

^^ Agreed, something doesn't seem right.

---

### Post by BlueStreak on 2006-07-14
Yikes!  It's that surprising?

Seriously I'm not pulling anyone's leg here!

I'm running 6.06 on a dedicated machine (no dual boot).  I put the install CD in my drive and it auto mounted.

The file browser window popped up automatically.  Inside it was "autoun.exe".

I didn't think it would work but just out of curiosity I double clicked it and the setup ran.

It was exactly like installing the game would be in windows.

I didn't expect this to come as such a surprise. I swear this is exactly how it happened.

It shouldn't have worked that way?

---

### Post by vem0m on 2006-07-14
seems it might have installed thu wine or sumthing but i don't think so as it wouldn't run well if at all installed that way where did u get this CD?

---

### Post by BlueStreak on 2006-07-14
I got the CD at Circuit City.  There's 5 install CDs and 1 play CD.  It has the linux penguin on the back of the box.

I do have wine installed but I saw no indication of wine being used to install.  I don't use wine anyways as this machine is strictly linux, ext3 formatted.

--edit--just to reiterate, it runs fine except for the mouse being extremely jerky

---

### Post by vem0m on 2006-07-14
yes that is the 6 CD set no autorun installer u cannot execute a .EXE file like u said without an emu something is wrong somethign is really wrong

---

### Post by BlueStreak on 2006-07-14
yea I was very surprised when double clicking the .exe file actually worked.

this is freaking me out now.  the only emu installed that i know of is wine, but like I said I don't use it.  I only installed to take a look at it.

I don't know what to think.

if this helps, the only way to run it is from the desktop icon that was automatically installed.  i can't seem to run it from a terminal.

just to mention it again, i did a search for all things ut2004 and the only thing found was the desktop icon

---

### Post by vem0m on 2006-07-14
hehe goto ur home folder make sure u can see hidden files and folders and go into the .wine directory and then to drive_c and check for the folder lmao also right click the icon and tell me what the program path says

---

### Post by gschoper on 2006-07-14
If I double click on an .exe file in nautilus it executes. .exe's are associated with wine. Chances are you installed the windows version of ut2k4. check and see if it's installed under ~/.wine/drive_c/

gschoper

---

### Post by vem0m on 2006-07-14
hehe yep just what i asked him to do lol :P

---

### Post by BlueStreak on 2006-07-14
Oh man, now we're getting somewhere.  There's the ut2004 folder.

and here's the path:  "wine "C:\UT2004\System\UT2004.exe"

d'oh!

This sucks.  I guess it makes sense now

Sorry for all the trouble!

So I guess I should uninstall and reinstall properly, huh?

This is really pretty funny now :D   

Thanks for the help, i'll take my lashes now

---

### Post by vem0m on 2006-07-14
yes goto terminal and type uninstaller select UT2004 and wait for it to finish and then goto the directory we said and delete the UT20004 directory there in and then use the linux installer to install it over :P

hope all goes well for u

---

### Post by james016 on 2006-07-15
Just installing this now but I do have a question:

What is the purpose of the symbolic link it creates? It is in my home folder. What does it do?

---

### Post by Perfect Storm on 2006-07-15
How did you install it?

Usually you go for:

```
sudo sh /media/cdrom/linux-installer.sh
```

When finish exit the installer (Don't press the play button, if you do you'll get permission problems)

Now type ut2004 in the terminal.
You'll properly want the latest patch as well (it solved some crash problems and alot more)
Get the megapack (I made a list here [http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=view&id=256&catid=11](http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=view&id=256&catid=11) ) save it to your Desktop and unpack it.
then
```
cd Desktop
cd ut2004megapack-linux
sudo cp -r * /usr/local/games/ut2004

```
Done now start ut2004

---

### Post by vem0m on 2006-07-15
orrrrrr get the mega pack from [http://liflg.org/?catid=6&gameid=17](http://liflg.org/?catid=6&gameid=17) there and then goto terminal and do a sudo chmod +x ut2004.megapack-english-2.run
then a ./ut2004.megapack-english-2.run to install it :)

---

### Post by Perfect Storm on 2006-07-15
Aye, I just use to do it the other way around ^^


By te way I've now wrote a howto install ut2004 and howto patch it: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63)

---

