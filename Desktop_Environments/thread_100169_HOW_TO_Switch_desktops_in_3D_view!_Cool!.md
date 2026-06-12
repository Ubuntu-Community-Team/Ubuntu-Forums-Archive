---
title: "HOW TO: Switch desktops in 3D view! Cool!"
date: 2005-12-07
forum: Desktop Environments
---

### Post by anil_robo on 2005-12-07
First, make sure you have all the repositories and 3D support enabled!
 
1. Open a terminal window, type:
```
sudo apt-get install 3ddesktop
``` press enter
2. 3ddesktop should be installed.
3. you can type 3ddesk and press enter in terminal to run this. (Use arrow keys to change desktops, enter to select that desktop)
 
You'll see something like this:
 
[IMG]http://img215.imageshack.us/img215/4049/3ddesktop7tx.jpg[/IMG]
 
You can switch between desktops by:
1. Using the up and down arrow keys
2. Using the right and left arrow keys
3. Using the mouse scrolling wheel.

**How to make a desktop launcher for 3d desktop:**

1.Right click on an empty area in the taskbar, and click "add to panel"
2. Double click "custom application launcher"
3. Name: 3D Desktop changer
    Comment: My cool 3D Desktop changer (or whatever you like)
    Command: 3ddesk
    Make sure you have "run in terminal" unchecked.
If you want, you can select an icon by clicking on "no icon" button.
4. CLick OK

To run 3ddesktop switcher, just click on the icon you just made on the panel.

**How to assign the windows key to 3ddesktop:**

1. ```
gconf-editor
``` 2. Navigate to apps/metacity/keybinding_commands
3. Choose an empty command (I chose Command_1), double click, set value to 3ddesk
4. Now navigate to apps/metacity/global_keybindings in gconf-editor
5. Find Run_command_1 (or whichever command you chose in step3 above), double click it, set value to Super_L
6. Close gconf-editor
7. Check by pressing your windows key. It should start 3ddesktop.

**Tips:**
1. If the screens come up grey when you first run it, you probably do not have 3ddesktop daemon (3ddeskd) running. So you have to pass a command from terminal manually:
```
3ddesk --acquire=100
```  
2. 3ddesktop has many display modes. Try these:
```
3ddesk --mode=linear --nozoom
``` ```
3ddesk --view=slide
``` ```
3ddesk --view=linearzip
``` 
Other command-line options are:

     --version         Display version information
     --view=xxx        Uses the options from the view in 3ddesktop.conf
     --mode=xxx        Sets the arrangement mode
                        (one of carousel, cylinder, linear, viewmaster,
                         priceisright, flip, or random)
     --acquire[=#]     Grab images for all the desktops by cycling thru
                        (sleep for x millisecs at each screen for refresh)
     --acquirecurrent  Grab image for current desktop
     --nozoom          Disable the zoom out
     --changespeed     Set the rotation speed
     --zoomspeed       Set the zoom speed
     --gotoright       Goto the desktop to the right
     --gotoleft        Goto the desktop to the left
     --gotoup          Goto the desktop to the up
     --gotodown        Goto the desktop to the down
     --goto=#          Goto specified column (deprecated)
     --gotocolumn=#    Goto specified column
     --gotorow=#       Goto specified row
     --dontexit        Don't exit after a goto
     --stop            Stop 3ddesktop (kill 3ddeskd daemon)
     --reload          Force a reload of 3ddesktop.conf
     --noautofun       Don't Automatically turn on Fun Mode
     --revmousewheel   Reverse the mousewheel
     --swapmousebuttons Swap the mousebuttons
     --altmousebuttons Use alternate mousebuttons scheme
     --justswitch      Just switch desktops and acquire without graphics


This is great for people who have not got xgl working yet! Enjoy! :cool:

---

### Post by Rinzwind on 2005-12-07
I looks really really cool but I got a question:

How memory consuming is this?

---

### Post by Sokraates on 2005-12-07
[QUOTE=Rinzwind]I looks really really cool but I got a question:

How memory consuming is this?[/QUOTE]

And how stable?

---

### Post by anil_robo on 2005-12-07
I got a P4 1.73MHz 2MB Cache, 1GB DDR RAM.
On my system, it's as quick as switching desktops the "regular" way. However, since I'm not a geek, I don't know how to check for memory consumption by different applications. Maybe you can search in the forums how to check memory footprint of apps in Ubuntu, then install & run 3d desktop, and check it yourself.

And if you do that, I'd really appreciate if you also post your results to this thread. Thanks and have a great day!

---

### Post by anil_robo on 2005-12-07
[quote=Sokraates]And how stable?[/quote]
Again, SOkraates, I'd recommend you install it (it's from official Ubuntu repositories anyway), use it for some time, and check its stability this way. Please post your results in this thread once you're done with the testing. Thanks! :)

---

### Post by Sokraates on 2005-12-07
Looks as if I've just found a new toy to play with. :D 

BTW, anil_robo: which gfx-card and driver do you use?

---

### Post by Rinzwind on 2005-12-07
It was allready installed on my system  :D

Dell Inspirion 9300 512 Mb: it's too slow. 

I like the way it works tho and since I am going to spend some euro on new memory I'll be using it soon :)

edit: 
Ok I had it going crazy for a minute. Dunno what exactly happend but I had my desktops SPINNING like crazy and when it stopped the enter didn't get me back to the normal desktop :D It looks really cool but I suggest a system with a bit more memory than just 512 Mb :)

---

### Post by anil_robo on 2005-12-07
[quote=Sokraates]BTW, anil_robo: which gfx-card and driver do you use?[/quote] I have intel 915GM chipset, with 8MB onboard RAM. I wanted to have a proper 3D accelerator, but couldn't spare the money :(
Drivers: Ubuntu installed them for me! I didn't do a thing :D

---

### Post by anil_robo on 2005-12-07
[quote=Rinzwind]Ok I had it going crazy for a minute. Dunno what exactly happend but I had my desktops SPINNING like crazy and when it stopped the enter didn't get me back to the normal desktop :D It looks really cool but I suggest a system with a bit more memory than just 512 Mb :)[/quote]

When I used it for the first time, it didn't display all the four desktops. Some of them were shown as blank (see the screenshot in the first post). But after switching through all the desktops through "normal" Ubuntu desktop switcher, 3d desktop 'recognized' all the desktops well, and now it shows every desktop really well!

