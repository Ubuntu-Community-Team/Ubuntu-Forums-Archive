---
title: "New Jaunty Install. A few (minor) problems."
date: 2009-04-27
forum: General Help
---

### Post by kpkeerthi on 2009-04-27
1. No OSD notifications on mounting and unmounting external USB drives. I do remember seeing "It is now safe to remove your device" message in prior Ubuntu versions. Could this be a bug in the new notification system?

2. I have setup keyboard shortcuts for my favorite applications in CCSM -> Commands. 'Ctrl + Alt + n' is mapped to **nautilus** but it won't launch. I have tried other key combination but no luck either. Shortcuts for other applications work. All my key combination follow the convention Ctrl + Alt + <first-char-of-app-name>. [COLOR="Red"]- Fixed. The command should be **nautilus ~**.[/COLOR]

3. When I shutdown or restart, I see a black screen appearing for a second or two before usplash kicks in. I don't mind this but I could see the boot messages in the black screen when it appears which is rather annoying. I wish the transition from usplash to desktop (during startup) and from desktop to usplash (during shutdown) seamless and flicker free. Is it possble to clear off the boot messages?

4. How do I turn off the shutdown/restart beep? (pcspkr module is already blacklisted) [COLOR="Red"]- Fixed. Turn off sound under System -> Preferences > Power Management -> General -> Extras -> Sound notification. [/COLOR]

---

### Post by 243kof on 2009-04-27
> **kpkeerthi said:**
> 

3. When I shutdown or restart, I see a black screen appearing for a second or two before usplash kicks in.

In my machine, usplash never kicks in on shutdown. No text messages either, just a blank screen. I have this problem since I've upgraded to Jaunty.

> **kpkeerthi said:**
> 
4. How do I turn off the shutdown/restart beep? (pcspkr module is already blacklisted)

Is snd_pcsp module also blacklisted?

---

### Post by kpkeerthi on 2009-04-27
> **243kof said:**
> In my machine, usplash never kicks in on shutdown. No text messages either, just a blank screen. I have this problem since I've upgraded to Jaunty.
 I had this problem in Intrepid. Guess I'm lucky now. :)

> 
Is snd_pcsp module also blacklisted?
I don't have my laptop handy. Will check when I get back home. Thanks for the tip.

---

### Post by bdoe on 2009-04-27
> **243kof said:**
> In my machine, usplash never kicks in on shutdown. No text messages either, just a blank screen. I have this problem since I've upgraded to Jaunty.I get the usplash on shutdown, right after I see the text quickly flicker on my screen (text to the effect of "sudo shutdown -r now"). The usplash progress bar zips by quickly, the screen blanks, then turns a dazzling bright mosaic of colors slowly fading to black, appearing as though the GPU just cooked itself, right before my laptop shuts off. If I log off first before shutting down or restarting, I don't have that problem.

I agree - the shutdown beep is freaking annoying. It is the same beep that happens after issuing "sudo shutdown -r now" or "sudo shutdown now" in terminal, which makes me believe the developers changed how the system shuts down from previous versions. It used to seem orderly, but now seems loud and chaotic.

---

### Post by VCoolio on 2009-04-27
2. check the command; make it for example
```
nautilus /home/yourusername
```

4. system > preferences > power management > general: untick the box under extras about sound. This worked for me where a lot of other tips about blacklisting pcspkr etc did not.

---

### Post by kpkeerthi on 2009-04-27
> **VCoolio said:**
> 2. check the command; make it for example
```
nautilus /home/yourusername
```

I just ran **nautilus** from terminal window and it worked; so I assumed it would work the same in shortcuts. Anyways, I'll give 'nautilus /home/<user>' a shot. 

> 
4. system > preferences > power management > general: untick the box under extras about sound. This worked for me where a lot of other tips about blacklisting pcspkr etc did not.
Interesting. I did not notice this option.

Thanks for your help.

---

### Post by kpkeerthi on 2009-04-27
Thans vcoolio. You tips worked.

---

### Post by 243kof on 2009-04-28
The tip to turn off the "sound" box under Power Management didn't work for me :( 
I had to disable system beep completely by blacklisting pcspkr and snd_pcsp. This is not ideal for me, although I can still get a visual alert in place of the beep (System -> Preferences -> Sound -> Sounds tab -> Visual alert). Any hope that this issue be resolved in the next few updates? :P

---

### Post by Chainz on 2009-06-22
```
$ blacklist pcspkr
bash: blacklist: command not found
```

Power management preferences either didn't worked out :(

---

