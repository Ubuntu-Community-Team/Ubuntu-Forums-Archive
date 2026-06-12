---
title: "Xubuntu Minimal 24.04 desktop freeze on closing laptop lid"
date: 2024-07-22
forum: Desktop Environments
---

### Post by delanthear on 2024-07-22
I think I have the same issue as listed on this closed thread: [https://ubuntuforums.org/showthread.php?t=2482457](https://ubuntuforums.org/showthread.php?t=2482457)

Xubuntu 24.04 Minimal installed on a Toshiba Chromebook.  When I close the laptop lid, it's likely that when I come back to opening the lid, the window manager will be frozen.  Mouse pointer will still move, but I can't select anything and no keys do anything beyond a long press on power to reset the machine.

Any clues on how to debug?  I'm a noob :)

---

### Post by TheFu on 2024-07-22
I installed a few different versions of 24.04 when it was first released, just to see the GUI.  The Xubuntu 24.04 installs were never stable for me. The desktop would freeze within about 10 minutes of use.  I did 3 installs and it didn't get any better. I didn't plan to use XFCE, so these installs weren't very important to me, but a fresh install, with mostly default choices, should run, right?

My solution was not to use Xubuntu 24.04, but there were other core reasons why I didn't want any 24.04 at all (no LVM support in their desktops!).  Guess, I'm only saying - me too.  To me, "New" is the enemy of "Stable" and stable is what I seek from a desktop.

I'm curious.  You signed up here in 2006, are using a chromebook and you are still a noob?

---

### Post by delanthear on 2024-07-22
Yeah, basically, every few years I attempt to start using Linux as a desktop, install it and get derailed by something important not working and being unable to fix it.  Complete failures on install.  Audio not working.  WiFi not working.   Basically, it's never works enough for me to just use it, and I can never get the issues fixed, so I never actually get anywhere with learning how it works.  I suspect it's because I'm always installing on old weird laptops...

---

### Post by TheFu on 2024-07-22
I ran Ubuntu server with a lite-GUI on a Toshiba Chromebook CB-35 for about 3 yrs.  Besides the sucky keyboard, it was the best laptop for travel I've ever owned or used.  I was cautious to pick a chromebook with a replaceable BIOS and SSD.  I wish it had more RAM, but the CPU and iGPU were fine for my needs.  I did have to initially install a non-LTS version of Ubuntu to get the hardware supported, but when the LTS was release, the install was pretty easy.  Sadly, the keyboard started losing keys after about 2 yrs (crappy hardware) and replacement parts, without installation, was about 1/3rd to cost of the entire CB when new!  Installation would probably have cost $100, so now it would 2/3rd the price of new, so I decided to move on. Sometimes I still regret that.

Anyway, try a different GUI/flavor.  Lubuntu 24.04 worked great.  I bet Linux Mint would work well too (and avoid some of the Canonical-forced new things).

I never had issues with my CB wifi or wired ethernet (USB3-to-GigE adapter).  The touchpad and screen all worked, as did the sound. I don't remember if it had a webcam built-in or not. I never used it (it was pre-COVID).

Give Lubuntu 24.04 a try. I know it sounds crazy, but that "just worked" in my testing here. No problems at all.

---

### Post by delanthear on 2024-07-23
This is a CB30-B-13.   So far I attempted to install Elementary OS 7 which claimed to fail on install, then when I rebooted it seemed to work fine.  I fell into the trap of clicking Yes when it asked if I wanted to install updates and that killed it completely, so moved to the next distro I saw where people seemed to have some joy with Swanky.    Xubuntu was the next one to try and I chose Minimal as I expected it to need to be as light as possible.  On the surface it's working ok, but it seems like there is something [screwed with App Armor]("https://ubuntuforums.org/showthread.php?t=2499307") which means a lot of snaps just don't work.  (Cheese and Mousam just fail to work at all wtih lots of errors, other apps are hammering the logs), then we've got this lid issue and sometimes the audio just crashes and beeps constantly till I kill whatever was making the sound initially.

I'll persevere for a little while longer, but will make a jump to try one of those suggestions soon if I don't get further with the AppArmor issues.

---

### Post by TheFu on 2024-07-23
Snaps aren't good for Chromebooks with limited storage and limited RAM.  Best to avoid them completely.

---

### Post by delanthear on 2024-07-24
> I bet Linux Mint would work well too (and avoid some of the Canonical-forced new things).

Thought I'd give it a go, but takes up too much space.  Needs a minimum of 16GB, but the Chromebook only has a 15GB SSD.  Doh!

---

### Post by &amp;KyT$0P# on 2024-07-24
> **TheFu said:**
> Give Lubuntu 24.04 a try.

+1.  I used to run into an issue similar to this with xfwm4 in older Xubuntu versions, and my solution at the time was to switch window manager to Openbox, which Lubuntu uses by default.

---

### Post by delanthear on 2024-07-24
Giving it a try now.  Installer has crashed on me though so far...   (Just about typical....)

---

### Post by TheFu on 2024-07-24
> **delanthear said:**
> Thought I'd give it a go, but takes up too much space.  Needs a minimum of 16GB, but the Chromebook only has a 15GB SSD.  Doh!

I have bad news for you. 16G will be tight for every popular Linux made today. 

Option 1: swap out the SSD in your chromebook.  It isn't hard, if you have a model that allows it.  You don't need to spend much at all.  $20, of course, $30 will get you 3x more storage than the $20 version.

Option 2: use an ISO USB3 setup like Ventoy provides with separate data areas for your files and updates.  You can boot chromebooks from USB or microSD storage, though you really want USB3 or better storage for this.  Anyway, a 120G USB3 storage devices - it can even be an external SSD - will completely removed the storage limitation.

As for freezing when you close the lid.  Your available swap needs to be a little larger than your RAM in the system for hibernation to work.  You can disable hibernation and use "standby" mode, but that does drain the battery.  I used "standby" mode nightly for years with my Toshiba Chromebook without any issues, after I created a clean USB-disconnect for the USB3-to-GigE adapter.  Before that, it would never work and it crashed coming out of standby.

---

### Post by currentshaft on 2024-07-24
> **delanthear said:**
> I think I have the same issue as listed on this closed thread: [https://ubuntuforums.org/showthread.php?t=2482457](https://ubuntuforums.org/showthread.php?t=2482457)

Xubuntu 24.04 Minimal installed on a Toshiba Chromebook.  When I close the laptop lid, it's likely that when I come back to opening the lid, the window manager will be frozen.  Mouse pointer will still move, but I can't select anything and no keys do anything beyond a long press on power to reset the machine.

Any clues on how to debug?  I'm a noob :)

Try this press Control-Alt-F4 to get a non-GUI login prompt, log in, and run "startx".

---

### Post by delanthear on 2024-07-25
I don't need much space.  It's not used as a power laptop, just mostly for sofa browsing and taking places for keeping connected.

The good news though is that after 3 attempts at installing, I appear to now have a working Lubuntu install.  Doesn't crash when closing the lid.  Apparmor doesn't complain about normal apps trying to write out config files.  It even connects to WiFi.  It's taken me 15 years, but I might actually have a Linux Desktop I can work with....   ;)   Thanks for the recommendation!

I haven't tried the audio yet though, but I can live without that if it's not working....

---

### Post by TheFu on 2024-07-25
a) if this is solved, please use the Thread Tools button to mark it so. This helps other people with similar issues to find things that might work for their needs.

b) Sadly, 16GB is just the start of the bloat levels that nearly all modern GUI Linuxes need to load their base packages.  For most of 24.04 Ubuntu variants, we suggest 35GB as the minimum required storage.  Seriously, upgrade the SSD, if you can.  On my CB35, it was 8 screws off the back and 1 screw for the SSD.  That's it.  10 minutes if you go really slow.  If you know what you are doing, 3 minutes.  You will need to ensure you have 4GB for swap to prevent out-of-RAM crashes without any warnings too.  So that 16GB of SSD is now 12G.  A smaller amount of swap will just cause more crashes.  I did months of testing to discover this.  I had chromebooks with 2GB and 4GB of RAM in the testing.  Also had regular systems with 6, 8, 12, 16, and 32GB of RAM .... and found that 4.1GB is the ideal amount of SWAP for any Desktop Linux that doesn't hibernate.

