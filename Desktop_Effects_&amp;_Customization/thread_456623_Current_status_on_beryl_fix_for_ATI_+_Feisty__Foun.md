---
title: "Current status on beryl fix for ATI + Feisty???  Found out more but still not there"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by djrobthaman on 2007-05-27
Hi everyone.

So, I'm a bit more informed but really I'm only in the same place I was when I started trying to get beryl working.  So here's a list of things I know now:

1.  Still haven't been able to get beryl working with Feisty (using ATI Radeon X1300)

2.  The reason it won't work is because the latest release doesn't contain the beryl-xgl package

3.  Some people have been able to fix this by downgrading to an older version of beryl, where beryl-xgl is included.  This has not been able to work for me.

4.  Other people have been able to do even better and downgrade beryl, copy beryl-xgl, re-upgrade to the latest beryl and move the copied file to where it should be.  This hasn't worked for me either.

5.  With the latest version of beryl installed, nothing happens when I choose beryl as the windows manager.  Again, this is because beryl-xgl is not present.

6.  If I downgrade or add beryl-xgl to the upgraded beryl, choosing beryl as the window manager results in the white cube

7.  I can use the non beryl-xgl'd most recent version of beryl if I use the LD=preload.... fix, but this usually dosn't work for more than 10-15 minutes before I have to kill the process and run it again.  Even then certain things don't work 100%, like thumbnail previews.

I found a bug report on launchpad where someone claims that beryl-xgl was taken out because of some linkage issues with mesa or something.  Don't quote me on that one.

So, I think something probably changed in feisty (compared to edgy) so that the beryl-xgl causes that WSOD (or at least for people with something close to my specs... I can't believe I'm the only one that can't get any fixes to work).


So, after that long list my question is... has anyone found a replacement for the beryl-xgl file?  Has some gracious, benevolent coder written a file we can put in place of beryl-xgl that at least kinda fixes beryl for us ATI users?  Or has anyone come up with a better fix than the ones above (ld preload, downgrade, or add beryl-xgl to the current 0.2.1 install)

If anyone has any clues, knows where to look, or can point me in the right direction it would be greatly appreciated.

Thanks in advance,
Douglas

---

### Post by djrobthaman on 2007-05-27
PS  I've seen more than a few references on the net to beryl 0.3.0.  Does this actually exist?  It's not in any repos I have.

---

### Post by samegate on 2007-05-27
Hi djrobthaman,
I am as raw a noob as there is to linux;but after a lot of effort I have beryl running very well on an x1650xt. As you mentioned, I have downgraded to ver 2.0 and used the install guide on ubuntuguide.org Maybe this will help if you have not tried that guide. cheers

---

### Post by djrobthaman on 2007-05-27
Thanks samegate.  I already tried this guide though :(.  

Also, I guess I should have said I'm using a 64 bit version of Ubuntu.  

This is really upsetting though, because I had beryl working fantastically under Edgy.  I wish this were so with Feisty.

---

### Post by djrobthaman on 2007-05-28
Just a quick bump up.  Does anyone know of a not so buggy solution to beryl's missing beryl-xgl problem for us ATI users?

---

