---
title: "Dell D600 run-away vertical scrolling"
date: 2010-09-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fmouse on 2010-09-15
I have a Dell D600 laptop on which I recently upgraded Ubuntu Linux to 10.04.1 LTS from 8.x.  Prior to the upgrade, the touchpad mouse and mouse buttons had no problems, but after the upgrade, about every 4 to 8 times I click an arrow button on a vertical scrollbar, the window acts as if the button-up event wasn't sent and the window scrolls continuously.  I can sometimes stop the run-away scrolling by clicking again on the arrow button, and sometimes by moving the mouse pointer off of the scroll bar.  Sometimes nothing helps, and the window scrolls until it reaches its scroll limit.  If this happens, it takes some time, and a number of mouse-clicks to get the left mouse button working again.

The mouse is identified as an "AlpsPS/2 ALPS DualPoint TouchPad" by the kernel.  It's supported by the psmouse kernel module.

If I plug in a USB mouse and use it instead of the touchpad mouse, there is no problem.

---

### Post by mörgæs on 2010-09-15
How does the machine work, if you boot a live CD?

---

### Post by fmouse on 2010-09-15
> **mörgæs said:**
> How does the machine work, if you boot a live CD?

Good question.  I'll give it a try, and also put the Windows hard drive in it again and make sure the hardware is working properly.

---

### Post by rwillia328 on 2010-09-16
I am having the same issues with my Dell D600.  I originally upgraded from 8.10LTS to 10.04LTS and experienced the issue.  I then did a clean install and still experience the same issues with the mouse.  I did try the live CD The same issue exists with the Live CD.  I've been dealing with it for about 3 months since the upgrade.  I've been monitoring the forums looking for an answer without any luck.

Any help would be appreciated!

---

### Post by fmouse on 2010-09-16
> **rwillia328 said:**
> I am having the same issues with my Dell D600.  I originally upgraded from 8.10LTS to 10.04LTS and experienced the issue.  I then did a clean install and still experience the same issues with the mouse.  I did try the live CD The same issue exists with the Live CD.  I've been dealing with it for about 3 months since the upgrade.  I've been monitoring the forums looking for an answer without any luck.

rwillia328, my guess is that it's a kernel module issue, and that the ABI for the the Alps hardware may be proprietary, which always makes this kind of thing difficult for F/OSS developers.  I had this problem occasionally under my previous Ubuntu installation on the box, but not enough to complain about.  Now it's much more frequent.  I've been tinkering under the hood with Linux for like 10 years, and at this point I really don't want, or really have time to tinker anymore, I just want things to work so I can do higher level things.

Here's a thought.  You might want to contact the developers directly (modinfo psmouse and kernel source for alps.c) and ask where they think the problem may lie.  It's entirely possible that the problem is at a higher level, such as the X layer, or HAL.  The end result is that the mouse-up event isn't making it to the event-processing engine.  You can see this in other contexts, too, but it's most noticeable and most annoying on the scroll arrow buttons.  The quick-n-dirty fix, of course, is to carry a small optical USB mouse and use that - inconvenient, but functional and less annoying.

---

### Post by mörgæs on 2010-09-16
Maybe try 10.10? 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is still in beta, but if you guys don't mind experimenting it might be worth the while.

---

### Post by fmouse on 2010-09-16
> **mörgæs said:**
> Maybe try 10.10? 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is still in beta, but if you guys don't mind experimenting it might be worth the while.

Well .....   Maybe later.  I just don't have the time to mess with it unless I know that someone who is aware of the problem has explicitly done some development work to address it.

Thanks anyway, though.

---

### Post by rwillia328 on 2010-09-18
> **fmouse said:**
> rwillia328, my guess is that it's a kernel module issue, and that the ABI for the the Alps hardware may be proprietary, which always makes this kind of thing difficult for F/OSS developers.  I had this problem occasionally under my previous Ubuntu installation on the box, but not enough to complain about.  Now it's much more frequent.  I've been tinkering under the hood with Linux for like 10 years, and at this point I really don't want, or really have time to tinker anymore, I just want things to work so I can do higher level things.

