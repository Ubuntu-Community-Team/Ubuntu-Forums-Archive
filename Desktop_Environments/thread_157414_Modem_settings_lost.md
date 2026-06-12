---
title: "Modem settings lost"
date: 2006-04-09
forum: Desktop Environments
---

### Post by rockyredhead on 2006-04-09
In 3 days I am due to drive a long way and deliver a computer to my cousin whom I recommended linux to.  Everything was working okay.  In setting up another modem for myself I believe I have inadvertently wiped out the modems settings for the modem for the machine I am delivering.(I know - I should not have used the newer modem on this machine)  The older modem is an external serial  motorola 28.8. I have several init strings recorded for it from earlier windows days.   Currently network settings will not detect the modem though lights on the modem flashduring detection.  The modem is on port ttyS0.
as root dmesg | grep ttyS gives:
[42946.180000] ttyS0 at I/O 0x3f8 (irg =4) is a 16550A
[42946.183000] ttyS0 at I/O 0x3f8 (irg =4) is a 16550A
I do not know is this is some kind of conflict situation - and if so how to resolve it.

I found advice on init strings for breezy5.10 which suggested editing wvdial.conf.
and or gnome-ppp.  I cannot find either of these.  The only wvdial thing is a binary
wvdialconfig which is of course not editable.  I can only assume updates have removed the wvdial.conf as a security measure.  All I think I need to do is get the modem initialized with the right string set in its flash memory - to resolve the problem.  But I cannot find anything to do this in the current setup.
My cousin has access to someone who can sort out windows problems but not linux I expect.  I could get around this by putting xp on this machine but it would be 1/shameful 2/expensive (buy Xp.  buy bigger hd.  buy lots more memory) and 3/Give money to ms

I feel really in a bind.  I took holidays to deliver this machine and I have mucked things up badly.

---

### Post by rockyredhead on 2006-04-11
I made a modem appeal on a local user list and have sourced two modems which have enabled me to get the machine for my cousing working and also my desktop.
(unused ext 56k dynalink serial and a used commercial robotics modem.
Panic over!

---

