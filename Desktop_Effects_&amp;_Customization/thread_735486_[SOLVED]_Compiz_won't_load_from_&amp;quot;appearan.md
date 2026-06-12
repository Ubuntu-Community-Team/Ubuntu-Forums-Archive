---
title: "[SOLVED] Compiz won't load from &amp;quot;appearance settings&amp;quot;"
date: 2008-03-25
forum: Desktop Effects &amp; Customization
---

### Post by ezramorris on 2008-03-25
Hi,
I recently installed Compiz, and it worked fine. I used to go System > Preferences > Appearance > Visual Effects, and then choose 'None' or 'Custom' as I wanted.

However, today, when I click custom, the following happens:

Time (s)  |  Event
0             |  I click on the 'Custom' radio button. The dialog greys out until...
10           |  A message appears, which says "Desktop effects could not be enabled". The 'None' radio buttons re-selects.
14           |  The WM flickers, and it appears Compiz has loaded. If I'm quick I can move windows so they wobble, and activate the desktop cube, etc. as per my settings.
22            |  The WM flickers again, and the Compiz effects are removed.

I don't think this is necessarily to do with Compiz, since if I run Compiz from, say, the terminal, it loads fine.

I'm wondering if Appearance isn't waiting long enough for Compiz to load.

Any help would be much appreciated.
Thanks in advance.

---

### Post by codeslicer on 2008-03-25
Try opening up a terminal and typing "gnome-appearance-properties" then enable the effects. Paste the output here.

---

### Post by ezramorris on 2008-03-26
> **codeslicer said:**
> Try opening up a terminal and typing "gnome-appearance-properties" then enable the effects. Paste the output here.

Hi, it appears that this issue has resolved itelf, after I freed up a bit of disk space.

Thanks, anyway.

---

