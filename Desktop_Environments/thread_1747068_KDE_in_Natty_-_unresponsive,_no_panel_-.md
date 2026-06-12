---
title: "KDE in Natty - unresponsive, no panel -"
date: 2011-05-02
forum: Desktop Environments
---

### Post by a.m.wink on 2011-05-02
Dear all,

After a system notification I upgraded my (K)ubuntu from Maverick to Natty. Everything went seamlessly and in the background (some funny behaviour eg from acroread, as it was being upgraded I guess, as it went away again). All fine.

After the reboot a new KDE screen (& splash screen) came up, with mouse pointer, and with Skype starting automatically, but that was it. No response to keyboard & mouse, no panel or taskbar. The only thing that worked (and which eventually I used) was the exit dialog after pressing the power key.

Is this a bug that more people have seen? I tried moving my home dir and logging back in with an empty directory (so KDE could initialise empty) but that gave a blank (black) screen!

I have an ATI radeon and a dual monitor, but they both work so that does not seem to be the problem. The desktop backgrounds are there, they're just empty...

Any ideas?

Thx
AM

[SOLUTION]
My colleague's still working Maverick used the plasma desktop environment. Looked up which plasma-related packages were installed. It turned out plasma-desktop was there but not kde-plasma-desktop. Installed kde-plasma-desktop and now it works again!
Not sure why it was not installed automatically in the upgrade if it is a required package?

---

### Post by el_koraco on 2011-05-02
Some guys updated the system and kubuntu-desktop wasn't even installed. Apt has been having something against KDE in this cycle, a few times it removed people's dekstop during the dev phase. It probably has to do with the overload on servers, and packages not arriving in time. Another example as to why it's best to give it a few weeks after the release.

---

### Post by a.m.wink on 2011-05-03
You may have a point :). Then again, I just clicked 'update' when the graphics software management tool suggested to update. Maybe that suggestion should appear a few weeks later? I was updating not installing, so if the update process could pick up kde-plasma-desktop that would probably solve the problem for others as well. Will let the experts know :)

AM

---

### Post by nortexoid on 2011-05-05
I've had this problem occur A LOT in the past (having the backports repo enabled) and became a pro at reinstalling the necessary packages from a networking prompt. This time I think I've done things a bit more intelligently. I waited a few days to update (which didn't help), updated BUT DIDN'T RESTART!, and now noticed that kde-plasma-desktop is not even installed. So I'm installing it now. It appears all the other necessary packages are installed, so once I double check I'll restart and hope everything's ok.

This is a stable release and I don't have enabled any crazy repos, so it's surprising to me that such a serious issue is still unresolved.

---

### Post by a.m.wink on 2011-06-03
Found out that the solution above, which worked on my office computer, did not work at home :(

AMW

---

