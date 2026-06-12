---
title: "The future of sound input/output in Hoary"
date: 2005-03-25
forum: Desktop Environments
---

### Post by ioliver on 2005-03-25
I've read all the tales of woe and useful tips regards getting microphones to work in Hoary, but I still haven't managed to get mine working to my satisfaction.

In Multimedia Systems Selector I can choose input via ESD (which hangs the test), OSS (which give a heavily distorted and crackly input), or ALSA, which with a *lot* of tweaking is grim but the best I can get.

If I boot into Mepis it all just works, and even Skype is happy with zero changes to anything.

Is Ubuntu going to improve in this area in the Hoary timeframe or do we have to wait for the next version?

Ian

---

### Post by lgaboury on 2005-03-25
Hi,

I was experiencing the same distorted sound with ALSA.  I fixed this problem by selecting the proper device in the Volume Control. Right-click on the volume (speaker) icon on the taskbar.  Select Open Volume Control.  Click on File-> Change Device and ensure you select the ALSA Mixer.  Then Open the Multimedia Systems Selector and ensure your ALSA is selected as your output and input devices.  This fixed the problem for me resulting in a clear sound.  Hope this helps.

Luc.

---

### Post by ioliver on 2005-03-26
I ended up with roughly that setup, thought with ESD for output, but it did take a while, and quite a few occasions where Sound Recorder and MM Selector locked solid, before I hit on a working combination.

And microphone input quality is still "so so" rather than crystal clear.

Is there a good explanation anywhere of how ESD, OSS, ALSA, the mixers, the selectors, polyaudio, etc. all fit together and what the data flow is? 

(Not, of course, that this is any substitute for Hoary having a working setup "out of the box")

Ian

---

### Post by twiedi on 2005-03-26
Yes, I'd like to see an understandable explanation, too. Since I'm a former Windows user, I don't understand all the linux stuff that quick. And I'm struggling with the sound in Ubuntu for weeks. Sometimes Skype is working, though I don't know exactly why. But then audio and video streams are out of sync. Sometimes the other way around. 

If someone wants to write an easy to use HOWTO he will certainly gain a broad wave of sympathy from all the switchers like me.

But it would be best, Ubuntu would work just out of the box.

---

### Post by cwaldbieser on 2005-03-26
I just upgrade to Hoary, and I also had some problems with my sound.  (I thought I was going to have problems with my ATI 3D acceleration, but that worked easily :)).

After poking around considerably, reading posts from other forum members, googling, etc., here is what I found:

It seems like there is no "one standard way" to access the sound hardware in the *NIX world.  It seems like one of the earlier attempts at standardizing sound was OSS (The Open Sound System).  That was good, but as sound cards got cheaper and more feature rich, it didn't really cut it, so ALSA (Advanced Linux Sound Architecture) was supposed to be like a replacement.  There needed to be backwards compatibility for old OSS apps, so that still hung on.  Now there are quite a few more sound systems (Enightened Sound Daemon, polypaudio), and some sound libraries (OpenAL) or libraries with sound support (Simple Direct Media Layer), so for a program to get to the actual sound hardware, there is a "maze of twisty little passages all looking very much alike".

Desktops like Gnome or KDE simplify things, because you configure the entire desktop to use one sound system, and all the integrated apps use that system.  I am not sure how to configure what system you use in Gnome, but in KDE you can do it from KControl -> Sounds.

Of course, for non-integrated apps, you usually have to manually select from each of them what sound system it is going to use (XMMS, gxine, kaffeine, etc.).  Similarly, games that use particular libraries like OpenAL can often be configured to use different backends.  OpenAL can be made to use OSS, ALSA, ESD, or SDL by tweaking ~/.openalrc.  (This was eventually how I got chromium B.S.U. to work under Hoary).

There does not seem to be any kind of "uber interface" to the sound hardware that collects these various systems together and funnels everything together.  This is much different than "classic" file interfaces in *NIX where a real file, stdout, or /dev/null can all be treated very similarly.

That's my take on it for what it's worth.

---

### Post by ioliver on 2005-04-04
Hmmm, now I can't find Multi-Media Systems Selector on the menus. 

Any idea where it's gone?

Ian

---

