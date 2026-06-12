---
title: "Audio Problems"
date: 2008-12-05
forum: General Help
---

### Post by iAndrew on 2008-12-05
Well, I've just noticed that only 1 application can use my audio device at a time.

when I have amarok running then pause it and try to go on firefox/youtube to view stuff I can't hear the audio. Then, if I try to resume amarok I have to force quit it.

Is this known problem?

I've searched "audio device" already, the first few pages didn't match my symptoms so if there is please link me to it.

---

### Post by iAndrew on 2008-12-06
bump``

---

### Post by russofris on 2008-12-06
This is common.  Ultimately, the answer is probably going to be "Enable dmix in your ~/.asoundrc".  Unfortunately, configuring alsa properly often requires a 4 year degree in programming.

Do a quick grok of [http://www.alsa-project.org](http://www.alsa-project.org) .  Hit the docs, search for dmix.  Ping this thread when you get stuck on something specific.

Frank

---

### Post by iAndrew on 2008-12-06
I didn't find 'dmix' after clicking documentation link...

So I searched, this is what I got...

```
There is no page titled "dmix". You can create this page.

For more information about searching AlsaProject, see Searching AlsaProject.

Showing below up to 20 results starting with #1.

```

---

### Post by russofris on 2008-12-06
Apologies for my brief answer earlier.

The documentation you seek is located here:

[http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc)

Here's a summary of the situation:

Most consumer audio hardware can play one audio stream.  Few cards feature hardware mixing of multiple streams, and it is no longer considered a desirable trait.

ALSA is the audio subsystem for the linux kernel.  Alsa can mix multiple streams into a single stream via a facility called dmix.  Your audio card properties (including dmix) is configured via a file called the ".asoundrc".  Unfortunately, this is not a task for beginners and should be handled by your distribution (Ubuntu) or automatically for alsa ver > 1.09.  Unfortunately, it is not at this time.  In fact, few distributions outside of pro-audio distros will do this for you.

Take a look at the doc I have linked.  Or go straight to [http://alsa.opensrc.org/DmixPlugin](http://alsa.opensrc.org/DmixPlugin) .  See how far you get.  

This is one of the frustrating areas of running linux currently, and is currently in a state of flux.  Hopefully it will improve soon.

Best of luck.
Frank

---

### Post by danwood76 on 2008-12-06
This is incorrect information.

You simply need to setup pulseaudio properly, dmix is used for mixing down, for example, 5.1 surround down to stereo.

This guide will give you a really good audio setup:
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by spcwingo on 2008-12-06
I had the same problem.  I just installed libflashsupport through synaptic and voila!  Please note that libflashsupport is for flash player 9, not 10.  I'm not saying that it won't work with 10...I just haven't moved to 10 and can't say if it will or won't.

---

### Post by danwood76 on 2008-12-06
libflashsupport wont work with flash 10 as flash 10 can use pulse audio.
It causes lots of stability issues with firefox crashing and the like.

The fix is to setup pulse as the default playback system for all apps and it will then all work nicely together.
Using the guide I linked to in my previous post!

---

### Post by iAndrew on 2008-12-06
Thanks, I did those and it seems to work.

---

