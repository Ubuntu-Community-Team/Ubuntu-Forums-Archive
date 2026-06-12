---
title: "Issues with multiple monitors"
date: 2013-01-18
forum: Desktop Environments
---

### Post by IdoSC on 2013-01-18
I'm using Ubuntu 12.10 on a PC with GeForce GT220, and 2 monitors; one is used as a TV (Samsung P2770HD) and connected through the DVI port, and the other is used as a workspace monitor, connected through the VGA port (some old, obscure LCD monitor that Nvidia X Server Settings wizard names "unknown CRT monitor" for some reason).

Let me start by saying that my BIOS menu only appears on the P2770HD monitor.
Now, on Ubuntu: I always use duplicate displays when running my computer, resolution is 1152x864 (which is supposedly the best resolution my smaller LCD screen can get). Everything works fine, until I try to boot up any application that goes fullscreen (funnily enough, Windows based programs running on Wine, and my WinXP VirtualBox, are the only exceptions to this rule). I'm going to split my issues into different bullets:

1. Although I've already set my workstation monitor as the default screen in the Nvidia X server settings wizard, when any game goes full-screen, the small LCD alerts me that no input is received from the source, then the game appears on the TV. The case remains the same when I completely disable my TV monitor in Ubuntu's display settings (aka top right corner > System Settings > Displays) upon booting the game up.

**NOTE: **Just to point that out, the ideal outcome for me would be the ability to retain the mirrored displays even when in-game. But if I had to make a choice, I'd rather use my small LCD (most of my games require a keyboard and a mouse...) than the TV, keep that in mind.

2. Once I close the problematic fullscreen application, it appears that there's still no signal in the small LCD; when going back to Ubuntu's display settings, it also seems that the "Mirror displays" checkbox was magically unchecked. Obviously the signal returns to the small screen, however...

3. Once the signal returns after fixing the 2nd issue, my Launcher disappears. In order to fix that, I need to go back to Display settings, completely disable my P2770HD, then enable it and check "Mirror displays" once again, which is an incredibly tiresome process considering, y'know...I like playing games :P

4. This one's not really related to Ubuntu, but if anyone's already at it, I'd rather have my BIOS using the smaller LCD as the primary display rather than the P2770HD too.

Thanks in advance!

---

### Post by IdoSC on 2013-01-19
Sorry for the bump, but is anyone here familiar with that sort of issues?

---

