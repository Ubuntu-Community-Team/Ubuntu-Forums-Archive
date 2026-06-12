---
title: "Volume OSD disappeared in Breezy"
date: 2005-11-06
forum: Desktop Environments
---

### Post by Takis on 2005-11-06
I use the multimedia keys on my keyboard to adjust the volume in KDE, and I was always able to see the current volume level through the OSD. Now the OSD's disappeared and I can never remember what volume level I'm on. Has it been removed for some reason?

Running KDE 3.5 beta 2.

Cheers!

---

### Post by Takis on 2005-11-07
...and now it's automagically reappeared again, somehow. :confused: 


Ours is not to reason why.

---

### Post by stimpack on 2005-11-07
ooh didn't know KDE could do this, my multimedia controls work in Ubuntu, just assumed Kubuntu didnt do this :) . Is there a config file somewhere or setting dialog I can look at to try and get it to work?

---

### Post by mfyahya on 2005-11-07
I use a laptop and my OSD had disappeared too. I checked System->Preferences->Keyboard Shortuts and the sound control mappings were messed up. Remapping them got the OSD back.

---

### Post by Takis on 2005-11-07
[QUOTE=stimpack]ooh didn't know KDE could do this, my multimedia controls work in Ubuntu, just assumed Kubuntu didnt do this :) . Is there a config file somewhere or setting dialog I can look at to try and get it to work?[/QUOTE]
Well, there's two ways this works: the easy way, or the harder PITA way. Unfortunately I had to go the PITA way because my keyboard doesn't automagically map its keys, but for the moment let's see if yours does.

Go to Settings->Regional & Accessibility->Input Actions.

Have you ever used DCOP calls before? If not, hang tight, I'm going to write a How-To later today, it just takes a little while.

---

### Post by NeoChaosX on 2005-11-07
Is there a way to disable the OSD?

---

### Post by NeoChaosX on 2005-11-07
[QUOTE=mfyahya]I use a laptop and my OSD had disappeared too. I checked System->Preferences->Keyboard Shortuts and the sound control mappings were messed up. Remapping them got the OSD back.[/QUOTE]
What are the sound control mappings? I don't see them listed among the Keyboard Shortcuts.

---

### Post by stimpack on 2005-11-08
[QUOTE=Takis]
Go to Settings->Regional & Accessibility->Input Actions.
[/QUOTE]

Couldnt find an 'Input Actions' there is 'Keyboard Shortcuts' which doesnt seem to have anything applicable and 'KHotkeys' which seems a bit complicated (well I dont understand it at all if im honest)

Anyway I got it working with a xmodmap to XF86RaiseVolume etc.. inelegant imo, but it works.

---

### Post by Takis on 2005-11-08
[QUOTE=stimpack]Couldnt find an 'Input Actions' there is 'Keyboard Shortcuts' which doesnt seem to have anything applicable and 'KHotkeys' which seems a bit complicated (well I dont understand it at all if im honest)[/QUOTE]
KHotKeys is the Hoary name for Input Actions. I'm in the process of writing some [tutorials]("http://ubuntuforums.org/showthread.php?p=476973") for it because it's seriously cool.

---

