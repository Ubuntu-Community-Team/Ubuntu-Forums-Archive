---
title: "Help with Compiz fusion"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by person_99 on 2008-02-09
I just got Compiz fusion, and so far, it is great, but I haven't figured out how to do much.

Most important:I have 4 virtual desktops, but on my taskbar, it shows 32-64? How can I get this back to 4-8?

2, In the YouTube videos, it shows the windows raising with a transparent cube. I currently have a flat non-transparent cube, how can I get the windows to raise 3d and the inner cube transparent?

3. I currently have my emerald desktop theme as Truglass 0.5. However, I want to change the general colors of things like the start menu, etc. Where can I do this?

4. In some of the videos I have seen online, people had the exit window as a burning window. Where can I set this?

5. Is there a way to change settings quickly, like a profile system or something? 
Example: When I want the fancy desktop settings, I can go to one profile, but when I want to play a game (and not experience the FPS drops) I can go to a profile with lower special effects, without having to manually enable/disable various things..

Any help would be appreciated, especially with my 64 desktop buttons...

---

### Post by rainwalker on 2008-02-10
If you're talking about the workspace switcher in your gnome panel, you can right-click on it and set the number of desktops

To get the cube transparency, install the package "compizconfig-settings-manager" with Synaptic. Then go to System > Preferences > Advanced Desktop Effects Settings and go to the Desktop Cube settings and look under the "Transparent Cube" tab
To get the 3D windows, follow these instructions: [http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

If you're talking about changing the way things look other than your window borders, then what you're looking for is a different GTK theme. To get new ones, check out [www.gnome-look.og](www.gnome-look.og)

In System > Preferences > Advanced Desktop Effects Settings go to the Animations section and you can set specific animations for each action.

To switch between different levels of eyecandy, look under the "Visual Effects" tab in System > Preferences > Appearance

Also, you say you have lots of keyboard buttons? I'm assuming you have multimedia keys (play/pause/stop/next/previous/etc.); to get those to work you can install KeyTouch from [http://keytouch.sourceforge.net/download.php](http://keytouch.sourceforge.net/download.php)

---

### Post by person_99 on 2008-02-10
I don't have gnome, I use KDE, hence  **K**ubuntu, as it says on the top right corner of my posts.

I know how to tweak basic stuff in the compiz manager, but my problem is that even though I am supposed to only have 4 virtual desktops, and the cube has only 4 sides, my taskbar shows 64 button switchers.

> 
If you're talking about changing the way things look other than your window borders, then what you're looking for is a different GTK theme. To get new ones, check out [www.gnome-look.org](www.gnome-look.org)

Again, I have KDE.
I wanted to do my own (custom) themes, which is what I was trying to say in my first post.

> Also, you say you have lots of keyboard buttons? I'm assuming you have multimedia keys (play/pause/stop/next/previous/etc.); to get those to work you can install KeyTouch from [http://keytouch.sourceforge.net/download.php](http://keytouch.sourceforge.net/download.php).
When I said "Desktop buttons", I was talking about in the OS, on the taskbar. I didn't mean as in Keyboard buttons.
I wanted to know if there is an area where I can basically select a different profile that has different compiz settings then my current one. 
Example #2:

Profile 1 = Rotate cube enabled, paint with fire enabled, etc.
Profile 2 = Rotate cube disabled, paint with fire enabled, etc.
Profile 3 = Rotate cube disabled, paint with fire enabled, etc.

---

### Post by buntu_Geek on 2008-02-10
> **person_99 said:**
> Is there a way to change settings quickly, like a profile system or something? 
Example: When I want the fancy desktop settings, I can go to one profile, but when I want to play a game (and not experience the FPS drops) I can go to a profile with lower special effects, without having to manually enable/disable various things..


There is an option for exporting your profile,,,,
in the CompizConfig Settings manager..(CCSM--> Preferences)

You can set up your different profiles and export them when you think that you hav done with it....

give them a name ...

Then you can switch between them in the same preferences tab as and when you like.... just like that....

Hope this helped...

---

### Post by buntu_Geek on 2008-02-10
> **person_99 said:**
> 
4. In some of the videos I have seen online, people had the exit window as a burning window. Where can I set this?


You can configure these kind of Eye Candy stuffs in the Animation Plugin(in Effects category)....

In Close Animation Tab you could add your effect or change the existing one through the edit option....
Check that out....

That might help ...

---

### Post by rainwalker on 2008-02-10
Ah, I'm sorry, I didn't see you were running Kubuntu

---

### Post by person_99 on 2008-02-10
Thanks buntu, the profiling system seems to work good, and I found the the animation plugin you were referring to. I still have the flat solid cube, and the annoying amount of desktops on my taskbar.

---

### Post by buntu_Geek on 2008-02-10
For getting the 3D desktop Cube... i would suggest you the following link:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by mtgrocks04 on 2008-02-11
In the compiz-settings manager set the number of virtual desktops to 4, that should fix your problem :)

---

