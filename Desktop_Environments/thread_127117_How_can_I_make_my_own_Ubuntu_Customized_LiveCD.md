---
title: "How can I make my own Ubuntu Customized LiveCD?"
date: 2006-02-08
forum: Desktop Environments
---

### Post by derrick1985 on 2006-02-08
Hey Everyone,

I was wondering if anybody could point me in the direction of a howto for making your own Live CD of Ubuntu Linux? I basically just want to remove some programs and add my own to the list. Can I do this, and what would i need?

Thanks

---

### Post by taurus on 2006-02-08
You may want to check out Linux From Scratch if you want to roll out your own distro...

---

### Post by derrick1985 on 2006-02-08
What if I just want to remaster the live cd? isn't there a way to do that?

---

### Post by kg6gfq on 2006-07-22
I'm following the [LiveCD Customization guide]("https://help.ubuntu.com/community/LiveCDCustomization/6%2e10") on the wiki right now and it seems to be working so far.  You might give it a try if you haven't already found a way.  

Make sure you check the comments at the bottom, such things as updating /etc/resolv.conf (I copied the one from my own /etc into the chroot /etc) are crucial to installing software.  I think that it may be best, however, to remove that particular change before building the CD.  I'm not sure how the system would handle it, so...

Good luck with your customization!

---

