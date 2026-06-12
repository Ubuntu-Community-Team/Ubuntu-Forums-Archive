---
title: "is this dvd disc kaput?"
date: 2009-04-24
forum: General Help
---

### Post by logos34 on 2009-04-24
I tried burning ~1.3 GB data to a NEW dvd-rw last night (w/ k3b).  Finished writing successfully, but failed verify (unreadable sectors).  I thought it might be due to the fact that the drive was pretty hot--I'd been doing a lot of cd burning and erasing before.  When a second dvd failed to even begin writing, I quit for the night.  But here's what the first disc is showing:

> $ dvd+rw-mediainfo /dev/dvd
INQUIRY:                [ASUS    ][DRW-1608P2      ][1.41]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         14h, DVD-RW Sequential
 Media ID:              CMCW02      
 Current Write Speed:   2.0x1385=2770KB/s
 Write Speed #0:        2.0x1385=2770KB/s
 Write Speed #1:        1.0x1385=1385KB/s
 Speed Descriptor#0:    00/2298495 R@2.0x1385=2770KB/s W@2.0x1385=2770KB/s
 Speed Descriptor#1:    00/2298495 R@1.0x1385=1385KB/s W@1.0x1385=1385KB/s
READ DVD STRUCTURE[#10h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2298496*2KB=4707319808
READ DVD STRUCTURE[#0h]:
 Media Book Type:       32h, DVD-RW book [revision 2]
 Last border-out at:    2045*2KB=4188160
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    2
[COLOR="Red"] State of Last Session: reserved/damaged[/COLOR]
 "Next" Track:          2
 Number of Tracks:      2
READ FORMAT CAPACITIES:
 formatted:		132800*2048=271974400
 00h(800):		2297888*2048=4706074624
 10h(10):		2297888*2048=4706074624
 15h(10):		2297888*2048=4706074624
READ TRACK INFORMATION[#1]:
 Track State:           complete incremental
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            132800*2KB
READ TRACK INFORMATION[#2]:
[COLOR="Red"] Track State:           invisible incremental,damaged[/COLOR]
 Track Start Address:   161488*2KB
 Next Writable Address: 161488*2KB
 Free Blocks:           2136400*2KB
 Track Size:            2136400*2KB
FABRICATED TOC:
 Track#1  :             14@0
 Track#AA :             14@4294770689
 Multi-session Info:    #1@0
READ CAPACITY:          4294770689*2048=8795690371072

So does this mean the disc is ruined, and I should forget trying to save it with full format, 'dvd+rw-tools /dev/dvd -blank=full'?

---

### Post by cariboo on 2009-04-24
If the disk doesn't have any large scratches, I can't see sny reason why you shouldn't blank the dvd.

---

### Post by LowSky on 2009-04-24
dvd drives do go bad, a friend of mine goes through one about every two years because of his high use and I've had one go bad, with about 4-5 years of use on it.,

---

### Post by logos34 on 2009-04-24
ok, I just finished blanking it (it's a 2x, so it took 30 min!)...I looks like it may have survived:

> $ dvd+rw-mediainfo /dev/dvd
INQUIRY:                [ASUS    ][DRW-1608P2      ][1.41]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         14h, DVD-RW Sequential
 Media ID:              CMCW02      
 Current Write Speed:   2.0x1385=2770KB/s
 Write Speed #0:        2.0x1385=2770KB/s
 Write Speed #1:        1.0x1385=1385KB/s
 Speed Descriptor#0:    00/2298495 R@2.0x1385=2770KB/s W@2.0x1385=2770KB/s
 Speed Descriptor#1:    00/2298495 R@1.0x1385=1385KB/s W@1.0x1385=1385KB/s
READ DVD STRUCTURE[#10h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2298496*2KB=4707319808
READ DVD STRUCTURE[#0h]:
 Media Book Type:       32h, DVD-RW book [revision 2]
 Last border-out at:    2045*2KB=4188160
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ FORMAT CAPACITIES:
 unformatted:		2297888*2048=4706074624
 00h(800):		2297888*2048=4706074624
 10h(10):		2297888*2048=4706074624
 15h(10):		2297888*2048=4706074624
READ TRACK INFORMATION[#1]:
Track State:           invisible incremental
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           2297888*2KB
 Track Size:            2297888*2KB
READ CAPACITY:          0*2048=0

Back to normal I hope.

I guess the drive was just too hot last night (the disc came out practically smokin'). 

then again, it wouldn't surprise me if the drive is slowly failing (has trouble writing dvd+r where it never did before)

---

