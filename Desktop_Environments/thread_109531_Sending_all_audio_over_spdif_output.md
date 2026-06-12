---
title: "Sending *all* audio over spdif output"
date: 2005-12-28
forum: Desktop Environments
---

### Post by pagingmrherman on 2005-12-28
Hi, I've got ubuntu 5.10 installed on a PC with an SBLive! Value card (CT4832) but I can't for the life of me figure out how to get linux to send out audio over the S/PDIF connector.   I have a DD/DTS receiver that will handle raw PCM with no problems.  This box used to have winXP installed on it and I never used to have to use the analog connectors. 
AVI files encoded w/ dolby digital audio work fine when I use mplayer, xine, totem, etc. and set the audio to AC3 passthrough.
Has anybody ever got something like mp3 player software to send a pcm stream over the spdif connector???

Thx in adavance
PW

---

### Post by IRJustman on 2006-05-27
[QUOTE=pagingmrherman]Hi, I've got ubuntu 5.10 installed on a PC with an SBLive! Value card (CT4832) but I can't for the life of me figure out how to get linux to send out audio over the S/PDIF connector.   I have a DD/DTS receiver that will handle raw PCM with no problems.  This box used to have winXP installed on it and I never used to have to use the analog connectors. 
AVI files encoded w/ dolby digital audio work fine when I use mplayer, xine, totem, etc. and set the audio to AC3 passthrough.
Has anybody ever got something like mp3 player software to send a pcm stream over the spdif connector???

Thx in adavance
PW[/QUOTE]

In my case, I use an SBAudigy and I can only get Dolby Digital to work.  PCM used to work, but it quit working for whatever reason.

While I was servicing my Windows machine, since it has exactly the same card, I swapped cards (its S/PDIF port was tested with the amp a night or so prior and was working), and I had the same result.  No joy.  However, Dolby Digital works just fine.

Thoughts?

--Ian.

---

### Post by superm1 on 2006-06-02
This same thing just happened to my myth box.  PCM was being sent automatically over SPDIF, and then all of a sudden stopped working.  I fumble with all IEC958 related mixers to no solution.  I try in windows and it works first try.  I'm not sure what happened...

---

### Post by Osamabingandhi on 2006-06-04
Same problem for me. All sound worked fine till i turned on the ac3-passthrough, now i only have dolby digital, no mp3's.](*,) 

How about reinstall all alsa drivers, maybe that is the only way. But it would be nice to have both dolby digital and ordinary sound from the spdif output....:rolleyes:

---

### Post by superm1 on 2006-06-04
Well I came up with a solution:

Use an .asoundrc like this:

```
cat mythtv@davey:~$ cat .asoundrc
pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
        }
}

```


Works for me in all the other stuff I do on SPDIF, mupen64, zsnes. :)

---

### Post by Osamabingandhi on 2006-06-06
how do you manage this .asoundrc file? Where do you put it, which folder? is that myth@etc your login-name? How do you enable it?

If this is the answer to the spdif problem it would be extremly nice. Been without sound for a couple of days, nice with dolby digital but i like music too. Soon i will reinstall....but then i don't have spdif:( Problems problems

---

### Post by superm1 on 2006-06-06
Sorry, didn't realize that was ambiguous

The .asoundrc file goes in your home directory.  If you want it to be systemwide, there is a file in /etc that you can change too, but I don't know it offhand.

Odds are you don't have a .asoundrc to start, to you will have to make it.

The exact contents should be this:

```
 pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
        }
}
```

---

