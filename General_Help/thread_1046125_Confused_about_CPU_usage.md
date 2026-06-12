---
title: "Confused about CPU usage"
date: 2009-01-21
forum: General Help
---

### Post by Piraja on 2009-01-21
Dear all,

I'm wondering why my present CPU usage is around 55-60% even though Top shows values that add up to ca. 10-15% &#8212; see the attached screenshot with Conky, showing that MOC, Xorg and Conky are the top 3 processes, their CPU footprint adding up to some 10%. 

Maybe this is just something I don't quite understand about CPU usage and Top? Or perhaps something *is* wrong and I should be alarmed by this?

Regards,

Piraja

---

### Post by dabl on 2009-01-21
If you run "htop" (you might have to install the package) in the upper left corner it shows the CPU usage statistic.  I just now compared the htop usage with my gkrellm monitor, and there is also a large discrepancy.  It looks like gkrellm is showing the "instantaneous" usage (2% - 6%) but htop is showing the "highest lately" usage (12%).  Maybe your monitor is holding the highest usage for a period of time, or something like that?

Or else your graphical monitor is just not displaying it right.

---

### Post by Piraja on 2009-01-21
Thank you dabl,

I had installed htop previously but it did not occur to me that it would monitor differently. CPU usage is updated frequently in htop (ca. 1 sec interval), while top seems to show some sort of more static average. It still puzzles me that the values are so high: in htop, they vary between 40 and 90 percent, while the ciphers in the htop CPU% column still add up to only ca. 10%.

---

