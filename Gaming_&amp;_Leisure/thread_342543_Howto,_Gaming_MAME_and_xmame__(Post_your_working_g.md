---
title: "Howto, Gaming: MAME and xmame  (Post your working games !)"
date: 2007-01-20
forum: Gaming &amp; Leisure
---

### Post by burek on 2007-01-20
1/ Have a Linux box  :KS 

2/  If you have the arcade machine yourself & dumped its ROM for your own usage
(please dont download roms = illegal) 

3/ ```
sudo apt-get install xmame-sdl
sudo apt-get install xmame-tools   

```

4/ ```
cd  ;  mkdir -p  mame/roms
```
  
5/ from the console
> cd ; xmame -fullscreen mame/roms/mk.zip 
for mortal kombat for instance
  
if you wanna joystick:
> cd ; xmame mame/roms/mk.zip -fullscreen -ef 1 -jt 5 -jdev /dev/input/js0 
 
6/ _Quick keyboard configuration:_
type keyboard ok ok .... space
now, it s running in fullscreen
now, press TAB
then,  in input general > other controls 
insert  coins:   type enter and you might hit : Keypad 5
player 1 start:   type enter and you might hit : Keypad 1
ESC to exit the menu TAB of configuration 
  
7/  the game is now running in fullscreen, and waiting for coins & start key .... lala certainly demo running ...

8/ the keys for playing in mame are now: 
 KEYPAD 5   to insert coins
KEYPAD 1   to play 
Left CTRL to Fire !!
arrows of keyboard to move ...
  
9/ It works ==> OK 
so, now, please POST the :
a / file name of your zip file
b / game name 
c / and if you really like it a cool screenshot
**additionally, if you followed this howto & it worked for you, please let this thread know  (information for "statistics")**
  
10/ Enjoy Sharing !!
  
11/ you can too make a video of your desktop of it :
> sudo apt-get install xvidcap
$ xvidcap 
configuration for speed of xvidcap
[http://img300.imageshack.us/img300/7760/snapshot1xvidcap2tt.png](http://img300.imageshack.us/img300/7760/snapshot1xvidcap2tt.png)


12/ apt-get install kxmame
if you wanna a gui
but it is not working for all zip files !!!!! attention
console way is more working !
  
Screens of the arcade machines : [http://www.mame.net/wip0204.html](http://www.mame.net/wip0204.html)    (what is mame too) 
[http://www.mame.net/wip0208.html](http://www.mame.net/wip0208.html)
mame faq : [http://www.mame.net/mamefaq.html](http://www.mame.net/mamefaq.html)

======
nice howto : [http://www.mythwiki.de/index.php?title=MythGame](http://www.mythwiki.de/index.php?title=MythGame)
(xmame-tools has the chdman/make verify program,  other plugins that can be useful)

---

### Post by jingo811 on 2007-01-20
Need help!
> taco@bell:~$ **apt-get install xmame.sdl**
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
taco@bell:~$ **sudo apt-get install xmame.sdl**
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmame.sdl
taco@bell:~$


---

### Post by leech on 2007-01-20
It's supposed to be xmame-sdl, not xmame.sdl.  

Leech

---

### Post by jingo811 on 2007-01-20
ic.

---

### Post by burek on 2007-01-20
> **leech said:**
> It's supposed to be xmame-sdl, not xmame.sdl.  

Leech

Oup's sorry, windy keyboard ... :) :D typo
I edited/fixed the first post of this "howto"

---

### Post by rolando2424 on 2007-01-20
Isn't the download of roms ilegal?

---

### Post by burek on 2007-01-20
> **rolando2424 said:**
> Isn't the download of roms ilegal?
  If you have the arcaade machine yourself & dumped its ROM for your own usage

---

### Post by rolando2424 on 2007-01-20
> **burek said:**
> If you have the arcaade machine yourself & dumped its ROM for your own usage
Hum... ok...

---

### Post by burek on 2007-01-20
Pacmania
[http://www.megaupload.com/?d=7ESHBHMC](http://www.megaupload.com/?d=7ESHBHMC)

---

### Post by vixvix on 2007-01-20
I can not have the sdl version run on my edgy-server box, have to install the x-window-system-core to run xmame in X. Each time I tried to run xmame-sdl, it gave me something like device permission issue, but if I did sudo xmame-sdl, I got device not found instead.

Any idea? Is there a doc about ubuntu sdl config? I cannot google one. I heard some said the SDL is by default built in ubuntu.

---

### Post by burek on 2007-01-21
> **vixvix said:**
> I can not have the sdl version run on my edgy-server box, have to install the x-window-system-core to run xmame in X. Each time I tried to run xmame-sdl, it gave me something like device permission issue, but if I did sudo xmame-sdl, I got device not found instead.

Any idea? Is there a doc about ubuntu sdl config? I cannot google one. I heard some said the SDL is by default built in ubuntu.

Do you have graphic acceleration? glxgears is laggy or fully working ?

---

### Post by jingo811 on 2007-03-01
What does the ( cd ; ) part do?  You didn't have that some months ago?
> cd ; xmame -fullscreen mame/roms/mk.zip


[COLOR="Purple"]TUTORIAL - How to remain Lazy with some BASH scripting.[/COLOR]
Anyhow if you're lazy like me and thinks copying and pasting long commands such as this too troublesome from a text file.
```
xmame mame/roms/mk.zip -fullscreen -ef 1 -jt 5 -jdev /dev/input/js0
```
There's a way to access that long command with just a word or a two by using some BASH scripting.  Here are the steps:
**1.)** You should be in your **/home directory** when doing these steps!
```
me@linux:~$ mkdir bin
```
**2.)** Browse to your /home/bin directory with your **graphical file manager**.
**3.)** Right click with MOUSE > Create Document > Empty File
**4.)** Name the file "mortal_kombat" if that is the short command you want terminal to recongnize.  Then double click the file and **gedit** should open it up.
**5.)** Copy and paste this into the text document and save!
```
#!/bin/bash

# mortal_kombat - A script to run Mortal Kombat



xmame mame/roms/mk.zip -ef 1 -jt 5 -jdev /dev/input/js0

```
**6.)**
Go back to **terminal **and copy and paste these commands you have to be in **/home/bin** directory first.
```
chmod 755 mortal_kombat
```




**7.)**[COLOR="Purple"] The parts below only needs to be done once in your life time![/COLOR]
Still in terminal do these commands in your **/home directory**!
```
me@linux:~$ ls -la
```
To find your **.bashrc** file then make a backup of it!
```
me@linux:~$ sudo cp ~/.bashrc ~/.bashrc_backup
```
Then edit the file in gedit.
```
me@linux:~$ gksudo gedit ~/.bashrc
```
**8.)** And add this to the end of your file and save.
```
# My custom commands 
export PATH=$PATH:/home/[COLOR="Red"]me[/COLOR]/bin
```

