---
title: "indicator applet notifier and new messages in evolution"
date: 2009-11-07
forum: Desktop Environments
---

### Post by claracc on 2009-11-07
Hallo, since i upgraded from jaunty to karmic last week, the indicator applet doesn't show new messages coming from evolution tray, it always shows (0) although I have unread messages and i have tick in evolution preferences "when a new message arrives : produce a sound, show a notification and indicate new messages in panel.

In jaunty it worked perfectly, indicating with a yellow star in the envelope icon of indicator applet the arrival of a new message.

I have seen in the forum that it is a general problem with evolution and indicator applet notifier, and that there is reported as a bug.

Investigating more, I have seen that there is a folder /usr/share/indicators/messages/applications/, where there is the file evolution, i open it and i find a line: /usr/share/applications/evolution-mail.desktop. I go to folder /usr/share/applications and there I have  two files with the name evolution-mail.desktop and evolution.desktop.

I don't know very much about programming, so perhaps I am saying silly things, but could someone see the evolution-mail.desktop in order to perform a workaround for this issue with indicator applet?, perhaps changing something in this configuration file?.

Any ideas are very welcome, thanks.

---

