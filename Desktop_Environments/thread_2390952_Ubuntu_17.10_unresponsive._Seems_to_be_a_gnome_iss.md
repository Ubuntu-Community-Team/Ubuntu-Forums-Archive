---
title: "Ubuntu 17.10 unresponsive. Seems to be a gnome issue."
date: 2018-05-04
forum: Desktop Environments
---

### Post by davidsinfield on 2018-05-04
I'm getting lockups on Ubuntu 17.10 after upgrading from 16.10.

Here's a small excerpt from my syslog:



May  4 10:47:12 dev_1 gnome-software[2210]: Ignoring unexpected response
May  4 10:47:12 dev_1 gnome-software[2210]: g_byte_array_remove_range: assertion 'index_ + length <= array->len' failed

I'm getting about 20 of these every second. A bit more debugging info would be nice.

I like the gnome desktop and am reluctant to bin it for an alternative so I want to explore solutions before doing anything drastic. I can't find the 2210 error mentioned anywhere.

Any ideas how to fix it?

---

### Post by mörgæs on 2018-05-04
Upgrades are causing numerous problems. It's probably the most common class of problems reported here.
Have you considered a fresh install of 18.04?

---

### Post by deadflowr on 2018-05-04
Looks related to this bug;
[lpbug]1723362[/lpbug]

---

