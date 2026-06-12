---
title: "Ubuntu fails to draw application windows"
date: 2015-11-15
forum: Desktop Environments
---

### Post by loganetherton on 2015-11-15
I have a Dell M380 laptop which came with Ubuntu 14.04 preinstalled.

Recently, I've been experiencing a problem with application windows failing to draw properly, as shown in the below screenshot of a "block contact" window from Skype. The expected output is that it would render correctly.

[http://i.imgur.com/CcGeE0b.png](http://i.imgur.com/CcGeE0b.png)

This is not unique to Skype. It happens sporadically for all manner of windows.

Near as I can tell, everything else is working just fine, with the exception of sporadic problems with suspending the system (although I believe that's related to the wireless device, rather than anything related to video).

The current output from my Xorg.0.log can be found here: [http://paste.ubuntu.com/13294627/](http://paste.ubuntu.com/13294627/)

The output from lspci for my video devices (at least all of those that seem relevant) is:

VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
3D controller [0302]: NVIDIA Corporation GK107GLM [Quadro K1100M] [10de:0ff6] (rev ff)

Any suggestions, further debugging instructions, etc are welcome.

---

### Post by loganetherton on 2015-11-16
OK, so, when I mentioned that I was having problems suspending, but it was unrelated, I was WRONG.

I can consistently reproduce this problem by suspending my system, and then trying to open up any child window of a program. By this I mean:

1) Open Skype
2) Try to block a contact
3) Popup window fails to draw

Again, this happens with all programs, I am simply using Skype as an example.

Any ideas?

---

