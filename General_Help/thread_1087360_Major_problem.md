---
title: "Major problem"
date: 2009-03-04
forum: General Help
---

### Post by dougfresh on 2009-03-04
Ok guys, I'm back again.

My problem now is I get the black screen of death after loading up Ubuntu. What I have done since initial installation is:

Installed Wine and Wow - no problems
Tried and tried and tried again to install my ATI Radeon x1650 pro drivers - I think that succeeded.

I then installed the Catalyst Control Center program and that was smooth until I changed the desktop resolution from Clone Mode to Extended Desktop. It asked me to reboot, I rebooted and it gave me the black screen of death.

Help. These are the only 2 things I need installed after the initial Ubuntu installation. I have had nothing but trouble with them both... If I need to reformat I can and will, I still have the CD. If I need to re-do that, can someone post the guides for these 2 things? I have searched all over the internet trying to fix these problems which landed me where I am at now. I thought I had it figured out but obviously not...

Doug

---

### Post by banana jama on 2009-03-04
i don't know if this will help (im kind of a n00b) but i was once having the black screen of death and i poped out the battery while it happened and the problem was solved after that.

---

### Post by cariboo on 2009-03-04
If you have another computer, you can use remote desktop to correct your resolution.

Boot in recovery mode and drop to a root prompt at the menu, then at the prompt type:

```
vino-server &
```

This will start the remote desktop server, once bacj at the prompt type:

```
exit
```

and continue on to the black screen go to your other computer and try to log into the desktop.

Jim

---

### Post by dougfresh on 2009-03-04
Hey Jim,

Forgive my lack of linux knowledge, however my other computer is my Laptop which is currently running Windows XP. Can I still do that? I'm not sure the method to doing that.

Doug

---

### Post by dougfresh on 2009-03-05
bump

---

### Post by albandy on 2009-03-05
try pressing ctrl+alt+f2 to see if a text console appears.

---

### Post by dougfresh on 2009-03-05
No go.... I have the live disk if necessary... anyone?

---

