---
title: "two similar admin accounts behaving differently"
date: 2009-05-11
forum: General Help
---

### Post by Andrew Golightly on 2009-05-11
HI everyone,

Weird problem. Well actually there are 2.

So 2 accounts on Jaunty..

1. I can enable extra visual effects for my account. I created another account (with admin rights) and on attempting to enable extra visual effects, it searches for drivers, then just says that it is unable to do so.

2. I don't see the wireless icon in the 2nd account. Wireless access works fine on my account.

I installed Ubuntu on this laptop by installing it through Windows.. but that shouldn't affect it in anyway right? Apart from slightly slower performance?

Curious problems..

Help much appreciated.
Andrew

---

### Post by Andrew Golightly on 2009-05-12
Ok... something I came across.

I downloaded the Compiz-Check script.

It ran it on my account (remember same computer!!) and all passed.

I ran it on the other account.. and got the error that

a Software Rasterizer is in use.

Any help on that?

---

### Post by bodhi.zazen on 2009-05-12
Not sure if it makes a difference, but how did you switch accounts ?

Did you log off and back on or use the "switch users" option ? 

If that does not fix the problem perhaps it is another group you need to add to user 2 ?

groups user1
groups user2

---

### Post by BslBryan on 2009-05-12
Hello, Andrew Golightly. :-)

Hmm...  How strange.  I've never heard of this type of behavior.  

A software rasterizer is a graphics renderer/emulator.  I don't know how much that helps, because I, unfortunately, do not have an understanding of what that is, exactly.

May I suggest deleting that user account, and possibly creating a similar one?

I'm sorry I couldn't have been of greater help.

If I think of anything else, I'll post here.

Tell me what you decide to do. :-)

---

### Post by Andrew Golightly on 2009-05-13
Hi there.

I had switched between the two accounts. I notice that even when I logged out of my account, I could not enable the visual effects for the other person. However, on logging out of everyone, and re-logging back in as someone, then that person could enable their visual effects. This was true for everyone.

Looks like it was a memory issue? So resolved.

Also, the wireless icon came up when I had logged in as a user by themselves i.e. without switching into another them. I guess that makes sense, as the computer is already connected to a network.

Well thanks for your help!
Andrew

---