**9.)**
You should now be done BASH scripting.  Now when you want to run your game such as Mortal Kombat you no longer need to copy and paste this long command in terminal.
```
xmame mame/roms/mk.zip -fullscreen -ef 1 -jt 5 -jdev /dev/input/js0
```
All you need to do now is to type in the command below in terminal, but you [COLOR="Red"]NEED[/COLOR] to be in your **/home directory **when doing this or the BASH script won't find your game!
```
me@linux:~$ mortal_kombat
```


Let me know if this little tutorial worked for you or not!

---

### Post by lukew on 2007-03-01
> **vixvix said:**
> I can not have the sdl version run on my edgy-server box, have to install the x-window-system-core to run xmame in X. Each time I tried to run xmame-sdl, it gave me something like device permission issue, but if I did sudo xmame-sdl, I got device not found instead.

Any idea? Is there a doc about ubuntu sdl config? I cannot google one. I heard some said the SDL is by default built in ubuntu.

Can you not use xmame.x

Luke

---

### Post by Mr. DVD on 2007-04-21
I'm trying to run kxmame, but it says I have no xmame executable, what am I supposed to do?
Also, can you play on kaillera with either xmame or kxmame?

jingo811: actually, it didn't work =(. It just says command not found.

---

### Post by Bubbles on 2007-04-21
XMAME and its variants are dreadfully out-dated.  Compile your own SDLMAME instead.  It's actively maintained by base MAME contributors and is up-to-date with the official (win32) version.

[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)

---

### Post by Mr. DVD on 2007-04-21
> **Bubbles said:**
> XMAME and its variants are dreadfully out-dated.  Compile your own SDLMAME instead.  It's actively maintained by base MAME contributors and is up-to-date with the official (win32) version.

[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)

I'm curious. Can SDLMAME play on Kaillera then?

---

### Post by DoktorSeven on 2007-04-21
> **burek said:**
> 1/ Have a Linux box  :KS 
12/ apt-get install kxmame
if you wanna a gui
but it is not working for all zip files !!!!! attention
console way is more working !

