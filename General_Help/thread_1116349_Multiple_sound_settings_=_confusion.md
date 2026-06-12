---
title: "Multiple sound settings = confusion"
date: 2009-04-04
forum: General Help
---

### Post by coeus82 on 2009-04-04
Hello, 

I recently found out what was wrong with my sound by checking the Gnome Volume control and finding that PCM was all the way down. I took me days to find this problem because I was messing with the PulseAudio volume control instead. I would increase it to the maximum but it would never "fix" the problem. No sound would come out of my speakers. Only today did I think to try the Gnome volume control (which wasn't on my panel, I had to add it) and voila! the PCM was down. When I raised it sound came out of the speakers.

My question is, how come I can't just completely manage my volume control through PulseAudio's tool?

---

### Post by pbpersson on 2009-04-04
Where did you find this audio control?

How did you add this audio control?

I was recently fooling with my desktop here to fix an audio problem and in about a half dozen places I was able to choose:

ALSA
OSS
Pulseaudio

At least I think that was the issue.  My question is, if this can be set in six places, what if I have two set to each of these values?

Why do I even have a CHOICE?  I mean shouldn't the system SET these things so the sound will JUST WORK?

So I have no idea what this extra control is or where you found it.  However, when I went through the Pulseaudio tutorial they had me add three more audio controls and then told me how to configure them.

This is all way too confusing, at least that is my thought

---

### Post by coeus82 on 2009-04-05
> **pbpersson said:**
> Where did you find this audio control?


Hey pbpersson, you can right click on your panel then click on "Add to Panel". From there you will get a list of items you can add to your panel. Scroll all the way down until you see "Volume Control" and add that.

This is what I used. It doesn't seem to work together with Pulse Audio. For example, if I increase/decrease the volume from Pulse Audio's volume control, it doesn't affect that Gnome Volume Control and viceversa. This is what made thing complicated for me since I assumed Pulse Audio was the master control.

Let me know if that Gnome Volume Control helps you out.

> **pbpersson said:**
> Why do I even have a CHOICE? I mean shouldn't the system SET these things so the sound will JUST WORK?

Well, it makes sense to have a volume control. The sound did just work for me, until a crash from a flash video I was playing. This crash messed up my sound settings somehow. The problem, imo, is the fact that there are multiple volume controls that don't effect each other. One should be to control all.

---

