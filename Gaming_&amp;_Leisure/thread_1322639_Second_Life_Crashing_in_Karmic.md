---
title: "Second Life Crashing in Karmic"
date: 2009-11-11
forum: Gaming &amp; Leisure
---

### Post by Naiki Muliaina on 2009-11-11
Lotsa folk seem to be suffering from continuous crashes and sound problems in Karmic 64bit. It fizzles, crackles, gets worse, then the game crashes. PC specs are:

AMD 6000+ dual core (3.1gz i think)
Nvidia 9800gtx
8GB Black Dragon Ram
Gigabyte GA-MA790X Motherboard - [Linkage]("https://www.aria.co.uk/Products/Components/Motherboards/Socket+AM2+(AMD)/Gigabyte+GA-MA790X-DS4+AMD+790X+Socket+AM2+Motherboard+?productId=32061")

I have tried the SDL / Urban terror fix and it hasnt worked for me properly on SL.

Does anyone have any suggestions?

---

### Post by RabidWeezle on 2009-11-11
Haven't tried yet, but have you tried with a 3rd party viewer (omvviewer has an ubuntu ppa). Will check it out when I get home though.

--EDIT

Since this is the higher post: The answer is you need to disable openal audio in the secondlife script:

```
gedit secondlife
```

then uncomment this line so it looks like so:

```
export LL_BAD_OPENAL_DRIVER=x
```

---

### Post by Naiki Muliaina on 2009-11-11
> **RabidWeezle said:**
> Haven't tried yet, but have you tried with a 3rd party viewer (omvviewer has an ubuntu ppa). Will check it out when I get home though.

Good point, should also add, OMVViewer (my rock in the past) doesnt have a Karmic repo yet. I have used Snowglobe (from the playdeb repo), and the stand alone GreenLife (emerald) and Official (downloaded direct from SL's website) versions. Its the same on all of them.

---

### Post by VertexPusher on 2009-11-11
I use SL a lot in Karmic 64bit. What kind of crashes are you experiencing?

---

### Post by RabidWeezle on 2009-11-11
I will take a look at it when I get out from work in about 3.5 hours, see if I can make it work somehow. I know you can edit some settings in the secondlife startup script, perhaps there's something we can do in there to make it work. I'm also having popping/fizzling noises from other games aswell, complaining about how it can't connect to the pulseaudio server, I'm guessing it's the same issue of sorts.

---

### Post by Naiki Muliaina on 2009-11-11
I always crash on exit, quit the game and it freezes. I have to kill it to close it. It also randomly freezes during play. Only way out is to kill it.

> **RabidWeezle said:**
> complaining about how it can't connect to the pulseaudio server, I'm guessing it's the same issue of sorts.

Hmm perhaps i should try gutting everything Pulse from my PC and fill it up with Alsa?

---

### Post by RabidWeezle on 2009-11-11
have you tried the usual deletion of ~/.secondlife (if karmic was upgraded rather than a clean wipe/install)

--edit:
With Karmic, I wouldn't try removing pulseaudio, since it seems to be tied into the distro hardcore now, if you can just make it work with pulseaudio, you would probably be better off.

---

### Post by Naiki Muliaina on 2009-11-11
> **RabidWeezle said:**
> have you tried the usual deletion of ~/.secondlife (if karmic was upgraded rather than a clean wipe/install)

--edit:
With Karmic, I wouldn't try removing pulseaudio, since it seems to be tied into the distro hardcore now

Ahhh bugger, always had more success with ALSA than Pulse...  It was a clean install, not an upgrade.

---

### Post by RabidWeezle on 2009-11-11
> **Naiki Muliaina said:**
> Ahhh bugger, always had more success with ALSA than Pulse...  It was a clean install, not an upgrade.

I hear ya, before I used kubuntu on jaunty, and I wasn't tied into pulse at all, and SL/Skype/other games worked like a dream. But according to the pulseaudio guys it's not so much to be blamed on pulseaudio but ubuntu's dodgy implimentation of it.

---

### Post by Naiki Muliaina on 2009-11-11
Arf! Ah well, thanks for the response dude! If i have any advancements meself ill post them up here :)

