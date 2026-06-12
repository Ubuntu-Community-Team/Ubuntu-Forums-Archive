---
title: "[SOLVED] libx11-6 conflict"
date: 2008-12-18
forum: General Help
---

### Post by MoebusNet on 2008-12-18
After the latest 8.04.1 updates today, I can no longer resize my Desktop. When I checked the x11 files in Adept Manager, I found this conflict:

libx11-6

pre-required: x11-common >= 1:7.0.0
conflict: xlibs-data < 1:7.0.0

How can I fix this?

EDIT - This affected my Ubuntu 8.10 guest on VirtualBox 2.0.6 with Ubuntu 8.04.1 host. Reinstalling my Guest Additions cured the Desktop issue, but I seem to have a borked Network Manager in the guest OS. Needless to say, I'm quite hesitant to install the latest updates on my host OS until this all gets sorted out!

---