Beautiful! :)

---

### Post by 0okami on 2005-12-07
been using that for a while. Works flawless for me :) 
can it be assigned a "hot-key"? maybe i can give that "windows" key a new function. 

;)

---

### Post by Rinzwind on 2005-12-07
Hmm after using it for a bit it looks like it's working rather well on  my laptop. 
Even with 512 Mb. 

Damn this is a COOOOOL toy :D I am so gonna use this to bug my colleague's at work :D

---

### Post by anil_robo on 2005-12-07
[quote=0okami]been using that for a while. Works flawless for me :) 
can it be assigned a "hot-key"? maybe i can give that "windows" key a new function. 
;)[/quote]

Article on binding keys to programs: [http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

---

### Post by 0okami on 2005-12-07
[QUOTE=anil_robo]Article on binding keys to programs: [http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)[/QUOTE]

your a god anil_robo :) thanks.

---

### Post by pmj on 2005-12-07
Very cool. I only wish the windows in the 3d view were rendered in real time. As it is now it only shows what the workspaces looked like last time you visited them. Any new windows or information in them won't show up.

Still damn cool though!

---

### Post by anil_robo on 2005-12-07
[quote=0okami]your a god anil_robo :) thanks.[/quote]

I'm not a God. I'm a human being. If I were a God, I wouldn't be able to use Ubuntu, because it's Linux for Human Beings. And I would miss that dearly! ;)

---

### Post by Sokraates on 2005-12-07
Thanks, anil_robo! This app rocks!

Works flawlessly and smoothly on my Athlon XP 2100+, 512 MB RAM, ATI Radeon 9800 Pro (128 MB), fglrx-driver.

---

### Post by syntaxtothe on 2005-12-07
Doesn't seem to work.
[IMG]http://img.photobucket.com/albums/v335/syntaxtothe/Screensho0202t.png[/IMG]

---

### Post by BLTicklemonster on 2005-12-07
[QUOTE=anil_robo]way. However, since I'm not a geek, I don't know how to check for memory consumption [/QUOTE]
So people with alzheim- um alshie- um alzshimer- shoot, I can't spell it, should I be worried?

Bah, so if people who can't remember anything aren't geeks?



Looks like a cool thing, shame I can't remember how to install it.


What were we talkinig about?

---

### Post by anil_robo on 2005-12-08
[quote=syntaxtothe]Doesn't seem to work.
[/quote]

Syntaxtothe!
I think you have some problems with 3d accelerator drivers. I tried to find the solution in the forums, and I think you should make a search for "glxinfo" and "whatever-the-name-of-your-graphic-card-is".

and I'm sure you are not able to run 3d games (sudo apt-get install slune) too!

---

### Post by anil_robo on 2005-12-08
[quote=BLTicklemonster]So people with alzheim- um alshie- um alzshimer- shoot, I can't spell it, should I be worried?[/quote] It's ALZHEIMER'S disease. Somewhat similar to senile dementia, but smoking is incriminated as an etiological factor. CLassical symptoms are amnesia, aphasia, apraxia and agnosia. There is no cure, but ACE inhibitors and similar drugs offer temporary relief.

You should worry about ALzheimer's only after you're old enough! Not right now I guess! :D

> Bah, so if people who can't remember anything aren't geeks? 
[http://en.wikipedia.org/wiki/Geeks]("http://en.wikipedia.org/wiki/Geeks")

> Looks like a cool thing, shame I can't remember how to install it. sudo apt-get install 3ddesktop

> What were we talkinig about? 
I don't know! :rolleyes:

---

### Post by joelito on 2005-12-08
Works on my crapbox

Sempron 2300(~1500mhz)
512 MB Ram
Radeon 9200 128mb w/fglrx(propietary) driver
PC-Chips board w/via823 chipset

---

### Post by syntaxtothe on 2005-12-08
Yeah mate, I've noticed I have a 3d accel problem, I've been trying to debug this sucker for hours and to no avail. So I have to do something like this:? glxinfo Ati all in wonder radeon 7500

[QUOTE=anil_robo]Syntaxtothe!
I think you have some problems with 3d accelerator drivers. I tried to find the solution in the forums, and I think you should make a search for "glxinfo" and "whatever-the-name-of-your-graphic-card-is".

and I'm sure you are not able to run 3d games (sudo apt-get install slune) too![/QUOTE]

---

### Post by VenomousGecko on 2005-12-08
How do you enable the 3d acceleration (or hardware acceleration)?

---

### Post by Sokraates on 2005-12-09
[QUOTE=VenomousGecko]How do you enable the 3d acceleration (or hardware acceleration)?[/QUOTE]

depends on what Gfx-card you're using.

Look here for nVIDIA:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)


and here for ATI:

[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)

---

### Post by Sophisto on 2005-12-09
[QUOTE=anil_robo]I got a P4 1.73MHz 2MB Cache, 1GB DDR RAM.
However, since I'm not a geek, I don't know how to check for memory consumption by different applications.[/QUOTE]

Hmm I *do* know how to check for memory consumption but learning new things in linux has merely helped me to realise my deficiencies... I suppose I am trying my hardest becoming a geek....... But hey, ME loving it!!!!!!!!!

-----------------------------------------------------------------------------------------------------------------------------------

On a serious note; to me, those people who are real geeks are the ones that can only explain something by giving you very sparse information in a high-tech manner as possible (so someone inferior will have to admit it and beg for a simpler explanation). However, I havent experienced this very much on this forum and thats why I really appreciate the Ubuntu community and continue to stick with it!

(I suppose I went a bit off the track but nevermind)

---

### Post by blueturtl on 2005-12-12
I tested the 3ddesktop package and I like what I see: this really gives the user not used to virtual desktops good visualisation of it (thinking about others, not me). However on my system using it causes CPU usage to go up to 5-20% when simply idling! Why is this? Memory I have to donate, but why is it constantly eating at the CPU? I mean you'd think it only uses CPU when you actually switch desks through it...

---

### Post by runlevel0 on 2005-12-12
Not much, it runs a deamon in the background to grab the desktops in a given interval. 

I'm using it instead of the pager.

---

### Post by runlevel0 on 2005-12-12
I have put 3ddesk on a panel so that I can use it instead of the pager.

