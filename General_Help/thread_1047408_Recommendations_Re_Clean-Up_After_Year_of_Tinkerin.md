---
title: "Recommendations Re: Clean-Up After Year of Tinkering?"
date: 2009-01-22
forum: General Help
---

### Post by RipperHoss on 2009-01-22
Okay, a little over a year ago, I decided to make the switch from Vista 64 (I know, I was a heathen, but I've seen the light!) to Ubuntu (originally Hardy x64, upgraded to Intrepid x64) and have since switched every computer I own.  Despite the occasional headache (migraine), the switch has been relatively smooth.

Here is my situation:
Right now, I have three identical 250 GB SATA hard drives in my computer, in the following configuration:
[list][*]Drive 1: Boot drive, 232.88 GB NTFS Partition.  I call this the "Leper Colony" drive, as it still holds Vista 64.
[*]Drive 2: Two ext3 partitions, neither mounted under Ubuntu.  This was an install of openSUSE that lasted about 15 minutes (about how long I spent staring at the computer screen trying to comprehend Linux without Synaptic).
[*]Drive 3: My Ubuntu install. Auto-partitioned (before I knew better).[/list]

Naturally, having 2/3 of my hard drives occupied with things I will never use again is a less-than-ideal circumstance.

Here is my question:
Is it possible/plausible to purge both the 1st and 2nd hard drives and combine them into one /home partition without reinstalling?  I know that if I change my BIOS settings I can set drive 1 and 2 into RAID0, then create/move the /home partition there and see the benefits of that.  Is that the best way to stripe the two drives?  Is striping the two drives even necessary/beneficial, in this case?  Would changing the drives from AHCI (the current setting) to a BIOS-managed RAID have adverse effects in terms of performance?  Would merging the drives cause GRUB to flip out, as there would appear to be two logical drives instead of three?

Any assistance would be helpful.

Thanks!

---

