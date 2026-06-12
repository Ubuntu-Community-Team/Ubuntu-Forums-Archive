---
title: "Installing MAME for 6.06"
date: 2006-07-25
forum: Gaming &amp; Leisure
---

### Post by Wheelybin on 2006-07-25
Hello there, I had a look at [this old thread](http://www.ubuntuforums.org/showthread.php?t=10329) and [this blog](http://my.opera.com/Mr%20Green/blog/show.dml/171040) but neither seems to be any use (Rather, I don't understand the former).

How do I get MAME/Xmame/UbuntuMAME/Mame that works on Ubuntu to download and install? Many thanks.

---

### Post by Wheelybin on 2006-07-26
Great! I read [this](http://www.ubuntuforums.org/showthread.php?t=183561) and it's downloading. Unfortunatly I cannot get xmame, last place I looked didn't have it.

---

### Post by TasKiNG on 2006-07-26
right, installing xmame is quite easy when you know how :)
this is how i installed it under dapper drake

edit your /etc/apt/sources.list file and make sure you have these two lines ( note if not using dapper then replace with what you are using) :-

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper multiverse

now type:    sudo apt-get update

then:        sudo apt-get install xmame-common

now click on the link below to download the GXmame .deb file:  
[http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb](http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb)

in a terminal window in the same directory that you stored the above .deb file type:   sudo dpkg -i gxmame_0.35beta2-1_i386.deb

Thats xmame and a good frontend installed. you might want to remove those two lines now that you added to your sources.list file.

your roms files now need to go into the /usr/share/games/xmame/roms directory. ( i did a sudo chmod -R 777 /usr/share/games/xmame first ).

you will now find a shortcut to GXmame in your start menu under games.

run it and select "rebuild game list" then "file/audit all games"
when done click on "available" and you should see the roms that you are using.

Hope this helps

Cheers

TasKiNG

---

### Post by andlinux21 on 2006-07-30
Thanks for the help I couldn't get my ROMs to play but after chmod the folder everything works fine now.  I have a USB joystick to configure then its back down memory lane for me...:D

---

### Post by patrick295767 on 2006-07-31
> **TasKiNG said:**
> right, installing xmame is quite easy when you know how :)
this is how i installed it under dapper drake

edit your /etc/apt/sources.list file and make sure you have these two lines ( note if not using dapper then replace with what you are using) :-

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper multiverse

now type:    sudo apt-get update

then:        sudo apt-get install xmame-common

now click on the link below to download the GXmame .deb file:  
[http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb](http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb)

in a terminal window in the same directory that you stored the above .deb file type:   sudo dpkg -i gxmame_0.35beta2-1_i386.deb

Thats xmame and a good frontend installed. you might want to remove those two lines now that you added to your sources.list file.

your roms files now need to go into the /usr/share/games/xmame/roms directory. ( i did a sudo chmod -R 777 /usr/share/games/xmame first ).

you will now find a shortcut to GXmame in your start menu under games.

run it and select "rebuild game list" then "file/audit all games"
when done click on "available" and you should see the roms that you are using.

Hope this helps

Cheers

TasKiNG

Hi,   
 
