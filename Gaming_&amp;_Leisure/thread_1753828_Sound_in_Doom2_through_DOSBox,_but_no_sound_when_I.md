---
title: "Sound in Doom2 through DOSBox, but no sound when I play .wads"
date: 2011-05-09
forum: Gaming &amp; Leisure
---

### Post by hellhounds88 on 2011-05-09
Hi all,

This is my first post as a new Linux/Ubuntu user looking for help. Since switching to Ubuntu, Google has become my best friend, but I do believe that I'm having a problem which may be somewhat unique and might require some extra help for me to solve it.

So I have a copy of Doom 2 which I bought from Steam on Windows, copied to my Ubuntu /home/dos/c directory which mounts for DOSBox, and from which I removed all Steam-added files so that now I only have the basic doom2.exe and doom2.wad files in that directory. I wrote a configuration file to change the controls and a .bat file so that I could launch Doom 2 from my desktop. Everything for Doom 2 classic runs great: gameplay, sound, controls. It's all working great.

Until I try to load some of my favorite .wad files to play...

They all load just fine, using the standard DOS "doom2.exe -file x.wad" option, and nothing at all seems wrong with the gameplay. Only one problem: NO SOUND.

What could be causing this? Is there an additional option or parameter I need for the "doom2.exe" command which loads the sound? Where did my sound go?

I love Ubuntu and I enjoy working on the problems I encounter, because of the sense of satisfaction I get from having figured it out. My sincere thanks to anyone who responds.

---

### Post by perspectoff on 2011-05-09
Ummm, Doom2?

You want Skulltag, my friend.

Evolution: Doom2 -> ZDoom -> GZdoom -> Skulltag

Installation is automatic (for Ubuntu/Kubuntu/Debian operating systems) from repositories.

Here are the instructions I use:

Ubuntuguide:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Skulltag](http://ubuntuguide.org/wiki/Ubuntu:Natty#Skulltag)

or Kubuntuguide:

[http://www.kubuntuguide.info/index.php/Natty#Skulltag](http://www.kubuntuguide.info/index.php/Natty#Skulltag)

Skulltag allows you to automatically download and install hundreds of wads (my current favorites are Call of Duty look-alikes called RGA2 (Real Guns Advanced 2), play network games more easily than Steam, and even do realtime chat with other players.

I'll see you on Skulltag (look for me as Big Muah!)

---

### Post by hellhounds88 on 2011-05-09
Howdy and thanks for responding.

You're absolutely right that there's a whole universe of doom source ports out there for linux, and I could very easily just play doom through one of them, but I'm kind of interested to know the solution to this. I mean, I have the official .exe and the official .wad. From what I understand DOSBox is an excellent emulator, and coupled with the fact that I can get the vanilla doom 2 working flawlessly, it seems to me like I'm just missing something simple like an option or parameter that tells doom to load the sound (perhaps from the official doom2.wad) in addition to loading the .wad file?

---

### Post by perspectoff on 2011-05-09
There's a point where it's ridiculous to make a square peg try to fit in a round hole. The original Windows/DOS Doom2 from 1995 is a dinosaur and doesn't play very well compared to even PrBoom (which is directly installable on Ubuntu/Kubuntu).

All you really need is the Doom2.wad from your commercial Doom2 disk (which you can copy pretty easily to any folder for any source port). It will then play identically to the original Doom2.

If you want instructions how to do this, see

Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Natty#Doom](http://ubuntuguide.org/wiki/Ubuntu:Natty#Doom)

Kubuntuguide:

[http://www.kubuntuguide.info/index.php/Natty#Doom](http://www.kubuntuguide.info/index.php/Natty#Doom)


It's too bad you won't try Skulltag. I could use some worthy opponents. (They also have Deathmatch, Cooperative, Last Man Standing, and Capture the Flag types of Multiplayer games. You won't find those anywhere else.)

---

### Post by hellhounds88 on 2011-05-09
Never mind I figured it out!

For some reason the "doom2" command REQUIRES a .cfg file to tell it to have sound. Simply used "doom2 -config configfile.cfg -file whatever.wad" and the sound works. Eureka. Thanks for your help though, and I WILL give those source ports a try now!

---

