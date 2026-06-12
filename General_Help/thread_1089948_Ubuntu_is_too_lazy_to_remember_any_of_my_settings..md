---
title: "Ubuntu is too lazy to remember any of my settings..."
date: 2009-03-07
forum: General Help
---

### Post by ownaginatious on 2009-03-07
For some reason it seems like 90% of the settings in Ubuntu aren't saved the next time I start up. One of the really annoying ones, for example, is volume settings. Whenever I restart, my volume is always muted and the PCM is also muted, which I have to un-mute manually by going through that control panel.

Also, I have this problem that occurs every so often where compiz-fusion literally just stops, and Visual Effects are automatically set to none. The only way to have my settings saved is to log out and then log back in to make them come back when compiz fusion restarts with the graphical interface. If I try re-enabling them without logging out, they all get reset to their default values...

Is there a way to cure Ubuntu's amnesia?

P.S. I'm also having a problem with the sound mixer - and I've literally been having it forever. Sometimes programs cannot play sound until other sound playing programs are shutdown. The only way I've found to sort of remedy the problem is to manually kill task the pulseaudio server. It's really annoying because I can't have game sounds at the same time as music or sound in my virtual PC as well as my actual PC at the same time.

Any fix for that? lol

Thanks!

---

### Post by ownaginatious on 2009-03-08
bump...

---

### Post by ownaginatious on 2009-03-10
I will bump this indefinitely if I have to. I know someone out there probably knows how to solve at least one of my problems.

---

### Post by kmac on 2009-03-10
> **ownaginatious said:**
> 

P.S. I'm also having a problem with the sound mixer - and I've literally been having it forever. Sometimes programs cannot play sound until other sound playing programs are shutdown. The only way I've found to sort of remedy the problem is to manually kill task the pulseaudio server. It's really annoying because I can't have game sounds at the same time as music or sound in my virtual PC as well as my actual PC at the same time.

Any fix for that? lol


Change your default audio device from "OSS" or "Auto-detect" to "ALSA".

PS. Your persistence is admirable. Though I cannot solve your problem, I'm sure someone who can will get sick of your chronic bumping

---

### Post by ownaginatious on 2009-03-10
> **kmac said:**
> Change your default audio device from "OSS" or "Auto-detect" to "ALSA".

PS. Your persistence is admirable. Though I cannot solve your problem, I'm sure someone who can will get sick of your chronic bumping

That's the plan :). Thanks for your help!

---

### Post by chellrose on 2009-06-22
> **kmac said:**
> Change your default audio device from "OSS" or "Auto-detect" to "ALSA".

PS. Your persistence is admirable. Though I cannot solve your problem, I'm sure someone who can will get sick of your chronic bumping

I'm having the same problem with the sound being muted on startup.  How do I change the default device?

---

### Post by bubbhasdance on 2009-06-22
I would have a look at the Alsamixer (type alsamixer in Terminal) after startup, and then check PulseAudio Manager (I don't believe this is native, so download from Synaptic) and make sure all levels are up and the output you want is set to Default.

This worked for me, anyway. If there's anyone else that can help...

---

### Post by Wiebelhaus on 2009-06-22
This will happen if you don't shut down properly and no one cares if you bump till you pass out , it's just the Internet for crying out loud. It will take you more effort to do that than it would take me to ignore it.

---

### Post by bacchusmarsh on 2010-06-16
> **Sissy13 said:**
> I'm having the same problem with the sound being muted on startup.  How do I change the default device?

Try here...

[http://ubuntuforums.org/showthread.php?p=9471488#post9471488]("http://ubuntuforums.org/showthread.php?p=9471488#post9471488")

---

