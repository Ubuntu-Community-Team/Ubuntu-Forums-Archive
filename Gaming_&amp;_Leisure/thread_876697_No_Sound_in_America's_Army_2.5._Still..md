---
title: "No Sound in America's Army 2.5. Still."
date: 2008-08-01
forum: Gaming &amp; Leisure
---

### Post by metacognition on 2008-08-01
Yep. This problem has been going on and on and on. Is there no solution? I've searched these forums, Google, Cuil and I've tried all their remedies but still none work! Can someone help me? And solve this problem once and for all. Thanks.

Other:
America's Army 2.5
libopenal0a (Kubuntu)
Kubuntu 8.04

---

### Post by kdorf on 2008-08-01
I haven't played America's Army myself, but I did have a problem getting sound in UT2K4.

If I'm not mistaken, America's Army is based on the Unreal Engine and the fix should be similar. In the install directory there should be an OpenAL lib (check "System" subdirectory, if it exists). Delete it (or back it up, if you like) and create a symbolic link in its place that points to the OpenAL library with the same name in /usr/lib.

I can't say definitively that this will work, but it worked for me with UT2K4. Good luck.

---

### Post by metacognition on 2008-08-01
Hmm, thanks. I'm going to try that..

---

