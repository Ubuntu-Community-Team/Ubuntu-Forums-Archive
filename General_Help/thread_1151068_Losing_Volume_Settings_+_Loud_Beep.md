---
title: "Losing Volume Settings + Loud Beep"
date: 2009-05-06
forum: General Help
---

### Post by brandoncolorado on 2009-05-06
I am running 9.04 Netbook remix.  After each reboot my volume settings are lost.  Although this typically wouldn't be a big deal because I can just unmute, this means that the PC beep volume control is automatically set to "on."  This has embarrassed me quite a few times in the library already because I have forgotten to mute it with each restart.

How can I set the default volume settings?

I am adding 4 screenshots to this post to help explain my situation.  

1)  ALSA volume controls (this is what I see after each restart no matter what I change them to)

2)  ALSA settings

3)  Sound settings

4)  Blacklist (tried to shut the loud beeping off!)

Thanks

---

### Post by monsterstack on 2009-05-06
Hrmm, perhaps your PC speaker has another name. I've seen it named "snd_pcsp" before. What does

```
lsmod | grep -i pc
```

give?

---

### Post by brandoncolorado on 2009-05-06
> **monsterstack said:**
> Hrmm, perhaps your PC speaker has another name. I've seen it named "snd_pcsp" before. What does

```
lsmod | grep -i pc
```

give?

```
brandon@brandon-laptop:~$ lsmod | grep -i pc
snd_pcm                82820  2 snd_hda_intel,snd_hda_codec
snd_timer              29320  2 snd_pcm,snd_seq
snd                    66596  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm
brandon@brandon-laptop:~$ 

```

---

### Post by monsterstack on 2009-05-06
Well at least that explains why blacklisting the pcspkr module doesn't work. It isn't even on your computer! It may or may not be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366399") [bugs.launchpad.net].

Still, another solution posted [here]("http://ubuntuforums.org/archive/index.php/t-1041329.html") [ubuntuforums.org] suggests adding this line

```
sh -c "xset b off && xset b 0 0 0"
```

to "~/.profile". Where xset is the user preference facility for X, b is the system bell, and the three zeros are for volume, pitch and duration, all set to nothing just to be sure. Go ahead and create that file if it doesn't already exist. Having that line put in .profile means those settings will be enabled every time you log-in.

Log out and log back in again and see what happens.

As for your sound muting itself, I don't know what to suggest. :(

---

### Post by brandoncolorado on 2009-05-08
> **monsterstack said:**
> Well at least that explains why blacklisting the pcspkr module doesn't work. It isn't even on your computer! It may or may not be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366399") [bugs.launchpad.net].

Still, another solution posted [here]("http://ubuntuforums.org/archive/index.php/t-1041329.html") [ubuntuforums.org] suggests adding this line

```
sh -c "xset b off && xset b 0 0 0"
```

to "~/.profile". Where xset is the user preference facility for X, b is the system bell, and the three zeros are for volume, pitch and duration, all set to nothing just to be sure. Go ahead and create that file if it doesn't already exist. Having that line put in .profile means those settings will be enabled every time you log-in.

Log out and log back in again and see what happens.

As for your sound muting itself, I don't know what to suggest. :(

Thanks, I'll give this a go.  That makes way more sense now that you explained that command.

---

### Post by brandoncolorado on 2009-05-08
Unfortunately, that didn't work either.  Any other ideas anyone?

Maybe I can hire the office space guys to smash the **** out of my laptop.

---

