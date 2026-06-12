---
title: "Screensaver not locking screen"
date: 2006-06-20
forum: Desktop Environments
---

### Post by pkkid on 2006-06-20
Was wondering if anyone else is having this issue.

When I goto lock my screen the screensaver comes up, but upon moving the mouse it never asks for my password to get back into the desktop.  This is an issue as it is my work computer.

In Breezy Badger the screensaver locked up fine, but in Draper Drake it appears changes have been made to the screensaver functionality a bit, which might have been the cause of the issue.

Anyone know any fixes?

---

### Post by Shimmy on 2006-06-20
You might need to check the "Lock screen when screensaver is active" in System->Preferences->screensaver

But it should work without it since the buttons says "Lock screen".

I have the checkbox checked and my lock screen works as it should.

---

### Post by pkkid on 2006-06-20
Its strange, I do have this checked.  I also unchecked it, left the screen and checked it again just to make sure the setting was made, but it did not change.  When I goto lock the screen, a simple move of the mouse beings me back to the desktop.

---

### Post by Shimmy on 2006-06-20
[QUOTE=pkkid]Its strange, I do have this checked.  I also unchecked it, left the screen and checked it again just to make sure the setting was made, but it did not change.  When I goto lock the screen, a simple move of the mouse beings me back to the desktop.[/QUOTE]

Wierd, do you have "Enable automatic login" or similar enabled in System->Administration->Login Window->Security? I'dont know but this might override the screen lock feature..

---

### Post by pkkid on 2006-06-20
No it is not enabled, but it does make sense to check that.  Just a crazy install I suppose. :)

Any other ideas?

---

### Post by wiresquire on 2006-07-10
I just had this happen, too. Just move the mouse, and desktop is accessed  with no prompt for password.

Funny enough, After I wasn't prompted for password, I ran a couple of little tests:
- just till screensaver starts: prompts for password
- wait till screensaver is 'blanked' by Power Mgmt settings (DPMS I guess): prompts for password.

Hrmmm. So now it seems to work.

I'm wondering if it has something to do with the Power Management and setting the screen to blank after X minutes? Or maybe something else like sleep unsetting the screensaver.

My last scenario is letting it straight to DPMS setting screen off after initial login. That will have to wait for another time...

ws

---

