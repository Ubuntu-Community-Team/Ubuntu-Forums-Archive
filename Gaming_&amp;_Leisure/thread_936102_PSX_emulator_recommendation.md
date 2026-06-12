---
title: "PSX emulator recommendation"
date: 2008-10-02
forum: Gaming &amp; Leisure
---

### Post by zero777zero on 2008-10-02
i've been having a ton of problems getting a psx emulator working, then i came across this one: [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

just download, unzip and double click to launch. no plugins needed.

hope this post can save others some hastle

---

### Post by kylet450 on 2008-10-02
What about PCSX2?

[http://www.pcsx2.net/](http://www.pcsx2.net/)

Thats good.

---

### Post by dfreer on 2008-10-02
> **kylet450 said:**
> What about PCSX2?

[http://www.pcsx2.net/](http://www.pcsx2.net/)

Thats good.

For PS2 Emulation, yeah. Not PSX...

pSX, ePSXe, and PCSX (not 2) should all work fine, I happen to prefer pSX over the others as well.

---

### Post by zero777zero on 2008-10-31
looks like i'm going to eat my foot. i'm using this on intrepid ibex (not beta) and now it wont get past the "choose a language" window. it just closes after selection.

i'm having trouble decyphering if there is anything useful here [http://psxemulator.proboards54.com/index.cgi?board=support&action=display&thread=2986](http://psxemulator.proboards54.com/index.cgi?board=support&action=display&thread=2986)

i'm on 32bit mind you

---

### Post by dfreer on 2008-10-31
pSX + pulseaudio. This problem did not exist prior to Ubuntu Hardy, when pulseaudio was introduced. There's been some reports of disabling/removing pulseaudio to allow pSX to run, but I do not know if it works for everyone.
[http://ubuntuforums.org/showpost.php?p=5977268&postcount=238](http://ubuntuforums.org/showpost.php?p=5977268&postcount=238)

I've been running pSX on Debian Lenny just fine.

---

### Post by zero777zero on 2008-10-31
> **dfreer said:**
> pSX + pulseaudio. This problem did not exist prior to Ubuntu Hardy, when pulseaudio was introduced. There's been some reports of disabling/removing pulseaudio to allow pSX to run, but I do not know if it works for everyone.
[http://ubuntuforums.org/showpost.php?p=5977268&postcount=238](http://ubuntuforums.org/showpost.php?p=5977268&postcount=238)

I've been running pSX on Debian Lenny just fine.

I ran into that post before i bumped this thread, but I never had any issues with pSX on Hardy Heron. Now that I've upgraded to 8.10 the issue is occuring. I'd give that fix a try however i dont know what two files that post is referring to, since the poster only seems to state what the unstated files should be renamed to. :S :S :S

---

### Post by dfreer on 2008-10-31
Hmmm, I thought the poster was refering to renaming the files ~/.asoundrc and /etc/asound.conf to different names, but IDK. I just got Intrepid Live CD downloaded, let's see what it does.

---

### Post by Azure.Rise on 2008-10-31
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/) You need to find the bios file yourself. If you have any problems just install libgtkglext1 through Synaptic or the CLI and that should clear things up.

---

### Post by zero777zero on 2008-10-31
> **Azure.Rise said:**
> [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/) You need to find the bios file yourself. If you have any problems just install libgtkglext1 through Synaptic or the CLI and that should clear things up.

hi Azure.Rise, libgtkglext1 comes with 8.10 and it is installed. i have bios which work, scph1001.bin, and i have used many times before. the file is in the bios folder.

pSX crashes after the first screen, when i select the language.

---

### Post by dfreer on 2008-10-31
> **Azure.Rise said:**
> [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/) You need to find the bios file yourself. If you have any problems just install libgtkglext1 through Synaptic or the CLI and that should clear things up.

I'm thinking Azure.Rise simply read the thread title and not the posts therein...

Other than disabling pulseaudio *somehow* without messing up your sound system, I haven't heard of any reliable ways of getting pSX working since Hardy, and I've been searching for awhile. Since the emulator is closed-source, and the pSX author hasn't been active for some time now, here's your options that I can see:
(1). Use ePSXe or PCSX
(2). Find a way to disable/workaround pulseaudio
(3). Use Ubuntu < 8.04 or Debian (Lenny runs quite nicely)

---

### Post by zero777zero on 2008-11-01
thanks for your replies dfreer. i tried installing pcsx and had some issues with loading iso's, i probably just need to mount them. what i want to recommend to everyone is NOT trying to run the windows version of pSX through wine, i ended up an error message which generated an infinite times until i had to shut my computer down (the cpu barely granted opening the shutdown window). i dont know enough about the politics of software to know where the issue here lies, pSX using an outdated linux kernal as their coding standard, or ubuntu deviating from standards, or linux distros just lacking any real standardization other than LSB, but i hope this issue heals itself for people like me that have never touched code (yes, even we use linux!)

---

### Post by bornagainpenguin on 2008-11-03
> **zero777zero said:**
> what i want to recommend to everyone is NOT trying to run the windows version of pSX through wine, i ended up an error message which generated an infinite times until i had to shut my computer down (the cpu barely granted opening the shutdown window).

I'd like to add my voice to this.  I tried running Codeweaver's Crossover with the Windows version of pSX and ended up doing the endless loop also.

I broke out via the tried and true alt+ctrl+backspace method, killing my xserver.  I fiddled around some more and finally tried to kill pulseaudio with this command and then retrying the program:

```
sudo killall pulseaudio
```

That worked although the audio was still slightly stuttering but that was fixed easily by just increasing the buffer in the configuration menus, and after restarting everything works like it used to!

My question is, how can I add the above command to the menu shortcut so it will run automatically before I try to start pSX?

EDIT: Also there needs to be a way to restart the pulseaudio without having to restart the computer...

--bornagainpenguin

---

### Post by dfreer on 2008-11-03
> **bornagainpenguin said:**
> I fiddled around some more and finally tried to kill pulseaudio with this command and then retrying the program:

```
sudo killall pulseaudio
```

My question is, how can I add the above command to the menu shortcut so it will run automatically before I try to start pSX?

EDIT: Also there needs to be a way to restart the pulseaudio without having to restart the computer...

A bash script would be the answer here:
```
#!/bin/bash
# A script to disable pulseaudio, start pSX, 
# then on close restart pulseaudio.

gksudo killall pulseaudio ## Should pop up a window and ask for password
sleep 1
exec /usr/bin/pSX ## make sure this is the correct path to pSX
sleep 1
gksudo pulseaudio
```

Make sure the script is executable, then add it to the start menu with System -> Preferences -> Main Menu.

This bash script probably won't work, as I don't know anything about how to start/stop pulseaudio correctly, but it should be enough to get you started.

---

### Post by Lee83 on 2008-11-03
i personally have had no problems with PCSX,works a treat on dell inspiron 6400 running hardy,sound,frame rate,everything is bang on..easy to install too,straight from the repo's BIOS was the thing that took the longest to get and that was just a matter of googling :)

---

### Post by bornagainpenguin on 2008-11-03
> **dfreer said:**
> This bash script probably won't work, as I don't know anything about how to start/stop pulseaudio correctly, but it should be enough to get you started.

I hope you'll forgive me then if I wait a bit to try it after I''ve asked around for someone who is a bash expert to give it a look over...

Also, the goal is to be able to run this, have it disable pulseaudio, start pSX from the script, then when pSX closes have the script re-enable pulseaudio.  Any way this can be done or am I asking for something way too complicated? 

> **Lee83 said:**
> i personally have had no problems with PCSX,works a treat on dell inspiron 6400 running hardy...

I'm on Intrepid Ibex and while I had the same experience you did on Hardy using my EeePC, once I did a clean install to Intrepid I found the application simply refused to work with pulseaudio.

--bornagainpenguin

---

### Post by zero777zero on 2008-11-03
pcsx isnt working for me at all. the only option i have is using a CD, and i have everything as .bin/.iso

i'll give this thing a try for psx: sudo killall pulseaudio

also looking into giving epsxe another shot, but that one didnt recognize my controller properly last time around.
edit: looks like double clicking the epsxe executealbe file does nothing, go figure!

---

### Post by bornagainpenguin on 2008-11-03
> **dfreer said:**
> A bash script would be the answer here...

Make sure the script is executable, then add it to the start menu with System -> Preferences -> Main Menu.

This bash script probably won't work, as I don't know anything about how to start/stop pulseaudio correctly, but it should be enough to get you started.

I crossposted at the EeeUser forums, and Pox suggested this:

[quote=Pox]I think a more proper way to do it would be through the daemon controls:
```
#!/bin/bash
gksudo /etc/init.d/pulseaudio stop;
sleep 1;
/usr/bin/pSX;
sleep 1;
gksudo /etc/init.d/pulseaudio start;
```[/quote]

I just tried it and it worked!  I'm back baby!  I'm back!

--bornagainpenguin

---

### Post by dfreer on 2008-11-03
Yeah definitely is a better method. I know *absolutely* nothing about pulseaudio, didn't know that it runs as a daemon or I would've suggested that.

One further modification you might want to make, is create a special sudo case for it so it can be run without asking for a password. This is about the way I would handle it:

Create the bash script, but change it like so:
```
#!/bin/bash
/etc/init.d/pulseaudio stop;
sleep 1;
/usr/bin/pSX;
sleep 1;
/etc/init.d/pulseaudio start;
```

Add the following line to sudo:
```
$ sudo visudo
## Add the below line to enable, change the **username** to yours
**myusername**  ALL= NOPASSWD: /etc/init.d/pulseaudio

```

That should enable you to start/stop pulseaudio without needing a password, but you'll still need your password for everything else. It *might* also work if you add the script's name to visudo, and then run sudo from inside the script. If that works, that would allow the script *only* to be able to start/stop pulseaudio, everyone else including your user would have to use sudo to start/stop pulseaudio.

Sorry for the ramble, just some ideas. If this works for me on the Live CD, I'll create a package for this script and get it into my repository (assuming my repository software works).

---

### Post by Swatfoot on 2008-11-04
Im new to linux I am trying to use pcsx It seems to run fine but how do you get games for it? do I download them ?

---

### Post by dfreer on 2008-11-04
> **Swatfoot said:**
> Im new to linux I am trying to use pcsx It seems to run fine but how do you get games for it? do I download them ?

It's actually against the rules of this forum to ask about where to download games, as it's illegal to do so. Same goes for the BIOS. Most playstation emulators are quite capable of playing playstation games you already own, by placing the game CD in your CD drive.

---

### Post by zero777zero on 2008-11-04
> **Swatfoot said:**
> Im new to linux I am trying to use pcsx It seems to run fine but how do you get games for it? do I download them ?

to run a PSX emulator you will need bios, you can dump these from your playstation. in many countries it is legal to download them from the internet, but not in USA.

you can run a game by:
1. putting the gamedisc into your drive
2. playing from a game image (.bin/.iso) which you made by yourself from a game you own
3. in some countries (unsure about USA) you can legally download game images if you own the specific game you are downloading

---

### Post by dawynn on 2008-12-15
Thanks, guys, for the scripts.

Couple notes:
pcsx doesn't work for me either, under Intrepid.  Thank you guys so much for providing some script ideas to shut Pulseaudio off for pSX.  Been nice to get pSX working again.

Unfortunately, the pSX author is convinced that ALSA is *the* sound system for Linux.  I once asked about him using oss, and he was adamant about sticking with ALSA.  Same thing with incompatability with pulse, I guess.  Maybe, if he ever does an update, we might see some change in the sound system.  Not sure how active he is on coding this still, though.

As far as getting Playstation games.  See the following:
[http://linuxreviews.org/howtos/cdrecording/#toc11](http://linuxreviews.org/howtos/cdrecording/#toc11)
Gives some great help on how to pull data from PS1 CD's.  Makes it *real* nice to be able to put the disks away and just play from a hard drive (protects your collection, too!).  At least this way, you're legal as far as the games are concerned.

One other thing -- as far as sound issues.  There is a recognized issue with the Linux version of pSX.  For some reason, the sound works better if one cranks the latency up.  Doesn't seem to be a problem in Windows, but has been a problem ever since the Linux version was introduced.

---

### Post by dfreer on 2008-12-16
Regarding ripping playstation games to the hard drive using linux:

That guide has been mentioned a couple of times, and although it will work on some PSX games, do not expect it to backup up all of them correctly. There's several reasons for this, if needed I can dig up the relevant posts. 

One quick thing FTA:
> It makes no differnece if the contents table you feed cdrdao is called .cue or .toc
Which isn't quite true, it isn't following the correct format for .cue I do believe. It's been a while since I last discussed this issue.

For now, just make sure to test your ripped game to see if it works correctly :D

---

### Post by dawynn on 2008-12-16
It's also worth noting that, just as with most emulated systems, some emulators just work better with some games.

If I recall correctly, Tomb Raider didn't work for me under pSX, but did under PCSX (back when I could get that to work).  Final Fantasy IV is known to work under pSX, but with graphics glitches.  Other emulators do better with it.

It could just be my computer, but I found that pSX didn't keep up with the sound correctly on many games.  PCSX did a much better job of it.  But PCSX also seemed to run most games a bit faster (probably more true to the PS1 speed).  But then I'm using an Athlon 1.4 Ghz machine.  Better machines may not show the lag in pSX quite so bad.

Now that I'm remembering all this, I'm going to have to try harder to get PCSX working on my machine again...

---

