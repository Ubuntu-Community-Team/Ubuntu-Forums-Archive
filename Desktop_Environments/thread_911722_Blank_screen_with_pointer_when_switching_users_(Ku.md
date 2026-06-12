---
title: "Blank screen with pointer when switching users (Kubuntu Hardy)"
date: 2008-09-05
forum: Desktop Environments
---

### Post by chhamilton on 2008-09-05
I'm experiencing what appears to be a similar problem that others have discussed (white screen or blank screen with text cursor) when launching multiple simultaneous X sessions.

Here is what is happening:

(1) Login as user A (on terminal 7)
(2) Select Switch User -> Start New Session
(3) Login as user B (ends up on terminal 9, as terminal 8 is a text console and appears to be full of startup/boot related messages)
(4) Switch back to user A's session with Ctrl-Alt-F7.

After (4), the screen is completely black with a normal X mouse cursor.  If I move the cursor around, it will change shape corresponding to the shape it should take given the application under the cursor in that area (for example a text cursor over a Konsole app, or a resize cursor when over the corner of a window).  The X session is completely functional, it's just that *none* of the desktop gets drawn except for the cursor.

I can switch back to user B's session (Ctrl-Alt-F9), and everything draws as it should.

Here's the weird bit: if I run 'xrandr' from user A's session, then the screen will redraw and all is normal.  However, now when I go back to user B's session, it's *his* session that is black with a mouse cursor.  Running 'xrandr' from that session makes X start drawing itself once again, and pushes the problem back to the other user.

As a current workaround, I've bound a hotkey to run 'xrandr' so I can always force a 'refresh' so to speak.  A better 'workaround' would be for xrandr to run automatically whenever switching to a given session.  Are there any xevents fired off when an Xserver is given ownership of the screen, or any scripts run when doing session switches?

Ideally, I'd love it if somebody could tell me what is *actually* going on, and offer up a proper fix. Ideas?

I'm running Kubuntu Hardy (8.04) with KDE 3.5 on a Thinkpad X60t.

Regards,

Chris

---

### Post by chhamilton on 2008-09-08
Bump!

Nobody else is seeing such an issue?

Does anybody know of any way to ensure that a script is run everytime the session attached to the screen is changed?

---

### Post by chhamilton on 2008-09-08
After more tinkering, I should report that this only happens with the "intel" driver.  If I use the i810 driver (with the 915resolution package to make it properly detect the 1400x1050 resolution), then user switching between X sessions works just fine.  I need the "intel" driver for rotation and external monitor support, however.

---

### Post by chhamilton on 2008-09-08
Alright... so I can't seem to find anything out there that talks about solving this bug, although there are various cryptic references to similar issues.

As a workaround, I've created a little 'monitorvt' daemon that simply monitors the system for virtual terminal changes.  When it detects that the system has changed to a terminal on which an X session is running, it 'attaches' to that X session (sets up XAUTHORITY and DISPLAY), and runs 'xrandr' from that context.  This gives X the kick in the butt it needs to properly display the screen.  I've added this as a system service, and this takes care of the issue for me.  I've attached my source code along with a little installation script if anybody else wants to use this until a *proper* fix comes about.

---

