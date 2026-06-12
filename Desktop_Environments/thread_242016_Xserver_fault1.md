---
title: "Xserver fault1"
date: 2006-08-23
forum: Desktop Environments
---

### Post by Michiba on 2006-08-23
Hi all,

I have a small problem, I started up Ubuntu tonight (Australia) and I get the following ominous message

Failed to start Xserver (your graphical interfae)It is likley it is not set up correctly. Would you like to view the X server output to diagnose the problem.
  Yes  No

I hit enter with the "yes" highlight" and I get a bunch of stuff about Ubuntu being free and no warrenty etc. and then finally this.

-bash: no job control in this shell.

Ok, can I fix this or do I need to reinstall I have my home folder on a hdb1, so I can format hda no problem. If I can salvage the current installation it would save me tweaking all the bits and pieces the way I like them. 

All replies appreciated.

Michiba

---

### Post by Scythe!? on 2006-08-23
There was a dodgy update yesterday morning. I did the following and it worked.
```
sudo apt-get update
```

```
sudo apt-get install xserver-xorg-core
```

It should say it needs upgrading eg-
1 Upgraded,0 not installed, 0 removed...blah blah...

Then press Y or what ever it is to upgrade it then
```
sudo reboot
```

---

### Post by Michiba on 2006-08-23
Thanks for that. Tried it and failed. 

If anything else comes to mind please post it.

Thanks
Michiba

---

