---
title: "Gnome/Unity Freezes on 11.10"
date: 2011-12-31
forum: Desktop Environments
---

### Post by egoblin on 2011-12-31
So I upgraded to 11.10 from 11.04.
When I log into my account using unity or gnome classic, my computer becomes very slow (slow drag of windows etc) and eventually it freezes (within a few minutes).
By freezes, I mean that I can still move my mouse pointer around and see the caps lock light come on for the Keyboard. But I can't click on anything and I can't Crtl-Alt-Delete or anything of the sort. Unable to click or do anything, I eventually have to hard reset my desktop to get out of the situation.
I am however able to use OpenBox or KDE without problems.

I saw some posts saying there may be problems with upgrading from 11.04 to 11.10. So I booted using a 11.10 liveCD and since it boots you directly into unity, I face the exact same issue! 

Any help would be appreciated else I'll have to go back to 11.04 :(.

---

### Post by BC59 on 2011-12-31
If you are ready to format again your computer, then give a try to the kernel 3.2 which is still on RC status (unstable). Just to give a try before going back to 11.04.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/)

---

### Post by egoblin on 2011-12-31
Went thru the steps here:
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

And it fixed it (I think). No more hangs. I think it might have been the nvidia driver (esp since mine is an old card and I was using nvidia-current)

---

