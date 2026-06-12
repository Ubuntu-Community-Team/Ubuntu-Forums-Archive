---
title: "cpufreqd screwed up after jaunty upgrade"
date: 2009-06-02
forum: General Help
---

### Post by KeyserSoze93 on 2009-06-02
I have a Dell Latitude D600, and I was running Hardy on it up until yesterday. Then, I decided to upgrade to Jaunty (via Intrepid), and so far I'm thinking I should have stayed with Hardy.

The upgrade went fine, however NetworkManager refused to connect and in the end I had to switch to WICD. Then, next major issue: cpufreq-selector takes ages to switch modes...

Basically, I run say: cpufreq-selector -g performance, so I can play a game without it stuttering, and the terminal just hangs for about a minute before changing. Nothing like this was happening before.

Any ideas?

---

### Post by KeyserSoze93 on 2009-06-02
I may have solved this... For some reason, running cpufreq-set -g performance seems to work... No idea how this differs from cpufreq-selector, but fingers crossed - it seems to have solved this...

I only found out there was an app called cpufreq-set by ACCIDENT, when I did tab completion on cpufreq- to see what else came as part of the package...

---

### Post by dcstar on 2009-06-03
> **KeyserSoze93 said:**
> I may have solved this... For some reason, running cpufreq-set -g performance seems to work... No idea how this differs from cpufreq-selector, but fingers crossed - it seems to have solved this...

I only found out there was an app called cpufreq-set by ACCIDENT, when I did tab completion on cpufreq- to see what else came as part of the package...

Upgrades invariably have more problems than a fresh install, you may want to consider creating a separate /home partition and doing a fresh 9.04 install.

---

