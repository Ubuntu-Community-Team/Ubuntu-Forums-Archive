---
title: "making the desktop kidproof."
date: 2009-08-05
forum: Desktop Environments
---

### Post by PsYcHoTiC_MaDmAn on 2009-08-05
is there anyway to remove all the menu options and so on from a screen so that its childproof.

basically, all I want on there for him (4years old) is firefox so I can shove the occasional video on etc, the few games I've got working on there (also side note, any idea how to get it to downgrade to 16bit colour, it objects as the PC is running at 32bits) and the power off button.

I wish to retain full userbility on other screens, but obviously just that one nothing else

(what prompted this was him having change the screen resolution from 1024x768 to something like 800by640 and I couldn't access the apply changes button to reset the screen (rebooting did the trick, but prefer to avoid it))

---

### Post by aysiu on 2009-08-05
How about installing and using *pessulus*?

---

### Post by karrank% on 2009-08-05
Would creating a new user with all the required settings work?

---

### Post by estebarb on 2009-08-06
I think that it is not exactly what you want, but, how about installing Sugar? It was done to be usefull and kidproof at the same time :p. More info here:

[http://wiki.laptop.org/go/Sugar_on_Ubuntu_Linux](http://wiki.laptop.org/go/Sugar_on_Ubuntu_Linux)

---

### Post by warp99 on 2009-08-06
I have three small children in the house and the easiest way was separate non-administrative accounts for each child. Once you do that you can customize the desktop to your hearts content removing anything and everything since the changes will only be made to his/her share. 

You can also set the video resolution different for each user if you want, but you need to be using one of the open source video drivers and not the proprietary ones. You can also restrict printers, inputs, drive access, peripherals, you name it and apply this only to the child's share.

---

### Post by PsYcHoTiC_MaDmAn on 2009-08-06
thanks, I'll look into those.

having looked at the edit menus I can see how many I can remove.(including the enrtire system menu) any whay of disabling edit menu after I've set it all so he cant access it accidently

video drivers, well apparantly I dont have any propriatary hardware on the machine... despite having to install ATI drivers in 8.10 for the radeon card, when I search hardware in 9.04 it says there isnt any... yet the display is running through the graphics card (otherwise a maximum resolution of 800x600)

---

### Post by warp99 on 2009-08-06
> **PsYcHoTiC_MaDmAn said:**
> thanks, I'll look into those.

having looked at the edit menus I can see how many I can remove.(including the enrtire system menu) any whay of disabling edit menu after I've set it all so he cant access it accidently

video drivers, well apparantly I dont have any propriatary hardware on the machine... despite having to install ATI drivers in 8.10 for the radeon card, when I search hardware in 9.04 it says there isnt any... yet the display is running through the graphics card (otherwise a maximum resolution of 800x600)

With his own share you can remove everything is you want and only his desktop will be affected, no one else. If you're worried about him messing it up just back up the following hidden directories:

~/.config
~/.gnome2
~/.gnome2_private

And restore them if needed. Honestly you shouldn't even worry about this problem since I'm never had to deal with it and I've got three kids. They've been on Ubuntu since they where 4-5 years old, now the oldest is 8. Even if he deletes a couple of icons it takes like 30 seconds to put them back with the menu editor. Believe me it's a non-issue.

Just give him some desktop wallpaper with his favorite cartoon character or something like Thomas the Tank Engine and/or some whimsical icons, lots to choose from in the repositories, and he'll be ticked pink. Best thing if he does mess something up beyond repair no problem, just delete his share and start again.

As for the video card there are some issue with ATI dropping support for some older cards forcing 9.04 users to the open source drivers, which may not have as good of support for things like Compiz on some cards. Check to see if you're affected:

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

If you have one of the older cards you can check the forums to see how to change the resolution and/or improve the performance. You can also check with the guides I have listed in my signature. I would try those first, then search the forums.

---

