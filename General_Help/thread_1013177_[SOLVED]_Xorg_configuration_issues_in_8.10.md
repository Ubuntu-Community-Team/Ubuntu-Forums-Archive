---
title: "[SOLVED] Xorg configuration issues in 8.10"
date: 2008-12-16
forum: General Help
---

### Post by anjilslaire on 2008-12-16
All right,

I know with Intrepid there's a snazzy new hands-off xorg.conf file that pretty much ignores itself and any adjustments made to it. In fact, it even says so:
```

# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.

```

This is all fine and dandy when it behaves itself, but when it doesn't, I want to be able to tweak it and make it behave.

Case in point:
I updated my 8.10 Xubuntu install this morning, which grabbed several updates which also included something requiring a reboot. I was in the middle of something else so (out of the ordinary for me) I just clicked "Update" and didn't pay attention to what it was grabbing, then I rebooted later.

After th reboot, the mouse started misbehaving in Firefox, as in the scroll wheel when scrolling "up" suddenly started behaving as if the "Back" button was clicked. In previous Ubuntu releases, I could just fix this by ensuring the following was included in xorg.conf:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping" "1 2 3 4 5"
	Option 		"Buttons" 	"5" 
	Option		"Emulate3Buttons"	"false"
EndSection

```

I've even posted this on my blog months ago, and the traffic I've gotten to that post indicate this is a popular issue:
[http://anjilslaire.wordpress.com/2008/07/03/firefox-3-scroll-wheel-finally-fixed/]("http://anjilslaire.wordpress.com/2008/07/03/firefox-3-scroll-wheel-finally-fixed/")

But, back to the point: xorg is now unfriendly to manual editing. I found th following post which I tried, but it didn't resolve the issue either:
[http://ubuntuforums.org/showthread.php?t=1012911]("http://ubuntuforums.org/showthread.php?t=1012911")

Any thoughts? Is there any way xorg can be tamed, or is it now off-limits?

Thanks

---

### Post by anjilslaire on 2008-12-16
Update:
It was the kernel update to 2.6.27-9-generic.

I booted into 2.6.27-7-generic and all is well. Guess I'll be commenting -9-generic out in menu.lst and running 7-generic until things get sorted :)

Update, part 2:

Ugh, the scroll issue is now occuring again after a 2nd reboot into kernel 2.6.27-7-generic, so it wasn't the kernel that was the problem.

Suggestions?

---

### Post by anjilslaire on 2008-12-16
Also, I"ve tried removing my .mozilla directory as well, in case something was corrupted. No change.

---

### Post by anjilslaire on 2008-12-16
Final update. Found the solution:
```

sudo rmmod psmouse && sudo modprobe psmouse rate=100 proto=imps

```

Permant fix:
```

#Fix mouse for KVM
     options psmouse proto=imps

```
to the /etc/modprobe.d/options or /etc/modprobe.conf file.

credit:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/162790](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/162790)

---

### Post by kanesurfguru on 2008-12-21
Thanks a lot for your post on this fix.

I have my mouse and my scroll wheel everytime I use my kvm switch now, but I have lost my forward and back button, is there something I can put in the code to keep them?

Please help, thank you very much for what you have posted already.

---

### Post by kanesurfguru on 2008-12-21
back to the top

---

### Post by anjilslaire on 2008-12-21
I'm not sure about that one, hmmm....

---

### Post by kanesurfguru on 2008-12-22
Anyone got any ideas now?

Can you hear me now?

---

