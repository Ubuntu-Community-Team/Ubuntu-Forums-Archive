---
title: "How to Fire up a custom notification"
date: 2012-06-14
forum: Desktop Environments
---

### Post by koohyar on 2012-06-14
I know this seems to belong to the scope of rudiments of doing geeky stuff (!) but what is the command/procedure to building a custom notification and have it shown where other notifications such as rhythmbox's changing tracks, etc. do?
I hope I've been clear enough :)
any help would be appreciated\.

---

### Post by zombifier25 on 2012-06-14
What you are looking for is the command notify-send.
For example:
```
notify-send "title here" "message here"
```
will send a very simple notification with the title "title here", and the body message "message here". You can read its man page for more advanced options, such as icons, urgency, etc.

---

### Post by koohyar on 2012-06-15
Thanks a lot :)
Just what I needed\.

---

