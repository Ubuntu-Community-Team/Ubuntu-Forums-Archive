---
title: "[Unity] 23.10 Issues with Booting, GUI"
date: 2023-12-14
forum: Desktop Environments
---

### Post by sdsurfer on 2023-12-14
Linux computing level: just enough to get by most of the time, definitely not a guru.

MSI B560M Pro-VDH
Intel 17-11700K
64GB T-Force 3200 mhz RAM
Unity 23.10 (yes I know it's not an LTS)
NVIDIA G218 (GeForce8400 GS Rev. 3) [I](leave it alone, it does what I need and will replace it soon enough)
[/I]
Accessed via Grub V2
- Windows 7 (never use, but grub is there, going to move it)
- Ubuntu 20.04 (which [doesn't recognize onboard Ethernet]("https://ubuntuforums.org/showthread.php?t=2493379&p=14169259") and I gave up trying at least for now)
- Ubuntu Unity 23.10

Those have "advanced options" but in 23.10 there is nothing helpful, just goes to the unity launch.

Physical drives:
 - 500 MB with grub and Windows (never used)
- 1 TB OS drive with Ubuntu 20.04 (this role will probably change) ENCRYPTED
- 2 TB, originally a data drive but now partitioned between data and Unity 23.10

23.10 install went perfectly on my System76 Gazelle (writing from it now) and attempted install 23.10 on the MSI to mitigate [this problem]("https://ubuntuforums.org/showthread.php?t=2493379&p=14169259"), discussing only the most important ones below.

**[s]Problem 1: [/s]**[s]During boot Ubuntu outputs logs to the monitor, and if it dies on boot you can see the last entry, somewhat helpful. In Unity it does the same but it "fades out" after 10 seconds or so to a black screen. **Is there any way to disable this effect?** I might figure out # 2 on my own if I could see what it's doing.[/s] Edit: this is likely not a Unity problem, [see this post.]("https://ubuntuforums.org/showthread.php?t=2493485&p=14169685")

[s]
**Problem 2:** Recurrent "black screen" result on startup to Unity. As above since there's no recovery mode I can't do much from grub. Tried suggestions from multiple articles/posts to switch to shell/terminal, it basically stared back at me, thoroughly black. :-D **Is there any way to go into a recovery mode from Grub with Unity?**

**Problem 3:** Sometimes I can actually get in to the GUI, Nautilus is throwing various errors trying to open them.
- 1TB encrypted drive: This is dedicated to Ubuntu 20.04. as expected it asks for a password, then it disappeared completely from Nautilus with an error I can't recall and is not coming back. I'll try to get the error on the next reboot (if I ever get back into the GUI.)
- 500 GB volumes: This is where Windows and (I thought) grub was installed, attempting to open it I get "Wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error." 
- The first two ah well but the 22.04 is a HUGE deal, all my apps, domain development, and settings are in there and if I'm going to use this OS I need to be able to move them. [B]Can anyone guess at what's going on here?
[/B][/s][B]

[s]Edit : #4 Window Focus: [/B]This one is kind of big too any "save as," "upload Image" and I suspect other dialogues from the default Firefox install places the focus UNDER the window in which you're working. So if your FF window is maximized, it looks like something is disabled or broken. Once I figured out what was happening I thought it was a site issue, apparently not. Might be fixed by updating Firefox, which I'll try once I get past these other tasks. [B]Is this a known issue and is there a known fix?[/s]
[/B]

I have other issues but will refrain, just hoping to get through these and get back to work (this is my third day LOL.) Thank you in advance for having a look, I also have a Ubuntu 22.04 USB and I'd hate for it to come to that, Unity runs GREAT on my lappie and I like it over Gnome.

---

### Post by sdsurfer on 2023-12-20
> **sdsurfer said:**
> [B]
Edit : #4 Window Focus: [/B]This one is kind of big too any "save as," "upload Image" and I suspect other dialogues from the default Firefox install places the focus UNDER the window in which you're working. So if your FF window is maximized, it looks like something is disabled or broken. Once I figured out what was happening I thought it was a site issue, apparently not. Might be fixed by updating Firefox, which I'll try once I get past these other tasks. [B]Is this a known issue and is there a known fix?
[/B]


Updated the above, the first three were all environment related, most of which started with an old graphics card playing monkeyshines with the UEFI setting in the bios, which led to all sorts of problems. I never really get to the bottom of them but solved them by removing the card from the play.

#4 persists on my laptop and will try to get to the root of it, it may be just FF. I'm going to free up a partition to give Unity another shot, been working with gnome this week and just can't get used to it. :-D

---

### Post by sdsurfer on 2023-12-21
Issue #4: This indeed appears to be a FF issue, it's not doing it in any other apps. [This bug]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1949340") applies to Ubuntu 22.04 but I'm not finding anything for Unity, if I do I'll update this thread, for now, updating my system to Unity. Been working with Gnome for a week or so and just. Don't. Like it. :-D

---

### Post by BicyclerBoy on 2023-12-31
For the video card to work with UEFI booting the VBIOS (in card) must contain EFI GOP.
Video cards from about GTX660 & later supported this although most were shipped/sold without any support.
And it is possible to modify the VBIOS to add UEFI support.

BUT.. There is no way a 8400/9400 era card will ever support UEFI because there is no known UEFI module to copy from & then the onboard VBIOS eeprom is likely too small.
Sorry.

It is possible that after the "boot" phase the display might light up if SecureBoot &/or FastBoot are disabled.
But you will never see the UEFI-BIOS.

---

### Post by sdsurfer on 2024-01-16
test - please delete. I'm getting a security token error in another post. What the heck.

---

