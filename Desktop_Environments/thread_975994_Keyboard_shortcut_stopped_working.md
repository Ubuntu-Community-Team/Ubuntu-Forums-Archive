---
title: "Keyboard shortcut stopped working"
date: 2008-11-08
forum: Desktop Environments
---

### Post by Charlotte18 on 2008-11-08
I just updated to 8.10, 64-bit. Everything is fine except this: There's a button on my keyboard above the function keys that looks like a little house. In 8.04, this button opened Firefox, which is what I want it to do. Now after the upgrade  to 8.10, the button opens my Home folder instead. How do I set the button back to open Firefox?

---

### Post by linfidel on 2008-11-09
I'm having problems with my shortcuts, too, after upgrade.  I have several, all used to work, but now, only my volume keys work, but not the mute button.  But they all work with a clean install (which I do in a separate partition).  The clean install does open my Nautilus home folder, though - I think it used to open Firefox.  

Now, for your problem...  :)

Just out of curiosity, does it bring up the home page if you are in Firefox?  I know my same keyboard in Windows XP was somewhat context-sensitive; certain programs responded to that key, and brought up their own home page if they had focus.

Also, do you have Compiz installed (desktop effects).  If so, do you have the configuration manager?  There is a way using that to set keys.  On my system, it recognizes the home key, but it still won't work.  But if I press something like Alt-home, then it does work, and I can run Firefox that way.

If you're interested in trying it, and you don't know how to do it, respond here, and I'll check back and give you more information.

---

### Post by Charlotte18 on 2008-11-09
No, in Firefox, the button for the home page still opens the Home folder and not the web site set as the home page in Firefox.

I don't know what the "configuration manager" is. Under System > Preferences, I don't see any choice that pertains to this problem.

---

### Post by schongal on 2008-11-12
My "home" button also broke after upgrading to 8.04... I used it to launch Rhythmbox.  Now it does nothing.

Any help configuring this button would be greatly appreciated!

Thank you!

---

### Post by Charlotte18 on 2008-11-14
Anybody?

---

### Post by Charlotte18 on 2008-11-18
It appears that the shortcut to open the web browser, along with other shortcuts, can be reset by going to System > Preferences > Keyboard shortcuts.

I will not be able to test whether this works till Sunday.

---

### Post by linfidel on 2008-12-07
My problem may have been different than many others, but I came upon a fix.

I was able to get all the media keys working by a very unlikely (to me) method; I didn't discover it myself, it was reported in a launchpad bug report (300954).

I deleted this file:   ~/.gconf/desktop/gnome/peripherals/mouse/%gconf.xml

After restarting X, the keys worked.

---