I was trying to play killer instinct 1 under linux with mame. I still could not make it to play this one.
Have you ever tried this game ?
  [http://www.vgfreak.com/images/screens/killer1-1.jpg](http://www.vgfreak.com/images/screens/killer1-1.jpg)
  
(I think I'll check my rom ... for the mame)

Grezt

---

### Post by Bigs on 2006-08-01
> **patrick295767 said:**
> Hi,   
 
I was trying to play killer instinct 1 under linux with mame. I still could not make it to play this one.
Have you ever tried this game ?
  [http://www.vgfreak.com/images/screens/killer1-1.jpg](http://www.vgfreak.com/images/screens/killer1-1.jpg)
  
(I think I'll check my rom ... for the mame)

Grezt

Killer Instinct (along with several other games) requires its CHD (hard disk image, as the files were too big to store on ROM chips) file put into the CHD directior of MAME. There are places where you can get the full collection of CHD files, but the collection of them is about 35 Gig.

---

### Post by MaximB on 2006-08-02
I've installed kxmame BUT when I try to run somthing it's says :
No valid xmame/xmess executables found
even after I find and add the kxmame file in the directories
what can I do ?

---

### Post by patrick295767 on 2006-08-02
> **Bigs said:**
> Killer Instinct (along with several other games) requires its CHD (hard disk image, as the files were too big to store on ROM chips) file put into the CHD directior of MAME. There are places where you can get the full collection of CHD files, but the collection of them is about 35 Gig.

35Gig ? wow
 
For KILLER INSTINCT 1:
When I had windoze in the past, I used a special emulator.
My roms were about 600 MB, one cdrom, and the program : 

damn I cant recall, 
I dont think it was mame 
 
it was only ki1 and ki2 dedicated ; 
with > Apparement ,g tous les fichiers kil faut !!!
pour killer instinct 1 :u10-l1
u11-l1
u12-l1
u13-l1
u33-l1
u34-l1
u35-l1
u36-l1
u98-l14
kinst.chd

to add in the setup.

---

### Post by patrick295767 on 2006-08-02
> **andlinux21 said:**
> Thanks for the help I couldn't get my ROMs to play but after chmod the folder everything works fine now.  I have a USB joystick to configure then its back down memory lane for me...:D

*N64 world : :-) anyhow : *
[http://www.mameworld.net/easyemu/mamechd.htm](http://www.mameworld.net/easyemu/mamechd.htm)
looks nice device

---

### Post by DoktorSeven on 2006-08-02
> **MAXDDARK said:**
> I've installed kxmame BUT when I try to run somthing it's says :
No valid xmame/xmess executables found
even after I find and add the kxmame file in the directories
what can I do ?

You have to find the **xmame** executable, **not the kxmame**.  In mine I have added /usr/games/xmame.SDL and /usr/games/xmame.x11 (make sure you hit Add after browsing for it) in KXmame Directories -> XMame/XMess executables.

---

### Post by MaximB on 2006-08-03
I've installed it from add/remove programs
but I can't find the xmame exevutable anyware 
I found the kxmame....but you said I need the xmame
how can I install it properly ?
were can I find the xmame ?

---

### Post by fireedo on 2006-08-03
it mean you have to point out the right path to your xmame executable....if you installed from ubuntu repo you will got xmame 0.101 and if you use gnome then you should use GXmame then in the Option-->directories--->xmame executables  it should be point to the /usr/games/xmame

after that you have to point out the ROMS path on your harddrive or something

I hope this can help :)

---

### Post by MaximB on 2006-08-03
sorry , I can't find it anywere
could somone pose "how to" ?
I've installed it from the add/remove programs but it doesn't work.
package called : kxmame

---

### Post by DoktorSeven on 2006-08-03
xmame-x - X binaries for the Multiple Arcade Machine Emulator
xmame-sdl - SDL binaries for the Multiple Arcade Machine Emulator

Should be in Multiverse repositories -- if you don't have those packages, search forums for how to enable Multiverse.

Install one (or both) of those, the binaries should be in /usr/games/

---

### Post by dominicguy on 2006-09-04
when I try to play any game, I get "[nameofsomeFile] NOT FOUND".

](*,)

---

### Post by Anonii on 2006-09-04
Thread hijack <:

I get an error when I try to load a game. I go to the game directory (The one with 1000games) and double click one I would like to play. Metal Slug for example. Then I get a window saying that its loading some things, and then, this error:
> 
256-ph1.rom  NOT FOUND
256-ph2.rom  NOT FOUND
sfix.sfx     NOT FOUND
sp-s2.sp1    NOT FOUND
sm1.sm1      NOT FOUND
256-m1.bin   NOT FOUND
000-lo.lo    NOT FOUND
256-v1.bin   NOT FOUND
256-v2.bin   NOT FOUND
256-v3.bin   NOT FOUND
256-v4.bin   NOT FOUND
256-c1.bin   NOT FOUND
256-c2.bin   NOT FOUND
256-c3.bin   NOT FOUND
256-c4.bin   NOT FOUND
256-c5.bin   NOT FOUND
256-c6.bin   NOT FOUND
256-c7.bin   NOT FOUND
256-c8.bin   NOT FOUND

Any ideas  on why I'm getting this?

Thanks.

---

### Post by jetpeach on 2006-09-06
You have to download the roms and put them in one of the directories the frontend is looking in.  It's strange because by default they list all the games but you really can only play the ones you download (rom-world.com has lots).

But perhaps you already did download the rom, because my problem is that I did put the rom I wanted to play in the directory, but it still is missing some files.  Happens in Gxmame and Kxmame for me.  I don't think I need to unzip the files, I read somewhere not too, and it is finding some.

I think I just figured it out, it looks like multiple rom files are sometimes needed for games.

---

### Post by DoktorSeven on 2006-09-06
> **jetpeach said:**
> 
I think I just figured it out, it looks like multiple rom files are sometimes needed for games.

Exactly; for ROMs that play under a multisystem (like the PlayChoice 10 and Neogeo) you need a master ROM for the system itself.  Those should be available (probably under the system name) at the same place you got the original ROMs from.

Also, some games have "alternate" versions (different countries, hacks, variations, etc) that to play the variant, you need a common ROM set for the game itself plus the variant ROM as a separate ZIP file.  Usually the variant will have extra letters appended to the game name (for example Street Fighter II is "sf2.zip", a variant may be "sf2j.zip" for a Japanese version.  If you just want to play the standard one -- probably the US or World version of the game -- you'll just need the standard ROM set).

---

### Post by mocha on 2006-09-07
Excuse me for jumping in here, but I was wondering if anyone has been successful with installing the latest version of xmame from the website.  I grabbed the rpm and converted it with alien.  Then I installed it using dpkg.  It shows up in Synaptic that the version installed is 0.106, but Gxmame isn't recognizing it as a valid executible.  I compared the installations of 0.101 from the repositories with the 0.106 deb version and it seems like I need a file called "xmame.sdl" which is not installed with the 0.106 version.  Does anyone know what's going on here?

---

### Post by joergenlie on 2006-09-07
Hi! I'm really trying to get gxmame working as well. What I really dont get is the ROM stuff, where to get them, where to put it, what ROMs do I need. Is ROM the game? I'm trying to get the c64 Last ninja to work but I've spent some to days trying to fix it](*,) . I'm really keen on this. Last ninja was the best game of the 80's. If someone has got these things to work can they make a detailed howto? That would really save the day.

Thanks

Jørgen

---

### Post by jetpeach on 2006-09-08
> **mocha said:**
> Excuse me for jumping in here, but I was wondering if anyone has been successful with installing the latest version of xmame from the website.  I grabbed the rpm and converted it with alien.  Then I installed it using dpkg.  It shows up in Synaptic that the version installed is 0.106, but Gxmame isn't recognizing it as a valid executible.  I compared the installations of 0.101 from the repositories with the 0.106 deb version and it seems like I need a file called "xmame.sdl" which is not installed with the 0.106 version.  Does anyone know what's going on here?
That's funny, I downloaded that same RPM and was going to install it using Kpackage (i think it just runs alien to convert it) but then i thought - ah converting packages never works right, i won't bother.
So ultimately, on my desktop there is a xmame-0.106-1.fc5.i386.rpm sitting there, but i'm of no use to you sorry.  However, i would say that now that i finally got xmame working right i'm pretty happy with the current version in the repos, i haven't noticed anything wrong.

---

### Post by jetpeach on 2006-09-08
> **joergenlie said:**
> Hi! I'm really trying to get gxmame working as well. What I really dont get is the ROM stuff, where to get them, where to put it, what ROMs do I need. Is ROM the game? I'm trying to get the c64 Last ninja to work but I've spent some to days trying to fix it](*,) . I'm really keen on this. Last ninja was the best game of the 80's. If someone has got these things to work can they make a detailed howto? That would really save the day.

Thanks

Jørgen
Yes, the ROM is the game, xmame is just the game player.  So to get the roms, you can download individuals from many website, [first hit on a google search]("http://www.google.com/search?sourceid=navclient-ff&ie=UTF-8&rls=GGGL,GGGL:2006-30,GGGL:en&q=roms+download") worked for me (rom world).  As stated earlier, some games require a few roms.
Then, after installing xmame and gxmame (or kxmame, they are almost exactly the same just kxmame is for kde) go to the directories configuration (settings->directories) then the second tab (mame basic paths) and add the directory where you are storing the roms by selecting it and in the file menu top right and then clicking add (don't forget to click add, just selecting and seeing it there doesn't add it).  now start g/kxmame and whatever games you have roms for should be playable.

leave roms ZIPPED! no need to unzip them if i have heard right.

it's true, we really need a simple how-to thread to help people set this up, i spent too long dinking around.  other things i had to configure included (in kxmame, i think same in gxmame) settings->configure kxmame and on rendering tab changed to opengl, that gave me full screen ability which didn't work by default for me.  then i had to change the location of the joystick on the controllers tab to /dev/input/js0 to get my gamepad to work, i also installed something called joystick from the repos but i'm not sure if i actually needed to do that.

sorry i don't have time for me detail but hope this helps, if you have time and figure it out please compile a howto for others or add to the ubuntuguide.org wiki maybe, or both

edit: ps for roms, if you search isohunt.com for "mame" there is a _massive_ torrent that is 13GB that contains every mame game known to man, except for 1 apparently (i didn't check which 1 is missing, but 6235 files seemed plenty to keep me busy.)  you can always select just individual files from the torrent to download using ktorrent or azureus as well...

---

### Post by haxer on 2006-09-10
I have installed GXMame Arcade machine Emulator now but when i press file then audit all games i cant find shit what should i do?

---

### Post by DoktorSeven on 2006-09-11
Installing and using XMame:

1.  [Enable extra repositories,](http://www.psychocats.net/ubuntu/sources) ensuring that you add Multiverse.  Make sure you update your local repository list by refreshing in Synaptic, aptitude or using **apt-get update**.

2. Install either (or both) of the packages **xmame-x** or **xmame-sdl**.  xmame-x is preferred since it has an option to use OpenGL rendering for drawing the screens, which will make the games run faster (but will not do 3d rendering on 3d arcade games, unfortunately -- MAME does not do true 3d rendering, instead doing all true 3d rendering in software.  The OpenGL mode will simply draw the arcade screen faster).

3. Get either **kxmame** from the repositories (recommended) or download and install **gxmame** from the Sourceforge page [here](http://sourceforge.net/project/showfiles.php?group_id=50621) -- make sure you get **gxmame_0.35beta2-1_i386.deb**.  Install it with **dpkg** from the directory you saved it to (**dpkg -i gxmame_0.35beta2-1_i386.deb**).

4.  You need some Arcade ROMs.  *Note: since Arcade ROMs are technically copyrighted and illegal to download if you do not have the actual arcade machine, or at least the board with the ROM chips, getting ROMs may get you in trouble.*  Therefore I won't tell you exactly where or how to get them, but I hear that newsgroups are a good place, and there just might be some sites on that Internet that can be found by a certain Googly search engine...

5. Place all of your ROMs in a directory (doesn't matter where, just remember the location), *leaving them zipped* (if you "acquire" the ROMs from somewhere, they should already be zipped up and ready to go).

6. Run gxmame or kxmame.  If it's the first time you've run it, it should need to create a ROM list from xmame.  **This is not the same as finding your zipped ROMs!**  What it's doing is figuring out *all* of the ROMs that your currently installed version of xmame can possibly play.  When it is done, all of the games that xmame supports should be listed when you click "All" on the left side of kxmame/gxmame.

If it tells you that it cannot find an xmame executable, you either did not install xmame itself (see step 2), or it doesn't know where to look for some reason.  Either install xmame if you didn't, or open the **Directories** option from the Settings menu, find the option for "Xmame/Xmess executables:" (I'm reading from kxmame, gxmame should be similar), hit Browse and find your installed version of xmame (both xmame.x11 and xmame.SDL should be in /usr/games/), then when the path appears beside the Browse button, hit the Add button below it -- when you hit Apply/OK it should then do the MAME game search.

7. You now should add the directory where you saved the ROMs from before.  Open the Directories dialog from the Settings menu and go to the "XMame/XMess basic paths" tab (again, I'm going by kxmame; gxmame should be similar).  Beside "ROMS path" hit Browse, and go to the location you saved the ROM ZIP files in.  When you add it, make sure to hit "Add" underneath Browse to add it to the list, below the Browse line.  Hit Apply/OK.

8. *Now* you should be able to hit Refresh (on the toolbar, 4th over on kxmame; gxmame should again be similar).  Note that the option "Rebuild Game List" in Settings is *not* the same as Refresh; this does the master game list build described in (6).  After Refresh is done (it may take a little while to finish), clicking Available on the left side should bring up all of the ROMs you have available to you!

9. Settings->Configure kxmame (or Settings->(I believe) Default Game Settings in gxmame) allows you to set up common options such as graphics settings, enabling joysticks, etc.  After that, just double-click a game name to start play!

10. Final note: some game ROMs depend on other ROMs to play -- localized versions of games may require a "master" version to run, Neo-Geo games require the main NeoGeo system ROM, etc., so if you try to run a game and get a message that ROMs are missing, this is likely the cause.

Hope this helps someone.  Happy MAMEing.

---

### Post by ADroop on 2006-12-02
DoktorSeven... Just wanna tell ye that the 'how-to' ye made worked great. Thanks alot m8 and have a great life.

---

### Post by abbot on 2007-01-14
Having a problem with this.

I've got everything installed (xmame-x, xmame-sdl, gxmame) as well as 1 game for testing (ddonpach.zip) which is located in /usr/share/games/xmame/roms

My executable directory in gxmame is pointing to both /usr/games/xmame.SDL and /usr/games/xmame.x11

When I choose "Rebuild Game List" the progress box comes up for a split second and goes away without the progress bar even moving.  Nothing is displayed in my "All Games" section.  If I choose "Audit All Games" it does actually show my 1 game as "Correct" after a while, but still nothing shows up on my lists that I should be able to choose from.

I can type "xmame -l" in the terminal and the games list comes up fine, but gxmame just doesn't want to see the list for some reason.

Can someone please help?

---

### Post by morphx on 2007-04-24
> **abbot said:**
> Having a problem with this.
When I choose "Rebuild Game List" the progress box comes up for a split second and goes away without the progress bar even moving.  Nothing is displayed in my "All Games" section.  If I choose "Audit All Games" it does actually show my 1 game as "Correct" after a while, but still nothing shows up on my lists that I should be able to choose from.

I can type "xmame -l" in the terminal and the games list comes up fine, but gxmame just doesn't want to see the list for some reason.

Can someone please help?

I have this exact same problem. Does anyone knows how to fix this or what causes this problem?
I'm running Ubuntu 7.04 with GXMame 0.34b

---

### Post by DoktorSeven on 2007-04-24
gxmame might be your problem; it's rather old.  Try using kxmame instead.

---

### Post by morphx on 2007-04-30
Thanks for the info.
I don't like KXMame... at all...

Isn't there a native-gnome type of mame front end?

---

### Post by H.E. Pennypacker on 2007-06-21
> **TasKiNG said:**
> right, installing xmame is quite easy when you know how :)
this is how i installed it under dapper drake

edit your /etc/apt/sources.list file and make sure you have these two lines ( note if not using dapper then replace with what you are using) :-

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper multiverse

now type:    sudo apt-get update

then:        sudo apt-get install xmame-common

now click on the link below to download the GXmame .deb file:  
[http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb](http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb)

in a terminal window in the same directory that you stored the above .deb file type:   sudo dpkg -i gxmame_0.35beta2-1_i386.deb

Thats xmame and a good frontend installed. you might want to remove those two lines now that you added to your sources.list file.

your roms files now need to go into the /usr/share/games/xmame/roms directory. ( i did a sudo chmod -R 777 /usr/share/games/xmame first ).

you will now find a shortcut to GXmame in your start menu under games.

run it and select "rebuild game list" then "file/audit all games"
when done click on "available" and you should see the roms that you are using.

Hope this helps

Cheers

TasKiNG

Thanks...this worked great for my Feisty install.

---

### Post by Zyppora on 2007-06-30
All,

Thanks for the URLs (in the TS) and the how-to on this page, everything worked fine for me except for the loading of games.

I have everything set up the way it was described here, gxmame seems to run fine, etc. Now I have a game in my /roms dir (Garou.zip), which -should- enable me to play the game Garou: Mark of the Wolves (set 1). In fact, I've gotten it to work on an XP system not too long ago.

In the Mame games list, it keeps displaying a little X, indicating that the game's not available (it doesn't show up in the Available list either, so consistency galore). I KNOW for a fact that I have my paths set up correctly (even added my homedir (where I initially downloaded the zipfile) and the /roms dir without a trailing slash to make sure that wasn't the problem).

What the game does is load until approx. 76%, and then comes up with the following:
> 
LIRC disabled
253-sma.bin  NOT FOUND
253-ep1.p1   NOT FOUND
253-ep2.p2   NOT FOUND
[etc]


There's about fifteen to twenty items indicated as NOT FOUND.

Now, I'm a beginner when it comes to Linux and am not quite sure what the cause could be of this (or how to distill any useful information from the error dialog I'm getting), so if anyone could help me out on this one, I'd be very grateful.

On a sidenote: I used to have the same error on my XP system but I can't remember what I did, if anything, to solve it there :/

---

### Post by jetpeach on 2008-12-03
do other roms work? is it finding any of the roms? you could try using a directory in your home directory, or run mame as root just to be sure its not some permission error...

i'm not sure why your version of KI is so big, mine is quite small (5 mbs). hmm, well i just tried mine and it doesn't work on linux or windows (but my other roms do on both). it says its missing parts of the rom, so maybe that's why mine is smaller...

---

### Post by JdawgZX11d on 2008-12-05
After Harikore chewed me out for a double post and closed a thread on me, I found this out.

You leave the roms zipped up. Then the .chd file(92mb) gets put in its own directory. Now, I got the games to work, but a new problem arose. On KI 1, when I start my character selection, all the characters bodies are 'blank' and within seconds of the match starting, it locks up. KI2 works perfectly though.. Now I just need to get an arcade stick and I am 16 all over again..

---

### Post by hikaricore on 2008-12-05
I believe I told you to stop discussing roms here.

There are plenty of sites out there to do this on and again this is not one of them.

---

### Post by frenchn00b on 2008-12-22
this can be used with sdlmame, apparently:
[http://ubuntuforums.org/showthread.php?t=342543&highlight=howto+mame](http://ubuntuforums.org/showthread.php?t=342543&highlight=howto+mame)

```
cd ; sdlmame mame/roms/mk.zip -fullscreen -ef 1 -jt 5 -jdev /dev/input/js0
```

---

