---
title: "Sound Issues With Games?  Read This."
date: 2005-06-17
forum: Gaming &amp; Leisure
---

### Post by jdodson on 2005-06-17
MANY people on the forums here have had sound issues with games.  This thread is an attempt to solve them.  I will outline my problems and then the solutions I have found.  I will note the source when appropriate, as I did not come up with these ideas.

I know Breezy plans to "fix" most of these sound issues, however Hoary is here and now, and we need a fix for some games.

Problem: Quake3 and Enemy Territory have no sound.  In other words, I can't hear when I am getting fragged or when I am fragging, major problem.

There are a number of working solutions that people have mentioned on the forum.  Some have noted the "esd" process is getting in the way.  A simple "ps -aux | grep esd" and a "kill <proc>" to the offending "esd" process have cleared that up for some, as in they can hear things, however for me, and many other people, this did not solve the issue.

other people could run this command with positive results:

```
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
``` 

Thats well and good, if your hardware supports what you are trying to do.  When I rand that command on Quake3 the game would hard lock seconds into the arena.  It simply would not work for Enemy Territory.  Ok, so good for some, hard locks for others, there _HAS_ to be a better way.

After much digging I came across the _BEST_ solution I could find to date.  This fix has solved _ALL_ of my sound problems(I did not have sound issues with some games).  

