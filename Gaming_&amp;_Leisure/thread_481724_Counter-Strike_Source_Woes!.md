---
title: "Counter-Strike Source Woes!"
date: 2007-06-22
forum: Gaming &amp; Leisure
---

### Post by BlahMan_of.Doom on 2007-06-22
Or infact any other source game. This is what happens when I load it from Steam (wine 0.9.37, stable steam release). Please help & check attachment!

---

### Post by ubu-for on 2007-06-23
Did you follow [this](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games) guide?

---

### Post by BlahMan_of.Doom on 2007-06-23
Now I did, but it still does not work. Also, the WineCVS sh doesn't work either. It gives me this output: ```
$ sh WineCVS.sh
test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected

```
Thank you for trying though.

---

### Post by dfreer on 2007-06-23
do you have direct rendering enabled?
```
glxinfo | grep rendering
```

---

### Post by ubu-for on 2007-06-24
> **BlahMan_of.Doom said:**
> Now I did, but it still does not work. Also, the WineCVS sh doesn't work either.

Forget WineCVS, use [Wine](http://www.winehq.org/site/download-deb) 0.9.39 (Vista mode) instead and follow the guide above.

Which video card drivers do you use?

---

### Post by BlahMan_of.Doom on 2007-06-29
> **dfreer said:**
> do you have direct rendering enabled?
```
glxinfo | grep rendering
```
$ glxinfo | grep rendering
direct rendering: Yes

> **ubu-for said:**
> Forget WineCVS, use [Wine](http://www.winehq.org/site/download-deb) 0.9.39 (Vista mode) instead and follow the guide above.

Which video card drivers do you use?

I got the drivers using Envy. And okay I'll try that guide.

CS:S still does NOT work, even after the guide.

I forgot to add, silly of me. It gives me this everytime before I start a game:
[http://img515.imageshack.us/img515/7158/screenshotsz2.png](http://img515.imageshack.us/img515/7158/screenshotsz2.png)

---

### Post by ubu-for on 2007-06-30
First of all, you are using the latest Wine version with Vista mode, right?

BTW The developers released today Wine 0.9.40.

> **BlahMan_of.Doom said:**
> I got the drivers using Envy.

I've never used Envy to install my Nvidia drivers, because the "Ubuntu way" is easy and clean.

Maybe you should uninstall your Nvidia drivers with Envy and than type the following into the "Terminal".

```
sudo apt-get update
```

```
sudo apt-get install nvidia-glx
```

That's it!

> **BlahMan_of.Doom said:**
> I forgot to add, silly of me. It gives me this everytime before I start a game:
[http://img515.imageshack.us/img515/7158/screenshotsz2.png](http://img515.imageshack.us/img515/7158/screenshotsz2.png)

No, that wasn't silly! Steam thinks, you are using Windows with outdated drivers. This will appear sometimes in the future, too and isn't a problem at all.

---

### Post by BlahMan_of.Doom on 2007-07-04
Okay cool. I just got back from a roadtrip so I will try that when I come back.

---

### Post by BlahMan_of.Doom on 2007-07-05
It still doesn't work, same problem :(

---

### Post by Mike7171 on 2007-07-05
Is installing this as confusing as that guide makes it seem? I have the game sitting on my shelf and I'm contemplating installing it. I'm having enough trouble with Starcraft , Hitman, and Halo as it is. I'll try it though and see if I get the same problem as this.

---

### Post by dfreer on 2007-07-05
> **Mike7171 said:**
> Is installing this as confusing as that guide makes it seem? I have the game sitting on my shelf and I'm contemplating installing it. I'm having enough trouble with Starcraft , Hitman, and Halo as it is. I'll try it though and see if I get the same problem as this.

It seems to depend for different people. It's listed as Gold on wine appdb, and only really requires that you copy the tahoma.ttf file into the font directory. Not that hard to install, whether it will work or not (since you are already having lag issues with Starcraft, I dunno if it will).

Also, note until just recently Halo was unplayable in wine, and even now there are like a zillion posts about problems running it.

---

### Post by BlahMan_of.Doom on 2007-07-05
>.< Okay then so I guess there's no solution??

---

### Post by ubu-for on 2007-07-05
Run winecfg and disable "Pixel Shader".

---

### Post by Mike7171 on 2007-07-05
I installed Steam no problem. Runs perfectly. Now for the games. I have the Game Of The Year Edition of Half-Life 2 (Has HL2, HL1:source, HL deathmatch, and CS:S). Is there any other steps I need to do with this instead of that guide? Has anything changed?

EDIT: IT says I'm supposed to change the directory for Steam. How do I go about this? Because in step 4, it says to run Steam by typing "steam.exe" in terminal after its been changed, and it says command not found. So I need to change something, but I'm not sure what.

---

### Post by ubu-for on 2007-07-05
I don't think so. Just do it. ;)

---

### Post by Mike7171 on 2007-07-05
Lol, I'm going to. I'm just not sure how to change the directory so that Step 4 will work.

Output to "wine Steam.exe":

> 
mike@mike-desktop:~$ wine Steam.exe
wine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found

---

### Post by ryankent on 2007-07-05
you have to navigate to the steam directory, where steam.exe is, do you not?

---

### Post by Mike7171 on 2007-07-05
The guide tells me to **change** the directory of it. I'm not sure how to do that. Right now, the shortcut/icon to it is on my desktop, and I can start Steam also by going Applications > Wine > Programs > Valve > Steam.   

When I go into my .Wine folder, there is a Steam.exe file in there in the Valve folder, but it looks like a setup or something. Either way, Steam is supposed to run when I type "wine steam.exe" in Terminal, but it doesn't.

Edit:  "you have to navigate to the steam directory, where steam.exe is, do you not?"

Oh, I'm sorry, do you mean type out the navigation to it when trying to run it in Terminal?

---

### Post by ubu-for on 2007-07-05
For example:

```
cd ~/.wine/drive_c/Programs/Steam
```

---

### Post by Mike7171 on 2007-07-05
"No Such File Or directory". Do I just have to drag and drop the icon or something?

---

### Post by Mike7171 on 2007-07-05
Im ignoring that for now, and installing CSS through the Half Life 2 pack. Im up to the point where I need to insert Disc 2, but I can't open my cd drive. When I try to 'eject' it, it says "can not eject volume. HL_1 prevening" or in use or something. What do I do?

---

### Post by joos13 on 2007-07-05
I know you cant unmount a device (CD rom) while it is in use, so you may have a problem there.  as far as running steam.exe, you should not just glance over the problem.  changing directories is pretty basic yet important to know how to do.  just type in "cd" and then put the filepath string.  If there are any spaces in the string, aka /Program Files/, the filepath string must be in quotation marks.  once you navigate to your steam folder you should be able to run "wine steam.exe"

---

### Post by dfreer on 2007-07-05
"Change Directory" is what cd stands for, it doesn't actually "change" anything (permanently anyways).

You can simply just start steam by double-clicking the icon on the desktop or in the applications menu, it doesn't make a difference. However, starting it in the terminal is useful when posting error reports, because it shows some error messages in the terminal window.

So if you want to start steam in terminal, there's several different ways of doing it, although they all accomplish the same thing. First thing, try running this command in terminal:
```
nautilus ~/.wine/
```
From there, it will launch the file browser and you can check out the names out of the actual folders, for example on my system it goes like this:
```
~/.wine/drive_c/**Program Files**/Steam/steam.exe
```
Now, another important thing to note is that any time there are whitespaces in the Folder/File name, in terminal you need to either enclose the path in quotations or escape the whitespace with an "\" character. You should not use both methods together, just one or the other.

So on my system, I can navigate to the correct folder with this command:
```
cd ~/.wine/drive_c/**Program\ Files**/Steam/
```
Or:
```
cd "/home/dfreer/.wine/drive_c/**Program Files**/Steam/"
```
From there, my terminal prompt will change so that I can see which folder I am currently in, so it looks like this:
```
dfreer@fraghagbox:~$ cd ".wine/drive_c/Program Files/Steam/"
dfreer@fraghagbox:~/.wine/drive_c/Program Files/Steam$
```

From which you could easily execute the command:
```
wine steam.exe
```
Of course, you can combine this into one command like so:
```
wine ~/.wine/drive_c/Program\ Files/Steam/steam.exe
```
Provided you know the correct path. Another tip would be to use the tab completion feature of the terminal, try typing:
```
cat /etc/apt/sour
```
And then hit the <Tab> key, it will do one of two things:
(1) if there is only one file/folder that begins with "sour", it will automatically fill in your command so it would look something like this:
```
cat /etc/apt/sour**ces.list** 
```
(2) if there are multiple matches, it will produce a system beep and then if you hit <Tab> once more it will display all possible choices.

Hope this helped!!

EDIT: to eject cd's used in wine, try using the "wine eject" command. You might need to specify the path to the cd drive in winecfg before this command will work, so wine knows where the CD drive is. "sudo umount -f **/path/to/your/cdrom/here**" may also help

---

### Post by Mike7171 on 2007-07-05
I got Steam running through the Terminal now, so thank you. I'm gonna try installing the games now using that Sudo unmount path/to/cd/drive command. I'll let you know how it goes.

---

### Post by Mike7171 on 2007-07-05
I used "wine eject" and it worked, but when the disc loaded so it can continue the installation, it gave an error that said "installation ended prematurely due to error" . Anyone know what's going on, and how to get past this?

---

### Post by Mike7171 on 2007-07-05
In Steam, in the games section, it has CSS, HL2, and HL1S, and beside them all it says "Pre-Load Complete". They aren't fully installed yet though obviously. I'm not sure what that error was though.

---

### Post by dfreer on 2007-07-05
You could always download the games through steam, the pre-load complete normally occurs when you install the *.gcf files (such as by installing them from the CD), but steam doesn't know that you *own* those games yet. If you haven't done this before, try registering your CD-Key through My Games, at the bottom it has a button that says "Activate a product through Steam..."

---

### Post by Mike7171 on 2007-07-05
That's a good idea. When I double-click on the ones that are there now (Pre-loaded things), it brings me to the page to purchase them. I'll try to find a spot to enter my key. I'll wait until I'm done installing the HL2 Demo though (if it doesn't run smoothly, I know that the full game won't. I think. I'm doing it as a test).

---

### Post by Mike7171 on 2007-07-05
Demo works, but gameplay is laggy. The sound is horrible too. It lags a lot worse.

---

### Post by ubu-for on 2007-07-05
> **dfreer said:**
> You can simply just start steam by double-clicking the icon on the desktop or in the applications menu, it doesn't make a difference.

If you launch Steam that way, the bug "bin/vgui2.dll Fatal Error" appears very often.

> **dfreer said:**
> Or:
```
cd "/home/dfreer/.wine/drive_c/**Program Files**/Steam/
```

You've forgotten the close quotation marks.

---

### Post by dfreer on 2007-07-05
> **ubu-for said:**
> If you launch Steam that way, the bug "bin/vgui2.dll Fatal Error" appears very often.

Never seen that before myself, what does it do? Better yet, what's a better way to launch?


> **ubu-for said:**
> You've forgotten the close quotation marks.

I did indeed, good eye! fixed :D

---

### Post by ubu-for on 2007-07-05
> **dfreer said:**
> Never seen that before myself, what does it do?

The bug prevents CSS to launch.

> **dfreer said:**
> Better yet, what's a better way to launch?

```
cd ~/.wine/drive_c/Programs/Steam && WINEDEBUG=-all wine steam -applaunch 240 -fullscreen
```

> **dfreer said:**
> I did indeed, good eye! fixed :D

You've taken great pains to help with your post! It's much easier to lean backwards and to add some tips. ;)

---

### Post by dfreer on 2007-07-05
> **ubu-for said:**
> ```
cd ~/.wine/drive_c/Programs/Steam && WINEDEBUG=-all wine steam -applaunch 240 -fullscreen
```

Hmmm, I knew the WINEDEBUG=-all should simply turn off the wine error output to console, which causes steam to sometimes lag but I didn't think it's error output would actually cause Steam to crash. Although if steam store/steam itself is crashing, launching CS:S directly with the -applaunch switch should fix it (I haven't had any problems with recent wine versions). Ah, well, there is much to learn in the mystical magic that is WINE, if it prevents crashes I'm all for it.

As for double-clicking the icon's Mike7171, you could modify the original icon's or create your own so that you can launch this command ;)

> **ubu-for said:**
> You've taken great pains to help with your post! It's much easier to lean backwards and to add some tips. ;)

lol yeah sometimes I get carried away explaining things :D

---

### Post by Mike7171 on 2007-07-05
> As for double-clicking the icon's Mike7171, you could modify the original icon's or create your own so that you can launch this command

That's cool. How do I do this? 

Steam is downloading CCS right now. I actually launched it somehow, and it got to the server list, then Steam appeared on top of it, and started downloading at 65%. I'm using my old Steam account that I had all the games installed on, so maybe it just has to download them again or something.

---

### Post by Mike7171 on 2007-07-05
CCS is installed, and I get it's loading screen, but then the Steam window shows up on top of it. In the guide it said to just close the Steam windows as soon as it says "preparing to launch", but then a green-ish looking thing appears over it instead. Like, an empty space. Any ideas?

---

### Post by Mike7171 on 2007-07-05
Half Life 2 does the same thing. The sound also lags way behind in it (in the screens before the loading one where the steam window pops up).

---

### Post by Mike7171 on 2007-07-06
I looked around and I think it isn't just having the window open over it. I think the games are crashing all together at the load screen. Are there any threads about this? If not, any ideas?

---

### Post by BlahMan_of.Doom on 2007-07-13
I don't mean to come on rude but if you have a DIFFERENT problem with CS then make your own thread and stop triple-posting and spamming in mine :mad:. I still have yet to get a solution as everyone has been deluded to your wants. If you want something, then make your own thread. Want me to make this easy?

1) Click [here.](http://ubuntuforums.org/newthread.php?do=newthread&f=93)
2) You could also click the beige colored button labeled "Make New Post" in the Gaming & Leisure section. 

Go hijack someone else's thread with your double/triple/quad post spam.

---

