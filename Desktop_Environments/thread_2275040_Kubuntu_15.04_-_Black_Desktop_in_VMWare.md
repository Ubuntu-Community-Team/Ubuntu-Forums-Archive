---
title: "Kubuntu 15.04 - Black Desktop in VMWare"
date: 2015-04-23
forum: Desktop Environments
---

### Post by yahyavi on 2015-04-23
Hello,

I have a fresh installation of Kubuntu 15.04 64bit in VMWare 11. 
To get proper resolution you have to install VMWareTools. After installing VMWaretools the desktop does expand to my resolution but most of the desktop is black and cannot be right clicked as if it is not at the correct the resolution. 
I have attached a picture to clarify what I mean (it is resized the actual resolution is 2560x1440). Any idea how to fix this? (On the lockscreen it is actually at the correct resolution)

[IMG]https://i.imgur.com/Q33jMZc.png?2[/IMG]

---

### Post by sammiev on 2015-04-23
Ran into the same problem as you and never found a fix for it after updates were released a few months back.

Was hoping for a fix by release date, it never happen to any other of the flavors with 15o4.

---

### Post by yahyavi on 2015-04-23
Such a shame! I am loving KDE 5 and would love to move to 15.04.
The weird thing is it seems to work for a moment during login and a moment right before shut down for a few seconds.

I had a look at unifying outputs, but it doesn't seem to work either. Open-VM-Tools doesn't work either and you lose hardware acceleration.
Really hope someone finds a solution.

---

### Post by Ronald_Vance on 2015-04-24
I had the same problem. The desktop seems to correct itself after logging out and logging back in. As it stands plasma desktop doesn't seem to play nicely with VMware's Dynamic resolution.

---

### Post by sammiev on 2015-04-24
Now 15o4 has been rolling out, I hope to see a fix for this issue. It seems Ronald found away around it for now.

It seems some work was done on it as it would not correct itself for a few of us at the time the new desktop rolled out in the dev stages.

---

### Post by yahyavi on 2015-04-24
Just tried it and can confirm log out and login can fix the problem. 
Hope a permanent fix comes out soon.

---

### Post by ninja2 on 2015-04-30
Just wanted to report the same error :

_**Before the logout --> login trick :**_

[IMG]https://i.imgur.com/PxHjntG.png[/IMG]


_**After the logout --> login trick :**_

[IMG]http://i.imgur.com/KLeXzpQ.jpg[/IMG]

---

### Post by traction_music on 2015-08-17
Just a thread bump - another user here with the same configuration and the same issue. Would be great to get it patched.

---

### Post by deoren on 2015-09-09
Same problem here. As others have noted the log out/in trick works to temporarily resolve the problem. It's worth noting that the open-vm-tools package produces the same results.

---

### Post by jeremygc on 2015-10-13
Same problem here. Still no resolution :(

> **yahyavi said:**
> Hello,

I have a fresh installation of Kubuntu 15.04 64bit in VMWare 11. 
To get proper resolution you have to install VMWareTools. After installing VMWaretools the desktop does expand to my resolution but most of the desktop is black and cannot be right clicked as if it is not at the correct the resolution. 
I have attached a picture to clarify what I mean (it is resized the actual resolution is 2560x1440). Any idea how to fix this? (On the lockscreen it is actually at the correct resolution)

[IMG]https://i.imgur.com/Q33jMZc.png?2[/IMG]

---

