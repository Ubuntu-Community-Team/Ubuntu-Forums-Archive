---
title: "Zsnes and Sound"
date: 2008-03-23
forum: Gaming &amp; Leisure
---

### Post by riskbreaker927 on 2008-03-23
Hi folks!

I'm mostly posting this to list a solution to the problems I had with ZSNES. 

So I'm running the Hardy Heron beta (Ubuntu 8.04), and I have no sound in ZSNES. Google served me well in finding fixes for pre-PulseAudio Ubuntu, but alas that's not the case in Hardy.Also, for the record, I'm running a Dell Inspiron 1501 laptop with the default onboard sound. Here's what I eventually did.

Run Zsnes as follows:```
zsnes -ad sdl
```This will set ZSNES to use Simple Directmedia Layer output for sound (instead of ALSA as it defaults to,) and then launch ZSNES. If you get sound at this point, as I did, then that's good news. However, in my case, the sound was garbled and crackly. So after some more digging, I came across the following.

To get rid of the garbled sound, type:```
sudo apt-get install libsdl1.2debian-oss
```It may get rid of some other packages, but they are not that necessary. Or weren't in my case. Anyway, try ZSNES again and it should work.

Please feel free to post comments and questions, or move this if this is in the wrong section. Enjoy!

---

### Post by acoustibop on 2008-03-24
Rather than libsdl1.2debian-oss, riskbreaker927, try libsdl1.2debian-all.  This gives your system the option of all the SDL drivers, rather than just ALSA or OSS.

It's a good idea to try ZSNES with all the sound options - do zsnes --help to see what options there are, then set whichever works best in your ZSNES configuration (~/.zsnes/zsnesl.cfg).

---

### Post by GSZX1337 on 2008-03-24
To get rid of the garbled sound in ZSNES I just got turned off the sound filters.

---

### Post by itix on 2008-03-24
Where do you do that??

---

### Post by GSZX1337 on 2008-03-24
Under the souns options.

---

### Post by itix on 2008-03-24
Not on my zsnes. I have the folowing: 

Disable SPC emulation,
Enable Sound,
Enable Stereo Sound
Reverse Stereo Channels
Simulate surrond sound

Sampling rate
Volume level

Interpolation and Lowpass

---

### Post by acoustibop on 2008-03-24
They're at the bottom, under Interpolation and Lowpass, itix.

---

### Post by riskbreaker927 on 2008-03-24
> **acoustibop said:**
> Rather than libsdl1.2debian-oss, riskbreaker927, try libsdl1.2debian-all.  This gives your system the option of all the SDL drivers, rather than just ALSA or OSS.

It's a good idea to try ZSNES with all the sound options - do zsnes --help to see what options there are, then set whichever works best in your ZSNES configuration (~/.zsnes/zsnesl.cfg).

One of the things I found on this forum suggested this, but I found that it wasn't working when I had that package installed. The -oss package removed the -all package when I installed it, but hey, it works.

As for the guy who suggested turning off the sound filters. My problem was occuring on a clean install of zsnes (i.e. apt-get install zsnes, then run zsnes.) No sound filters are enabled by default.

---

### Post by acoustibop on 2008-03-24
If you install any specific SDl package, it will remove the -all package, riskbreaker927.  However, the -all package includes the -OSS driver.

---

### Post by riskbreaker927 on 2008-03-25
Well it seems like the important part is, regardless of whether or not the -oss or -all package is installed, the oss driver needs to be used. How would one do that using the -all package? It seems like it defaults to something else (likely alsa).

---

### Post by acoustibop on 2008-03-25
See my earlier post, riskbreaker927:

> **acoustibop said:**
> ... then set whichever works best in your ZSNES configuration (~/.zsnes/zsnesl.cfg).

If you do zsnes -? in a terminal, it'll give you a list of the sound settings you can use.

---

### Post by disturbedite on 2008-03-25
there is another possible problem here.  there is a known issue of zsnes having crackling audio with some motherboards that have onboard sound chips (instead of sound cards).
it is still the best snes emulator though.

