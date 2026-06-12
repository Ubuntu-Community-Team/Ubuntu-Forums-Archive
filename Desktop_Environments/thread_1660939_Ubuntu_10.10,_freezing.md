---
title: "Ubuntu 10.10, freezing"
date: 2011-01-06
forum: Desktop Environments
---

### Post by Neikius on 2011-01-06
So, I have just installed ubuntu 10.10 using wubi on a sempron 2800+ and radeon 9250. Almost everything was working ok, but for the hardlocks that occured at the rate of 2 per hour. Finally I just gave up on it. For now.

I suspect the radeon driver that came preinstalled. Why? I had bad experience with the 8xxx radeons in the past (hardlocks too) and it could be something similar. OR it could be something ACPI related I guess. So, any clues, anyone knows of a similar situation? As you know hardlocks don't produce any logs. I will report in a week or so, when I can get back to the affected PC.

---

### Post by MARP1961 on 2011-01-06
I had numerous freezes, especially at startup and shutdown on both Lucid and Maverick versions. It only happened on my old desktop that had had a PCI Wi-Fi card installed. I thought the Linux default driver was causing the problems, so I used ndiswrapper to install the Windows XP driver (which I found on the install disk) that came with the PCI adapter I bought a couple of years ago. No freezes since!

---

### Post by Neikius on 2011-01-10
Hm, I can safely say its not ubunt's fault, most likely its the psu or gpu (a pasive card is heating quite much). It doesn't show up in windows but ubuntu has those nice graphic effects that I guess heat up the card :) Something similar happens when you launch any 3d game on windows in minutes... 

At least we are sure now what is wrong but at the glance I never thought of that. My memories of all the years fiddling with fglrx and crashing all the time came back even though I hoped this was dealt with so I jumped to conclusions.

Anyway this is it I guess. Thanks for trying.

---

