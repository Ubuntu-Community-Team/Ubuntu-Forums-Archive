---
title: "ScreensaverBug"
date: 2006-08-06
forum: Desktop Environments
---

### Post by 1Paul on 2006-08-06
When I was browsing the screensavers to select one, one of them was bugged. My ubuntu system hang and I had to restart the comp. Now, when I try to select a new screensaver the buggy one is the one selected so it always crashes when I enter the screensaver menu. It also crashes when im idle and the screensaver is activated.

Im new, so I dont know how to get around this. Help is needed:)

And btw, is there any "Ctrl+Alt+Delete" fuction on ubuntu?

Thanks!

---

### Post by mgmiller on 2006-08-06
You can try running System > Administration > Synaptic Package manager.  Then do a search for gnome-screensaver.  Right click it and then left click mark for reinstallation.  Next, click apply at the top of the page and see if that fixes it.

In answer to your last question, the closest is ctrl+alt+backspace  This will restart your x session and should bring you back to the login screen.  You rarely have to reboot the whole machine, usually it's just x that gets a bit confused.

One other thing I can think of is that you are not using the accelerated drivers for your video card.  If you have selected a screen saver that requires openGL acceleration, that might be why you are hanging.  There are many threads on installing accelerated drivers for nvidia and ati cards.  You didn't say which one you have.  If it's nvidia or ati, easyubuntu might be the easiest way for you.  Search for this in the forum.

"teach a man to fish...yadda yadda yadda"

Hope this helps.

---