The panel is bottom, centered and has autohide on. There are 3 icons on it, more or less like this 

< [] >   (two nice 3D arrows and a monitor icon, indeed)

I use the arrows to switch from one desktop to the next and the central icon launches 3ddesk.

The commands for the icons are: 

```

3ddesk --mode=flip --gotoleft
3ddesk --mode=flip --gotoright

```

To get a smooth operation I run the 3ddesk daemon started by the session manager. This daemon can grab the screens of all desktops in the background. Just open the session editor and add this :

```

3ddeskd --acquire=100 --wm=gnome2 --fastest

```

This grabs the screens every 100s using Gnome2 settings and a hack to hog CPU for faster operation. It's not specially CPU consuming...

I use the Flip and linear modes to change desktops, which are not specially spectacular, but my intention was to change desktops in a fluxbox/openbox style...

---

### Post by anil_robo on 2005-12-12
Runlevel0, Great job! Pretty! :)

---

### Post by anil_robo on 2005-12-19
I see many people are having problems with cpu usage with this cool app. I don't have a powerful 3d card myself (onboard intel 915GM), but this app rocks on my laptop! There could be something in your 3ddesktop configuration, or your 3d configuration.

> *This is a nice feature. Unfortunately I had to remove it because it studders my scrolling and window dragging. The CPU peeks to 50% every 2 seconds also.*
                                
Most likely, you're using 3d desktop with *--acquire* option (as suggested by someone else in this thread). This option forces 3ddesk to acquire a screenshot of each of your desktops first by cycling through them, and then starts the program. Try running 3ddesk from a terminal without any options, and you'll be fine.

If you don't like that high cpu usage, you have to disable *--acquire* option.

The 3Ddesktop saves its preferences in /etc/3ddesktop/3ddesktop.conf. Backup this file, and edit it as per your liking! :grin: If you're uncomfortable with editing conf files, you can still get a workaround:

1. open a terminal window, and type **3ddesk --stop**. Press enter. This stops 3ddesktop daemon.
2. Now restart the 3ddesktop daemon in the fastest mode: in the terminal, type **3ddeskd --fastest** and press enter. Please note you should run 3ddeskd for this step, not 3ddesk.
3. Now your 3ddesktop is configured to run in the fastest graphic mode. Test it by typing **3ddesk** in the terminal and pressing enter.
4. Still having problems? You have problems with your 3d graphics hardware. Locate help for installing and enabling 3d support for your graphic card from these forums - do a search! :grin:

---

### Post by David Jaša on 2005-12-28
[QUOTE=Sokraates]BTW, anil_robo: which gfx-card and driver do you use?[/QUOTE]

I'm using it on Celeron 850 with 256 MB RAM and Savage/IX card (8 MB VRAM) and it's smooth.

anil_robo: Great toy. :-)

```
david@david:~ $ ps aux |head -n 1
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
david@david:~ $ ps aux |grep 3ddesk
david    27235  1.6 14.4  44652 36984 ?        SNs  21:44   0:10 3ddeskd
```

---

### Post by bmk789 on 2005-12-31
Can someone tell me what repository it is in?  I'm using AMD64 with a 6800GT and I'm dying to use 3ddesktop, but it doesn't show up in synaptic.

---

### Post by bmk789 on 2005-12-31
nvm, i got it installed and working with the windows key as shortcut.  But, it seems to freeze my comp sometimes and its getting annoying.  Any ideas?

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=bmk789]nvm, i got it installed and working with the windows key as shortcut.  But, it seems to freeze my comp sometimes and its getting annoying.  Any ideas?[/QUOTE]
How does it freeze?  Does it still show the number at the top of the screen?  Try hitting escape.

---

### Post by bmk789 on 2005-12-31
It just stops where its at.  It has all the desktops in 3d with the number at the top.  I've tried escape and noting can unfreeze it.

---

### Post by chimera on 2005-12-31
It works for me, but all the desktops in 3d view have inveted collors (blue instead of red, white instead of black...) how do I fix this?

---

### Post by onesojourner on 2006-01-27
I finally got a new cheap nvidia video card and got this running. its very nice. I set my F12 keybinding to "3ddesk --mode=flip --gotoleft" and its great. I just wish i could figure out how to program it to do that from that little key between ctrl and alt... I just dont know what the name of it is.

---

### Post by jrei on 2006-01-27
If you can't set the keycodes within its config, use the gconf-editor to set gnome keyboard commands, that will work.

I would assume to combine it with "brightside" to activate it when you move a mouse in one of your desktop corners.

Customising the config can also save alot of performance. I had it working on a Pentium 850 with ATI Rage 128/16MB RAM. I don't think there will be a performance problem at all on newer systems.

Greetings, Jörn

---

### Post by onesojourner on 2006-02-01
I just changed this to "3ddesk --mode=cylinder --gotoleft"

that makes it way cooler.

---

### Post by codemills on 2006-02-07
doesnt run in e17 cvs. its cvs i know but common 3ddesktop has option of --wm=enlightenment. shud run i think.

right now it only captures the active workspace not others and i can switch zoom-in/out for only 1 workspace...

