---
title: "Invalid gtk theme file?"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by rkrash34 on 2007-12-01
Ok, I search the forums but couldn't find anything referencing this particular problem.

Anyway, all I'm trying to do is modify a gtk theme. The theme I want to modify initially installs perfectly. So all I'm doing is unpacking it and changing a few of the images, button colors, menu background, etc. I make sure the name and format of the images is exactly the same before they r replaced, then I repack the theme file to a tar.gz and when I try to install it says "invalid file format"? what gives? I'm not changing any settings, just image files?

---

### Post by rkrash34 on 2007-12-01
I think I may have found part of the problem.... I'm having to uncompress the original tar.gz file under root, so the uncompress file and in turn the new compressed file belong to root, and when I try to install under my user name I assume the theme manager is being denied access. So I log in as root and change the file owner ship to my user name, and log back in as my user name, but the file still appears to be locked and belonging to root? yet again, what gives?

---

### Post by rkrash34 on 2007-12-01
Anyone?

---

### Post by rkrash34 on 2007-12-01
well figured out the permissions problem, apparently u have to reboot instead of just logging out and logging back in. but that apparently isn't the problem as i'm still getting the invalid file message. anyone out there?

---

