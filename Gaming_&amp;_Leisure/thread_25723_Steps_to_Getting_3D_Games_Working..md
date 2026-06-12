---
title: "Steps to Getting 3D Games Working."
date: 2005-04-10
forum: Gaming &amp; Leisure
---

### Post by jdodson on 2005-04-10
I decided to create this guide because it seems people new to GNU/Linux and Ubuntu are having problems getting some basic things done before getting game X to work.  If someone does not seem to have a basic handle on getting 3D working or a game installed, have them come here first.  

Some "quick link" information:

* Want to know if [your card is support in Ubuntu?](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)  
* If your card is not supported I recommend filing a bug report [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com)

Steps

#1) Figure out what kind of video card you have.  If your video card is Nvidia or ATI follow the Ubuntu Guide to getting your 3D drivers installed: 

     * Ubuntu Guide: [http://www.ubuntuguide.org](http://www.ubuntuguide.org) 
     * Official Ubuntu Wiki 3D Guide:  [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)
     * ATI 3D guide: [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557) 

(**Just install the drivers as the guide states, apt-get can do it all for you if you have Nvidia or ATI, you do not need to download any other packages!!!**)  if you are using ANY other brand of video card do a google search for "linux <insert brand> drivers" that should be a good start for you.  I personally recommend Nvidia cards(I have one, it rocks).

If your video card is an **Intel integrated**, check this guide here: [http://ubuntuforums.org/showthread.php?t=27029&highlight=i810](http://ubuntuforums.org/showthread.php?t=27029&highlight=i810)

#1.1) If you are having problems with your Nvidia card, [check this official wiki site for more information.](http://www.ubuntulinux.org/support/documentation/faq/Official_nVidia) 

#2) Now we need to test 3D to see if everything is working correctly.   Open a console and type the following at the command line:

```
glxgears
``` 

Notice the output.  If you are getting > 1000 FPS(frames per second) you should be good to go for most 3D games on GNU/Linux.  If you are getting lower FPS you either have a low end video card or something is configured incorrectly.  check [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for high performance option settings per video card.   

#3) You can now begin 3D gaming, personally I like to download a game from universe to test things out.  Some good ones to try are "tuxkart" or "neverball".  You can also check out the [Uber GNU/Linux games list.](http://ubuntuforums.org/showthread.php?t=5153)

#4) Now you can install your favoriate GNU/Linux game.  Realize that it is better to run native compiled GNU/Linux games such as Unreal Tournament 2004 or Neverwinter Nights than using Winex/Cedega.   Its even better to run free games in universe, and you would be surprised how many great 3D games are included.

#4.1) Remember you must correctly run the installer script to get things to install correctly.  For instance if you are installing Unreal Tournament 2004, put in the CD and from console type the following:

```

cd /media/cdrom0
sh ./linux-installer.sh

``` 

Basically you went to the cdrom directory and called the install script.  the "sh" command before the "linux-installer.sh".  If you see any game installer end in "*.sh" you can type "sh ./whatever-installer.sh" to begin installation.

#4.2)  Some games such as Neverwinter Nights require you to do some craziness to install them.  Doing a Google search can really help this proccess.  You can also check the [Uber GNU/Linux games list.](http://ubuntuforums.org/showthread.php?t=5153)  I have some info on installing games a bit easier for games that a bit terse to install(neverwinter nights install info included).

#5) If you game does not load or quits with an error the first step you should follow is doing a google search with the error message.  Thing is, most people have already had the same problems as you.  So running a relevant Google search is your best friend.  If you still cant get it to run, do a forum search.  If that yeilds no results post a question to the forum. 

-jdodson

last updated 5/15/05

---

### Post by wxm505 on 2005-04-11
I am using a onboard graphics card intel 82852/855.
It worked well under Warty 4.10 but Hoary 5.04.
I am not sure what configure changed after upgrade
by Synaptic.
I tested the 3D of this card. It was not good.

satan@ubuntu:~ $ glxgears
1373 frames in 5.0 seconds = 274.600 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1425 frames in 5.0 seconds = 285.000 FPS
1424 frames in 5.0 seconds = 284.800 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1425 frames in 5.0 seconds = 285.000 FPS

Any help?? Cheers

---

### Post by jdodson on 2005-04-11
[QUOTE=wxm505]I am using a onboard graphics card intel 82852/855.
It worked well under Warty 4.10 but Hoary 5.04.
I am not sure what configure changed after upgrade
by Synaptic.
I tested the 3D of this card. It was not good.

satan@ubuntu:~ $ glxgears
1373 frames in 5.0 seconds = 274.600 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1425 frames in 5.0 seconds = 285.000 FPS
1424 frames in 5.0 seconds = 284.800 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1425 frames in 5.0 seconds = 285.000 FPS

Any help?? Cheers[/QUOTE]

please follow step one.  when you find a solution to your problem post it here, i will add it to the document.  i do not have a integrated intel card(nor do i know if your FPS levels are good for the card you have), so i can not comment on how to get 3D video working in hoary with your setup.

---

### Post by wxm505 on 2005-04-11
I did step one and searched the driver in google.
There is not any drivers avaliable at all.
The point is the card worked very well under warty
but hoary. Do u know what made the changes of the
configure of graphics card and driver after upgrade??
Thanks a lot:)

---

### Post by jdodson on 2005-04-11
[QUOTE=wxm505]I did step one and searched the driver in google.
There is not any drivers avaliable at all.
The point is the card worked very well under warty
but hoary. Do u know what made the changes of the
configure of graphics card and driver after upgrade??
Thanks a lot:)[/QUOTE]

i dont know what changed.  i would submit a bug on this [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com)

---

### Post by Gandalf on 2005-04-11
i have the same video card, and i get the same FPS, i found some drivers but i don't know how to install them, in fact they are designed to XFree86 and don't know how to do with xorg (gives error on install the xfree not activated in kernel), the sources can be found on [http://dri.sf.net](http://dri.sf.net) or directly here -> [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

---

### Post by jdodson on 2005-04-11
[QUOTE=Gandalf]i have the same video card, and i get the same FPS, i found some drivers but i don't know how to install them, in fact they are designed to XFree86 and don't know how to do with xorg (gives error on install the xfree not activated in kernel), the sources can be found on [http://dri.sf.net](http://dri.sf.net) or directly here -> [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)[/QUOTE]

[http://support.intel.com/support/graphics/sb/CS-010512.htm#3](http://support.intel.com/support/graphics/sb/CS-010512.htm#3)

install the "kernel-headers" package via apt-get to build against the kernel.

since i dont have a intel card, i really cant help you beyond the links i provided and having you run a google search.

---

### Post by Gandalf on 2005-04-11
[QUOTE=jdodson][http://support.intel.com/support/graphics/sb/CS-010512.htm#3](http://support.intel.com/support/graphics/sb/CS-010512.htm#3)

install the "kernel-headers" package via apt-get to build against the kernel.

since i dont have a intel card, i really cant help you beyond the links i provided and having you run a google search.[/QUOTE]
 well actually i get the drivers from the link you posted above on intel page, but download it and run install.sh (even if you don't have intel it will make first) you will notice that it's for 2.4.X kernel only so i searched again and found that page which they have a newer version, it supports 2.6.X but unfortunately not xorg

---

### Post by jdodson on 2005-04-11
[QUOTE=Gandalf]well actually i get the drivers from the link you posted above on intel page, but download it and run install.sh (even if you don't have intel it will make first) you will notice that it's for 2.4.X kernel only so i searched again and found that page which they have a newer version, it supports 2.6.X but unfortunately not xorg[/QUOTE]

thats the boat ATI users were in for so long(no 3D xorg support).  if you need 3D i would recommend a revert back to warty with backports.  its kinda lame, but if you want 3D it looks like Xfree might be the only choice.  unless some other person knows a workaround.

---

### Post by Gandalf on 2005-04-11
[QUOTE=jdodson]thats the boat ATI users were in for so long(no 3D xorg support).  if you need 3D i would recommend a revert back to warty with backports.  its kinda lame, but if you want 3D it looks like Xfree might be the only choice.  unless some other person knows a workaround.[/QUOTE]
 hmmmmm... :'( ok no problem, BTW do you have a solution to my wifi problem please?

---

### Post by jdodson on 2005-04-11
[QUOTE=Gandalf]hmmmmm... :'( ok no problem, BTW do you have a solution to my wifi problem please?[/QUOTE]

i have no idea what you are referring to.

this thread is for 3D video problems.  if you have a link to the other thread i can take a swing at it.

---

### Post by wxm505 on 2005-04-11
I think that it is the point. The intel 82852/855 GM card was
supported by XFree86 but Xorg. 
So the only choice is switch to warty or wait for the new driver 
releasing.
Do u think there is a better idea?Or someone will fix this bug soon?
Thanks a lot:)

---

### Post by jdodson on 2005-04-11
[QUOTE=wxm505]I think that it is the point. The intel 82852/855 GM card was
supported by XFree86 but Xorg. 
So the only choice is switch to warty or wait for the new driver 
releasing.
Do u think there is a better idea?Or someone will fix this bug soon?
Thanks a lot:)[/QUOTE]

they have frozen all packages for hoary.  so your best bet is to submit a bug via [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com).  

as far as i can tell your options are:

find a fix.

revert to warty.

wait for new development version to fix problems(if it can)

---

### Post by tormod on 2005-04-11
I put together a tarball with the DRI snapshot 20050311 for the savage video cards. The kernel drivers are for 2.6.11-1-k7. See the included README and install.sh for more info:
[http://tormod.webhop.org/linux/hoary-savage.html](http://tormod.webhop.org/linux/hoary-savage.html)

Tormod

---

### Post by jdodson on 2005-04-11
[QUOTE=tormod]I put together a tarball with the DRI snapshot 20050311 for the savage video cards. The kernel drivers are for 2.6.11. See the included install.sh for more info.
[http://tormod.webhop.org/linux/kernels/hoary-savage.tgz](http://tormod.webhop.org/linux/kernels/hoary-savage.tgz) (1.7MB)

Tormod[/QUOTE]

this is awesome, thank you.

---

### Post by almarag on 2005-04-13
For the sentimentals... if you have some old stuff like games for 486 and so on, you can make work with <a href="http://dosbox.sourceforge.net/">DosBox</a> (apt-get install dosbox). It's Free Open Source MS-DOS clone. I've try to run some really old stuff that I used to play (like Mortal Kombat 3, some old LucasArts like Sam&Max and Maniac Mansion) and it's really awesome. Really retro... :) I recommend you.

almarag.

---

### Post by jdodson on 2005-04-13
[QUOTE=almarag]For the sentimentals... if you have some old stuff like games for 486 and so on, you can make work with <a href="http://dosbox.sourceforge.net/">DosBox</a> (apt-get install dosbox). It's Free Open Source MS-DOS clone. I've try to run some really old stuff that I used to play (like Mortal Kombat 3, some old LucasArts like Sam&Max and Maniac Mansion) and it's really awesome. Really retro... :) I recommend you.

almarag.[/QUOTE]

lucasarts games can be easily run via summvm([http://www.scummvm.org/](http://www.scummvm.org/)) as well.  i would recommend that above dosbox.

---

### Post by chronos on 2005-04-16
I managed to get Quake III working, but when I close the game, it doesn't switch back to my desktop resolution and I have to change it manually... :-? Any suggestions?

---

### Post by crane on 2005-04-16
[QUOTE=chronos]I managed to get Quake III working, but when I close the game, it doesn't switch back to my desktop resolution and I have to change it manually... :-? Any suggestions?[/QUOTE]

I have seen this problem with UT2K4, what res are you running quake3 and what res is your desktop?
Just as a test make sure they are set the same and see what happens. I believe this problem can be fixed with tweaking the XF86Config or xorg.conf files.

---

### Post by crane on 2005-04-16
very nice jdodson,
  Maybe it's time I upgraded to hoary :roll:

I'd like to point out that some games use a .run file to install. These files are also executed with the sh command ( sh linuxq3apoint-1.32b-3.x86.run )

Quake3 is one of the games that use the .run file.
check out [How do i install windows Quake3Arena](http://www.ubuntuforums.org/showpost.php?p=117918&postcount=12) thread!

---

### Post by shakin on 2005-04-16
[QUOTE=wxm505]I am using a onboard graphics card intel 82852/855.
It worked well under Warty 4.10 but Hoary 5.04.
I am not sure what configure changed after upgrade
by Synaptic.
I tested the 3D of this card. It was not good.

satan@ubuntu:~ $ glxgears
1373 frames in 5.0 seconds = 274.600 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1425 frames in 5.0 seconds = 285.000 FPS
1424 frames in 5.0 seconds = 284.800 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1425 frames in 5.0 seconds = 285.000 FPS

Any help?? Cheers[/QUOTE]

I wrote a how-to for integrated Intel video cards. Performance still isn't amazing, but you should hit over 1000FPS. [Here's the how-to guide](http://ubuntuforums.org/showthread.php?t=27029&highlight=i810). It worked on my Intel i915 using the i855resolution tool and the i810 driver.

---

### Post by chronos on 2005-04-17
[QUOTE=crane]I have seen this problem with UT2K4, what res are you running quake3 and what res is your desktop?
Just as a test make sure they are set the same and see what happens. I believe this problem can be fixed with tweaking the XF86Config or xorg.conf files.[/QUOTE]
My desktop resolution is 1280*1024. It works if the Q3 res is set to the same, but it's unplayable because of a crappy graphics card (it's my secondary computer)... :roll:

---

### Post by crane on 2005-04-17
[QUOTE=chronos]My desktop resolution is 1280*1024. It works if the Q3 res is set to the same, but it's unplayable because of a crappy graphics card (it's my secondary computer)... :roll:[/QUOTE]

Thats where the problem is coming in at. I run my desktop and quake3 at the same res.
This can be fixed by tweaking the X config file, but I can't remember how. Try searching for the problem in the forums a bit more. I'm sorry I can't be more help but if I come across the solution I will post it here.!!

---

### Post by gratefulfrog on 2005-05-04
Thanks for the good info!

One note: The following link in the original post from jdodson is full of errors:

[QUOTE=jdodson]
     * ATI 3D guide: [http://ubuntuforums.org/showthread.php?t=3567](http://ubuntuforums.org/showthread.php?t=3567) 
[/QUOTE]
This one is much better:
     [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

---

### Post by theerga on 2005-05-24
When trying to run wolfenstien enemy teritory the screen gose black due to the fact of the virtual screen being bigger thant the actual on i need to edut that one file to stop it from being able to do that where would it be located or what should i type in the terminal

---

### Post by fabiuu on 2005-06-25
oh well hey hey

can u tell me the names of the "great free linux games"?

tks

---

### Post by Omnios on 2005-06-27
I actualy read this on a post a few weeks ago but some of the problems with slower cards is that Hoary dfaults to 25 color depth and aperently in the last release it was defaulted at 16.

 Anyways I just set my color depth to 16 wich is equivilent to XP 24 depth with no noticable difference in quality but my glxgears whent from 400 to 790.

 Though not a total fix it may help out a bit with gaming.

---

### Post by | MM | on 2005-07-12
Ok im all go. UT2k4 64bit linux is going good, one crash while playing an onslaugh game(when i hit a guy in that hover vehicle), but vanilla DM seems crash free.

---

### Post by stretched_lobes on 2005-08-11
Hello I have read all the posts here and I still am having specific problems. I have a native linux port of the original Soldier of Fortune and uake 3 Arena. I bought them before Loki went out of business. I cannot get either to install. I used mandrake prior to ubuntu and they worked perfectly. Do you have any ideas what I am doing wrong. The Loki installer comes up but the option to install is greyed out and not usable on the installer. Thanks for your time.

---

### Post by crane on 2005-08-12
[QUOTE=stretched_lobes]Hello I have read all the posts here and I still am having specific problems. I have a native linux port of the original Soldier of Fortune and uake 3 Arena. I bought them before Loki went out of business. I cannot get either to install. I used mandrake prior to ubuntu and they worked perfectly. Do you have any ideas what I am doing wrong. The Loki installer comes up but the option to install is greyed out and not usable on the installer. Thanks for your time.[/QUOTE]

This may be a dumb question but have you run them as root? I have no experience with SoF but quake 3 should work flawlessly. do you run the installers in terminal? What errors are you getting? If any.

---

### Post by stretched_lobes on 2005-08-13
I will try running it again this after noon. To your questions: Yes I ran the command as root. I really do not get any errors. SOF will pop up the graphical installer, which allows me to do everything but proceed. The Button for next is greyed out. I have been doing some ressearch since. I found an area that has Loki installers and upgrades. Do you think that may work. I will also try quake 3 this afternoon. Thanks for your help will reply soon.

---

### Post by crane on 2005-08-13
[QUOTE=stretched_lobes]I will try running it again this after noon. To your questions: Yes I ran the command as root. I really do not get any errors. SOF will pop up the graphical installer, which allows me to do everything but proceed. The Button for next is greyed out. I have been doing some ressearch since. I found an area that has Loki installers and upgrades. Do you think that may work. I will also try quake 3 this afternoon. Thanks for your help will reply soon.[/QUOTE]
 Cool, I don't see where it would hurt to try them. worst thing is they wouldn't work.
Are you trying an installer for Q3 as well? All you need for 3 in windows is the windows q3 install disk and the .run file.
 I'll be on later  so let me know how it goes.

---

### Post by stretched_lobes on 2005-08-14
sorry I did not get back with you yesterday . I tried this morning finally it installed the program. When I ran it with the command sof in the shell it gave me these messages:

dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Soldier of Fortune (sof-bin). Is SOF_DATA_PATH set?

I actually am installing the game with a loki cd disc commercially purchased. 
 this is the command I used, which launched the installer properly:

sudo sh setup.sh 

(actual command from the games read me file gave : sh setup.sh   as the command)
I am not trying uake 3 since Sof worked flawlessly on mandrake 9.1. Once I figure out what I did wrong here then I will try. It is really frustrating to not have something specifically made for linux to work on one distro and not another. Oh well I am probably doing something that is very minor. Again thank you for your help. and I apologize about yesterday, I had a mechanical emergency in the house, which took most up most of my afternoon.

---

### Post by crane on 2005-08-14
[QUOTE=stretched_lobes]sorry I did not get back with you yesterday . I tried this morning finally it installed the program. When I ran it with the command sof in the shell it gave me these messages:

dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Soldier of Fortune (sof-bin). Is SOF_DATA_PATH set?

I actually am installing the game with a loki cd disc commercially purchased. 
 this is the command I used, which launched the installer properly:

sudo sh setup.sh 

(actual command from the games read me file gave : sh setup.sh   as the command)
I am not trying uake 3 since Sof worked flawlessly on mandrake 9.1. Once I figure out what I did wrong here then I will try. It is really frustrating to not have something specifically made for linux to work on one distro and not another. Oh well I am probably doing something that is very minor. Again thank you for your help. and I apologize about yesterday, I had a mechanical emergency in the house, which took most up most of my afternoon.[/QUOTE]

Hope the mechanical emergency is better now. 
The sof script should just point to the launch script in the directory it was installed. Try using the full path. Something like /usr/local/games/sof/sof

I am unfamiliar with sof, does this game run in linux or use wine?

---

### Post by stretched_lobes on 2005-08-15
Thanks for the help . That did it it works now. SOF is Soldier of Fortune (the original one) The difference is that this game was made for linux only. It was amusing to see the warning on the box that it would not work on windows systems. I also have Quake 3 which was also a linux version. I got a sweet deal on Sof, Heretic2, Heroes of might and magic(cannot remember which number) and descent 3. They were all 2.99 at electronic boutique. i guess it was before Loki went belly up. They all work well except Heretic 2 and Descent 3.  Again thanks for your help I am going to try Quake 3 now to see if it works. Thanks again.

---

### Post by crane on 2005-08-15
cool, glad to here it. If you get quake3 running good you should drop by the House of Pain server. just connect to 207.44.248.20:27969

Thats where I play all the time. I usually play as Crane_ASWP or just Crane. There are some that play there that are really good but everyone shows good manners and is polite. Of they aren't, they are gone. It's really a great place to play.

Oh one more note. Be sure to download pbweb.x86 from they website any run it in you ~/.q3a/pb folder to update punkbuster before playing. This will keep you from getting kicked to spectate while it updates ingame.

Good Luck \\:D/

---

### Post by nERDboY on 2005-08-21
OK maybe im just an idiot but im trying to get wine to work, ive managed with a 2004 .rpm which i converted to a .deb and installed but now ive got a 2005 version in source. ive installed gcc and know ive got to compile it but i have no clue how to compile and then convert to a .deb archive to install from which ios what i think ive got to do 

 :-? thanks

---

### Post by crane on 2005-08-21
[QUOTE=nERDboY]OK maybe im just an idiot but im trying to get wine to work, ive managed with a 2004 .rpm which i converted to a .deb and installed but now ive got a 2005 version in source. ive installed gcc and know ive got to compile it but i have no clue how to compile and then convert to a .deb archive to install from which ios what i think ive got to do 

 :-? thanks[/QUOTE]

Couple of questions:
 What games are you trying to run in wine
 Did you try the wine from the Ubuntu repositories (they may be backported I'm not sure)
 And have you done a search for .deb files?
 I installed an older version of wine from some .deb files I downloaded with no problem. At the time the version in repos was busted.  

oh and you not just an Idiot :grin: 
LOL just kidding man, I know the feeling. Working with linux can make you feel like the smartest guy in the world one moment and a complete idiot the next. Although I'm not a **complete** idiot because I have parts :p  missing.

---

### Post by l0c0dantes on 2005-08-27
Hi there, I try to edit the xorg.conf in the terminal, but i keep getting this message loco@Awesome:/etc/X11$ sudo ./xorg.conf
sudo: ./xorg.conf: command not found
loco@Awesome:/etc/X11$ sudo xorg.conf
sudo: xorg.conf: command not found


I try to go through the file system, and i can open the file, but it is read only, is there anything I can do?

---

### Post by crane on 2005-08-27
[QUOTE=l0c0dantes]Hi there, I try to edit the xorg.conf in the terminal, but i keep getting this message loco@Awesome:/etc/X11$ sudo ./xorg.conf
sudo: ./xorg.conf: command not found
loco@Awesome:/etc/X11$ sudo xorg.conf
sudo: xorg.conf: command not found


I try to go through the file system, and i can open the file, but it is read only, is there anything I can do?[/QUOTE]


You have to use a text editor to make changes.
sudo vi /etc/X11/xorg.conf   to edit in terminal  or

sudo gedit /etc/X11/xorg.conf  to use a gui editor.

---

### Post by daller on 2005-09-13
I have an nvidia card:

0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)

I installed nvidia-glx, and modified xorg.conf (changed from nv to nvidia!)

Running ppracer works fine - but I can't get glxgears to work.

Running glxgears from konsole simple starts the gears, but there is no output (and the gears are quite slow)

Any ideas?

WELL - the guys made me laugh:

glxgears -iacknowledgethatthistoolisnotabenchmark

...damn!

---

### Post by Benzima on 2005-09-13
Well, I tried this and now my system is "in pieces", totally broken. Typing this from my other PC. I thought everything was going pretty good till I got to the stop/start X server. After that, it was command prompt only. I tried to copy back my old xorg.config but that didn't seem to matter. So then I tried to reinstall 5.04. I got Grub error 22, I think. I deleted all partitions and now I have grub error 17 or something. What a mess.

I sux, but I'm not discouraged. "Learn by doing." 

Bak to the drawing board. Guess I better read some more.

---

### Post by daller on 2005-09-21
I have a slightly different problem, installing games:

[http://ubuntuforums.org/showthread.php?t=67850](http://ubuntuforums.org/showthread.php?t=67850)

...My cdrom-drive locks up!

---

### Post by Tiberium707 on 2005-10-01
Can somebody tell me if games like Halo or C&C Renegade or anyother command and conquer games work?What about homeworld?Better yet, are most windows programs compatible with ubuntu?

---

### Post by daller on 2005-10-02
The sound in both UT2004 and Quake3 suddenly disappeared! (maybe after an upgrade - I don't know)

Does any of you have the same problem?

...It only in these 2 games! (Amarok played fine!)

Any suggestions?

---

### Post by heftigrat on 2005-11-09
to jdodson:

you.
rock.

now to get sound working...

---

### Post by daller on 2005-11-10
[QUOTE=heftigrat]to jdodson:

you.
rock.

now to get sound working...[/QUOTE]

It works fine if you kill "artsd"

---

### Post by heftigrat on 2005-11-10
[QUOTE=daller]It works fine if you kill "artsd"[/QUOTE]

Rockin.  Works like a charm.  But of course now I get an err that says "can't save file" or some crap like that, but that one's easy to fix (file permissions).  Thanks for your help!

---

### Post by daller on 2005-11-11
...I'm running all my games with sudo...

---

### Post by heftigrat on 2005-11-11
[COLOR="Black"][FONT="Courier New"]Isn't that a "no-no"?  I thought that could _potentially_ seriously screw up the system.  Or is sudo not quite the same as running as root?

I did find the path RTCW was trying to write to, which is in ~/.wolf, so I just did a "chmod -R u+rwx ~/.wolf".[/FONT][/COLOR]

---

### Post by anemptygun on 2007-11-29
noted'

---