### Post by Osamabingandhi on 2006-06-06
ok, thanks for the fast reply.:)  I have made and edited the file and will restart to try it out. I changed the 48000 value to 44000 cause i think my card only handles 44khz....I cross my fingers and hope it works(my dolby sound is gone too for some reson:(  )

---

### Post by superm1 on 2006-06-06
[quote=Osamabingandhi]ok, thanks for the fast reply.:)  I have made and edited the file and will restart to try it out. I changed the 48000 value to 44000 cause i think my card only handles 44khz....I cross my fingers and hope it works(my dolby sound is gone too for some reson:(  )[/quote]

As for the 44khz, you might want to double check with that.  My sound all sounded quite distorted at 44.1 which I Think is the default.  

You shouldnt need to restart for the effect to happen I don't think...

---

### Post by Osamabingandhi on 2006-06-06
i have a quite old soundblaster live 5.1 and quite certain it hasn't more than 44,1 khz. But the script helped to bring back my dolby sound but only for a while, until i tried to play a mp3 sound. After that no sound again.

Got any other ide, its so frustrating not to be able to use sound. Soon i will go out and buy the cheapest soundcard and see if that works instead.

Thank you for trying to help, it's very nice of you:)

---

### Post by Osamabingandhi on 2006-06-06
i thougt of something, maybe the slave plug thingy should be changed for my card. Got no idea what to exange it though...

---

### Post by superm1 on 2006-06-06
Well you can try iec958 instead if your card has that.

---

### Post by Osamabingandhi on 2006-06-06
don't really knows what name the spdif 3,5mm plug has:confused:  What i am attempting now is to download the lastest beta drivers that alsa has and try them. But this i quite hard to do....hopefully this will work. I will try the script you have and try it one more time then i give up for tonight. This is giving me stress like the days with windows98....](*,)

---

### Post by superm1 on 2006-06-07
If I have learned anything about betas over the years -

If you had it working right using stable software, and then it stopped working suddenly - the beta won't necessarily solve your problem.  Usually something related to the setup has gone wrong.

Now if you put that .asoundrc into your home directory, what apps are you trying to play stuff with now?  If its anything using OSS, I doubt it will work.  Anything using alsa?  If thats the case, then you should make sure audio is directed to the ALSA device "default".  This will redirect to the SPDIF output using the .asoundrc I provided.  And you say that DD works and then stops working?  What apps are you doing DD with?  What is the device configured for there?

For my living room setup, I have 2 major apps that use DD.
Mythfrontend is configured to use ALSA:spdif and AC3 passthru is enabled.
Xine-UI is just configured to opt to use pass thru.

I play zsnes & mupen64, and both are configured to just use the defaut audio device.

Now the thing here is that I never have two apps fighting for spdif output.  I don't use any app or even gnome for that matter that would even think about using esd.  Everything is launched directly from myth, so only one app will try to use audio at a time.

---

### Post by Osamabingandhi on 2006-06-08
I think i may have come up with a solution to my problem. I have not tried this yet so it may or may not be the solution. When i had just installed ubuntu sound worked through the spdif plug with PCM with no problem until i used totem player and enabled AC3 pass through, and therefore dolby digital works too. The conclusion is that totem player is the devil :twisted: and corrupted my soundsettings...

As you say superm1 is that to play two sources that compete over the spdif plug may corrupt things, or as i have come to believe that it is the totem player. To use totem player and activate this AC3 pass through to get dolby digital may be the problem. I will make a fresh install and uninstall totem player and install xing-player or/and myth-end. I liked the zoom thingy in totem player, but i guess that function is in other programs. I hope i can make a fresh install today...and see i my faith in the devil proves right :)

---

### Post by pyrforos on 2007-07-05
hi guys.My problem is similar...I have sound but only from xmms amarok mplayer vlc .
My tvtime , ALL SYSTEM SOUNDS , mercyry etc are muted..Any ideas?( i im using the .asoundrc 

```
 pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
        }
}
```

---

### Post by machs_fuel42 on 2007-07-15
thought that i'd mention that this solution worked for my ALC650 / VIA 8235 build into my asus mobo.  IEC958 and IEC958 output is on, IEC playback is 100 %.

Amarok and totem now route through spdif, totem sends whatever channels the video has..

VLC and Mplayer don't seem to work, will have to look into that later.

---

### Post by AndrewWalker on 2007-09-01
I'm having the same problem with identical machines! I built one for a mate, my one works fine but his only outputs dts or dolby digital to spdif, everything else is analog only and nothing from the optical output. I've even copied my config settings over to no avail!

---

### Post by daqron on 2007-09-03
There is a very good tutorial on this **[here]("http://forum.doom9.org/showthread.php?s=&postid=628821#post628821")** (see in particular Part 8 #5 - "How can I play AC3/DTS over S/PDIF (digital) output?"). This helped me get my Turtle Beach Montego DDL soundcard to work properly in Ubuntu 7.04 using the alsamixer utility. By default, the S/PDIF (optical) output was muted. There doesn't seem to be anyplace in the GUI interface to control that particular output, which was labeled "IEC958" but the command line alsamixer tool is able to turn it on and off. Once enabled, sound from all sources was piped, in all its glory, through the optical output.

Note that while the alsamixer should be a standard tool available in Ubuntu, some of the other resources mentioned in the tutorial, including alsaconf, do not appear to be present. Perhaps the available tools vary by distribution. In any case, alsaconf wasn't required for S/PDIF functionality on my box.

Hope this helps!

---

### Post by superm1 on 2007-09-12
> **daqron said:**
> There is a very good tutorial on this **[here]("http://forum.doom9.org/showthread.php?s=&postid=628821#post628821")** (see in particular Part 8 #5 - "How can I play AC3/DTS over S/PDIF (digital) output?"). This helped me get my Turtle Beach Montego DDL soundcard to work properly in Ubuntu 7.04 using the alsamixer utility. By default, the S/PDIF (optical) output was muted. There doesn't seem to be anyplace in the GUI interface to control that particular output, which was labeled "IEC958" but the command line alsamixer tool is able to turn it on and off. Once enabled, sound from all sources was piped, in all its glory, through the optical output.

Note that while the alsamixer should be a standard tool available in Ubuntu, some of the other resources mentioned in the tutorial, including alsaconf, do not appear to be present. Perhaps the available tools vary by distribution. In any case, alsaconf wasn't required for S/PDIF functionality on my box.

Hope this helps!
Well it is present in the normal gnome gui too.  You just need to turn on the additional mixers.  Go to Edit-Preferences.

---

