---
title: "Multimedia problems"
date: 2005-10-16
forum: Desktop Environments
---

### Post by CAE on 2005-10-16
I have a plethora of problems relating to the playback of video files on my system. I'm using Kaffeine and if possible I'd rather not install other apps due to size considerations of a small hard drive (derail: how big's a base install supposed to be? I think I'm already running out of room :().

So, a checklist.
- AVI: Appears to work fine, sound and video.
- WMV: Choppy sound only, no video.
- MOV: Video only, no sound.
- MPEG: Kaffeine shits itself, for lack of a better expression, and quits.

From what I can recall, I've "installed" w32codecs (downloaded from mplayer site, extracted to /usr/lib/win32). I've also installed ffmpeg and its gstreamer plugin. So what else do I need, keeping in mind that I don't want more than necessary? Also, is there anything I can remove to increase the free space?

---

### Post by tseliot on 2005-10-16
[QUOTE=CAE]I have a plethora of problems relating to the playback of video files on my system. I'm using Kaffeine and if possible I'd rather not install other apps due to size considerations of a small hard drive (derail: how big's a base install supposed to be? I think I'm already running out of room :().

So, a checklist.
- AVI: Appears to work fine, sound and video.
- WMV: Choppy sound only, no video.
- MOV: Video only, no sound.
- MPEG: Kaffeine shits itself, for lack of a better expression, and quits.

From what I can recall, I've "installed" w32codecs (downloaded from mplayer site, extracted to /usr/lib/win32). I've also installed ffmpeg and its gstreamer plugin. So what else do I need, keeping in mind that I don't want more than necessary? Also, is there anything I can remove to increase the free space?[/QUOTE]
Open Synaptic/Kynaptic and install xine and kaffeine-xine (it works better than gstreamer for me)

---

### Post by GeneralZod on 2005-10-16
[QUOTE=CAE]erail: how big's a base install supposed to be? I think I'm already running out of room :([/QUOTE]

'Sup, duders? :coal:

I always reserve 5GB's for my / partition (with /home on a separate partition), but I find it exceptionally hard to use more than 3.5GB.

How big is your /var/cache/apt/archives directory? If you don't need these cached downloads, you can always clear this out.

---

### Post by CAE on 2005-10-16
[QUOTE=tseliot]Open Synaptic/Kynaptic and install xine and kaffeine-xine (it works better than gstreamer for me)[/QUOTE]

Getting more offtopic, but I'd just like to point out that, my god, Adept is crappy. Stop hardcoding font values in, for a start guys.

[QUOTE=GeneralZod]Sup, duders? :coal:

I always reserve 5GB's for my / partition (with /home on a separate partition), but I find it exceptionally hard to use more than 3.5GB.

How big is your /var/cache/apt/archives directory?[/QUOTE]

I saw your post in one of my other threads, and how could I forget that avatar? ;-*

I run apt-get clean frequently, as I'm used to the small drive. However, on second check, I don't know how I got the impression that this drive was filling up. My install's still less than 2 Gb. I guess I'm going crazy without my videos?

---

### Post by tseliot on 2005-10-16
[QUOTE=CAE]Getting more offtopic, but I'd just like to point out that, my god, Adept is crappy. Stop hardcoding font values in, for a start guys.[/QUOTE]
Well, I don't like adept too.

[QUOTE=CAE] I run apt-get clean frequently, as I'm used to the small drive. However, on second check, I don't know how I got the impression that this drive was filling up. My install's still less than 2 Gb. I guess I'm going crazy without my videos?[/QUOTE]
if you install "kaffeine-xine" you can remove "kaffeine-gstreamer" to save some space

---

### Post by CAE on 2005-10-16
[QUOTE=tseliot]Well, I don't like adept too.


if you install "kaffeine-xine" you can remove "kaffeine-gstreamer" to save some space[/QUOTE]

Okay, point proven. kaffeine-xine works great and I should've listened to you in the first place. Thanks. :)

---

### Post by tseliot on 2005-10-16
[QUOTE=CAE]Okay, point proven. kaffeine-xine works great and I should've listened to you in the first place. Thanks. :)[/QUOTE]
I'm happy for you, Xine is great!

---

### Post by Takis on 2005-10-16
I install the kaffeine-xine package, but Kaffeine doesn't seem to pick it up. I'll open up Kaffeine, but it won't give me the option to use the Xine engine. Any ideas?

---

### Post by CAE on 2005-10-16
[QUOTE=Takis]I install the kaffeine-xine package, but Kaffeine doesn't seem to pick it up. I'll open up Kaffeine, but it won't give me the option to use the Xine engine. Any ideas?[/QUOTE]

That's weird. After I installed it, the option "Kaffeine" (Xine, although that's all that was there) was available along with "Kaffeine Gstreamer" under Settings > Player Engine.

---

### Post by tseliot on 2005-10-16
[QUOTE=Takis]I install the kaffeine-xine package, but Kaffeine doesn't seem to pick it up. I'll open up Kaffeine, but it won't give me the option to use the Xine engine. Any ideas?[/QUOTE]
Try to uninstall "kaffeine-gstreamer" from synaptic/kynaptic (so that kaffeine will be forced to use xine). And you can also install "xine-ui"

---

### Post by Takis on 2005-10-16
Tried that, didn't work. Kaffeine defaults to its crappy kaboodle engine, and doesn't give me any other options. I tried editing ~/.kde/share/config/kaffeinerc and setting "Last Service Desktop Name" to "kaffeine_part", but Kaffeine complains that it has no idea what kaffeine part is.

Edit: I've the same problem as what's listed here. Unfortunately it doesn't seem to provide a conclusive solution.
[http://www.ubuntuforums.org/showthread.php?t=73078](http://www.ubuntuforums.org/showthread.php?t=73078)
I've asked bored2k whether he managed to solve it, waiting on his PM now.

Edit again: For some stupid reason, a reboot fixed the problem. The Xine engine appears in Kaffeine now. This reminds me of my Windows days... :(

---

