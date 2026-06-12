---
title: "switch user fails ... sometimes freezes"
date: 2015-03-27
forum: Desktop Environments
---

### Post by Skaperen on 2015-03-27
i have many userids/usernames set up to autologin with no password.  i can thus select another username from the upper-right gear drop-down menu and it goes right to it ... usually ... but sometimes it prompts for a password.  then i can select another user and skip that prompt. later i can get to that user ok. sometimes it prompts often. even less often this switch does not go all the way and the desktop stops taking input. a quick press of the power button gets a choice of shutdown/reboot/suspend options but they don't work.  the only way out that i have found is to hold the power button to really power off.  then i can power back up and the system comes back up.

**anyone seen this or know what could be causing it?**  i upgrade regularly and this started happening after an upgrade a couple months ago.

---

### Post by dino99 on 2015-03-27
i can think about 1 reason when for example there is still some jobs running

---

### Post by Skaperen on 2015-03-28
i don't see a reason in there that switching to a user that was set up to auto-login would prompt for a password when it should just login or switch.  seems like a Unity bug to me.

---

### Post by Skaperen on 2015-03-29
> **9d9 said:**
> i can think about 1 reason when for example there is still some jobs running

what kind of jobs do you mean?

---

### Post by Skaperen on 2015-03-29
when my laptop is slow i can ***see*** what Unity is doing for a _user switch_.  it is locking the current user and some how doing a login on the target user.  i see the screen-lock display first for the user i am switching away from (presumably locking it) then the screen-lock display of the user i am switching to (presumably the VT switch to the target X server originally locked when i left it) then some how it unlocks it.   **but it is still unclear what is failing when it fails** ... whether doing the unlock action does not happen or if the screen lock thinks the user needs a password (this happens for users set to need no PW to login).  this only happens sometimes ... like a timing error (sending the unlock action before the VT switch is complete).  it does happen about the same when the machine is busy.

looks like a lot of bugs in **unity-panel-service --lockscreen-mode**

---

### Post by Skaperen on 2015-03-30
this *only happens* when switching **to** _a user that is already logged in_.  it appears to be a bug getting the process ```
/usr/lib/unity/unity-panel-service --lockscreen-mode
``` to **unlock**. for users that are set up as [U]login without a password

[/U]*edit* ... more observations:

this *only* happens when the target user was _rather recently_ (i do not, yet, know the exact timing, but _it is on the order of a few minutes_) locked.  users that i switched *away from* _quite a while ago_ **do not encounter this problem**.

---

### Post by Buntu Bunny on 2015-04-03
I am having the problem as well on Xubuntu 12.04. There are only two users on this computer, my husband and me. (He uses Classic DE) Sometimes when one or the other switches desktops everything freezes, *mostly* going from my desktop to his, but occasionally the other way. There is no pattern for this so it seems random. Neither of us locks our screens/desktops.

---