How so?  Every MAME ROM I tried worked in xmame through KXMAME.  Did you do something like try to run a ROM file/zip that depended on another one (like a localized version of an arcade game -- these zip files contain only the differences in the localized/hacked/etc version and the original, and you need the master version to do it) or needed a BIOS (like the NEOGEO games that needs the NEOGEO bios)?  Also, CHMs (IIRC, I don't use them) have to be unzipped in a subdirectory of where their ROM is, with the subdirectory named the same as the MAME ROM name -- I *think* (again, I don't use them, but seems like I remember that's what to do from my one experience with them).

KXMAME is very simple and works just fine -- all you need to do is go to a couple of config options.  Make sure it's pointing to an installed version of xmame (should be in /usr/games/) (**note: the GUI is a bit odd in that you not only have to browse to the target, you have to Add it to the list underneath using another button**), and then point it to the directory (or directories) your zipped ROMs are in.

Oh, and one other thing -- why does kxmame depend on xmame-sdl only in Feisty?  I use xmame-x since it has the OpenGL acceleration to speed up rendering, and it won't let me keep it.  (Meh, I'll compile my own kxmame.)

---

### Post by BoyOfDestiny on 2007-04-22
Well I don't have the arcade machine for this one. 
However not an issue for Robby Roto.

"Thanks to the kind generosity of Jamie Fenton, the original ROM images for Robby Roto  have been made available for free, non-commercial use."

