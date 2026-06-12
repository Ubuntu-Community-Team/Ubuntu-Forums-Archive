---
title: "why regressions?"
date: 2008-11-05
forum: Development CD/DVD Image Testing
---

### Post by kornelix on 2008-11-05
With Intrepid some things that were working before got broken. Others have made lists of these.

My question: why does this seem to happen too often?

First, I am not sure of the meaning of "regression". Sometimes it seems to mean "bug", sometimes it means "lost feature", and sometimes "killed bug that came back to life". So what is the meaning used by developers and administrators?

Many suggestions have been made that more pre-release testing is needed to avoid regressions, and many other suggestions about how to achieve more and better testing. My question is: why does it happen in the first place, and can the development process be improved to avoid this? Is this an unavoidable problem when a project has multiple devleopers, each working on a private copy of the code which is merged later?

I woud appreciate some insight. Thanks.

---

### Post by dmitrijledkov on 2008-11-06
Well regressions will always happen.

As you mind find in any design project if Part A works and Part B works, when you put them together they might or might not work.

Ubuntu core is GNOME. Both projects make a release every 6 months. It is not feature driven but time driven. That means that upto a certain point new features are written and then release is tested and pushed out.

Then ubuntu takes it packages it and tests it for a lot time. (Most of ubuntu developers contribute directly to upstream). During the testing process bugs appear sometimes within software, sometimes simply because of combination of softwares not liking each other. Eg I've install App A, it doesn't like App B, and App B instead of crashing, chrashes App C.

Usually each version update brings bugs. Some of them are brand you, some are "resurrects". Regression means that it worked in previous version before, but now it stopped.

Eash ubuntu release uses latest packages, eg most of the software from new release is either brand new or a new release. So there are very little software which is the same between two releases.

So I wish people stop using words regression when talking about distros. It is all new code all over the place. It's just a new bug, which isn't present in -1 repos.

Hope this explains a little bit.

---

### Post by kornelix on 2008-11-11
Thanks, that was helpful. I still have my doubts about the process. A process that results in so many bugs getting out to end users cannot be optimal. And the bugs are often obvious. I believe that time-driven releases should be delayed as needed to fix known bugs. Regarding killed bugs that come back to life later - it is hard to imagine that this is caused by interaction with some other change - more likely the previous fix was simply lost when new code, cloned before the bug fix and then modified for some other purpose, was merged back in again. Am I wrong about this?

---

### Post by Mutiny32 on 2009-01-15
> **kornelix said:**
> Thanks, that was helpful. I still have my doubts about the process. A process that results in so many bugs getting out to end users cannot be optimal. And the bugs are often obvious. I believe that time-driven releases should be delayed as needed to fix known bugs. Regarding killed bugs that come back to life later - it is hard to imagine that this is caused by interaction with some other change - more likely the previous fix was simply lost when new code, cloned before the bug fix and then modified for some other purpose, was merged back in again. Am I wrong about this?

Move to Debian if you want long release cycles due  to extensive stability testing.

---

### Post by QwUo173Hy on 2009-02-12
I stick with LTS releases on my work machine as it's operation is vital. Everytime a new release comes out, I install it on the laptop around Alpha4, report all the bugs that effect my usage and if they get addressed on time I install the new release on the laptop, otherwise I go back to LTS.

If I install the new release on the laptop I test it for a few weeks and if the features I use are stable I install it on the main machine.

---

