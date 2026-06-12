---
title: "Sound problem when flash videos are playing"
date: 2008-12-29
forum: Desktop Environments
---

### Post by kodalisrikanth on 2008-12-29
Hi, 

      I am having strange problem. When i play videos from  youtube or any other flash website, sound is not coming from the speakers. I also observed that, After playing the flash video i am not able to listen any audio from my computer.

      After playing the video i checked my sound settings by
system->preferences->Sound
And there is no beep sound.

      Temporarily, I am rebooting into recovery mode whenever i got this problem. Then everything is working fine.

                     How to fix this error...?

---

### Post by sirgimp on 2009-01-07
> **kodalisrikanth said:**
> Hi, 

      I am having strange problem. When i play videos from  youtube or any other flash website, sound is not coming from the speakers. I also observed that, After playing the flash video i am not able to listen any audio from my computer.

      After playing the video i checked my sound settings by
system->preferences->Sound
And there is no beep sound.

      Temporarily, I am rebooting into recovery mode whenever i got this problem. Then everything is working fine.

                     How to fix this error...?
What version of Ubuntu are you useing. This problem was pretty bad in Hardy Heron, and improved in Itrepid Ibex. But I still frequently loose sound when playing flash video or MP3's. My only solution has been to:

1) Use System Monitor *System>Administration>System Monitor* to Kill any Firefox processes. Then restart Firefox. 

2) If that doesn't work, then give it the old Restart and the sound comes back (for a day or two). 

It seems to be an ongoing problem that I don't understand and find very frustrating. Under *Sound Preferences* there are several options under the *Sound Playback* dropdown list. Mine is set to *Autodetect*. Would I get better results if I choose *ALSA* or *Pulse Audio*?

---

### Post by jesuspresley on 2009-01-07
I have the same issue in Firefox + Flash, also in Songbird. 
Rythmbox somehow is not affected.

As I had the same problem in Firefox + Flash within Windows XP before, I presume it's a flash player issue...?

---

### Post by jesuspresley on 2009-01-09
Actually, rebooting doesn't solve the problem.
Even reinstalling flash does not.

I will have to dig into my systemwide sound settings then. Grimes.

---

### Post by namdung on 2009-01-09
Check if anything else has the sound device file open.
```
less /proc/asound/card0/pcm0p/info
```

and look at subdevices_avail (at the end of the file)
If avail is 0, then something already has your sound card open.

Try this for multiple sound solution:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Which Ubuntu version?
Which Flash player version?

---

### Post by jesuspresley on 2009-01-10
This is how it looks:
```
card: 0
device: 0
subdevice: 0
stream: PLAYBACK
id: emu10k1
name: ADC Capture/Standard PCM Playback
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 32
*subdevices_avail: 31*
```

So I followed your link: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
...and in the guide I read this:

> **Flash and java**
If you have flash9, you need to have
libflashsupport
to get your audio to work properly. If you have flash10 or higher, you do not need libflashsupport and should remove it.

If you are using amd64 Hardy be sure to read the sticky guides at the top of the 64bit forum to get 32bit flash and java working. If you are using Intrepid amd64, the ubuntu-restricted-extras package will set you up properly so you can skip this.

Even though I have Flash10, I wondered if the *libflashsupport* package might cause the trouble. 
So I installed *libflashsupport* using Synaptics, restarted Firefox and everything worked!

For me the prob is solved.

---

