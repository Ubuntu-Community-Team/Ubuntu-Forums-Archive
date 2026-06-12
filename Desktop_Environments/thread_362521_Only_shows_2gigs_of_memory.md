---
title: "Only shows 2gigs of memory"
date: 2007-02-15
forum: Desktop Environments
---

### Post by randyleepublic on 2007-02-15
My mobo's bios correctly shows 4 gigs of ram.  But System monitor and saidar both only show 2 gigs.  Help!

---

### Post by Jussi Kukkonen on 2007-02-15
I believe the kernel is configured to support memory sizes <4gb... If that's the case, you'll need to compile your own kernel to get the rest in use. There are several howtos in the forums, if you're interested in doing that. Use the old kernel config, just change the *"High memory support option"* in *"Processor type and features"*.

---

