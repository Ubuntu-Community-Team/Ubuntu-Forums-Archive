---
title: "amd dgpu poor performance"
date: 2021-02-05
forum: Gaming &amp; Leisure
---

### Post by saeedkh on 2021-02-05
[FONT=Helvetica]Hi everyone. It’s been a while since I installed Ubuntu. My laptop model is Probook 4540S. When I ran glmark, the FPS of the Intel graphics card showed better than the AMD graphics card, and the game is like Counter 23 FPS, and in Windows it is 50 FPS. Why AMD is so weak in Linux. Can it be improved?[/FONT]

---

### Post by CelticWarrior on 2021-02-05
Welcome.

Are you sure about the model? All the search results I've found for 4540S mention Intel Graphics only.

---

### Post by saeedkh on 2021-02-05
Yes probook4540s. It has two Intel and AMD graphics cards. And specifications below the graphics card in Ubuntu
*-display                 
       description: VGA compatible controller
       product: Thames [Radeon HD 7550M/7570M/7650M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:34 memory:b0000000-bfffffff memory:d0900000-d091ffff ioport:3000(size=256) memory:d0920000-d093ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4000(size=64) memory:c0000-dffff

---

### Post by nunchuckmadness on 2021-03-06
Make sure to use the proprietary drivers. it looks like it has an intel cpu with internal graphics and the amd card. idk if the onboard graphics would mess with it... when optimized amd should work well with the right distros. make sure youre on 20.04

---

### Post by mikewhatever on 2021-03-06
> **nunchuckmadness said:**
> Make sure to use the proprietary drivers. it looks like it has an intel cpu with internal graphics and the amd card. idk if the onboard graphics would mess with it... when optimized amd should work well with the right distros. make sure youre on 20.04

There aren't proprietary drivers available for both, so it is easier said then done.

---

### Post by nunchuckmadness on 2021-03-06
> **mikewhatever said:**
> There aren't proprietary drivers available for both, so it is easier said then done.

check additional drivers in software and updates,

found this on the web, Linux/ubuntu drivers at the bottom of the webpage. idk about the intel.. 

[https://www.amd.com/en/support/graphics/amd-radeon-hd/amd-radeon-hd-7000m-series/amd-radeon-hd-7650m](https://www.amd.com/en/support/graphics/amd-radeon-hd/amd-radeon-hd-7000m-series/amd-radeon-hd-7650m)

---

### Post by CelticWarrior on 2021-03-06
Again, > *[COLOR=#000000]**There aren't proprietary drivers available for both**, so it is easier said then done.[/COLOR]*

> [COLOR=#000000]check additional drivers in software and updates[/COLOR]
You won't find any for Intel or AMD graphics.

> [COLOR=#000000]found this on the web, Linux/ubuntu drivers at the bottom of the webpage. idk about the intel..[/COLOR]

[https://www.amd.com/en/support/graph...adeon-hd-7650m]("https://www.amd.com/en/support/graphics/amd-radeon-hd/amd-radeon-hd-7000m-series/amd-radeon-hd-7650m")
You found the old and currently unsupported AMD proprietary drivers from 2015!
Even if they could be installed - they can't - you wouldn't want them.

---

### Post by nunchuckmadness on 2021-03-07
my bad, these are for 20.04  [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20)

---

### Post by CelticWarrior on 2021-03-07
> **nunchuckmadness said:**
> my bad, these are for 20.04  [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20)
Indeed, but not for the OP's card.
There are currently two open-source drivers for AMD graphics: Radeon and amgpu. The Ubuntu installer chooses the correct driver depending on the hardware. Older cards are supported by radeon, newer cards are supported by amgpu. The OP's runs with radeon. Only those that run with amgpu have the option to install the proprietary version - amgpu-pro -, of your link, although almost never there's a reason for that:

[https://www.reddit.com/r/Ubuntu/comments/6c3n7t/open_amdgpu_drivers_vs_official_amd_drivers_which/](https://www.reddit.com/r/Ubuntu/comments/6c3n7t/open_amdgpu_drivers_vs_official_amd_drivers_which/)
[https://www.phoronix.com/scan.php?page=article&item=mesa-201aco-amd&num=1](https://www.phoronix.com/scan.php?page=article&item=mesa-201aco-amd&num=1)
[https://www.youtube.com/watch?v=bcXCYCaLh1I](https://www.youtube.com/watch?v=bcXCYCaLh1I)

---

### Post by nunchuckmadness on 2021-03-07
i think the 2015 drivers are the latest proprietary even the windows drivers are dated 2015. idk, the config might not be viable for gaming in linux. newer stuff is working better because more dev work is being done with linux in mind so expected older stuff to work as well as it does in windows might not be realistic, unless there's a good driver out there somewhere.

---

### Post by QIII on 2021-03-07
nunchuckmadness -- please desist with the speculation about a better AMD driver "out there".  There is none, as explained above.  Let me repeat:  AMD graphics hardware is supported by two and ONLY two drivers:  radeon or amdgpu, and which is installed is dependent on which supports the hardware detected.  Each of them is open source.  

Both the radeon and amdgpu modules are already present in the Linux kernel, so there is no reason to go looking for something.

There is a proprietary overlay called AMDGPU-PRO, which AMD makes available, but its support is limited to a subset of hardware which amdgpu supports.  That overlay may provide some users with useful additions.  But, again, only if amdgpu supports the hardware.

The older Catalyst drivers will not work with modern Linux distributions.  Catalyst is dead.

That is it.  That is all.  There is no more.

---

### Post by Doug S on 2021-03-07
Wasn't there a massive massive overhaul of this stuff as of [kernel 5.11]("https://lists.freedesktop.org/archives/dri-devel/2020-November/285936.html")?
Still with many [bugs]("https://gitlab.freedesktop.org/drm/amd/-/issues") to sort out.
My suggestion is to try [kernel 5.12-rc2]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12-rc2/"), just as a test.

Disclaimer: I am a server person and know nothing about graphics. I only know the above because I tried to help someone [on another thread]("https://ubuntuforums.org/showthread.php?t=2455791&page=2&p=14024411#post14024411").

---

### Post by nunchuckmadness on 2021-03-07
> **QIII said:**
> please desist with the speculation about a better AMD driver "out there".  There is none

Sorry, it wasn't my intention to suggest there was anything available, just implying a hobbyist somewhere may have written something for themselves that works.

---

### Post by mastablasta on 2021-03-08
> **Doug S said:**
> Wasn't there a massive massive overhaul of this stuff as of [kernel 5.11]("https://lists.freedesktop.org/archives/dri-devel/2020-November/285936.html")?
Still with many [bugs]("https://gitlab.freedesktop.org/drm/amd/-/issues") to sort out.
My suggestion is to try [kernel 5.12-rc2]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12-rc2/"), just as a test.


readeon driver mostly gets minor bug fixes. what could be improved mostly was already improved. especially for older chips.

for example 5.11:
```
[COLOR=#000000]radeon:
[/COLOR][COLOR=#000000]- Expose voltage via hwmon on Sumo APUs[/COLOR]
```

ok, so now you can see the voltage. it won't improve performance unless you planned to overclock.

with radeon driver there are some switches you could try if there is a specific area identified as being problematic. first one is that GPU switching, make sure that when you switch, the AMD has all it needs. proper power, ram settings etc.

when they made radeon for the last supported chips, at first it was 30% drop in perfomance compared to catalyst. but that slowly improved and the performance should be close to what closed source drivers had when they were available. and that was one slightly worse (maybe 5-10% %) than on windows.

---

### Post by babanaqash on 2021-04-20
> **saeedkh said:**
> [FONT=Helvetica]Hi everyone. It’s been a while since I installed [[COLOR=#000000]whatsapp sniffer[/COLOR]]("http://www.gbhouse.info/whatsapp-sniffer-apk/"). My laptop model is Probook 4540S. When I ran glmark, the FPS of the Intel graphics card showed better than the AMD graphics card, and the game is like Counter 23 FPS, and in Windows it is 50 FPS. Why AMD is so weak in Linux. Can it be improved?[/FONT]

I don't think it can be improved. However, if you found any solution, do let me know the process.

[SIZE=3]Thank you in advance[/SIZE]

---

### Post by saeedkh on 2021-04-20
Anyway . Windows supports better than the graphics driver. For some systems like my laptop, Linux is not a good choice

---

### Post by mastablasta on 2021-04-21
you mean AMD supports their older hardware better on windows than on linux. quite possible. older AMD chips had worse support than in windows even before with AMD closed source proprietary drivers

things improved quite a bit with AMDGPU and we went full AMD with their Vega graphics (Ryzen) on laptop and performance is really good. 

but phoronix is a good resource. they test various linux drivers against windows. sometimes results are a bit odd. at lower settings linux would get bad results but at higher it could be better than in windows.

in any case you should use what works bets for you PC. if windows work better, then just use windows.some people dual boot which is not really an issue with fast SSD and nvme drives around today. i set up a special shortcut i named "boot to win" that would boot to windows once and then when i rebooted form there i would get back to linux. but as time moved on i used ti less and less and most old games i already moved to linux. they run through playonlinux/wine and performance is mixed. a few run a lot better and faster than in windows (most notably Far Cry 2), some are running slower or have slow downs during the game, some are about the same.

i never played CSgo while on windows. on linux CS:GO shows 20 FPS on medium, however it must be way better than that as to me it feels quite smooth. normally i get a slow down at the start of game but after 2 or 3 rounds or after warm up it all works well. the only issue i have is 10 v 10 on causal. it lags on start, but when most people are eliminated it works normal. and i think it is all because of my old single core CPU. so i usually wait at the back a bit, cover the rear access and only later got into action. oh and deathmatch / wargames is also very slow. but i think it would be slow on windows as well. the nvidia card i use should easilly give 60FPS, so it must be the CPU.

---

### Post by annajane on 2021-04-23
[COLOR=#000000]did you use the proprietary drivers?[/COLOR]

---

### Post by mastablasta on 2021-04-26
yes, i use nvidia 3.90 driver (card is already in legacy support). maybe VAC or something is taxing the CPU. before it loaded pretty fast, now it takes 10 minutes to load on my single core CPU and 3 minutes on my kids PC that has Ryzen 7. maybe i need to just reinstall the whole thing.

i also did some further checks and it turns out that no other platforms for CS:GO (FaceIt, ECL, ELS...) are available for linux because they don't have the anticheat for linux. this is a bit sad, because on valve MM there are soooo many cheaters. i don't mind if i lose a lot. i am not a pro. but to play against head shots only people who can see through smoke and track you through walls for a wall bang is kind of tiring. there is also an issue where you get lev 30 players matched with lev 5 or lev 1 players. 

few weeks ago we had a match where we kicked one on our end after 3 round and they kicked 4 on their end for cheating and griefing. so it was 4 v1 and it ended soon after. another match saw one on our end kicked and one on their end. later i watched a match replay and i had to report another one.  but they will just create or buy a new account. 

what they od is buy premium, cheat to collect rewards for missions fast and then sell the items. once the items are sold, they also sell the account. 

so mostly we play against bots and each other. 

back with original CS:GO (1.6.) if someone was blatant cheater, they got kicked off and banned from server immediately. maybe there should be a similar linux service to these on windows. it would also be good to have some kind of working honour system as well as fast move against cheats (not 6 month later after they already changed 100 account they ban their first one).

---

### Post by mastablasta on 2021-04-28
i improved performance slightly by reducing swappiness. it was set to default which is 60, but i have only 4 GB RAM so system started using (HDD) disk way too fast.

how to reduce swappiness: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Look under title: **What is swappiness and how do I change it?**

---

