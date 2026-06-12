---
title: "Moved to 8.10, Firefox menus slow with Cygwin X"
date: 2009-01-14
forum: General Help
---

### Post by sorceror on 2009-01-14
I have an Ubuntu box (fairly anemic, i810 chipset, P3-750MHz, 384MB RAM) next to my Windows XP box at work. I usually use the Ubuntu box as a server - I ssh in, without logging in at the desktop. (100BT network, not gigabit.)

I set the DISPLAY to my XP box and run the Cygwin X server on the XP machine. (Note: not X tunneled through ssh, but direct network connection.) I wouldn't dare surf the net with Windows, so I run Firefox on the Ubu box and display it on the XP box. Performance isn't ultra-fast, but I don't hit YouTube at work so it's been more than acceptable until now.

Just last week I upgraded to 8.10, and things work... but bringing up menus or the first keystrokes into a text field are incredibly slow. Doing a right-click on a hyperlink takes seven seconds to bring up the menu. Everything else (page renders, tab switching, etc.) seems to run at normal speed. On 8.04, there was little if any perceptible delay in bringing up menus.

I've tried disabling all Firefox extensions with no effect. Logging directly into the Ubuntu box and using Firefox with the i810 graphics does not show this problem - menus come up at the speed I'm accustomed to.

The only other X program I use, Jpilot, does not show this behavior under Cygwin/X. It seems as responsive as before. My Cygwin install has not changed. Does anyone have any hints or suggestions for what I can do to fix this?

---

### Post by sorceror on 2009-01-14
I just checked with Xming, another X server for Windows. Same issue, it seems to be related to Firefox on a remote X connection. I'm going to go run a test with a Solaris box next.

---

