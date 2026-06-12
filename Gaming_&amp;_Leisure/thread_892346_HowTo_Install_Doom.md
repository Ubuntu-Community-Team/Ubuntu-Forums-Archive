---
title: "HowTo Install Doom"
date: 2008-08-17
forum: Gaming &amp; Leisure
---

### Post by billybag on 2008-08-17
This is my first How To and i am writing it because it took me a very very long time to install Doom on my machine. Their were many methods and directions that i found were confusing. I am hoping to deter anyone else from having the same problems and making the same mistake

[B]
Method 1. COMMON SENSE (synaptic)[/B]
*Note: You may laugh, but i actually discovered this AFTER trying methods 2 and 3!*
Open up terminal and type:
```
sudo apt-get install doom-wad-shareware prboom
```
Now click on PrBoom in your games menu.

**IF YOU EXPERIENCE FREEZING:**
Create the following empty file: /etc/timidity/timidity.cfg

This is definitely the easiest method, but it may not be for everybody so here are 2 other methods.

**METHOD 2: LEGACY**
*Note: This method took me a while to figure out and for a while i thought i was doing something wrong or missing something. Their was a lack of instruction on the internet and i had to piece this together myself. I used the doom-wad-shareware file for my .wad. I have sound working and this could be why, but i don't know for sure.*