Here's a thought.  You might want to contact the developers directly (modinfo psmouse and kernel source for alps.c) and ask where they think the problem may lie.  It's entirely possible that the problem is at a higher level, such as the X layer, or HAL.  The end result is that the mouse-up event isn't making it to the event-processing engine.  You can see this in other contexts, too, but it's most noticeable and most annoying on the scroll arrow buttons.  The quick-n-dirty fix, of course, is to carry a small optical USB mouse and use that - inconvenient, but functional and less annoying.

Thanks for the reply fmouse  I'm somewhat in the same situation you are.  I've been tinkering with linux for about 7 years and looking to go onto higher level stuff.  I think this is enough of an issue for me that I'll delve into a bit further and see if I can figure it out.  I agree that it's quite possible that the issue lies at a higher level given the changes to the X architecture from 8x to 9x.  My thought is to get the Dell ISO of 9.04 and see if I can figure out what they did.  I have tried 9.x on this box with the same result as 10.04.

---

### Post by mörgæs on 2010-09-18
Great. If you guys happen to find a solution, please post here.

---

### Post by sethtriggs on 2011-01-24
I'm having the exact same problem with my custom-built workstation. I was spurred to upgrade from 9.10 to 10.04 due to needing to beta-test a program (it needed a newer version of qt than 9.10 supported.

That was a big mistake. Not only did the ATI card crap itself, but I now have this same confounding mouse problem. It makes it all but impossible to select anything, and clicking and dragging does not work at all.

Is this a kernel issue? Testing all my mice on different computers and systems shows they work (including Windows 7), so I am at a loss. All the equipment was working before I went to 10.04.

-Seth

---

### Post by mörgæs on 2011-01-25
You are not talking of 10.10, have you tried a live boot with this one? 

Some people report that updating the BIOS might help in these cases. I can not guarantee that it works, but it could be worth a shot.

---

### Post by fmouse on 2011-01-25
> **sethtriggs said:**
> I'm having the exact same problem with my custom-built workstation. I was spurred to upgrade from 9.10 to 10.04 due to needing to beta-test a program (it needed a newer version of qt than 9.10 supported.
I found that I got *much* better results in general by doing a clean install of 10.04 rather than trying to upgrade onto a previous version.  This didn't affect the mouse problem, but other parts of the installation were much cleaner and more integrated than was the case when I tried to do an upgrade over an existing Ubuntu installation.
> **sethtriggs said:**
> That was a big mistake. Not only did the ATI card crap itself, but I now have this same confounding mouse problem. It makes it all but impossible to select anything, and clicking and dragging does not work at all.
The problem only seems to affect my touchpad mouse.  I bought a Logitech bluetooth mouse and an IOgear bluetooth adapter and they work just fine.
> **sethtriggs said:**
> Is this a kernel issue? Testing all my mice on different computers and systems shows they work (including Windows 7), so I am at a loss. All the equipment was working before I went to 10.04.I suspect that this is a kernel issue.  The Alps hardware behind the touchpad mouse may have a proprietary ABI, which causes problems for Linux kernel developers, although earlier versions of the kernel didn't have this problem.  The mouse is a Logitech V470 Bluetooth Cordless Laser Mouse for Notebooks, and I love it.

---

### Post by sethtriggs on 2011-01-26
> **fmouse said:**
> I found that I got *much* better results in general by doing a clean install of 10.04 rather than trying to upgrade onto a previous version.  This didn't affect the mouse problem, but other parts of the installation were much cleaner and more integrated than was the case when I tried to do an upgrade over an existing Ubuntu installation.

The problem only seems to affect my touchpad mouse.  I bought a Logitech bluetooth mouse and an IOgear bluetooth adapter and they work just fine.
I suspect that this is a kernel issue.  The Alps hardware behind the touchpad mouse may have a proprietary ABI, which causes problems for Linux kernel developers, although earlier versions of the kernel didn't have this problem.  The mouse is a Logitech V470 Bluetooth Cordless Laser Mouse for Notebooks, and I love it.

Thanks fmouse. I did get the mouse to work by accident once and I can't remember what setting I made (so I've done another thread to iron it out). I'm almost able to get this working, if I could just lick this mouse problem.

Booting into different kernels didn't seem to help me at all as the system wouldn't boot. By chance, if you have an earlier Ubuntu disk, does your mouse work there on LiveCD? I can't test this out on my machine since the optical drive is broken (in a perfect storm of crap!)

-Seth

---

