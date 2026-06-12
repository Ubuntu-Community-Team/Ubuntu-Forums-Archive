---
title: "No sound after an ALSA update."
date: 2009-01-17
forum: General Help
---

### Post by Chaseums on 2009-01-17
Hey,

Recently I've been trying to everything in my power to figure out why in the world I can't capture sound, and it had occured to me that perhaps I just didn't have up-to-date drivers. I've only been running Ubuntu for about 2 weeks or so, so I started doing a little bit of research as to what the problem might be. After searching the forums for a little bit, I found a thread which told me how to update and install my ALSA drivers (The same thread had spoken of how it had fixed that users' sound capture problems!)

So, I figured that nothing bad could come of updating, right? apparently, wrong! xD

After I updated and rebooted, I noticed that my volume control had a nice, fat, mutey-looking "X" next to it. When I try to open it, it says that either I don't have the correct GStreamer plugins installed or my sound card isn't configured, and basically says, "No sound for you, ye lil' n00bsteak :)". I just installed most if not all GStreamer plugins way earlier in the day, so I'm thinking that's not the problem.

So, can anyone offer some insight as to what may be going on? Guess I'll be listening to my iPod til I can get this figured out :D Let me know if you need more information.

Thanks a ton!

---

### Post by 2hot6ft2 on 2009-01-17
Well you can try reinstalling the plugins with
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.
---------------------
8.10 uses PulseAudio.

The first one is to fix pulse so that's where I would start.

Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
A short version here. I suspect it will be modified.
[http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html)

Hope this helps.

---

### Post by Chaseums on 2009-01-18
Hey again, and thanks so much for your help.

But, the problem is still unresolved. Yet, I believe I've found the true problem. 

After trying to fix PA and moving onto just trying to use ALSA instead of PA, I realised that my computer wasn't registering a sound card due to one of the steps that needed to be taken or order to make the change from PA to ALSA. When I tried "asoundconf list" no cards were found, yet when I did "lshw", (which I have no idea what that means, just saw that it seemed to list all hardware) under a subheading that said "Multimedia UNCLAIMED" I got:

 > *-multimedia UNCLAIMED
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: latency=0 maxlatency=5 mingnt=2

Call me crazy, but I'm pretty sure this is my sound card. Now, I've already checked and made sure that the card was enabled in my BIOS, so now I'm at a dead-end on figuring out why my card isn't registering. If I could just get my system to register it then the problem should be resolved, but I have no idea of how to make the system do that. :-\ 

So once again, your help would be sooo greatly appreciated, and thank you for everything you've done thus far.

---

### Post by linux_tech on 2009-01-18
what is output of
```

cat /proc/asound/card0/codec#* | grep Codec


```

---

### Post by Chaseums on 2009-01-18
> **linux_tech said:**
> what is output of
```

cat /proc/asound/card0/codec#* | grep Codec


```

Output:

> cat: /proc/asound/card0/codec#*: No such file or directory

---

### Post by linux_tech on 2009-01-18
In terminal type:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

reboot, test sound

---

### Post by Chaseums on 2009-01-18
Thank you so much my friend. Everything seems to be working fine now :D

EXCEPT for the main reason why I tried to change things around: my audio capture. It's still not working. What info would you need in order to figure out why it's not working?

---

### Post by linux_tech on 2009-01-18
what are system make, model?
try this again (post results)
```
cat /proc/asound/card0/codec#* | grep Codec
```

go thru this link also:
[http://ubuntufs.wordpress.com/2006/06/08/trouble-with-your-microphone/](http://ubuntufs.wordpress.com/2006/06/08/trouble-with-your-microphone/)

make sure mic, rec, capture settings are all available and selected

---

### Post by jonlightyear2000 on 2009-01-18
Just to say I have the exact same problem!  So if you guys figure it out please let me know how! :D

---

### Post by Chaseums on 2009-01-18
Realtek ALC888 is the result of the command.

HP Compaq dx2450 Microtower.

I went into the link you've given me, and I don't seem to have the Alacarte menu editor, and the capture tab doesn't come up on my volume control after I've ticked what they've told me to tick (I didn't have all of the options that they wanted me to tick, however.) A capture volume control comes up under the recording tab, though. Every time I open the volume control and move it over to the record tab, my mic is always muted. I've tried unmuting, closing, and reopening and everytime I reopen the control it's remuted.

---

### Post by linux_tech on 2009-01-18
Try this, in the terminal type:

```
sudo gedit /etc/modprode.d/asla-base
```

add the following text at the bottom;

options snd-hda-intel model=3stack-dig

reboot, then see if capture has appeared or not, if so test mic
if not, replace the 3stack-dig with one of these options, try one at a time. You have to reboot or reload after each.  
	
6stack-dig	
3stack-6ch    
3stack-6ch-dig 

you can reload alsa with :
```

sudo alsa force-reload

sudo /etc/init.d/alsa-utils start

```

Let me know if any of these make capture settings show.

---

### Post by linux_tech on 2009-01-18
also please try 6stack-digout

---

### Post by Chaseums on 2009-01-18
I think there may be a problem with my gedit, perhaps?

when I run that command in my terminal and the text doc opens up, it's completely blank. I figured I'd just input your line anyway and give it a try, but when i tried to close and save it it said, "Could not find the file /etc/modprode.d/asla-base"

---

### Post by Taidgh on 2009-01-19
Try ```
sudo gedit /etc/modprode.d/alsa-base
```
instead.

---

### Post by Chaseums on 2009-01-19
> **Taidgh said:**
> Try ```
sudo gedit /etc/modprode.d/alsa-base
```
instead.

That also brings up a blank document.

---

### Post by Ptero-4 on 2009-01-19
It's
```
gksudo gedit /etc/modprobe.d/alsa-base
```

---

### Post by Chaseums on 2009-01-20
Hey, and thanks to everyone who's helped thus far. 

The results are, the very last command given actually opened up the correct document, but when I tried adding any of the four options that I was told to input into the doc, I still never got the capture tab.

What's the difference between the capture tab, and the capture options under the Recording tab, is my question.

---

