---
title: "Reporting bug in 18.04"
date: 2019-07-31
forum: Desktop Environments
---

### Post by barking63 on 2019-07-31
About once a day, Ubuntu 18.04 slows to a crawl and then stops responding because Firefox, Web Content, or kswapd0 starts hogging the CPU (sometimes >100% use).

I believe this is a bug and would like to report it as such, but I need some advice about how to gather the information required ([https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)) to file a Launchpad report.

Because this is not a crash, no crash file is generated. Because the system becomes unresponsive, I generally cannot open a terminal and then open top after the problem occurs. And because when I am able to open top, one of three different processes seems to be at fault, I am not sure which package to report the bug against.

Any suggestions about how to gather the required information?

Thank you.

---

### Post by Autodave on 2019-07-31
18.04 has been out for awhile now and I really don't see any posts here with that problem.  Are you sure that your equipment isn't at fault?  Could you give us the specs on your machine?

To me, it sounds like an overheating problem.

---

### Post by barking63 on 2019-07-31
Thanks for the quick reply.

There are several similar bug reports for 18.04, but I wasn't able to determine from the reports whether they are the same or merely superficially similar. The Launchpad bug numbers are #1759734, #1788989, #1764597, and possibly #1759734.

The machine is a Lenovo E460 with four Intel Core i3-6100U CPUs @ 2.3GHz, 4 GB RAM, and a 250 GB SSD.

Question about your hypothesis: Do you believe that overheating would *cause* excessive CPU usage? Or that it would *result from* excessive CPU usage?

---

### Post by Autodave on 2019-07-31
Memory overheating *could *cause that.  The CPU running at 100% could definitely cause that.

Do you hear the fan running?  Are the inlet / outlet vents unblocked?  Have you tried blowing compressed air through the unit? (Please make sure that unit is shut down first.)

---

### Post by barking63 on 2019-08-01
Thank you. I haven't tried compressed air but can do so.

The fan is definitely running when the CPU is at 100%. Inlet/outlet vents are unblocked, clean, and free of significant dust. I've installed psensor and will keep an eye on load and temperature and see if anything jumps out.

Whatever the role of heat in the problem, *something* is still causing the CPU to run at 100%, and I'm assuming it's the CPU load that's causing the system to grind to a halt. IMO, browsing a static web page (no gaming or video), even having half a dozen tabs open, shouldn't do this. And FWIW I never had this problem in 16.04; it began a few months ago after I did a clean install of 18.04. Hence my supposition that it's a software issue.

---

### Post by Autodave on 2019-08-01
Another thing that I thought of: are you using an ad blocker?  Some of them will grind a machine to a halt.  *uBlock* is a decent one to use if you must.

---

### Post by speartip on 2019-08-01
Following on from Autodave, if Firefox is causing your problem, try disabling all the addons & see if the problem goes away. If it does, enable them 1 by 1 to see which is causing the issue.

---

### Post by barking63 on 2019-08-04
Thanks for the suggestions, but I don't have any adblockers or other Firefox extensions installed. The only extensions listed at about:support are the search engines that come pre-installed.

---

### Post by barking63 on 2019-08-04
Still working on this. Tried Firefox in safe mode, but no improvement. Hardware temperatures are fine at 40*C or so.

Firefox and "Web Content" are still consuming excess resources. For example, merely opening Morningstar.com's home page sends Firefox to 40% + Web Content 80-115% CPU use. Having two or three pages running at once is enough to freeze up. Percentages are much reduced if I turn off Javascript, but of course most web sites don't work without Javascript. As far as I recall, this problem is new to 18.04, in that I never had trouble with it using 16.04.

---

### Post by ra7411 on 2019-08-04
> **barking63 said:**
> Still working on this. Tried Firefox in safe mode, but no improvement. Hardware temperatures are fine at 40*C or so.

Firefox and "Web Content" are still consuming excess resources. For example, merely opening Morningstar.com's home page sends Firefox to 40% + Web Content 80-115% CPU use. Having two or three pages running at once is enough to freeze up. Percentages are much reduced if I turn off Javascript, but of course most web sites don't work without Javascript. As far as I recall, this problem is new to 18.04, in that I never had trouble with it using 16.04.

Do you get high cpu usage and overheating w/ different browsers?
I've been using FF for a couple yrs and it sometimes runs the cpu pretty hard for no apparent reason. I use System Monitor to kill FF, do a FF restart and restore, and everything is fine again.

---

### Post by barking63 on 2019-08-04
Thanks for the suggestion. I'm not getting overheating, though; just high CPU usage leading to freeze-up.

Just tried the same page via Chrome, and it is running three separate chrome processes totaling 120% CPU. True on a few other pages too, always ones running Javascript.

Don't know enough about how Ubuntu/Firefox/Chrome implement Javascript to know where to go from there...

