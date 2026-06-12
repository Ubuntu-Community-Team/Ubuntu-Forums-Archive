---
title: "Improving the NES Emulation Scene on Ubuntu"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by punkrockguy318 on 2006-06-12
Hello!
Over the past few weeks, I have been getting some "Legend of Zelda" cravings.  Too lazy to find my NES, I decided to check out NES emulators for Linux.  The most stable and complete emulator I found was FCE Ultra.  However, the interface was terrible.  There was no GUI, and even the command-line was poor and undocumented.
So, instead of just complaining, I decided to program.  I whipped out vim and glade, and I coded and coded.  And now, we have a mean, clean, emulating machine: gfceu.
Gfceu is a graphical frontend for fceu using python and GTK2.  I have posted tarbells and ubuntu packages on my server located here: [http://dietschnitzel.com](http://dietschnitzel.com)
Please, test and enjoy!  Once the universe repos are up, I'll see if I can get this pushed into edgy.


But wait, there's more!
Many people are unaware that fceu supports network play.  The source code for the server is fairly hidden, but I have whipped up an ubuntu package for it.  You can download the package here: [http://dietschnitzel.com](http://dietschnitzel.com)
To run the server once the package is installed, just run:
```
$fceu-server /etc/fceu-server-standard.conf
```
And your good to go!  Gfceu has network support, so you can connect to the server using that.

---

### Post by fluffington on 2006-06-12
Very nice. It's not very good at handling filenames with spaces or other characters that have special meaning in the shell, though:

```

$ ./gfceu
/home/noah/Desktop/zelda/Legend of Zelda, The (U) (PRG0).nes
GFCEU debug:  command = fceu -sound 1 /home/noah/Desktop/zelda/Legend of Zelda, The (U) (PRG0).nes
sh: -c: line 0: syntax error near unexpected token `('
sh: -c: line 0: `fceu -sound 1 /home/noah/Desktop/zelda/Legend of Zelda, The (U) (PRG0).nes'

```

Perhaps some extra quotes are in order. Also, I can't configure the gamepad(s) if I haven't already selected a ROM, the dialog for configuring the gamepads isn't very intuitive (just a titlebar with the button name on it), and it prompts for each button multiple times.

After I renamed my ROM and figured out the button configuration, though it worked nicely. Keep up the good work.

---

### Post by punkrockguy318 on 2006-06-12
[QUOTE=fluffington]Very nice. It's not very good at handling filenames with spaces or other characters that have special meaning in the shell, though:

```

$ ./gfceu
/home/noah/Desktop/zelda/Legend of Zelda, The (U) (PRG0).nes
GFCEU debug:  command = fceu -sound 1 /home/noah/Desktop/zelda/Legend of Zelda, The (U) (PRG0).nes
sh: -c: line 0: syntax error near unexpected token `('
sh: -c: line 0: `fceu -sound 1 /home/noah/Desktop/zelda/Legend of Zelda, The (U) (PRG0).nes'

```

Perhaps some extra quotes are in order. Also, I can't configure the gamepad(s) if I haven't already selected a ROM, the dialog for configuring the gamepads isn't very intuitive (just a titlebar with the button name on it), and it prompts for each button multiple times.

After I renamed my ROM and figured out the button configuration, though it worked nicely. Keep up the good work.[/QUOTE]

Thanks so much for testing my program.  I've addressed a few of your problems:
Spaces and special characters  - Fixed in 0.1.1
Input configuration without selected ROM - Fixed in 0.1.1
Unintutitive input configuration - This is all handled by fceu itself.  I have contacted the developers of fceu and see if I could get some work upstream done with this, but have received no reply.  FCEU uses a binary configuaration file, and the only way to write input configs is through fceu itself :-\.  Maybe sometime when I'm feeling adventurous I'll check out the fceu source and see what I can do.

For the 0.1.1 release, check out the same place: [http://punkrockguy318.no-ip.org/gfceu](http://punkrockguy318.no-ip.org/gfceu)

God bless and enjoy!

---

### Post by fluffington on 2006-06-12
Wow, that was fast. It works much better now.

---

### Post by punkrockguy318 on 2006-06-12
[QUOTE=fluffington]Wow, that was fast. It works much better now.[/QUOTE]
I hope you enjoy it!  In the next couple weeks I'm planning to add a video tab and an advanced tab.

Also, I'm going to talk to some people and see what the best way is to avoid the gnome-screensaver bug.

God bless,
Lukas

---

### Post by DoktorSeven on 2006-06-13
Please, for the love of all things great and small, have the program remember the last directory you looked for a ROM in, if not every time, at least in the same session.

I stink at Python, but this seemed to do what I'm talking about:
```

--- gfceu-0.1.1/gfceu   2006-06-12 21:04:37.000000000 -0500
+++ gfceu/gfceu 2006-06-13 00:38:38.000000000 -0500
@@ -22,6 +22,7 @@
 """
 import sys
 import os
+import user
 
 try:
   import pytgtk
@@ -36,6 +37,7 @@
   sys.exit(1)
 
 class gui:
+  lastdir = ""
   def __init__(self):
     try:
       self.xml=gtk.glade.XML (os.path.dirname(sys.argv[0])+'/gfceu.glade')
@@ -80,9 +82,12 @@
     filter.add_mime_type("application/x-nes-rom")
     filter.add_pattern("*.nes")
     chooser.add_filter(filter)
-    
+    if self.lastdir == "":
+       self.lastdir = user.home
+    chooser.set_current_folder (self.lastdir)
     response = chooser.run()
     if response == gtk.RESPONSE_OK:
+      self.lastdir = chooser.get_current_folder()      
       self.xml.get_widget('romentry').set_text(chooser.get_filename())
     chooser.destroy()

```

---

### Post by eqisow on 2006-06-13
Fantastic! This is something that's needed very badly. Many thanks for putting this together. Now, that being said, here are my complaints. ;) 

* You have to configure the input for every game you play
* It ask you to program every input twice
* Doesn't remember ROM folder
* No options for screen size / full screen

I'm not sure how many of these relate to your interface and how many are simply the limitations of FCEU. However, if you want to take a look at some excellent emulator interfaces check out Mupen 64, ZSNES, or gxmame. There is also gTuxNES (NES emulator GUI), but it's just not very good imo.

P.S. - If this thing gets popular and you need help with hosting, I can lend a hand. :)

Edit: Also, here's a [list of NES emulators for Linux]("http://64.233.161.104/search?q=cache:DcIRDPC6F74J:www.zophar.net/unix/nes.html+nes+linux+emulators&hl=en&gl=us&ct=clnk&cd=1&client=firefox"). One of them might serve as a better back-end than FCEU. (The link is a google cahce since the actual page seems to be down, so you will have to search for each emulator individually)

---

### Post by punkrockguy318 on 2006-06-13
> **eqisow]Fantastic! This is something that's needed very badly. Many thanks for putting this together. Now, that being said, here are my complaints.  said:**
> list of NES emulators for Linux[/URL]. One of them might serve as a better back-end than FCEU. (The link is a google cahce since the actual page seems to be down, so you will have to search for each emulator individually)

Thanks for your input!
As far as configuring the input, this is pretty much out of my control.  This is all handled by fceu.  I'm not the greatest at interpreting other coder's C, and I was clueless when I looked at the fceu source code.  
I'll definitely add options for fullscreen/windowed and write in code so gfceu will remember the options.

After exploring other emulators, it looks like using a different emulator may be much more usable.  The ones that seemsed particuarlly interesting were iNes and RockNES.  This week I'll see what I can do to package those two for Ubuntu, and code gfceu so it is emulator-independent.  I'd like to shift this project from a gfceu to a gnes sort of project.

---

### Post by punkrockguy318 on 2006-06-13
I mentioned iNes in my above post; unfortunately it is not free.  Perhaps rocknes will work, I'll look more into it.

---

### Post by punkrockguy318 on 2006-06-13
Ah!  Both shot down!  RockNES does not even run on UNIX.  I guess I'll have to keep looking...

EDIT:  There is an older unofficial rocknes port, but it already has an ingame gui.  Also, I don't believe it's open source.

---

### Post by punkrockguy318 on 2006-06-13
** 0.2 released **
I've taken all of your requests into consideration, and here are the changes in this release:
* Fullscreen support
* File chooser looks in last used directory
* All checkboxes and entries are remembered for next opening
* Overall code structure rehaul
* Other minor bugfixes

Please, test and give me more feedback!  Grab the ubuntu packages and tgzs right here: [http://punkrockguy318.no-ip.org/gfceu](http://punkrockguy318.no-ip.org/gfceu)

---

### Post by eqisow on 2006-06-13
This project is looking better and better! I actually think it would be good to have it included in the repositories. If nothing else, perhaps you could set up your own repository for it.

Anyway, here's the things I noticed with this version:

* No option to add scan lines (I think NES/SNES games look better with the scan lines)
* Still not remembering my ROM folder
* Not remembering gamepad configuration (but you said this was an FCEU issue, correct?)

Edit: OK, it turns out that it does remember the ROM folder, sort of. When I close the program and then re-open it it remembers the ROM folder from the last time it ran. However, on the first run, when I open my second (or third, fourth, etc) ROM, it still starts in my home directory.

Edit again: You should definitely release the source code to this thing as well. :)

---

### Post by fluffington on 2006-06-13
Looking better all the time. If I played more NES games, it would have a permanent place on my hard drive.

My only remaining complaint is the gamepad configuration. Displaying a dialog that lets you click the button you want to set and then press it (and display what keys go with each button) would be a huge improvement.

I also second eqisow's scanlines request.

---

### Post by eqisow on 2006-06-13
Actually, I kind of like the way the gamepad programming works now, where it just cycles through the keys and you press the button you want. Perhaps, however, it would be a good idea to implement fluffington's idea, but leave the current button configuration as an option. I think ZSNES is probably the best example of how to do gamepad configuration. Mupen 64 doesn't do as good of a job, but it does have a picture of the N64 gamepad as part of the configuration tool, which I think is acool idea.

Also, if FCEU has support for peripherals (and I'm not sure that it does) such as the light-gun, it would be good if that was included somehow.

---

### Post by punkrockguy318 on 2006-06-13
**Version 0.2.1 released!**
Changelog:
* Fixed the silly file chooser bug where reopening the chooser would reset the folder
* New artwork!
* Desktop file included

In the next release, I'm going to add a video tab, where effects like TV blur, aspect ratio, and scanlines can be configured.

Oh, and about the source?  It's included! :D  It's written in Python, so just open up the gfceu file, and all of the code is right there.

As usual, check out the new release here: [http://punkrockguy318.no-ip.org/gfceu](http://punkrockguy318.no-ip.org/gfceu)

---

### Post by eqisow on 2006-06-13
I was just about to mention the thing about the aspect ratio. Good to see that you beat me to the punch. :p

I think after this next version I'll be out of feature request, at least as far as things that FCEU can handle go. You've done an excellent job with this project thusfar. :)

Edit: BTW, you've officially replaced gTuxNES as my NES emulator of choice!

---

### Post by OrganicPanda on 2006-06-13
dude this thing kicks ***, i always just assumed emulation didnt work on linux (do not ask me why) ... this has opened my eyes and made my day .... back to naked mario (gotta love hacks) woooo

---

### Post by punkrockguy318 on 2006-06-14
NEWS!
I was offered write access to the FCE Ultra source tree, so I can begin moving this application upstream.  Also, if I work on fceu upstream, I'd like to improve the following aspects of fceu:
* Improving the intuitivity of the command-line interface
* Make the input config more usable
* Move from binary config file to plain text

---

### Post by MicroChris on 2006-06-14
This is AWESOME! Great work man.. I plan on following this project.

---

### Post by CronoDekar on 2006-06-14
Sweet dude!  After struggling with core FCEU I kinda gave up on getting it to work, but now this works like a dream.  Thanks, and keep up the good work!

---

### Post by punkrockguy318 on 2006-06-14
Hello,
Since I figured this project was actually useful, I decided to work on my HTML/CSS skills are work up a website.  Check it out:  [http://punkrockguy318.no-ip.org/gfceu/](http://punkrockguy318.no-ip.org/gfceu/)

New releases and things will be announced there.

PS:  If you can't tell, I'm running off of a slowish connection, and a slowish server.  If someone can help me out with some hosting, that would be GREATLY appreciated :D

---

### Post by eqisow on 2006-06-14
I told you I'd help with hosting. Check your PM's. :p

---

### Post by punkrockguy318 on 2006-06-14
[QUOTE=eqisow]I told you I'd help with hosting. Check your PM's. :p[/QUOTE]

Ah great!  I replied!  Sorry, I thought email notifications were on, but they weren't.

---

### Post by punkrockguy318 on 2006-06-15
Good news everyone!  I've been accepted as a FCE Ultra developer.  I've already begun work on the netplay server, and later on this week I'll be moving all gfceu upstream.

If I get a chance, I'd like to improve some things of fceu.  The input configuration system and the binary configuration files can be improved.  I hope to make fceu a killer emulator :p 

I would be hacking away in the svn right now, but it's off to band practice.  Stay tuned guys, good things on the way!

---

### Post by fluffington on 2006-06-15
[QUOTE=punkrockguy318]Good news everyone!  I've been accepted as a FCE Ultra developer.  I've already begun work on the netplay server, and later on this week I'll be moving all gfceu upstream.

If I get a chance, I'd like to improve some things of fceu.  The input configuration system and the binary configuration files can be improved.  I hope to make fceu a killer emulator :p 

I would be hacking away in the svn right now, but it's off to band practice.  Stay tuned guys, good things on the way![/QUOTE]

That's awesome.

---

### Post by deathbyswiftwind on 2006-06-15
I use rocknes for linux its currently my fav nes emu. Unfortunatly it does not contain network play. I have rocknes so if youd like I can post the deb file. Good work with yours though youve improved it much :)

---

### Post by punkrockguy318 on 2006-06-17
Hey guys!  I'd suggest you all check out the newest version: 0.2.2.  The previous releases has a minor issue with the *.desktop file that you many have found quite annoying.  It associated itself with text files in nautilus.

For the newest release, check out [http://punkrockguy318.no-ip.org/gfceu](http://punkrockguy318.no-ip.org/gfceu)

---

### Post by srt4play on 2006-06-17
Thanks a lot for you work on this!  It works great but I have one problem.  I had to install the server with the --force-depends option because it complained about failed dependencies for libc6 and some others.  The server works great.  But now synaptic wants to remove it anytime I go to install packages. 

Is there a way to tell apt/synaptic to leave fceu-server alone and ignore the dependency issues?

---

### Post by CronoDekar on 2006-06-17
[QUOTE=punkrockguy318]Hey guys!  I'd suggest you all check out the newest version: 0.2.2.  The previous releases has a minor issue with the *.desktop file that you many have found quite annoying.  It associated itself with text files in nautilus.

For the newest release, check out [http://punkrockguy318.no-ip.org/gfceu](http://punkrockguy318.no-ip.org/gfceu)[/QUOTE]

Heh, I didn't even notice.  Though oddly, when I purge the old one and install the new one, it reassociates itself with ASCII-based files.  Even deleting the commented MIME type thing doesn't seem to work -- only by deleting the desktop shortcut.  Remaking a shortcut via Alacarte seems to make it work fine.

Odd.  Not a big deal though.

EDIT: OK, when I did a sudo mv gfceu.desktop fceu.desktop it worked fine, so GNOME must be somehow "remembering" the old desktop file or something and reacting to it.

---

### Post by mhancoc7 on 2006-06-17
This is awesome!!! 

I really love this. The only thing that I am having trouble with is the Fullscreen. When I check "enable fullscreen", I get a full screen, but the game is still in the center of the screen surrounded by a large black frame. I mean the game does not stretch to fill the fullscreen. Could someone help me with that?

Great program, God Bless, Jereme

---

### Post by eqisow on 2006-06-17
mhancoc7, that has to do with the fact that there is currently no way to set aspect ratio in GFCEU. However, it is on the to do list.

I have no idea why the default aspect ratio is anything besides 4:3 though.

---

### Post by mhancoc7 on 2006-06-18
Thanks, I will look forward to that feature. 

Great work!!

Jereme

---

### Post by punkrockguy318 on 2006-06-18
[QUOTE=srt4play]Thanks a lot for you work on this!  It works great but I have one problem.  I had to install the server with the --force-depends option because it complained about failed dependencies for libc6 and some others.  The server works great.  But now synaptic wants to remove it anytime I go to install packages. 

Is there a way to tell apt/synaptic to leave fceu-server alone and ignore the dependency issues?[/QUOTE]

The fceu-server package was built on an edgy machine, so I guess it's having some problems on dapper machines.  I hacked up the code a bit and tarbelled a 0.0.4 version of the server.  Once it's officially released, I'll make packages for both Dapper and Edgy.

Thanks for your kind words!

---

### Post by punkrockguy318 on 2006-06-18
[QUOTE=mhancoc7]Thanks, I will look forward to that feature. 

Great work!!

Jereme[/QUOTE]
Thanks for you kind words!

About your fullscreen issue:  it's due to that there is no support for various aspect ratios.  I would like to start working on that, but there are a few other things I would like to improve first.  Unfortunately, it's not a trivial task :-\  But, I will see what I can do.

God bless,
Lukas

---

### Post by MetalMusicAddict on 2006-06-18
I am posting this SVG icon for punkrockguy318 to see. I contacted him about working with him. Hopefully he will let me. ;)

This is a work-in-progress.  Please do not use yet.

---

### Post by Kuprin on 2006-06-18
Never got FCEU sound working in Ubuntu, though I haven't tried especially hard as of late. Sound works in everything else aside from ScummVM, which I'll eventually get around to fixing, I hope...

---

### Post by punkrockguy318 on 2006-06-19
[QUOTE=MetalMusicAddict]I am posting this SVG icon for punkrockguy318 to see. I contacted him about working with him. Hopefully he will let me. ;)

This is a work-in-progress.  Please do not use yet.[/QUOTE]
Hello,
I am overjoyed that you are willing to contribute! :D The icon you've worked up is pretty neat!  I do, however, have something specific in mind if your up for the challenge. I'd like an icon that is simply an NES controller, in a sort of cartoonish style (similiar in style to the other default gnome-games icons).  Would you be up for creating something like that?
Thank you so much for your willingness to contribute! :D 

God bless,
Lukas

---

### Post by punkrockguy318 on 2006-06-21
**Version 0.2.3 has been released!**
Check out the website at [http://punkrockguy318.no-ip.org/gfceu](http://punkrockguy318.no-ip.org/gfceu) for packages.  Enjoy!
Please report any bugs/feature requests here on this thread, to keep everything public.

---

### Post by MetalMusicAddict on 2006-06-21
Sorry I havnt got back about the icon. I am in the middle of selling my house. I have a friend who is a better sketch artist drawing up a cartoon-ish icon for ya. ;)

What the changes in the new package?

---

### Post by punkrockguy318 on 2006-06-21
[QUOTE=MetalMusicAddict]Sorry I havnt got back about the icon. I am in the middle of selling my house. I have a friend who is a better sketch artist drawing up a cartoon-ish icon for ya. ;)

What the changes in the new package?[/QUOTE]
* Network - You can now load ROMS that are on a network share
* Smarter - Gfceu now handles itself better in sticky situations (if fceu isn't installed in path, or glade/gtk is missing or xml files aren't available)
* More descriptive error messages - gives detailed instructions on fixing stuff
* Internals Improved - New messaging system that more applications should replicate.  It print fatal errors to both the command-line and in a GTK message box.  This gets rid of the "silent deaths" that so many linux applications fall under

---

### Post by MetalMusicAddict on 2006-06-21
[QUOTE=punkrockguy318]* Network - You can now load ROMS that are on a network share[/QUOTE]
NICE! This lets me keep my roms in 1 spot on my server. ;)

---

### Post by punkrockguy318 on 2006-06-21
**Version 0.2.4**
There was a bug in 0.2.3, and gfceu wouldn't find fceu if it was in the last entry of the $PATH.  Upgrade to 0.2.4 for the fix

---

### Post by punkrockguy318 on 2006-06-21
[QUOTE=MetalMusicAddict]NICE! This lets me keep my roms in 1 spot on my server. ;)[/QUOTE]
Erg, the network open feature is having troubles.  Wait a couple days and I'll see if I can fix it.

---

### Post by stevejesus on 2006-06-23
This application is GREAT!  Great frontend!  Great WORK!  
And also, thanks for writing it in python!  It made a great architecture independant .deb and it works GREAT on my PowerBook!

---

### Post by punkrockguy318 on 2006-06-23
[QUOTE=stevejesus]This application is GREAT!  Great frontend!  Great WORK!  
And also, thanks for writing it in python!  It made a great architecture independant .deb and it works GREAT on my PowerBook![/QUOTE]
Thanks so much for your compliments!  They really inspire me to keep writing :) It feels good knowing my works are appreciated.

