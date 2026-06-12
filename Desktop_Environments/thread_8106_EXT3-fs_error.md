---
title: "EXT3-fs error"
date: 2004-12-14
forum: Desktop Environments
---

### Post by sharingan on 2004-12-14
hi!

first of all, i'm not sure if this the right forum to post this issue. please redirect me to the right place if necessary...

now the problem...

i have ubuntu installed in a laptop for a month. there was a lack of power supply yesterday and everything is working slower. i don't know if that could be the explanation...
when i shut down the computer i see line after line th following error:

[FONT=Courier New]EXT3-fs error (device hda2) in start_transaction: Journal has aborted[/FONT]

i have been working with linux for almost a year and this is the first time i see such a message.

i have no idea how to proceed... i'm wondering if i should re-install ubuntu... but there should be another solution!!

thnx for any tip or help!!

---

### Post by sharingan on 2004-12-19
if someone is interested, this is finally what i did:

[list]
[*]start Ubuntu in the safe mode
[*]check the filesytem with [FONT=Courier New]fsck.ext3 -f /dev/hda2[/FONT]
[*]reboot
[*]install the S.M.A.R.T. Monitoring Tools
[*]switch on the disk support: [FONT=Courier New]smartctl -s on /dev/hda[/FONT]
[*]execute an automatic test:  [FONT=Courier New]smartctl -t long /dev/hda[/FONT]
[*]the results of this test are left in an internal register: [FONT=Courier New]smartctl -l selftest /dev/hda[/FONT]
[*]a report can be found executing [FONT=Courier New]smartctl -H /dev/hda[/FONT]
[/list]

---

