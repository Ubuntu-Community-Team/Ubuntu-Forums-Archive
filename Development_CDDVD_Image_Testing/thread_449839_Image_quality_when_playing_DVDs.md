---
title: "Image quality when playing DVDs"
date: 2007-05-20
forum: Development CD/DVD Image Testing
---

### Post by justdedict on 2007-05-20
I am having problems playing dvds on my computer. I am using Ubuntu 7.04 and tried several players, all with the same result. 
The dvd is loaded and plays (more or less), but the quality is very low. I am able to make out the video more or less but there is more green than image, the sound and image are very irregular. 
I've been playing around with codecs but as for now with no result.

Any brilliant suggestions?

Just

---

### Post by smithman89 on 2007-05-20
Well, one thing that may be a factor is:  What are your computer specs?  Of course, if you have an older computer, you will probably encounter poor quality due to the video card.  But if you do have a newer computer that SHOULD be able to run the vids better, if you havent already, install the packages for your video card, like nvidia-glx (or the fiesty equivalent).  One last possibility is that your DVD player/decoder is not working properly.

---

### Post by justdedict on 2007-05-20
It's a Dell Inspiron 1501, no idea about video card specs. The laptop is new.
I am able to play dvds under windows. Also, I am able to play certain dvds (like a salsa instruction dvd I have here). Suppose this one has different codecs or something. Commercial dvds give a lot of problems.

---

### Post by justdedict on 2007-05-20
Ah solved it!

Installed additional packages via [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Thanks anyway smithman for the response.

Just

---

### Post by smithman89 on 2007-05-20
Ok, i did a little reseach, and your notebook has an intgrated ATI graphics chip in it.  My suggestion is to install the ATI graphics package if you havent done so already.  Another thing, if the DVD has menus, you should use the gxine movie player, ive had trouble with other programs because they dont support menus.  If these dont work, keep trying out codecs.

---