anytips? i really want this cool toy to work on e17 ( [http://get-e.org](http://get-e.org) )

---

### Post by ahood on 2006-02-07
I too have got this 3ddesk app working and it is really a cool app. Highly recommended.....

Hardware:
CPU - AMD Athlon XP 2100
RAM - 512 Mb
Graphics Card - Nvidia GeForce 6600GT (AGP) - 256 Mb

I edited the 3ddesk config file to take a screenshot in 512 mode rather than 1024 to convserve RAM.

I use xbindkeys to assign the '3ddesk' command to the keyboard 'Windows' key (between ctrl and alt).

I edited the System --> Preferences --> Session to start 3ddesk (gksudo 3ddesk) and xbindkeys at startup.

It works great. 

I didn't use virtual desktops, but now I do.

Dr. Hood

---

### Post by Zach1188 on 2006-02-13
Sorry to bump an old thread, but...

When I try the first step in the tutorial, it does this:

zach@zCOMP:~$ sudo apt-get install 3ddesktop
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  3ddesktop: Depends: libimlib2 but it is not going to be installed
  cpuinfo: Depends: kdelibs4c2a (>= 4:3.5.0-2) but it is not installable
           Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed           Depends: libidn11 (>= 0.5.18) but 0.5.13-1.0 is to be installed
           Depends: libqt3-mt (>= 3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
           Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
           Depends: libxrender1 (>= 1:0.9.0.2) but 1:0.9.0-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



Not sure if I did it correct, but when I go to "Add to Panel", there isn't even anything with "3" in it. What am I doing wrong?

---

### Post by nalmeth on 2006-02-13
You have a bunch of unresolved dependencies.

In a terminal type 
sudo apt-get -f install

that should clear up all the dependencies, and might install 3ddesktop too. Do you have your graphics card drivers installed?

---

### Post by Zach1188 on 2006-02-13
I installed it using Adept, and made a button for it. 

So I click the button in the task bar, and it just sits there. I pressed the arrows and everything, nothing. Also, I am using KDE (Kubuntu).

When I tried sudo apt-get -f install, I got:
zach@zCOMP:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.

---

### Post by nalmeth on 2006-02-13
Did the install go ok? Adept might have resolved those dependencies automatically for you. From the output of -f install it looks like you're clear. 

Did you make the command for the icon "3ddesk" instead of '3ddesktop'? If so, are your graphics card drivers installed? 

If you get it going, there are also different view modes that you can select with commands.

To see what it can do, in a terminal, type:
3ddesk --help

When I used to use kde, I made a folder in my home folder, and created shortcuts for commands so I could click for different view modes. I then added a quick-browser on my panel to this folder, so I had a sort of 3ddesktop panel applet. 3ddesk --acquire is good (um, if that is the actual command)

---

### Post by Zach1188 on 2006-02-13
I did everything you said, and still, it just sits there when I click it.

How do I install my graphics card drivers (I am using a 128 mb ATI Radeon) ? I have also noticed that animations run slowly in linux, when they would normally run fast in windows. When you drag the mouse on the desktop (To select multiple icons), the square it makes lags insanely.

---

### Post by exofire on 2006-02-13
[QUOTE=Zach1188]I did everything you said, and still, it just sits there when I click it.

How do I install my graphics card drivers (I am using a 128 mb ATI Radeon) ? I have also noticed that animations run slowly in linux, when they would normally run fast in windows. When you drag the mouse on the desktop (To select multiple icons), the square it makes lags insanely.[/QUOTE]

I have an ATI Radeon 9800 PRO.

Here is some info on how to get your ATI card working, at least it worked for me:

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)

and

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5-inst.html)

I hope this helps.

---

### Post by nalmeth on 2006-02-13
Yeah, definately sounds like 3d-acceleration is not setup. My graphics card was setup out of the box, so I don't know a whole lot about setting them up. A quick search of these forums got me this, this might be a good place to start:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
[http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378)
I wouldn't stray too far from these forums, because here you'll find information thats more particular to you and the system you're using.

---

### Post by nalmeth on 2006-02-13
- BTW for everybody using 3ddesktop -

If you use it alot, does it tend to slow down you graphics performance? Using 3ddesktop a couple of times makes my screensavers skip, and slows games down too.

I have 128 megabyte graphics card, but it is a built-in intel, so that may explain things..

---

### Post by Zach1188 on 2006-02-13
[QUOTE=exofire]I have an ATI Radeon 9800 PRO.

Here is some info on how to get your ATI card working, at least it worked for me:

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)

and

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5-inst.html)

I hope this helps.[/QUOTE]
Thanks for that, the problem is, I do not know which ATI Radeon graphics card I have. How do I find out?

Edit:
I found the paper I got when I purchased my computer, and my graphics card is listed as "128MB ATI and Mobility Radeon X300, for Inspiron 9300."

Edit2: I went to the Notebook section, but one file is a .run file, and the rest are .rpm files, how do I install them?
[B]
Edit3:
I discovered my stupidity, lol, and I installed the driver. It did not do a single bit of good. I got no error messages or anything. Dragging on the mouse on the desktop still has the laggy square issue.[/B]

---

### Post by nalmeth on 2006-02-13
> one file is a .run file,  
sudo sh whatever.run
> 
and the rest are .rpm files,
to install rpm's (for future reference, or if you want to do it that way):
sudo apt-get install alien
cd /(directory that the rpm is in)
sudo alien whatever.rpm
sudo dpkg -i whatever.deb

basically, .rpm's are installation packages for red hat, just like ubuntu and debian have .debs. Alien turns the .rpm into a .deb, which you install with dpkg. I don't know if there is a user interface for this or not, if you don't like the terminal.

Check this page again to make sure you're following right procedure for Ubuntu
[http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378)

> I discovered my stupidity, lol, and I installed the driver. It did not do a single bit of good. I got no error messages or anything. Dragging on the mouse on the desktop still has the laggy square issue.

EDIT: No ones stupid for not being able to figure out a new system with a snap of the fingers! Did you reboot the computer? Did you install the right driver for your specific card, and not the one that is already included in the kernel again?

---

### Post by Zach1188 on 2006-02-14
I think I downloaded the correct one (For notebooks), but I could not find one for a X300. Also, I did reboot my computer.

---

### Post by Piggah on 2006-02-14
Not sure why, but whenever I have this running, everything is really laggy. As soon as I stop the daemon it goes back to normal. I have 3.2GHz p4 and 1 gig of RAM, so I don't see it's a problem...

Suggestions?

---

### Post by nalmeth on 2006-02-14
In a terminal, type:
lspci

look for a line that has ATI in it, I believe it will tell you what model you have

---

### Post by kojikabuto_l on 2006-02-14
It works like a lightning for me!!  \\:D/ 

P4 2.4 Ghz + 1 Gb Ram + Nvidia 6600 GT

Its is posible to have a diferent wallpaper for each Desktop ?

There is a combo to switch panels? for example CTRL+ mouse wheel

---

