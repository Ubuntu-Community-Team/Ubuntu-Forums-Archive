---
title: "some update borked graphics"
date: 2013-09-13
forum: Desktop Environments
---

### Post by geoffcahoon on 2013-09-13
A recent update has  created a big problem. I think it has only been about 2 weeks. I don't remember what the candidates would be. But now windows and dialogs, any box drawn by the window manager, and even some items that don't look like there are frames or windows there, will suddenly distort on the left side. The title bar will twist down on the left behind the window, all the text inside dialogs will twist down to the left and magnify. It will sometimes be triggered by a mouse over, but not always, and often without. Youtube flash videos will flicker with random distortions and boxes like this, and sometimes the whole page will go nuts with all the elements redrawing incorrectly.  It does seem to relate to things with text. This text window is doing odd things as I write this, suddenly redrawing the characters in a distorted order, than flickering back to normal. It is not specific to an application. It happens in a browser more often, but also in any app with a title bar and other normal drawn elements. The launcher bar has been affected also. It doesn't make the computer completely unusable, but it is both annoying and alarming. I am running Ubuntu 12.04, have an Nvidia 9500 GT card running the nvidia driver, version 304.88, and my computer has an AMD 9650 quad core chip with 4 gigs of ram. I am using regular Unity desktop. It has been wonderfully solid before this. I tried re-installing compiz, and rebuilding the nvidia kernel driver. Before I give up and make a fresh install of 13.04, I thought I would ask and see if anyone can help. I googled and checked launchpad, but couldn't find anything that sounded similar. 

Geoff

---

### Post by buzzingrobot on 2013-09-13
Did these symptoms appear immediately after your last update two weeks ago?  It is extremely unlikely for the impact of an update to take two weeks to appear.

Have you installed anything else or altered your configuration since that update two weeks ago>

Sad to say, hardware malfunction might account for that odd behavior.

Burn a LiveCD of Ubuntu or another distribution, boot it in live mode and see if the symptoms replicate.

---

### Post by geoffcahoon on 2013-09-15
The recent update with x11 files built against an SRUed (?) core fixed it. 

The problem showed up immediately with the earlier update. I just tried to live with it, and hadn't payed enough attention to the updates to have any idea what it was. I tried 13.04, hoping that would be solid, but it too showed a little bit of the behavior. And it was running the new open source driver, not an nvidia binary. Maybe I should reboot that one and see if there is an update for it too. 

Thanks buzz for responding. It's nice when someone helps. 

Don't know why it says my join date was September. I have been a member of the forums since about 2005 or something. The new login I guess.

---

### Post by geoffcahoon on 2013-09-15
spoke too early. It was clean for awhile. But now glitches are back. They started first in the little hi-lite boxes when you mouse over a link, then window title bars. No more flashing glitches when youtube flash videos were playing, but the player screen will occasionally flicker green when mousing between links. I will boot a puppy and see if it is clean. it will be running in a vesa mode so shouldn't be any issues there. I probably have an old ubuntu live cd too.

---

