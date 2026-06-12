---
title: "Request: Dwarf Fortress how to help"
date: 2009-08-10
forum: Gaming &amp; Leisure
---

### Post by kenji_03 on 2009-08-10
[FONT=Arial][SIZE=2]Ok so I decided to check out linux because I heard Dwarf Fortress would run faster on it than it would on Vista.  I installed Ubuntu but I'm not sure I have everything I need.  The read-me file of the [Linux-native version (link2gameFile)]("http://www.bay12games.com/dwarves/df_28_181_40d13_linux.tar.bz2") says that I need the following packages.
--:KS--
* GTK+2 (or higher)
*SDL 1.2+
*SDL_image

And an OpenGL impelentation program:

* libgl
* libglu
--:KS--
Now i have heard that Ubuntu has a lot of this stuff already covered, but what do I need to download and what do I not?  I am on an AMD machine and I see the[ Dwarf Fortress Wikia]("http://dwarffortresswiki.net/index.php/System_requirements#Ubuntu.2FKubuntu") says all I need is the [/SIZE][/FONT]  [FONT=Arial][SIZE=2]libsdl-image1.2_1.2.6-3_i386.deb file, but the link provided is an "Intel x86 machine" version.  Is there an AMD x86 machine version or will I be okay with the Intel version.  Also, what is the title for this file in the repository?

I know this is a ton of questions but I've seen a lot of other people who are new to Ubuntu and want to play Dwarf Fortress, so can anyone with more experience help me build a "how to" guide?

(Side note, I picked Ubuntu because of this forum, with free "tech support" like this I don't think I'll ever go back to ***dows.[/SIZE][/FONT]

---

### Post by Grishka on 2009-08-10
have you tried simply running the game from it's directory? just double click 'df'.

---

### Post by kenji_03 on 2009-08-12
> **Grishka said:**
> have you tried simply running the game from it's directory? just double click 'df'.
Yes, I get 8 FPS

---

### Post by DoFa on 2009-08-25
hi kenji

i too swapped from windonts 7 to linux beliving DF to be faster,
in my experience it is Much faster due to less consumption of your cpu/ ram etc.

I LOVE DF my fave game of all time

first off DL the newest version of DF 40d14 here

[http://www.bay12games.com/dwarves/df_28_181_40d14_linux.tar.bz2](http://www.bay12games.com/dwarves/df_28_181_40d14_linux.tar.bz2)

its got some neat new features (ZOOOOOOM how long weve w8ed!) 

what sort of system are u running?
8fps seems very shoddy

atom pcs can do that

please post ur specs including ur ubuntu version im using Jaunty (9.04)
and have no trouble running DF "out of box" without any of those things u mentioned.

unpack the Tar file same way as u would a zip file drag and drop all the stuff into a folder in ur /home/myname/DF (for example)

DONT click on the dwarffort.exe file u have to double click the df shell script file. 
its called DF and has >_ on the front of it.

have you run DF before on ur old OS? if no the be sure to DL the tilesets and graphic sets to they make the game look so awesome mike maydays are good.

are u trying to run a 16x16 starting grid??????

my specs are
acer aspire 5720
Ubuntu "Jaunty Jakalope" 9.04 32 bit
intel Duo T7500
4gb RAM
intel X3100 graphic media slowdowner (worst graphic onboard ever)

i get 20 fps running a 16x16 grid size with 7 dorfs.

 try running a smaller grid size i find 3x3 will hold all the stuff ull ever need or be able to use and can run 100fps till around 50 dorfs the 70fps at 70ish then it gets bad 50fps at 90ishdorfs maxing out at 20-30fps for 150 dorfs (thats pretty quick for that many dorfs btw :P) and down and down :) set the dorf limit in the init file to 100 cos thats the most u need to get all the features.

go for a medium world size or smaller unless u have an  Uber pc

if you have a rather slow comp theres a whole load of things u can do to max the framrate on the DF wiki

[http://www.dwarffortresswiki.net/index.php/Maximizing_framerate](http://www.dwarffortresswiki.net/index.php/Maximizing_framerate)

if you are still completly stuck or are new to DF and are unsure hoe to do it i could always media fire a copy for  with all the SPEEEEEEEED reducing stuff turned off with all the nice tilesets too if u get desperate? but u should try it urself first in case u wanna change stuff in the future.

hope this helps, dont forget to ping ur rig plz so i can suggest how much fps ull be getting or maybe some things to take in account running DF :)


DoFa
Strike The Earth

---

### Post by DoFa on 2009-08-25
i was reading thru ur last post again and seeing as im still a linux noob myself i just realised ur running a 64bit linux? 

i looked thru the DF wiki and found out this for you......

if your using ubuntu jaunty goto system -> admin -> synaptic pakage manager and type the package in "libsdl-image1.2_1.2.6-3_i386" tick the box and off u go dont ever download from a none secure source always use package manager as its a lot more secure plus it finds the dependecies for u.

** Ubuntu/Kubuntu - Using getlibs**

 The other way to get the require SDL_image library is to use getlibs, which will get the correct 32bit library when run on 64bit Ubuntu and create all the required links. 
At a command prompt: 
  sudo apt-get install ia32-libs getlibs
 sudo getlibs -l libSDL_image-1.2.so.0
The game can now be run from the df_linux folder (or wherever you extracted it to) using the df script


these details are available here:
[http://dwarffortresswiki.net/index.php/System_requirements](http://dwarffortresswiki.net/index.php/System_requirements)

about halfway down :)

DoFa
DoFa cancels sleep : Playing Dwarf Fortress

---

### Post by Torrasque on 2011-11-19
I too need help with this. I have tried running it right from the df file but nothing happens.

---

### Post by oldrocker99 on 2011-11-21
> **kenji_03 said:**
> [FONT=Arial][SIZE=2]Ok so I decided to check out linux because I heard Dwarf Fortress would run faster on it than it would on Vista.  I installed Ubuntu but I'm not sure I have everything I need.  The read-me file of the [Linux-native version (link2gameFile)]("http://www.bay12games.com/dwarves/df_28_181_40d13_linux.tar.bz2") says that I need the following packages.
--:KS--
* GTK+2 (or higher)
*SDL 1.2+
*SDL_image

And an OpenGL impelentation program:

* libgl
* libglu
--:KS--
Now i have heard that Ubuntu has a lot of this stuff already covered, but what do I need to download and what do I not?  I am on an AMD machine and I see the[ Dwarf Fortress Wikia]("http://dwarffortresswiki.net/index.php/System_requirements#Ubuntu.2FKubuntu") says all I need is the [/SIZE][/FONT]  [FONT=Arial][SIZE=2]libsdl-image1.2_1.2.6-3_i386.deb file, but the link provided is an "Intel x86 machine" version.  Is there an AMD x86 machine version or will I be okay with the Intel version.  Also, what is the title for this file in the repository?

I know this is a ton of questions but I've seen a lot of other people who are new to Ubuntu and want to play Dwarf Fortress, so can anyone with more experience help me build a "how to" guide?

(Side note, I picked Ubuntu because of this forum, with free "tech support" like this I don't think I'll ever go back to ***dows.[/SIZE][/FONT]

Package files named *_i386.deb are for ANY 32-bit system, regardless of processor manufacturer. Packages which are named *_amd64 work on ANY 64-bit system, including modern Intel CPUs, even with the "amd64" in the name, the reason being that AMD came out with the first 64-bit CPU. 

Just so you know, and knowing is half the battle (GI Joe):D

---

### Post by Elfy on 2011-11-21
Closed.

@Torrasque - start your own thread. Don't resurrect an old one.

---

