---
title: "very strange problem on boot"
date: 2009-01-10
forum: General Help
---

### Post by mckinnley on 2009-01-10
i have vista installed on my computer and i wanted to dual boot with kubuntu, so i did all the partitioning crap and got it all to work, but when i upgraded to version 8.10 all i would get is this white screen. so i reinstalled it. and that didn't work, then i reinstalled it again. then i tried installing it inside windows, then i tried reinstalling it again on my hard drive. the last time worked finally, no white screen. however, now when it loads i don't get any gui, none.
i tried startx and i tried installing the gui from the command line but it just keeps telling me that no screens were found, which doesn't really make any sense because i wouldn't be looking at it if there were no screen.
another strange thing is that when i start up i have kubuntu listed twice, and the recovery mode listed twice. if i choose to load kubuntu it tells me that it can't boot from that partition and gives me an error code. then i try to load vista and it tells me that it's an incorrect executable. so i found out that if i want to use my computer, i have to put the kubuntu live disc into the slot, load it up, and then from the menu tell it to boot from first hard disc. this pulls up the same menu from before except that this time it will actually boot it up.
another weird thing is that when i go into vista it will then give me another menu saying "vista, kubuntu, kubuntu" as if kubuntu were installed in vista still, but it isn't, it lists it twice when it shouldn't be listing it at all because i uninstalled it.

this whole thing does seem to be a very strange issue

---

### Post by domoso on 2009-01-10
I just recently install 8.10 myself. Had weird issues as well but, was able to fix them. No screens, when I've run into it, is usually a mis-configured xorg.conf. However, it appears 8.10 is handling the xorg.conf differently as the typical settings found from older versions <=8.06 are not in xorg.conf. So, I don't know what to tell you but, I'd start with figuring our where 8.10 is configuring X for things like screen resolution and video drivers.

---

