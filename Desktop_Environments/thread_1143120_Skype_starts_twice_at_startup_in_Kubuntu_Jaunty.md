---
title: "Skype starts twice at startup in Kubuntu Jaunty"
date: 2009-04-29
forum: Desktop Environments
---

### Post by The_Fallen on 2009-04-29
Hi,

since I updated my Kubuntu to Jaunty, Skype always starts twice after login, even if I shut Kubuntu down before with only one running. Any idea why this could happen? There is no link in the Autostart directory or anything like that...

Cheers

---

### Post by Zorael on 2009-04-29
What happens if you set KDE to start with an empty session? Does one (Skype) start then, anyway? System settings -> Sessions.

---

### Post by The_Fallen on 2009-04-30
If I do that, Skype only starts up once (which it shouldn't, right?). So there must be any other mechanism in place to start a second instance. Any idea?

---

### Post by Zorael on 2009-04-30
I'd check ~/.kde/Autostart, /usr/share/autostart (with subdirectories) and /etc/xdg/autostart for any script that could be starting it. Oh, and the autostart section in System Settings.

---

### Post by The_Fallen on 2009-04-30
Ha, it was Autostart in System Settings. I haven't seen that one before. Thanks a lot! :-)

---

