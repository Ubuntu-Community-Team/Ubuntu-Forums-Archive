---
title: "Ubuntu 9.10 Desktop obscured"
date: 2009-10-30
forum: Desktop Environments
---

### Post by awbrns on 2009-10-30
Hi all,

I've encountered a problem that has me baffled. I just upgraded to ver 9.10 and when I login (I'm the main user with the root password) everything initializes except my desktop is a black screen.  All the panels are there and all the applications seem to work. Also, when other users log in, their desktops function normally.  one final note, when I log out I get a glimpse of my actual desktop just before the logout finalizes.  I should let you know I'm not a computer person, just a windows refugee.  I've rarely used the terminal so my grasp of it's usage is limited.  I appreciate any help you can provide.

Alec

---

### Post by gnat56 on 2009-10-30
I've been having a similar problem.  My Gnome Panels are semi-transparent, and I can see my desktop through them.  But I can't see my desktop or any icons on it.  I've also noticed that when I maximize a window, it goes all black except for it's titlebar.

I have found a solution (sort of).  If you're willing to not have the desktop effects that are provided by Compiz, go to System/Preferences/Appearance, then click on the Visual Effects tab and select None.  This will give you your desktop back.

If you still want transparency, go to Applications/System Tools/Configuration Editor, then in the left panel of that window, navigate to /apps/metacity/general, and select compositing_manager.  You'll now have some transparency.

I hope this helps.  If you want desktop effects and your desktop, you're in the same boat as I am.

--Nathaniel

---

### Post by DynastyX on 2009-10-30
I've had this same problem, when I reboot everything goes back to normal but all my compiz settings get forgotten.

---

### Post by cdnjay on 2009-10-31
I had this same problem and disabling the visual effects "solved" it for me as well.  It just occurred suddenly. I tried restarting the computer, restarting nautilus and deleting the nautilus user data to no avail.  My guess now is that there is some kind of compatibility issue with my video card driver with 9.10, not sure though.

Jason

---

### Post by awbrns on 2009-10-31
> **awbrns said:**
> Hi all,

I've encountered a problem that has me baffled. I just upgraded to ver 9.10 and when I login (I'm the main user with the root password) everything initializes except my desktop is a black screen.  All the panels are there and all the applications seem to work. Also, when other users log in, their desktops function normally.  one final note, when I log out I get a glimpse of my actual desktop just before the logout finalizes.  I should let you know I'm not a computer person, just a windows refugee.  I've rarely used the terminal so my grasp of it's usage is limited.  I appreciate any help you can provide.

Alec
Hi,
Just to update my previous post. I tried the suggestion to select "none" for visual effects.  Tadaa! My desktop returned to normal.  Interesting note tho, apparently the drivers that were used in the previous version are no longer available.  Which is why the background was black.  Any suggestions on driver support/downloads? I have an older ati radeon video card if that's a consideration.  Again, I know just enough about linux to get into trouble.  Remember that if your replies are somewhat technical.
Thanks!
Alec

---

