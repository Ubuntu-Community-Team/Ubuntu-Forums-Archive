---
title: "No Window Borders"
date: 2009-09-20
forum: Desktop Environments
---

### Post by vi1985 on 2009-09-20
Hi, 

I am wondering how to restore the borders on all my windows (the resizeable border, with max-min-close buttons). They have disappeared some time ago after a massive update (updated to either 8.x or 9.04, with many additional updates that were recommended/required by ubuntu).

Currently, I have a gnome ubuntu 9.04, and am using an ATI driver. I can provide more info about my system if you ask for it.

Thank you very much for your time! Fixing this would make my life much easier.

Vic.

---

### Post by majiciannz on 2009-09-20
> **vi1985 said:**
> Hi, 

I am wondering how to restore the borders on all my windows (the resizeable border, with max-min-close buttons). They have disappeared some time ago after a massive update (updated to either 8.x or 9.04, with many additional updates that were recommended/required by ubuntu).

Currently, I have a gnome ubuntu 9.04, and am using an ATI driver. I can provide more info about my system if you ask for it.

Thank you very much for your time! Fixing this would make my life much easier.

Vic.
Not really sure what you mean.....

However if you right click your desktop and select "Change desktop background"
Open "Themes" tab...you can select the effects and window boarders etc. that you want.

Hope this helps

---

### Post by vi1985 on 2009-09-20
Thanks majiciannz, but when I switch themes, everything changes as it should, except the window borders remain absent. By that I mean they aren't there at all; the bar at the top of a window that states the name of the window, lets you resize it, minimize-maximize and colse it, is not there. All I see is a rectangle with the contents of the window.

Vic.

---

### Post by majiciannz on 2009-09-21
Hi Vic,

Sorry but I'm unable to duplicate the fault so unable to advise how to fix it.

I'll keep working on it and if I come up with the answer I'll post on this thread.

Hopefully someone else will know.

Good luck

---

### Post by oboedad55 on 2009-09-21
> **vi1985 said:**
> Thanks majiciannz, but when I switch themes, everything changes as it should, except the window borders remain absent. By that I mean they aren't there at all; the bar at the top of a window that states the name of the window, lets you resize it, minimize-maximize and colse it, is not there. All I see is a rectangle with the contents of the window.

Vic.

Are you using compiz? If so, install fusion-icon and emerald window manager. I had this problem with 8.04 and the fusion-icon did the trick. You'll see easily what it does.

---

### Post by vi1985 on 2009-09-21
> **oboedad55 said:**
> Are you using compiz? If so, install fusion-icon and emerald window manager. I had this problem with 8.04 and the fusion-icon did the trick. You'll see easily what it does.

Thank you so much! This solved it.

Vic.

---

### Post by oboedad55 on 2009-09-21
> **vi1985 said:**
> Thank you so much! This solved it.

Vic.

I'm glad it worked, happy to be of service. Now you've got something to pass along as you cruise these forums.

---

### Post by vi1985 on 2009-09-21
> **oboedad55 said:**
> I'm glad it worked, happy to be of service. Now you've got something to pass along as you cruise these forums.

I'll try. Thanks again.

---

### Post by Mike_tn on 2010-11-02
> **oboedad55 said:**
> Are you using compiz? If so, install fusion-icon and emerald window manager. I had this problem with 8.04 and the fusion-icon did the trick. You'll see easily what it does.
I could buy you a big mac and fries. thanks

---

### Post by Sonsum on 2010-11-24
> **oboedad55 said:**
> Are you using compiz? If so, install fusion-icon and emerald window manager. I had this problem with 8.04 and the fusion-icon did the trick. You'll see easily what it does.

A combination of this and the command ```
metacity --replace
``` solved this for me. Thanks!

---

### Post by oboedad55 on 2010-11-24
Glad it worked. So you're running metacity instead of compiz. You won't get all the swell visual effects but not everyone cares about that. If you want to switch alt-F2 and do, compiz --replace

---

