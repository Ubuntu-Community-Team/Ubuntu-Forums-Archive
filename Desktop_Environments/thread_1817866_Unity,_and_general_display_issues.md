---
title: "Unity, and general display issues"
date: 2011-08-03
forum: Desktop Environments
---

### Post by tibmag2120 on 2011-08-03
Hi, first post here
 
I recently installed ubuntu 11.04 on my laptop,
my laptop is a HP touchsmart Tm2 with the intel i3 chipset
and intel integrated HD graphics.
 
the first install I broke playing with various settings, just to see
what would and wouldn't work, I had to boot with "nomodeset" 
the entire time (before I broke it).
 
I formatted and reinstalled, had to boot with "nomodeset" again
the first and only thing I did was install all updates, I had walked 
away from the install and I had not edited GRUB yet and was 
surprised when I came back to find not only did the laptop reboot
successfully (without 'nomodeset'), but also the unity desktop was running.
 
Now to the issue, I also broke the second install, and here I am
on the third install, and I am back to having to use "nomodeset" or
I boot into a black screen, and no unity desktop.
 
I cannot figure out what driver or update somehow got installed on the second install
that seemingly made everything work
 
-Thanks

---

### Post by tibmag2120 on 2011-08-11
Ok, so a few days after this post, the third install randomly started loading again, with no problems, no need for "nomodeset" and unity and compiz ran great, now yesterday it is back to booting into a black screen, unless you add "nomodeset" to grub, along with that unity and compiz no longer function (which is to be expected under the "nomodeset" startup)
 
has anyone experianced this at all, or have any advice on how to stablize this install.
 
thanks in advance

---

### Post by GnomeMax on 2011-08-11
I ran into something similar a while back when I was fixing a desktop PC for someone.  Installed Ubuntu (they lost their Windows license with the hard drive) - a few distros back - and got much the same response as you have.  Mine turned out to be the onboard video.  Tried it with a cheap nVidia card and it ran just fine.

Not much help for the laptop since you can't change the chip...  But, if you can get it to install again (and run), see what happens when you turn off all the eye candy stuff and drop the resolution.

---

### Post by tibmag2120 on 2011-08-11
Finally figured it out, not sure if this is a solution that others would be interested in, again the laptop is an HP Touchsmart tm2, with the i3 chipset and integrated intel hd graphics.  If you install 11.04 and all updates and boot up WITHOUT the AC adaptor plugged in, the machine will boot fine, with no graphics issues, full unity support and compiz with all the bells and whistles.  If the AC adaptor is plugged into the laptop, Ubuntu will boot to a black screen unless "nomodeset" is used.  After bootup, the machine accepts the AC adaptor just fine and doesn't drop off or anything.

I know its wierd, doesn't make sense to me either, not sure if this is something dev's would be interested in, but there it is

---