I will quote from: [http://www.accidentalegg.co.uk/random_problems.php](http://www.accidentalegg.co.uk/random_problems.php)


[B]So anyway, cut to the chase...

   1. Make sure you've got aRts(I did by default in Ubuntu) installed. You'll soon know if you haven't.
   2. Change your quake3 startup script (/usr/local/games/quake3 for me). Where it reads "./quake3.x86 $*" change it to to "artsdsp -m ./quake3.x86 $*"
   3. Run 'artsd -F 6 -S 256', and keep it running...
   4. Start Quake 3!

All this does is run the Quake 3 binary inside artsdsp which captures all it's sound device accesses and re-routes them through aRts. The '-m' tells artsdsp to emulate mmap-ing, which Quake 3 does.[/B]

So basically what you are doing is forcing Quake 3, or Enemy Territory(works in the same way) to use the artsd sound daemon for sound.  I ran Quake3 from start to finish(single player mode) with no hard locks, freezes or any sound issues.  

Good luck, and good gaming!

---

### Post by DarkKnight on 2005-06-29
Is there any way to fix the terrible lag the sound has? 

I tried it just now, it fixed all my problems, but I have to wait an extra second to hear a bullet... lol

Also, is there anyway to automate this into a script so I don't have to open a console everytime I want to play?
(Just for ease of use, nothing else.)

---

### Post by jdodson on 2005-06-29
[QUOTE=DarkKnight]Is there any way to fix the terrible lag the sound has? 

I tried it just now, it fixed all my problems, but I have to wait an extra second to hear a bullet... lol

Also, is there anyway to automate this into a script so I don't have to open a console everytime I want to play?
(Just for ease of use, nothing else.)[/QUOTE]

check the site i refrenced for lag issues, they might have a possible fix.

try killing esd while you run the game, perhaps they are messing with each other(i seriously doubt it, but it is possible).

---

### Post by DarkKnight on 2005-06-29
[QUOTE=jdodson]check the site i refrenced for lag issues, they might have a possible fix.

try killing esd while you run the game, perhaps they are messing with each other(i seriously doubt it, but it is possible).[/QUOTE]
 Nothing there... 

I've tried to use the 'old' method, but I get this: 
bash: /proc/asound/card0/pcm0p/oss: Permission denied

When I use sudo, It still says permission denied, but never asks for the pass...

EDIT: It's also not ESD, when I kill it, it still lags. 
I use ALSA too.

---

### Post by emperor on 2005-07-02
<Using default sound settings NOT the sound changes in the Hoary wiki>

What finally fixed the sound in games for me was installing a different sdl library. I **removed** the default ***"libsdl1.2debian-oss"*** and **installed** ***"libsdl1.2debian-all**"*. Now sound works in all the games I have installed.

---

### Post by WorLord on 2005-07-14
> After much digging I came across the _BEST_ solution I could find to date. 

I know this probably comes pretty late, but I believe I've found a better solution!

**Step 1:** Follow the sound section of the UbuntuGuide (at [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly) ) exactly.
**Step 2:** Make sure you have universe repositories installed, and then do a ```
sudo apt-get install polypaudio polypaudio-alsa
```
(Polypaudio is at 0.7 now, and is in every way that I can tell ESD's superior at the present time.)  This will uninsall esound and (possibly) the ubuntu-desktop packages, if that matters to anyone.
**Step 3:** Launch Quake3.  Polyp has MMAP-oss plugins that pretty much automagically handle things, and with no lag whatsoever.  

So far, this has not only fixed the problem on two machines I've used, but it has preserved sound functionality in everything esle I throw at it, also.  XMMS, BMP, Rhythmbox, Flash in Firefox, Q3 - all work without having to kill sound servers, change configs, or alter the Q3 launch script.  

(Note: Both of the machines I've tested this on would freeze with the "direct > /proc/asound/card0/pcm0p/oss" solution, and had *horrible* lag with aRts and unplayability with esddsp.  Both machines were using the ac'97 and intel8x0 modules.)

---

### Post by emperor on 2005-07-14
[QUOTE=WorLord]I know this probably comes pretty late, but I believe I've found a better solution!

**Step 1:** Follow [this guide]("http://http://www.ubuntuguide.org/#configuresoundproperly")  exactly.

[/QUOTE]

Your "this guide" link points to: [http://www.microsoft.com/](http://www.microsoft.com/)

???

---

### Post by huru on 2005-07-15
One problem I had was that my USB mic grabbed ALSA card index 0. I had configured card 1 (which was the real sound card) to be used as default in asound.conf and programs like Totem, Beep Media Player etc were happily playing sounds but games would not. Linux native games worked all right but without sounds, while running games with cedega didn't work at all. When I realised the reason for this I added following line to /etc/modprobe.d/alsa-base:

```
options snd-usb-audio index=-2
``` 

Now the indexes go as they should and my sound card gets index 0, everything works as expected. Hope this helps someone who might have same problem :)

---

### Post by WorLord on 2005-07-15
[QUOTE=emperor]Your "this guide" link points to: [http://www.microsoft.com/](http://www.microsoft.com/)

???[/QUOTE]

I honestly have no idea what you're talking about.  I'm even mousing over your quote of me (which shows what is linked to), and while it DOES show a mistaken link (two sets of "http://"'s), it does not show anything having to do with Microsoft.  

Unless you're using IE, which redirects people to MS (usually) in the event that the browser doesn't understand the link in question.

At any rate, I've fixed my own error.

---

### Post by emperor on 2005-07-15
The original "this guide" link with the double "http://" still goes to the microsoft site. I am using Firefox version 1.0.4 on Hoary. Very weird but true non-the-less!

justing typing "http" as the URI brings up microsofts site.

---

### Post by seekingmysoul on 2005-07-16
I just installed ubuntu and when I click on your "guide" I also go to Microsofts website.   Can you type the full address instead of giving a link.   Thanks

---

### Post by rutty on 2005-07-18
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

---

### Post by gyaresu on 2005-07-24
Well I've done "everything" suggested to fix sound under Enemy Territory both here and from the interweb.
From installing polypaudio && libesd-alsa0
I've edited my asound.conf
I've had all programmes working fine under esd or alsa but I *could_not* get 'ET' working...

The solution:
[http://www.accidentalegg.co.uk/random_problems.php](http://www.accidentalegg.co.uk/random_problems.php)

edit your /usr/local/games/enemy-territory/et script and tell et.x86 binary to use the aRts sound daemon.

```

$ sudo apt-get install gstreamer0.8-artsd
$ cd /usr/local/games/enemy-territory/
$ sudo cp /usr/local/games/enemy-territory/et usr/local/games/enemy-territory/et.bak   
$ cat et.bak
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./et.x86 "$@"
$ sudo gedit et
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
# inserted "artsdsp -m" here
exec artsdsp -m ./et.x86 "$@"
$ artsd -F 6 -S 256
...(let it run >> open up another terminal)

$ et



```

---

### Post by dbeckham32 on 2005-07-24
WorLord,

I tried your suggestions and it worked perfectly. I can hear Enemy Territory great, plus my music player was not adversely affected. You rock.

Thanks.

---

### Post by arcanistherogue on 2005-07-25
I'm having trouble with this, and I'm on Kubuntu.  I had a bit of trouble doing the said methods due to the fact they pertained to GNOME, and the libsdl1.2debian-all one didnt work.  

At first the sound lagged, then when i went back to the default there was no sound at all.  not in games at least.

any help with this?

---

### Post by jkndrkn on 2005-08-06
[QUOTE=WorLord]**Step 2:** Make sure you have universe repositories installed, and then do a ```
sudo apt-get install polypaudio polypaudio-alsa
```[/QUOTE]

Sweet Jiving Jesus.
The solution I've been looking for.
Now all my games have sound.

---

### Post by Kanbeki on 2005-08-07
I've tried all of these suggestions, aRTS lags really bad and polypaudi gives me this ```
module.c: Failed to open module "module-x11-bell": module-x11-bell.so: cannot open shared object file: No such file or directory
``` and never seems to work or detect anything that outputs sound..help for a noob?

---

### Post by gyaresu on 2005-08-07
[QUOTE=Kanbeki]I've tried all of these suggestions, aRTS lags really bad and polypaudi gives me this ```
module.c: Failed to open module "module-x11-bell": module-x11-bell.so: cannot open shared object file: No such file or directory
``` and never seems to work or detect anything that outputs sound..help for a noob?[/QUOTE]


Try asking for help in the #ubuntu channel on irc.freenode.net 
Lots of helpfull folk there.

---

### Post by TKe on 2005-08-28
[QUOTE=gyaresu]Well I've done "everything" suggested to fix sound under Enemy Territory both here and from the interweb.
From installing polypaudio && libesd-alsa0
I've edited my asound.conf
I've had all programmes working fine under esd or alsa but I *could_not* get 'ET' working...

The solution:
[http://www.accidentalegg.co.uk/random_problems.php](http://www.accidentalegg.co.uk/random_problems.php)

edit your /usr/local/games/enemy-territory/et script and tell et.x86 binary to use the aRts sound daemon.

```

$ sudo apt-get install gstreamer0.8-artsd
$ cd /usr/local/games/enemy-territory/
$ sudo cp /usr/local/games/enemy-territory/et usr/local/games/enemy-territory/et.bak   
$ cat et.bak
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./et.x86 "$@"
$ sudo gedit et
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
# inserted "artsdsp -m" here
exec artsdsp -m ./et.x86 "$@"
$ artsd -F 6 -S 256
...(let it run >> open up another terminal)

$ et



```[/QUOTE]

This works for me, thnx. I also tested all other methods mentioned on this topic and also some other instructions mentioned elsewhere on this forum  ](*,) . Huh, I hope the next release from Ubuntu will make this much easier... There should be easier way to do this...

---

### Post by kmail on 2005-09-01
so i installed this polypaudio thing, how am i supposed to use it? When i run the command it gives me this: 
```
mkisand@ubuntu:~$ polypaudio source.c: created 0 "null_monitor" with sample spec "S16LE 2ch 44100Hz" sink.c: created 0 "null" with sample spec "S16LE 2ch 44100Hz" module.c: Loaded "module-null-sink" (index: #0; argument: ""). module.c: Loaded "module-esound-protocol-unix" (index: #1; argument: ""). protocol-native.c: loading cookie from disk. module.c: Loaded "module-native-protocol-unix" (index: #2; argument: ""). client.c: created 0 "STDIN/STDOUT client" module.c: Loaded "module-cli" (index: #3; argument: ""). module.c: Loaded "module-x11-bell" (index: #4; argument: "sample=x11-bell sink=output"). module-x11-publish.c: using already loaded auth cookie. module.c: Loaded "module-x11-publish" (index: #5; argument: ""). main.c: Daemon startup complete. Welcome to polypaudio! Use "help" for usage information. >>> 
``` 
and that help gives me info about some creepy commands, but i get no sound whatsoever in enemy territory and quake, it still says cannot mmap device.
when i do echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
enemy territory works bat using that on quake, gives me sound, but quake just crashes randomly, with sound enabled, it always crashes.
What do i do now?

---

### Post by TheIdiotThatIsMe on 2005-09-20
[QUOTE=WorLord]I know this probably comes pretty late, but I believe I've found a better solution!

**Step 1:** Follow the sound section of the UbuntuGuide (at [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly) ) exactly.
**Step 2:** Make sure you have universe repositories installed, and then do a ```
sudo apt-get install polypaudio polypaudio-alsa
```
(Polypaudio is at 0.7 now, and is in every way that I can tell ESD's superior at the present time.)  This will uninsall esound and (possibly) the ubuntu-desktop packages, if that matters to anyone.
**Step 3:** Launch Quake3.  Polyp has MMAP-oss plugins that pretty much automagically handle things, and with no lag whatsoever.  

So far, this has not only fixed the problem on two machines I've used, but it has preserved sound functionality in everything esle I throw at it, also.  XMMS, BMP, Rhythmbox, Flash in Firefox, Q3 - all work without having to kill sound servers, change configs, or alter the Q3 launch script.  

(Note: Both of the machines I've tested this on would freeze with the "direct > /proc/asound/card0/pcm0p/oss" solution, and had *horrible* lag with aRts and unplayability with esddsp.  Both machines were using the ac'97 and intel8x0 modules.)[/QUOTE]

-nvm-

---

### Post by bob_c_b on 2005-09-20
I tired almost every suggestion in this thread with my onboard sound (AD1881 onboard a Gigabyte 848P chipset mobo), none of them worked and at one point my sound was borked in just about every application in every way you could imagine (out of synch, static, no sound at all, etc...). On a whim I found a guy selling brand new SoundBlaster Live 5.1 cards on eBay for $23, did a clean install of 5.04 and now sound works in everything. I set ALSA as my primary mixer but haven't really tweaked anything else, good quality sounds in Quake III, UT2K4, Uplink, media, etc...

I know it's not a free solution, but it was well worth the $23 for the time and hassle I saved.

---

### Post by gyaresu on 2005-09-20
> On a whim I found a guy selling brand new SoundBlaster Live 5.1 cards on eBay for $23 

Great to hear.
If one doesn't use a 5.1 speaker setup then it's a bit of overkill.
The secret to buying soundcards that work with linux is to look for a gameport on the card.
If it has a gameport then it has a chip (as opposed to being a 'winsound' card), if it has a chip then there will be modules.
Generic C-Media-chiped cards for AU$5 are the win!

---

### Post by bob_c_b on 2005-09-20
[QUOTE=gyaresu]Great to hear.
If one doesn't use a 5.1 speaker setup then it's a bit of overkill.
The secret to buying soundcards that work with linux is to look for a gameport on the card.
If it has a gameport then it has a chip (as opposed to being a 'winsound' card), if it has a chip then there will be modules.
Generic C-Media-chiped cards for AU$5 are the win![/QUOTE]

Very true, a card with an actual chip is key, but even many add in boards are host based now. That is a good deal on that Cmedia card, and I am sure there are other bargains to be had, I never personally had much luck with CMedia cards.  I specifically went after a card that was documented as well supported on the ALSA site more than any other criteria. And while yes, technically it is overkill, it is a very adequate card for my 2.1 speakers and headphones.

---

### Post by alsimoes on 2005-09-24
I am trying this:

[QUOTE=jdodson]...
[B]So anyway, cut to the chase...

   1. Make sure you've got aRts(I did by default in Ubuntu) installed. You'll soon know if you haven't.
   2. Change your quake3 startup script (/usr/local/games/quake3 for me). Where it reads "./quake3.x86 $*" change it to to "artsdsp -m ./quake3.x86 $*"
   3. Run 'artsd -F 6 -S 256', and keep it running...
   4. Start Quake 3!
...[/QUOTE]

...but I get this:

```
andre@ubuntu:~$ artsd -F 6 -S 256
unix_connect: can't connect to server (unix:/tmp/mcop-andre/localhost_localdomain-2494-43352a92)
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
Error while initializing the sound driver:
device: default can't be opened for playback (No such file or directory)

```

---

### Post by Rosenrot on 2006-06-26
[QUOTE=jdodson]MANY people on the forums here have had sound issues with games.  This thread is an attempt to solve them.  I will outline my problems and then the solutions I have found.  I will note the source when appropriate, as I did not come up with these ideas.

I know Breezy plans to "fix" most of these sound issues, however Hoary is here and now, and we need a fix for some games.

Problem: Quake3 and Enemy Territory have no sound.  In other words, I can't hear when I am getting fragged or when I am fragging, major problem.

There are a number of working solutions that people have mentioned on the forum.  Some have noted the "esd" process is getting in the way.  A simple "ps -aux | grep esd" and a "kill <proc>" to the offending "esd" process have cleared that up for some, as in they can hear things, however for me, and many other people, this did not solve the issue.

other people could run this command with positive results:

```
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
``` 

Thats well and good, if your hardware supports what you are trying to do.  When I rand that command on Quake3 the game would hard lock seconds into the arena.  It simply would not work for Enemy Territory.  Ok, so good for some, hard locks for others, there _HAS_ to be a better way.

After much digging I came across the _BEST_ solution I could find to date.  This fix has solved _ALL_ of my sound problems(I did not have sound issues with some games).  

I will quote from: [http://www.accidentalegg.co.uk/random_problems.php](http://www.accidentalegg.co.uk/random_problems.php)


[B]So anyway, cut to the chase...

   1. Make sure you've got aRts(I did by default in Ubuntu) installed. You'll soon know if you haven't.
   2. Change your quake3 startup script (/usr/local/games/quake3 for me). Where it reads "./quake3.x86 $*" change it to to "artsdsp -m ./quake3.x86 $*"
   3. Run 'artsd -F 6 -S 256', and keep it running...
   4. Start Quake 3!

All this does is run the Quake 3 binary inside artsdsp which captures all it's sound device accesses and re-routes them through aRts. The '-m' tells artsdsp to emulate mmap-ing, which Quake 3 does.[/B]

So basically what you are doing is forcing Quake 3, or Enemy Territory(works in the same way) to use the artsd sound daemon for sound.  I ran Quake3 from start to finish(single player mode) with no hard locks, freezes or any sound issues.  

Good luck, and good gaming![/QUOTE]

how would i do this with UT2004?

---

### Post by EPOX123 on 2006-06-28
Try to compile this program it got my m-audio audiophile 2496 to work.

[http://www.craknet.net/joss/](http://www.craknet.net/joss/)

I made a deb pack dont have a place to upload it.

---

