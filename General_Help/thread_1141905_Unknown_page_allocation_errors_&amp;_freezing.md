---
title: "Unknown page allocation errors &amp; freezing"
date: 2009-04-28
forum: General Help
---

### Post by ricmitch on 2009-04-28
I'm running Hardy server on a headless machine (interaction is solely by SSH) and it keeps freezing up and becoming unresponsive quite regularly. When I check the logs on reboot, there are a lot of "page allocation failure" messages for different processes - starting with:
> swapper: page allocation failure. order:1, mode:0x4020. Just before the the freezes there is very high memory usage.

The rest of the log for an average freeze-up can be found at the link below:
[http://pastebin.com/m235a1278](http://pastebin.com/m235a1278)

I'm at a loss.

---

### Post by codeseer on 2009-04-28
Have you tried upgrading the kernel?

---

### Post by ricmitch on 2009-04-28
I'm running 2.6.24-21-server at the moment. Can't update it any more via apt and 8.04 is LTS after all - ideally I don't want to have to upgrade beyond that.

---

### Post by codeseer on 2009-04-28
From my readings on the error, it seems like Intrepid version-equal kernels are recommended for the issue. It seems like that error is commonly related to the kernel. You could probably upgrade all the way, unless you have some specific reason not to.

---

### Post by gna on 2009-05-13
Any new thoughts on this, i am experiancing same problems, and an upgrade to intrepid is not an option because that changes the full OCFS2 version which would cause me an obligatory upgrade on 5 server at once.

And anway, this LTS OUGHT to be correct that, because then, why is this called LTS when its not supposed to be supported.

---

