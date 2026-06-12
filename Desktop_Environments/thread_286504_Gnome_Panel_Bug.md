---
title: "Gnome Panel Bug"
date: 2006-10-27
forum: Desktop Environments
---

### Post by imaca on 2006-10-27
Hi,
I have a radeon 9800 card and recently got a new 24" monitor.
After a short time of using the new montor Gnome refused to start either crashing to the login screen or locking up completely.
After 2 weeks of checking hardware and reinstalling Ubuntu 4 times I have finally found the cause of my woes.
Because of the high resolution of the monitor I increased the size of the top panel to 36 pixels. I also have panels set to solid colour.
The combination of these causes my system to crash.
36 pixels and "none" for background is OK, as is "solid color" and 24 pixels.
This is quite repeatable and happens with the fglrx or ati driver.
I can't believe such a small thing can cause the system to crash!
Is this bug already known?

---