---

### Post by RabidWeezle on 2009-11-11
Trying different drivers in the secondlife script, (using snowglobe) so far no dice, will keep trying...

I made a video on youtube showing the outputs going batty on karmic:
[http://www.youtube.com/watch?v=FopDUiJjjDE](http://www.youtube.com/watch?v=FopDUiJjjDE)

Got it working:
gedit /path/to/snowglobe (or whatever client you use)

uncomment the line to disable openal:

```
export LL_BAD_OPENAL_DRIVER=x
```

---

### Post by Naiki Muliaina on 2009-11-11
Ooo cool ty!

Cant check it right now, doing a run of stand up comedy around SL, but ty, will check it when im done :)

---

### Post by RabidWeezle on 2009-11-11
> **Naiki Muliaina said:**
> Ooo cool ty!

Cant check it right now, doing a run of stand up comedy around SL, but ty, will check it when im done :)

just found a better fix even, make a ~/.openalrc and stick in it:

```

(define devices '(alsa))
(define alsa-device "pulse")

```

---EDIT scratch that, this doesn't work :(

---

### Post by VertexPusher on 2009-11-11
> **RabidWeezle said:**
> But according to the pulseaudio guys it's not so much to be blamed on pulseaudio but ubuntu's dodgy implimentation of it.
If that was true, Fedora's implementation should be much better because it is maintained by the PulseAudio guys themselves. But Fedora users are reporting the same sound issues as everyone else. Check out their forums.

---

### Post by Naiki Muliaina on 2009-11-12
> **RabidWeezle said:**
> 
gedit /path/to/snowglobe (or whatever client you use)

uncomment the line to disable openal:

```
export LL_BAD_OPENAL_DRIVER=x
```

This one works fine for me, turns of music media, but faaaar better than crashing all the time ^^

---

### Post by VertexPusher on 2009-11-12
If you remove Pulse, the crashes will stop too, but you will keep media playback.

---

### Post by RabidWeezle on 2009-11-13
with all gstreamer/vlc/mplayer stuff installed, I still get streaming music in snowglobe with pulse

---

### Post by Naiki Muliaina on 2009-11-13
Hmm gonna have to have another poke at it tonight... Thankies again for the replys :)

---

### Post by logomancer on 2009-11-13
Switching to FMOD (what uncommenting that line does) does *not* work for me; I get no sound at all.

My issue is similar -- CPU usage jumped significantly after I upgraded from 9.04 to 9.10. I started hearing distorted sound, and then no sound at all after a few minutes. Renaming /path/to/SL/lib/libopenal.so.1 to something else extended the time, but entering an area with a lot of avatars caused the CPU to spike again. Enabling voice seems to make things worse.

I am, frankly, at a loss as to what to do about this. I would guess that the problem lies in how SL (and the Vivox voice binary) uses OpenAL and/or pulseaudio. However, lacking sufficient knowledge of OpenAL and the SL codebase, I have no idea how to fix it.

---

### Post by logomancer on 2009-11-14
As it happens, there is a fix for the behavior I presented in my last post.

The problem lies with the OpenAL library included with the official SL viewer; it is quite old, and has limited Pulseaudio support. Removing or renaming the included library -- thus forcing SL to use libopenal 1.8.466, which is included with Ubuntu -- is somewhat of an improvement. Even with this method, issues still exist with the voice client, including increased CPU usage and outgoing voice transmissions having a sped-up "chipmunk" quality to them. From [this post]("http://old.nabble.com/Recording-strangeness-with-OpenAL-Soft-1.8.466-td24293767.html"), it seems that there was a bug in libopenal 1.8.466 that caused this to happen. It has been fixed in later versions, but they have not been included by default in Ubuntu 9.10.

So, in order to fix the SL issues, we need a newer version of libopenal. Fortunately, this is quite possible by compiling a new version from source provided on the OpenAL website.

