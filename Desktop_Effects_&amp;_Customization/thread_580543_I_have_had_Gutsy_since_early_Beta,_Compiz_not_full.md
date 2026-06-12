---
title: "I have had Gutsy since early Beta, Compiz not fully present..."
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by Jim March on 2007-10-18
I appear to be punished for using Gutsy in Beta.  Now that it's fully released, I can't get one key window.

I'm running a single-core Celeron 1.6 laptop of recent make (Acer 3680) with 1.5gig RAM and the Intel 945 graphics chip.  I'm getting the same issue running the "intel" and "i810" drivers.

Background: I was trying to follow the directions for getting rid of the brain-dead "snap to grid" effect in Compiz found here:

[http://kevin.vanzonneveld.net/techblog/article/disable_snapping_windows_in_compizfusion/](http://kevin.vanzonneveld.net/techblog/article/disable_snapping_windows_in_compizfusion/)

At 52 seconds in, you can see he goes to "appearance" and then the "visual effects" tab.  So far so good, I can get there.

But I only have THREE radio buttons: "None", "Normal" and "Extra".  

In Kevin's video, he has a fourth button - I can't catch the name but it leads to a whole universe of settings and fine-tuning I don't have.

Now, I could add “gnome-compiz-manager” in Synaptic and get some controls.  But I can't turn off snap-to-grid with that thing and it's otherwise a buggy kluge.  For starters, all settings done there are re-set to default the moment I reboot.

I want the full settings normal to Compiz.  I don't think I should be punished for being a beta user - that's insane.

I've tried fully removing everything Compiz-related in Synaptic and starting over.  Didn't help.

Anybody have a clue what's going on here?

---

### Post by mrvertigo on 2007-10-18
are you current on updates? have you tried requesting a reinstall from synaptic, and BTW dont be afraid of the compix manager......

---

### Post by Jim March on 2007-10-18
Updates were the first thing I tried.

And I'm not "afraid" of Compiz Manager, it simply cannot turn off the window location snapping that is BY FAR the most disgusting part of Gutsy.

I want the settings that fresh Gutsy users seem to have access to.

---

### Post by z0phi3l on 2007-10-18
Install this,


```
 sudo apt-get install compizconfig-settings-manager
```


That should get you the extra settings you desire, for some reason it wasn't installing in the Beta, don't know if it was fixed or not for Live.

---

### Post by Jim March on 2007-10-18
Oh thank GOD.  Yeah, that helped.  A lot.

OK.  Now to get a cube instead of just two flat sides to a pane (sigh).

---

### Post by mrvertigo on 2007-10-18
lol

---

### Post by sharp65 on 2007-10-19
I installed ccsm but I'm not quit sure how to get a cube. I'm pretty sure I enabled it in the settings manager, but I'm just getting 2 flat panes back to back. Anyone know what options I need to chose?

---

