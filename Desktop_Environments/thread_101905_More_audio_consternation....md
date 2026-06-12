---
title: "More audio consternation..."
date: 2005-12-10
forum: Desktop Environments
---

### Post by ionizd on 2005-12-10
I just installed the restricted format codec packages, including the w32 codec pack. I went to play a .wmv file and got the following error:
*ALSA device "default" is already in use by another program.*
 None of this stuff happened before I got tired of the XMMS freezups and de-installed it. What can I do to fix this?

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=ionizd]I just installed the restricted format codec packages, including the w32 codec pack. I went to play a .wmv file and got the following error:
*ALSA device "default" is already in use by another program.*
 None of this stuff happened before I got tired of the XMMS freezups and de-installed it. What can I do to fix this?[/QUOTE]
What app are you using to play the songs now?

Assuming that your default audio device is /dev/dsp, you can find the other process that is using it with:
```

$ lsof /dev/dsp

```

---

### Post by ionizd on 2005-12-10
[QUOTE=cwaldbieser]What app are you using to play the songs now?

Assuming that your default audio device is /dev/dsp, you can find the other process that is using it with:
```

$ lsof /dev/dsp

```[/QUOTE]
 Kaffeine(with gstreamer), I think. I tried that code you gave me with the following result:
[I]jason@guineapig:~$ lsof /dev/dsp
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.[/I]
 Huh?
*** Edit ***
Also, when trying to open a web page with a multimedia file(of an unknown type) in it, I get a message that says, *"no plugin found for 'shockwave flash media' . Do you want to download one from www.macromedia.com?"*, then immediately gives me the following error:
*Can't init Audio Driver 'alsasink' - trying another one...*
followed by:
*Can't init Video Driver 'xvimagesink' - trying another one...*
followed by:
*No useable video-driver found! (xvimagesink)*
 then the web page totally fails to open.
WTF? I have working audio, and my video seems to work fine.

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=ionizd]Kaffeine(with gstreamer), I think. I tried that code you gave me with the following result:
[I]jason@guineapig:~$ lsof /dev/dsp
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.[/I]
 Huh?[/QUOTE]
It is just saying, in it's roundabout way, that no process has an open handle to /dev/dsp.

Hmm, do you have any other sound cards?  I have 2 in my system, and I don't the integrated one, so I normally am using /dev/dsp1.  Not sure if that makes a difference.

Do you hear normal system sounds or other sounds, or do you have a problem with those, too?

Is there a config option for something like an engine under Kaffeine?  It has been a while since I used it.  Usually, things are laid out so you select the engine you want to use, and then you can choose a sound device underneath that sometimes.

---

### Post by ionizd on 2005-12-10
[QUOTE=cwaldbieser]It is just saying, in it's roundabout way, that no process has an open handle to /dev/dsp.

Hmm, do you have any other sound cards?  I have 2 in my system, and I don't the integrated one, so I normally am using /dev/dsp1.  Not sure if that makes a difference.

Do you hear normal system sounds or other sounds, or do you have a problem with those, too?

Is there a config option for something like an engine under Kaffeine?  It has been a while since I used it.  Usually, things are laid out so you select the engine you want to use, and then you can choose a sound device underneath that sometimes.[/QUOTE]
 Please read the edit to my earlier post. I only have one sound card and no integrated sound, and it's been a pain in the a$$ ever since I installed it. System sounds are no problem.

---

### Post by cwaldbieser on 2005-12-11
[QUOTE=ionizd]Please read the edit to my earlier post. I only have one sound card and no integrated sound, and it's been a pain in the a$$ ever since I installed it. System sounds are no problem.[/QUOTE]
Well, there are some things that I guess would be useful for us to know.

I am assuming that based on your errors you are using ALSA and not esd, or aRTS or some other sound system, correct?

Can you give us a URL that has an example of the page where you get the no sound error?

Have you had any success with alternate applications like gxine?

---

### Post by ionizd on 2005-12-11
I'm a Linux moron, and I have no idea what you guys are talking about roughly 90% of the time, but I'll try to respond intelligently to your questions.
 Based on the information my computer is spitting out at me, ALSA is the sound system, but I don't know if there are others installed and interfering with the proper operation of ALSA. I don't even know how to check that.
 I can't give you the URL specifically that causes the problem, but it's a MySpace.com posting. Of course you know that video and audio clips are a part of some of those posts.
 What's gxine? If it's another multimedia player, I haven't tried it. I would like to know if there is a listing of the different packages available in the repositories broken down and sorted by what it does, what it can be used with (and what it *can't* be used with!), and what Windows program it roughly correlates to. Is there anything out there like that?

---

### Post by ionizd on 2005-12-11
[QUOTE=cwaldbieser]Is there a config option for something like an engine under Kaffeine?  It has been a while since I used it.  Usually, things are laid out so you select the engine you want to use, and then you can choose a sound device underneath that sometimes.[/QUOTE]
 Sorry for the double post, but I just noticed this again. Where *is* this?

---

### Post by cwaldbieser on 2005-12-11
[QUOTE=ionizd]I'm a Linux moron, and I have no idea what you guys are talking about roughly 90% of the time, but I'll try to respond intelligently to your questions.
 Based on the information my computer is spitting out at me, ALSA is the sound system, but I don't know if there are others installed and interfering with the proper operation of ALSA. I don't even know how to check that.
 I can't give you the URL specifically that causes the problem, but it's a MySpace.com posting. Of course you know that video and audio clips are a part of some of those posts.
 What's gxine? If it's another multimedia player, I haven't tried it. I would like to know if there is a listing of the different packages available in the repositories broken down and sorted by what it does, what it can be used with (and what it *can't* be used with!), and what Windows program it roughly correlates to. Is there anything out there like that?[/QUOTE]

This link should give you a good idea of programs in Ubuntu that correspond to programs in Windows:
[http://www.ubuntuforums.org/showthread.php?t=33183]("http://www.ubuntuforums.org/showthread.php?t=33183")

If you open up Control Center -> Sound and Multimedia -> Sound System -> Hardware tab, what does it say you are using for an Audio Device?

Also, what is the output of:
```

$ ps aux | grep esd

```
This let's us know if the "Enlightened Sound Daemon" (esd) is running.  Potentially it can cause conflicts with other running sound systems.

gxine is another wrapper around the "xine" engine used to play videos.  It is like kaffeine, but has more of a gnome look and feel to it.  I use it instead of kaffeine because I had some jerkiness with kaffeine playback.  gxine is in the repositories, and it might even be installed on your system by default.  It you type:
```

$ gxine

```
and the program pops up, you already have it.

---

### Post by cwaldbieser on 2005-12-11
[QUOTE=ionizd]Sorry for the double post, but I just noticed this again. Where *is* this?[/QUOTE]
It would be burried in the kaffeine menu somewhere-- I am using gxine, which has a raft of options under File -> Preferences.  I can't really install kaffeine without uninstalling gxine or else I would just download it and look up what the menus were for you.

---

### Post by ionizd on 2006-01-02
I am still having problems playing video files. I get the same error as before, and I've nearly lost my mind chasing down different settings and options. Is there a way to get rid of all audio and video players, the entire sound system and any thing else associated with audio and video playback (sort of like uninstalling the device and using driver cleaner in windows), then starting a fresh install of the sound card drivers, the sound system and finally the players?

---

### Post by Gimbo on 2006-01-03
I've replied with my suggestions on your other post:
[http://www.ubuntuforums.org/showthread.php?t=111920]("http://www.ubuntuforums.org/showthread.php?t=111920")

No idea how useful that'll be, though (I'm sure I'm as new or newer than you to Ubuntu).

---