Also, I worked up a new release today.  It's on the site as usual, and you can find the changelog there.  [http://punkrockguy318.no-ip.org/gfceu](http://punkrockguy318.no-ip.org/gfceu)

This release adds support for network ROM loading, as it was broken in 0.2.3 and 0.2.4

---

### Post by stevejesus on 2006-06-23
I would like to help this projects popularity even further.
I am going to bring gfceu to Fedora users.
I will be setting up a fedora 5 box later this evening and start packaging RPM's.
I think I have enough time on my hands that i can package for you for every release (which seems like every day lol).
Also, I think you and I should set up some repositories for apt and yum on my server.
Get back with me!

---

### Post by MetalMusicAddict on 2006-06-23
[QUOTE=stevejesus]Also, I think you and I should set up some repositories for apt and yum on my server.
Get back with me![/QUOTE]
I was thinking the same thing. punkrockguy318 you should talk to Quinnstorm about using her repo for APT. She hosts all her Compiz stuff there as well as a couple of others. Its **deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main**.

---

### Post by punkrockguy318 on 2006-06-23
[QUOTE=stevejesus]I would like to help this projects popularity even further.
I am going to bring gfceu to Fedora users.
I will be setting up a fedora 5 box later this evening and start packaging RPM's.
I think I have enough time on my hands that i can package for you for every release (which seems like every day lol).
Also, I think you and I should set up some repositories for apt and yum on my server.
Get back with me![/QUOTE]
Hey,
  Python supports RPM package generation through the distutils package (what I'm currently using for the build system - setup.py).  Perhaps with a bit of tweaking on my build system, the RPMs could be generated whenever I create the source packages?  I would definitely love some help with that, I have little experience with RPMs (I used Mandrake 8, a while back).  And I wouldn't know where to start on setting up a yum repository.
  As far as the debian packages go, I'd like to get gfceu and fceu-server into universe and debian.  Until then, maybe another repository would be a good home.
  Thanks for your compliments and enthusiasm!  :) 

God bless,
Lukas

---

