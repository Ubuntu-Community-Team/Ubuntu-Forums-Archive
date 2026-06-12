---
title: "Ubuntu 24.04 6th Monitor Not Working [SOLVED]"
date: 2024-05-30
forum: Desktop Environments
---

### Post by joshebosh on 2024-05-30
Figured I'd post my solution if it helps others.

I have an
ASROCK Livemixer Z790 (1 DP + 1 HDMI builtin ports)
NVIDIA GTX 4060 (3 DP + 1 HDMI)

for total of 6 monitor ports

Pluggin in the 6th Monitor would cause the desktop to glitch out, turning everything white, regardless of any combo of ports used...
I read around on other forums which were talking about Nvidia BaseMosaic only able to handle up to 5 monitors, but none of the suggestions helped.
Eventually I stumbled on an NVIDIA config that solved my problem, which I did not find amidst my reading, so figured I'd post here to help the next person

so to get all monitors working I did

```
$ nvidia-settings
```

then click on "PRIME Profiles" then click "NVIDIA Performance Mode"

hope that helps

---

