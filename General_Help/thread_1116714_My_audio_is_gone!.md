---
title: "My audio is gone!"
date: 2009-04-05
forum: General Help
---

### Post by DanielCarrera on 2009-04-05
Hello.

I have Intrepid Ibex. For some reason my audio has magically stopped working. I first noticed when I went to YouTube just now, but I have the same problem if I try to watch a video with Totem or gxine. Strangely, if I am playing a movie and I raise the volume to the max I hear static on the speakers. So *something* is communicating with the speakers.

I tried rebooting the computer as that would reboot whatever audio daemon I'm using, but that didn't help. I don't know what to try.

Any ideas? Help!

---

### Post by Lunx on 2009-04-05
Don't know if this will fix your problem, but someone else had problems a couple of days back (as I did ealier myself with Intrepid). Turns out it was a setting in alsa. This is a cut and paste from the earlier thread

> Not sure this will help, but I had problems with sound and static myself. Using HDA Intel (Asla mixer) and it turns out it was the PCM setting being turned down to nothing (but still activated, not muted). If you are using same, you can right click on your volume button in top panel and open volume control and then check what the PCM setting is. 

As I said, no idea if this will solve it, but it's something to investigate anyway

Turns out their problem was the same and this fixed it for them

[http://ubuntuforums.org/showthread.php?t=1112966](http://ubuntuforums.org/showthread.php?t=1112966)

---

### Post by DanielCarrera on 2009-04-05
Btw, the same thing happens whether I use the computer's internal speakers or plug in external speakers. When I play a movie I hear that static that is normal of speakers, but nothing else. So it's like something is at least /trying/ to talk to the speaker.

---

### Post by Lunx on 2009-04-05
> **DanielCarrera said:**
> Btw, the same thing happens whether I use the computer's internal speakers or plug in external speakers. When I play a movie I hear that static that is normal of speakers, but nothing else. So it's like something is at least /trying/ to talk to the speaker.

So are you getting sound sometimes, or not at all, or only in certain apps and not others? If it's just static all the time then my solution may work as it happened to me two or three times in Intrepid and it was always the PCM setting being turned way down (but not muted), that turned out being the culprit.

---

### Post by DanielCarrera on 2009-04-05
> **Lunx said:**
> Don't know if this will fix your problem, but someone else had problems a couple of days back (as I did ealier myself with Intrepid). Turns out it was a setting in alsa. This is a cut and paste from the earlier thread

I'm not sure I understand the proposed solution. I can go into alsamixer. I see exactly one volume control called Master. If I press tab I see Capture, and if I press Tab I see Master and Capture, but that's it. Should I see more volume controls? I don't see a volume control called PCM. Where do I find the PCM settings?

The Master control is set to full and is not muted.

Btw, I also have an HDA Intel device (or at least, aplay -l claims hat I do) so I have hopes that my problem may be similar to yours.

---

### Post by DanielCarrera on 2009-04-05
> **Lunx said:**
> So are you getting sound sometimes, or not at all, or only in certain apps and not others?

Not at all. I tried several apps, and none can produce audio. But I can hear speaker static.

> If it's just static all the time then my solution may work as it happened to me two or three times in Intrepid and it was always the PCM setting being turned way down (but not muted), that turned out being the culprit.

Where do I find the PCM setting?

---

### Post by Lunx on 2009-04-05
> **DanielCarrera said:**
>  I see exactly one volume control called Master. If I press tab I see Capture, and if I press Tab I see Master and Capture, but that's it. Should I see more volume controls? 


Btw, I also have an HDA Intel device (or at least, aplay -l claims hat I do) so I have hopes that my problem may be similar to yours.

Sounds as if your volume control is set to something different to how it should be (Capture of HDA or Monitor of HDA or somesuch). Try right clicking the volume control on your panel and selecting Open Volume Control. At the top of the window that opens you'll see Device and in there you can select the right option (Based on what you've said I'd guess the top one which says **HDA Intel (Alsa Mixer)**). Then you'll see all the controls and from memory PCM is the second one from left. Try muting/unmuting and sliding the controls up (while there you can check the front volume if you like, as I notice this is always turned down a bit and stops you getting max sound even when all other volume settings are set to full).

---

### Post by DanielCarrera on 2009-04-05
IT WORKS! IT WORKS!

THANK YOU, THANK YOU, THANK YOU.

I didn't understand what you were saying the first time, but it's not your fault, I had previously found the command-line alsamixer and the thing in System > Preferences > Sound and I was looking at those. I didn't pick up on the fact that you said to right-click on the volume control.

Thanks again.

---

### Post by Lunx on 2009-04-05
Glad it worked (I know very little about sound, this is the only problem I've had where I've worked out the problem on my own, and it's the only thing I know to suggest to others :p ) Anyhow, that's two from two now re: solutions, plus my problems as well, so it's most likely a bug somewhere that causes that setting to change somehow.

---

### Post by phalbert on 2009-04-14
[i]> **lunx said:**
> don't know if this will fix your problem, but someone else had problems a couple of days back (as i did ealier myself with intrepid). Turns out it was a setting in alsa. This is a cut and paste from the earlier thread



turns out their problem was the same and this fixed it for them

[http://ubuntuforums.org/showthread.php?t=1112966](http://ubuntuforums.org/showthread.php?t=1112966)


[/i]

**thank you!!!!!**

---

