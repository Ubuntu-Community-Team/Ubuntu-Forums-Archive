---
title: "beryl kills videos?"
date: 2007-03-22
forum: Desktop Effects &amp; Customization
---

### Post by da1nonlymikeo on 2007-03-22
hey everyone, ever since i installed beryl, when i play videos or i go to a website that has a video playing like flash or java i suppose, my media player and firefox close](*,) . whats going on??

---

### Post by Stickymaddness on 2007-03-22
I think it's because you have Beryl running...

Beryl runs smoothly on my system, but as soon as I try something like glxgears or a 3D screen saver things go really slowly...

---

### Post by da1nonlymikeo on 2007-03-22
thats what i thought too, because this never happened untill i installed beryl. but when i kill beryl and beryl manager it still dose it. :(

---

### Post by zdude on 2007-03-22
Hmmm, I am running Beryl and I don't have any of those issues. Since it does it when Beryl is not running I would guess some plugin in your browser/system is borked.

---

### Post by mcduck on 2007-03-22
For videos, try configuring your video players to use some other video output plugin.

---

### Post by SyberKowboy on 2007-07-13
I've tried both opengl and xv and am having no luck. The weird thing is that I just had it working on another install and couldn't get rid of the lag. So I reinstalled and after Beryl I have no video instead of just lag. Starting to piss me right off. Doesn't matter the player or output module! Helps pleases :p

---

### Post by FuturePilot on 2007-07-14
What happens when you switch to Metacity? Right click on the Beryl Manager icon and go to Select Window Manager. Click on Metacity.

---

### Post by SyberKowboy on 2007-07-16
Haven't tried that but I have isolated it to Beryl. If I uncheck the session mananager launcher for Beryl and restart X the problem goes away. I can ever launch AWN without Beryl, which is dumb, but it works and all video works great.  Has anyone else had issues with Beryl killing video?

---

### Post by SyberKowboy on 2007-07-16
I just tried changing the manager to Metacity and the video works beautifully. But during playback if I change it back to Beryl.....BOOM, CRASH, BANG, like Adam West kicking criminals in the nutz, my video player crashes to the floor with a THUMP. Beryl gods please forgive me and save my system from the crash. Ahhhhh.....

---

### Post by SyberKowboy on 2007-07-16
bump....

---

### Post by SyberKowboy on 2007-07-16
> **zdude said:**
> Hmmm, I am running Beryl and I don't have any of those issues. Since it does it when Beryl is not running I would guess some plugin in your browser/system is borked.

Are you running Beryl in a GNOME session or a Xgl session? Would love to know.

Thanks...

---

### Post by Ace2016 on 2007-07-17
I am able to play videos fine, i use XGL and beryl, i i do notice higher cpu usage during video playback, i am unable to play very high resolution videos like the Elephants Dream video. Inability to play videos is down to the speed of your cpu, i don't think there is hardware acceleration for apps running on xgl so the cpu does the work

My system specs: 

AMD Athlon XP2000+  .  1.25GB of ram  .  NVidia Geforce FX5200+

its not that great but its ok for a good game of ut2004, being upgraded soon for ut2007 & kde4 ;)

What are your system specs?

---

### Post by vsugadhan on 2007-07-17
Seems I too have the same problem...Videos wont run.... It works on metacity though....
Anyone find a workaround?

---

### Post by SyberKowboy on 2007-07-18
I'm running all this ontop of GNOME on a laptop with these specs

MSI Whitebook intel 945 chipset
Intel 950GMA integrated video
T7200 Merom Core 2 Duo 2Ghz
2gigs of RAM
SATA HDD

I could get it to run on Xgl, but I broke too many things getting it the way I wanted and started over. Now I can't render a damn thing. All video players die as soon as I run them if Beryl is going, but as soon as I switch to Metacity it's all good. Not the worst thing in the world but really annoying. Really would like to know how to fix this one.  TIA

---

### Post by mysticmatrix on 2007-07-19
Try This:

On terminal type

```
gstreamer-properties
```

From video output, choose video plugin: No XV.
This will enable play in Totem.

For Mplayer, right click --> Preferences. On video tab, choose X11 as your driver.

You can similarly fix problems with VLC and Xine. 

In short, turn output of every god damn video player you know to X11 ( No XV or OpenGL)

---

### Post by SyberKowboy on 2007-07-20
Well I'll be a stuck pig in quicksand. That cured it right up like a shot of penicillin. Thanks

---

### Post by stuntman84 on 2007-08-10
mysticmatrix:  hey! thank you...have been trying to figure this out since a long time...thanks again!

---

### Post by FeistyStyle on 2007-08-16
The gstreamer properties open when I type the command but I see this in the terminal when I do it

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'

Switching to X11 didnt work via Gstreamer but changing the settings in Mplayer to X11 did, however I have no full screen support with Mplayer, the video just stays the same size

what should i do?

totem still closes despite the gstreamer command

---

### Post by punong_bisyonaryo on 2007-09-18
> **mysticmatrix said:**
> Try This:

On terminal type

```
gstreamer-properties
```

From video output, choose video plugin: No XV.
This will enable play in Totem.

For Mplayer, right click --> Preferences. On video tab, choose X11 as your driver.

You can similarly fix problems with VLC and Xine. 

In short, turn output of every god damn video player you know to X11 ( No XV or OpenGL)

On a clean install, beryl with Totem-gstreamer works fine. But somehow I messed things up when I install totem-xine (which removed totem-gstreamer). I removed it and reinstalled totem-gstreamer because beryl has problems displaying the video with totem-xine. However, this broke my totem-gstreamer as well. It doesn't crash, but it just displays black after playing the first frame of the video. It reappears sometimes when you nudge the window a bit, but will just as easily disappear again. No problem with metacity.

I tried deleting all my conf files (all those hidden .folders in my home folder), but it was only this solution that fixed it.

I am curious about the root cause of this: What is XV? Is the default No XV or is it X11/Shm/Xv? To what does "Autodetect" default to? Or did some application change these properties?:confused:

---

### Post by petay on 2007-10-02
I have been having the same problem with my lappy!!

my desktop has the same things installed and workes fine but my lappy didnt like the video settings

i managed to get it working with mplayer but i could not find the settings for totem, till now of course!!!!

maybe the internal intel graphics dont like the way that beryl changes things??

Thanks for the fix :D

---

