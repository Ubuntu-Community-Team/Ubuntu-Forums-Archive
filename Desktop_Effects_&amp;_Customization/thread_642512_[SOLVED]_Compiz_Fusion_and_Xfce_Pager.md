---
title: "[SOLVED] Compiz Fusion and Xfce Pager"
date: 2007-12-16
forum: Desktop Effects &amp; Customization
---

### Post by cardinals_fan on 2007-12-16
I like using Xfce and Compiz Fusion together.  Recently, I decided to use the Xfce Pager plugin (for the panel) rather than the Expo plugin in Compiz.  Whenever I change desktops with the pager, the applications on the original desktop disappear.  They reappear if I go back to the original desktop.  When I leave a desktop, the open windows show the close animation (but don't actually close).  I'm having trouble describing it, so I've attached some annotated screenshots.

Any thoughts on which Compiz setting is causing trouble?

---

### Post by john.nicholls on 2007-12-17
I've had the problem of the applications on the original workspace disappearing, but I can't remember what the solution was, but I think it was in the Xfce settings. Make sure that in Desktop preferences allow Xfce is ticked, and that Workspaces is set to four.

---

### Post by cardinals_fan on 2007-12-18
Thanks for the reply.  Where do I check "allow xfce"?

---

### Post by john.nicholls on 2007-12-18
Xfce Settings Manager | Desktop Preferences | Allow Xfce to manage the desktop

You might also check the following settings in  Compiz General Settings | Desktop Size:
Horizontal virtual size: 4
Vertical virtual size: 1
No of desktops: 1

---

### Post by cardinals_fan on 2007-12-19
That is all correct.  I've read that Compiz workspaces are not the same as Xfce (or GNOME or KDE) workspaces.  What does your pager plugin look like?  Mine shows the four desktops only when I set the # of desktops in Compiz to, otherwise it shows one desktop divided into four.

---

### Post by john.nicholls on 2007-12-20
Screenshot attached. The pager is slightly to the left of middle showing Firefox on the fourth desktop.

---

### Post by cardinals_fan on 2007-12-20
I am getting very confused.  When my Compiz settings have 2 by 2 and 1 desktop, i get 1 subdivided desktop in the pager.  If I change the settings to have 4 desktops, I get 4 desktops in the pager (as shown in my earlier screenshots).  If worst comes to worst, I suppose that I can use the Expo plugin in Compiz to  manage my desktops - but it's not quite as convenient as the pager.

---

### Post by cardinals_fan on 2007-12-20
Update: I am (at least temporarily) off of Compiz.  The pager plugin is vastly more efficient than Expo and I value it more than the desktop bling.  I made an icon to launch Compiz, so I can have it back if I need it.  Xfwm4 is actually quite nice (and I certainly don't miss the crashes :wink:).

---

### Post by cardinals_fan on 2008-01-06
I'm marking this thread as solved.  I still can't make Compiz and the pager cooperate, but Xfwm4 is **very nice**, and I don't really miss Compiz.

---

### Post by Martel on 2008-03-26
I had this same problem until I changed horozontal virtual size to 4, vertical to 1, and desktop number to 1. Then I removed the pager panel and  added it again.

Hope this helps. The bling is nice.

---

### Post by cardinals_fan on 2008-03-26
> **Martel said:**
> I had this same problem until I changed horozontal virtual size to 4, vertical to 1, and desktop number to 1. Then I removed the pager panel and  added it again.

Hope this helps. The bling is nice.
I tried that and it didn't work, but thanks anyway.  It all turned out OK because I'm actually much happier using Xfwm than I was using Compiz.

---

