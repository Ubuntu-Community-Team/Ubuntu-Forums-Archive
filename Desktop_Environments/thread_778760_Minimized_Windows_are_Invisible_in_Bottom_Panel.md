---
title: "Minimized Windows are Invisible in Bottom Panel"
date: 2008-05-02
forum: Desktop Environments
---

### Post by eeefresh on 2008-05-02
I have a weird issue with the bottom panel that I can't seem to fix.  It all started when I enabled some Advanced Desktop Settings in Compiz, but the problem persists even when I turn off the advanced settings.

Normally you would have icons in your bottom panel for your different desktops, minimized windows and your "show desktop" button.  However, every time I reboot, the bottom panel basically loses all those icons.  If I minimize a window, it doesn't show up in the panel at all...but if I click on where the minimized window *should* be, it opens again...so its there, I just can't see it.  Same thing with my workspaces icons and my show desktop icon...all invisible in the panel, but work when I click on them.

When I go into panel settings I can change it to "solid color," and that works...until I reboot.  Then its gone again.  If I go in again and change it "use theme setting", it works....until I reboot.  Basically I have to alternate between the two every time I reboot in order to see the icons on my bottom panel.

Any ideas?

---

### Post by kaunofrantas on 2008-05-06
same problem here. i do not use compiz, but when i minimize applications they can't be seen on bottom panel. it happened today - didn't have this problem before. can't see even when the panel color is changed to solid.

can anybody help?

oops: fixed by reloading - don't know what happened

---

### Post by cyrusrayne on 2008-05-06
This certainly does seem bizarre.  What distro are you folks using and have you logged a bug report on Launchpad yet?

---

### Post by kaunofrantas on 2008-05-06
crap - it doesn't work again - when you minimize it is basically gone - i use ubuntu 8.04

---

### Post by cyrusrayne on 2008-05-06
In that case, I'd say file a report on launchpad.net and see what they recommend as I haven't encountered the error myself yet.  Will keep looking.

---

### Post by kaunofrantas on 2008-05-06
ok, by searching forums i found this answer:

> **mrmiserable said:**
> right click panel---- /add to panel/windows list



it worked for me - i was getting worried

---

### Post by eeefresh on 2008-05-10
I am using 8.04 as well, and adding window list to panel worked!

---

### Post by maninsitu on 2008-11-12
Yes, I had the same problem and this fixed it. So simple how did I turn it off in the first place? :lolflag:

---

### Post by Mitch72 on 2008-11-12
Compiz must interfere with it I guess... maybe it's the gtk theme?

---

### Post by hwttdz on 2009-03-20
So this appears to sometimes be caused by not having the window list added to the panel.   

Sometimes it's caused by having an invisible window list.  As I have just had this happen to me.  I was able to minimize and maximize windows by clicking on the panel (I just couldn't choose which ones I minimized or maximized because I couldn't see them).  Did a bug get opened for this behavior, is there a known fix or cause?

---

