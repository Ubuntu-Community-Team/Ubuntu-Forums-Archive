---
title: "2 on screen displays for Thinkpad volume?"
date: 2005-12-21
forum: General Help
---

### Post by MartinJ on 2005-12-21
not sure if this is in the correct forum...

Using a Thinkpad R32.

After doing a reinstall to upgrade to Breezy I set up the Thinkpad buttons using the KDE settings and tpb.  Everything works great except that there is now an extra On Screen display at the bottom of the screen.  I'm not sure how to remove this as I only want the bigger, themed display in the middle of the screen.

I've attached a screenshot.

Thanks,

---

### Post by lordbob99 on 2005-12-22
I spent hours trying to figure out this exact same problem..

So the one you want to keep (that's in the middle of the screen) is the Thinkpad Buttons KMilo plugin.  The one one you want to get rid of (on the bottom of the screen) I believe was tpb (Thinkpad Buttons).

Removing the tpb package (either using apt-get or synaptic) should eliminate the annoying bar on the bottom.

Hopefully this allows you to not bang your head on the keyboard as long as i did. ](*,)

---

### Post by MartinJ on 2006-01-11
Thanks for the help.  I decided I needed to keep tpb for controlling some other of the thinkpad buttons.  However, I turned off the display for it by editing /etc/tpbrc and changing OSD to off.  Everything working correctly now.

---