First, we need to satisfy dependencies. Type the following command into a terminal:
```
$ sudo aptitude install cmake libasound2-dev libpulse-dev
```

Next, we need to download the latest source release from the OpenAL website. As of this post, it was 1.10.622:
```
$ wget http://kcat.strangesoft.net/openal-releases/openal-soft-1.10.622.tar.bz2
```

Extract the bzipped tar file:
```
$ tar xvjf openal-soft-1.10.622.tar.bz2
```

Change to the build directory you just made:
```
$ cd openal-soft-1.10.622/build
```

Run CMake to configure the makefiles:
```
$ cmake ..
```

Note: At this point, there should be some text here, and at the end should be something like this:
```
-- Building OpenAL with support for the following backends:
--      ALSA, OSS, PulseAudio, WaveFile
```

**Make sure that ALSA and PulseAudio show up there.** If you didn't, it means you didn't install the dependencies properly; execute the first command of this HOWTO and try again.

After that, make the package:
```
$ make
```

If all goes well, you should have libopenal.so.1.10.622 in the directory. Rename the old libopenal in the SL viewer directory:
```
$ mv /path/to/secondlife/lib/libopenal.so.1 /path/to/secondlife/lib/libopenal.so.1.old
```

And replace it with the new one:
```
$ cp libopenal.so.1.10.622 /path/to/secondlife/lib/libopenal.so.1
```

You're done!

---

### Post by Milleman on 2009-11-22
> **logomancer said:**
> As it happens, there is a fix for the behavior I presented in my last post.

The problem lies with the OpenAL library included with the official SL viewer; it is quite old, and has limited Pulseaudio support. Removing or renaming the included library -- thus forcing SL to use libopenal 1.8.466, which is included with Ubuntu -- is somewhat of an improvement. Even with this method, issues still exist with the voice client, including increased CPU usage and outgoing voice transmissions having a sped-up "chipmunk" quality to them. From [this post]("http://old.nabble.com/Recording-strangeness-with-OpenAL-Soft-1.8.466-td24293767.html"), it seems that there was a bug in libopenal 1.8.466 that caused this to happen. It has been fixed in later versions, but they have not been included by default in Ubuntu 9.10.

So, in order to fix the SL issues, we need a newer version of libopenal. Fortunately, this is quite possible by compiling a new version from source provided on the OpenAL website.

First, we need to satisfy dependencies. Type the following command into a terminal:
```
$ sudo aptitude install cmake libasound2-dev libpulse-dev
```

Next, we need to download the latest source release from the OpenAL website. As of this post, it was 1.10.622:
```
$ wget http://kcat.strangesoft.net/openal-releases/openal-soft-1.10.622.tar.bz2
```

Extract the bzipped tar file:
```
$ tar xvjf openal-soft-1.10.622.tar.bz2
```

Change to the build directory you just made:
```
$ cd openal-soft-1.10.622/build
```

Run CMake to configure the makefiles:
```
$ cmake ..
```

Note: At this point, there should be some text here, and at the end should be something like this:
```
-- Building OpenAL with support for the following backends:
--      ALSA, OSS, PulseAudio, WaveFile
```

**Make sure that ALSA and PulseAudio show up there.** If you didn't, it means you didn't install the dependencies properly; execute the first command of this HOWTO and try again.

After that, make the package:
```
$ make
```

If all goes well, you should have libopenal.so.1.10.622 in the directory. Rename the old libopenal in the SL viewer directory:
```
$ mv /path/to/secondlife/lib/libopenal.so.1 /path/to/secondlife/lib/libopenal.so.1.old
```

And replace it with the new one:
```
$ cp libopenal.so.1.10.622 /path/to/secondlife/lib/libopenal.so.1
```

You're done!



