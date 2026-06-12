---
title: "GNOME wont load"
date: 2006-01-23
forum: Desktop Environments
---

### Post by osisnie on 2006-01-23
Let me start off by saying that I am completely new to the world of linux. To be perfectly honest, the only reason I tried installing it at all was due to a quite large span of boredom. But that is not to say that I don't want to toy around with it. So here's whats happened.
----------------------------------------
First I tried with the live cd. Everything seemed to be going alright until it tried to load GNOME. It said "Ok" on that little splash screen thing but the screen went black and there was a frozen underscore in the top-left corner. No activity was going on.. no attempts to access the CD or hdd

So I went and burned a knoppix live cd. Apparently that uses KDE. It worked nearly flawlessly. The desktop refused to display over 640x480 at 60 hz though. I figure that's because I didn't have a specific ATi driver for my Radeon 7500 though.

So fresh off my minor success, I decided to throw caution to the wind and fully install ubuntu 5.10. The installation seemed to go fine, again, until it went to load GNOME where the same thing happened as before.

So I thought that maybe it was the videocard screwing up all that nonsense. So I went back into windows (xp home) and enabled the onboard chip, and disabled the physical card. However this did nothing to remedy the situation.
----------------------------------------

So I'm wondering if you might have a clue as to what the problem might be. My computer specs are as follows:

P3 930 MHz
128 MB PC133
Main OS: Windows XP Home (No SP)
ATi Radeon 7500

---

### Post by dcstar on 2006-01-23
[QUOTE=osisnie]Let me start off by saying that I am completely new to the world of linux. To be perfectly honest, the only reason I tried installing it at all was due to a quite large span of boredom. But that is not to say that I don't want to toy around with it. So here's whats happened.
----------------------------------------
First I tried with the live cd. Everything seemed to be going alright until it tried to load GNOME. It said "Ok" on that little splash screen thing but the screen went black and there was a frozen underscore in the top-left corner. No activity was going on.. no attempts to access the CD or hdd

So I went and burned a knoppix live cd. Apparently that uses KDE. It worked nearly flawlessly. The desktop refused to display over 640x480 at 60 hz though. I figure that's because I didn't have a specific ATi driver for my Radeon 7500 though.

So fresh off my minor success, I decided to throw caution to the wind and fully install ubuntu 5.10. The installation seemed to go fine, again, until it went to load GNOME where the same thing happened as before.

So I thought that maybe it was the videocard screwing up all that nonsense. So I went back into windows (xp home) and enabled the onboard chip, and disabled the physical card. However this did nothing to remedy the situation.
----------------------------------------

So I'm wondering if you might have a clue as to what the problem might be. My computer specs are as follows:

P3 930 MHz
128 MB PC133
Main OS: Windows XP Home (No SP)
ATi Radeon 7500[/QUOTE]
Do a forum search for things like "X server", there are many threads on how to change over to a text screen and manually reconfigure your /etc/xorg.conf settings when problems like yours are encountered.

If you don't get anywhere with that, repost your problem in the "Installation and Upgrade Help" forum.

---

