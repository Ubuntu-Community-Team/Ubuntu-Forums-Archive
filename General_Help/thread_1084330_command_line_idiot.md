---
title: "command line idiot"
date: 2009-03-01
forum: General Help
---

### Post by skedds on 2009-03-01
I was using ubuntu HH, and typed sudo rm -r on an important folder. I thought it did something else... but now my folder is permanently deleted. 

Is there any possible way to get my files back? These are very important to me. I dunno if this makes it better or worse, but It's on a VMWare image, not an actual hard drive.

If there's anything you can do, I would be very thankful.

---

### Post by punx45 on 2009-03-01
sorry to say, but rm is permanent.   since it was a VM image, if you have a snapshot, you should be able to revert to it.

helpful hint for later on, make an alias of rm so that it asks before deleting.

alias rm='rm -i'
 
add that to .bash_aliases in your home directory.

---

### Post by skedds on 2009-03-01
> **punx45 said:**
> sorry to say, but rm is permanent.   since it was a VM image, if you have a snapshot, you should be able to revert to it.

helpful hint for later on, make an alias of rm so that it asks before deleting.

alias rm='rm -i'
 
add that to .bash_aliases in your home directory.
guh, ya I had wished I had a snapshot.

The only reason I did it because I didn't know what it was gonna do. I hopefully wont do it again.


But isn't there some kind of recover tool like ones for windows?

---

### Post by mdgrech on 2009-03-01
You just did the windows equvelent of deleting a file, then emptying out your recycle bin, then deleting all your snapshots.

Unless someone knows something I don't I dont think you can get it back...what was it exactly anyhow

---

### Post by skedds on 2009-03-01
> **mdgrech said:**
> You just did the windows equvelent of deleting a file, then emptying out your recycle bin, then deleting all your snapshots.

Unless someone knows something I don't I dont think you can get it back...what was it exactly anyhow

'bout 4 days worth of php code I programmed :(

---

### Post by JECHO on 2009-03-01
> **skedds said:**
> 'bout 4 days worth of php code I programmed :(

ouch.

---

### Post by Old *ix Geek on 2009-03-02
> **skedds said:**
> The only reason I did it because I didn't know what it was gonna do. I hopefully wont do it again.When in doubt, **man** is your friend.  Had you checked what you were about to do by typing:
```
man rm
```
you would've saved yourself a LOT of grief!

---

### Post by mulligan.can on 2009-03-02
You can have a shot at using testdisk/photorec but i dont like your chances.

---

