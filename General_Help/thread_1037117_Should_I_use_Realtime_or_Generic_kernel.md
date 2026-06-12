---
title: "Should I use Realtime or Generic kernel?"
date: 2009-01-11
forum: General Help
---

### Post by Hooya on 2009-01-11
I don't know when it started showing up, but at some point I started booting into the Real-Time kernel instead of the Generic one.  Should I be?  As a typical desktop user does it matter at all or should I boot into Generic and get rid of my rt kernel?

I've read a little on RT operating systems but there's nothing there that says it's preferred for typical desktop environments.  The rest of the information is all nice and technical, to the point where I don't know if I can read any real-life relevancy to it.

---

### Post by mcduck on 2009-01-11
For all normal desktop use the generic kernel works better. RT kernel allows one program to take much more of computer's power, at expense of all other running programs and services. This is often required for real-time tasks like professional audio recording, but never on typical desktop use.

The generic kernel is more tuned for normal desktop usage and balances the load better with many programs running at the same time.

---

### Post by Hooya on 2009-01-11
Thank you.  So it's totally fine for me to boot into the Generic kernel and then remove the real time kernels, right?

---

### Post by mcduck on 2009-01-12
Yes, it's safe.

---

