---
title: "Wrong Icons in Icon View; Correct in List View (Nautilus)"
date: 2010-03-15
forum: Desktop Environments
---

### Post by floborg on 2010-03-15
Recently upgraded from Jaunty to Karmic.  Now, I'm not seeing the proper icons for a few file types in Nautilus using the "Icon View."  When I switch to "List View," the icons are correct.  In my icon set, I can't see any obvious differences between the various sizes (16x16, 24x24, etc).  I noticed the same thing with other icon sets, including Humanity.

Some of the offenders include html, txt, key, asc, cfg, and a number of text types.

Anyone have any ideas?

---

### Post by lidex on 2010-03-15
What icon set are you using? Look in "/usr/share/icons" and "~/.icons" and see if the folder for your particular set exists in both locations. If not copy-and-paste so that it is, then logout. If it persists, try switching to different ones and then back. May need to flush your icon cache - or rebuild. Look here:
[http://forums.gentoo.org/viewtopic-t-596363.html?sid=7cd23f4e65884795289decf7e922eb29]("http://forums.gentoo.org/viewtopic-t-596363.html?sid=7cd23f4e65884795289decf7e922eb29")

---

### Post by floborg on 2010-03-15
Well, I only installed the icons to my home.  That caused no problems in Hardy, Intrepid, or Jaunty.  Like I mentioned before, this is happening with other icons sets, including Humanity.

I ran that command in my ~/.icons directory, got a success message, and nothing changed.

---

### Post by floborg on 2010-03-15
I made a USB startup disk from the Karmic LiveCD, booted it up, and saw the same thing with Humanity and my custom icon set.  So, now I doubt I'm the only one with this issue.

---

### Post by lidex on 2010-03-15
First I've heard of that. Did you search the forums?

---

### Post by floborg on 2010-03-16
> **lidex said:**
> First I've heard of that. Did you search the forums?

Of course.  Trying to dig through some more today.  No related posts found so far.

I'm going to take a look at this in a virtual machine with a fresh install as well.

I suspect that the "text preview in icons" might have been broken for Karmic.

---

### Post by floborg on 2010-03-16
I can confirm that the icons in Icon View return to normal when the "Show text in icons" option is turned off.  I guess they expanded the number of mimetypes that work with this feature.  Perhaps, too many are supported considering that some of these contain code.

---

