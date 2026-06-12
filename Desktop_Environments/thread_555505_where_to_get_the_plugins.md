---
title: "where to get the plugins ???"
date: 2007-09-20
forum: Desktop Environments
---

### Post by hellolijo on 2007-09-20
hi,
     i am using 6.06 version of Ubuntu..
     i want to play the MP3 and MPEG files in the Totem Media Player 
     i read the documentation of restricted formats community
     But i cant solve my problem
   
     where i can find the necessary plugins for the Totem Player
      

Help me as fast as possible

Thank u

---

### Post by Midwest-Linux on 2007-09-20
I have the Ubuntu 7.04, Go to add/remove programs, when you get there...click the top where it says Ubuntu supported, click it to all available, then slightly to the left click media or audio video, then just slightly to the right from that you will see the various things to add to your system, click restricted G-streamers..( I click all of them) ...hit apply on the bottom and it will download and install and them you should be good to go. Like I said I have ubuntu 7.04 , I do not have the 6.06 so I do not know how that differs... I am sure others will be here to add to this....Let us know how it works out...

---

### Post by Wolki on 2007-09-20
> **Midwest-Linux said:**
> Like I said I have ubuntu 7.04 , I do not have the 6.06 so I do not know how that differs... I am sure others will be here to add to this....Let us know how it works out...

I'm having a bit of trouble remembering how it was on dapper, iirc you couldn't just select all applications but  had to check two boxed, "community supported" and "non-free applications". Or was that breezy? One of both ways should work, you'll see which one when you look at the "Add/Remove Applictions" window.
Then just search for gstreamer and install all the plugins you find there.

If you have any problems, there are detailed instructions for installing support for many media formats at [https://help.ubuntu.com/community/RestrictedFormat](https://help.ubuntu.com/community/RestrictedFormat)

---

### Post by jim_p on 2007-09-20
Have a look at the medibuntu repository
```
# Medibuntu repository
deb http://packages.medibuntu.org/ dapper free non-free
```

Also, try changing your default Ubuntu repo from 
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted

 to 

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```

---

