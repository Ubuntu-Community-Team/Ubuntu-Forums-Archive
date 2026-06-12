---
title: "trouble starting the rt kernel"
date: 2009-05-20
forum: General Help
---

### Post by hortstu on 2009-05-20
Im in the PREEMPT RT kernel right now. ( not anymore I couldn't get the page to load)  I got some error messages at start up but other than the screen being a 1/4 inch off center I don't see a difference.

Here's my memory of the error message.

low graphics mode
error found - need to update configuration
(EE) NVIDIA (0): Failed to load NVIDIA kernel module
(EE) NVIDIA (0):***Aborting***
(EE) screen(s) found, but none have usable configuration

---

### Post by hortstu on 2009-05-20
Am i asking this in the right place?

---

### Post by hortstu on 2009-05-20
Is there a better place to put this question... where it might get an answer?

---

### Post by adamogardner on 2009-05-20
> **hortstu said:**
> Is there a better place to put this question... where it might get an answer?

Yeah,  but it might be uncomfortable.

---

### Post by adamogardner on 2009-05-20
what are you trying to do?  Why are you in this PREEMPT Kernal thing?  Are you tripping out on an error message that isn't effecting you?

---

### Post by hortstu on 2009-05-20
I need the realtime kernel to work in order to use a peripheral at its best.

The kernel doesn't work properly.  There is an error message before it even starts.

---

### Post by adamogardner on 2009-05-20
Why don't you just surf the web like everyone else?

---

### Post by hortstu on 2009-05-20
Or maybe I could pull an "office space" on this box.

---

### Post by vivichrist on 2009-05-24
I went to [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) and
grabed the 2.6.29-4 source deb and applied the rt16 patch to it from
[http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/). then copied across
the /boot/config-2.6.28-12-generic to that kernel source root directory.
did "make gconfig" and opened that config changed to full pre-emtion and
timing to 1000 like Luke Macneil has done. "make-kpkg clean" then
"CONCURRENCY_LEVEL=2 fakeroot make-kpkg --initrd --append-to-
version=-custom kernel_image kernel_headers" installed the resulting
packages headers first. and hey presto. note. CONCURRENCY_LEVEL=2
because my **** has duel core and this required installation of certain
dev packages. this is amd64 though. can point you to a few sites if you need more details.

---

