---
title: "rockbox and a sansa view"
date: 2009-07-11
forum: Desktop Environments
---

### Post by Mia1990 on 2009-07-11
will rockbox firmware work on ubuntu with no problem i am looking for a way to get my sansa view to work on ubuntu and found that this may be a way to do so.

---

### Post by Chronon on 2009-07-11
A player using the Rockbox firmware just behaves as a UMS device. Ubuntu *should* support UMS devices just fine.  (There were some bugs with libgphoto2 which I worked around -- not sure if the fixes have made it in yet.)

Unfortunately, Rockbox isn't supported on the View yet.  

You can see the supported players on the Rockbox main page: [http://www.rockbox.org](http://www.rockbox.org)

---

### Post by Mia1990 on 2009-07-11
would you know any firmware that does support the sansa view or just any in general

---

### Post by Chronon on 2009-07-11
Sorry, Rockbox is the only alternative firmware that I'm aware of for audio players.

Are you concerned about having more features on the player itself or just managing your music in Linux?  I was under the impression that the View supported MSC mode (behaving as a UMS device).

---

### Post by Mia1990 on 2009-07-11
> **Chronon said:**
> Sorry, Rockbox is the only alternative firmware that I'm aware of for audio players.

Are you concerned about having more features on the player itself or just managing your music in Linux?  I was under the impression that the View supported MSC mode (behaving as a UMS device).

It works some of the time but it's a battle to get it to work.I'm not concerned about having more features just looking for something to managing my music in linux a little better.

---

### Post by Chronon on 2009-07-11
Ah.  I believe you will find this bug report relevant:
[https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/355998)

There are a couple of workarounds in there that I tried (I'm not sure which one worked for me but I'm not seeing this behavior anymore).

---

### Post by Mia1990 on 2009-07-11
Thank you i'll check the link out and see if i can get it to work better.
Mia

---

### Post by Chronon on 2009-07-11
You're welcome.  Good luck!

---

