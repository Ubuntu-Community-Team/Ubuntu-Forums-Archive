---
title: "weird zsnes sound problem"
date: 2007-12-25
forum: Gaming &amp; Leisure
---

### Post by MEGAMANULTIMATE on 2007-12-25
For some reason, the sound in ZSNES sounds incredibly clear for maybe a few minutes during play. But suddenly, it'll crackle and sink into cacophony until I push the ESC key and bring up the main menu. I tried a suggestion on another thread that had me download a libdeb-oss (horribly misspelled) package that would presumably get rid of the problem. I'm still not out of the woods yet, though. Any suggestions? I'm running a Dell M1210 with Feisty. In any case, don't even bother with me if you're trying to enjoy your holiday. Thanks!

---

### Post by jan quark on 2007-12-25
had the same sound problems like you. but... nothing really helped. Then I messed up something more important than the ZSNES and had to do  a fresh re-install.:lolflag:

No problems since then. When I find out more will post it here.

---

### Post by P235 on 2007-12-25
I too share the same problem with sound quality with zsnes and simply muted the volume.  But now I realize that the sound no longer works with zsnes either.  I get this message from the terminal.

```
ALSA lib pcm_dmix.c:914:(snd_pcm_dmix_open) unable to open slave
Sound init failed!
```

Maybe a restart will solve the problem, but my uptime!

---

### Post by disturbedite on 2007-12-25
this is a known problem (bug?) with zsnes when the user has an onboard sound card (chip).  do you guys happen to have onboard sound?

---

### Post by MEGAMANULTIMATE on 2007-12-25
If by onboard sound card, you mean a built in sound card (SigmaTel Stac9221), then yes. I also have Logitech V20 speakers in one of the USB ports. Is there any way for me to make it so that the sound comes from my speakers instead?

---

### Post by disturbedite on 2007-12-26
"built-in" is the non-technical term, so to speak, onboard means the same thing tho.

i compiled zsnes from svn and was getting the same problem, (cuz of my onboard sound card), but when i uninstalled it and reinstalled the zsnes from the repo, the problem was gone.  so apparently there is a patch or something that is applied in the repo package of zsnes that fixes the problem, at least for me.  so i stick with that version.

---

### Post by MEGAMANULTIMATE on 2007-12-26
What version is the repos version that you have? I'm pretty sure I had 1.51 downloaded from a .deb file off the internet, but Synaptic still shows that as the latest version.

EDIT: This is ridiculous. I tried reinstalling the synaptic version, and now every time I try to change the video resolution, the program disappears completely. What's up with this?

EDIT II: Now I've discovered that I can't even boot up games without the program disappearing. I don't know what I did wrong. I did try to compile 1.42 from source, following the forum's instructions at zsnes.com. It didn't work though, and now this is happening? Help!

EDIT III: Nevermind. Fixed it. Sorry for that.

---

### Post by FranMichaels on 2007-12-26
> **MEGAMANULTIMATE said:**
> For some reason, the sound in ZSNES sounds incredibly clear for maybe a few minutes during play. But suddenly, it'll crackle and sink into cacophony until I push the ESC key and bring up the main menu. I tried a suggestion on another thread that had me download a libdeb-oss (horribly misspelled) package that would presumably get rid of the problem. I'm still not out of the woods yet, though. Any suggestions? I'm running a Dell M1210 with Feisty. In any case, don't even bother with me if you're trying to enjoy your holiday. Thanks!

I posted something about this on my blog (which I almost never post to ;) )

"If you experience any sound issues.

gedit ~/.zsnes/zsnesl.cfg

On line 178, change "auto" to "sdl"
libAoDriver="sdl"

