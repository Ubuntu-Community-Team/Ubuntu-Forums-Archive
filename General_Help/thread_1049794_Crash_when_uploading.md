---
title: "Crash when uploading"
date: 2009-01-24
forum: General Help
---

### Post by SukruH on 2009-01-24
Hello,

When I connect to my computer on WAN with FileZilla's ssh client and download at ~6-7 MB/s, it crashes after a while, and the client says "No route to host".

When I try to ping it, it says:
From *[ip here]* icmp_seq=3 Destination Host Unreachable

It works fine if I reset the computer, but doing that is not easy as I do not have physical access to the box whenever I want.

This has happened more than six times now...

---

### Post by scarf on 2009-01-25
this sounds like an issue with the remote computer's network interface/card.  is it possible to install another NIC and see how that goes?

---

### Post by SukruH on 2009-01-25
Thanks, I'll try that.

---

