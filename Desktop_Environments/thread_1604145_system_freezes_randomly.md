---
title: "system freezes randomly?"
date: 2010-10-23
forum: Desktop Environments
---

### Post by finalni on 2010-10-23
I installed ubuntu 10.04 two days ago and after few minutes or hours it completely freezes - mouse doesn't respond, ctrl+alt+f1 and magic sysrq don't work, so I have to reboot. This usually happens while using opera & amarok..

pc conf: P4 2.4 GHz, 1.28 GB RAM, asus P4S800D-X, ATI Radeon 9200

dual boot with Win7

---

### Post by sikander3786 on 2010-10-23
Hi and Welcome to the forums.

It is not easy to track problems like those so you'll need to be a bit patient throughout.

Can you please confirm it by using some other Web Browser and Media Player for the time being so Opera and Amarok can be ruled out.

Does Windows 7 run fine on the same hardware?

If I was in the same situation, probably at first I would've ruled out RAM by running memtest from Grub menu.

Did you install proprietary drivers for you ATI card? Which version?

For troubleshooting, here is some wealthy information.

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by ubutu on 2010-10-23
Delete Win7: Problem solved.:D

---

### Post by finalni on 2010-10-23
since I completely forgot about drivers :oops: while trying to install them, I'll post only a partial answer:
win7 works fine, mostly.. few times it did behave unusually, foobar would crash and I could't run any program, there was a message "not enough system resources" or sth like that.

I already ran memtest for 2hrs and it found no errors. If I understand it well, that doesn't mean much, so I tried running the system with only two ram modules and it froze no matter which two I used.. and just recently it froze while using Rhythmbox and Firefox (instead of Amarok and Opera), at first the screen and mouse froze and the music stopped playing as well (usually it would all stop at once).

not sure how to test if motherboard's fine

:-?

---

### Post by finalni on 2010-10-24
I somehow managed to install drivers for ATI card and everything seems to work fine now, thank you very much for your help :)

---

### Post by pveurshout on 2010-11-13
Good to hear your problems are solved :) I'm having the same problem and although I'm not entirely sure, it definately seems related to using Opera in my case. Will try without and see what happens. I'm using an nVidia card, by the way, with the proprietary drivers installed.

---

