---
title: "ATI Radeon x300 dual-head probs with 11.04"
date: 2011-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gbrowne on 2011-04-19
My Dell Inspiron 9300 worked pretty much faultlessly with 10.04, but stopped resuming from hibernate at 10.10.  Rather than chase this, I decided to await the release of Natty.

Running the Beta 2 release of 11.04 from CD, I find that it has problems with my ATI Mobility Radeon X300 graphics card (M22) doing dual-head.  In 'monitor preferences', I unticked 'same image in all monitors' and it correctly identified my external Samsung monitor.  However, when I stacked the ext monitor above the laptop panel and clicked 'apply' the external screen seemed to display correctly, but the laptop screen background was covered with random-seeming columns of coloured patterns.  I then noticed that if I moved any window on either screen it left behind a trail of window edges, likewise when the tabs on the lhs of the screen moved in an out they did the same.  While moving anything the background flashes different colours.

I chose to return to the previous config and after some flashing of both screens the windowing system (Compiz ??) crashed leaving only the background wallpaper image.  After a few moments the screens returned to the previous state with same image on both.

Would be happy to perform any tests if it would help resolve the issue ready for the release next week.  Dual-head worked brilliantly with this exact same hardware in 10.04.

Cheers,
GB.

---

### Post by gbrowne on 2011-05-12
Further to this, I have now upgraded to 11.04 and have discovered that if you set both displays to 1280x1024, the problem goes away completely.  Is this just a configuration issue rather than a bug ?

Any ideas where I might look please - I would really like to solve this problem ?

GB.

---

### Post by Ryborg on 2011-05-23
I'm having the same problem with a FireGL 3100 dual head setup.  I have 2 monitors with differing resolutions.  When I untick mirror, I get the exact same problem when monitors are configured at different resolutions.

---

### Post by nickymlg on 2011-07-21
I had the same issue but in my desktop, hp sr1297. I workarounded it, changing to classic login and forgetting about unity launcher. I now got two monitors and my desktop extended not duplicated.

---

### Post by gbrowne on 2011-07-22
As this is highly reproducible, presumably this should be reported as a bug to be hopefully fixed in the next release ?

G.

---

