---
title: "Upgrade originated desktop environment that only has one application"
date: 2018-07-30
forum: Desktop Environments
---

### Post by mehrlicht2 on 2018-07-30
HI.

I upgraded to 18.04 LTS. Had some problems at the end and now at the login screen I can only log into two accounts with the same name and that enter directly into KODI. When I exit Kodi I go back to the login screen... I cannot do anything else (except open terminal).

How can I fix it? 

Thanks

---

### Post by deadflowr on 2018-07-30
Yep, kodi has it's own session.
You can switch session at login,
depending on display manager if using Ubuntu's new display manager, gdm. then when you click to enter your password, a cog will show under the password field. (next to the sign in button)
click on the cog to expand the selection field and choose Ubuntu.
The click to close and enter your password.

If still using Ubuntu older display manager, lightdm, then there should be a badge right next to the user name in the login screen.
Click ( or if clicking isn't working press TAB and space) and select again select the option Ubuntu, and click the arrow at the left to close.
Then enter the password.

Both should set the main Ubuntu desktop as the session to start.

---

### Post by mehrlicht2 on 2018-07-31
It only shows two sessions/desktop environments and both are KODi... (Old display manager).
 :(


> **deadflowr said:**
> Yep, kodi has it's own session.
You can switch session at login,
depending on display manager if using Ubuntu's new display manager, gdm. then when you click to enter your password, a cog will show under the password field. (next to the sign in button)
click on the cog to expand the selection field and choose Ubuntu.
The click to close and enter your password.

If still using Ubuntu older display manager, lightdm, then there should be a badge right next to the user name in the login screen.
Click ( or if clicking isn't working press TAB and space) and select again select the option Ubuntu, and click the arrow at the left to close.
Then enter the password.

Both should set the main Ubuntu desktop as the session to start.

---

### Post by deadflowr on 2018-07-31
Then install Ubuntu's desktop then
```
sudo apt update
sudo apt install ubuntu-desktop^
```
It might ask to set the display manager, as 18.04 uses gdm as the default.
Either display manager runs fine, so your choice.

Since kodi does not have a terminal (me thinks), when you get to the login screen, instead of entering your password, press ctrl + alt + F1 (or F2-6)
to get a console.
Login there and run the above commands.
When done, you can reboot from there by running sudo reboot.

---

