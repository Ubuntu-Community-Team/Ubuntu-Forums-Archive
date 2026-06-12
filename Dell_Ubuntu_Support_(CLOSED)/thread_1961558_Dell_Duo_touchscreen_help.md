---
title: "Dell Duo touchscreen help?"
date: 2012-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by unused_bagels on 2012-04-19
I've been using this tutorial:
[http://ubuntuforums.org/showthread.php?t=1658635](http://ubuntuforums.org/showthread.php?t=1658635)

I used to run Ubuntu "Ubermix" which has a package for the Duo to make the hardware work.  It was too restrictive, so I installed the newest version (which I love)

I got most things working, but my biggest problem is twofold:
 
1) I can't pull off click-and-drag with the touchscreen.
    (I can drag the mouse, but the drag doesn't register until after I pick up my finger, which doesn't really acheive anything.)

2) I want to zoom in my screen (change the resolution to make everything bigger) for my fat fingers.  
    I used to have an app that let me do it with the push of a button, but the app doesn't work in v12.  I don't want to just zoom in on part of the screen, I just want to be like, boink! lower resolution!
 
Can anyone help me out?

---

### Post by unused_bagels on 2012-04-23
update: Also, if I use the on-screen keyboard and touchscreen to log in to my computer, my touchpad mouse doesn't work for the rest of my session.

---

### Post by drumour on 2012-04-28
There has been a Launchpad bug raised and patched regarding this touchscreen.

Look out for the package linux - 3.2.0-24.37. [https://bugs.launchpad.net/bugs/913164](https://bugs.launchpad.net/bugs/913164) - if you want more info.

Your usage may vary but I find that installing Easystroke makes my Duo more user friendly. 

In Easystroke I set Button 1 as the gesture button under Behaviour on the Preferences tab. Then when I want to click and drag just a slight pause on touching an object and it drags...

Ubuntu Tweak has a text scaling factor under its Fonts setting and a "close" button only option under its Window setting that makes things a bit easier for fingers...

---

### Post by unused_bagels on 2012-04-29
> **drumour said:**
> There has been a Launchpad bug raised and patched regarding this touchscreen.

Look out for the package linux - 3.2.0-24.37. [https://bugs.launchpad.net/bugs/913164](https://bugs.launchpad.net/bugs/913164) - if you want more info.

Your usage may vary but I find that installing Easystroke makes my Duo more user friendly. 

In Easystroke I set Button 1 as the gesture button under Behaviour on the Preferences tab. Then when I want to click and drag just a slight pause on touching an object and it drags...

Ubuntu Tweak has a text scaling factor under its Fonts setting and a "close" button only option under its Window setting that makes things a bit easier for fingers...

I never could get Easystroke to install.  Something about the ppa or the package, it would never display as something I could install via synaptic.
 
As far as the zoom issue, I partially solved it, as I found the script I used.  Try it, it's awesome.
[http://ubuntuforums.org/showpost.php?p=11874659&postcount=688](http://ubuntuforums.org/showpost.php?p=11874659&postcount=688)
I still have an issue with the touchscreen, though as sometimes if I use it, mouse input will disappear altogether, and I can point at things with the touchscreen, but can't click anything, and the touch*pad* stops working.  It makes me afraid to use the touch-screen.

---

### Post by drumour on 2012-04-29
Easystroke is now available from the precise/universe repositories via synaptic.
I know it may not be helpful but from there Iv'e had no problems - except that in 12.04 it doesnt show up in the systray when it starts which means you dont know its running\ can't configure it!

The workaround I use is this command:
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

Which can be undone/reset with this command:
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier']"

This is explained here for example:
[http://keyable.blogspot.co.uk/2012/04/fix-show-ibus-icon-on-ubuntu-1204-panel.html](http://keyable.blogspot.co.uk/2012/04/fix-show-ibus-icon-on-ubuntu-1204-panel.html)

The zoom script is too complex for me
:)
But Nautilus has a scaling option. Edit -> Preferences->View->Icon View Defaults. This also changes the size of Desktop Icons since Nautilus is the Desktop!

---