Close the file.
The other settings can be changed from the GUI under Config -> Sound.
48000HZ with High Quality low pass filtering (you'll notice if you have a sub-woofer.)"

Try that :KS

P.S. This is for zsnes 1.51 compiled with libao support. There are many threads on it, or you can grab a deb. Search around. Good luck!

---

### Post by MEGAMANULTIMATE on 2007-12-26
Thanks for the help. Sorry for this newb question, but how do I know if my version's compiled with libao?

EDIT: I checked the file like you suggested, but what was brought up didn't even have 178 lines. Is there something else I have to do?

---

### Post by FranMichaels on 2007-12-26
> **MEGAMANULTIMATE said:**
> Thanks for the help. Sorry for this newb question, but how do I know if my version's compiled with libao?

Good question, I compiled it in myself (it's easy when you've done it at least once ;) You should find a few threads with step by step if you are interested)

I looked around (zsnes -> about etc...), nothing seems to mention libao support in the details, 

Do you have the option libao in the config file? Did changing the sound driver help?

---

### Post by MEGAMANULTIMATE on 2007-12-26
I checked the file, and there seemed to be no option to change the sound driver. It was only a hundred lines long, and no more. Maybe my version's gimped or something....

---

### Post by FranMichaels on 2007-12-27
> **MEGAMANULTIMATE said:**
> I checked the file, and there seemed to be no option to change the sound driver. It was only a hundred lines long, and no more. Maybe my version's gimped or something....

No libao then I guess.