As for killing and restarting, when this happens it freezes hard enough that I can't access the system monitor or terminal. Can move the cursor around, but keyboard is nonresponsive and nothing else works. So that's not an option.

---

### Post by Autodave on 2019-08-05
The only thought I have right now: if it were my machine, I would try Xubuntu on it.  Xubuntu is a much lighter desktop and just might solve your problem.  Even if you aren't sure, make a boot medium with Xubuntu 18.04 and run the machine from that and see what happens.  If all seems good, install it.  You could also make it dual boot with Ubuntu.

---

### Post by pushbike06 on 2019-08-05
How much RAM do you have installed? I think you need at least 4Gb these days with the huge webpage content, scripts etc. If you want to run Fire Fox with multiple tabs. e.g 4tabs could push you over 2Gb this would require the CPU to work over time shuffling stuff on/off the Swap space.
I recently had to increase from 2Gb to 4Gb because of the slowing down of everything.
Ubuntu 18.04.2 64bit 250Gb HD 4GB RAM 0 swap space.
Intel® Core™2 Duo CPU E7500 @ 2.93GHz × 2

---

### Post by kingof1981 on 2019-09-01
hey.
i've a almost the same problem while firefox is running. WEB Content runs up all cores to a 100% when i start any application that requires root powers. this happens only on my laptop and only while running root applictons. i run  journalctl -xb and top to might locate the issue but as far i can see through the output from journalctl -xb i can't see anything unusual. while the cpu is at full load, journalctl -xb gives no output.  the only thing i noticed that WEB content thingy running at full load.
> -- Logs begin at Tue 2018-05-29 19:51:06 CEST, end at Sun 2019-09-01 14:31:04 CEST. --
sep. 01 14:24:53 ko81x2 kernel: microcode: microcode updated early to revision 0x21, date = 2019-02-13
sep. 01 14:24:53 ko81x2 kernel: Linux version 4.15.0-60-generic (buildd@lgw01-amd64-030) (gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1)) #67-Ubuntu SMP Thu Aug 22 16:55:30 UTC 2019 (Ubuntu 4.15.0-60.67-generic 4.15.18)
sep. 01 14:24:53 ko81x2 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-60-generic root=UUID=7e6b3a00-6150-4808-bfbc-8ff2654c8b48 ro quiet splash vt.handoff=7
sep. 01 14:24:53 ko81x2 kernel: KERNEL supported cpus:
sep. 01 14:24:53 ko81x2 kernel:   Intel GenuineIntel
sep. 01 14:24:53 ko81x2 kernel:   AMD AuthenticAMD
sep. 01 14:24:53 ko81x2 kernel:   Centaur CentaurHauls
sep. 01 14:24:53 ko81x2 kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
sep. 01 14:24:53 ko81x2 kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
sep. 01 14:24:53 ko81x2 kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
sep. 01 14:24:53 ko81x2 kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
sep. 01 14:24:53 ko81x2 kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
sep. 01 14:24:53 ko81x2 kernel: e820: BIOS-provided physical RAM map:
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009d3ff] usable
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x000000000009d400-0x000000000009ffff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x0000000040005000-0x000000009ffaffff] usable
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x000000009ffb0000-0x00000000a13affff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000a13b0000-0x00000000aa3befff] usable
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000aa3bf000-0x00000000aaebefff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000aaebf000-0x00000000aafbefff] ACPI NVS
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000aafbf000-0x00000000aaffefff] ACPI data
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000aafff000-0x00000000aaffffff] usable
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000ab000000-0x00000000af9fffff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
sep. 01 14:24:53 ko81x2 kernel: BIOS-e820: [mem 0x0000000100000000-0x000000024f5fffff] usable
sep. 01 14:24:53 ko81x2 kernel: NX (Execute Disable) protection: active
sep. 01 14:24:53 ko81x2 kernel: SMBIOS 2.7 present.
sep. 01 14:24:53 ko81x2 kernel: DMI: Dell Inc. Vostro 3560/05GV6H, BIOS A17 04/14/2014
sep. 01 14:24:53 ko81x2 kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
sep. 01 14:24:53 ko81x2 kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
sep. 01 14:24:53 ko81x2 kernel: e820: last_pfn = 0x24f600 max_arch_pfn = 0x400000000
sep. 01 14:24:53 ko81x2 kernel: MTRR default type: uncachable
sep. 01 14:24:53 ko81x2 kernel: MTRR fixed ranges enabled:
sep. 01 14:24:53 ko81x2 kernel:   00000-9FFFF write-back
sep. 01 14:24:53 ko81x2 kernel:   A0000-BFFFF uncachable
sep. 01 14:24:53 ko81x2 kernel:   C0000-E7FFF write-protect
sep. 01 14:24:53 ko81x2 kernel:   E8000-EFFFF write-combining
sep. 01 14:24:53 ko81x2 kernel:   F0000-FFFFF write-protect



---

