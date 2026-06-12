---
title: "Kubuntu: Can't login"
date: 2007-03-09
forum: Desktop Environments
---

### Post by svetlin on 2007-03-09
Hi,

I started my computer this morning and everything was fine. Then about 40 updates appeared in Adept, I updated, restarted and now get the following message when I try to login:

```
Xserver: warning: unable to write to /tmp; X session may exit with an error
```

I can't login neither in Gnome, nor in KDE or Failsafe. I removed all files from my home dir and from /tmp, but with no result.

This is the output of .xsession-errors:

```
Xsession: X session started for svetlin at Fri Mar  9 12:00:45 EET 2007
/etc/X11/Xsession: line 115: echo: write error: No space left on device
Xsession: warning: unable to write to /tmp; X session may exit with an error

** ERROR **: Resource problem creating '/tmp/orbit-svetlin'
aborting...

```

---

### Post by svetlin on 2007-03-09
I feel stupid :(
My disk was full. But I checked yesterday and it had 4GB free space...

---

### Post by tracyapotter on 2007-04-14
This happened to me today also.  I did not know what was happening until I found your post.

For those as new as me I will tell you what I did to get out of this jam.

When the login screen comes up, go to the Menu button and start in Console mode.
Log in with normal username and password.
Then at the prompt type: sudo apt-get autoclean

This will delete all the leftover files from the 8 or nine updates and upgrades I had done since the last time I cleaned up.  This only bought me a few megs but was enough to get past the required threshold (whatever that is) and then I could do a more proper cleanup.

Thanks again,

TA Potter

---

