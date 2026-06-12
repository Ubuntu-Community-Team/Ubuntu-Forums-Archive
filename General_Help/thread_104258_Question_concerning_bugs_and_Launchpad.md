---
title: "Question concerning bugs and Launchpad"
date: 2005-12-15
forum: General Help
---

### Post by halfvolle melk on 2005-12-15
Hello everyone!

Doing some stuff in Nautilus I encountered something that might be considered as a bug, but I'm not sure. Then I found the request to first check it here or the other two alternatives. Here it is.

I tried to copy files from a badly scratched CD-R which you can also see through fairly well so no wonder it can't be read entirely or at all. But the 5th file, the Nautilus copy dialogue got stuck (no crash) at copying/reading the file. It didn't respond to 'cancel', the top-right "X" or "X close" from the toolbar and bravely kept om trying to copy this file. Twice I've tried this, with the same result. The first time a reboot got rid of the persistent Nautilus (obviously).

The second time "kill -9 [pid]" did. And then, two things:
- Nautilus woudn't be started anew with the GUI ("starting file browser" in the toolbar only to disapear after a few seconds), it would after "nautilus &" in a terminal and after that works from the GUI also.
-After killing I got a pop-up telling me that Nautilus had unexpectedly crashed asking me to either close the pop-up or to report to the development team* or do something else. The Windows user still lurking in the background swiftly found the ok/close/go away-button before I could consider the options. I could easily recreate the incident and file the error report* if that's any help.

I couldn't find it on
[https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=nautilus&search=Search&orderby=-priority%2C-severity](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=nautilus&search=Search&orderby=-priority%2C-severity)
but I'm sorry if this is already a known bug and wasted your time and sorry it took me so many words ("but I lack the time to make it short" - Blaise Pascal :)). Just trying to do my bit.

If not, what to file, how to file it and should I recreate the incident*?

Cheers,
Halfvolle Melk

---

