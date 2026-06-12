---
title: "KDE Multimedia Keys Works but how to modify?"
date: 2007-01-23
forum: Desktop Environments
---

### Post by eldaria on 2007-01-23
Hello, 

I have a Logitech Keybaord connected to Kubuntu Edgy.

The multimedia keys are working, but I can't find anywhere how to modify what they do or how they do it.

I looked in the System Settings->Accessibility-Input Actions
But the Keys are not configured in here.
I also looked in kmix, but they are not configured there either.

The reason is that I want to modify them is that the volume key changes 10% at a time, this is way to large steps, I want to make them 1% steps.

Also in Amarok the Play/Pause button starts the music from the beginning instead of Pause when already playing. 

Where can I modify this behavior?

I found the file where I think the events from the keyboard are sent to the system.
I found this in /usr/share/apps/kxkb/ubuntu.xmodmap

```

keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext 

keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume

```

But again I can't see where to modify the actual values of Volume changem or what the action is called for Play/Pause instead of Play only.

Any hint's highly appreciated. ;-)

Brian.

---

### Post by lvanderree on 2007-02-02
Maybe this can do what you want, found it on google, so just copy-pasted it:

> 
```

sudo apt-get install xbindkeys xbindkeys-config
xbindkeys --default > ~/.xbindkeysrc
xbindkeys-config

```

This will bring up a but-ugly configuration screen. Just click "New" and assign a remark to the new shortcut. Then press "Grab" and press the combination you want


---

### Post by g8m on 2007-02-03
Input actions is one place, but I believe there is also a keyboard-shortcuts, with 3 tabs to modify the key behavior. Also apps like amarok have separate keyboars-shortcut configuration screens. Very confusing in KDE. Also kmix (volume control) has a configuration tool for volume up and down. Although with my KDE install, volume down using the keyboard wheel doesn't work, volume up does. Weird.

---

### Post by michael003 on 2007-03-01
After not finding anything about this issue, I dove into the source code. The step size is not configurable, but if you press Ctrl+VolUp/VolDown it should change in steps of 1%. (Ctrl+VolUp doesn't work on my computer though, although Ctrl+VolDown does.)

The README file with the kmilo source code says
> If you use CTRL in conjunction with volUp/Down it changes the volume by 10, otherwise by 1.

which contradicts the actual implementation. It makes more sense (to me at least) to do it as the README states.

---

### Post by eldaria on 2007-03-02
Interesting, the ctrl+Volume works.
But that must be implemented somewhere in code, but question is where, I wonder should we enter it as a bug?

And I agree the way you say the readme states it should work, would make more sense.
Could it be the way (k)ubuntu implemented it, that someone got it wrong? :-)
Have not tried any other distributions since Kubuntu 6.06 came out and before that it was windows. :-)
What source did you download by the way?
could be fun to see how they did it.

---

### Post by michael003 on 2007-03-02
> **eldaria said:**
> But that must be implemented somewhere in code, but question is where, I wonder should we enter it as a bug?
Here's the relevent code: [http://websvn.kde.org/branches/KDE/3.5/kdeutils/kmilo/generic/generic_monitor.cpp?revision=624936&view=markup](http://websvn.kde.org/branches/KDE/3.5/kdeutils/kmilo/generic/generic_monitor.cpp?revision=624936&view=markup)

If I have time I might hack it and submit a patch.

> **eldaria said:**
> Could it be the way (k)ubuntu implemented it, that someone got it wrong? :-)

No -- it's directly from KDE.

---

### Post by eldaria on 2007-03-02
> **michael003 said:**
> Here's the relevent code: 
If I have time I might hack it and submit a patch.


Great, I will look forward to that.

I will also try and look at the code, will see if it makes any sense to me. ;-)
I'm new to coding in linux, I used to do some coding in Visual Basic, but hey it might be a learning experience. :-)

Actually the function of the volume key be it 1% or 10% should be configurable, since if for example you have a keyboard with one button for volume up and one for down, pushing it 100 times to go from 100 to 0 or other way around, would be a pain.

However on some keyboards including both of mine, there is "knob" so it is very fast and easy to adjust, and here a 1% step would make more sense.

---

### Post by JanusDC on 2008-02-16
> **michael003 said:**
> After not finding anything about this issue, I dove into the source code. The step size is not configurable, but if you press Ctrl+VolUp/VolDown it should change in steps of 1%. (Ctrl+VolUp doesn't work on my computer though, although Ctrl+VolDown does.)

The README file with the kmilo source code says


which contradicts the actual implementation. It makes more sense (to me at least) to do it as the README states.

It still working like you said. I have a HP Pavilion dv2745se and this works exactly as you said. Thanks for your discovery :)

---