---

### Post by itix on 2008-03-25
... no they're not :S

---

### Post by itix on 2008-03-25
OSS gives no sound at all on my ACER.

---

### Post by acoustibop on 2008-03-25
Then try the other options, itix, and see what works for you.  See my first post in this thread, and other people's posts, as to how to do this.

Personally, I find the sdl option is what works for me.

---

### Post by itix on 2008-03-25
Tried the other options... I highly suspect that it has something to do with my motherboard as *disturbedite* suggested above.
Would that possibly affect the windows version as well. What I'm trying to say is that zsnes ran fine while I still had windows...

---

### Post by acoustibop on 2008-03-25
Does sound work Ok for you other than in ZSNES, itix?  If that's so, I'd suggest installing the libsdl1.2debian-all package (it'll remove libsdl1.2debian-alsa but don't worry; also is actually reinstalled as part of the libsdl1.2debian-all package) and then try the ZSNES options again.

---

### Post by disturbedite on 2008-03-26
> **itix said:**
> Tried the other options... I highly suspect that it has something to do with my motherboard as *disturbedite* suggested above.
Would that possibly affect the windows version as well. What I'm trying to say is that zsnes ran fine while I still had windows...
i wish i could tell you, but i don't know if the onboard sound issue affects windows also or not.

---

### Post by acoustibop on 2008-03-26
At a guess, onboard sound issues probably relates to drivers, disturbedite.  So no, you wouldn't necessarily get the same issues in Windows because you'd probably have a specific the the manufacturer has so kindly provided...

---

### Post by itix on 2008-03-26
I have already installed the *libsdl1.2debian-all* package and re-tried the different sound options. The sound works best with SDL since I can load and save on stats without lost sound, but it is still scratchy, ALSA can be scratchy to sometimes, (but it puts out this "underrun" thing) and it always fails after loading my last save state.

---

### Post by acoustibop on 2008-03-26
The 'underrun' message suggests you have a soundcard with inherently high latency, itix.  Your best bet, if you have spare PCI slot in your machine, is to get a decent soundcard and disable the onboard one.

Sound latency in Ubuntu is improving all the time; my guess is that Hardy will be even better in this regard.

---

### Post by itix on 2008-03-27
I have already installed the *libsdl1.2debian-all* package and re-tried the different sound options. The sound works best with SDL since I can load and save on stats without lost sound, but it is still scratchy, ALSA can be scratchy to sometimes, (but it puts out this "underrun" thing) and it always fails after loading my last save state.

---

### Post by acoustibop on 2008-03-27
You've just repeated your last post, itix.  As I said the problem with your sound and the "underrun" message - I presume it's "sound underrun?" - is your soundcard.  Although newer versions of Ubuntu (hopefully Hardy) will improve this, your present onboard solution will always put a limit on what you can get.

This should be better in Windows, because Windows does have inherently lower latency than Linux.  New Linux distributions are always improving, though.

---

### Post by itix on 2008-03-28
Ooops. I'm sorry. It must have happened when I resumed my browser.

The message is "ALSA underrun, must be more than 0ms", and I get it constantly while running games in ZSNES. I have Explained it more thoroughly [here]("http://ubuntuforums.org/showthread.php?t=730783").
I have the Hardy Beta, but it hasn't solved any sound problems with ZSNES unfortunately.

---

### Post by acoustibop on 2008-03-28
Sounds like you have a sound latency problem, itix.  Linux kernels generally have higher sound latency than Windows, although Ubuntu has been getting very good in this respect - latency in Gutsy is excellent, and I'm hoping it'll get even better in Hardy.

However, your soundcard also contributes to the sound latency - some cards have very low latency, but some (even some that are good in other respects) can have very high latency, and when a high latency card is run in a Linux kernel, you can get problems.  There's no real fix, except choosing a distribution where the latency is as low as possible and - mainly -  using a good sound card.

What sort of soundcard are you using?

---

