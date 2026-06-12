---
title: "Finally! Permanent menus and buttons... maybe?"
date: 2012-01-27
forum: Desktop Environments
---

### Post by Sven Sorensen on 2012-01-27
I'm pretty sure I'm not the only one REALLY annoyed by the lack of an option, in Unity, to keep windows buttons and menus always visible in the top panel.
Maybe there's a way to finally fix this annoying bug, err.. feature of Ubuntu's new UI: the last version sports a new feature called Menus Discovery that basically let menus and buttons to be visible for a few seconds when a program is launched... but then they fade away again. ](*,) ([http://www.ubuntuvibes.com/2012/01/unity-50-brings-new-features-in-ubuntu.html](http://www.ubuntuvibes.com/2012/01/unity-50-brings-new-features-in-ubuntu.html))
The duration of this Discovery thingy can be tweaked through CCSM... setting it to a year could finally do the trick for me... however, there is a maximum limit of 10 seconds.

Here's my call for help: could an hex editor remove the limit? Something like that workaround for the Magic Lamp effect: [http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/343679-howto-magic-lamp-genie-effect-os-x.html](http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/343679-howto-magic-lamp-genie-effect-os-x.html)
If we can get rid of the time limit, we can finally have a way to customize Global Menu's behavior... 
Does anybody have the know-how to try that?

---

### Post by u2nTu on 2012-02-22
+1,  but desperately, longingly so.

---

### Post by tweakt on 2012-05-29
I tried, but it seems to be internally capped:

gconftool-2 --type int --set /apps/compiz-1/plugins/unityshell/screen0/options/menus_discovery_duration 86400

Setting these values beyond limits makes them revert to default values :-(

---

### Post by tweakt on 2012-05-29
You should cc: to this bug. iaz has a build with a patch to enable this you might be interested in testing.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/789979](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/789979)

---

