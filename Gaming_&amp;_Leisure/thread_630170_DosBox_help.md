---
title: "DosBox help"
date: 2007-12-03
forum: Gaming &amp; Leisure
---

### Post by MisterMetallic on 2007-12-03
Hi, I really need someone's help trying to run 'Betrayal At Krondor' on the Dosbox emulator. I know this has been covered before, and I apologize if im breaking some forum code by doing this. I tried to follow the steps on this forum and others and I get stuck at the same part every time.
I am unable to mount a drive in the program. I am on the first screen when you open DosBox, and the command promp says 'Z:\>'. I know Im supposed to type 'mount c:\home\myusername\games, but It never works. the message is as follows :
'usage MOUNT Drive-Letter Local-Directory'
'So a MOUNT c c:\windows mounts windows directoty as the c: drive in dosbox'

Again im sorry if this is annoying to some folks, but Im almost completely computer illiterate next to people around here, and have no idea what im doing wrong. Thank you very much for any help.

---

### Post by Herman on 2007-12-03
To start dosbox and run a program, just type the path and name of the .exe (executable file). 
The directory you want dosbox to run in will be mounted as the 'C:\' drive' (automatically).

So if the game you wanted to play in in Ubuntu and it's located in \home\myusername\games, and it's called Betrayal At Krondor.exe, you would open your terminal and enter,
```
 dosbox games/Betrayal At Krondor.exe -fullscreen
```

 If the game you want to play is really in your C:\ partition (/dev/hda1), first you would check to see if your Windows partition is already mounted in Ubuntu, usually in /media, and if not, you would need to mount it yourself, in a regular terminal in Ubuntu. [            Mounting Windows FAT32 or NTFS filesystems]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop").

Then find out the file path to your game and then open dosbox in the directory the game is in so dosbox will treat that directory as if it is the C:\ drive.
For example, you would type something like the following into your terminal in Ubuntu  'dosbox /media/hda1/Documents\ and\ Settings/MisterMetallic/My\ Documents/My\ Games/Betrayal\ At\ Krondor.exe -fullscreen' into a terminal (without the inverted commas),
```
dosbox /media/hda1/Documents\ and\ Settings/MisterMetallic/My\ Documents/My\ Games/Betrayal\ At\ Krondor.exe -fullscreen
```You would need to alter that file path to suit your own particular computer, of course, this was just an example I made up, but it would be something like that. 
TIP: Use your tab key a lot when typing commands. (Just type the first two or three letters of each file and then press TAB, it will make your work easier).
Regards, Herman :)

---

### Post by anaconda on 2007-12-03
I must be lazy, because I just use nautilus and go to the folder which has the .exe file and right-click on that file and select "open with DosBox"

The first time you need to select "open with other aplication" and type dosbox to the use custom command..

---

### Post by wounded on 2007-12-03
> **anaconda said:**
> I must be lazy, because I just use nautilus and go to the folder which has the .exe file and right-click on that file and select "open with DosBox"

The first time you need to select "open with other aplication" and type dosbox to the use custom command..

hmm, I don't know if that works correctly (Simply because I've never tried it) but if you want an easy way to run dos games through dosbox I've found that Dosbox Game Loader works great. [http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/](http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/)

You just download the newest Linux archive and decompress it whereever you want. It comes with a version of Dosbox already. I pmake a new folder in the DBGL folder (That you just decompressed) and toss all my dos games in there (I call it dosroot). Then I double click on the DBGL program (Which requires java I think, so you might have to apt-get that) and then a menu comes up. I click "add profile" and fill in the name of the game and some other optional information (You can add things like developer and publisher if you want) and tell it where the EXE is located on my harddrive (dosroot) and then it appears in the DBGL menu when I load the program. Then I can just double click on whatever game I want to play from my list and it loads it in dosbox. 

HOWEVER! From your original post let me correct you, so that you can toy with dosbox by itself if you want. In linux there are no drive letters so it would look like this instead
```
Z:>mount c /home/wounded/games/dbgl/dosroot
```
That's what I do, then that makes my dosbox C drive the drive where all my dosgames and stuff is. 

The easiest way to do this is to automate it. In the dosbox config file (It is in the DOSbox-0.72 folder if you download DBGL, if you apt-get dosbox I guess it's in /etc somewhere, I'm typing 'man dosbox' in a terminal will tell you where) and just scroll to the very bottom of the file. You should come across "[autoexec]"

Everything after that line will get ran as a command when you start dosbox. so you can make it look like this:
```
[autoexec]
mount C /home/games/dos
mount D /media/cdrom0 -t cdrom
C:
cls

```
Then whenever you open dosbox it will automatically mount /home/games/dos (Or whatever folder you point to in that line) as the C drive. The second mount command tells dosbox to make /media/cdrom0 (Where CDs get mounted when you insert them) to become the D drive for dosbox (Which will let you play dos games that require the cd to play). Then the "C:" will make it so that you are in the actual dosbox hard drive and "cls" will clear the screen. Then when you start dosbox you will be greeted with a blank screen that says only "C:>" and ready for you to run whatever game you want.

Hope this helps a bit. Good luck.

---

### Post by Eddie Wilson on 2007-12-03
A lot of good help can be found on the DosBox web site. [http://dosbox.sourceforge.net/news.php?show_news=1](http://dosbox.sourceforge.net/news.php?show_news=1)
DosBox is hard to beat. Enjoy.
Eddie

---

### Post by FranMichaels on 2007-12-03
> **anaconda said:**
> I must be lazy, because I just use nautilus and go to the folder which has the .exe file and right-click on that file and select "open with DosBox"

The first time you need to select "open with other aplication" and type dosbox to the use custom command..

I can vouch this does work properly in dosbox 0.72 (support for ~ locations was added)
[http://www.getdeb.net/app.php?name=Dosbox](http://www.getdeb.net/app.php?name=Dosbox)

Basically the game thinks it's running form C:\
So, if it's set up right, no games should give you any trouble. I actually prefer it this way, since the game doesn't see any of my other DOS folders, so on the off chance some ancient DOS virus is around, it can't mess things up :)

So, just right click that .bat, .com, or .exe and good to go. 

:KS

---

