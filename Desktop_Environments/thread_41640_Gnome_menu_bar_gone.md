---
title: "Gnome menu bar gone"
date: 2005-06-14
forum: Desktop Environments
---

### Post by JeffG on 2005-06-14
I created a second (non priv) user for my system, and the menu bar at the top of his screen has suddenly disappeared. I tried 'killall gnome-panel' as suggested in another post, but that didn't work.

The menu bar disappeared mid-session, and doesn't come back when I log into his account again. The only way to get out of this appears to hit the button on the box - the only thing I can do is create a terminal from the desktop right-click menu and it won't let me logout from there. Before this happened, he had run several sessions on this account.

Help please! (My own [primary] account is OK).

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=JeffG]I created a second (non priv) user for my system, and the menu bar at the top of his screen has suddenly disappeared. I tried 'killall gnome-panel' as suggested in another post, but that didn't work.

The menu bar disappeared mid-session, and doesn't come back when I log into his account again. The only way to get out of this appears to hit the button on the box - the only thing I can do is create a terminal from the desktop right-click menu and it won't let me logout from there. Before this happened, he had run several sessions on this account.

Help please! (My own [primary] account is OK).[/QUOTE]
 1. You can logout form terminal by typing 
gnome-session-save --kill
An emergency (but less so than hitting the power button on the box) way of loggin out is hitting crl-alt-backspace. This kills X server, which then reatsrts, bringign you to login screen again. 

2. Try removing user's ~/.gnome and ~/.gnome2 directories (from text console, obtainable by ctrl-alt-F1; use alt-F7 to get back to login screen). This removes all Gnome customization - including panels - so GNOME will start with default configuration again.

---

### Post by JeffG on 2005-06-14
Thanks for the tips. There was no .gnome directory, so I deleted all of .gnome2 and restarted - still no top menu. .gnome2 was re-created, but still no .gnome. (My own home directory does have .gnome and .gnome2).

Alt-F1 brings up the expanded menu, so at least he can do something, but I'd really like to get the menu bar back!

I messed with the text console - at one point alt-F7 just gave me a blank screen with a cursor in the top left corner. Why was this?

thanks so far,
Jeff.

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=JeffG]Thanks for the tips. There was no .gnome directory, so I deleted all of .gnome2 and restarted - still no top menu. .gnome2 was re-created, but still no .gnome. (My own home directory does have .gnome and .gnome2).

Alt-F1 brings up the expanded menu, so at least he can do something, but I'd really like to get the menu bar back!

I messed with the text console - at one point alt-F7 just gave me a blank screen with a cursor in the top left corner. Why was this?

thanks so far,
Jeff.[/QUOTE]
 you should also delete 
.gconf  
.gconfd 
.gnome2_private

Sorry, I forgot about them. 

As for blank screen with a cursor in the top left corner - it means that X server couldn't start.

---

### Post by JeffG on 2005-06-14
Many thanks - all fixed now. :smile:

---

