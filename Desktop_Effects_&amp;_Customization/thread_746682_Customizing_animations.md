---
title: "Customizing animations"
date: 2008-04-05
forum: Desktop Effects &amp; Customization
---

### Post by driebel on 2008-04-05
Hi everyone, I'm a super-newbie, slowly becoming accustomed to Ubuntu, and loving it.
I'm not having problems per se, but I'm hoping someone could give me some tips on window dressing.  I've got all the fun toys of Compiz installed, and I thought it would be fun to assign different animations to different types of windows as they close, minimize, etc.  Can someone point me to a good documentation source for compiz that can spell out these  options?
For example, most of my windows close with the spiffy "burn" effect, but I think it would be cool if my mail messages folded up like airplanes.  I can't trigger that on the title of the window, that matches the subject line and is thus different for each message.  Is there a "type," or "name" option that's common to evolution compose mail windows?  More generally, how do I go about finding out the "type"  "name" or "role" of various windows?  What do those properties mean?
Thanks in advance.  I know this is just fluff, but it's not like I have a life or better things to do ;)

Dave

---

### Post by nuclearpidgeon on 2008-04-05
This may work, I don't use evolution, I use thunderbird.
1. Load up a terminal
2. Use this command:
```
xprop WM_CLASS | cut -d\" -f4
```
then click on the window you want a different animation to occur on (make sure you've already opened it)
Keep the terminal window open
3. Open ccsm (System => Preferences => Advanced Desktop Effects Settings)
If you don't have it, type```
sudo apt-get install compizconfig-settings-manager
``` in a terminal
4. Click on Animations
5. Click the appropriate tab (Close, open, minimize etc.) You'd probably want close for sending an email.
6. Click Add
7. Choose your effect, and duration.
8. In Window Match type> (class=%put the thing from the teminal here, minus the percent signs%)
9. OK, close etc.

That may work, I'm not sure
Also check this out:
[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)
I got my stuff from there

---

### Post by driebel on 2008-04-06
That's exactly what I need.  I haven't implemented it yet, but that's the info.  Thanks!

---

