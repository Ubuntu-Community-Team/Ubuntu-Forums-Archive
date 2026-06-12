---
title: "Skype suddenly refuses to work (running 64bit)"
date: 2009-05-15
forum: General Help
---

### Post by Kimm on 2009-05-15
Well, the thread title pretty much describes the issue. Today Skype decided to stop working. When I try to execute Skype, the window pops up and then disappears instantly. When I run it from a terminal, all it tells me is "Aborted."

Right now I have the Skype installed from the medibuntu repositories, but I also tried the static and dynamic *.tar files from skype.com, all yielded the same results.

The only thing I've changed since I last ran it is that I've bought a new webcam. But the webcam is working flawlessly in Cheese and Ekiga, and 32bit v4l libraries where installed with skype from medibuntu.

Any ideas?

---

### Post by TB2 on 2009-05-15
I see the exact same symptoms on my fresh 32bit install. I made a thread earlier: [http://ubuntuforums.org/showthread.php?t=1160012](http://ubuntuforums.org/showthread.php?t=1160012)

Also tried the other installation methods. Webcam is working in cheese without problems as well. Have you tried to run a backtrace?

---

### Post by Kimm on 2009-05-15
> **TB2 said:**
> I see the exact same symptoms on my fresh 32bit install. I made a thread earlier: [http://ubuntuforums.org/showthread.php?t=1160012](http://ubuntuforums.org/showthread.php?t=1160012)

Also tried the other installation methods. Webcam is working in cheese without problems as well. Have you tried to run a backtrace?

The backtrace didn't yield any useful results (the same as in your thread actually).

Also, I've confirmed that its a webcam issue. If I unplug the cam, skype can start, if I plug it in while Skype is running it keeps working, but if I restart skype again with the webcam plugged in it crashes.

I should note that I unchecked "use webcam" (or something similar) in skypes config dialog when I got it running, but it still refuses to run while the camera is plugged in.

---

### Post by TB2 on 2009-05-15
Same for me. Skype can start when the webcam is unplugged. If I plug it in while skype is running it keeps running but as soon as I try to use it (e.g. open preferences dialog) skype crashes with the same "Aborted" message. Btw [I filed a bug at skype]("https://developer.skype.com/jira/browse/SCL-482")

---

### Post by Kimm on 2009-05-15
I replied to the bug report and submited my crashlogs as well. Lets hope they can fix this, I pretty much got the webcam to use it with Skype

---

### Post by TB2 on 2009-05-15
Yeah I sure hope so! I installed ubuntu on my girlfriends PC to replace Vista, but if skype ain't working, it sure is a desaster :P

---

### Post by TB2 on 2009-05-16
The reason why there's an error when trying to trace skype is that /usr/bin/skype is just a script running /usr/bin/skype.real with an LD_PRELOAD. But tracing skype.real doesn't reveal anything nevertheless, as there are no debugging symbols.

Btw, unloading the uvcvideo module stops skype from crashing with the cam plugged in. of course this simply prevents the cam from working.

Have you tried any other video conferencing software? For me, none of them work:
- Ekiga can make calls, but video isn't working, and hanging the phone freezes Ekiga
- Qutecom runs once, but when doing something involing the cam, it crashes and then crashes instantly on subsequent runs.
- KPhone can make calls and doesn't crash, but video isn't working either
- Linphone opens a window that is apparently supposed to show the webcam picture but instead it's just green and it refuses to do calls or anything while spitting lots of colourful errors in the terminal.

Does anyone of these work for you?

---

### Post by Kimm on 2009-05-16
> **TB2 said:**
> The reason why there's an error when trying to trace skype is that /usr/bin/skype is just a script running /usr/bin/skype.real with an LD_PRELOAD. But tracing skype.real doesn't reveal anything nevertheless, as there are no debugging symbols.

Btw, unloading the uvcvideo module stops skype from crashing with the cam plugged in. of course this simply prevents the cam from working.

Have you tried any other video conferencing software? For me, none of them work:
- Ekiga can make calls, but video isn't working, and hanging the phone freezes Ekiga
- Qutecom runs once, but when doing something involing the cam, it crashes and then crashes instantly on subsequent runs.
- KPhone can make calls and doesn't crash, but video isn't working either
- Linphone opens a window that is apparently supposed to show the webcam picture but instead it's just green and it refuses to do calls or anything while spitting lots of colourful errors in the terminal.

Does anyone of these work for you?

Ah, that explains the error then.

Other than Skype, I've tried Ekiga, which works flawlessly it seems.
I get the same problem as you with Linphone though.

---

### Post by Kimm on 2009-05-17
Well, I fixed it. It was a UVC driver issue (which is the mother of all webcam related issued apparently).

I solved it by following the instructions on how to compile my own driver here: [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

Marking the thread as Solved :)

---

### Post by TB2 on 2009-05-17
Thanks a lot dude, I'll try it out asap!

---

