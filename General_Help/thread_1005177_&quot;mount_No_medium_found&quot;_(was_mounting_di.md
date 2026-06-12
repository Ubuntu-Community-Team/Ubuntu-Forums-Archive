---
title: "&quot;mount: No medium found&quot; (was mounting discs before, now it isn't.)"
date: 2008-12-08
forum: General Help
---

### Post by Th3Professor on 2008-12-08
I was transferring backed-up data from CDs/DVDs (sr0 (scd0)) to the computer, it worked fine for several discs then stopped working. I tried mounting previously mounted discs and it wouldn't work (although it did previously).

I receive:
"mount: No medium found"
when attempting to mount discs now.

I've made no changes in any settings.

dmesg | grep sr0 shows the following, I'll include the head/tail of the list...

head:
```

9:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[42986.725852] sr 9:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[42986.725858] end_request: I/O error, dev sr0, sector 1342968
[42986.725863] Buffer I/O error on device sr0, logical block 167871
[42993.208661] sr 9:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[42993.208670] sr 9:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[42993.208673] sr 9:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[42993.208679] end_request: I/O error, dev sr0, sector 1342968
[42993.208684] Buffer I/O error on device sr0, logical block 167871
[43000.765951] sr 9:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

```tail:
```

[47865.949976] sr 9:0:0:0: [sr0] Sense Key : Medium Error [current] 
[47865.949980] sr 9:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[47865.949984] end_request: I/O error, dev sr0, sector 1236600
[47865.949989] Buffer I/O error on device sr0, logical block 154575
[47866.526514] sr 9:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[47866.526522] sr 9:0:0:0: [sr0] Sense Key : Medium Error [current] 
[47866.526527] sr 9:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[47866.526531] end_request: I/O error, dev sr0, sector 1236600
[47866.526536] Buffer I/O error on device sr0, logical block 154575
[48157.753773] sr 9:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[48157.753780] sr 9:0:0:0: [sr0] Sense Key : Medium Error [current] 
[48157.753784] sr 9:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[48157.753788] end_request: I/O error, dev sr0, sector 1223520
[48157.753793] Buffer I/O error on device sr0, logical block 305880
[48157.753797] Buffer I/O error on device sr0, logical block 305881
[48157.753802] Buffer I/O error on device sr0, logical block 305882
[48157.753804] Buffer I/O error on device sr0, logical block 305883
[48157.753807] Buffer I/O error on device sr0, logical block 305884
[48157.753809] Buffer I/O error on device sr0, logical block 305885
[48157.753811] Buffer I/O error on device sr0, logical block 305886
[48157.753814] Buffer I/O error on device sr0, logical block 305887
[48157.753816] Buffer I/O error on device sr0, logical block 305888
[48157.753818] Buffer I/O error on device sr0, logical block 305889

```How do I get the computer to mount discs again?

Thanks!

EDIT/UPDATE:

ls -la on /media shows this:
```

-rw-r--r--  1 root root     0 2008-12-07 13:44 .hal-mtab
-rw-------  1 root root     0 2008-12-07 21:41 .hal-mtab-lock

```Should I "rm" the lock file and/or both of those files?

EDIT2:
Nevermind on the .hal-mtab-lock (rm'ing didn't make a difference... still no mounting).
(I put them back... figured they're needed.)

EDIT3:
Okay, lshal shows the following on scd0:
```

access_control.file = '/dev/scd0' (string)
block.device = '/dev/scd0' (string)

```EDIT4:
I rebooted... now I can mount CDs/DVDs again, however... now my LVM's not working. Any ideas? Do a fsck?

EDIT5:
Okay... this is very odd. I did another reboot, and now LVM's working, as is the DVD drive, etc. However, I ended up getting *tons* of errors scrolling by on boot, including the cd/dvd drive i/o errors, and now i/o errors on USBs, etc. more errors. Yet, everything appears to be working.

Is there something buggy with the most recent kernel? This is pretty frustrating.

---