### Post by FranMichaels on 2008-03-28
> **itix said:**
> I have already installed the *libsdl1.2debian-all* package and re-tried the different sound options. The sound works best with SDL since I can load and save on stats without lost sound, but it is still scratchy, ALSA can be scratchy to sometimes, (but it puts out this "underrun" thing) and it always fails after loading my last save state.

Did you try setting the sample rate to 48000hz in zsnes?
Also, is your zsnes compiled with libao support (I'm guessing it is since you mentioned setting it to SDL...)

---

### Post by itix on 2008-03-28
That would be one of the few parts of my computer that I am unsure of as of today, acoustibop. Thank ou anyway for trying. I can't give ou a "thank you" since that would be misleading, so simply; Thank You.

To FranMichaels. You just solved it, Thank You! I have no idea how or why that solved the problem but it did :D

---

### Post by itix on 2008-03-29
I change my mind. It did not at all solve anythig. Some component of compiz crashed and the sound worked, but now that I have restarted the computer, everyting is back to "normal". Why is this?

---

### Post by acoustibop on 2008-03-29
Always disable Compiz when playing games, itix.  Right click on your desktop, click Change Desktop Background , go to the Visual Effects tab and select None,

---

### Post by FranMichaels on 2008-03-29
Hmm. The sound should work even with compiz on. At least it did for me (and I have onboard sound on a laptop so nothing fantastic...) 

Does
```
zsnes --h | grep ad
```
Return a line like this >  -ad <>  Select Audio Driver :
I just want to be certain your zsnes has libao support, because the sound problems you have sound (haha no pun intended!) like the issues I had before enabling libao support.)

What is the video out for zsnes? OpenGL (O something in the list) or just DR. Try switching between the two.

Also, does the sound start to get messed up as you play? If so, does pressing escape twice (in zsnes, going to menu and going back) make it sound normal? 

