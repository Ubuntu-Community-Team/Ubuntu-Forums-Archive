---
title: "Volume"
date: 2009-02-15
forum: General Help
---

### Post by Awesom on 2009-02-15
Hi, I recently loaded ubuntu onto my computer I am used to windows but am getting the hang of everything, really loving it except that my sound works but is not very loud compared to what it was and the keyboard to turn sound up or down shows the bar of volume level but it doesnt actually effect the volume level.

---

### Post by Awesom on 2009-02-15
Anyone please?

---

### Post by indeterminate on 2009-02-15
Does your soundcard use the Intel HDA chipset? It's really common, and I've noticed that the Linux drivers just don't let it get as loud as the Windows drivers do. To check if yours is one of these, run "lsmod | grep snd_hda_intel" from the console. If it prints anything, that might be your problem. See [this thread]("http://ubuntuforums.org/showthread.php?t=389560").

Also if you double-click on the volume icon in the taskbar, you can check to make sure that all the playback channels are appropriately high. It might not be turned up all the way. Sometimes the support for those built-in volume buttons on the keyboard can be kinda buggy.

---

### Post by Awesom on 2009-02-15
Hmm I thought id checked the volume in the taskbar thing but obviously must not have cuz it made a pretty big difference when I turned it all the way up. And the keyboard thing works perfect on windows on linux it shows the bar as if its going up or down but makes no actual difference.

What you said to type bring this up.
```

snd_hda_intel         346136  5 
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd                    56996  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

---

