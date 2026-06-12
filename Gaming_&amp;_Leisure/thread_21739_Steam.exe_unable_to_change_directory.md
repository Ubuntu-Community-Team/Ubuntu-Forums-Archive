---
title: "Steam.exe unable to change directory"
date: 2005-03-23
forum: Gaming &amp; Leisure
---

### Post by Dracontopes on 2005-03-23
I installed Cedega fine (at least I think so, it was a .deb package) and installed Steam. But when I close Steam and try to reopen it (conclusion: Steam runs when installing etc, but afterwards no luck starting Steam again), it gives me this error:

Steam.exe (main exception): Unable to change directory to /home/chris/steam/

Uhh, WTF? :mad:

---

### Post by Beire on 2005-03-24
[QUOTE=Dracontopes]I installed Cedega fine (at least I think so, it was a .deb package) and installed Steam. But when I close Steam and try to reopen it (conclusion: Steam runs when installing etc, but afterwards no luck starting Steam again), it gives me this error:

Steam.exe (main exception): Unable to change directory to /home/chris/steam/

Uhh, WTF? :mad:[/QUOTE]
 does'nt start here anymore too. only i get these errors :

```
beire@beire:~/.cvscedega $ cvscedega c_drive/Program\ Files/Valve/Steam/STEAM.exe
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:keyboard:X11DRV_KEYBOARD_DetectLayout Your keyboard layout was not found!
Using closest match instead (French keyboard layout) for scancode mapping.
Please define your layout in windows/x11drv/keyboard.c and submit them
to us for inclusion into future Wine releases.
See the Wine User Guide, chapter "Keyboard" for more information.
err:task:GetThreadQueue16 Breaking 16 bit for tid 12
err:task:GetThreadQueue16 Breaking 16 bit for tid 12
err:win:WIN_FindWndPtr window 6002e belongs to other process
fixme:win32:DEVICE_Open Unknown/unsupported VxD GDPERF. Try --winver nt40 or win31 !
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
fixme:ole:CoCreateInstance no classfactory created for CLSID {8856f961-340a-11d0-a96b-00c04fd705a2}, hres is 0x80040154
fixme:ntdll:NtQueryInformationProcess (0xffffffff,0x00000000,0xb7a2e9dc,0x00000018,(nil)),stub!
/usr/local/bin/cvscedega: line 87: 11339 Segmentation fault      "$ConfigurePrefix/bin/$WineExecName" "$@"


```

---

### Post by nahkapaavali on 2005-03-24
Just a quickie here: how did you install steam with cvscedega? 

I´ve tried to search some howtos but didnt find anything useful.

Thanks!

---

### Post by Dracontopes on 2005-03-24
[QUOTE=nahkapaavali]Just a quickie here: how did you install steam with cvscedega? 

I´ve tried to search some howtos but didnt find anything useful.

Thanks![/QUOTE]
 I just downloaded a .deb file @ some site google found... So I don't use cvscedega. It's not totally legal but I haven't found a way to install cvscedega...

I installed Steam by running: cedega SteamInstall.exe

And it's gogogo from there :P

---

### Post by telmo on 2005-03-24
[QUOTE=Dracontopes]I installed Cedega fine (at least I think so, it was a .deb package) and installed Steam. But when I close Steam and try to reopen it (conclusion: Steam runs when installing etc, but afterwards no luck starting Steam again), it gives me this error:

Steam.exe (main exception): Unable to change directory to /home/chris/steam/

Uhh, WTF? :mad:[/QUOTE]


I have the same exact problem... and I WANT TO PLAY IT!!!

---

### Post by Dracontopes on 2005-03-26
I tried CedegaCVS, but that doesn't work either... :(

Anyone help plz? :) Running cedega...

---

### Post by NateC on 2005-04-09
I am having this exact same problem, wtf!

---

### Post by Dracontopes on 2005-04-10
I found some sort of workaround: change to the directory (from terminal) where the steam.exe file is located and then do: ```
cedega STEAM.exe
```