Tried the library compiling above, but no luck. The Second Life client sound works for 2-3 minutes or so, then the sound disappears. Just like before. Exit the Second Life client results in a stuck client window which has to be killed in order to go away. :(

Running Karmic 64 bit...

---

### Post by bbeatle on 2009-11-28
A solution that works for me can be found [here]("http://gersar.netsons.org/?p=70"). It's in italian but my translator works fine

---

### Post by Uikku on 2009-12-01
> **bbeatle said:**
> A solution that works for me can be found [here]("http://gersar.netsons.org/?p=70"). It's in italian but my translator works fine

That indeed did the trick for me too. Sound working and no crashing on exit. Even though Google translator's English was even more peculiar than mine... Thanks!

---

### Post by kikiadjhka1223 on 2009-12-01
Thanks for that awesome description!  Have fun at Houston!

---

### Post by chris282 on 2009-12-05
Hi logomancer,

Hope you're still out there.  First up I should admit that I'm very new to Ubuntu, and easily confused.  That said, I did find your instructions quite excellently written and followable, and I've had a lot to compare them with over the past week.

However...  I've got as far as the penultimate step:
[I]
    If all goes well, you should have libopenal.so.1.10.622 in the directory. Rename the old libopenal in the SL viewer directory:

    $ mv /path/to/secondlife/lib/libopenal.so.1 /path/to/secondlife/lib/libopenal.so.1.old[/I]

And I've come up with the message "mv: cannot stat '/path/to/secondlife/lib/libopenal.so.1': No such file or directory"

I've tried what I thought would be the logical step of renaming libopenal.so.1 in Nautilus (? - file manager), and copying and pasting the new libopenal.so.1 into the folder, but it shows an icon with a little lock on it, and tells me "This link cannot be used, because its target "libopenal.so.1.10.622" doesn't exist."

Any chance you might be able to suggest where I'm going wrong?

Hopeful thanks,

- Chris.

---

### Post by Sahkolihaa on 2009-12-06
Luckily Linden Lab are actually working on this issue. I posted on PJIRA about it and the issue actually got imported into LL's own JIRA.

Here's the issue: [http://jira.secondlife.com/browse/VWR-16092](http://jira.secondlife.com/browse/VWR-16092)

I've switched to Xubuntu 32-bit Karmic since it lacks PulseAudio and after installing OpenAL from the repository and re-naming the one that comes with SL, I have no issues with the inworld sounds anymore. Voice still acts up but I blame Vivox for poor Linux support.

---

### Post by chris282 on 2009-12-06
Persistence trumps incompetence.  I've successfully completed the final step, but still no joy.  Glad to hear the problem's being looked at, Sahkolihaa, but I'd quite like to give Gerado's solution a try since it seems to have done the trick for Uikku and bbeatle.

Copying the translation here:
[I]
All those who like me playing on Second Life will surely have had some annoying problems Upgrading Ubuntu to version 9.10.  The first is the audio: at a certain point, the reproduction of ambient sound, and even those systems, including those that you can hear the reception of the IM, even if it still crashes can play audio streams like music you can listen to different land. A second problem concerns the stage of logging, in which the client blocks preventing that window closes. A third problem I encountered about the impossibility of using the voice to communicate through our voice with other residents.

All these troubles are caused by the incompatibility of the boring sound system integrated into Ubuntu Karmic the Second Life client who was working perfectly but in Jaunty. A solution to all problems that I mentioned above is to copy the directory ${SECONDLIFE_INSTALL_DIR}/lib a library which I proceeded to import from my old Jaunty and I proceeded to pack the archive that you can download from [[COLOR=Blue]here[/COLOR].]("http://dl.dropbox.com/u/1111567/Archivio_Sito_Web/SLCompatLib.tar.gz") Once extracted the compressed files in the directory mentioned in the secondlife return to function effectively.[/I] 

This seems to rely on having had Jaunty previously installed (I think), and I'm a first time user of Karmic, so I'm at a bit of a loss.  Can anyone help?

Many thanks,

- Chris

---

### Post by chris282 on 2009-12-06
Quick update here:

Had a look at the SL forums and found the following: [http://forums.secondlife.com/showthread.php?p=2637881#post2637881](http://forums.secondlife.com/showthread.php?p=2637881#post2637881)

I've downloaded the GStreamer plugins, and now have sound.  Happy days.

Cheers all,

- Chris.

---

### Post by aaricia on 2010-01-24
Hello,

I have followed this discussion, but I couldn found the solution to my problem.
I was able to run SecondLife from Karmic Koala without problem, then when the version for linux changed, the SecondLife client forced to installed the new one, and since then, I am unable do run SecondLife in Ubuntu.

After the message of "Logging", it takes a while a while and then, there is another message on screen saying "Unable to loggin in SecondLife".

I have tried deleting the .secondlife folder but nothing happens.

I run SecondLife clicking on the sh file SecondLife, run on terminal, and this is the text that appears on terminal before crashing:

2010-01-24T18:45:03Z INFO: authenticate: Authenticating: Shariputra Martian, 
2010-01-24T18:45:03Z INFO: authenticate: Options: inventory-root, inventory-skeleton, inventory-lib-root, inventory-lib-owner, inventory-skel-lib, initial-outfit, gestures, event_categories, event_notifications, classified_categories, buddy-list, ui-config, tutorial_setting, login-flags, global-textures, END
2010-01-24T18:45:03Z INFO: authenticate: LLUserAuth::authenticate: uri=https://login.agni.lindenlab.com/cgi-bin/login.cgi
2010-01-24T18:45:03Z INFO: setStartupState: Startup state changing from STATE_LOGIN_AUTHENTICATE to STATE_LOGIN_NO_DATA_YET
2010-01-24T18:45:43Z WARNING: process: LLXMLRPCTransaction CURL error 28: Connection time-out after 40001 ms
2010-01-24T18:45:43Z WARNING: process: LLXMLRPCTransaction request URI: [https://login.agni.lindenlab.com/cgi-bin/login.cgi](https://login.agni.lindenlab.com/cgi-bin/login.cgi)
2010-01-24T18:45:43Z INFO: authResponse: Processed response: 28
2010-01-24T18:45:43Z INFO: setStartupState: Startup state changing from STATE_LOGIN_NO_DATA_YET to STATE_LOGIN_DOWNLOADING
2010-01-24T18:45:43Z INFO: setStartupState: Startup state changing from STATE_LOGIN_DOWNLOADING to STATE_LOGIN_PROCESS_RESPONSE
2010-01-24T18:45:43Z INFO: LLNotificationHistoryChannel::savePersistentNotifications: Saving open notifications to /home/mcgarcia/.secondlife/user_settings/open_notifications.xml
2010-01-24T18:45:43Z WARNING: LLAlertDialog: Alert: Unable to connect to Second Life.
Despite our best efforts, something unexpected has gone wrong. 
 
Please check secondlife.com/status 
to see if there is a known problem with the service.


Any suggestion would be much appreciate thank you

---

### Post by ell02 on 2010-02-11
Here is how i run sl
[http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse](http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse)
I dont use voice and i use the emerald (greenlife) 1.23.5.950 release. I dont use the newer one as i crash on editing appearance.
peace

---

### Post by kaligus on 2010-02-13
FWIW 32bit Karmic latest updates no problems anywhere with secondlife.

I do not run with voice ever.

Emerald
SL default linux
imprudence
snow globe
SL beta/testing linux (couple versions old)

All with the same results, building, appearance, moving, etc. all seem to work.  I just checked again to make sure.

I know that editing the main secondlife script on any version/flavor of the client has some options that may fix some crashes.  So far I have not had to resort to that except on 64bit (which I left at Karmic so I could have my machine back... 64bit breaks too much)

---

### Post by c0rrupt0r on 2010-04-23
> **RabidWeezle said:**
> Haven't tried yet, but have you tried with a 3rd party viewer (omvviewer has an ubuntu ppa). Will check it out when I get home though.

--EDIT

Since this is the higher post: The answer is you need to disable openal audio in the secondlife script:

```
gedit secondlife
```

then uncomment this line so it looks like so:

```
export LL_BAD_OPENAL_DRIVER=x
```

This did not fix the issue with the sound on emerald viewer for me, Still having the fuzzy and static sounds and then it crashes totall.

---