### Post by fraction on 2006-02-14
[quote=lspci]
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
[/quote]I've got a crapy SIS card.  Does this mean I'll never get it working? :(

---

### Post by Zach1188 on 2006-02-14
Edit:
I figured out what was wrong. When you install the driver, it makes a new xorg.conf in /home/<name>/

So simply backup your xorg.conf, and paste the one it made into that.

Now my computer runs a LOT faster (Just like windows), and the game "Slune" runs like a dream, even on high resolutions. Thanks for the help!

---

### Post by astronerd on 2006-02-15
Hi, I think I have an ATI X300 video card, but when I did 
lspci | grep ATI
to find out what card it was it gives me back 
 lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70

Is there another way to find out if I can use this card for this without trying it and borking my system?

---

### Post by dcstar on 2006-02-15
[QUOTE=astronerd]Hi, I think I have an ATI X300 video card, but when I did 
lspci | grep ATI
to find out what card it was it gives me back 
 lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70

Is there another way to find out if I can use this card for this without trying it and borking my system?[/QUOTE]
See if **lshw** gives you more info in the display report.

---

### Post by namit on 2006-04-17
I am gettting this error message
Can anyone help?

Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

---

### Post by pestypest on 2006-04-30
[QUOTE=namit]I am gettting this error message
Can anyone help?

Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)[/QUOTE]

getting something the same need some help here plz


aemon started.  Run 3ddesk to activate.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
jason@jason:~$ Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.

---

### Post by YaNoS on 2006-04-30
I'm getting

```
Attempting to start 3ddesktop server.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)
```

Sucks :-k

---

### Post by Mikebgr on 2006-05-01
nifty program! lots of thanks

---

### Post by YaNoS on 2006-05-01
Now I'm getting the same error as the guys above?
How do I configure hardware acceleration?

---

### Post by skinnygmg on 2006-05-19
this is what i get when i try the first command:

