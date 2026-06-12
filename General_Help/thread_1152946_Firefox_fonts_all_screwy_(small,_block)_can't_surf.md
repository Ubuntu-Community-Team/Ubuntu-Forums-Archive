---
title: "Firefox fonts all screwy (small, block) can't surf or read well"
date: 2009-05-08
forum: General Help
---

### Post by Dragon45 on 2009-05-08
I just did a clean install/format to Jaunty.  Everything was working fine for a day, and then I apt-get 'ed Wine. I closed/reopened firefox and noticed most of my fonts in firefox were all screwed up. They all render "properly"; there's no weird characters, but everything looks much smaller and blockier and generally more painful to read. 

I did apt-get remove and then dpkg --purge of Wine and the problem persits.

I think some fonts are missing but i have no idea which ones. I tried the following steps as suggested in other possibly-related threads:

1) Since this is a dual-boot machine, I copy-pasted all my fonts from my font directory in Windows to ~/.fonts, chmod o+rwx * on them, and then did fc-cache.

2) sudo apt-get install ttf-mscorefonts-installer
3) Tried installing some other ttf-someotherrandomfonts

Still nothing is working. This is possibly the most annoying problem I've ever faced. I have not done anything else with this system.

---

### Post by magump on 2009-05-08
In Firefox, you might try going to Edit>Prefernces and clicking on the Content tab.  There you will see Fonts & Colors.  Check the default font size, etc.

Hope this works.

---

### Post by bacardiandwatermelon on 2009-05-08
Ctrl+0 resets the zoom in Firefox...

---

### Post by magump on 2009-05-08
Just thought of another thing for you to check.  When you "purged" wine, your system's screen resolution may have changed.  Does the change in fonts change the desktop fonts also?

---

### Post by caro on 2009-05-13
I've had the same thing.  Instead of Arial looking like Arial, it looks like an old style font or something.  For some reason, this works for me:

Close Firefox
Go to System > Preferences > Appearance 
Click on the font tab
Select the fonts you want.  Even if they haven't changed, click on them again and close.
Launch Firefox.

Hope it works for you.

---

### Post by joelop on 2009-06-03
Hi All,

I'm having the same problem here since the day I installed Ubuntu 2 weeks ago. When surfing con **Firefox** I find hard to read articles from many sites because the font is too small (for example this forum and the body message I'm writing in). Ctrl+ is not a good option since it breaks the page layout and I didn't have this problem in Firefox for Win XP.

With **Thunderbird** I have the same problem when reading messages. Personal emails are OK (it's not great though), but when I have to read messages coming from a Yahoo! discussion list I'm member of it's completely crappy.

Is there anything we can do or 'Ubuntians' have to bear with it :(

PS: I had this problem before installing Wine.

---

### Post by Teutorix on 2009-06-03
Ubuntu has a dirty habbit of making the screen resolution too high, try change it to a lower resolution.

*warning* make sure it is a compatible resolution on your monitor, ubuntu does NOT check first *warning*

---

### Post by joelop on 2009-06-03
> **Teutorix said:**
> Ubuntu has a dirty habbit of making the screen resolution too high, try change it to a lower resolution.

*warning* make sure it is a compatible resolution on your monitor, ubuntu does NOT check first *warning*

I just tried and it looks the resolutions on my screen is the good one.

---

