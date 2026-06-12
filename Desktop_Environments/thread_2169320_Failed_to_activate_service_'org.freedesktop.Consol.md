---
title: "Failed to activate service 'org.freedesktop.ConsoleKit': timed out"
date: 2013-08-21
forum: Desktop Environments
---

### Post by troyrock on 2013-08-21
I have been combing through my syslog, trying to fix the errors that I find there because of another problem that I'm experiencing (having to do with autofs and sshfs which is not related I don't think) and I find some items that from what I can gather are related to timing issues and dbus.  I get the following errors:

> Aug 21 09:35:14 Tan dbus[1094]: [system] Failed to activate service 'org.freedesktop.ConsoleKit': timed out
Aug 21 09:35:14 Tan rtkit-daemon[1709]: Warning: PolicyKit call failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I found some related bug reports that indicate that possibly the dbus is not ready and that the order of loading should be changed but I am not sure how to change the ordering.  Any help would be appreciated.  Thanks.

---

