---
title: "Recent updated killed my sound!"
date: 2006-09-17
forum: Desktop Environments
---

### Post by adds2one on 2006-09-17
I clicked the update button a couple of days ago and installed the new kernel updated. I hadn't used my computer for a few days but this morning I tried to play some mp3s and dicovered that my sound is no longer working. It worked fine before the update and now my dmesg is full of messages such as this:

```
[17179590.264000] snd_timer: Unknown symbol snd_register_device
[17179590.268000] snd_timer: disagrees about version of symbol snd_info_register
[17179590.268000] snd_timer: Unknown symbol snd_info_register
[17179590.268000] snd_timer: disagrees about version of symbol snd_info_create
[17179590.292000] snd_indigoio: Unknown symbol snd_pcm_hw_constraint_integer
[17179590.292000] snd_indigoio: Unknown symbol snd_pcm_lib_preallocate_pages
[17179590.296000] snd_indigoio: Unknown symbol snd_pcm_period_elapsed
[17179590.296000] snd_indigoio: Unknown symbol snd_pcm_hw_constraint_step

```

Since I only got my pcmcia pro audio sound card working a few weeks ago I am feeling very dicouraged. 

I know that some people are having a different problem with the recent update, [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52649](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52649)

but is anyone else experiencing my problem?

Is there a fix?

Please help!

---

### Post by adds2one on 2006-09-17
Here is what happens when I try to manually modprobe my sound card:

```
jjob@jjob-laptop:~$ sudo modprobe snd_indigoio
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-26-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-26-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-26-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_indigoio (/lib/modules/2.6.15-26-386/kernel/sound/pci/echoaudio/snd-indigoio.ko): Unknown symbol in module, or unknown parameter (see dmesg)
jjob@jjob-laptop:~$

```

---

### Post by adds2one on 2006-09-17
And now I have discovered that /etc/modprobe.d/alsa-base is GONE!!

Did this update destroy ALSA? How else can I check?

---

### Post by agrabah on 2006-09-17
Hi there.

I just noticed it too. My sound isn't working either, and I have the same errors (literally - I too have an echo card).

You might try reinstalling alsa; some did have success with it, or boot the old kernel. That way I got my onboard sound working; I didn't have the energy to !recompile! alsa yet; I'm kinda too busy to try it now.

Tine (just to let you know you're not alone in this; sorry for not really helping)

---

### Post by tylerjames on 2006-09-17
Hey dude,

I killed my sound last week when I installed the 686-smp kernel. I found a pretty good thread with help for audio problems.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I ended up having to purge/remove alsa (as explained in the thread) which then forces you to reinstall ubuntu-desktop and gdm.

But it was all worth it, because it got my sound back and now I can take advantage of my two cpu cores!

I hope it works out for ya.

---

### Post by poekie on 2006-09-18
Same problem here, I was completely panicking. Now trying the purge-reinstall alsa solution.. I'll let you know if it worked, going down for reboot now :p 

[edit]
Yup, IT WORKED :D:D:D
phew :)

---

### Post by adds2one on 2006-09-18
Great, sounds like I can fix this.

Question though, how do I purge ALSA?

---

### Post by agrabah on 2006-09-19
Just skimming the two posts I get the idea it won't really work with your sound card - remember, the alsa build that came shipped with ubuntu didn't support echo indigo. Maybe if you purge alsa, the reinstall all the other things and then recompile alsa.

Just a thought...

Tine

---

### Post by ampop on 2006-09-19
30 minutes ago I was listening music with XMMS. Then it was a upgrade to 2.6.15-27-386, and others upgrades that I didn't memorize. I reboot and now, the sound it's dead. ](*,) 
Any body with the same problem?

---

### Post by Jebenko on 2006-09-20
The same here  ](*,)
No sound after the update and the reboot.

---

### Post by ampop on 2006-09-21
I solved my problem with this: [http://ubuntuforums.org/showthread.php?t=202555&page=5](http://ubuntuforums.org/showthread.php?t=202555&page=5)

---

### Post by rrwo on 2006-09-21
I've just noticed this as well. It's worked until I booted up this morning.

There does not appear to be any errors in my dmesg log, though.

---

### Post by rrwo on 2006-09-21
Thanks. The link about updating the ALSA driver seems to have fixed it.

---

### Post by hashimoto on 2006-09-21
I also noticed that I lack sound, but I have no idea how long it has been gone. I have a standard SB card that has never caused any problems before.

---

