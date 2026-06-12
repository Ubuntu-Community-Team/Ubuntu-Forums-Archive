---
title: "Rise of the Triad (ROTT) Woes"
date: 2007-11-30
forum: Gaming &amp; Leisure
---

### Post by plinydogg on 2007-11-30
Hi peeps,

I just installed Rise of the Triad via Synaptic and when I run it (by typing "rott" in the terminal), the game starts fine but once I've selected difficulty, etc. and the actual game has begun everything freezes after the first second ticks away. I've got plenty of hardware muscle for this one so I can't figure out what I'm doing wrong. 

Any ideas would be appreciated!

---

### Post by Vadi on 2007-11-30
Seems like a game problem. It froze for me too.

---

### Post by cogadh on 2007-11-30
Ditto, but it didn't happen for me until I started the game, moved around a bit, then went back to the options menu to try and change something.

---

### Post by wishyjr on 2007-12-01
whoa whoa, rise of the triad is in the repos!? Ace! I'll install it and probably come back to this thread when it doesn't work for me too ;)

---

### Post by plinydogg on 2007-12-01
I would just run it with DosBox, but if I remember correctly it doesn't work properly in DosBox (but I could be wrong). wishyjr: yes, it's in the repos. Do a search for "rott".

---

### Post by derekr44 on 2007-12-01
Where are youuuuuu?

Over heeeeeere...

---

### Post by PrimoTurbo on 2007-12-02
You realize you need the data files, this is probably the engine of the game. Have you installed the data file or no?

> Rise of the Triad -- The HUNT Begins
Rise of the Triad is a high quality, fast scrolling first-person perspective
3D action game. It includes a lot of destructive enemies, an arsenal of
weapons from simple pistols to missile launchers, life-preserving armor, traps
and ambushes galore.

WARNING: Rise of the Triad features wanton and gratuitous violence.

 Homepage: <http://icculus.org/rott/>

[B]This package contains no data files but can install the shareware data files
from the Internet.[/B]

---

### Post by mister_k81 on 2007-12-02
I had no idea that ROTT was available through the repositories. Cool, I just tried it. :) 

My only suggestion would be to go into the repositories and download timidity midi sequencer. A lot of older DOS PC games require it or they end up crashing, from what I noticed. 

 Or just type: ":~$ sudo apt-get install timidity" into the terminal without the quotes.

---

### Post by cogadh on 2007-12-02
> **PrimoTurbo said:**
> You realize you need the data files, this is probably the engine of the game. Have you installed the data file or no?
The package gives you the option of downloading and installing the shareware data files when you run it.

---

### Post by plinydogg on 2007-12-02
I did what cogadh was talking about and downloaded the shareware files.

---

### Post by el_oscuro on 2007-12-26
From my username, you can tell I am a serious ROTT fan.  I have played it since it came out, and can even defeat NME without cheats :lolflag:

That said, I have it working on Gusty including sound (I had to install timidy to get the music working).  YMMV.

The question I have is how do I get it working with Darkwar which , you can also purchase them from 3drealms.com).  The one in the repository is for the shareware version only.  I have successfully compiled the source from [http://icculus.org](http://icculus.org) and modified it to use the Darkwar wads, but it doesn't have the full screen hack (nothing like fighting NME in a 2" x 3" window).  Does anyone have the source with the fullscreen hack or is there a version/configuration in the repository which supports the darkwar wads?

:)I also have successfully compiled the source for Duke Nukem 3d from [http://icculus.org](http://icculus.org) but am still waiting on my wads from 3drealms:)

---

### Post by toupeiro on 2007-12-30
> Rise of the Triad Startup  Version 1.4
 Shareware Version 
Z_INIT: 8950000 bytes
IN_Startup: Mouse Present
    Adding /usr/share/games/rott/HUNTBGIN.WAD.
    Adding /usr/share/games/rott/REMOTE1.RTS.
W_Wad: Wad Manager Started NUMLUMPS=2103
OH NO OH NO ROTT CRASHED!
Here is where:
Stack dump:
{
        /lib/libc.so.6 [0x2aecc3d037d0]
        rott(BuildTables+0x5a) [0x456352]
        rott(main+0xc1) [0x46a51d]
        /lib/libc.so.6(__libc_start_main+0xf4) [0x2aecc3cefb44]
        rott [0x427da9]
}



sigh... I think 64-bit foils me again.. one of my all time favorite FPS's. 

God mode... MMMUUURRRRRR

---

### Post by jespdj on 2008-01-02
> **mister_k81 said:**
> My only suggestion would be to go into the repositories and download timidity midi sequencer. A lot of older DOS PC games require it or they end up crashing, from what I noticed. 

 Or just type: ":~$ sudo apt-get install timidity" into the terminal without the quotes.
I just installed ROTT and had the same problem - the game freezes after about a second or so, and I had to kill it with kill -9.

Installing timidity fixed the problem!

---

### Post by el_oscuro on 2008-01-10
A bit off topic, but I got my Duke Nukem 3d CD, and it works!  You have to have the atomic edition or the standard edition with the plutonium pak, but it works.  The sound is scratchy and there is no music, but everything else works!

---

### Post by plinydogg on 2008-01-12
I'm not familiar with Timidity...what is it?

That's good news about Duke3D...I love that game too!

---

### Post by Dark Aspect on 2008-01-12
> **toupeiro said:**
> sigh... I think 64-bit foils me again.. one of my all time favorite FPS's. 

God mode... MMMUUURRRRRR
If the game does not work on 64-bit Linux just use dosbox,I have yet to have an issue with it if you set the CPU cycles high enough.I am not really a  Rise of the Triad fan though so I never finished the game under dosbox,it may have bugs idk.I think dosemu will run the game too since dosbox was too slow to play back Duke Nukem on my system I have tested a few games under that emulator.

To get off topic yes I got Duke Nukem 3D to work on Dosemu with sound but I have no midi music??????????Ideas for why that is would be nice.

---

### Post by jlang00069 on 2009-04-03
Hey guys,
   I had the same issue with locking up after selecting difficulty. After I installed timidity, it seems to work. Haven't played it much but this should get you further than the 'difficulty selection' screen.

happy hunting,
-JL

---

### Post by lingenfr on 2009-05-02
Thanks guys, timidity was the answer. Also, there is a page with instructions, but if you didn't see it, your type 'rott fullscreen' to run it fullscreen. I think that I will buy the download version of this. I am going to look to see where to place the file. Thanks.

---

### Post by mister_k81 on 2009-05-02
> **lingenfr said:**
> Thanks guys, timidity was the answer. Also, there is a page with instructions, but if you didn't see it, your type 'rott fullscreen' to run it fullscreen. I think that I will buy the download version of this. I am going to look to see where to place the file. Thanks.

Pressing 'Alt+Enter' is also the universal key command to get in and out of fullscreen mode. 


> **plinydogg said:**
> I'm not familiar with Timidity...what is it?

That's good news about Duke3D...I love that game too!

I know I'm over a year late to respond to this one... 

But, Timidity is a software synthesizer that is used to play MIDI music files. The majority of sound cards/ sound hardware today don't have MIDI support built in (as far as I know), so you have to emulate it through software using programs like Timidity. Almost all of the old-school DOS games used MIDI as their main source of music.   
   
Though I'm sure there's also a way to disable the MIDI music in Rise of the Triad and get it to work without crashing all the time.

Also, does anyone out there know if there are any alternatives to Timidity? I'd really like to know.

---

