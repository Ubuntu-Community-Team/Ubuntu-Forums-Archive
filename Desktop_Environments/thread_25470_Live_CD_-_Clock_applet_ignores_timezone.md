---
title: "Live CD - Clock applet ignores timezone?"
date: 2005-04-10
forum: Desktop Environments
---

### Post by Enki on 2005-04-10
Hi,

Using the 5.04 live CD (tried both i386 and AMD64) the clock applet seems unaware of the chosen timezone. That is, when I choose Europe/Amsterdam in Time and Date settings, the time shown there is correct, but the clock in the top panel is 2 hrs behind. Selecting 'Use UTC' makes no difference.

Any idea on what causes this? Has anyone experienced the same with Hoary installed (ie not using live cd)?

Regards

---

### Post by PhilD on 2005-04-10
Yes, I had that happen with the live. I have Ubuntu installed on the hard disk now and it's correct.

---

### Post by mandy2tom on 2005-04-20
[QUOTE=Enki]Hi,

Using the 5.04 live CD (tried both i386 and AMD64) the clock applet seems unaware of the chosen timezone. That is, when I choose Europe/Amsterdam in Time and Date settings, the time shown there is correct, but the clock in the top panel is 2 hrs behind. Selecting 'Use UTC' makes no difference.

Any idea on what causes this? Has anyone experienced the same with Hoary installed (ie not using live cd)?

Regards[/QUOTE]
 It was bugging me too. Im running live cd
select time zone, close 
alt-f2
killall gnome-panel

---

