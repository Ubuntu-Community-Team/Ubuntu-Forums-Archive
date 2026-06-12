---
title: "Screen flicker"
date: 2010-05-13
forum: Desktop Environments
---

### Post by kawshik84 on 2010-05-13
Hi,

I am new to UBUNTU. I have downloaded the ver10.04.
I am running it on my laptop with a NVIDIA GeForce GO 7600 128MB graphics card. I am using the NVIDIA driver on the system.

The screen flickers randomly after say every 1 min. By flickering I mean it just refreshes and goes blank for say 1ms during the refresh. It happens even more if I turn on CompViz option.

Is there a way around this?

Thanks.

---

### Post by rhersel on 2010-06-22
Well there are alot of things you could try. If you search the forums you will find several recipes. Unfortunately only this script really works (for me with exactly your environment):

#!/bin/bash
while true; do
    nvidia-settings -q all > /dev/null
    sleep 25;
done

This script forces the Nvidia powermizer every 25 seconds to stay on the highest level and not switch between power levels which causes the flicker.

Launch the script from your autostart or start it manually on demand.

---

### Post by turin13 on 2010-08-15
...which can overheat and burn you graphics card.
This is not a solution.

---

