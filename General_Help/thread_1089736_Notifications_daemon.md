---
title: "Notifications daemon"
date: 2009-03-07
forum: General Help
---

### Post by houcem on 2009-03-07
Can you tell me what is the daemon responsible of the basic notifications in Ubuntu8.10 and how to configure it. I've accidentally disabled the notifications about the availability of wireless networks by clicking "do not show me this again" button in the popup and I don't know how to get it back.

---

### Post by jpeddicord on 2009-03-07
You can't directly configure the notification daemon, but the issue you are describing lies in network manager. It's an easy tweak, but you'll need to open the configuration editor: hit Alt+F2 and type **gconf-editor** to open it.

Then, navigate the folders on the left side to /apps/nm-applet. Then, on the right side, uncheck "disable-connected-notifications." The next time you sign in you should see that they are being displayed again.

---

### Post by houcem on 2009-03-07
Thanks a lot. I can also see a configuration option to the notification daemon "popup location" can customize it to be displayed above of the panel?  By the way what does Jaunty look like?

---

### Post by jpeddicord on 2009-03-07
> **houcem said:**
> Thanks a lot. I can also see a configuration option to the notification daemon "popup location" can customize it to be displayed above of the panel?  By the way what does Jaunty look like?

The popup location options have been removed as notify-osd has replaced notification-daemon. For information on that, see this: [http://www.markshuttleworth.com/archives/265](http://www.markshuttleworth.com/archives/265)

---

