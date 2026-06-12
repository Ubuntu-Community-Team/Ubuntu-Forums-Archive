---
title: "Natty, Unity, all &quot;panels&quot; missing"
date: 2011-04-29
forum: Desktop Environments
---

### Post by ljg_3 on 2011-04-29
Updated overnight, all the panels, dockbar, etc. are missing. I did happen to notice during the update that something like user/frontend failed. Any help, was very much looking forward to trying out unity.

---

### Post by Krytarik on 2011-04-29
If you had the "Desktop Cube" enabled before, try this:

- see this post:
[]("http://ubuntuforums.org/showthread.p...8#post10734118")[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)
- but you may only need to add "unityshell" to the mentioned key, and make sure "wall" isn't set
- to launch "gconf-editor", just create a launcher for it at your desktop with the very command
- the path to the Unity specific profile may be "/apps/compizconfig-1/profiles/unity/general/screen0/options", please give feedback on that

Greetings.

---

### Post by KegHead on 2011-04-29
Hi!

You may need to update again.

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

suao apt-get install linux-image -f

Restart.

KegHead

---

### Post by ljg_3 on 2011-05-01
Hello, and thanks so much for the input. 


To Keghead.
            You were pretty much right, some files didn't download, I just went through synaptic. Thanks again.

To Krytarik
             Thanks for the launcher tip, I'm a noob and didn't know. There were no panels so that made navigation tons easier. Disabling the wall did nothing for my problem, however the location was right, and you showed me an easy way to accomplish tasks without much point and clicking. Thanks.

---

### Post by Krytarik on 2011-05-01
Sorry, there was a faulty link in my previous post, although I tried to correct it earlier, but it's correct now, please check again there.

---