[http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

---

### Post by acoustibop on 2007-12-27
Well, looking in zsnesl.cfg I see:
```
;  ----
; -- Sound --
;  ----

; libAO driver to use. Use zsnes --help to see valid list.
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="auto"
```
and then doing zsnes --help I get:
```
~$ zsnes --help
Usage : zsnes [-d,-f #, ... ] <filename.sfc>
   Eg : zsnes -s -r 2 game.sfc

  -1 #/-2 #   Select Player 1/2 Input :
                0 = None       1 = Keyboard/Gamepad
  -ad <>  Select Audio Driver :
                  auto = Automatically select output
                  null = Null output
                   nas = NAS output
                   oss = OSS audio driver output 
                  alsa = Advanced Linux Sound Architecture (ALSA) output
                   esd = ESounD output
                 pulse = PulseAudio Output
                  arts = aRts output
                   sdl = Simple DirectMedia Layer output
  -dd     Disable sound SPC700/DSP emulation which also disables sound output
  -ds     Disable sound output
```
etc.

---

### Post by &#12465;&#12452;&#12488; on 2007-12-27
Had to fight myself in order to minimize Chrono Trigger now, because I've been having such a good time gaming after getting rid of the sound problems! It was thanks to this thread that I sorted things out anyway, so I should tell what I did.

One week ago, I also made a thread about this problem.
[http://ubuntuforums.org/showthread.php?t=643760](http://ubuntuforums.org/showthread.php?t=643760)

At that time, I mistook SDL for causing the problem, but thanks to this thread, I was made aware of them having switched to using libao! (Yeah, the gutsy ZSNES build is compiled with libao support.) I tried a lot of output methods, alsa, oss, esd, even pulseaudio, but it kept on crackling anyway.

That was until I switched to SDL output. Playback's perfect now, and that's about freakin' time too. Don't you ever try ruining my game music appreciation again!!

**Quick fix:**
Start ZSNES from a terminal with the command "zsnes -ad sdl" to select SDL audio, hopefully that'll do it.


(I should have read FranMichaels's posts more carefully before trying everything else but sdl)

---

### Post by MEGAMANULTIMATE on 2007-12-27
Oddly enough, sdl doesn't work well for me. I switched the output to 'oss' and now it works okay...I hope everybody else will find happiness here, as well.

---

### Post by disturbedite on 2007-12-28
when i was compiling zsnes from svn i had libao support (which means it is enabled by default).  perhaps this was my problem...

---

### Post by liquidypoo on 2008-01-18
> **FranMichaels said:**
> I posted something about this on my blog (which I almost never post to ;) )

"If you experience any sound issues.

gedit ~/.zsnes/zsnesl.cfg

On line 178, change "auto" to "sdl"
libAoDriver="sdl"

Close the file.
The other settings can be changed from the GUI under Config -> Sound.
48000HZ with High Quality low pass filtering (you'll notice if you have a sub-woofer.)"

Try that :KS

P.S. This is for zsnes 1.51 compiled with libao support. There are many threads on it, or you can grab a deb. Search around. Good luck!

I finally got fed up with the sound acting like this and was about to post a thread, but this one's still fairly new.

Anyway, when I changed the libAoDriver to sdl, the sound quality went down considerably.  It wasn't choppy at all, but it was really crackly.  Are there any other options, or should I just keep dealing with it?

By the way, if there're any people in the same boat as myself, another way to fix the sound is to just tap the turbo key (or whatever you want to call it, it's the "~" key for me).

---

### Post by agds on 2008-03-08
> **&#12465 said:**
> Had to fight myself in order to minimize Chrono Trigger now, because I've been having such a good time gaming after getting rid of the sound problems! It was thanks to this thread that I sorted things out anyway, so I should tell what I did.

One week ago, I also made a thread about this problem.
[http://ubuntuforums.org/showthread.php?t=643760](http://ubuntuforums.org/showthread.php?t=643760)

At that time, I mistook SDL for causing the problem, but thanks to this thread, I was made aware of them having switched to using libao! (Yeah, the gutsy ZSNES build is compiled with libao support.) I tried a lot of output methods, alsa, oss, esd, even pulseaudio, but it kept on crackling anyway.

That was until I switched to SDL output. Playback's perfect now, and that's about freakin' time too. Don't you ever try ruining my game music appreciation again!!

**Quick fix:**
Start ZSNES from a terminal with the command "zsnes -ad sdl" to select SDL audio, hopefully that'll do it.


(I should have read FranMichaels's posts more carefully before trying everything else but sdl)

I confirm this quick fix worked beautifully on a Dell GX270 with AC97 integrated sound.  Now I also cannot tear myself away from *Chrono Trigger*.

---

### Post by acoustibop on 2008-03-08
The "zsnes -ad sdl" command didn't make any difference for me.  What did work was editing the /.zsnes/zsnesl.cfg file so that the libAO selection line reads libAoDriver="sdl"

It could be a good idea to try the various options (see my post above) until you find one that works satisfactorily, if the methods here don't work.

---

### Post by agds on 2008-03-09
Okay, so this is getting weird.

Yesterday starting from the command line with 'zsnes -ad sdl &' worked fine.  Today the sound quality was much worse, even though I was using the same command.

So I tried 'zsnes -ad alsa &' and got excellent results.  This is strange, since ALSA sounded intolerably choppy in the past.

I did a dist-upgrade last night, so maybe that's the culprit.

---

### Post by grossaffe on 2008-03-09
i also had the sound problem with ZSNES, it got to the point where i couldn't stand it anymore.  fortunately, by the time that happened, teh SNES9x with GTK and OpenGL came out.  Once I installed that, i haven't looked back.

---

### Post by sfx on 2008-06-26
I just disabled the echo effect in the zsnesl.cfg file, and that got rid of my crackling problems.

---

### Post by farrell2k on 2008-06-26
On every machine I've inslled Zsnes, which is now 4, this proplem has been dealt with by setting the playback frequency to 48KHz, then restarting the application.  No driver switching, or messing with code required.

---

### Post by hawksbill on 2008-09-12
Changing the sample rate worked :) For some reason when I switch from any sample rating to 8000hz quit then change the sample rating back up to anything sound works fine. But just keeping it at 48000hz did the trick.

---

### Post by bigblackpapa on 2009-01-10
I compiled my zsnes because there is no release yet for the Atom processor. I was getting weird and annoying sound effects, but I was able to play. I finally found the solution so I hope it will help someone.

Solution:
1. install the following packages with Synaptic Package Manager (sudo synaptic): libsdl-mixer1.2-dev libsdl-gfx1.2-dev (may be useful as well)
2. recompile

Now the sound is perfect, same as in a real Snes :guitar: !!

---

