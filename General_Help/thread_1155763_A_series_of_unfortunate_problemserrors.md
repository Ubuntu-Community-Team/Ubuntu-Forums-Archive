---
title: "A series of unfortunate problems/errors"
date: 2009-05-11
forum: General Help
---

### Post by happinesskills on 2009-05-11
Here are my list of current problems & errors:

1- .SWF files freeze after a couple of frames/seconds.
2- NO sound is being emitted. In System>Preferences>Sounds only OSS doesn't pull up an error, but can't close the test. Also says that ALSA is being used, but I don't have anything that could use it running (like Banshee).
3- Firefox doesn't close. It either stops responding for a while, then closes or just crashes before it closes. (I've had this problem for a while)
4- Kinda like the one above, but most programs either stop responding & then close or they crash before closing.
5- A few other minor problems & errors.

I will update this post as more arise

---

### Post by jonnymccullagh on 2009-05-11
I had a few similar problems on 8.10 but have not experienced similar issues after upgrading to 9.04.

For the Flash/Firefox problem I had tried a few things like clearing the cache and killing pluseaudio but for some reason disabling the Flash plugin then restarting Firefox and renabling Flash got things started again. There may be more info for you in the following thread:
[http://ubuntuforums.org/showthread.php?t=598034&page=2](http://ubuntuforums.org/showthread.php?t=598034&page=2)

hope this helps,
j

---

### Post by pro003 on 2009-05-11
> **happinesskills said:**
> Here are my list of current problems & errors:

1- .SWF files freeze after a couple of frames/seconds.
2- NO sound is being emitted. In System>Preferences>Sounds only OSS doesn't pull up an error, but can't close the test. Also says that ALSA is being used, but I don't have anything that could use it running (like Banshee).
3- Firefox doesn't close. It either stops responding for a while, then closes or just crashes before it closes. (I've had this problem for a while)
4- Kinda like the one above, but most programs either stop responding & then close or they crash before closing.
5- A few other minor problems & errors.

I will update this post as more arise

try disabling visual effects and see if it gets any better..

---

### Post by ralphwroberts on 2009-05-11
I have been experiencing exactly the same problems described above -- Flash videos freezing after a couple of seconds and Firefox crashing being the worse -- since upgrading to 9.04. I've tried everything I can find on this forum and nothing makes any difference.

Does anyone know if the developers are working on this problem?

---

### Post by pro003 on 2009-05-11
it's just the general problems with upgrades I think, if you look around the forum, many people have issues after upgrading... and probably someones working on it too...

---

### Post by happinesskills on 2009-05-12
Allright, It must have been just yesterday because Sound & Flash are working.

The only thing now is Firefox either crashing instead of closing or stops responding, then closes.

Anyone with my previous problems is allowed to hijack this thread.

---

### Post by pro003 on 2009-05-12
> **happinesskills said:**
> Allright, It must have been just yesterday because Sound & Flash are working.

The only thing now is Firefox either crashing instead of closing or stops responding, then closes.

Anyone with my previous problems is allowed to hijack this thread.

do you have any unusual plugins in firefox? or even some themes can cause crashing in firefox...

try to uninstall it

```
sudo apt-get remove --purge firefox
``` 

and than install it again...

---