---

### Post by delanthear on 2024-07-25
> **TheFu said:**
> a) if this is solved, please use the Thread Tools button to mark it so. This helps other people with similar issues to find things that might work for their needs.

Even if it's not solved?  We've effectively abandoned the problem?  (I mean, I'm fine with that, but the issue with lid closure causing crashes is undiagnosed completely.

> **TheFu said:**
> b) Sadly, 16GB is just the start of the bloat levels that nearly all modern GUI Linuxes need to load their base packages.  For most of 24.04 Ubuntu variants, we suggest 35GB as the minimum required storage.  Seriously, upgrade the SSD, if you can.  On my CB35, it was 8 screws off the back and 1 screw for the SSD.  That's it.  10 minutes if you go really slow.  If you know what you are doing, 3 minutes.  You will need to ensure you have 4GB for swap to prevent out-of-RAM crashes without any warnings too.  So that 16GB of SSD is now 12G.  A smaller amount of swap will just cause more crashes.  I did months of testing to discover this.  I had chromebooks with 2GB and 4GB of RAM in the testing.  Also had regular systems with 6, 8, 12, 16, and 32GB of RAM .... and found that 4.1GB is the ideal amount of SWAP for any Desktop Linux that doesn't hibernate.

Yeah, I may do this at some point.  Skint though.

---

### Post by TheFu on 2024-07-25
> **delanthear said:**
> Even if it's not solved?  We've effectively abandoned the problem?  (I mean, I'm fine with that, but the issue with lid closure causing crashes is undiagnosed completely.



Yeah, I may do this at some point.  Skint though.

Sorry.  I look over about 30 threads daily and sometimes get confused.

Only you decide if the workarounds are a solution or not.  We aren't like Google's Chromebook support forums here - they decide and close things that aren't closed all the time.

Xubuntu 24.04 was unstable for you. It is unstable for lots of others too.  Lubuntu 24.04 is stable for 2 of the long-time posters here.  With Lubuntu and an appropriately sized swap (4G) does the issue happen?  If it does, can you look through the system logs around the time the lid is closed AND when it is opened for issues?
Also, how much free RAM and swap does the system have?

See how the different issues are related?  Too little disk space means that perhaps Ubuntu-flavors aren't a good fit for your needs.  There are other, stripped down, Linux releases.  If you really want just the smallest, browser-only, Linux, check out Tiny Core.  In 64MB, the entire OS gets loaded into RAM, you get a modern browser and little else. Boot times are crazy fast.  Very little storage is used or accessed, so it is ideal for something like a chromebook.

In short, there is a storage and RAM price required for most Ubuntu Flavors to work.

---

