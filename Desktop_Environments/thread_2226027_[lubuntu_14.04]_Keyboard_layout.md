---
title: "[lubuntu 14.04] Keyboard layout"
date: 2014-05-24
forum: Desktop Environments
---

### Post by Kifferand on 2014-05-24
Hello,
I set my keyboard layout manager on french and russian (fr, ru). It has been quite unstable, yet usable, until I disconnected from the session. I could not enter my password to enter a new session, so I put the english layout, my password worked and:
1. All my system had turned to english!
2. there seems to be no way to use FR and RU again, the layout it is stuck on english (US). Note that the keyboard layout manager still shows french and russian with a Alt+Shift toggle...
 My /etc/default/keyboard looks well set:
 [HTML]
XKBMODEL="pc105"
XKBLAYOUT="fr, ru"
XKBVARIANT=""
XKBOPTIONS="grp:alt_shift_toggle,grp_led:scroll"[/HTML]
when I try:
[HTML] setxkbmap -option grp:alt_shift_toggle "fr,ru"[/HTML]
or:
[HTML]setxkbmap -layout "fr,ru" -option "grp:alt_shift_toggle"[/HTML]
I get this:
[HTML]Error loading new keyboard description[/HTML]
In /usr/share/X11/xkb/symbols, the fr and ru files are here, although I have made a few modifications to the fr keyboard.
Thank you in advance.

---

### Post by bapoumba on 2014-05-25
If you right click on the keyboard layout in the panel > Keyboard Layout handler Settings, can you choose your keyboard layout, or add or move up one already there ?

The system language is in Prefs > Language Support.

---

### Post by Kifferand on 2014-05-26
Thank you,
Everything was set as I wanted in the Keyboard Layout handler Settings.
I saw that I'm far from being the only one to have this problem. It is a [well-known bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1246272").
I decided to reinstall lubuntu and just set one quick time the keyboard layouts I need. Then I won't touch it until the bug is solved. It's been an hour and so far it works.

---

### Post by bapoumba on 2014-05-26
Question is now if the settings are going to stick after a session logout or a reboot.

---

### Post by Kifferand on 2014-05-26
I've been rebooting around five times today, and it still works. I'll write here if I encounter the same problem again.
Thanks !

---

### Post by bapoumba on 2014-05-26
Glad to know you fixed it so far. Please do not hesitate to post again.

---

### Post by welshmike on 2014-06-24
Yes. Seems to be a bug in the install.

I chose UK keyboard during Lubuntu 14.04 Install but I ended up with US keyboard.

I changed the the key layout of the keyboard as follows:

right mouse click on the US icon at the RHS of the taskbar
click "Keyboard Layout Handler" Settings
in the Keyboard Layout Handler window
click + Add   gb English(uk) then OK
click us then  click - Remove
click Close

---

### Post by psyduckbug on 2014-06-30
When i write:

setxkbmap -option grp:alt_shift_toggle "fr,ru"
in console return error

---

### Post by welshmike on 2014-06-30
Did you carry out the suggestion in my message #7 immediately before yours?
The changes for you should be:
click + Add re .... (or similar to add russian keyboard) then click OK
click fr then click - Remove

---

