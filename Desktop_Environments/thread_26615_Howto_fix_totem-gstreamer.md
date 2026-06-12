---
title: "Howto fix totem-gstreamer"
date: 2005-04-13
forum: Desktop Environments
---

### Post by philcolbourn on 2005-04-13
I broke totem-gstreamer because I thought I would try totem-xine.

Until just now, I had no idea how to fix it and no amount of installing or reinstalling or purging would work.

Then to help someone it was suggested the gstreamer-plugins should be installed.
Why didn't I think of that?

I installed the package and some things now worked.
I then decided to get all gstreamer bit (just in case) with apt-get install gstreamer0.8*.

I also installed w32codecs from another site.

Then I remembered a gstreamer register program (gstr-register) and ran it.

Now I can play all of my test video files and sound seems to work.

I hope this helps someone.

---

### Post by soul_rebel on 2005-04-13
you mean you are watching divx with totem-gtstreamer?

---

### Post by shupacanucks on 2005-04-13
How do you start gstr-register?

---

### Post by Bob D. on 2005-04-13
[QUOTE=shupacanucks]How do you start gstr-register?[/QUOTE]
The correct command is 'gst-register-0.8'.

Bob

---

### Post by soul_rebel on 2005-04-13
I am getting much better performance with totem-xine, although i managed to get totem-gstreamer decode divx.

---

### Post by philcolbourn on 2005-04-18
[QUOTE=soul_rebel]you mean you are watching divx with totem-gtstreamer?[/QUOTE]
 I seem to be able to play divx files.

---