### Post by punkrockguy318 on 2006-06-25
The website is now located at [http://gfceu.thepiratecove.org](http://gfceu.thepiratecove.org)
I'll be away this week, so it will be a while before the code gets updated.

God bless,
Lukas

---

### Post by MetalMusicAddict on 2006-06-25
Just a heads up, after going from .2.3 to .2.5 I could no longer launch a ROM. Ill run it from a terminal to see if it gives me anything. Ill post back.

---

### Post by punkrockguy318 on 2006-06-25
[QUOTE=MetalMusicAddict]Just a heads up, after going from .2.3 to .2.5 I could no longer launch a ROM. Ill run it from a terminal to see if it gives me anything. Ill post back.[/QUOTE]
Try redownloading and reinstalling.  There was a bad tarbell on the server for a while.  If problems keep happening, see what output you get on the terminal and I'll check it out when I come home.

---

### Post by SlugO on 2006-06-25
[QUOTE=MetalMusicAddict]Just a heads up, after going from .2.3 to .2.5 I could no longer launch a ROM. Ill run it from a terminal to see if it gives me anything. Ill post back.[/QUOTE]
I have the same problem. I downloaded the .deb just a couple of minutes ago so there's definitely something wrong with the version that's on the site right now.

Here's the output from terminal after I try to start a ROM:```
janne@mylly:~$ gfceu
Gfceu message:  Using: /usr/games/fceu
Traceback (most recent call last):
  File "/usr/bin/gfceu", line 290, in launchbutton_clicked
    if options.networkrom:
AttributeError: game_options instance has no attribute 'networkrom'
```
Network play isn't checked.

---

### Post by stevejesus on 2006-06-25
Yeah, so I had planned on packaging gfceu on Friday night for SuSE and Fedora but...  then I started drinking.  I have been drinking ever since.  I'm still kind of drunk, haha.
Anyhow, since it's just a simple Python app, you could probably just use Alien to convert the deb to rpm and it will probably work just fine.  But an RPM built on the system it's supposed to run on is definitely healthier for the machine.  Its nice when the package manager likes the package you install :)

---

### Post by stevejesus on 2006-06-25
Yeah, anyhow...  I have downloaded the ISO's for openSuSEand fedora and I will be setting up a machine for them soon.  Then I will start packaging

---

### Post by MetalMusicAddict on 2006-06-25
Heres a rough inking. Needs a little clean-up but its an idea. I have a SVG of it Im gonna color if you like it. I would like to throw the Gnome foot in somewhere.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=11763&d=1151284760[/IMG]

---

### Post by GuitarHero on 2006-06-26
Hey man I could design a nice looking site for you.  (no offense to your current design, its just a bit plain).  You can still host it where it is.  I just like your project and want to help out, but my coding knowledge only extends to the web.  Just drop me a PM if you're interested.

---

### Post by braveerudite on 2006-06-26
[QUOTE=MetalMusicAddict]Heres a rough inking. Needs a little clean-up but its an idea. I have a SVG of it Im gonna color if you like it. I would like to throw the Gnome foot in somewhere.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=11763&d=1151284760[/IMG][/QUOTE]


Dude that desing Rocks.

Is "gfceu" going to be in the regular repos in the future?

I'm still very noob to Linux so I'll try to install it.  If there is a apt-get command I can use to get this and install it plz let me know.  (I always go for easy way for these things)

Great work and thx for your time in this project.  I could never get FCE to work on ubuntu.

---

### Post by GuitarHero on 2006-06-26
I think a penguin holding a nes controller like that one^ would be sweet. then you could call it lintendo

---

### Post by braveerudite on 2006-06-26
[QUOTE=GuitarHero]I think a penguin holding a nes controller like that one^ would be sweet. then you could call it lintendo[/QUOTE]


or LiNEx


BTW I got it working thx to GDebi!!! 


Thank you so much for this NES Emulator I am so greatful!!! Woot WOot!!!

---

### Post by GuitarHero on 2006-06-26
whats a good site for roms?

---

### Post by braveerudite on 2006-06-26
[QUOTE=GuitarHero]whats a good site for roms?[/QUOTE]

[http://www.torrentspy.com](http://www.torrentspy.com)

Just type nes in the search bar and you should see a torrent with every single NES game ever created and you can download them all on a single click.


Ejoy!!!

---

### Post by braveerudite on 2006-06-27
When I click on input devices to configure my XBox 360 USB Controller all I get is a small pop up that does not close down no matter what I do.  Has anyone been able to configure gfceu to work with Xbox 360 controllers?

---

### Post by GuitarHero on 2006-06-27
anyone else having problems getting sound to work with the newest version?

---

### Post by GuitarHero on 2006-06-27
[http://www.retrousb.com/nintendo.html](http://www.retrousb.com/nintendo.html)
anyone know if that would work with GFCEU?

---

### Post by MetalMusicAddict on 2006-06-27
MAN! Thats killer! I wonder if they would work with Linux in general? I would TOTALLY buy one if it would work with FCEU.

Hey punkrock. Ill totally buy one of these if you add support via a GUI config. :) Not kidding.
[IMG]http://www.retrousb.com/images/retropad1_med.jpg[/IMG]

---

### Post by DoktorSeven on 2006-06-27
Sounds like a simple USB HID controller, which should work just fine.

I want one of those too :)

---

### Post by GuitarHero on 2006-06-27
Im getting one

---

### Post by braveerudite on 2006-06-28
I can't get my Xbox 360 Controller to work with this emulator.  When I press the input config option all I get is a line that is impossible to close.  Anyone else try with Xbox 360 controller.

FYI Xbox 360 controllers are USB and work perfecly on Windows XP just like any other cheap Logitec controller.  So I think Xbox 360 controller should work as well.

Please post the Model and brand of controller you  are using with this emulator and please let me know if the input device option to configure controllers work for you guys.

---

### Post by nbpetts on 2006-06-28
i am having problems getting gfceu to recognixe the directional buttons on my gravis gamepad pro (usb).  The a, b, x, y buttons work fine, its jsut the directionals.  jscalibrator recognizes them, just not fceu, it just ignores them durring the button set up thing.  any suggestions?

---

### Post by nbpetts on 2006-06-30
i fixed it for those of us who experience the same problem.  just needed the program joystick, and then a calibration.

```
sudo apt-get install joystick
```

```
jscal
```

then map the gamepad buttons in gfceu/fceu

---

### Post by SlugO on 2006-06-30
Where has punkrockguy disappeared?
Gfceu is still broken, it won't start the roms :(

---

### Post by braveerudite on 2006-06-30
[QUOTE=nbpetts]i fixed it for those of us who experience the same problem.  just needed the program joystick, and then a calibration.

```
sudo apt-get install joystick
```

```
jscal
```

then map the gamepad buttons in gfceu/fceu[/QUOTE]


Thx for this, but this is still little tricky to get working for a noob like me.](*,) 

Is PunkRockGuys STill alive.?

---

### Post by nbpetts on 2006-06-30
till gfceu gets working again, the code for the fceu command line is

to play a game

```
fceu nameofrom.nes
```

to play a game with a controler

```
fceu -inputcfg gamepad1 nameofrom.nes
```

hope that helps

---

### Post by punkrockguy318 on 2006-06-30
[QUOTE=braveerudite]Thx for this, but this is still little tricky to get working for a noob like me.](*,) 

Is PunkRockGuys STill alive.?[/QUOTE]

I have returned!  I took a week of vacation and went down to the beach, had a great time!  I'll check out the posted error messages and get a fix as soon as possible.  Expect a fixed version today (friday) or tomorrow (saturday).

For the impatient, give 0.2.3 a try.

---

### Post by punkrockguy318 on 2006-06-30
Hello everyone, I have returned from vacation!  There's a couple topics that are being discussed in this thread that I would like to address.
  Some people have been having problems opening ROMs since 0.2.5.  I have released a new version, 0.2.6, that can be found on the website.  I was unable to reproduce the bug on my machine, but I believe I found what the problem was and it has been fixed.  Upgrade to the latest version, and give  me your feedback, please.

  MetalMusicAddict:  Your sketch looks AWESOME!  I love it!  If you decide to add the GNOME foot, keep it subtle.  The fact that gfceu fits in best with the GNOME desktop shouldn't be a major point that the icon is trying to convey.  Speaking of that, some other project titles have been suggested, which I seem to like.  I may change the title from gfceu.  Gfceu is awkward to type, and impossible to say.  How would you say that?  "Gee, faa key ooh"?  "Gee, fahk you"?  I'm not quite sure, and I don't think anyone is.

  braveerudite:  The current input configuration system is unintutive.  You must read the titlebar of that small, uncloseable window, and press a key/button you would like to use for it.  Until I can fix that in upstream fceu, I may add a dialog box describing this ugly process. 

  About the USB NES controller:  It seems to be a USB HID device, it should work just like any other gamepad.  MetalMusicAddict, the deal is on :D I've already started working on it, but it's going to be a bit of a project.

  SteveJesus:  Once you sober up a bit, try testing some 'aliened' rpm packages on OpenSuSE, and let me know how they work.

  GuitarHero:  My website is quite plain. It's my first endevour with css, my other projects were with tables (gross).  I'd like to keep the website simple and not too busy, but I'm SURE there is a better way to do it than my site.  Drop me a line if you would like to help me out :D  Also, I would like set up a forum on the website.  There are SO many topics going on inside this thread it's difficult to keep up with.  Could you set up something like that?  I wouldn't have the first idea.

---

### Post by MetalMusicAddict on 2006-06-30
> **punkrockguy318]MetalMusicAddict:  Your sketch looks AWESOME!  I love it!  If you decide to add the GNOME foot, keep it subtle.  The fact that gfceu fits in best with the GNOME desktop shouldn't be a major point that the icon is trying to convey.[/QUOTE] 
Thanx man. Ill clean it up and do some color work this weekend. I have 4 days off work.  said:**
> About the USB NES controller:  It seems to be a USB HID device, it should work just like any other gamepad.  MetalMusicAddict, the deal is on :D I've already started working on it, but it's going to be a bit of a project.
PM me with some info. Address or phone would be good also.

---

### Post by braveerudite on 2006-06-30
[QUOTE=punkrockguy318]
  braveerudite:  The current input configuration system is unintutive.  You must read the titlebar of that small, uncloseable window, and press a key/button you would like to use for it.  Until I can fix that in upstream fceu, I may add a dialog box describing this ugly process. 
  [/QUOTE]

I am looking very forward to this project! I'm happy just to know that you'll take care of the controller configuration settings with time. \\:D/ 


Can MetalMusicAddict sketch have tux holding the controller or somewere in the emu-logo??? Please, Please ,please [-o<



And last:  If you plan to change the name, Would you please list a few in a poll for us to vote? (Just asking, but name it whatever you want I'll still plan to keep using it, LOL ) :)

Great Job =D>

---

### Post by dipswitch on 2006-06-30
This is working great time to get some more roms. Thanks punkrockguy!

What names have been suggested so far? Howabout liNES

---

### Post by verbalshadow on 2006-07-01
I made a generic NES emu icon just a quick bang out of a classic NES controller not as cool as what MetalMusicAddict has planned but its simple and thats what I like. See the attached SVG

---

### Post by stevejesus on 2006-07-02
ok, im back.  Im a little bit more sober too!
I set up a machine the other day, was going to dual-boot FC5 and OpenSuSE.
I dont use FC5 but I used to moons ago.  OpenSuSe is rediculous.  I'll test alien'ed packages on it but thats all I will do.  That OS seems to be a complete trainwreck as par as managing and building packages go.  In fedora I will test alien'ed packages and probably build some fresh packages that are just for FC5.  
Stay tuned for an update.
Im trying to work this into my schedule as best I can.
I've got a new album coming out...  ye'ah!

---

### Post by MetalMusicAddict on 2006-07-02
Heres a color one.
[IMG]http://img46.imageshack.us/img46/7509/nes5qq.png[/IMG]
Good? I gotta figure out how to add a shadow in Inkscape. I also think Im gonna change it from saying "Nintendo" to "Gnome" because I think there might legal reasons. I also like the idea. Am I wrong about the legal reasons?

Ill send you the svg if you give me some contact info punkrock. I also need to send you the controller. ;)

---

### Post by GuitarHero on 2006-07-02
[QUOTE=punkrockguy318]
  GuitarHero:  My website is quite plain. It's my first endevour with css, my other projects were with tables (gross).  I'd like to keep the website simple and not too busy, but I'm SURE there is a better way to do it than my site.  Drop me a line if you would like to help me out :D  Also, I would like set up a forum on the website.  There are SO many topics going on inside this thread it's difficult to keep up with.  Could you set up something like that?  I wouldn't have the first idea.[/QUOTE]
Yeah sure I'll make you a simple site. How about something 8bit themed?  That way it would have to be simple, yet still have style.  Forums are also easy.  Just one thing, I know someone else in this topic provided you hosting(i forget who) but if you want me to use that host ill have to have the login info at some point.  I can make the site and upload it first to my host for you to see though.  Ill work on it later today.  Ive been lookin for a web design project.

---

### Post by braveerudite on 2006-07-02
[QUOTE=MetalMusicAddict]Heres a color one.
[IMG]http://img46.imageshack.us/img46/7509/nes5qq.png[/IMG]
Good? I gotta figure out how to add a shadow in Inkscape. I also think Im gonna change it from saying "Nintendo" to "Gnome" because I think there might legal reasons. I also like the idea. Am I wrong about the legal reasons?

Ill send you the svg if you give me some contact info punkrock. I also need to send you the controller. ;)[/QUOTE]


Oh man that looks so freaking cool... I kept a copy and spray it all over the place when I play Counter-Strike.

Great Job Metal Music Addict.... you are making this project presentation look cool.  =D>

PS: You should make a wallpaper using your desing and combine it with the Ubuntu logo and the name of this project then summit it to [http://www.gnome-look.org/](http://www.gnome-look.org/)  that way this project can start getting promotion. With black, grey or brown backgrounds 

1280X1024 and 1024X768

I'm just suggesting :)

---

### Post by punkrockguy318 on 2006-07-02
Again, as usual sorry for the inconvience of so many topics in one thread, forums are on the way, I hope!

Steve:  Keep me posted on the RPMs.  I tried the new OpenSuSe, but I couldn't even get it to install.  I would like gfceu to be available to as many people as possible.  Also, new album?  What do you play?  And what type of music?  Got any samples?

VerbalShadow:  Nice clean icon!  Cool!

MetalMusicAddict:  I LOVE the icon! I'll mail you about details.

GuitarHero:  I like the 8bit idea.  Set up a sample on your webserver and give me a link when you make some progress.  Can't wait to see it!

Everyone:  There's a new version is on the way.  Not many new features, but a lot of bugfixes and code cleanup.  Nothing to get overly excited about, but if you want to check it out before the release look in the svn.

---

### Post by GuitarHero on 2006-07-02
[http://img421.imageshack.us/img421/206/zomglolbbq3gh.png](http://img421.imageshack.us/img421/206/zomglolbbq3gh.png)
My host is down so i can only upload a preview, let me know if you want it changed before i put content on it.

---

### Post by MetalMusicAddict on 2006-07-03
Does anyone here know a good bit about **joystick** and **jscalibrator**?

I see them mentioned as needed to get my Gravis working but like a couple of others here I cant get the axis controls to work. Should I install **xserver-xorg-input-joystick**? Do I need to add lines to my Xorg?

Im using a Gravis Eliminator Aftershock on Xubuntu.
[IMG]http://outcastcomputers.com/ProdImages/48031_L.jpg[/IMG]

---

### Post by nbpetts on 2006-07-03
when I was having problems getting my (much) older model gravis gamepad working this worked for me.

Install joystick

```
sudo apt-get update

sudo apt-get install joystick
```

then install jscalibrator


```
sudo apt-get jscalibrator
```

then run the calibration processes 

```
jscal -c /dev/input/js0 (this is my joystick location check yours)


jstest /dev/input/js0 (or wherever)
```

If I remember correctly, this should return 0 for no error.

run jscalibrator 

```
jscalibrator
```

and it should recognize the type of gamepad correctly and recognize all of your buttons, and axis

now, fceu should recognize the directional pads.

minor troubleshooting: try a different USB port, I don’t know why, but I was suggested in the literature that got my pad working, and it worked for me.

---

### Post by droazen on 2006-07-03
Hey guys, I've had one of those modded nes controllers from retrozone for about a year now, & can confirm that it works fine with (plain-vanilla) fceu. Though I remember it took me about 10 tries with fceu -inputcfg before it recognized everything correctly (as I recall, the secret was to only press a given button on the pad the FIRST time fceu prompts you for it, & press some random keyboard button during the remaining 3 prompts).

Haven't tried Gfceu yet, but it sounds like a fantastic idea! I've always thought it was a bit unfair that the windows version of fceu has a full GUI while the linux version is strictly console. The prospect of a text config file is also very appealing :)  Perhaps a long-term goal could be to port the windows fceu GUI to GTK? (haha though I guess that's a bit ambitious this early in the game..)

---

### Post by MetalMusicAddict on 2006-07-03
OK. **jscal -c /dev/input/js0** worked for me. I didnt understand the prompts though. It guides you through calibrating the axis sticks and pad though I have no idea what I did.

After I ran **jscalibration** I noticed when the GUI comes up it looks to have the controls reversed (counter-clockwise instead of clockwise) or turned 90 degrees.

This controller has 3 sticks on it and I dont know where its assigning them.

---

### Post by MetalMusicAddict on 2006-07-03
> **droazen]Hey guys, I've had one of those modded nes controllers from retrozone for about a year now, & can confirm that it works fine with (plain-vanilla) fceu. Though I remember it took me about 10 tries with fceu -inputcfg before it recognized everything correctly (as I recall, the secret was to only press a given button on the pad the FIRST time fceu prompts you for it, & press some random keyboard button during the remaining 3 prompts).[/QUOTE]
Nice to hear it. Im ordering 3 today.  said:**
> Haven't tried Gfceu yet, but it sounds like a fantastic idea! I've always thought it was a bit unfair that the windows version of fceu has a full GUI while the linux version is strictly console. The prospect of a text config file is also very appealing :)  **Perhaps a long-term goal could be to port the windows fceu GUI to GTK?** (haha though I guess that's a bit ambitious this early in the game..)
Some of the things that have been discussed are going to be better than what the windows GUI provides. Stay tuned, we're still sorting things out. ;)

---

### Post by nbpetts on 2006-07-03
if you run jscalibrator and click the tab for logical mode, it will show you the names of each axis on your gamepad and look a lot like jscal as far as the numbers go, that might help you interperate the interface for jscal, thats what i did.

---

### Post by punkrockguy318 on 2006-07-03
Hey,
Today I did a LOT of work on the server code.  It's in the SVN if you'd like to see it.

However, it needs testing before I can release it into the wild.  I need someone that would be willing to test some network play with gfceu and the new server.  I'll tell you exactly what to do.  Give me an IM: lukaswayne9

---

### Post by vampiric_blade on 2006-07-03
[QUOTE=MetalMusicAddict]Nice to hear it. Im ordering 3 today. ;)

Some of the things that have been discussed are going to be better than what the windows GUI provides. Stay tuned, we're still sorting things out. ;)[/QUOTE]


I've been watching this thread for a while now, so now it's time ti chime in :)

I have one of these pads from retrozone, and it works just fine and dandy in dapper.  with fceu.  No fiddling around was necessary.  I plugged it in and was done.

---

### Post by zooter on 2006-07-04
Hello all!  I found a great  program for using a joystick on linux.  It should get rid of the need to include joystick stuff in idvidual programs because it emulates the mouse and keyboard with a joystick.  It's called **qjoypad** and it's not available as a package for ubuntu yet and I'm hoping to promote this program because I think it should be a part of every distro.  Here is the qjoypad website:  [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)

I've searched the internet for a program on linux that emulates the keyboard and mouse on linux and there aren't many at all and the ones that exist aren't developed enough.  

Anyways, with the exception of a few small bugs, it runs just fine on mandriva.  I was able to configure it to play in fceu and everything worked except the autofire.  The autofire actually works when I test it with a text editor by programming one of the joystick buttons to be a letter, but for some reason fceu doesn't recognize the autofire.  It may be too fast for fceu.  Also, if I change directions too fast with qjoypad, it doesn't change directions at all.  I tried installing the deb package for it on ubuntu but it conflicted with stuff I already have installed. These are the small bugs I've found in the program so far.  Other than that it works great.

Another use I get out of this program is that I use it to watch streaming video off the internet through my tv.  I have a usb extension so that I can use my gamepad like a tv remote control. 

I have emailed the developer of the program and he told me that he's too busy to work on it anymore.  I am posting this message in the hope that others can pick up on this project because I think a program like this is very useful.  It should be available already for every distro IMHO, but for some reason it's not.

I hope you all find this program and the info I gave useful.   This should make using gamepads and joysticks on linux a little easier.

---

### Post by MetalMusicAddict on 2006-07-04
Thanx for the heads up zooter. The app does sound nice. Too bad it isnt worked on anymore.

---

### Post by KalasMannen on 2006-07-09
Oh man! This is so great! I just saw that some guys put the sourceforge site back for fceu, and now i find this great gui app! This is like having christmas two days in a row!

This is some great stuff, i hope you'll continue work on it, and add some options for display and aspectratio and such (As i see that you've already mentioned above).

Keep it up!;)

---

### Post by MetalMusicAddict on 2006-07-09
You'll see. Cool things are planned. ;)

---

### Post by KalasMannen on 2006-07-10
Im sure there is :p

I'll follow this project closely in the future.. :)

---

### Post by Metacarpal on 2006-07-11
Just stumbled on this while looking to get my Gravis gamepad working for ZSNES.

I'm DLing the .debs for this now.  I'm mega-psyched.  Thanks so much to everyone working on this, especially you, Punkrock!

---

### Post by braveerudite on 2006-07-11
Hey guys!!! Just checking on the status of the project.  Is there a new release, site or anything else?  Is the project still alive?   Later all.

---

### Post by Metacarpal on 2006-07-11
Hm.  Ran into a snag, hoping you can help.
When I try to run GFCEU, pretty much nothing happens.  Tried running in Terminal, and here's what I got:

> metacarpal@musecatcher:~$ gfceu
gfceu message:  Using: /usr/games/fceu
Traceback (most recent call last):
  File "/usr/bin/gfceu", line 572, in ?
    give_widgets()
  File "/usr/bin/gfceu", line 155, in give_widgets
    xml.get_widget('join_port').set_value(float(options.join_port))
ValueError: empty string for float()
metacarpal@musecatcher:~$

If I try running it with sudo from the Run Application tool in Panel, I get the following message:

> gfceu ERROR Code 4:
Could not find the fceu binary.
    Ensure that FCE Ultra is installed and in the $PATH.
    On Debian based systems (like Ubuntu), try the following command:
    sudo apt-get install fceu

I thought this might have been because I installed FCEU through Synaptic prior to installing GFCEU.  (I forgot I'm not in RPM-dependancy Hell anymore. ;) )  So I removed both (through Synaptic) and re-installed the GFCEU .deb package, which kindly re-installed FCEU for me.  But still no joy. ](*,) 

Any thoughts?

---

### Post by punkrockguy318 on 2006-07-11
> **Metacarpal said:**
> Hm.  Ran into a snag, hoping you can help.
When I try to run GFCEU, pretty much nothing happens.  Tried running in Terminal, and here's what I got:



If I try running it with sudo from the Run Application tool in Panel, I get the following message:



I thought this might have been because I installed FCEU through Synaptic prior to installing GFCEU.  (I forgot I'm not in RPM-dependancy Hell anymore. ;) )  So I removed both (through Synaptic) and re-installed the GFCEU .deb package, which kindly re-installed FCEU for me.  But still no joy. ](*,) 

Any thoughts?

Yes, sorry about that!  It's a known bug.  I've just uploaded a new version that will fix this bug.  Download version 0.3.2 from the website: [http://gfceu.thepiratecove.org/](http://gfceu.thepiratecove.org/)

All release information will be announced at [http://gfceu.thepiratecove.org/](http://gfceu.thepiratecove.org/)

Enjoy!  Please respond with feedback!

---

### Post by Metacarpal on 2006-07-12
Wow - thanks for the fast response!

Works great now.  Finally, I'll get to see if this new copy of Final Fantasy 2 I got hold of is translated properly...  Been wanting to play this game for years.  :)

---

### Post by MetalMusicAddict on 2006-07-12
> **braveerudite said:**
> Hey guys!!! Just checking on the status of the project.  Is there a new release, site or anything else?  Is the project still alive?   Later all.

Yep were still here. Punkrock already answered about the release. My icon is now added. :) The new site is comming along thanx to GuitarHero. Its a 8-bit cartoony style. Really fun. ;) This project is alive a kicking. Just at this early stage we're trying to sort stuff out.

We still are looking for people to:
[LIST]
[*]Packagers for other distros
[*]Info on repos
[*]Someone to make a Win installer
[/LIST]
Any help at all is welcome. :)

---

### Post by fridaythe14th on 2006-07-12
This cures one of my Linx headaches. I've used a lot of time finding a NES emulator with GUI until I gave up. 6 months later I found this. Thank you!

I couldn't get toggling from/to fullscreen to work with either F4 or Alt-Tab (Alt-Tab is probably not the best combination of keys to use). It's not important to me though.

---

### Post by punkrockguy318 on 2006-07-16
> **fridaythe14th said:**
> This cures one of my Linx headaches. I've used a lot of time finding a NES emulator with GUI until I gave up. 6 months later I found this. Thank you!

I couldn't get toggling from/to fullscreen to work with either F4 or Alt-Tab (Alt-Tab is probably not the best combination of keys to use). It's not important to me though.

Check out version 0.4.0, the key sequence is alt-enter.  Enjoy!

---

### Post by fatsheldon on 2006-07-20
just thought i'd let you know that i'm using your latest Ubuntu package.  works great as far as i can tell.  no issues to report.

i do have a question.  does anyone think that fceu will have any problems letting me use an old NES controller hacked to USB (similar to [THIS]("http://www.joystiq.com/2004/09/07/how-to-make-a-nintendo-controller-into-a-pc-joystick/"))?

i'm quite interested in knowing and will probably go ahead hacking one up even if no one responds, but a little verification would be great...

fatsheldon

---

### Post by punkrockguy318 on 2006-07-20
> **fatsheldon said:**
> just thought i'd let you know that i'm using your latest Ubuntu package.  works great as far as i can tell.  no issues to report.

i do have a question.  does anyone think that fceu will have any problems letting me use an old NES controller hacked to USB (similar to [THIS]("http://www.joystiq.com/2004/09/07/how-to-make-a-nintendo-controller-into-a-pc-joystick/"))?

i'm quite interested in knowing and will probably go ahead hacking one up even if no one responds, but a little verification would be great...

fatsheldon

I can't confirm first hand, but that device should just be a standard HID.  FCEU/SDL should have no problem handleing that.

---

### Post by punkrockguy318 on 2006-07-21
For those of you that don't follow my nice news page:

0.5.0 has been released.

And for the lazy:
[http://gfceu.thepiratecove.org](http://gfceu.thepiratecove.org)

Why upgrade?  Because it's a higher version number of course!

---

### Post by CronoDekar on 2006-07-21
```
7zr is a stand-alone executable. 7zr handles less archive formats  than  7z, but does not need any others. 7zr is a "light-version" of 7za that only handles 7z archives.
```

Looks like an artifact crept in to the man page ;)

---

### Post by punkrockguy318 on 2006-07-21
> **CronoDekar said:**
> ```
7zr is a stand-alone executable. 7zr handles less archive formats  than  7z, but does not need any others. 7zr is a "light-version" of 7za that only handles 7z archives.
```

Looks like an artifact crept in to the man page ;)

Oops, that's fixed in svn.  I used the 7z man page as a template, I guess I skipped over that :)
Thanks! I would have never noticed.

---

### Post by jamespi on 2006-07-22
hi,

i reckon an appropriate and snappy project name would be GNES. liNES (an earlier suggestion in this thread) implies it is only designed for linux, but in truth it is designed for GTK. Also GNES rolls off the tongue easier, and I think most GNOME savvy people would understand what the project is just from the name.

---

### Post by jamespi on 2006-07-22
i just had a similar thought - earlier on the guy who designed that rather nifty logo said he wanted to change it from saying NINTENDO on the controller to avoid trademark issues; how about changing it to say GNINTENDO (although i dont think this helps on the trademark front that much ;-)

---

### Post by punkrockguy318 on 2006-07-22
> **jamespi said:**
> i just had a similar thought - earlier on the guy who designed that rather nifty logo said he wanted to change it from saying NINTENDO on the controller to avoid trademark issues; how about changing it to say GNINTENDO (although i dont think this helps on the trademark front that much ;-)

About the name change, it might be changed to FCE Ultra.  I've been working with the upstream FCE Ultra team, and it might become  a part of the fceu tarbell.

---

### Post by bruenig on 2006-07-22
Is there anyway to incorporate a save state like some other emulators have? That would put this over the top. 

Perhaps it exists and I dont know about it. If that is the case, please tell me how.

---

### Post by Stabicron on 2006-07-22
> **bruenig said:**
> Is there anyway to incorporate a save state like some other emulators have? That would put this over the top. 

Perhaps it exists and I dont know about it. If that is the case, please tell me how.

Yeah this is also something I would love to see, must say I was suprised when I saw that someone finally made a decent working GUI for one of my favortie emulators, very nice job. However all its missing for me atm is the save state features, also having an option in the gui you can enable that will auto-pause the emu when the window looses focus would be nice as well *I usually have GAIM running at the same time and you can imagine what happens when I am trying to say jump over a pit and an IM pops up*. In anycase keep up the good work.

---

### Post by fridaythe14th on 2006-07-22
To save in FCEU you press and hold a number key and then F5. To load you do the same except press F7 instead of F5. The number key you choose is the number you save to and load from. The files are stored in ~/.fceultra/fcs

Thanks again punkrockguy. Toggling between fullscreen and not now works great :)

---

### Post by thegnark on 2006-07-23
punkrockguy318:

can you make a small change in the rom selection dialog to include .zip files? fceu supports opening a zipped rom file. in fact, if i change the view to "all files" and open one of my zipped roms, it already works perfect


thanks!

---

### Post by lleberg on 2006-07-29
I have a small question, how do i get fullscreen to actually befullscreen, without black boarders.. :)

---

### Post by MetalMusicAddict on 2006-07-29
> **lleberg said:**
> I have a small question, how do i get fullscreen to actually befullscreen, without black boarders.. :)

You need to make sure you have the res you want to fullscreen to in your Xorg. ie: if you wanna do 640x480 fullscreen you need to make sure you can change you desktop res to that.

---

### Post by lleberg on 2006-07-30
Well, i have.
For now i reduce my res with ctrl alt - when i'm about to play, but this isn't a real sollution is it?
What options in fceu (or gfceu) should i use?

My native is 1280x1024

---

### Post by MetalMusicAddict on 2006-08-14
For all of you who didnt know gFCEU has a new [SITE]("http://gfceu.thepiratecove.org/index.php"). It also had its own forums now. Go there and register. :)

---

### Post by twotonz on 2006-08-23
PUNK RULES!
Sorry, just had to add my 2 cents here. To all the guys that have made this possibile, a big thanks. When I stumbled across this thread last week, I smiled and thought, aha, another go at getting some sort of emulation working that is half way stabil. Anyway, I continued to follow the thread, and then a couple of days ago, figured I would investigate more & installed the gui.
Very impressive, I know you have heard it all before, but you lot here have just brought gaming under ubuntu a big step forward, well done!
Sooo, where did I stash my old nintendo games?

Love & Peace
anthony

---

### Post by punkrockguy318 on 2006-08-23
> **twotonz said:**
> PUNK RULES!
Sorry, just had to add my 2 cents here. To all the guys that have made this possibile, a big thanks. When I stumbled across this thread last week, I smiled and thought, aha, another go at getting some sort of emulation working that is half way stabil. Anyway, I continued to follow the thread, and then a couple of days ago, figured I would investigate more & installed the gui.
Very impressive, I know you have heard it all before, but you lot here have just brought gaming under ubuntu a big step forward, well done!
Sooo, where did I stash my old nintendo games?

Love & Peace
anthony

Thanks a lot bro! :D

---

### Post by cyrano_says on 2006-08-25
thanks for this one.. was looking for a way to play my old nintendo games..

thanks again...

---

### Post by RavenOfOdin on 2006-08-25
FCEUltra runs in Debian Etch but I can't seem to alter the default key mappings.

Thus, B and A (Ctrl and Alt) don't work.

---

### Post by Dr. Feelgood on 2006-09-03
Just a small request for the next release.  I may be the only one but sometimes I need to type "killall esd" in terminal before starting fceu to get the sound to work.  I tried aoss before but its laggy.  Can you incorporate this into gfceu?  Maybe allow for a line to be entered in terminal ahead of starting fceu kind like the options line you already have?  Or maybe just a checkable "killall esd" option?

---

### Post by punkrockguy318 on 2006-09-03
> **Dr. Feelgood said:**
> Just a small request for the next release.  I may be the only one but sometimes I need to type "killall esd" in terminal before starting fceu to get the sound to work.  I tried aoss before but its laggy.  Can you incorporate this into gfceu?  Maybe allow for a line to be entered in terminal ahead of starting fceu kind like the options line you already have?  Or maybe just a checkable "killall esd" option?

esd-killing-gfceu.sh
```

#!/bin/sh
# gfceu startup script that kills esd
# 9/3/06

killall esd
gfceu
nohup esd &

```

There you go, just run gfceu from this script, and watch you esd problems dissappear.

---

### Post by Dr. Feelgood on 2006-09-04
What's the "nohup esd &" line for?

---

### Post by DoktorSeven on 2006-09-04
Starts up ESD again after gfceu's done.

---

### Post by Dr. Feelgood on 2006-09-04
ahh... in that case I don't think it's necessary.  I haven't run into any bugs just typing killall esd into terminal and not worrying about restarting it.

---

### Post by etotehpii on 2006-09-17
Hey, great job on this emulator.  It runs just as nicly as NEStron does in Windows.

---

### Post by punkrockguy318 on 2006-09-17
> **etotehpii said:**
> Hey, great job on this emulator.  It runs just as nicly as NEStron does in Windows.

I can't take credit for a whole lot of the emulator code, only the Graphical User Interface.  But thank you :D 

Oh, new version on the way.  You can check it out in svn.

---

### Post by skralljt on 2006-09-20
This is great, one of the things that is going to help me abandon win32!  Now that I have the full breadth of the early 90's games to choose from linux is no longer such a bad choice.  Thanks for selflessly working on this and making the world a better place for washingtonians living with the dreary weather.

---

### Post by MetalMusicAddict on 2006-09-20
> **skralljt said:**
> Thanks for selflessly working on this and making the world a better place for **washingtonians** living with the dreary weather.
GO NATS!

Well maybe you should say goodbye to that dumb old 495 and join all the other Washingtonians like myself in N.C. :) Theres lots of us down here and better weather. ;)

---

### Post by Wheelman on 2006-09-29
Hmm this is weird... I installed your .deb file and the game played fine.  Then, i restarted the computer and the roms would not load.  I got the message "Can not load binary file"  Then i removed it and reinstalled it and EVERTHING on my computer including FCEU is running very slow..it won't even emulate at full speed now :(  Any ideas what went wrong and what I can do to correct it?

Thanks

---

### Post by punkrockguy318 on 2006-10-14
0.5.2 has been released!   Check out [http://gfceu.thepiratecove.org](http://gfceu.thepiratecove.org) and download away.

---

### Post by IronMan7491 on 2006-10-14
I'm sure you're aware of this but your links are down. Nice work btw.

---

### Post by punkrockguy318 on 2006-10-14
> **punkrockguy318 said:**
> 0.5.2 has been released!   Check out [http://gfceu.thepiratecove.org](http://gfceu.thepiratecove.org) and download away.

EDIT: Fixed link.

---

### Post by J-Rod on 2006-12-06
Pirate cove is down, is there a mirror anywhere?

---

### Post by fng on 2006-12-07
0.5.0 version can be found here : [https://launchpad.net/distros/ubuntu/+source/gfceu/0.5.0-0ubuntu1]("https://launchpad.net/distros/ubuntu/+source/gfceu/0.5.0-0ubuntu1")

---

### Post by guillaumeh on 2006-12-07
The website [http://gfceu.thepiratecove.org/](http://gfceu.thepiratecove.org/) seems down.

---

### Post by punkrockguy318 on 2006-12-07
Argh!  I'm buying some server space soon, so the site will be relocated in the near future.  Sorry for the delay!

(Or if anyone else is willing to donate some space, that would be great.)

---

### Post by punkrockguy318 on 2006-12-09
I've got plenty of server space and bandwidth.  [http://s189529521.onlinehome.us/](http://s189529521.onlinehome.us/)

The site isn't completely up yet, but you can still download gfceu.

Enjoy!

---

### Post by User_Program on 2006-12-09
Thanks Lukas! 
BTW you have done a great job with gfceu ultra! keep it up :)

---

### Post by punkrockguy318 on 2007-01-01
Version 0.6.0

This version fixes a couple (severe) bugs, and supports ALSA (sort of).

Enjoy!

0.5.2 is severely glitched, please upgrade to 0.6.0 ASAP!

---

### Post by rolando2424 on 2007-01-02
Works like a charm :D

---

### Post by punkrockguy318 on 2007-01-02
> **rolando2424 said:**
> Works like a charm :D

So glad to hear that!

---

### Post by punkrockguy318 on 2007-01-05
Alright, GFCEU is finally up and has a new home:  [http://dietschnitzel.com](http://dietschnitzel.com)

Also, the new gfceu is in feisty, so feel free to apt-get install gfceu if you're running feisty.

---

### Post by braveerudite on 2007-01-15
Hello PunkRockGuy318

I'm very happy to know that you still keeping up to date this project.  This is my first time visiting this thread in months.  Few days ago I went to visit your old site and it was down.  I was very worry at first but after reading the latest post I can see that the project is still pretty much alive.  Thank you so much for taking your time to port this great emulator to Ubuntu.  Keep up the good work :)

---

### Post by BrendanM on 2007-01-20
PunkRockGuy,
Thanks a ton for making this awesome GUI. Stuff like this is the best thing about open source software. Somebody can notice a problem/opportunity, and write their own software to solve it. Can I make a feature request for future versions? How about a way to pass Game Genie cheats to the emulator? I'm pretty sure FCEU already supports them, and you could probably enter them in the advanced tab, but it'd be nice to have a "cheats" tab where you could put them in easily. Thanks again.

---

### Post by adamJ5 on 2007-01-22
I Love You!!! Thanks So Much! :d

---

### Post by punkrockguy318 on 2007-01-22
> **BrendanM said:**
> PunkRockGuy,
Thanks a ton for making this awesome GUI. Stuff like this is the best thing about open source software. Somebody can notice a problem/opportunity, and write their own software to solve it. Can I make a feature request for future versions? How about a way to pass Game Genie cheats to the emulator? I'm pretty sure FCEU already supports them, and you could probably enter them in the advanced tab, but it'd be nice to have a "cheats" tab where you could put them in easily. Thanks again.

Sounds like a good feature; i'll look into it for the next version

---

### Post by NorthernPaladin on 2007-01-24
This rocks!! I simply love nes, when I grew up I had one, now I play the same games with my computer! Thank you very very very much!!!:D
Could you put a configuration tab where you could assign keys to every function, for example saving/loading, because I play with a gamepad and I`d like to put those into the pad so I would not have to reach my keyboard to do them, and a speed up button would be great

---

### Post by chris_wong on 2007-02-05
when i try to configure a gamepad/controls, i just get a little rectangle wth random colours. please help me.

---

### Post by punkrockguy318 on 2007-02-05
> **chris_wong said:**
> when i try to configure a gamepad/controls, i just get a little rectangle wth random colours. please help me.

The box should say in the titlebar "Gamepad (A)" or something.  Just preess the key you would like to associate with that button.

I know this is suboptimal, but this is out of my control.  It's a FCEU feature that I cannot change without changing FCEU.  This has been changed in the new version of FCEU, but it not released yet and will not be released for a while (if ever).

---

### Post by survient on 2007-03-05
I like the idea of gfceu, but, for some odd reason, it's slow for me. I'm running x64 ubuntu, all my GTK apps and GNOME apps run fine, but this one, It'll load GFCEU, I'll put in the parameters, and it'll take a half hour for the FCEU box to show up. in that half hour, my cpu will be doing nothing. It'll load the window when I click something, close something, or open something, I don't get it.

---

### Post by punkrockguy318 on 2007-03-05
> **survient said:**
> I like the idea of gfceu, but, for some odd reason, it's slow for me. I'm running x64 ubuntu, all my GTK apps and GNOME apps run fine, but this one, It'll load GFCEU, I'll put in the parameters, and it'll take a half hour for the FCEU box to show up. in that half hour, my cpu will be doing nothing. It'll load the window when I click something, close something, or open something, I don't get it.

what version are you using?  be sure your using the latest version from [http://dietschnitzel.com](http://dietschnitzel.com)

---

### Post by survient on 2007-03-06
Heh, they need to update the synaptic. I was on version 0.3 something, now I'm up to date, it works great. thx

---

### Post by madcowbcs on 2007-03-18
Thanks for working on the NES scene for the kids from the 80's!
I've been having a heck of a time finding an emulator that lets me run a or use a USB GAMEPAD.

The program kills itself most of the time when I try to load it.  I haven't been able to get it to run properly yet.  I would love to be apart of the testing solution though.  I'm sure there is something I have overlooked that will help all the other NES fans out there.  I have a few friends that would like to help beta GFCEU too.  What settings should I inspect for compatablity issues?

---

### Post by punkrockguy318 on 2007-03-27
> **madcowbcs said:**
> Thanks for working on the NES scene for the kids from the 80's!
I've been having a heck of a time finding an emulator that lets me run a or use a USB GAMEPAD.

The program kills itself most of the time when I try to load it.  I haven't been able to get it to run properly yet.  I would love to be apart of the testing solution though.  I'm sure there is something I have overlooked that will help all the other NES fans out there.  I have a few friends that would like to help beta GFCEU too.  What settings should I inspect for compatablity issues?

what version are you using?

---

### Post by braveerudite on 2007-04-01
I'm using the latest GNOME FCE Ultra 0.6.0 and the sound is out of sync.  What gives?

---

### Post by dhtseany on 2007-04-02
Ok this may sound like a really dumb question but how do I open it?

---

### Post by punkrockguy318 on 2007-04-02
Applications... Games... GFCEU NES emulator

if that's not there, run this command:

gfceu

---

### Post by dfreer on 2007-04-12
Is there any chance that you could incorporate a ROM directory view, like ZSNES perhaps? I'm talking about when the program starts, instead of seeing just the last ROM you played, it could have a list of all the ROM's in that current directory, and then you just select the one you want.
Alas, I would do this myself, yet I do not know the programming... *cry*

[EDIT] - BTW, great job with the frontend!! And I'm loving the icon too

---

### Post by m4443 on 2007-04-25
Help! I get this like window, when I'm trying to change input settings:

[IMG]http://img464.imageshack.us/img464/8483/pictdt5.png[/IMG]

So, how I change input settings?

And sorry for my very very bad english[SIZE="1"](because, I'm from Finland...)[/SIZE].  :)

---

### Post by dfreer on 2007-04-25
When that pops up, try typing the key that you want to assign to that button. For example, in the above pic it says "A". You would then type which key you wish to be "A". I'm pretty sure it will ask you for the same key twice, so make sure to hit the same button each time.

---

### Post by disturbedite on 2007-04-26
based on the title of this thread and skimming through it a bit i'd just like to add that nestopia (the best nes/fam emulator for windows) is being actively developed for linux.  (preview #5 is about to be released i believe).  i test it out with a few others (afaict) on the emuversal forum.

once it is released for linux imho as far as i'm concerned it will obsolete all other nes emulators for linux.

its already stable and works fine for me, give it a try if you want.  (for linux version you must download the full release source code and then grab the linux source and extract it over the full release's source and then compile).

---

### Post by punkrockguy318 on 2007-04-26
Does it support a GUI for linux?

---

### Post by braveerudite on 2007-04-26
> **disturbedite said:**
> based on the title of this thread and skimming through it a bit i'd just like to add that nestopia (the best nes/fam emulator for windows) is being actively developed for linux.  (preview #5 is about to be released i believe).  i test it out with a few others (afaict) on the emuversal forum.

once it is released for linux imho as far as i'm concerned it will obsolete all other nes emulators for linux.

its already stable and works fine for me, give it a try if you want.  (for linux version you must download the full release source code and then grab the linux source and extract it over the full release's source and then compile).

As a Nestopia user for windows I agree 100% with what said.  This Linux version you speak about is great news.  Would you please compile an Ubuntu 7.04 (Festy) version for us? :) That would ROCK!!!

---

### Post by disturbedite on 2007-04-26
@punkrockguy
yes it does!

@braveerudite
i can't create a deb package unfortunately cuz the source is such that you just have to extract the source then cd to the directory and just type make.  thats it.
i will post a linux tar.gz archive with the precompiled binary and what not.  give me a few minutes.

INSTRUCTIONS:
extract the archive contents to wherever you want (preferably somewhere like /usr/share/games/nestopia or /usr/local/games/nestopia) except nstcontrols & nstsettings, put those last two files i mentioned in your home directory.  (you'll have to create it, /home/USERNAME/.nestopia).  then run and set whatever settings you like.

awaiting your playing pleasure;  (click on wait in line & download)
[http://www.content-type.com/865286426/Nestopia+1.3.6.tar.gz.htm](http://www.content-type.com/865286426/Nestopia+1.3.6.tar.gz.htm)

---

### Post by braveerudite on 2007-04-26
Thank you for your reply, although I understood what you said I rather wait for a .deb compile version that way is easy to uninstall. Keep us posted with this Nestopia 4 Linux thing.

---

### Post by disturbedite on 2007-04-26
dude, all you have to do is extract the archive contents *anywhere* you want, put the the two files in your nestopia home directory and play away.  if you wanna uninstall it just delete the nestopia folders.

btw, nestopia for linux preview #5 is going to be released soon i believe.

---

### Post by dfreer on 2007-04-26
I can make a .deb for you guys, for i386 and possibly AMD64 if it is needed/wanted. However, I just tried nestopia, and I gotta say I don't see any reason why it is better than gfceu (if someone could tell me why they think it is better I'll listen)... it has a GUI, but I didn't see any way to map my USB controller or keyboard unless I edit the .nestopia/nstcontrols manually. Here's the nstcontrols file for anyone who wants to look at it:

```
;
; NEStopia Linux controls file
;
; First column cannot be changed or you'll break the emulator
; Second column is the key for the first column, or one of these special names:
; 
; _ENTER, _LCTRL, _RCTRL, _LALT, _RALT, _SPACE, _LSHIFT, _RSHIFT, _TAB
; _UP, _DOWN, _LEFT, _RIGHT, _KPENTER, _KP0, _KP1, _KP2, _KP3, _KP4, _KP5, _KP6,
; _KP7, _KP8, _KP9, _KPDOT, _KPSLASH, _KPSTAR, _KPMINUS, _KPPLUS (use __ to bind the actual _)
;
; Third column maps joypads:
; _JxAyPLUS = joystick #x axis #y positive direction
; _JxAyMINUS = joystick #x axis #y negative direction
; _JxBy = joystick #x button #y pressed
;
; Some keys are special:
; ESC always exits
; ALT-ENTER always toggles screen modes
;

; player 1
; default joypad values are for a PlayStation 2 controller via an EMS USB adaptor
;
P1UP	_UP	_J0A1MINUS
P1DN	_DOWN	_J0A1PLUS
P1LT	_LEFT	_J0A0MINUS
P1RT	_RIGHT	_J0A0PLUS
P1A	,	_J0B2
P1B	.	_J0B3
P1START	1	_J0B9
P1SELECT	2 _J0B8

; player 2
P2UP	_KP8	_J1A1MINUS
P2DN	_KP2	_J1A1PLUS
P2LT	_KP4	_J1A0MINUS
P2RT	_KP6	_J1A0PLUS
P2A	_KPSLASH	_J1B2
P2B	_KPSTAR	_J1B3
P2START	_KPENTER	_J1B9
P2SELECT	_KPPLUS	_J1B8

; end of file
```

I'd have to find a way to get the scancodes or whatever for each keypress on my USB controller :( I think fceu has a horrible interface, but with gcfeu it isn't that bad. Anyways, I'll get to work on a i386 .deb for ya guys (there will be two of them, since it seems that nestopia can be compiled specifcally to use single or dual core processors (actually, it can do quad as well now that I look at it).

EDIT: Oops I'm a idiot. I read the readme wrong. It can be COMPILED using a dual core processor, to improve compile times. doh lol. so there will be only one version.

---

### Post by braveerudite on 2007-04-26
Hey man, is very nice for you to take your time to this for us. My problem is this. If I have to open a file and manually config the USB controllers than is not worth my time. Is 2007 and manually config a USB controller is not attractive. But that is not your fault and besides you are compiling from an unfinish linux port and we don't know if they be adding a GUI for controller set up.

About the reason why we think is better well that depends, In my opinion is the best NES emulator for Windows but that can completely change in Linux.  We hope that an official release for Linux could be as good as the Windows.

I wonder if those working on the Linux port of NEStopia are the same developers from Windows version.

Thank you very much again for taking the time to put this together for us but if I have to open files an edit to get my Logitech controller to work then I won't bother to try it. But then again if I can do that with the GUI then I'm defenetly in.  Compile on brother!!!

---

### Post by dfreer on 2007-04-26
no problems :) I used fceu in windows, but that was about 2 some years ago when I was actually USING windows lol. I haven't heard of nestopia, but if the GUI in linux is anything like the windows version... ew. Basically, my feeling is EVERY emulator should be as simply and easy as ZSNES... but whatever. I wish I knew enough about programming to write my own frontends. :D
Does nestopia have better game support than fceu, is that why it is better? I don't think I've had any game issues with fceu, but I only have like 10-15 NES games.

---

### Post by disturbedite on 2007-04-27
no offense guys, and i'm not trying to sound smart, but from the sound of your responses you guys don't know the technical aspects of emulation, cuz if you did, you wouldn't have asked that question.

but to answer the question, nestopia has the best compatibility (ability to run the most games) and it only gets better with every release.

and its open source.

---

### Post by dfreer on 2007-04-27
hmmm. I admit I know nothing about programming. and open source is all well and good. but at the end of the day, the GUI's for both systems could use some improvement, and in my mind nestopia slightly more improvement. As for emulation compatibility, it sounds great. All of my games run pretty much perfectly on both systems, so on that issue they both win on that point. I wouldn't mind at all switching to nestopia, that is why I downloaded it. But the GUI as of right now is preventing me from even playing comfortably.

Should I use a open-source program that is hard to use, or should I use the one that isn't but is a *bit* eaiser to use? When nestopia becomes easy I'll be among the first to switch :D sounds like a great project

---

### Post by disturbedite on 2007-04-27
> **dfreer said:**
> hmmm. I admit I know nothing about programming. and open source is all well and good. but at the end of the day, the GUI's for both systems could use some improvement, and in my mind nestopia slightly more improvement. As for emulation compatibility, it sounds great. All of my games run pretty much perfectly on both systems, so on that issue they both win on that point. I wouldn't mind at all switching to nestopia, that is why I downloaded it. But the GUI as of right now is preventing me from even playing comfortably.

Should I use a open-source program that is hard to use, or should I use the one that isn't but is a *bit* eaiser to use? When nestopia becomes easy I'll be among the first to switch :D sounds like a great project

its all up to you, whatever you choose, more power to ya.  (thats the spirit of free software!)  you're right that nestopia's gui needs improvement, but keep in mind its a preview (alpha), it hasn't even been released for general public consumption yet.  (at least not on sourceforge).  its fine for me tho.  better than anyone other nes emulator for linux i've tried...

---

### Post by stafio on 2007-05-06
Out of the NES emulators for Linux that I've tried, Fakenes is the best. There's a .deb available here: [http://www.fbriere.net/debian/nes-emu/sid/]("http://www.fbriere.net/debian/nes-emu/sid/"). There are also several other NES emulator packages here, but as I said, I find Fakenes to be the best of the bunch.

---

### Post by pooslinger on 2007-05-06
> **stafio said:**
> Out of the NES emulators for Linux that I've tried, Fakenes is the best. There's a .deb available here: [http://www.fbriere.net/debian/nes-emu/sid/]("http://www.fbriere.net/debian/nes-emu/sid/"). There are also several other NES emulator packages here, but as I said, I find Fakenes to be the best of the bunch.

Fakenes runs great.  Thanks for the link.

---

### Post by en3rgy on 2007-06-09
Thank you everyone for this awesome thread. You've all been so helpful (well, most of you at least). 
;););););)

---

### Post by adam0509 on 2007-06-23
can't compile nestopia in here...

wich package do I need ?

```

sudo apt-get install build-essential libalsaplayer-dev libsdl1.2-dev libgtk2.0-dev

```

Got all of these...

---

### Post by MaindotC on 2007-11-15
Has anyone hosted an fceu game using fceu-server, and if so, can you tell me about what it should look like?

I run fceu-server and it shows the following in the window:
```
asymptote@asymptote-laptop:/usr/share$ fceu-server
Cannot load configuration file /etc/fceu-standard.conf.
Binding to port 4046... Ok
Listening on socket... Ok

```

When my friend joins this appears: ```

Client 0 connecting from 216.239.68.191 on Thu Nov 15 17:51:37 2007
Game 0 added
Client 0 assigned to game 0 as player 1 <Neuron>
```
And then he disconnects:```

Player <Neuron> disconnected from game 0 on Thu Nov 15 17:51:44 2007
Game 0 destroyed.
```

Let's compare this to Zsnes netplay.  When someone joins a game, you have like a pre-game screen with a chat window and you can select which game you want to play.  I'm not seeing this in fceu.  This is what it looks like when I join the game I'm hosting.  I use "localhost" for the address:```

Client 0 connecting from 127.0.0.1 on Thu Nov 15 17:54:27 2007
Game 0 added
Client 0 assigned to game 0 as player 1 <*Player 1>
Player <*Player 1> disconnected from game 0 on Thu Nov 15 17:54:29 2007
Game 0 destroyed.

```
And of course that's me disc'ing.  If we both join at the same time, fceu-server will assign me to game 0 and my friend to game 1.  I start the game but don't see him in with me.  He doesn't see anything on his screen signifying start of the game.

What should be the process for two players using netplay?  I apologize for not consulting the documentation but it's unavailable on the sourceforge site and even if it was, I doubt there's a section that says "how to" but instead talks about the capabilities of fceu-server.

---

### Post by punkrockguy318 on 2007-11-15
> **strAlan said:**
> Has anyone hosted an fceu game using fceu-server, and if so, can you tell me about what it should look like?

I run fceu-server and it shows the following in the window:
```
asymptote@asymptote-laptop:/usr/share$ fceu-server
Cannot load configuration file /etc/fceu-standard.conf.
Binding to port 4046... Ok
Listening on socket... Ok

```

When my friend joins this appears: ```

Client 0 connecting from 216.239.68.191 on Thu Nov 15 17:51:37 2007
Game 0 added
Client 0 assigned to game 0 as player 1 <Neuron>
```
And then he disconnects:```

Player <Neuron> disconnected from game 0 on Thu Nov 15 17:51:44 2007
Game 0 destroyed.
```

Let's compare this to Zsnes netplay.  When someone joins a game, you have like a pre-game screen with a chat window and you can select which game you want to play.  I'm not seeing this in fceu.  This is what it looks like when I join the game I'm hosting.  I use "localhost" for the address:```

Client 0 connecting from 127.0.0.1 on Thu Nov 15 17:54:27 2007
Game 0 added
Client 0 assigned to game 0 as player 1 <*Player 1>
Player <*Player 1> disconnected from game 0 on Thu Nov 15 17:54:29 2007
Game 0 destroyed.

```
And of course that's me disc'ing.  If we both join at the same time, fceu-server will assign me to game 0 and my friend to game 1.  I start the game but don't see him in with me.  He doesn't see anything on his screen signifying start of the game.

What should be the process for two players using netplay?  I apologize for not consulting the documentation but it's unavailable on the sourceforge site and even if it was, I doubt there's a section that says "how to" but instead talks about the capabilities of fceu-server.

That's how fceu netplay works.  It's very basic, and not much too it.  There isn't any real interface to it at all, unfortunately.  Not much work was ever really put into the fceu-server.  It was pretty much unusable until I coded some bits and peices to clean it up.  

Sadly, i doubt it's going to improve much.  Not much work is being done with fceu so not much will get done until a new developer decides to pick up on it.

I've said this before, but I deal with little of the fceu code itself.  I mostly just work on the GUI for fceu, which is a seperate program.


For netplay to work, you need to make sure your ports are forwardered correctly and that a firewall is blocking any connections.

The second player might need to use controls for the second player gamepad, but I'm not sure.  If you're having problems, give it a shot.

---

### Post by MaindotC on 2007-11-15
Thank you very much for taking the time to reply.  It feels good to know someone checks the threads from time to time.  However, this doesn't really address my issue.  I'm not contesting the quality of the code, I'm asking how to implement it.  I see my friending joining so I know at least the connectivity issue works, I just don't know how to get him into the game with me.

Does that clarify what I was asking?

---

### Post by Zeikcied on 2007-11-16
I haven't read this entire thread, so forgive me if this has been asked, but is it possible to use cheats with GFCE?

I know the Windows version of FCE Ultra has an extensive cheat function, but there doesn't seem to be an equivalent for Linux.  I would have thought someone would port that over.  Isn't the Windows version open-source?  Can there be a direct port of that interface to the Linux version?

---

### Post by Felson on 2007-11-16
@Zeikcied
GFCE is a GUI to FCE, so if FCE does it, you may need to ignore the GUI and launch it in command line to get your cheats to work. That said, I haven't used that emulator yet.

---

### Post by Zeikcied on 2007-11-16
> **Felson said:**
> @Zeikcied
GFCE is a GUI to FCE, so if FCE does it, you may need to ignore the GUI and launch it in command line to get your cheats to work. That said, I haven't used that emulator yet.
Apparently fceu has a cheat interface that you can use by pressing F2.  The problem is that the interface uses the console, and hides the game window.  So if you try it using gfceu, your game window will disappear, and you have to kill fceu to get the program back.  It might work if you start gfceu from the console, but I haven't tried that.

I still have the .cht files from the Windows version, but I don't know where I should put them to use them in fceu on Linux.

In fact, I've found this lack of cheat function to be an annoyance with gfceu and with vgaexpress (a VisualBoy Advance front-end).  I did find ZSNES in the repositories, and that has a cheat function (and is virtually identical to the Windows version).  Which makes me wonder why other emulator GUIs on Linux seem to ignore the cheat functions.  I'd rather have the GUI/front-end have the same feature set as the Windows equivalent.

---

### Post by MaindotC on 2007-11-17
So how about getting fceu-server working per my previous posts? :)

---

### Post by punkrockguy318 on 2007-11-17
> **strAlan said:**
> So how about getting fceu-server working per my previous posts? :)

Have you tried getting the connected users to use the player 2 controls?

---

### Post by MyKal on 2007-11-21
what about Snes9x???

that one is just aching for a descent gui

---

### Post by Felson on 2007-11-21
NES   = Nintendo Entertainment System
SNES = Super Nintendo Entertainment System

snes9x = snes 

:)

---

### Post by MaindotC on 2007-11-21
> **punkrockguy318 said:**
> Have you tried getting the connected users to use the player 2 controls?

Excellent idea, and thank you for your thoughts.  I actually wiped out all the kernels in my /boot folder by running some program, and I haven't had time or desire to reinstall.  I'll let you know when I test this and thank you again for your help!

---

### Post by punkrockguy318 on 2008-07-02
I remember there was a lot of complaining in this thread about issues with fullscreen, and it not scaling properly.

I just made a commit in the latest subversion of fceu and fceu now autoscales when fullscreen.  However, I would like some testing and feedback on this.  If there's anyone that wants to help out please test out the latest subversion of fceux and let me know how things work.

---

### Post by Keithel on 2008-07-02
If I recall, NESticle was my emulator of choice a long while back... My mind thinks I was using it on Linux, but maybe I'm thinking of fceu -- the interfaces are quite similar IIRC, and there seems to be no evidence on the web indicating there was a Linux port of NESticle....

Going from some NESticle research, I found that Nestopia may be a reasonable candidate for providing your front end to...

[http://www.vg-network.com/nestopia](http://www.vg-network.com/nestopia)
[http://nestopia.sourceforge.net/](http://nestopia.sourceforge.net/)
[http://rbelmont.mameworld.info/?page_id=200](http://rbelmont.mameworld.info/?page_id=200)

I haven't specifically checked out your work, but your goal is great! Having a nice user friendly interface for loading and playing NES games is great. :)

---

### Post by punkrockguy318 on 2008-07-02
> **Keithel said:**
> If I recall, NESticle was my emulator of choice a long while back... My mind thinks I was using it on Linux, but maybe I'm thinking of fceu -- the interfaces are quite similar IIRC, and there seems to be no evidence on the web indicating there was a Linux port of NESticle....

Going from some NESticle research, I found that Nestopia may be a reasonable candidate for providing your front end to...

[http://www.vg-network.com/nestopia](http://www.vg-network.com/nestopia)
[http://nestopia.sourceforge.net/](http://nestopia.sourceforge.net/)
[http://rbelmont.mameworld.info/?page_id=200](http://rbelmont.mameworld.info/?page_id=200)

I haven't specifically checked out your work, but your goal is great! Having a nice user friendly interface for loading and playing NES games is great. :)

a lot of work is being done to the fceu codebase.  a new branch called fceux is sort of merging features from all of the forks of fceu and adding a lot of new ones.  i'm actually working on the code for the linux port.  the new version is really improving and gfceu is improving along with it.  once we get a release together, i will try to get some packages for us ubuntu people :)

---

### Post by CC_machine on 2008-07-03
you're a Linux user that doesnt know how to "man fceu" and then apply "fceu <romname> <arguments>" in a terminal? seriously, not that hard. the only thing i disliked was the default controls, and that took me 20 seconds to grab the right arguments to let me input my own.

but then again, this is for Ubuntu users. Rock on dude!

---

### Post by punkrockguy318 on 2008-07-03
> **CC_machine said:**
> you're a Linux user that doesnt know how to "man fceu" and then apply "fceu <romname> <arguments>" in a terminal? seriously, not that hard. the only thing i disliked was the default controls, and that took me 20 seconds to grab the right arguments to let me input my own.

but then again, this is for Ubuntu users. Rock on dude!

Regardless of whether you have the technical ability to run command line arguments or not; It's convenient to have a GUI that will remember your options for you and what not.

---

### Post by dfreer on 2008-07-03
> **punkrockguy318 said:**
> a lot of work is being done to the fceu codebase.  a new branch called fceux is sort of merging features from all of the forks of fceu and adding a lot of new ones.  i'm actually working on the code for the linux port.  the new version is really improving and gfceu is improving along with it.  once we get a release together, i will try to get some packages for us ubuntu people :)

Thanks a lot for working on this, looking forward to it!

---

### Post by punkrockguy318 on 2008-08-03
FceuX 2.0.0 was just released and sports a whole set of new features.  GfceuX 2.0.0 was also released alongside it, and you can grab them both from the source tarbel.  Check it out on the [website]("http://fceux.com").

---

### Post by Bagleemo on 2008-10-16
I'm wondering if anyone knows how to disable the number key inputs to choose save slot on fceu(x?)? 
I have a mame cabinet running wahcade as a front end for fceu, amongst others. It uses a keyboard encoder for many of the buttons I use to play. I can and have easily mapped them to the gamepad. I am running Ubuntu 8.04 and it works great, the only problem is the buttons I have mapped to select and start are number keys, so while they do work for select and start they also bring up that little save slot number overlay thing, which is kind of tacky and confuses people when they are playing. Anyway to unmap them from the save slot feature?  I can't change their keyboard encoder value cause that would hose up mame and others.

---

### Post by punkrockguy318 on 2008-10-17
> **Bagleemo said:**
> I'm wondering if anyone knows how to disable the number key inputs to choose save slot on fceu(x?)? 
I have a mame cabinet running wahcade as a front end for fceu, amongst others. It uses a keyboard encoder for many of the buttons I use to play. I can and have easily mapped them to the gamepad. I am running Ubuntu 8.04 and it works great, the only problem is the buttons I have mapped to select and start are number keys, so while they do work for select and start they also bring up that little save slot number overlay thing, which is kind of tacky and confuses people when they are playing. Anyway to unmap them from the save slot feature?  I can't change their keyboard encoder value cause that would hose up mame and others.

Improved button mapping is one of my next big goals for linux fceux once I get the time and motivation.  I've started work on a GUI for editing button mapping coniguration, but it has a little ways to go.

Come to think of it, there is NO possible way to do this in the SDL build.  Wow, I never noticed how lame that was.  I should be able to fix it up in the subversion build (sometime), but I have no idea when the rest of the team will be ready to release 2.0.3.

I remember the code for that being rather um disgusting but I'll work on it when I get a chance.  Your best bet is to file a bug in the fceux bug tracker ([http://sourceforge.net/tracker2/?group_id=13536](http://sourceforge.net/tracker2/?group_id=13536)) and mark it with sdl and i'll check it out eventually.

---

### Post by punkrockguy318 on 2008-10-17
there's a lot of WTF code in that part of the sdl build . . . it looks likes a lot of things will need to be cleaned but i'll keep my IDE open that file in hopes that it will motivate me to clean it up a little bit and get that issue resolved.

---

### Post by Bagleemo on 2008-10-17
Ah, great! Thanks for the info. I have filed a bug as per your instructions. And thanks for all your work making such a great emulator!

---

### Post by buckeyered80 on 2008-10-28
Hey, sorry if I missed this somewhere in this thread, but did anyone ever get fullscreen aspect ratio working correctly? Mine will scale to fullscreen when I check the OpenGL rendering option, but it has white flashing lines on the top and bottom of the screen.  However, it works perfectly without the opengl...but I prefer the fullscreen.  Any ideas?

---

### Post by punkrockguy318 on 2008-10-29
> **buckeyered80 said:**
> Hey, sorry if I missed this somewhere in this thread, but did anyone ever get fullscreen aspect ratio working correctly? Mine will scale to fullscreen when I check the OpenGL rendering option, but it has white flashing lines on the top and bottom of the screen.  However, it works perfectly without the opengl...but I prefer the fullscreen.  Any ideas?

what version of fceu are you using?  the fullscreen scaling has improved greatly in the 2.x branch; i'd reccomend switching to that if your using fceu 1.x

---

### Post by buckeyered80 on 2008-10-29
I'll check the version when I get back to my Kubuntu machine.  I got it from synaptic just the other night, so I am not sure if synaptic keeps that updated pretty well or not.  I'll get back to you with that tonight.  Thanks for the response!

---

### Post by punkrockguy318 on 2008-10-29
> **buckeyered80 said:**
> I'll check the version when I get back to my Kubuntu machine.  I got it from synaptic just the other night, so I am not sure if synaptic keeps that updated pretty well or not.  I'll get back to you with that tonight.  Thanks for the response!

yeah that's the 1.x series.  the 1.x series is really old actually, and unfortunately 2.x didn't get into the repos (even for 8.10).

---

### Post by malleus74 on 2008-10-29
punkrockguy318: 

I had an idea I posted on Ubuntu Brainstorm the other day:

[http://brainstorm.ubuntu.com/idea/14906/](http://brainstorm.ubuntu.com/idea/14906/)

A lot of other projects aren't as user-friendly as yours. What do you think of the basic idea?

---

### Post by buckeyered80 on 2008-10-29
Ok thanks PunkRockGuy.  What is the best way to upgrade?  Can you post the link to the latest and greatest 2.x package?  Thanks for all the work you've done on this.  I think it actually works better than my Windows NES emulators...very smooth emulation.  Thanks again.

---

### Post by buckeyered80 on 2008-10-29
OK, I found the latest package.  But I don't know how to install it.  Anyone who has it working properly, can you make a how-to?  It I don't want to get stuck in a dependency battle, lol.

---

### Post by Felson on 2008-10-29
Not that this helps you now.... But if you find a good how-to, post in my "Emulation How-To Links" thread (link in my sig). For that one, and any others for that matter.

---

### Post by buckeyered80 on 2008-10-30
Yeah Felson,

If no one posts a how-to by this weekend, I will try to figure it out on my own and I'll see what I can do.  Long live NES gaming.

---

### Post by punkrockguy318 on 2008-10-30
> **buckeyered80 said:**
> Yeah Felson,

If no one posts a how-to by this weekend, I will try to figure it out on my own and I'll see what I can do.  Long live NES gaming.

will do when i'm less drunk

just someone post tomorrow and bump this topic so i remember

---

### Post by buckeyered80 on 2008-10-31
Haha...ok punkrockguy, sober up and write a how-to!  I was reading the posts earlier and I noticed that SteveJesus had the same problem.

---

### Post by punkrockguy318 on 2008-11-03
> **buckeyered80 said:**
> Haha...ok punkrockguy, sober up and write a how-to!  I was reading the posts earlier and I noticed that SteveJesus had the same problem.

i'll write somethin up tonight, i totally forgot about this thread

---

### Post by alexhrdr on 2008-11-04
> **punkrockguy318 said:**
> i'll write somethin up tonight, i totally forgot about this thread

Yes please.  Thank you so much!

---

### Post by punkrockguy318 on 2008-11-05
[http://ubuntuforums.org/showthread.php?p=6108669#post6108669]("http://ubuntuforums.org/showthread.php?p=6108669#post6108669")

I posted a guide here.  Please test this out!  I might has missed some things out, I have installed fceux on a fresh system in a while.

Enjoy!

---

### Post by buckeyered80 on 2008-11-05
Ok thanks PunkRockGuy.  Everything went fine up until the scons install.  I installed the dependencies, downloaded the source package of fceux, and extracted it to home directory.  Then when I went to cd into the FCEU directory and:

 ```
sudo scons install
```

I got this:

```
$ sudo scons install
scons: Reading SConscript files ...
platform:  posix
Checking for C library SDL... yes
Checking for C library z... no
Did not find libz or z.lib, exiting!

```

What the heck is library z?  lol

---

### Post by Felson on 2008-11-06
Try doing the following. I think it's the one you need.
```

sudo aptitude install zlib1g-dev

```

---

### Post by Felson on 2008-11-06
Delete

---

### Post by punkrockguy318 on 2008-11-06
> **buckeyered80 said:**
> Ok thanks PunkRockGuy.  Everything went fine up until the scons install.  I installed the dependencies, downloaded the source package of fceux, and extracted it to home directory.  Then when I went to cd into the FCEU directory and:

 ```
sudo scons install
```

I got this:

```
$ sudo scons install
scons: Reading SConscript files ...
platform:  posix
Checking for C library SDL... yes
Checking for C library z... no
Did not find libz or z.lib, exiting!

```

What the heck is library z?  lol

forgot a dependency, thanks.  libz-dev is required.  fixed in the howto

---

### Post by buckeyered80 on 2008-11-06
You guys are awesome, thanks for the quick reply.  I will test it when I get home and let you know the results.

---

### Post by buckeyered80 on 2008-11-06
Ok it works now....the depency missing was actually zlib1g-dev.  Works like a charm...thanks for your help PunkRockGuy.

---

### Post by punkrockguy318 on 2008-11-10
If you are having issues with sound, check this post out:
[http://ubuntuforums.org/showthread.php?p=6142341#post6142341](http://ubuntuforums.org/showthread.php?p=6142341#post6142341)

---

### Post by decadude on 2009-01-19
does anyone have a precompiled debian package for nestopia??

one that just autoinstalls and has an icon and what not


also does anyone know a way to save state in games on gfceu

thanks to all who reply

---

### Post by punkrockguy318 on 2009-01-19
> **decadude said:**
> does anyone have a precompiled debian package for nestopia??

one that just autoinstalls and has an icon and what not


also does anyone know a way to save state in games on gfceu

thanks to all who reply

save/load state f5/f7

---

