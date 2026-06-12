---
title: "How to make settings available to all the users in KDE4?"
date: 2010-05-05
forum: Desktop Environments
---

### Post by wrix on 2010-05-05
Hello, I am looking for a way to make my setting available to all the users in the system in KDE4 (even to those users which I may create letter). Please help me in this regard, thanks in advance.

---

### Post by Zorael on 2010-05-05
One thing you could do is to set the settings as you like it, and then copy the relevant files from the **~/.kde** directory to **/etc/skel/**. Files and directories in there are copied upon creation of a new user, into its new home. But this would only affect new users and not currently existing ones. Not sure of a solution that would suit both.

**~/.kde/share/config/*<directories>*** for application settings, and **~/.kde/share/apps/*<directories>*** for application resources. Obviously you can also copy other directories, like **~/.config/chromium** for Chromium settings/resources.

---

