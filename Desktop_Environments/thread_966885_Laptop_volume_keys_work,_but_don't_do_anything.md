---
title: "Laptop volume keys work, but don't do anything"
date: 2008-11-01
forum: Desktop Environments
---

### Post by snova on 2008-11-01
The volume keys on my laptop are recognized, and appear to be working, but they don't actually do anything.

When I press one of the buttons, they function as expected:

[[IMG]http://img371.imageshack.us/img371/5536/volumekeyssg9.th.png[/IMG]](http://img371.imageshack.us/my.php?image=volumekeyssg9.png)

But then nothing has happened, it's still at zero:

[[IMG]http://img89.imageshack.us/img89/4724/volumemeteror5.th.png[/IMG]](http://img89.imageshack.us/my.php?image=volumemeteror5.png)

And I still do not hear anything.

I am using Intrepid Ibex, with Gnome.

---

### Post by Ecna on 2008-12-04
I have the same problem, it appeared when I upgraded to this onery goat version. I should have stayed with Hardy Heron. :P

I'm on a Compal HEL-80.

Has anyone else figured this one out? Or know a good way to track it down?

Have you had any luck snova?

I found this bug that might be related if it gives anyone a clue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706)

---

### Post by sdennie on 2008-12-05
It sounds like there is a disconnect between the channel being controlled and the channel that is useful.  First, right click on the speaker, select Preferences and try moving the controlled channel to/from PCM/Front.  Check to see if the speaker icon now accurately reflects your volume.  Then, go to System->Preferences->Sound and at the bottom, select the same channel you selected from the volume control applet.

---

### Post by snova on 2008-12-05
I don't think I ever got it to work in Gnome. Eventually I went back to KDE and discovered it *still* didn't operate correctly- but at least then I was in a familiar environment and found the right settings to change.

I think the cause was that it was changing PCM instead of Master. Either way, it works now.

---