```

$ sudo apt-get install 3ddesktop
Reading package lists... Done
Building dependency tree... Done
3ddesktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

i ran apt-get update.  any suggestions

---

### Post by coolclassic on 2006-05-21
I have installed 3ddesktop using synaptic and then using the command line enter the command "3ddesk" at this point kde shutdowns and nividia software is reloaded and then leaves me with kde login. 

How do I get 3ddesktop working.

---

### Post by blakegrover on 2006-05-23
I have a Dell Inspiron 9300 with the ATI X300 Mobility card and when I run 3ddesk to switch it locks up xorg and I have to switch to a terminal and kill 3ddeskd

the error it gives me is

fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!


any help ? I also have problems with fliipscreen3d screensaver with same error message

using the latest ati driver

Blake

---

### Post by blakegrover on 2006-05-25
Just so everyone who has a Dell Inspiron 9300 with the ATI card and wants 3ddesktop to work I just installed the latest ati driver  8.25.18 and it works great!!!!

---

### Post by gamgee911 on 2006-05-29
I'm on Drapper Drake and I put in the command and i get "E: Couldn't find package 3ddesktop"
 I really want this program, what do i do to get it?

thank you for your help

---

### Post by mats-a on 2006-05-30
I get the same error, nice if anyone could help me

---

### Post by blakegrover on 2006-05-30
You need to make sure to edit the file /etc/apt/sources.list and take out the # sign in front of the other repositories in the file.  Then run apt-get update and then try to install 3ddesktop

Blake

---

### Post by Lunar_Lamp on 2006-06-02
Hmm, I love this application, but unfortunately I have 1 minor qualm with it.

Firstly, it calls the workspaces "1" "2" "3" etc, as opposed to my names that I have input.  It would have been nice to have it call them what I call them (example, system, work, leisure, chat or whatever).

---

### Post by coolclassic on 2006-06-02
[QUOTE=Lunar_Lamp]Hmm, I love this application, but unfortunately I have 1 minor qualm with it.

Firstly, it calls the workspaces "1" "2" "3" etc, as opposed to my names that I have input.  It would have been nice to have it call them what I call them (example, system, work, leisure, chat or whatever).[/QUOTE]

I like that idea, I think it might be as simple as getting the source code and editing it.

---

### Post by tribaal on 2006-06-02
Wooooohhoooooo!

You just gave me one more reason to love linux :)

- trib'

---

### Post by rippon on 2006-06-11
Is there any way to make it so the mouse wheel changes it. Because it seems kind of stupid and an overly lengthy operation to have to click on a program just to change the desktop and all....

---

### Post by Linutz on 2006-06-12
I dual boot Ubuntu 6.06 amd mepis 6 beta and it works in both, but it really flies in mepis.

Great app!!! I hope it continues to evolve.

Thanks :D

---

### Post by oranjy on 2006-06-13
Hi

Everything works fine so far. I have a couple of questions though.

1) When I first start it the screens go grey. I typed the code into the terminal to get the daemon running which is fine but is there anyway to keep it running all the time? It seems to turn off once I restart...

2) I've installed a program now so that I can have different pictures on different workspace backgrounds but they dont show up on the 3D view when I'm going round them. Is there any way to fix this?

Sorry if these are basic questions but I'm new to ubuntu :oops:

Thanks

---

### Post by gmanpsycho on 2006-06-21
It works for me... Dell Inspiron 5150 w/ GeForce FX Go5200.... smooth.... running VMware server with WinXP SP2....


Squeeeet!

---

### Post by H.E. Pennypacker on 2006-06-21
I never use multiple desktops (workspace).  I only use one, and that's why I am looking for an applet/application that will allow me to **switch windows**, not desktops, in much the same way as 3D-Desktop.

Ideally, I'd have something like Windows Vista's Flip 3D feature, shown here:

[img]http://www.winsupersite.com/images/reviews/vista-5219-review-flip3d.jpg[/img]

Anyone know of one?

---

### Post by searayman on 2006-06-21
ok igot it to work on my computer and love it, but i have one question. I use gaim for instant messanger, and liek to keep that opne on another desktop like desktop 2. I do my internet surfing on desktop 1 and can hear if somone ims me on desktop 2, and then i switch over to it. I like hearing the nise from desktop 2 but when somone ims me there but i dont like how when i am on desktop 1 there im box shows up in the panel. is there anything i can do about that?

---

### Post by Mr. Fa on 2006-06-22
Can anyone change the zoom-out depth for carousel mode, i tried to add "depth   10 " to the 3ddesktop.conf file under the default view, but no luck. can anyone help, pls? 
Thx in advance

---

### Post by poor_kenny on 2006-06-26
[QUOTE=Mr. Fa]Can anyone change the zoom-out depth for carousel mode, i tried to add "depth   10 " to the 3ddesktop.conf file under the default view, but no luck. can anyone help, pls? 
Thx in advance[/QUOTE]

If you're using something like "3ddesk --mode=carousel --gotoleft --dontexit" in the command line or launcher (like was mentioned earlier in this thread) then you're not using the default "view". To use that one you'd just use "3ddesk" without any other commands 
(it would basically be "3ddesk --view=default")

After loooking through the config file I just put together my own and put it with the examples. It looks like this:

view     custom
mode    cylinder
show_digit    off
frame_color   blue
use_wireframe true
randdelay   10
zoom         on
depth         6
gotoright    on
dontexit     on
animation_speed  20
changespeed  20
zoomspeed  20

So I just use "3ddesk --view=custom" in a launcher or command line. 

BTW: I found a depth of 6 about right. 10 would put it way out there!

The "frame_color" and "use_wireframe" works well. you don't get the ugly gray screens for the ones that aren't cached. It's a good alternative to running it in the session manager as Runlevel0 was talking about.

I also threw in a nice blue sky background image that I found in a google search; scaled it down to 512x512 and stuck it in there!

# Examples (uncomment to use)
#
#texturesize 512
#wm          kde2

wm   gnome2 
texturesize   512  
default_background    /usr/share/3ddesktop/bg_image.bmp
default_background_texturesize   256

--------
This thing is pretty cool!

---

### Post by N8MAN1068 on 2006-06-26
How do you take a screenshot in 3ddesk mode? 

Also, and this is off topic, but when I have applications open and switch desktop, they show as minimized or whatnot on the status bar. Any way I can have each desktop only show what is open in that desktop on the status bar?

---

### Post by tobeon on 2006-06-26
is there a way of getting rid of the big green numbers?

---

### Post by poor_kenny on 2006-06-26
[QUOTE=tobeon]is there a way of getting rid of the big green numbers?[/QUOTE]
tobeon: you can just edit the 3ddesktop.conf file. you might want to do a backup first: sudo cp /etc/3ddesktop/3ddesktop.conf /etc/3ddesktop/3ddesktop.conf_backup

then just: sudo gedit /etc/3ddesktop/3ddesktop.conf 

just set the "show_digit" to "off" on whatever view configuration you're using. (or put "show_digit off" in if it's not there.) When I set the show_digit to "off" on the default "view" configuration it worked. (I left the "digit_size   100" and "digit_color   green" in there.) I was still just using "3ddesk --mode=cylinder --gotoleft --dontexit" in a launcher when I did that so it must've been using the default "view".

I suggest you just make your own "view" configuration. you can take a look at my previous post. I think the author intended folks to do that, he explains it pretty well.

..."N8MAN1068" --- no I don't think you can take a screenshot 'cause 3ddesktop is basically working with one already (the way I understand it). Same reason for just seeing what is open on your current desktop on the status bar.

---

### Post by shepherdnick on 2006-06-26
Hi there,

Been following the guides on this thread and in other threads and now having successfully upgraded my drivers (and installed that funny little control panel thing) I am still having trouble getting this to run with my ati RADEON XPRESS 200M card that's in my laptop.

I'm getting that ever abundant message that I should configure my hardware acceleration but I have no idea if it needs it or how to go about it.  To be honest, I don't think it does, it runs HL2 fine in XP.

Please let me in on any info/help you may have :D

Nick

---

### Post by pimpaulogy on 2006-06-28
I also have been reading through this entire thread a got some good ideas on how to get 3ddesktop to work.
Here's my issue:
If my machine in freshly booted, I can run 3ddesk and I get the default settings and everything runs smooth, as expected.  I then start to use some of the other settings with mode switches and gotoleft/right switches, and then all of a sudden, it starts to perform extremely slow.  If I just type 3ddesk, it takes on the mode that was last used and moves extremely slow during the zoom and rotation from desktop to desktop.  If I do a 3ddesk --stop, and then just run 3ddesk again, same results.  If I reboot, then it's back to normal speed again.
Does anyone else experience this and found a way to fix it?  I have setup a couple of icons to do the fliping and rotating for me for convenience, but it's not worth it when it suddenly starts to run slow.

---

### Post by poor_kenny on 2006-06-29
[QUOTE=poor_kenny]

> Originally Posted by Mr. Fa
Can anyone change the zoom-out depth for carousel mode, i tried to add "depth 10 " to the 3ddesktop.conf file under the default view, but no luck. can anyone help, pls?
Thx in advance

If you're using something like "3ddesk --mode=carousel --gotoleft --dontexit" in the command line or launcher (like was mentioned earlier in this thread) then you're not using the default "view". To use that one you'd just use "3ddesk" without any other commands 
(it would basically be "3ddesk --view=default")
[/QUOTE]
Turns out was wrong about that. #-o I apogize. Running something like "3ddesk --mode=carousel" *would* use the default "view".  After messing with the "depth" myself a little I noticed there wasn't much difference between the "depth 10" setting and the setting that is default. Maybe that's what's going on. Sorry about that! 

[QUOTE=pimpaulogy]
If my machine in freshly booted, I can run 3ddesk and I get the default settings and everything runs smooth, as expected.  I then start to use some of the other settings with mode switches and gotoleft/right switches, and then all of a sudden, it starts to perform extremely slow.  If I just type 3ddesk, it takes on the mode that was last used and moves extremely slow during the zoom and rotation from desktop to desktop.  If I do a 3ddesk --stop, and then just run 3ddesk again, same results.  If I reboot, then it's back to normal speed again.
[/QUOTE]
I seemed to have that problem too at first. I changed the window manager ("wm") to "gnome2" and if I remember correctly that helped. I also changed the "texturesize" to 512 which gets it to cache a smaller image file size.

In the 3ddesktop.conf file look for this:
[COLOR="Sienna"]
# Examples (uncomment to use)
#

#texturesize 512

#wm          kde2
[/COLOR]
...and below it add in:
[COLOR="Sienna"]
wm           gnome2 
texturesize   512  
[/COLOR]
Hopefully that will help.

---

### Post by toolazy2work on 2006-07-28
to anil_robo
It sounds like the reason for that is that you dont have the 3ddeskd service running.  run "3ddeskd -aquire 0" i beleive that should solve your problem.  
to everyone,
I have been having a problem with the depth variable in 3ddesktop switcher.  The variable only works sometimes with certain modes.  I have to change the mode to linear and then change the depth in order for it to change.  I was wondering if anyone else was having similar problems or if anyone had a solution.
Thanks 
toolazy2work

---

### Post by Sybux on 2006-08-03
I've just discovered 3D Desktop and it's very nice and funny.
But I've got a problem with it. When I invoke 3ddesk with my hot keys, the displays are never refresh.

Is there a way ? I'm running 3ddesk -acquire=100 but it doesn't seems to works.

Some help should be welcome !

---

### Post by clyde9999 on 2006-08-12
I really like the 3D Desktop. It works great for me!!!

---

### Post by Psquared on 2006-08-14
awesomely cool; now, if we could just manipulate the screens with the mouse and move them around anywhere we want. Somebody was working on that using an experimental desktop, called Matisse, but I never heard anymore about it.

---

### Post by Lopsicle on 2006-08-17
Got it working using the windoz button, looks great thank you :D

---

### Post by rusyear04 on 2006-08-21
thank you very much!!

...after a long search for this little piece of pleasure (and lots of lost nerves) your article has helped me (=a bloody beginner with unix/linux) a lot!

thanx!!

---

### Post by jasongamer14 on 2006-08-23
I have a problem people!
i have installed 3ddesktop
but in terminal when i type 3ddesk it says 
bash: 3ddesk: command not found
does anyone no how to fix this im very annoyed](*,) 
if you do can you email me at [email]jason.jaws.13@hotmail.co.uk[/email]
or just reply on here!

---

### Post by Nikola.srb on 2006-10-08
whow, this 3ddesk is great thing to play with :)

I hope it can be setup to start by some mouse button (I don't use even half of those little things :) )

---

### Post by boz on 2006-11-10
AMD Mobile Sempron 1.8G nVidia GeForce 6050 w/ latest driver.  Works GREAT.  I only use 20-30% CPU and barely any memory when switching desktops.

---

### Post by adam98971 on 2006-12-29
this looks really cool i hope that my 512 can handle it tho


edit- works great! and not memory consuming for me :D also is there anyway to change the black background?

---

### Post by NoJock on 2006-12-29
Ok that would be great but it doesnt work at all on my 1.2g celeron with 640 meg ram. the results are below and i am verry green to linux. This is my edubuntu partition.

lee@lee-desktop:~$ 3desk
bash: 3desk: command not found
lee@lee-desktop:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

---

### Post by wesley_of_course on 2007-01-03
Way  COOL!  Luv it and BIG  Thanks !

  :-k  ,  Beryl / Compiz  hhhmmmmm ,,,,,,,,,

P-4  1.6  
Nvidia


:cool:

---

### Post by shadowsypher on 2007-01-20
NoJock Looks like you need to install ur vid drivers and then xgl

---

### Post by jpyanowski on 2007-01-20
A great find for old laptop users!!! Works great. Thanks for the info.=D>

---

### Post by Orfeus on 2007-02-18
I only have one desktop slide. The other one is grey.Why?

---

### Post by ayed on 2007-02-18
It did not work for me!
Got this people!!:
[B]ayed@ayed-desktop:~$ (3ddeskd)
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
ayed@ayed-desktop:~$ 3ddeskd
Daemon started.  Run 3ddesk to activate.
ayed@ayed-desktop:~$ 3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.[/B]

---

### Post by Orfeus on 2007-02-18
i had the same problem. You have to configure ur graphics card

---

### Post by ayed on 2007-02-19
How do I do that? My video vard is 128 mb, nVida 5200?
Please Help!

---

### Post by nandanator on 2007-02-28
Hello Friends

I installed 3ddesktop and did the basic commands but iam facing this message whenever i type "3ddesk" in the terminal

Message
-------------


nandu@nanduz-rig:~$ 3ddeskd --acquire=100 --wm=gnome2 --fastest
Could not find more then one virtual desktop!

================================================================
3ddesktop will be acquiring images in one moment. Please wait...
================================================================

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.


Could anyone help me with this?
Thanks in advance.

Regards
Nandu

Specs
====
AMD64 3000+
512MB DDR400 Hynix
ASUS A8N-VM MoBo with nVidia 6100 and nForce 410

---

### Post by FaceLeg on 2007-03-01
Hi guys!

After some fiddling I have figured out how to configure 3dDesk to show a pic in the background.

For about an hour I tried doing this by adding the options:

default_background /media/DaDeng/Pictures/Neurons/neuron.bmp
default_background_texturesize 512
screen_width 1024
screen_height 768

Into a custom "view".

e.g.

view         default    ## this is the default if no --view specified
mode          random
zoom         on
show_digit   on
digit_size   100
digit_color  gray
use_breathing false
default_background /media/DaDeng/Pictures/Neurons/neuron.bmp
default_background_texturesize 512
screen_width 1024
screen_height 768

As soon as I bothered to read the entire config file, I realised why this wasn't working...

The commands pertaining to background pictures are global, meaning they affect all views.
This means that they need to be set above the first view.

The relevant section of my current 3ddesk.conf reads:

default_background /media/DaDeng/Pictures/Neurons/neuron1024.bmp (1)
default_background_texturesize 1024 (2)
screen_width 1024
screen_height 768

view         default    ## this is the default if no --view specified
mode       random (3)
zoom         on
show_digit   on
digit_size   100
digit_color  gray
use_breathing false

(1) Note that the full path for the file is required.
     I would like to add that I have successfully used .jpg files for my backgrounds, and files with sizes over 512.
(2) This and the two commands below I added "just to be sure" and seeing as it works, I can't be bothered removing them.
(3) A random mode will be used each time.

Also if you press 'b' while switching it makes your windows look transparent.

Hope this was helpful.

---

### Post by jkvelu on 2007-03-12
i am getting confused after reading the 11 page thread..( am new to Linux guys..)

is there any simple way to do the 3D Desktop..

```
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