Now I *can* start Steam and play some Counter-Strike: Source, but the performance is like totally crap and the sounds are not high quality...

---

### Post by Perfect Storm on 2005-04-10
Steam is version 4.2, there's a newer one 4.3 it works perfect.

---

### Post by NateC on 2005-04-10
I am using 4.3


Edit: Dude! Your work-a-round worked like a charm... thanks a lot man!

---

### Post by fackamato on 2005-04-10
[QUOTE=Dracontopes]I found some sort of workaround: change to the directory (from terminal) where the steam.exe file is located and then do: ```
cedega STEAM.exe
```

Now I *can* start Steam and play some Counter-Strike: Source, but the performance is like totally crap and the sounds are not high quality...[/QUOTE]

Huh? Workaround? In what way is this a workaround? How would you otherwise start steam if not go into the dir and execute cedega?!

---

### Post by Dracontopes on 2005-04-10
Heheh it's not really a work-a-round, just a trick to make it work.

---

### Post by fackamato on 2005-04-10
[QUOTE=Dracontopes]Heheh it's not really a work-a-round, just a trick to make it work.[/QUOTE]

I don't get it. Is there another way to start steam than to enter its dir, and cedega steam.exe ?

---

### Post by keyshawn on 2005-04-13
[QUOTE=fackamato]I don't get it. Is there another way to start steam than to enter its dir, and cedega steam.exe ?[/QUOTE]

well, you can make a script for it [which is a temporary solution]
[store the script in your home folder]

For more detailed info about a script - [http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)


Below is a script I made for folding@home

 ```

#!/bin/bash

#made by keyshawn, i'm lazy to type in this script everytime.

cd src
./FAH502-Linux.exe 

``` 

just edit it in your favorite text editor and save [no extension]. then just go to the terminal and type in:
./name_of_script

cuts down the work a bit :smile:

---

### Post by fackamato on 2005-04-13
yeah of course
but what I mean is, why didn't it work for the others in this thread, and why did it suddenly start to work then they just did "cd gamedir, cedega game.exe" ? I mean, that's the only way you'd start a game. I wonder how they tried to run it otherwise!  :lol:

---

### Post by mglukhovsky on 2005-04-14
The other method that could be used is Point2Play, where one simply runs the Windows installation from within Point2Play, and icons are automatically created. One simply selects the game withing Point2Play or uses the icon and the game is launched. One advantage of Point2Play is the centrality of all the games; another is that it allows one to simply change Cedega settings for a game-by-game basis.

---

### Post by Dracontopes on 2005-04-15
[QUOTE=fackamato]yeah of course
but what I mean is, why didn't it work for the others in this thread, and why did it suddenly start to work then they just did "cd gamedir, cedega game.exe" ? I mean, that's the only way you'd start a game. I wonder how they tried to run it otherwise! :lol:[/QUOTE]

I tried to start Steam from a terminal: cedega /long/path/into/my/home/folder/for/steam/directory/STEAM.exe

But that don't work :) But manually entering the dir and start STEAM from there does work.

---

### Post by sinbad782 on 2005-04-16
Hmm,
   This sound a little like what I experienced recently when reinstalling win xp with steam on a separate SATA drive. The drive letters all changed due to a new partitioning scheme I had configured. Once everything was back in place and I reinstalled, I couldn't install/update any of the games. I had to go into the Steam directory and delete the client registry file (called something like clientregistry.blob). After I did this and restarted steam, it took a few seconds to rebuild the registry, but after that everything worked fine. 

It's worth a try, as the worst that can happen is that the steam client has to build itself a new registry file (clientregistry.blob). 

PJS

---

### Post by Alysander on 2006-09-24
I had this problem initally too,

Change the "path to program" to the windows version of the path like this:
C:/Program Files/Valve/Steam/Steam.exe
rather than using the linux path which steam doesn't understand.

Look at the other shortcuts in Cedega that are already installed too.

Hope this helps

---

