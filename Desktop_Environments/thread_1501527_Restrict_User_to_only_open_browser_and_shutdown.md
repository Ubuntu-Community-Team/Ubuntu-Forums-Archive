---
title: "Restrict User to only open browser and shutdown"
date: 2010-06-04
forum: Desktop Environments
---

### Post by mydigia on 2010-06-04
Hi,

We just installed Ubuntu latest version (10.04), and what we are willing to do, is restrict the main computer user (none-administrator) to be only able to use web browser (Mozilla Firefox or some other) and that is it. Not allowed to do anything else, apart from this, and shutting down the station.


Can this happen?
How and where should we apply this type of limitation on a user?


Thanks,
Ali.

---

### Post by germanix on 2010-06-06
Go in the menu (top left of the desktop) where it says Applications-Places-System to the System Menu. Click on it and the in the drop-down window that opens look for "users and groups" and click it once. A window will open called "User Settings" If the User that you want to have restricted access is already there on the left side of the window (you will see his user name), then click on his name to highlight him/her. (If not you first have to add him/her by clicking "ADD" and then adding this user) On the right side of the window you will see the account type for this user, probably set as "custom" or as "desktop user". If he/she is set to "custom" click change behind the account type and change it on the next window to "desktop user". Close this window and now go back to the first window "user settings" and click the "advanced settings" button. A new window will now open and there you can un-check all the boxes that you do not want this user to use and only check the Internet box (either Lan or Wlan) or both depending how your Internet connection works. (with or without cable connection) Then close this window and restart the computer. The next time this user logs on he/she will only be able to use the Internet or those boxes that you checked. (Whilst doing all of the above you will be asked to enter to password in order to do the changes - do this)
Hope this solves your problem.
Note: It may be that after you changed the user setting from "custom" to "desktop user" that the advanced setting box may not appear. If this is the case then change the setting of the user back to "custom" and then change the boxes under "advanced setting".
I am the only user on my computer so I have not done this myself so I do not know if this box under the advanced settings appear when the user is only a "desktop user"

---

### Post by mydigia on 2010-06-07
Hi,

Many thanks for your reply.

I am doing as so, but I don't know if this way the user will be limited to only what I need.

For instance, I do not want any other access, even changing the time, background, nothing. Just opening firefox and browsing, and shutting down...

Will this way be doing what i need?

Thanks for your time,
Ali.

---

### Post by estyles on 2010-06-07
I don't think that's going to do what you want.  I suspect that the answer will have something to do with the user shell and init scripts.  You might search for linux restricted shell...

I was doing some research on this to try and help answer your question, and I'm kind of interested in it myself, but I wasn't able to find a simple answer.  You're probably going to want to do something like restrict them from running any programs and have firefox launched when they login, and have it log them out when they close firefox. (which should be possible with like an .xinitrc or .xsession file...)

If you remove the gnome panels for that user, that will probably be part of the battle...

---

### Post by rizzeh on 2010-06-07
might be worth looking at ltsp solution as it sounds like a inet cafe kinda thing.

[http://www.ltsp.org/](http://www.ltsp.org/)
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

