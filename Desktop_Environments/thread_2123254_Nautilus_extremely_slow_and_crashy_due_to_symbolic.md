---
title: "Nautilus extremely slow and crashy due to symbolic link in Templates"
date: 2013-03-07
forum: Desktop Environments
---

### Post by xiphosurus on 2013-03-07
Recently I was moving some files around to create space on my SSD. I have a faulty mouse, so some actions occurred unexpectedly. Next thing I know, Nautilus was using 100% CPU even after a reboot. It was extremely slow to start, and crashes upon trying to close. Strange thing was that sudo nautilus works perfectly fine, as is Nautilus in other users accounts. Only mine. So I was sure it was just some stupid configuration in Nautilus... and I googled for help. But no matter how I tried to reset Nautilus, problem still same.

To cut the story short, after 2 days of tinkering, I used system monitor to track what files Nautilus was accessing. Strangely, upon opening Nautilus, it was trying to access the picture folder I had moved out of my SSD and symlinked back into ~/Pictures. I then used "find ~ -lname /path/to/folder" and found that my stupid mouse had caused me to create a symlink to that picture folder in ~/Templates!!! Once I deleted this symlink, problem solved. Not sure if this should count as a bug? But nevertheless posted here in the small chance that I can save someone else 2 days of time. :)

---

