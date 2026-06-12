---
title: "Keyboard and shortcuts Problem"
date: 2005-09-01
forum: Desktop Environments
---

### Post by steve0921 on 2005-09-01
I'm having a problem that window management shortcuts like Alt-Tab and Alt-F4 aren't working. I've checked both *System > Preferences > Keyboard* and *System > Preferences > Keyboard Shortcuts* and everything appears to be configured properly.

It also appears that I can't type in the firefox, mozilla, or epiphany location/search bars or in web pages. My keyboard operates perfectly in Gedit though and outside the browsers I have found no other problems (except for window shortcuts).

To further confuse me, sometimes when I reboot the problem will disappear for a bit, but eventually starts again.

I am new to Ubuntu and GNOME and have no idea where to look for the problem. Can somebody point me in the right direction?

---

### Post by sto6ma9ch on 2005-09-01
Hmmm . . . have you tried another keyboard?

---

### Post by steve0921 on 2005-09-01
Actually I'm using a laptop and can't figure out how to get a second keyboard set up.

Also, the fact that the keyboard works in Gedit (where I'm composing this post) and that it has worked briefly in all of GNOME leads me to believe that it isn't the problem.

I'm so baffled at this point I think I might move to another distro and hope for the best...

---

### Post by emperor on 2005-09-15
[QUOTE=steve0921]

It also appears that I can't type in the firefox, mozilla, or epiphany location/search bars or in web pages. My keyboard operates perfectly in Gedit though and outside the browsers I have found no other problems (except for window shortcuts).

To further confuse me, sometimes when I reboot the problem will disappear for a bit, but eventually starts again.
[/QUOTE]

I am experiencing a similar problem in the URL and search entry box in Firefox on my Dell i9300 laptop. Sometimes the keyboard quits responding. After typing one character, the cursor focus moves again then when I put the focus back with the mouse, the keyboard does not work in firefox. However, the keyboard works in other apps OK. I am using Firefox 1.06 from backports.

---

### Post by steve0921 on 2005-09-18
My problem was a result of a sticky windows key on my keyboard. By default, the key doesn't do anything in ubuntu so this was hard to detect, but pressing the key a few times (and unsticking it) seems to clear everything up.

Don't know how much this will help.

---

### Post by emperor on 2005-09-18
The problem is not a stuck key on my laptop. Both Mozilla and Firefox 1.06 from backports exhibit this problem in the URL and search entry fields.

---

### Post by steve0921 on 2005-10-16
Gave up on Ubuntu for a while because of wifi problems, but back now.

If there happens to be anyone else has a stuck windows key, the problems I had seem to be related to the default mapping of win key to super. By changing the alt/win key behaviour in keyboard preferences > layout options my problem seems gone. At least in Breezy.

---

### Post by kxs on 2005-10-23
I also have problem with keyboard and shortcuts. I change Alt/Win behavior to "Meta (or Hyper) is mapped to the Win-keys.". Then I change for example my Home Folder shortcut to Win+h (<Mod4>h). The shortcut changes, but when I push Win and h nothing happens. It worked on Hoary, though.

---

