---
title: "Unreal Tournament"
date: 2010-10-15
forum: Gaming &amp; Leisure
---

### Post by bumder on 2010-10-15
hi,

i was looking for a decent, light game to put on my lucid netbook, and was looking at either quake 3 or UT GOTY.

has anyone installed this on ubuntu before, or know how i can get the linux version?

---

### Post by The Cog on 2010-10-15
I have wasted far to many hours of my life playing UT GOTY edition on Ubuntu. Works perfectly, on every version up until 10.10 where they broke the sound. It's many years since I installed it and I can't remember how for sure. I think the installer is on the CD. 

Doom3 also works on all recent Ubuntu versions except 10.10 where again, they broke the sound. Gave me nightmares the first time, literally. I haven't tried any other games so can't say.

I'll move this thread to the gaming forum.

---

### Post by Fire_Chief on 2010-10-15
If you're familiar with Quake 3 then I bet you'd get hours of enjoyment from [OpenArena]("http://www.openarena.ws"). Best of all, it's available in the repos! :D

---

### Post by Scott Swinyard on 2010-10-16
You can use the original game installer disk(s) for goty and then go here to pick up a Linux installer: 

[http://liflg.org/?catid=6&gameid=51](http://liflg.org/?catid=6&gameid=51)

---

### Post by alexandrius on 2010-10-16
has anybody fixed sound for unreal 2004 in 10.10?

---

### Post by bumder on 2010-10-16
okay, i'm a little confused :s

do i use the pc version under wine, or can i run it natively?

not sure if there is a dedication linux version like there is a mac version.

also, i'm on a netbook, so will have to make an iso due to lack of optical drivage...

---

### Post by Rustybolts on 2010-10-16
My version of Unreal Tournament contained the linux installer on the dvd. If not there is a linux installer available here:
[http://liflg.org/?catid=6&gameid=17](http://liflg.org/?catid=6&gameid=17)
which can be used with win cd.

---

### Post by bumder on 2010-10-16
that ut2004 i think.

i'm looking for the original GOTY version, the one without the silly vehicles in it.


i think i might just bung a snes emulator on my netbook instead, a lot easier :D

is snes9x still the best emulator on linux?

cheers

---

### Post by Zteam on 2010-10-16
try out Nexuiz it's a very nice FPS with stunning graphics and plenty of maps online servers too. :P

---

### Post by Rustybolts on 2010-10-16
same website
[http://liflg.org/?catid=6&gameid=51](http://liflg.org/?catid=6&gameid=51)

---

### Post by bumder on 2010-10-17
> try out Nexuiz it's a very nice FPS with stunning graphics and plenty of maps online servers too.

does this have offline bots, as i will primarily be without der tinternet :(

---

### Post by Sylos on 2010-10-17
Hi there.
OP - just throw another couple of pennies in:
I have UT GOTY and UT2003 running natively on ubuntu 9.10 with no issues (did take me a while to sort it but I got there in the end).

If you run in to issues then post as I may well have had similar experience.

Happy fraggin.

PS: Nexuiz is pretty awesome but really eats resources if you want decent graphics - if your looking for light weight games then that might not be the best.

---

### Post by flying sheep on 2010-10-17
does someone still have a problem with the sound in ut2004? here what i did (the sound was the last error):

[LIST][*]error: ut2004 wants libstdc++5
solution:```
# add-apt-repository ppa:jason-scheunemann/ppa
# apt-get update
# apt-get install libstdc++5
```

[*]error: ut2004 crashes sometimes
solution: patch (ut2004-lnxpatch3369-2.tar.bz2) installed (this prevented ut2004 from starting, but also fixed the crash: read on)

[*]error: shared library libsdl-1.2.so.0 shipped with the game/patch isn’t 64-bit
solution:```
# cd /opt/ut2004/System
# rm libsdl-1.2.so.0
# ln -s /usr/lib/libsdl-1.2.so.0 libsdl-1.2.so.0
```

[*]error: sound doesn’t work
solution: ```
# cd /opt/ut2004/System
# rm openal.so
# ln -s /usr/lib/libopenal.so.1 openal.so
```
[/LIST]

---

### Post by bumder on 2010-10-27
Might see if I can pick up Unreal Tournament GOTY PC version used on ebay, then use the Loki installer.
 
Had a look at Nexuiz and Warsow, but as I will be primarily offline, I don't think they will be as good single player.
 
As a side note, just started playing mahjongg (the one included on install), can anyone recommend any other basic board games that are worth getting?
 
I may try Chinese Chess if I have the time!
 
Cheers
 
:KS

---

### Post by Sylos on 2010-10-27
> **bumder said:**
> Might see if I can pick up Unreal Tournament GOTY PC version used on ebay, then use the Loki installer.
 
:KS


From memory the last I time installed this the Loki installer didnt work first off - something to do with POSIX version I think - so it may need some fettling. I think there are guides available on how to do it so try some googling. If you cant find anything then I can have a rumage in my archive and see how I did it.

Good luck

---

### Post by bumder on 2010-10-29
Finally got it, installed it, and got it running correctly under 10.04!

Here is what I did:

Acquired a disc image, and mounted onto desktop, then used 'export SETUP_CDROM=/path/to/cdrom' in terminal to point to this.

Extracted all the iso's game files to a folder named UT, and navigated to it in terminal.

Used the Loki installer (needed first to install [http://packages.ubuntu.com/en/jaunty/libgtk1.2-common](http://packages.ubuntu.com/en/jaunty/libgtk1.2-common)
[http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl)
[http://packages.ubuntu.com/en/jaunty/libgtk1.2](http://packages.ubuntu.com/en/jaunty/libgtk1.2))

Run the game using shell script in the newly installed game folder.

Noticed the game was uber fast, and had no sound, so went to [http://www.fingel.com/ut/howtos/utonlinux.html](http://www.fingel.com/ut/howtos/utonlinux.html), and installed the custom script launcher, which fixed both sound and speed issues.

Hope this helps someone else in future!

---

### Post by R33D3M33R on 2010-10-29
[https://help.ubuntu.com/community/Games/Native/UnrealTournament](https://help.ubuntu.com/community/Games/Native/UnrealTournament)

---

### Post by bumder on 2010-10-29
Just out of interest, how would one uninstall a game like this? Is it just a case of deleting the directory?

---

### Post by Omnomnom on 2010-10-29
May I suggest OpenArena? It's pretty good :)

---

### Post by R33D3M33R on 2010-10-29
bumder: there is an unistall script in your UT directory.

---

### Post by bumder on 2010-10-29
yep, just looked and found the uninstall script.

Cheers R33D3M33R (the redeemer is the ultimate weapon in UT too!)

Gonna close this thread as 'solved' now :)

---

### Post by R33D3M33R on 2010-10-30
Glad to help you.

And btw. my nickname is derived from that weapon, because I'm also a big Unreal/UT series fan :).

Happy fragging! :)

---

### Post by bumder on 2010-11-02
just out of interest, i intalled the bonus packs too using the loki installer.

would the uninstall script in the UT directory delete these as well?

---

### Post by MyKal on 2011-08-27
I am sorry to necro such an old thread but i though it should be noted that newer versions of ubuntu have rendered this thread un-solved since the libgtk packages needed for the loki installer to work are no longer (as far as i can tell) available at any of the links listed above 

does anybody have any idea how to get this game running now?

---

### Post by schneil on 2011-09-26
I found how to get the missing files on this page:
[http://www.margrave.myzen.co.uk/InstallUTonLinux.html](http://www.margrave.myzen.co.uk/InstallUTonLinux.html)

It has links to the missing files, then unreal tournament will install :)

[http://launchpadlibrarian.net/10754135/libglib1.2ldbl_1.2.10-19build1_i386.deb](http://launchpadlibrarian.net/10754135/libglib1.2ldbl_1.2.10-19build1_i386.deb)

[https://launchpad.net/ubuntu/+source/gtk+1.2/1.2.10-18.1build2/+build/484191/+files/libgtk1.2-common_1.2.10-18.1build2_all.deb](https://launchpad.net/ubuntu/+source/gtk+1.2/1.2.10-18.1build2/+build/484191/+files/libgtk1.2-common_1.2.10-18.1build2_all.deb)

[https://launchpad.net/ubuntu/+source/gtk+1.2/1.2.10-18.1build2/+build/484191/+files/libgtk1.2_1.2.10-18.1build2_i386.deb](https://launchpad.net/ubuntu/+source/gtk+1.2/1.2.10-18.1build2/+build/484191/+files/libgtk1.2_1.2.10-18.1build2_i386.deb)

Then do a sudo sh  unreal_installer_whatever

To get sound you have to edit the entry in your menu and put padsp in there.
Also edit unreal.ini and change AudioDevice=ALAudio.ALAudioSubsystem line to  AudioDevice=Audio.GenericAudioSubsystem 

To get the game to save settings change permissions of the .loki folder in your home directory so you can read and write files.

Enjoy :)

---

### Post by schneil on 2011-09-26
To play on a 64 bit system you'll need the amd 64 packages

[https://launchpadlibrarian.net/10815906/libglib1.2ldbl_1.2.10-19build1_amd64.deb](https://launchpadlibrarian.net/10815906/libglib1.2ldbl_1.2.10-19build1_amd64.deb)

[https://launchpadlibrarian.net/11167856/libgtk1.2_1.2.10-18.1build2_amd64.deb](https://launchpadlibrarian.net/11167856/libgtk1.2_1.2.10-18.1build2_amd64.deb)

enjoy :)

---

### Post by schneil on 2011-09-27
Now then all the above worked great on my old box (a pentium D)

On my newer box a core2quad I get the game speeding up and slowing down all the time.  Gah!!

I've tried disabling speedstep and also having the game run on one processor.  Not worked 100%  Anyone got any ideas?

---

