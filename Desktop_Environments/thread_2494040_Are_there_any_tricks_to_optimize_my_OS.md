---
title: "Are there any tricks to optimize my OS?"
date: 2024-01-03
forum: Desktop Environments
---

### Post by peyre on 2024-01-03
I'm running the latest Xubuntu LTS on an old desktop from 2009 with a Core 2 Duo processor (Wolfdale, E5200@2.50GHz) and 4GB of RAM.  I've overclocked it a bit, RAM's at maximum, the OS runs on an SSD, and I've installed a decent (but not fancy) graphics card.  The computer works ok, though it gets slow on some things, especially in Firefox and playing Lord of the Rings Online, and also for compiling an open-source game I like to tinker with.

I know, why th would I still be using a heavy-duty browser and trying to play an MMORPG on such an archaic machine?  It's what I have and it works, and I'll upgrade when a more advanced desktop comes my way.  My computing needs are generally pretty simple.

I was just wondering if there were any tricks I could pull to streamline the Linux install to make it a little more responsive on heavyweight programs.

---

### Post by SeijiSensei on 2024-01-03
Does it have a swap file or swap partition? If not, you can follow these steps to create a swapfile.

[https://linuxize.com/post/create-a-linux-swap-file/](https://linuxize.com/post/create-a-linux-swap-file/)

I'd go with at least 4G and maybe 8G depending on how much free space is left on the SSD drive.

---

### Post by peyre on 2024-01-03
Oh yes, it should.  That is, during the install I let it create the default partitions.  I haven't checked specifically to see, but gnome-system-monitor does show a swap area.

---

### Post by SeijiSensei on 2024-01-03
Run the command "top" in a terminal. It will show you the usage of actual memory and swap like this
```

MiB Mem :   7777.6 total,    533.8 free,   4919.2 used,   4943.9 buff/cache     
MiB Swap:   8192.0 total,   6615.9 free,   1576.1 used.   2858.4 avail Mem 

```

This machine has 8 GB of memory to which I added an 8 GB swap file just the other day. Already the kernel has put 1.5 G of data in there. And all I doing is browsing and reading email with Thunderbird. 

I don't how large a swap area is these days by default. 

Browser tabs are especially greedy.

---

### Post by peyre on 2024-01-03
Thanks, I'll check it tonight!

---

### Post by ajgreeny on 2024-01-03
If there is any possibility of adding another 4G of RAM I think you would also find the system speed noticeably better, but you already have an SSD so it may not be as much difference as I saw on my laptop with an Intel® Core&#8482;i3 Dual Core Mobile Processor i3-4100M  when I doubled RAM form 4G to 8G.

I still have a spinning HDD, but I know that an SSD is really needed for speed so will eventually get one but not on this machine which has a case that is beginning to fall apart so circumstances really do not warrant the expense just yet.

---

### Post by peyre on 2024-01-03
Pretty sure this thing's topped out at 4GB.

---

### Post by peyre on 2024-01-03
Here it is!  Yep, 4GB of swap.

```
MiB Mem :   3906.1 total,    652.1 free,   1582.5 used,   1671.5 buff/cache
MiB Swap:   3898.0 total,   3898.0 free,      0.0 used.   2074.5 avail Mem
```

---

### Post by ActionParsnip on 2024-01-04
Does a lighter browser like Midori work OK for you? It'll use fewer resources than Firefox

---

### Post by peyre on 2024-01-04
Dropping Firefox as my primary browser is kind of out because I'm very tied up with how it works and the plug-ins I use in it.  I do use Chromium when I want something a bit more lightweight than Firefox, and maybe something like Midori would be even better for a lighter-weight experience.  And I try to limit how many tabs I have open in Firefox.

---

### Post by SeijiSensei on 2024-01-04
I'm a little surprised your system reports no swap in use. Run "cat /proc/sys/vm/swappiness". My value is 60. What's yours?

Higher values encourage the kernel to write to swap.

"Swappiness is a Linux kernel parameter that controls how assertive the swapping mechanism is. Swapping moves inactive memory pages from physical memory to swap memory on a disk (either in a swap file or a swap partition). The process aims to balance data in RAM and utilizes the swap space when physical memory reaches its limits.

The swappiness value is a number between 0 and 200. Lower values indicate minor swapping, and higher values aggressive swapping. When physical memory runs low, the swappiness value directs the kernel's decision for swapping pages."

[https://phoenixnap.com/kb/swappiness](https://phoenixnap.com/kb/swappiness)

---

### Post by peyre on 2024-01-04
Ok, here's **top**.  I have both Firefox and LOTRO running.

```
MiB Mem :   3906.1 total,    104.2 free,   3244.5 used,    557.4 buff/cache
MiB Swap:   3898.0 total,   3840.0 free,     58.0 used.    380.2 avail Mem
```

And **cat /proc/sys/vm/swappiness** returns:

```
15
```

---

### Post by Rubi1200 on 2024-01-04
You should consider increasing the swappiness on your system.

---

### Post by peyre on 2024-01-05
Ok, I've set it to 20.  If you think it should be higher, just let me know.

---

### Post by peyre on 2024-01-10
So, I checked the motherboard; it's a Gigabyte GA-G31M-ES2L, which tops out at 4GB RAM.  Too bad.

But, maybe rather than the RAM, I could upgrade the processor.  It currently has a Core 2 Duo, but the specs say it will support a Core 2 Quad.  Now maybe that's a 2-and-2 (2 physical, 2 virtual core) processor, but that would still be a significant speed bump.

---

### Post by SeijiSensei on 2024-01-11
> **peyre said:**
> Ok, I've set it to 20.  If you think it should be higher, just let me know.

The default on a new build is 60. The max is 200. I'd start by setting it to 60.

---

### Post by peyre on 2024-01-11
Thanks, I'll try that.

---

### Post by SeijiSensei on 2024-01-11
Let it run for a couple of days, then run top again. I bet more of your swap will be used.

---

### Post by TheFu on 2024-01-11
> **peyre said:**
> So, I checked the motherboard; it's a Gigabyte GA-G31M-ES2L, which tops out at 4GB RAM.  Too bad.

But, maybe rather than the RAM, I could upgrade the processor.  It currently has a Core 2 Duo, but the specs say it will support a Core 2 Quad.  Now maybe that's a 2-and-2 (2 physical, 2 virtual core) processor, but that would still be a significant speed bump.

I wouldn't put any money into a system this old.  A used $100 Chromebook would be faster - like 10x faster - even with the same 4GB of RAM.
[https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+E5200+%40+2.50GHz&id=1097](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+E5200+%40+2.50GHz&id=1097) shows 900 passmarks.  That's pretty low these days.
3500 is about the minimal I'd happily run any light Ubuntu desktop using.  For a full Gnome DE, I'd want 8000+ passmarks.

For reference, a Raspberry Pi v4 passmark is about the same as that old E5200. [https://www.cpubenchmark.net/cpu.php?cpu=BCM2711&id=4297](https://www.cpubenchmark.net/cpu.php?cpu=BCM2711&id=4297)

Throwing more money at some problems, especially when the lifespan for a system is close to the end already, isn't a good investment.  A $200 system upgrade would do wonders.  Building a system around a $65 Ryzen 3 4100 would be a huge upgrade.  There are motherboards for $70 and $21 of 8GB of DDR4 RAM would be amazing for your setup.  That's basically 11000 passmarks for less than $180.  That can be doubled for just a little more cash.  If you won't use the existing GPU, then look to get a Ryzen with an iGPU. That will be cheaper and less hassle long term.  Of course, this does mean having $170 to spend, reusing the existing case, PSU, monitor, keyboard, mouse, and all other peripherals. Only the motherboard, CPU and RAM would change.

The supply of B550  Ryzen motherboards is becoming tight, so if you have any hope to upgrade to the next generation, this is the time. Don't wait too long or you'll be stuck getting the latest generation that require DDR5 RAM which will be 2x the cost of DDR4 for at least another year.

---

### Post by peyre on 2024-01-14
A Chromebook might be ok for a laptop, but my laptop's less slow and less important than my desktop.  I use a full-size box at home, with optical drive, card readers, and other things.  Plus it has a delightful old-school feel to it I just love.  I'd like to stretch it out a little if I can.

Looking into it, I found I can upgrade this to a quad-core processor with faster cores than my two current ones (3 GHz vs. 2.5) for under $40, including tax, shipping, and tube of thermal paste.  I had already ordered it before I saw your reply on Thursday.  Of course, if I flub up the transplant, I'll have to do something like what you describe.

---

### Post by TheFu on 2024-01-15
> **peyre said:**
> A Chromebook might be ok for a laptop, but my laptop's less slow and less important than my desktop.  I use a full-size box at home, with optical drive, card readers, and other things.  Plus it has a delightful old-school feel to it I just love.  I'd like to stretch it out a little if I can.

A USB3 dock makes many laptops into amazing desktops.
I have a $20 USB optical drive. It can be used with any system I have, as needed, unlike the older SATA or IDE DVD drives I have.
I use the same monitor, keyboard, mouse with my laptop at home as I do with my desktops, thanks to a KVM-switch.  
For many people, external storage is available over USB3 or faster storage.  My laptop has an eSATA external connector which I've never seen on any Chromebook, but that connector uses a PCMCIA slot, which I've never seen a cheap Chromebook have either.
I've owned 3 chromebook systems.  The single, best, laptop that I've ever owned was a 13.3inch Toshiba Chromebook with 1080p screen, Core ?i3-5250? CPU, 64G SSD. It was very light - under 2 lbs and provided 8-11 hrs of battery, before the battery bulged.  Eventually, I wore out the keyboard on it to the point the it was constantly emitting extra keystrokes, even with an external keyboard connected.  Replacing the keyboard was $80 for parts and $100 for labor, because the keyboard replacement requires removing everything from the case first.  Plastic rivets would be broke, making it never be quite right again. Still i really enjoyed that system for what it was.

OTOH, the passmark rating for that box was about 3500. My current desktop passmarks are just under 20,000. They are nearly identical systems, but one was $450 and the other was sub-$300. There was a 2 yr difference in buying the parts. Prices dropped. Now the CPU is the same price as I paid when it was cheap a few years ago, but the motherboard costs 50% more - stock on it is restricted now.  

My "upgrades" happen about every 7-10 yrs and I try to triple the performance.  Depending on the total time and market situation, my target price was $200 for an upgrade. With Ryzen, the performance improvement AND the ability to have a socket, AM4, that would last more than 2 yrs and provide CPU-only upgrades without much risk got me to spend a little more.  I did move from a 2600 to a 5600G, selling the old 2600 (13000 passmarks) and 16GB of RAM at the time, which made the upgrade for $40.  The new CPU had 19600 passmarks - so a 50% performance increase for $40. Not bad.

Picking the time to buy to get the CPU cheap, motherboard cheap, RAM cheap, is an art.  I can say that throwing money at anything over 5 yrs old is a bad idea, unless that part can be used in newer computers too.  For example, I'd never buy more DDR3 today and I'd have to think REALLY hard about buying DDR4 RAM today.  BTW, I have some unused DDR3 and DDR4 that need a good home.  I'll probably find a local friend to buy me an expensive sandwich for 16GB - in trade.  Now, buying an SSD is not a problem, since that SSD can be used in newer computers be it NVMe or SATA connected.  Heck, I'm putting old SATA SSDs into external cases for sneaker*net storage.

I have a number of 10 yr old computers (MB+CPU+RAM) that would be so much faster, but can't be sold in good conscience to someone else. On one, the BIOS can't always be commanded to come up. It takes about 20 attempts to get into the BIOS once.

Of course, how we spend our money if a personal choice.

---

### Post by him610 on 2024-01-15
You might consider buying a refurbished PC. One can find a recent model for reasonable cost. They are probably coming off lease from a business that get refurbished and put on sale to the public.
For example:  [https://www.newegg.com/dell-optiplex-5050-business-desktops-amp-workstations/p/1VK-0001-6CMN5]("https://www.newegg.com/dell-optiplex-5050-business-desktops-amp-workstations/p/1VK-0001-6CMN5")

Good luck.

---

### Post by peyre on 2024-01-16
Thanks fellas, I appreciate the advice.  I'll likely do something like that down the road.  But since I had the processor already, I swapped it out, and - the difference is night and day!  I used to have to close Firefox for LOTRO to work even reasonably well, and even at that it was jerky in places.  Now it runs surprisingly smooth, even with Firefox open.  And compiling RIS doesn't peg the CPU any more.  

Years back when I bought this thing, I didn't spring for anything top-of-the-line; in fact I recall thinking, ehh, dual-core is enough for me; it's more than I have now.  So I may have had more room for improvement than you were estimating.  Anyhow when this thing becomes too slow for me, the only way to improve things will be to replace it.

---

