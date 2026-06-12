---
title: "Disabling Plasma Shortcuts"
date: 2015-06-16
forum: Desktop Environments
---

### Post by john412 on 2015-06-16
I am working on locking down desktop settings for a limited user account. It looks like I only have 1 area remaining to lock down and I cannot find anywhere to do so. I need to disable the Plasma shortcut keys, specifically all of the Alt+D,[X] short keys.

example: Alt+D,S will bring up the Desktop Settings dialog box

I have gone through all of the kiosk settings, the Menu Editor, every file in ~/.kde/, every single option I saw in Global Keyboard Shortcuts, Google and this forum. I would really like to do this the right way and not over ride the behavior by mapping them elsewhere. Please a couple of requests: 

1. Please do not mark this as a duplicate without providing a link to the forum post (see this happen a lot).
2. Please do not mark/dismiss this as a duplicate without verifying the details. I see a lot of posts marked as duplicates where the question is similar but not specifically answered in other posts (also see this happen a lot).
3. Please verify the setting is where you say it is before dismissively answering "it is in blah control" and not provide any specific details. I have looked through every one that I can find, either I have already missed it three times, or it is not actually there.
4. Please provide specific instructions. I am not an idiot. But, I am coming back to KDE after many years and the system has changed and has always been complex under the hood (IMO).

I hope I do not sound like an ass. I have just been working on this for 2 full days and I am already pulling out what little hair I have left. ;)

TIA!

---

### Post by john412 on 2015-06-16
I had to install kunbuntu-desktop to get the dialog boxes (from the cashew) to disable these shortcuts. We will not be installing it on the end user systems but will instead copy the config file changes in plasma-desktoprc. I believe these are the configuration options needed in case anyone else needs to do the same:

[Shortcuts]
lock widgets=none
manage activities=none

[Shortcuts-Applet]
configure=none
remove=none
run associated application=none

[Shortcuts-Containment]
add widgets=none
configure=none
next applet=none
previous applet=none
remove=none
run associated application=none

---

