---
title: "No sound in pcsx emulator"
date: 2010-05-24
forum: Emulators
---

### Post by Akpsp on 2010-05-24
Hi guys. I got the pcsx emulator, everything is working just fine, except for the sound. I found the pcsx emulator from the playdeb site.

---

### Post by portets on 2010-05-24
which version of ubuntu?

and do any other games have broken sound?

---

### Post by Akpsp on 2010-05-25
> **portets said:**
> which version of ubuntu?

and do any other games have broken sound?

The latest version of Ubuntu, 10.04. I have tried using different sound plugins, but they aing working. I have also tried 3 or 4 different games and still no sound. Do you think its my Graphics card? Cause I heard some GPU's werent compatable or something. I have a Radeon HD 4850. Also, im using my gpu for audio. I tried regular speakers, but still nothing.

Also, off from the topic. I have the Snes9x installed, but it lags or stutters. Any way of improving the performance?

---

### Post by jakejw93 on 2010-05-26
I have the same problem right now, trying many different sound plugins and bios!

---

### Post by benhur99ph on 2010-06-03
I got audio problems too. Sometimes when I start a game there is sound...
But sometimes there's none. 

I can get sound by starting the game, then hit Esc .. then resume the game again and again for a couple of times. Sometimes it works but most of the time it won't. 

Even if I did get the sound to work, it's choppy and irritating. Wonder what's wrong. It worked flawlessly back when I was still using Ubuntu 8.04...

---

### Post by disturbedite on 2010-06-03
i'd like to recommend for people to not use pcsx. it shouldn't have kept being used for quite a while. its development has been dead for a long time.

i'd recommend pSX. it doesn't required plugins. best PS1 emulator imo.

or, if you'd like to use plugins, try pcsxr. (it continues development of pcsx).

---

### Post by hikaricore on 2010-06-04
Development on the various forks of pcsx has been slow but steady from what I've seen, the main branch is stale but this is no reason to dissuade its use.
On the other side of this topic PSX hasn't been updated in atleast a year and still can not properly support pulseaudio which has become a staple of modern distros.

A lot of people with integrated audio (mostly intel) currently can not and never have been able to run PSX.
Epsxe and pcsx work perfectly fine in these cases and i more than adequate imho.

---

### Post by disturbedite on 2010-06-05
> **hikaricore said:**
> Development on the various forks of pcsx has been slow but steady from what I've seen, the main branch is stale but this is no reason to dissuade its use.
On the other side of this topic PSX hasn't been updated in atleast a year and still can not properly support pulseaudio which has become a staple of modern distros.

A lot of people with integrated audio (mostly intel) currently can not and never have been able to run PSX.
Epsxe and pcsx work perfectly fine in these cases and i more than adequate imho.

i said pcsx NOT the branches. two different things.

i have integrated audio (intel) on my current & last motherboards and have never had a problem with audio with pSX.

---

### Post by hikaricore on 2010-06-05
Then you can safely consider yourself to not be in the "lots of people" group.  :p

---

### Post by Mazukambax on 2010-06-16
...

---

### Post by T. G. Cid on 2010-06-18
> **Mazukambax said:**
> I'm having the same problem everything runs fine but no sound. Ubuntu 10.04

Using padsp gave me working sound on 10.04

Try the following from a terminal:
padsp pcsx

---

### Post by LtPitt on 2010-10-31
You made my day! :D
It works great!

Now...
To understand...

What does it mean?

---

### Post by I'mGeorge on 2010-10-31
> **Akpsp said:**
> Hi guys. I got the pcsx emulator, everything is working just fine, except for the sound. I found the pcsx emulator from the playdeb site.

Have you considered using pcsx2 ? you can download it from their site extract it and voilla you have a pretty up to date handy ps2 emulator. If your using a 64 bit Ubuntu you will need some auxiliary files to be copied in /usr/lib32, just search for ia32-libs-pcsx2.deb and it should work allright, I know that because I'm using it right now under debian and everything works ok.

---

### Post by cadcam on 2010-11-04
whoa
i don't understand the post on terminal.

padsp and pcsx2

i'm using pcsx2 and i can't get sound.  i've tried switching the sound plugins, etc.  

any ideas?

i'm runnin maverick 64.

---

### Post by wingnux on 2010-11-04
Is this thread about PCSX or PCSX2??

---

### Post by Mazukambax on 2010-11-29
> **T. G. Cid said:**
> Using padsp gave me working sound on 10.04

Try the following from a terminal:
padsp pcsx

It works flawlessly, thank you very much.

---

### Post by Mazukambax on 2010-11-29
> **Mazukambax said:**
> It works flawlessly, thank you very much.

ok, this are the games that games that runs that I tested, FF7, Marvel vs. Capcom, Parasite Eve, Xenogears, Crono Cross and legend of Dragoon but for some odd reason Final fantasy tactics seen to get stuck in the first battle right at Gafgarion turn, the music keeps playing and and all the physics too the rain the character movements but nothing happens after that, why is that?

---

### Post by Sly Cooper on 2011-01-18
hey, I'm also having this problem, but padsd pcsx doesn't help.

I'm running 10.10 Ubuntu, can anyone help?

---

