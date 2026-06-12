---
title: "Update Manager bug?"
date: 2010-02-19
forum: Desktop Environments
---

### Post by keforex on 2010-02-19
Every once in a while the update manager pops up telling me I have updates I can install. I always update, and it has been working great.

Today the update manager popped up again, and when I click on "Install Updates" absolutely nothing happens. No password dialog box, nothing. The button bevels, comes back and nothing happens. Is this a bug? How to solve it?

---

### Post by Hero of Time on 2010-02-20
Refresh the list and see if that works. If it doesn't, you can manually check for updates and update your system using Synaptic Package Manager, or from a terminal using 'sudo apt-get update && sudo apt-get upgrade'.

---

### Post by keforex on 2010-02-22
Thanks for that - it does work when I update the list, but this used to not be an issue - so I wonder if it's a new bug or what...

---

### Post by Hero of Time on 2010-02-23
Just wait for the next batch of updates, maybe it really is a bug. To make sure, check the last release of the update-manager package, both core and GUI part.

---

