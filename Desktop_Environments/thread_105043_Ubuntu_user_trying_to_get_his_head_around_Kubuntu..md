---
title: "Ubuntu user trying to get his head around Kubuntu. Need Help."
date: 2005-12-17
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2005-12-17
I grabbed the latest daily for Kubuntu. Dapper seems to be shaping up nicely. Here goes with some of my "switching to Kubuntu" problems.

When I go to "System Settings" (nice GUI BTW) and then "Network Settings" it brings up a window that is too big (goes beyond the bottom of the screen), tells me my "Platform is unsupported" (no clue what that means) and for me to change anything I need to click the "Administrator Mode" button.
I assume its at the bottom and I cant hit it. Thing is, on other windows where it has that button, when I click it it sometimes works and sometimes not. Just a blank window sometimes. I kinda expect it to ask me for a password. Am I wrong?

I know this is a daily build and I would like to help out testing but If I cant get online Im screwed.

Anyone know the command to run the "Network Settings" app? I could **sudo network-settings** or something like that.

---

### Post by GeneralZod on 2005-12-17
Try running "kcontrol" from the command-line - it's like System Settings, but (in Hoary and Breezy at least) it actually all fits on the screen :) Some people have difficulties switching to "Administrator" mode in kcontrol; if you have this trouble, do

```

sudo kcontrol

```

instead.  Network stuff is contained in here, but note that there are bugs with the KDE network configuration - for example, it always completely deletes your gateway information, so you have to enter it into /etc/network/interfaces manually :rolleyes:  Maybe this has been fixed in Dapper, though :)

Good luck!

---

### Post by MetalMusicAddict on 2005-12-17
Nice Ill give that a look now.

---

