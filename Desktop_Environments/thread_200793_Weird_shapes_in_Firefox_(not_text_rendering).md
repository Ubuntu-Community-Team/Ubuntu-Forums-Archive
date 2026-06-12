---
title: "Weird shapes in Firefox (not text rendering)"
date: 2006-06-20
forum: Desktop Environments
---

### Post by salzo on 2006-06-20
Hi! I recently installed Dapper and Firefox is showing some weird shapes. I can't explain easily how does it looks (image attached, weird-firefox-dapper1.jpg).

I'm working with:
- Chip Integrated ProSavage8 3D Graphic (VIA KM266)
- StudioWorks LG Monitor

The shapes appear everywhere (ubuntuforums, gmail, etc...). I worked with Breezy a long time and never saw something like that. I've not made any change in the default configurations. I installed Dapper from the Desktop CD.

Somebody has any idea?..where can I begging looking for?

Thank you very much.

---

### Post by Jasper Houtman on 2006-06-20
Do you have the same problem in Galeon?
I would try a complete reinstall of firefox (use synaptic complete removal, and then install with add/remove programs).

Be sure to make backups of your plugins though.

---

### Post by salzo on 2006-06-20
Hi! thanks. I have not tried Galeon but downloaded the Firefox distro from getfirefox.com (firefox-1.5.0.4.tar.gz) extracted and executed it, and happened the same.

---

### Post by Jasper Houtman on 2006-06-20
Prob won't work until you delete the shared directory in your home folder.

Do a complete removal of firefox first.
Then press Ctrl+H in nautilus in the Home directory to find it (.Mozilla), and then delete it (preferably after you backed up your plugins)

After that reinstall the latest version of firefox.

---

### Post by salzo on 2006-06-21
Hi! Thanks...
I haven't made the firefox complete removal prob but I have noted that the problem  is only presented when I'm using a 1024x768 resolution (or an 800x600 one). I can only use this resolution because in highers, the maximum refresh rate my monitor supports is 60Hz and it's horrible. With 1280x1024 this doesn't occurs. I believe I have a problem in my X configuration.

---

### Post by salzo on 2006-06-21
Hi! Looking for some basic configurations in my /etc/X11/xorg.conf, I specified my monitor's supported HorizSync and VertRefresh (Monitor section) and changed the DefaultDepth value (Screen section) from 16 to 24. The problem is not happenning (well, It does happend, but instantaneously and is almost 
imperceptible). I'm now sure it's not a Firefox problem.

I will read about Xorg and will try to tune this settings.

Thank you very much...

---

