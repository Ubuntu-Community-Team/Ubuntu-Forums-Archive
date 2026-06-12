---
title: "Evolution cannot add/edit events in google calendar"
date: 2016-06-13
forum: Desktop Environments
---

### Post by sms3 on 2016-06-13
Hi all,

using 16.04 ubuntu, added google calendar to evolution via gnome / unity accounts. Email works well, but when I tried to add an appointment to my google calendar the event cannot be edited and the error message in the event window says "Event cannot be edited, because the selected calendar is read only". 

Any ideas how to access google calendar read-write in Evolution?

Thanks!

SMS

---

### Post by X-RED_Tech on 2016-06-13
I think you need to give permission to apps at your Google account.

---

### Post by sms3 on 2016-06-14
Hi,

Thanks, did that. Just found out that on a similar install on another laptop (same Ubuntu 16.04 fresh install) it works. Drives me crazy why it works read/write on one laptop and only read on the other.

---

### Post by sms3 on 2016-06-20
After removing all settings and reinstalling it still did not work. I then found that I come to a different GUI when accessing Gnome Online Accounts directly from Evolution or from system settings. So in both (similar looking, but still not the same) setting screens I removed gmail, and then added it back in the system wide settings. After logging out and in again it started to work. So this is resolved, however it is not clear to me what exactly caused that issue.

---

### Post by X-RED_Tech on 2016-06-20
If you installed the Gnome desktop on top of the vanilla Ubuntu or Unity in Ubuntu-GNOME then it usually resulted in two different online accounts with different but very similar names and both appearing with the same icon in system settings. It was a long time ago I noticed that (I just stick with Unity this days) so I don't know if that still the case.

---

### Post by sms3 on 2016-06-22
Oh gosh, it came back. After working for one day today the calendar is locked again. don't get it. 

@X-RED_Tech: Have not installed anything on top, just using out of the box Unity.

---

