---
title: "system tray icons detached on login"
date: 2008-07-31
forum: Desktop Environments
---

### Post by XMartinX on 2008-07-31
Hi. 

I am running kubuntu with kde 4.1.0 and plasma. I have compiz and emerald enabled also. I am running on a Dell Vostro 200 with the latest realtime kernel. When I boot up and login to kde4, things usually start up with no problems except that sometimes I get a "dcopserver not running" message. Doing a ps -e reveals that dcopserver is in fact running so maybe that's a timing issue or some other synchronisation problem. 
However, if I log out of kde and then log back in, some of the system-tray icons do not appear in the system tray but are detached and appear at the top-left corner of the desktop. Also they have corresponding entries in the task-bar (i.e. they appear as normal tasks with the icons in little mini windows). Clicking on the icons gives the same behaviour as if they were in the system-tray. KMail and KNetworkManager behave in this manner. The question is "why?".
Another problem I have is that rainlendar does not always start up. This again seems to be when logging out and then in again, although not every time. On this note, does anyone know of a plasma widget that mimicks rainlendar? I particularly use the todo list feature at the moment.

Thankyou for your patience in reading this and I look forward to any constructive help you may have.

---

### Post by XMartinX on 2008-07-31
I was running an old version of kmail (kde 3.5.9) ! I have kde 3.5.9 installed alongside kde 4.1 in case I need to fall back for recovery reasons. configured kmenu to use the new kmail and the problem disappeared.

---

