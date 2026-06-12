---
title: "Potentially dangerous Desktop Sharing bug?"
date: 2005-05-21
forum: Desktop Environments
---

### Post by philipacamaniac on 2005-05-21
I was experimenting with the Desktop Sharing features builtin to KDE, which is really just a frontend for VNC protocols.

When you enable "Allow uninvited connections" (how a normal VNC server works), then one important option, "Allow uninvited connections to control the desktop", doesn't work. As in, whether that box is checked or not, the client can control the desktop.

Anyone wanting to use the Desktop Sharing feature for letting people view their screens should be aware of this. I didn't test to see if it applies to the Invitation-based connections, but I'm sure it does.

My bet is that this is an upstream bug, so I'll be reporting it to the KDE bugzilla, not Ubuntu's. Has anyone else experienced this behavior?

---

