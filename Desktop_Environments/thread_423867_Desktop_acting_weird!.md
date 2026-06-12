---
title: "Desktop acting weird!"
date: 2007-04-26
forum: Desktop Environments
---

### Post by dogeatery on 2007-04-26
I'm not even sure how to begin describing this problem.  I just recently clean-installed Xubuntu Feisty onto my Dell Inspiron 600m from a live CD and it's been working great for a few days.  I have been thrilled with its ease of use and clean good looks over my past Ubuntu installation.

This morning I was using it like normal, getting news online and downloading a torrent, installed flash 9.0 to view espn.com pages... and then I noticed that the title bars were missing from all of my windows.  Maximized windows and smaller windows,  so I have to click 'file'--> 'quit'

No problem, thought I should just restart and it would go away but I have done this and everything automatically opens up again and still without title bars.  Not only this, any new applications I open appear in the top left corner with title bars 'cut off' by the edge of the screen.  AND when I middle click with my mousewheel, instead of a desktop environment menu I get only 'add or remove workspace' but when I click to add a workspace it gives me an error message.

I'm sorry I can't be any more specific unless you tell me what you need to know.

-dogeatery
:confused:

---

### Post by dogeatery on 2007-04-26
Ok problem solved!

I learned that xfce has a minor bug whereby the desktop environment sometimes goes on the fritz when it's got lots of windows open.  The problem I had was with the window manager, specifically.

The solution was to open a run window with alt+f2
-------------------> type 'xfwm4 restart'
-------------------> everything snapped back into place  :guitar: 

If the desktop itself goes away:
-------------------> alt+f2
-------------------> type xfdesktop restart

I hope this info can help someone else in future!  

-dogeatery

---

### Post by firfin on 2007-04-27
Good for you that you solved it. I am experiencing the same problem on a 'standard' ubuntu install. Do you know if this problem also exists for Gnome?
And if so how to restart that windows manager?

---

### Post by dogeatery on 2007-05-26
sorry man, I sure don't... try uninstalling gnome: sudo aptitude remove gnome-desktop

and then re-installing it: sudo aptitude install gnome-desktop

---