if so, does your home folder have a .asoundrc or .asoundrc.asoundconf
you can try renaming those to .bak or moving them to trash (so you can just drag n' drop them back in if nothing helps here.)

Then run zsnes.

If still no improvement
open a terminal and type
```
asoundconf list
```

From there it will list your available soundcards

then type the name of the card (the list probably has one anyway, and remember it is case sensitive)

```
asoundconf set-default-card **YourSoundcard**

```
*Replace YourSoundcard with the name of your soundcard from asoundconf list.

Try zsnes again. If it still doesn't work, I'm totally stumped... If you want I can help you build zsnes from the dev's subversion repository. ZSNES "1.52" runs well enough (though I don't know if it would help this sound problem, I use it as default I just can't help but run bleeding edge versions of certain emulators ;)

:KS

---

### Post by iris-n on 2008-03-29
Seems like a stupid remark, but what made my sound good was turning down the zsnes volume from 100% to ~60%
This after changing the sampling rate to 48 Khz, so i could use alsa.
To note, i use one of this so-cursed onboard crappy sound cards.

---

### Post by itix on 2008-03-30
Will that affect my settings?? I don't want them to get lost.

---

### Post by itix on 2008-03-30
The code returned ```
itix@itix-laptop:~$ zsnes --h | grep ad
                0 = None       1 = Keyboard/Gamepad
  -ad <>  Select Audio Driver :
  -zm #   Auto load specified movie slot on startup [0..9]
  -zs #   Auto load specified save state slot on startup [0..99]

```
(which is what I guess you wanted)

...and for some strange reason ALSA has given up on me completely now too.

The sound I used when compiz chrashed and which now seams to be my only sound is SDL. When I prevously COULD use ALSA, it scratched most the time to be perfectly honest.

---

### Post by acoustibop on 2008-03-30
Reboot, itix.  Do don't usually have to in Linux, but when things like this happens, it's a good idea at least to restart X and sometimes to reboot.

---

### Post by FranMichaels on 2008-03-30
> **itix said:**
> Will that affect my settings?? I don't want them to get lost.

if you back up those 2 files, you can restore the settings drag and drop. Aren't your current settings problematic?

---

### Post by itix on 2008-03-30
No...  compiz settings :p

---

### Post by Cresho on 2008-03-31
hi!

I spent tons of hours getting zsnes and gxmame running.  All I did to get these two running in hardy heron was to install libsdl1.2debian-all and run "zsnes -ad sdl" in the terminal.  I have no problems.

---

### Post by itix on 2008-03-31
Yes... SDL works for me too as long as compiz is turned off, but there has to be some restore point for compiz or something because it takes too long to restore all settings to compiz manually.

---

### Post by acoustibop on 2008-03-31
See my previous [post in this thread]("http://ubuntuforums.org/showpost.php?p=4610009&postcount=29"), itix.  I'm not that bothered with Compiz, but IMO if you disable Compiz this way, and re-enable it by re-selecting the setting (probably Extra) that you had before, it should restore the same settings that you had.

---

### Post by riskbreaker927 on 2008-04-03
acoustibop, in my experience, using the appearance options menu does get rid of your compiz settings. My method of getting rid of compiz when necessary is ```
metacity --replace
``` and then to bring it back ```
compiz --replace
```

---

### Post by itix on 2008-04-03
Thank you. Works like a charm.
You see, acoustibop; I have CCSM which allow me to configure compiz individually to my liking. If i choose none in appearance settings, I have to go to CCSM and reset all my changes but the cool terminal codes I got from riskbreaker I don't have to do that.

Off to my other thread and mark it as solved.

---

### Post by doorknob60 on 2008-04-05
Thanks, FranMichaels! Setting it to 48000 was the only way I could even get sound to come out of it after over an hour of Googling and messing with settings :D

---

### Post by divadotrebla on 2008-04-26
> **Cresho said:**
> hi!

I spent tons of hours getting zsnes and gxmame running.  All I did to get these two running in hardy heron was to install libsdl1.2debian-all and run "zsnes -ad sdl" in the terminal.  I have no problems.

This works here too.

Thanks all the people who is responding in this post.

---

### Post by camurgo on 2008-04-28
> **divadotrebla said:**
> This works here too.

Thanks all the people who is responding in this post.


Here too. Although it took a reboot to kick in =]
Thanks everyone.

---

### Post by monroetransfer on 2009-10-31
I ran ```
sudo aptitude install libsdl1.2debian-oss
```, changed the audio sample rate to 48000 Hz and then ran the emulator with ```
zsnes -ad sdl
``` and the alsa error "underrun at least 0ms" (or something like that) ceased. The sound now plays perfectly. I'm on linux mint 6 fluxbox community ce, which is loosely based on intrepid. So if you're running intrepid, this might be useful info.

---

### Post by Woojoo//.deb on 2009-11-02
there was a similar thread a while ago in which self compiling was the solution. that time i made a build for the same reason for my laptop as and it worked just fine ^^ [zsnes_1.51b-0_i386.deb]("http://bamn.de/downloads/zsnes_1.51b-0_i386.deb")
this is my build you can try to download and install the .deb it should work but didnt rebuild in months!! so be warned!! its on your own risk to use that build. but i dont think it breaks anything but just in case this is not an offical build.


Edit: this is a link to the old thread with similar problems [link]("http://ubuntuforums.org/showthread.php?t=1069941") the .deb got only normal alsa oss support stuff and will not work if you use Pulseaudio as audio server

---

### Post by hellocatfood on 2009-11-15
Running this code worked best for me
```
zsnes -ad sdl
```

---

### Post by Wolf-Jakob Gratz on 2009-11-18
> **riskbreaker927 said:**
> To get rid of the garbled sound, type:```
sudo apt-get install libsdl1.2debian-oss
```It may get rid of some other packages, but they are not that necessary. Or weren't in my case. Anyway, try ZSNES again and it should work.

This worked for me, thanks

---

### Post by tristan8276 on 2009-12-22
I had the same problem, and found that using   sudo zsnes -s -ad oss   worked well for me.

---

