---
title: "Volume knob controls wrong volume"
date: 2007-03-21
forum: Desktop Environments
---

### Post by thecolorifix on 2007-03-21
So my multimedia keys work great except that the volume knob controls the "master" volume instead of the "PCM" volume, which is the one that actually alters the volume. The master volume does absolutely nothing as far as I can tell.

I'm running Ubuntu Ultimate edition with the GNOME desktop environment. I had Kubuntu and it was an easy fix, in the sound mixer you could just right click on the volume slider and assign the multimedia keys to different volumes. Well, that doesn't work in GNOME, and I've been googling like crazy but I can't find any answers.

Thanks in advance for any help.

---

### Post by ComplexNumber on 2007-03-21
> **thecolorifix said:**
> So my multimedia keys work great except that the volume knob controls the "master" volume instead of the "PCM" volume, which is the one that actually alters the volume. The master volume does absolutely nothing as far as I can tell.

I'm running Ubuntu Ultimate edition with the GNOME desktop environment. I had Kubuntu and it was an easy fix, in the sound mixer you could just right click on the volume slider and assign the multimedia keys to different volumes. Well, that doesn't work in GNOME, and I've been googling like crazy but I can't find any answers.

Thanks in advance for any help.
right click on the volume applet, select preferences. you can change from master to PCM there. or is that what you're saying doesn't work in gnome? it works on mine.

i don't know as yet why your master control does nothing. if you right click on the volume applet and select 'open volume control', then go to Edit' in the menu, then 'change device'. do you have the correct sound device selected?

---

### Post by thecolorifix on 2007-03-21
> **ComplexNumber said:**
> right click on the volume applet, select preferences. you can change from master to PCM there. or is that what you're saying doesn't work in gnome? it works on mine.

i don't know as yet why your master control does nothing. if you right click on the volume applet and select 'open volume control', then go to Edit' in the menu, then 'change device'. do you have the correct sound device selected?

No, all the volume controls int he software work fine, it's just that the volume knob on my keyboard controls the "master volume", which does NOTHING.

I have the correct device selected, yes.

---

### Post by DarkOx on 2007-03-21
I had the same problem, and found two ways to fix it. The first method was specifically for my soundcard: I had to log out into a console and type: "sudo modprobe -r snd_intel8x0" and "sudo modprobe snd_intel8x0 ac97_quirk=hp_only", after which my volume keys worked normally.

Before I found that solution though, I used a more generic one, using a program called keytouch to change the bindings. Here's how I got it working:
 
1. Install keytouch and keytouch-editor (both are in the repositories, but you might need to install the beta keytouch-editor from [here]("http://sourceforge.net/project/showfiles.php?group_id=111201"))

 2. Launch keytouch-editor, and make a file for your computer (mine was a Dell 600m). I selected the default keyboard setting. After that, go to New to add a key, and it will ask for you to press one of your volume keys. You then have to associate a program that will change your volume to each key. I used "aumix -w -3" for volume down and "aumix -w +3" for volume up (I had to download auxmix first. It's in the repositories). Save.

 3. I think that you could use amixer to control the volume, and maybe it's better because it's installed in Ubuntu by default. However, I couldn't figure out it's syntax and I didn't feel like experimenting with it.
 
4. Open up keytouch, and tell it to import the file you made in keytouch-editor. Select that file, and apply it (it's defaults should be fine). Test your buttons. The volume bar wouldn't appear on mine (which is what led me to search for the other solution) but it worked fine otherwise.

Hopefully that helps.

---

### Post by Hendrik van den Boogaard on 2007-03-28
I have the same problem on my A8N-VM CSM motherboard. In Dapper the volume-up and down keys change the 'headphones' output which is on the front of the computer.

In Feisty it worked when I tried alpha 3 but now on beta the volume up and down actually changes the microphone slider. I wish there was a setting somewhere to set WHICH input you can change when using the multimedia keys somewhere. This shouldn't be too hard to program...

I might even code it myself when I have the time ;).

So request: make an additional select box in gnome-volume-control which you can set the volume slider that will be controller with the volume-up and down buttons on the keyboard.

---

### Post by hotani on 2007-04-14
same here. Volume controls are attached to the 'front' speakers and not PCM. I'm using Feisty.

EDIT: fixed. Go to System -> Preferences -> Sound
Under "Devices" tab, section "Default Mixer Tracks", select the one you want the volume controls to change.

---

### Post by aquamammal on 2007-11-13
I had this problem too. But after this It's fixed. Thanks.

---