Several roms free and legal for non-commercial use hosted here
[http://www.mamedev.org/roms/](http://www.mamedev.org/roms/)

I wouldn't mind if Ubuntu started including more public domain and freely distributed roms along with these emulators... Or maybe they do, at least 2 games for scummvm are in the repo: beneath a steel sky and flight of the amazon queen... I guess it just depends on the license...

Happy gaming!

EDIT: Shown running under sdlmame version 0114u2

---

### Post by jingo811 on 2007-04-22
**@Mr. DVD**
> I'm trying to run kxmame, [COLOR="Red"]but it says I have no xmame executable[/COLOR], what am I supposed to do?
Also, can you play on kaillera with either xmame or kxmame?

jingo811: actually, it didn't work =(. It just says command not found.

From the looks of your post you can't even run the program the regular way, that might be the problem.
My BASH script tutorial won't work if your game didn't work by following the very FIRST tutorial on XMAME.
...By the way I only followed the steps 1-9, I didn't bother installing any GUI, kxmamem, etc. so that could be another factor for you to count in!

But maybe you won't have to go through all that trouble with SDLMAME.  I'm gonna try it myself, if I figure out how to install it properly.  There's so many instructions scattered everywhere and I have never compiled before.  So things aren't looking good for me but we'll see.....

---

### Post by jingo811 on 2007-04-22
........hmm it doesn't look so hard to install SDLMAME compared to XMAME after all.
[http://apt.ludomatic.fr/?hl=en](http://apt.ludomatic.fr/?hl=en)
But I use Dapper 6.06
And the tut says this:
> If you're using Edgy (Ubuntu 6.10), add the lines below to the opened file 
( /etc/apt/sources.list ):

  deb [http://apt.ludomatic.fr](http://apt.ludomatic.fr) **edgy** contrib
  deb-src [http://apt.ludomatic.fr](http://apt.ludomatic.fr) **edgy** contrib

Do I simply edit that to **dapper** or how does it work?  
I'm just at gamer not a programmer. :)

........
........

Now I see another download option
[http://rbelmont.mameworld.info/sdlmame0114u2.zip](http://rbelmont.mameworld.info/sdlmame0114u2.zip)
extracted it sifted through the SDLMAME.txt which instructed some more tech stuff about installation.

I'm too stupid for this sheet #-o  All this endless reading I'm sticking to my obsolete XMAME if it works why break it.

---

### Post by c.falco on 2007-04-23
No, an edgy package won't work for dapper, as dependencies won't be satisfied.

You can download updated i386 binary packages for dapper, edgy and feisty from
[http://wallyweek.altervista.org]("http://wallyweek.altervista.org").

Please note you have to download the right .deb file for your ubuntu release,
and manually install it from console with
[FONT="Courier New"]sudo dpkg --install <path_to_package-name-and_version>.deb.
[/FONT]
I'm sorry, I'm still in the process of setting up a repository, which will be heasier to
use with apt-get or Synaptic. It's taking much time as I expected.

Cheers,
Cesare.

---

### Post by bokorpop on 2007-05-03
I just installed gxmame on feisty and am ready to play but where do I put the roms?? 


I am new to Linux/Ubuntu btw and have been maming on windows for a while. I don't really know "where" programs are installed in linux and dont know how to locate the rom folder.

---

### Post by DoktorSeven on 2007-05-03
There is a tab in gxmame's preferences that allows you to point to where you put the ROMs.  There should be a button to let you browse for the directory, then after you find it, you add that directory to the list underneath by another button (Add, or similar; I don't have gxmame installed to check).

---

### Post by bokorpop on 2007-05-04
This didn't work. Do MAME roms work the same in windows and linux? Its only the MAME program that is different, not the actual roms right?

---

### Post by DoktorSeven on 2007-05-04
Yes, it should be very much the same.

I do recommend that you use kxmame instead of gxmame; gxmame seems much more buggy and doesn't work as well as kxmame.  Get kxmame and a version of xmame (xmame-sdl and kxmame in the repos play together well; I still don't know why the package maintaner says there are problems with kxmame and xmame-x crashing X; it certainly doesn't for me).

After running kxmame it may ask to rebuild the game database.  Do so (this tellks kxmame all the games the currently installed xmame can run).

Settings->Directories.  

Kxmame paths tab: Browse to /usr/games/xmame beside Xmame/xmess executables, hit Add.

Mame/Mess basic paths: Browse to your ROM directory beside Mame ROMS path, hit Add. 

 Hit OK, then hit the circular arrow on the toolbar (Refresh).  Games you have should show up in the Available list (after clicking Available on the left side).  Doubleclick the game name to run.

(Even if you decide to stay with gxmame, the method should roughly be the same.  I know older versions of gxmame do not work at all with newer xmame versions though; 0.35beta2 worked last time I tried it, but it's been a long time since I've used gxmame since kxmame is so much better.)

---

### Post by bokorpop on 2007-05-07
Thanks so much! I got kxmame, did what you said and got many Roms working, however.......

I am now faced with 2 new problems:

1) many games do not work with error messages such as "LIRC disabled" and saying rom files are missing(when the same game/rom works in windows)

2) Don't know how to get my controller configured. It is a Saitek p990, which according to someone one a dif msg board- works fine with linux out of the box, no drivers needed. When I go to configure the controls within the game by pressing "tab" none of the roms respond at all when i try to reset the keys to gamepad keys.

any advice?

---

### Post by DoktorSeven on 2007-05-07
1) Not sure what to tell you about this, unless it's something where the Windows version of MAME works with that game and the Linux version doesn't (possible since the last xmame lags behind the Windows version, but only with a few newer games).

2) Settings->Configure kxmame -> Controllers (left side).  Generally using Standard Joystick type with the prefix /dev/input/js should work, though you can try SDL joystick if that fails (with the same joystick prefix).

---

### Post by mistermax on 2007-05-08
Where should ROMS be placed /usr/share ? Also, can I use my cabinet art?

---

### Post by DoktorSeven on 2007-05-08
As stated above, ROMs can be placed *anywhere you want*.  All you have to do is go into kxmame's configuration under Settings->Directories and add the place you put the ROMs.  In that same configuration you can set what directories contain your cabinet art, flyers, marquees, etc, etc, if you have them.

---

### Post by jingo811 on 2007-08-29
I'm trying kxmame since the quick and nice CLI method no longer seems to work :(  What's with this kxmame error?

> LIRC disabled
xvse.03f NOT FOUND
xvse.04f NOT FOUND
xvsex.03f NOT FOUND (NO GOOD DUMP KNOWN)
xvsex.04f NOT FOUND (NO GOOD DUMP KNOWN)

I want old skool install method to work again 	[-(

---

### Post by jingo811 on 2007-08-29
I uninstalled kxmame did 
```
sudo apt-get autoremove
```
and followed the authors original install method still I get errors.  Kxmame messed everything up for good how do I clean everything and begin from scratch?

---

### Post by DoktorSeven on 2007-08-30
KXMame is just a frontend that executes the commandline much as you're doing.  The "good" dump info between versions might have changed; the info that "NO GOOD DUMP (is) KNOWN" might mean that something's not working now.  Try a different variant of xmvsf (you'll have to specify the ROM directory on the MAME commandline to get it to load all of the bits and pieces).

---

### Post by jingo811 on 2007-08-30
So that's the problem they updated things.  It works now!  Tnx for putting up with my bad temper :)

---

### Post by jingo811 on 2007-11-01
Problems again I reformatted / and reinstalled Ubuntu again then I followed the instructions at first page like I've always done now there's some new problem never before seen.
How do I solve this?

```
root@sama:~# **cd ; xmame -fullscreen mame/roms/mk.zip**
The program 'xmame' can be found in the following packages:
 * xmame-sdl
 * xmame-x
 * xmame-svga
Try: apt-get install <selected package>
Make sure you have the 'multiverse' component enabled
bash: xmame: command not found
root@sama:~# 
```

---

### Post by MaindotC on 2007-12-03
I just downloaded the windows executable and wine'd it.  Changed video options to DirectDraw instead of DirectX - works perfectly.  I don't know how to compile the source code from the site - I know how to compile generally but apparently the source code is referencing variables that aren't in the main program (obviously) and I don't know how to get them to refer to their locations.

If anyone could try compiling and installing I'd appreciate the help. But then again wine works just fine.

---

