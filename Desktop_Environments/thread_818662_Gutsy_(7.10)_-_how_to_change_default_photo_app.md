---
title: "Gutsy (7.10) - how to change default photo app?"
date: 2008-06-04
forum: Desktop Environments
---

### Post by timcredible on 2008-06-04
I'm still running gutsy on one machine and want digikam to come up when the system sees a camera or a photo card.  I changed the System->Preferences->Camera tab to 'digikam --detect-camera', but f-spot still pops up when I put a photo card in the PC.  I see that in hardy you can change this in nautilus, but that option doesn't appear to be there in gutsy.  Anyone know how I can do this?  Thanks.

---

### Post by unutbu on 2008-06-04
Click System>Preferences>Removable Drives and Media.
Go to the Camera tab.
You can either change the command to
```
digikam --detect-camera
``` or, if you want to use gthumb to download the pictures, but want digikam to pop up afterward, you can write a simple script with both commands in it.

---

### Post by timcredible on 2008-06-04
thanks for the reply, but that only changes what happens when it sees a camera, it doesn't change what happens when i put in a photo card - f-spot still pops up.

---

### Post by unutbu on 2008-06-04
I think you can do it with udev rules.
See [http://ubuntuforums.org/showpost.php?p=1574752&postcount=16](http://ubuntuforums.org/showpost.php?p=1574752&postcount=16) for an example. I have never done this so you may want to post another thread with "udev" in the title to attract the attention of those who might be able to help you.

Edit: You might also want to read /usr/share/doc/udev/writing_udev_rules/index.html. Our machines come with documentation! Who wudda thunk it?

---

### Post by timcredible on 2008-06-04
thanks for the reply.  i was hoping for an easier way to do it, but if this is the only way, i think i'll upgrade to 8.04 and then go through the less (but not much less) painful method of changing this in 8.04.  makes me think about giving up on gnome and going back to kde.

---

