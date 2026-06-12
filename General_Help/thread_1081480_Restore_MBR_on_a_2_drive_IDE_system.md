---
title: "Restore MBR on a 2 drive IDE system"
date: 2009-02-26
forum: General Help
---

### Post by gcmartin on 2009-02-26
I have a 2 drive system on the _Primary IDE bus_.

The system used to boot the Windows Boot Manager, which then would boot my system. (The boot manager had 3 options of which ONLY the default selection boots my system.)
When the Windows booted, I have the following 3 partiton configuration spread across 2 physical drives on the Primary IDE bus:

Primary IDE Drive (Original Drive--> 13GB)
1 h[LIST]
[*]idden primary partition (old drive C: before I got my new drive...not used anymore)
[*]an
[/LIST]extended partition with my Drive E: (my Windows system)

Secondary IDE Drive (160GB)
The 2nd drive has my partitions C: in a primary partition and D: in the extended partition area

The system has lost the MBR.

I believe that I can restore the MBR, But I believe it will restore to its native state.

***_1st, some history, then a question?_***
**History:** Years ago, my system started as a Win98SE on Drive C: It was upgraded when I repartitioned and install XP into Partition E: in the extended area. SO, upon completion, I had Win98SE on drive C: on a Primary partition, and in the extended area on that drive I had windows drives D: and E:.

When space was needed, I added a 2nd drive to the Primary IDE bus, copied the contents of Drive C: and D: to the new drive; and hid the old Drive C:

When I booted, everything was where I expected and XP has run happily for 6 years.

**Question:** If I restore MBR, how will the PC know to pass control to the Windows Boot Manager? What am I going to need to know and what will I need to do???

---

### Post by dcstar on 2009-02-27
> **gcmartin said:**
> I have a 2 drive system on the _Primary IDE bus_.

The system used to boot the Windows Boot Manager, which then would boot my system. (The boot manager had 3 options of which ONLY the default selection boots my system.)
........
**Question:** If I restore MBR, how will the PC know to pass control to the Windows Boot Manager? What am I going to need to know and what will I need to do???

You know, perhaps you would have better luck posting a question about WINDOWS in a WINDOWS forum as this seems to have nothing whatsoever to do with Ubuntu Linux.

---

### Post by gcmartin on 2009-02-27
Always a wise guy somewhere.

My problem happened as a result of a Ubuntu install in the freespace on Drive 2.

I don't see "blaming" an OS as necessary to pose a question for assistance. My current issue will allow me to see the boot manager and within that boot manager I will add the necessary entry to allow Ubuntu to boot. I figured this was the proper area to pose this question as it would bring laughter in the MS community if I hinted that this resulted after a UBUNTU install.

Now, manbe someone can help me, since we know how I got here.

Is this the proper sub-area of the forum to post this question?

---

