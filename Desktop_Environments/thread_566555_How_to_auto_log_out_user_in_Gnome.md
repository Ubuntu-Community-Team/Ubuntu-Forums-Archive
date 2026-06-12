---
title: "How to auto log out user in Gnome?"
date: 2007-10-03
forum: Desktop Environments
---

### Post by lancest on 2007-10-03
I have some Ubuntu pc's set up at a school. I want them to auto log out to (to login screen) when the user is away for 15 minutes. How to do this in Gnome?

---

### Post by reckless2k2 on 2007-10-03
is the screen lock feature an option or are you looking specifically for auto-logout? the concern would be unsaved work would be lost and such. the screen lock will kick in upon screensaver start and it also gives you the option to log in as another user as well.

---

### Post by lancest on 2007-10-03
I am looking for a complete restart of X back to the login screen. The reason for this is that  I am having some problems with keeping custom color settings on a few (Nvidia) pc's. [COLOR="Red"]Once the PC goes idle (power management & screen saver) then Nvidia custom color settings are lost[/COLOR]. Washed out Gnome! Nobody has answered that question in this forum. So I figured a restart of X windows would be best to prevent this problem -short of a better answer.  (I saw this problem in Feisty now seeing it in Gutsy)

---

### Post by lancest on 2007-10-08
After some testing the root of my issue turns out to be the [SIZE="4"]Gnome screensaver[/SIZE]. 
On certain PC's Nvidia color settings are lost when screen saver starts. This is in random computers in my experience. 
Talked about here:
[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/147905](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/147905)
Problem solved- it's ok for the display to sleep but [SIZE="5"]deactivate screensaver[/SIZE] itself.

---

