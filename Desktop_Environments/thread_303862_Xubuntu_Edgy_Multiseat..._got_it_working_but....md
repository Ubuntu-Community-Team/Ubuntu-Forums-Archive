---
title: "Xubuntu Edgy Multiseat... got it working but..."
date: 2006-11-20
forum: Desktop Environments
---

### Post by tinsami1 on 2006-11-20
Hi folks,

I'm trying out a multiseat setup using Xubuntu 6.10.

Got everything working, but the keyboard mappings needs some tweaking.

My problem is, when a user from any of the terminal logs out, X or GDM does not bring me back to the login screen (gdmgreeter?) -- just a blank screen.  CTRL-ALT-Backspace doesn't work when in this situation.

](*,) 

Any tips on where to look at?

Thanks.

---

### Post by ingo on 2006-11-22
yes, /etc/X11/xorg.conf is likely to be the culprit, but when did this problem start occurring?

---

### Post by tinsami1 on 2006-11-22
Problem solved!  The problem was with my /etc/gdm/gdm.conf-custom. I removed all reference to vt7 in all my command= sections, and things are as expected.

---

### Post by erpod on 2007-09-18
Dear All, 

**How did you build a multi-seat with Xubuntu?**
There are several methods listed on the Web, 
which one did you use? [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

I s it stable? 
I OpenSuse better for Multi-seat? (KDE is quicker with OpenSuse)
What graphic card did you use, aso?

Even if you cannot answer all, a few answer will be appreciated

Thanks

---

