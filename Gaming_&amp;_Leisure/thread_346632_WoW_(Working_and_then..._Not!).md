---
title: "WoW (Working and then... Not!)"
date: 2007-01-26
forum: Gaming &amp; Leisure
---

### Post by Poptart on 2007-01-26
Okay, so earlier today I managed to get WoW working with an ATI Radeon 9200 with Wine. The frame clipping was enough to make me go out and buy a GeForce 6200, which I promptly installed. I had some issues because Ubuntu was looking for the ATI card still, but I got it straightened out eventually with dpkg-configure xserver-xorg and then by following the Ubuntuguide.org's instructions for getting Nvidia stuff installed in Dapper.

Wow ran PERFECTLY for several hours. My machine ended up hanging (I'm still not sure why), and I had to reboot. Since the reboot my OpenGL hasn't been working, and I'm getting 3D acceleration errors. I know it's my OpenGL because Cedega's little test thing says that that, specifically, isn't working - the 3D acceleration appears to be peachy keen.

What the heck do I need to do to fix this, because I am totally thrown. If I absolutely have to reinstall I will, but I'd like to keep the status quo as long as possible.

Thanks!

:)

---

### Post by Ferrat on 2007-01-26
Have you tried reinstalling the driver and checking that Ubuntu isn't running the right driver/xorg-conf ect? 

The crash could have cost you some settings that didn't save for ex.

---

### Post by Poptart on 2007-01-26
I have tried reinstalling everything, I even tried doing the legacy drivers over the regular drivers (which is what were working before). I've played with the xorg.conf file a few times to make sure it's pointing to the correct set of drivers, or even the "wrong" set just to see if that works.

My desktop displays the 3D accelerated effects of the compiz/xgl stuff, but when I try to boot WoW up it says it can't start 3D accleration. :/

What I would like to do is completely remove any and all files on my computer related to my video card (or previous video card), reinstall and see if that effects anything. But I don't know what the names are for all the files I'd need to ditch.

I'm slowly reaching the conclusion that a reinstall would be best.

Or, do you think upgrading to Edgy and starting over again with that would do the trick?

---

### Post by Ferrat on 2007-01-26
If your reinstalling I would go with edgy but don't upgrade, reinstall with Edgy CD if possible. 

You don't have Compiz/xgl stuff running that prevents the 3D acc. ?

Tried reinstalling wine might help aswell if you haven't tried that, but it''s a weirdo problem, prolly some setting ect. that didn't save due to crash, question is what >_<

---

### Post by jaytek13 on 2007-01-26
Oddly enough, I am also experiencing a very severe degradation in my performance with WoW. I just installed and got it working 2 days ago, and then it was working fine in all areas after the recommended tweaks (20-30fps outside and near 60 indoors). Now today, my performance had diminished to an unplayable 10-15 fps outdoors.

So, I tried disabling shaders, lowering my resolution, turning off my sound... Virtually no changes in doing any of these things.

I didn't experience any odd crashes, though. I have absolutely no indication of what has caused the degradation.

---

### Post by Poptart on 2007-01-26
Okay, I uninstalled everything I possibly could and then reinstalled everything and now it works just fine.

Only problem is I have no idea what was wrong!

---

### Post by Ferrat on 2007-01-27
> **jaytek13 said:**
> Oddly enough, I am also experiencing a very severe degradation in my performance with WoW. I just installed and got it working 2 days ago, and then it was working fine in all areas after the recommended tweaks (20-30fps outside and near 60 indoors). Now today, my performance had diminished to an unplayable 10-15 fps outdoors.

So, I tried disabling shaders, lowering my resolution, turning off my sound... Virtually no changes in doing any of these things.

I didn't experience any odd crashes, though. I have absolutely no indication of what has caused the degradation.

And you haven't installed anything during this time? 
could be another program taking power

---

### Post by Poptart on 2007-01-27
Okay, same problem again. This time, the computer didn't crash, I shut it down properly. Something isn't saving somewhere. :/

I'm going to do a clean install of Edgy.

---

### Post by Ferrat on 2007-01-27
> **Poptart said:**
> Okay, same problem again. This time, the computer didn't crash, I shut it down properly. Something isn't saving somewhere. :/

I'm going to do a clean install of Edgy.

That's very weird, but yeah a clean Edgy install sounds best

---

### Post by Poptart on 2007-01-28
Whatever the problem was, a clean install fixed it good. I think maybe the compiz/xgl thing interfered. I won't try that again.

Thanks for the quick responses, even though my problem was just lame. :D

---

