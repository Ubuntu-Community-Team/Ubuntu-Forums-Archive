---
title: "Xubuntu resume from hibernation goes to blank screen"
date: 2017-04-29
forum: Desktop Environments
---

### Post by kahukowhai on 2017-04-29
I have Xubuntu 16.04.2 and when it was first installed, hibernation was very reliable. However in the last few months quite regularly it will not start the GUI properly after resuming from hibernation.

My graphics card is NVidia GTX750 using the NVidia drivers and after some updates were installed and there was no resolution of the resume problems I looked at the logs and found the one about there being a mismatch between the drivers and the API, so I updated the driver files and that one went away. After that the resume became more reliable but I am still getting it failing about every two weeks.

What will happen is the computer will show a completely black screen and the pointer will be an x shape, now if you press Ctrl Alt F1 it gets you out to a shell and from there you can log on to ubuntu. the messages I could see on the screen say one of the last things it has done is started LightDM. 

If I type startx it will start the normal desktop GUI but without the applications it has restored. 

Then if I bring up Task Manager I can see applications from the resume running in the system, they are obviously linked to a different desktop session than the one I am in right now and I can't see a way of getting to that session.

Then because there are applications that are already running in the other session and some of them will only single instance I can't start them in the current session because they are already running in a different session. At this point all I can do is to pull the plug.

So, questions are
- is it possible to get to the other desktop session if this is happening since startx just starts a new session
- what logs do I look in to try to work out what the problem is.

---

### Post by eelie on 2017-04-30
hello, not sure if this is related but whenever I go to suspend and then resume from a suspend mode, I don't get a blank screen like you but rather all the windows in Ubuntu get some extraneous lines and borders and the close, minimize buttons disappear. I have to logout or restart the computer to get it back to normal. 

This problem exists for me in Ubuntu 16.04 and 17.04. Have NVIDIA Quadra m4000m (375 version) on Xeon.

Any idea if these are related?

---

### Post by wildmanne39 on 2017-04-30
eelie please start your own thread so the both of you can get the individual help you need.
Thanks

---

