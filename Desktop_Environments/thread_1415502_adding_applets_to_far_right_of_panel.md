---
title: "adding applets to far right of panel"
date: 2010-02-24
forum: Desktop Environments
---

### Post by miatawnt2b on 2010-02-24
currently I have the wireless, bluetooth and sound applets on teh far right of the panel (upper right corner) I can't seem to move them left to add another applet to the far right.  how do I move these things?

THanks
-J

---

### Post by stinkeye on 2010-02-25
Right click just to the left of those icons and click on about and if it says Notification Area,thats what you want to move.

---

### Post by Kakers on 2010-02-25
If you have selected Move make sure the 'Lock to Panel' option is uncheck.

If it is a case you want to have an added applet on the top panel that you want to drag it right past other applets, you have to uncheck the 'Lock to panel' option on the applets that you are going to move your desired applets past.

---

### Post by miatawnt2b on 2010-02-25
The issue is that the bluetooth networking and sound icons are at the far right, and they do not have a move or lock to panel option associated.  I can't add applets to teh right of them because there is nowhere to click on the panel, nor can I drag applets to the left of these over them.

What am I missing here?

-J

---

### Post by Kakers on 2010-02-25
Ah right so they are, but you can add an applet in the middle and the drag that applet to the right of those two icons provided that any applets between the one you want to move and the bluetooth / sound icons are not locked

---

### Post by stinkeye on 2010-02-25
Open configuration editor (gconf-editor in terminal) and go to
/apps/panel/global/locked_down
and make sure the panel is not locked down.

then go to
/apps/panel/applets/notification_area_screen0/locked
and untick locked

You should now be able to move other applets to the right of the notification area.

I created a new account so as to get the default set up
and it looks like this. Depending on your theme sometimes the bar on the left is not visible or am I missing something.
You cant move individual icons within the notification area, you can only move the entire applet. The icons are displayed in their startup order from right to left.

---

### Post by Kakers on 2010-02-25
You can drag into the notification area if you right click the separator bar, the one the red arrow is pointing to and unlocking that :D at least like you say.... as long as your theme allows it.

---

### Post by miatawnt2b on 2010-02-25
> **stinkeye said:**
> Open configuration editor (gconf-editor in terminal) and go to
/apps/panel/global/locked_down
and make sure the panel is not locked down.

then go to
/apps/panel/applets/notification_area_screen0/locked
and untick locked

You should now be able to move other applets to the right of the notification area.

I created a new account so as to get the default set up
and it looks like this. Depending on your theme sometimes the bar on the left is not visible or am I missing something.
You cant move individual icons within the notification area, you can only move the entire applet. The icons are displayed in their startup order from right to left.

AWESOME!  Thank You very much!
-J

---