1. First you MUST HAVE a .WAD file. This contains everything (sounds, maps, etc.):
**doom-wad-shareware** can be installed via terminal or synaptic
```
sudo apt-get install doom-wad-shareware
```
alternatively you can download the **FreeDOOM** .wad from this site [http://freedoom.sourceforge.net/download/]("http://freedoom.sourceforge.net/download/")

if you downloaded the doom-wad-shareware version from synaptic, you may wonder where the .wad file is when i tell you to move it. It is located in /usr/share/games/doom

2. Download the newest LEGACY files from here [http://legacy.newdoom.com/downloads.php]("http://legacy.newdoom.com/downloads.php")

3. Extract the .zip file to your home folder (or wherever you prefer) and place your.wad file directly into it. Now open up terminal and enter the extracted folder (i will assume you placed it into your home folder)

```
cd legacy_142_linux
``` and hit ENTER
```
./llxdoom
``` and hit enter
Some wacky stuff will happen. It will let you know if your .wad file cannot be found. If it isn't, then you forgot to place it into the extracted legacy folder. 

Now type
```
./lsdldoom
```
If everything went well, you should be ready to play!


**Method 3. DOS**
*Note: This method is fairly easy but inconvenient. It is a process to start the game up every time you want to play. This uses the original DOOM engine, however, and may be liked by collectors or people who would just like to have the original DOOM*

1. Download DOSBox. It is available under SYNAPTIC, GETDEB.NET or by typing the following into terminal:
```
sudo apt-get install dosbox
```

2. download the folowing zip file [ftp://ftp.idsoftware.com/idstuff/doom/doom19s.zip]("ftp://ftp.idsoftware.com/idstuff/doom/doom19s.zip")

3. Extract the the .zip to your home directory. You should now have a folder called 'doom19s'

4. open up DOSBox. It should be located under games in your gnome panel menu. Type the following:

```
mount c ~/doom19s
``` and hit ENTER
You will get the following message:
*Drive C is mounted as local directory /home/billy/doom19s*
Now type 
```

c:

```
The Z\:> will now be a C:\> and type in:
```
DEICE.EXE
```

5. You will now get the setup screen. It will ask you which drive you would like to install to. type c and hit enter.

It will then ask you for a directory name. Hit enter unless you would like to call the directory something else. I am unsure if this will screw anything up, to be safe, i would keep it the way it is and hit enter

It will tell you the directory does not exist. Type y to create it anyway.

6. We are brought back to the dos prompt screen. We now type in the following:
```
DOOMS_19.EXE
``` and hit ENTER
It will now extract some files. THIS TAKES A FEW MINUTES. It will seem like it has stopped at ```
Inflating: DOOM1.WAD
``` but it hasn't so don't worry.

After it is done (the last file it extracts will be SETUP.EXE) type the following:

```
SETUP.EXE
``` and hit enter

7. You are now brought to the DOOM SETUP WIZARD. This all depends on your system and if you are unsure, then i suggest just hitting enter through the whole thing. I selected Keyboard + Mouse for my controller type, but was unsure when it came to the sound. I hit enter through out the whole sound setup and received **no sound problems when it came to actual game play** which is a huge plus. So i hit enter 3 times and then selected ```
Save parameters and launch DOOM
```

To quit DOOM (and DOSBox):
Hit Esc key to bring you to the menu. Use your arrows to select QUIT then hit Y. You will be brought back to the DOSBox prompt. type ```
exit
``` to leave DOSBox

To play DOOM: Open DOSBox.
Type ```
mount c ~/doom19s/DOOMS
``` and hit ENTER
Type ```
c:
``` and hit ENTER
Type ```
DOOM.EXE
```

don't make funn. I really hope this proves useful for people!!!

REFERENCES: [http://gentoo-wiki.com/HOWTO_Play_Doom#Shareware_Doom]("http://gentoo-wiki.com/HOWTO_Play_Doom#Shareware_Doom")
[http://legacywiki.net/index.php/Main_Page]("http://legacywiki.net/index.php/Main_Page")
[http://freedoom.sourceforge.net/download/]("http://freedoom.sourceforge.net/download/")

---

### Post by grossaffe on 2008-08-17
yes, but can it play doom?

edit: oh, and I've always been partial to the Enhanced Doom Gaming Engine (EDGE)

though that one can't exactly run the rickroll wad (I haven't figured out how to get that to work in linux.  Its a zdoom wad if I remember correctly)

---

### Post by Crafty Kisses on 2008-08-17
Nice tutorial, I still need to get my full copy of DOOM, I know it's laying around here somewhere.

---

### Post by Despot Despondency on 2008-08-17
Hey, thanks for the tutorial. Tried the first method but it keeps freezing. Tried creating an empty file /etc/timidity/timidity.cfg, but it still seems to freeze. Any other ideas? Cheers

---

### Post by Orlsend on 2008-08-17
> **Despot Despondency said:**
> Hey, thanks for the tutorial. Tried the first method but it keeps freezing. Tried creating an empty file /etc/timidity/timidity.cfg, but it still seems to freeze. Any other ideas? Cheers
I have the same problem too

---

### Post by Despot Despondency on 2008-08-17
Tried downloading lxdoom instead and it seems to be working, nut with a few errors, 

1) can't maximize the screen

2) the screen is semi-transparent upon loading, though I solved this by holding down alt and scrolling the mouse wheel. see link [http://http://ubuntuforums.org/showthread.php?t=656663&highlight=lxdoom]("http://http://ubuntuforums.org/showthread.php?t=656663&highlight=lxdoom")

Would still like to know how to maximize the screen, or even just resize it a bit, as it is pretty small at the moment. Forgot how bad I am at this game.

---

### Post by Laibcoms on 2008-08-17
Personally, I do it like this:

Step 1: Check via Applications -> Add/Remove
Step 2: If it's not listed there, check via Synaptic (GUI version) - easier installation and uninstallation
Step 3: Download via the official website for the Ubuntu or Linux version and install it (compile if needed)
Step 4: If still to no avail, then other methods as you've listed ;) like DOSbox, etc.

Good job tho ^_^

---

### Post by dado prso on 2008-08-17
Method 1:

create   /etc/timidity/timidity.cfg

I can't create this file.  I don't have permission.

---

### Post by dado prso on 2008-08-17
Nevermind, I'm stupid.

---

### Post by Master O on 2008-08-17
Another easy way to play Doom in Linux:

[www.skulltag.com](www.skulltag.com), which not only provides full multiplayer for Ultimate Doom, Doom 2, Heretic, and Hexen, but is also fully available for Linux.

I fully recommend it, especially its Invasion mode.

All you have to do is put your doom.wad and/or doom2.wad (your choice) in the same folder as skulltag and you're all set.

---

### Post by billybag on 2008-08-17
In your home folder their is a foldef called .prboom. In their contains a file called brboom.cfg. Open this in text editor and search for where it says 'full screen     0'. Change this to 1 for fullscreen


as for the still freezing after creating the timidity file, try actually installing timidity. I found this fix in a bug report and either method was suggested. i didnt post the second suggestion because i didnt think it would be needed... but perhaps it is for some people

as far as transparency. this could be because of compiz. I installed the compiz-icon-button from synaptic. This allows me to quickly switch between compiz and metacity which i do before i play a game. you can also probably define the opacity settings to ignore the doom window via the general option and then the opacity tab

---

### Post by billybag on 2008-08-17
> **Master O said:**
> Another easy way to play Doom in Linux:

[www.skulltag.com](www.skulltag.com), which not only provides full multiplayer for Ultimate Doom, Doom 2, Heretic, and Hexen, but is also fully available for Linux.

I fully recommend it, especially its Invasion mode.

All you have to do is put your doom.wad and/or doom2.wad (your choice) in the same folder as skulltag and you're all set.


i dont nknow man. i just tried this and ir broke my prboom. now i cant get it to work and i never even got skulltag to work.

EDIT. So ironically, after trying to install skulltag, my prboom no longer works and after a couple hours trying to fix it, i have not succeeded... oh the irony

---

### Post by Master O on 2008-08-17
> **billybag said:**
> i dont nknow man. i just tried this and ir broke my prboom. now i cant get it to work and i never even got skulltag to work.

EDIT. So ironically, after trying to install skulltag, my prboom no longer works and after a couple hours trying to fix it, i have not succeeded... oh the irony

There's no need to put prboom in skulltag.  I clearly said all you needed  (was the original doom.wad and doom2.wad, which you then put in the same folder as skulltag.pk3, skulltag-server, skulltag, and skulltag.wad.  Upon running skulltag, it'll ask which doom you want to play.

I never said anything about installing it with PRboom.

Hopefully this should also help:

[http://skulltag.com/wiki/Setting_up#Installing_the_Skulltag_Client_on_Linux.2FFreeBSD](http://skulltag.com/wiki/Setting_up#Installing_the_Skulltag_Client_on_Linux.2FFreeBSD)

---

### Post by Laibcoms on 2008-08-17
Hmm. skulltag, very interesting, I'll try that one.   I miss Doom 2! :p

Thanks for the link ;)

Update:
Ok, it's a MOD... I will need Doom files T_T  anyone can provide a link?  Probably with Heretic also :p

Tnx tnx

---

### Post by Despot Despondency on 2008-08-18
For lxdoom you have to change the setting in the file /lxdoom/boom.cfg, which is the home folder. It's has screen_width and screen_height setting that you set to preference.

With regard to prboom freezing, I tried installing timidity but it still froze.

Will try out you suggestions with regard to transparency. cheers

---

### Post by grossaffe on 2008-08-18
> **Laibcoms said:**
> Hmm. skulltag, very interesting, I'll try that one.   I miss Doom 2! :p

Thanks for the link ;)

Update:
Ok, it's a MOD... I will need Doom files T_T  anyone can provide a link?  Probably with Heretic also :p

Tnx tnx

I'm pretty sure that stuff is on the same level as ROMs, just don't ask about them.

---

### Post by Laibcoms on 2008-08-19
Yah.  Found Doom 1 and Doom 2, as well as Heretic!  hehe :p

Digging up, it seems they just make the old game run on newer machines.  The way I understood it, the Ports can also add new features and graphics on-top of the old file and voila running in newer machines.

Very interesting implementation, using the original gamefile (just one lol doom.wad, doom2.wad, heretic.wad), and interesting iD soft put everything in one file hehe.

---

### Post by grossaffe on 2008-08-19
> **Laibcoms said:**
> Yah.  Found Doom 1 and Doom 2, as well as Heretic!  hehe :p

Digging up, it seems they just make the old game run on newer machines.  The way I understood it, the Ports can also add new features and graphics on-top of the old file and voila running in newer machines.

Very interesting implementation, using the original gamefile (just one lol doom.wad, doom2.wad, heretic.wad), and interesting iD soft put everything in one file hehe.
well, they aren't exactly ports as much as they are their own engines.  Many of them change it from pseudo 3d into true 3d.  oh, and a fun mod to check out i the Goldeneye Total Conversion.  its a pretty good remake of goldeneye for the EDGE engine (though its probably still being worked on, but a lot of levels are already done.)

---

### Post by linuxguymarshall on 2008-08-19
I am having trouble running my DOOM wads with anything. I kept my wad collection in a .rar file and the other day when I decompressed them all the borders of objects had a white outline. This had not happened any other time I decompressed them and it is not the source port because FreeDOOM works just fine.

Any ideas?

---

### Post by Azure.Rise on 2008-09-14
I've installed prboom, freedoom, and the shareware wad file through Synaptic. It automatically  loads freedoom and I can't figure out how to run the shareware file. Any help?

---

### Post by The Spy on 2008-09-27
Does PrBoom support multiplayer?

---

### Post by chungy on 2008-09-28
> **billybag said:**
> 
**Method 3. DOS**
*Note: This method is fairly easy but inconvenient. It is a process to start the game up every time you want to play. This uses the original DOOM engine, however, and may be liked by collectors or people who would just like to have the original DOOM*

Better idea is to use Chocolate Doom: [http://chocolate-doom.org/](http://chocolate-doom.org/)

---

### Post by Azure.Rise on 2008-10-01
Does anyone know how to load a specific WAD file? I want to load the shareware file for DOOM, because it loads the FreeDoom one by default.

---

### Post by chungy on 2008-10-01
"prboom -iwad /path/to/doom1.wad" should work, assuming the package behaves normally (I compile prboom plus from SVN myself :/)

---

### Post by Azure.Rise on 2008-10-01
Thanks, that worked.

---

### Post by SilverWave on 2008-12-06
Thanks! that was just what I was looking for.
Here is what works for me on 8.10.

doom -iwad /usr/share/games/doom/doom1.wad
or
prboom -iwad /usr/share/games/doom/doom1.wad

---

### Post by michelkogan on 2009-12-26
wow ... iddqd works great :D

---

### Post by perspectoff on 2010-08-14
I personally like the quick, simple instructions at

Ubuntuguide: [http://ubuntuguide.org/wiki/Ubuntu:All#Skulltag](http://ubuntuguide.org/wiki/Ubuntu:All#Skulltag)

Kubuntuguide: [http://kubuntuguide.org/All#Skulltag](http://kubuntuguide.org/All#Skulltag)

PrBoom is frustrating compared to Zdoom. I actually installed Zdoom in Ubuntu using 

[http://zdoom.org/wiki/Compile_ZDoom_on_Linux](http://zdoom.org/wiki/Compile_ZDoom_on_Linux)

It works nicely.

Of course, Skulltag is ZDoom modified for online play, and I only play Skulltag now.

---

### Post by QwUo173Hy on 2010-09-05
I'm running Skulltag on a Pentium III, with 512 megs of RAM and it's quite sluggish. When I ran Doom originally (years ago), a 486 with 16 MB of RAM was plenty. Am I doing something really stupid here or what?

---

### Post by perspectoff on 2010-09-05
> **Master O said:**
> Another easy way to play Doom in Linux:

[www.skulltag.com](www.skulltag.com), which not only provides full multiplayer for Ultimate Doom, Doom 2, Heretic, and Hexen, but is also fully available for Linux.

I fully recommend it, especially its Invasion mode.
t
All you have to do is put your doom.wad and/or doom2.wad (your choice) in the same folder as skulltag and you're all set.

Oh gawd yes! Skulltag all the way!

Skulltag is an enhanced version of Zdoom that allows network play easily. It facilitates WAD acquisition and all kinds of things.

I have played the old PrBoom after playing Zdoom and it is like going back to gas lighting instead of electricity!

See:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Doom](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Doom)

and 

[http://kubuntuguide.org/Lucid#Doom](http://kubuntuguide.org/Lucid#Doom)


Instructions for Skulltag, Zdoom, and PrBoom are all there.

---

### Post by perspectoff on 2010-09-05
> **The Spy said:**
> Does PrBoom support multiplayer?

No. you want Skulltag.

---

### Post by perspectoff on 2010-09-05
> **jarlath said:**
> I'm running Skulltag on a Pentium III, with 512 megs of RAM and it's quite sluggish. When I ran Doom originally (years ago), a 486 with 16 MB of RAM was plenty. Am I doing something really stupid here or what?

Well, Skulltag is network oriented. Your speed is probably due to your Internet connection and slower computers are intirinsically slower on the Internet.

If you don't want to play network multiplayer and just want Zdoom, then see

[http://zdoom.org/wiki/Compile_ZDoom_on_Linux](http://zdoom.org/wiki/Compile_ZDoom_on_Linux)

---

### Post by QwUo173Hy on 2010-09-05
> **perspectoff said:**
> Well, Skulltag is network oriented. Your speed is probably due to your Internet connection and slower computers are intirinsically slower on the Internet.

If you don't want to play network multiplayer and just want Zdoom, then see

[http://zdoom.org/wiki/Compile_ZDoom_on_Linux](http://zdoom.org/wiki/Compile_ZDoom_on_Linux)
Thanks perspectoff. I'm actually playing locally - alone. But I'll try zdoom anyway and see what I can get out of it.

---