```

---

### Post by Damo1976 on 2007-04-04
Hi,

This is great.

Is it possible to zoom out a bit less though?
My desktops are like specs on the horizon (slight exaggeration)

Somewhere half way between no zoom and normal zoom would be great.
Great programme though

Cheers,

Damian

---

### Post by BLTicklemonster on 2007-04-04
Another cool toy!!!

---

### Post by Damo1976 on 2007-04-04
How do I edit the config file?
I can't find it.

Cheers

Damo

> **FaceLeg said:**
> Hi guys!

After some fiddling I have figured out how to configure 3dDesk to show a pic in the background.

For about an hour I tried doing this by adding the options:

default_background /media/DaDeng/Pictures/Neurons/neuron.bmp
default_background_texturesize 512
screen_width 1024
screen_height 768

Into a custom "view".

e.g.

view         default    ## this is the default if no --view specified
mode          random
zoom         on
show_digit   on
digit_size   100
digit_color  gray
use_breathing false
default_background /media/DaDeng/Pictures/Neurons/neuron.bmp
default_background_texturesize 512
screen_width 1024
screen_height 768

As soon as I bothered to read the entire config file, I realised why this wasn't working...

The commands pertaining to background pictures are global, meaning they affect all views.
This means that they need to be set above the first view.

The relevant section of my current 3ddesk.conf reads:

default_background /media/DaDeng/Pictures/Neurons/neuron1024.bmp (1)
default_background_texturesize 1024 (2)
screen_width 1024
screen_height 768

view         default    ## this is the default if no --view specified
mode       random (3)
zoom         on
show_digit   on
digit_size   100
digit_color  gray
use_breathing false

(1) Note that the full path for the file is required.
     I would like to add that I have successfully used .jpg files for my backgrounds, and files with sizes over 512.
(2) This and the two commands below I added "just to be sure" and seeing as it works, I can't be bothered removing them.
(3) A random mode will be used each time.

Also if you press 'b' while switching it makes your windows look transparent.

Hope this was helpful.

---

### Post by smartboyathome on 2007-04-05
> **anil_robo said:**
> 
[IMG]http://img215.imageshack.us/img215/4049/3ddesktop7tx.jpg[/IMG]


Any idea how to get your desktop to show up?

---

### Post by abtin_j on 2007-04-18
so i got 3d desktop installed... its working quite well, but i cant get to 'personalize' my 4 different desktops meaning i cant have a different wallpaper assigned to the different screens...? is that normal? how can i go about doing that? any replies would be highly appreciated. cheers :)

---

### Post by FaceLeg on 2007-04-22
> **Damo1976 said:**
> Hi,

This is great.

Is it possible to zoom out a bit less though?
My desktops are like specs on the horizon (slight exaggeration)

Somewhere half way between no zoom and normal zoom would be great.
Great programme though

Cheers,

Damian

You will be able to change the zoom level by altering this file:

```
sudo gedit /etc/3ddesk.conf
```

I recommend you read this first, however, as it contains a detailed guide for changing settings in this program.

[http://linuxreviews.org/features/3ddesktop/#toc1](http://linuxreviews.org/features/3ddesktop/#toc1)

---

### Post by picpak on 2007-05-21
> **FaceLeg said:**
> Also if you press 'b' while switching it makes your windows look transparent.

And pressing 'm' changes the transparancy of the windows. :)

---

### Post by green-12 on 2007-06-21
*NEWB HERE*

I followed the instructions to set the windows key as the hot-key but it isn't working? Does anyone else have this problem? Advice?

---

### Post by tom1g on 2007-06-25
hi, I just got ubuntu running on my PC.

first i looked for 3d desktop (all my friends are talking about it)

well, the problem is it doesn't work on my machine... :(


i copypasted this into the terminal:

sudo apt-get install 3ddesktop

and I tried to ran it by typing 3ddesk into the terminal but i got this message as reply:

Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)


any help?

thx

---

### Post by tom1g on 2007-06-26
please help people =(

---

### Post by tjpais on 2007-07-26
so i juss installed this and it only gives me 2 desktops...how do i get the 4 desktops as shown in the screenshot ? how many more desktops can u add?

---

### Post by tjpais on 2007-07-26
> **tom1g said:**
> please help people =(

hey man i had the same problem..it was because my gfx card was not installed....the fglrx driver for ATI does not supper x1300,1400,1500,1600 and up to 1900 so i installed this program called ENVY and that installs ur gfx drivers for you and now it works. except i dont see all 4 desktops.

hope that helps

---

### Post by dezavoo on 2007-08-29
Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

---

### Post by Chicago on 2007-08-30
Hi,
I downloaded and installed 3ddesktop, typed 3ddesk and got the 3ddesktop but only 1 desktop.  After I edited the gconf file I couldn't get the 3D effects back.
I have AMD Athlon 64; 512MB DDR2 nVIDIA GeForce 7300GS
1 GB DDR

Can anyone give me an idea as to what has happened.  Be gentle, I'm new with linux!

---

### Post by mahasmb on 2007-09-09
Bery and Compiz-Fusion are a hassle to install with ATI and Intel vIdeo cards. 3D Desktop is a good substitute for until Gutsy Gibbon comes out next month (I hear it's going to come with Compiz-Fusion already included).

Thanks a lot for this how to!

---

### Post by superdif on 2007-09-09
In my system works (Kubuntu 7.04, Intel Core 2 Duo 6700, 2Gb DDR2 800 ram, Nvidia 8800GTX), but there is a small (but very annoying) problem.

Every time I use it, I get the the 3ddesk icon on the task bar for about 30 seconds; after these seconds it disappears, but while is there if I (mouse) scroll anything (like a web page) the scrolling is jerky (after 3ddesk disappears from the task bar,  the scrolling return to be fluid).

---

### Post by Othyz on 2007-11-09
Hi, total new guy here. 3D desktop is not on my system. I think...

Here is the message I get.

[ATTACH]49675[/ATTACH]

Thanks in advance for the patience.

---

### Post by kseise on 2007-11-23
Othyz,
     That error means that 3ddesktop is not in the Gutsy repositories.  I don't know why it has been taken out.  I am looking for it also.  I will post back if I find a solution.

---

### Post by kseise on 2007-11-23
It's not the prettiest solution, but I dowloaded the .deb file from the Debian website.  

[Using this link]("http://packages.debian.org/etch/3ddesktop/i386/download")

I opened the package in the gdebi (default action when you click the link in Firefox).  It check the dependencies and installed just fine.  

Don't forget, the default for Ubuntu is only two desktops.  If you activate 3ddesk, you will only see two desktops unless you change that setting.

---

### Post by love2learn on 2008-03-29
Back from the dead!
I wanted to thank kseise for the fix in gutsy. It is a confirm fix.

Thanks
L2L

---

### Post by obada_aq on 2008-04-11
Hi all,  i am totally new at ubuntu and linux OS, I have typed the command but there was a problem, the terminal shows the following 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 3ddesktop


how can i solve this? (in details, please!)

---

