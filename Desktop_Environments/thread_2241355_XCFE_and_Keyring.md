---
title: "XCFE and Keyring"
date: 2014-08-25
forum: Desktop Environments
---

### Post by gordon99 on 2014-08-25
I have been running Xubuntu 14.04 with XCFE desktop on a dual booted laptop for a few months. I am a slow learner when it comes to computer commands. 
i recently installed Evolution e-mail client and by and large it seems fine. However, one annoying feature is that, every time I log on to Evolution, I am required to enter my e-mail accounts' passwords in a Mail Authentication Request box. It even asks if I want to save the password in my Keyring, not that I have any knowledge of having this particular software. 
Though I do not particularly want to have the keyring facility it may be that until I set it up, in which to save my e-mail account passwords, I will be continually pestered to enter pws. to get access to my mail. Reading posts elsewhere, I get the impression there is a bug, or just something missing, which prevents Keyring installing in XCFE. Am I right to believe this and, if so, is there a known workaround that a slow learner might be able to follow?

---

### Post by gordon99 on 2014-08-25
Sorry, XCFE should be XFCE I believe.

---

### Post by fidelis2 on 2014-08-30
> **gordon99 said:**
> Though I do not particularly want to have the keyring facility it may be that until I set it up, in which to save my e-mail account passwords, I will be continually pestered to enter pws. to get access to my mail. Reading posts elsewhere, I get the impression there is a bug, or just something missing, which prevents Keyring installing in XCFE. Am I right to believe this and, if so, is there a known workaround that a slow learner might be able to follow?

When I installed Xubuntu 14.04 a few weeks ago, I had to manually install the (GNOME) keyring program in the Software-Centre by searching for its name which is "**seahorse**", and then install this one.
Worked fine, and since then the keyring which should be the same like you mean, runs fine on Xubuntu 14. To edit the keyring's preferences and keys, you can open it via its icon in the XFCE configuration center (sorry, don't know the English name for the latter one since I'm using a localised Xubuntu).

(Please also check in the XFCE configuration center, under the icon "sessions and starting" (or such), in the last tab named "experienced" (or so) that the 1st option named "Start GNOME runtime at startup time" is enabled. I think it is by default; but in case it's not, the GNOME keyring won't fully work as far as I know, which could be what you mentioned under bugs.)

Anyway, now the keyring successfully stores my passwords for shared network drives, for encrypted LUKS containers, for SSH keys, and so on. If you set the keyring's master-password (or how it's being named) to the same as your login password, the keyring is opened automatically when needed without asking for another password.

Or did I missunderstand your mentioned problem?

---

