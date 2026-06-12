---
title: "Utility for &quot;triggered video recording&quot;"
date: 2006-10-02
forum: Desktop Environments
---

### Post by YigalB on 2006-10-02
I would like to connect a CAM to my Ubuntu machine, leave it all night (and day), and record only when there is a change in the picture, so it will not eat all my disk space and save me going over the whole video later on.
Any idea of a utility that perform this task?

---

### Post by adwait on 2006-10-02
What you are looking for is a motion sensor, and as far as I know, not implementable as a software. There will always be minute changes in the picture, eg: the light etc. Also, I don't think its that easy for a computer to detect these things.....I might be wrong though...

---

### Post by YigalB on 2006-10-02
I agree that a motion sensor is a good solution, but it requires software too.
But yes - software can detect changes in frames, I know some utilities exist for Windows.
And I am Ok to accept non-100% solution, for example false recording.
I would say the algorithm is:
record 30 minus prior to triggering moment and 30 seconds after.
If another trigger occurs during recording - extend recording by 30 seconds.

---

