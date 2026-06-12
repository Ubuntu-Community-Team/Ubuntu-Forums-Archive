---
title: "Tinkered with /etc/fstab, now wont boot"
date: 2005-06-24
forum: Desktop Environments
---

### Post by VenomousGecko on 2005-06-24
I was attempted to follow the ubuntu installation instructions for Beagle and one of the steps says to add user_xattr to the options in fstab.  However, after doing that on my root partion (whoops) I get an error that it is an unrecognized option and then the partion is mounted read only.  Now as you may have figured out, kinda hard to take that option out of fstab if it is on a read only partition and I cant save the changes. 

I have tried to boot into recovery mode and then type 

#mount -o remount,rw /dev/sda2 

but this does not work.  Any suggestions???

---

### Post by Dave_is_sexy on 2005-06-24
[clicky clicky](http://www.fs-driver.org/) 

That's a windows ext2/3 driver. it'll let you do whatever. I got it installed and no probs. Be sure to read the docs tho so you're aware of it's abilities n stuff.

---

### Post by VenomousGecko on 2005-06-24
EXCELLENT!

That worked like a charm.  I appreciate all of your help. I am typing this to you from Ubuntu.  Back in the saddle!

---

