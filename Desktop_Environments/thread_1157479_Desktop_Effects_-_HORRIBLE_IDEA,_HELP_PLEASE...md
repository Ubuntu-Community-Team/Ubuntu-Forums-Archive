---
title: "Desktop Effects - HORRIBLE IDEA, HELP PLEASE.."
date: 2009-05-12
forum: Desktop Environments
---

### Post by GeistDev on 2009-05-12
Ok so I am using and older Dell (with on-board graphics card) and have been running Kubuntu 9.04 fine and loving it.  I was bored earlier and was tampering with the desktop settings and I clicked "enable desktop effects"... horrible mistake.  Kubuntu froze.  I restarted Kubuntu and to my dismay, the settings had been saved.  I logged in with my username and password, but then the screen forever stays at the gray login-splash screen.  I can move the cursor around but nothing more happens - my guess because the KDE4 desktop can't load the "desktop effects" on my system.

So what I need to know now is how do I reverse this with no use of GUI and not even being able to log in?  The ALT-SHIFT-F12 trick won't work here as I have seen others say since I can't get into the desktop...  Is there a command I can run in bash to DISABLE the desktop effects?

Please help me out here, I would HATE to have to reinstall and start over (I just got everything the way I wanted it  :()

---

### Post by aesis05401 on 2009-05-12
kwriteconfig --group Compositing --key Enabled --file kwinrc false

Here is the original thread: [http://kubuntuforums.net/forums/index.php?topic=3099578.0]("http://kubuntuforums.net/forums/index.php?topic=3099578.0")

---

