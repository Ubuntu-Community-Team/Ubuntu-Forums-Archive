---
title: "[SOLVED] Disabling GDM Disables Soundcard"
date: 2008-12-05
forum: Desktop Environments
---

### Post by ejcdke on 2008-12-05
Hello, I recently upgraded to 8.10 and decided I want to get a bit more serious with Linux and boot directly to the terminal.  I would like to keep Gnome around for the cases where it's needed, but I want to do most of my work in the terminal.  I disabled  GDM and found that audio no longer works when GDM is disabled.  When GDM is off, using "aplay -l" at the terminal returns "no soundcard found no soundcard found."  However, When GDM is on, it returns:

```
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I've tried using modprobe to run snd-hda-intel when GDM is off, but that did not work.  I've tried many ways of disabling GDM and they seem to result in the same disabled sound.  I've also fooled with the tips at [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") while GDM was disabled with no luck.

Can anyone help me?  How can make Ubuntu 8.10 boot to the terminal rather than Gnome without disabling the sound?  Thank you in advance for any assistance.

Eric

---

### Post by ajgreeny on 2008-12-05
It may not be what you are looking for but you could simply let gdm start and then in the sessions option choose the console, which as far as I remember is one of the options available.  Or you could just let gdm get to the login page and then Ctrl+Alt+F1 to the console, and login there.

At least, I can't see why it wouldn't work.  I've never tried it, but I can't see why it would not work.

---

### Post by ejcdke on 2008-12-05
Thanks.  That might be my solution for now.  Although, the puzzle solver in me really wants to get this working.  I don't understand how the soundcard would be tied with GDM to the point where disabling GDM disables sound.

---

### Post by Zorael on 2008-12-05
Could it be that the pulseaudio daemon is run when X starts?
```
$ pulseaudio -d
```

---

### Post by ejcdke on 2008-12-05
Thanks Zorael.  I don't think that's the problem.  When I boot, I hit the command prompt and run "startx", which seems to load the pulseaudio daemon fine.  I did double check and it's running.

---

### Post by Zorael on 2008-12-05
Mayhaps I misunderstood; I thought you wanted sound - for which you need the pulseaudio daemon running - in a boot-to-tty setup with GDM (and by extension, X) not starting automatically?

---

### Post by ejcdke on 2008-12-06
I don't need sound in the terminal.  I disabled GDM and now when I login to X (via "startx"), the sound is disabled.

---

### Post by Zorael on 2008-12-06
> **ejcdke said:**
> I don't need sound in the terminal.  I disabled GDM and now when I login to X (via "startx"), the sound is disabled.
That makes sense, ignore me. :3

---

### Post by ejcdke on 2008-12-06
Eh, it was good advice and I appreciate the effort :)  Anyone else have ideas?

---

### Post by ejcdke on 2008-12-08
Update:  I changed my method of disabling GDM to the following:

```
sudo update-rc.d -f gdm remove
sudo update-rc.d gdm start 30 3 4 5 . stop 01 0 1 2 6 .
```

When I boot to the terminal and login, I can run "aplay -l" and see the proper result.  However, when I startx, open a terminal window in Gnome, and then enter "aplay -l", the system returns that it cannot find my soundcard.  I hit ctrl+alt+F2 and tried "aplay -l" from the terminal while still logged into X and it worked fine.  I'm actually getting sound from terminal apps without issue, but I X will not let me use sound.

So, I logged out of X and did a "sudo su" from the terminal and did a "startx" as root.  Sound worked perfectly.  This seems odd, but would point to some sort of permissions issue.  I checked to make sure I was a member of the "audo" group, and I am.  anyone have ideas as to what access I might need to grant myself to get sound running?  Hopefully I'm making sense.

---

### Post by ejcdke on 2008-12-08
Another update:  I did a chmod on /dev/snd /dev/dsp /dev/mixer /dev/sequencer and /dev/sequencer2.  I noticed that the some audio functions suddenly became available to me in X, but "aplay -l" still states that no soundcards are found while in X.  If I log out of X back to the terminal "aplay -l" seems to work fine.

---

### Post by ejcdke on 2008-12-08
This one is solved!!  I'm so excited.  After realizing it was a permissions problem, and toying with groups didn't work, I did a little more research.  I came across [http://www.usenet-forums.com/linux-general/74048-sound-alsa-works-only-root.html]("http://www.usenet-forums.com/linux-general/74048-sound-alsa-works-only-root.html").  I started by running:
```
usermod -G `groups $myusername | cut '-d ' -f3- | tr ' ' ','`,audio $myusername
``` ...and that didn't work, even after a reboot.  Note that I replaced "myusername" with my actual username.

The instructions in the aforementioned site stated that running the following will give all users access to the audio system. ```
find /dev -group audio -type c -exec chmod a+rw '{}' ';'
``` ...and that worked!  I had to reboot the system, but GDM is disabled and audio is working in X!  Hooray!

---

### Post by Bronyr on 2009-09-03
I did all the above, I now have sound, but it's very low...
??

---

### Post by ejcdke on 2009-09-03
Hmm... Come to think of it, the sound wasn't very loud, but my speakers had a volume control that could take things way up.  I went to full on Ubuntu Server and no longer have an Ubuntu Desktop system to toy with, so I can't really offer any help at this point.  I suspect that the problem is still permissions related and that there is simply another file or two that require adjustment.  Check /etc/security/console.perms and see what it says under "<sound>".  This will give you the various directory location of the audio related files.  Check permissions in each of those locations to see if something isn't right.  I bet /dev/mixer is the root of the issue.

---

### Post by Bronyr on 2009-09-04
I had no sound whatsoever and that low sound after applying the fix was just the volume adjustment - it's all working, and your trick actually worked, thanks!

---

