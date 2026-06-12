---
title: "thunderbird, how to access profile manager?"
date: 2010-10-28
forum: Desktop Environments
---

### Post by ubto66 on 2010-10-28
OS: ubuntu 10.04 lts.
Email client: thunderbird.

Asking how to access thunderbird's profile manager?
How to erase a profile?
How to create a profile?

Please write a detailed description.

---

### Post by mcduck on 2010-10-28
open a terminal and run "thunderbird -p"

You'll see buttons that allow you to both create and delete profiles.

---

### Post by Swiftjay on 2010-10-28
> **mcduck said:**
> open a terminal and run "thunderbird -p"

You'll see buttons that allow you to both create and delete profiles.

doing normal p gives you this error: run-mozilla.sh: Cannot execute /usr/lib/thunderbird-3.1.5/thunderbird-bin.pure.


Has to be a capital thunderbird -P just checked man thunderbird to confirm

---

### Post by ubto66 on 2011-03-03
Thank you.
It worked.

---

### Post by dhamumodi on 2011-08-18
in ubuntu 11.04 can't run thunderbird via terminal

---

### Post by gocoder on 2011-11-23
Check the Software Center or synaptic to see if it's installed.  If "which thunderbird" returns nothing and thunderbird is installed, check your PATH environmental variable.  In Oneiric, thunderbird is in /usr/bin.  That path should be in PATH.

---

