---
title: "Remote Desktop Fails for One Particular User"
date: 2012-01-25
forum: Desktop Environments
---

### Post by iposner on 2012-01-25
Running 11.10 patched up to date. When one particular user is logged on to the "target" computer and I try and connect remotely to the desktop from another computer, I get the message that the server has closed the connection. However when another user is logged on to the "target" computer, remote desktop works correctly.

First thing's first - I checked the Remote Desktop settings available through the GUI - and they're identical to those of user profiles that succeed.

So then I checked the group membership of the failing user - the user is in the Administrators group and I've been through all the other groups defined on the machine comparing the membership of users that succeed with remote desktop and comparing the membership against the user that fails. I can't find any differences.

If the group membership is the same, then there must either be a permissioning of some resource which is granted per-user to successfully connecting users and which is missing for this user. Or perhaps there's a config file/folder which exists for the others.

I really need help from someone that understands the vinagre server.

---

### Post by iposner on 2012-01-29
OK -- Here's some more info. I've discovered that for the failing user profile, the vino-server process isn't running, but when I log on as another user, it is.

So presumably the vino-server is getting started as part of the logon process. But where are services that start on logon set?

---

### Post by iposner on 2012-01-29
More info - I've just found out through looking through the vino-server change list that a patch was put in that **hides vino-server from the list of startup applications**.

That's a step forward as it now means that just because I can't see vino-server as a startup application under working profiles doesn't mean it isn't there.

So the question is, *where are the per-user startup applications stored on the filesystem?*

---

