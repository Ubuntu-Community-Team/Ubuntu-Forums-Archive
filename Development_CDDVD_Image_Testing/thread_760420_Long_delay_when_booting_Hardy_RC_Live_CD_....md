---
title: "Long delay when booting Hardy RC Live CD ..."
date: 2008-04-20
forum: Development CD/DVD Image Testing
---

### Post by Waka Jawaka on 2008-04-20
[FONT="Courier New"][SIZE="2"]
**Hardware:**

Type         : HP Notebook nx5000 (2004)
CPU          : 1.6 Ghz Intel Centrino
Chip Set     : Intel 855GM
RAM          : 2 GB
HDD          : 160 GB Seagate PATA
Optical Drive: HL-DT-ST DVD+RW GCA-4040N
Floppy Drive : None, neither built-in nor attached

In the BIOS the boot order is set to:

Notebook Multibay  : first
Notebook Hard Drive: second

There is no dedicated menu item for a Floppy drive
in the BIOS.


**Problem:**

When I tried to boot the Hardy Beta Live CD a few days ago,
the procedure seemed to get stuck right in the beginning.
For several minutes all I got to see was the Ubuntu splash
with a busy bar. The LED of the CD drive was permanently
on. As there was no audible activity from the CD drive I
thought the downloaded ISO or the CD might be corrupt and
I gave up.

Yesterday I downloaded the latest Hardy RC. I checked the
ISO Hash and burned the CD with conservative 8x speed to
make sure. This time I gave the boot procedure a little
more time and I found out that it actually hasn't got
stuck indefinitely. It comes back to life and loads the
system correctly after a very long delay.

Booting from the Hardy RC Live CD this is what happens
after the initial language selection ...


- 0.00  Loading Linux Kernel (progress bar)

- 0.05  Ubuntu splash (busy bar)

- 2.30  Blank screen (blinking cursor)

- 3.45  [ID] Buffer I/O Error On Device FD0, Logical Block 0

- 5.00  [ID] Buffer I/O Error On Device FD0, Logical Block 0

- 6.15  CD activity resumes and boot continues normally


... it seems, the 6 minute delay is caused by the hardware
detection which is looking for a non-existent Floppy drive.
Neither Feisty nor Gutsy show this behaviour when I boot
their Live CDs on my notebook.

As I don't want to install Hardy to my HDD before the final
release comes out, I cannot say if the problem persists in
a proper installation. But even when booting from a Live CD,
which ought to be a showcase for Ubuntu, such an unnecessarily
long delay is unacceptable. I hope someone finds the time to
look into this before the final release comes out.






[/SIZE][/FONT]

---

### Post by PmDematagoda on 2008-04-20
I have moved this thread to the Development CD/DVD Image Testing section where it may receive better attention.

About the splash problem did you try booting with "nosplash"?

Oh and one thing, while you may consider 8x to be conservative, in actuality it isn't for a Live CD where it is recommended to be burnt at a speed of 4x or less, did you try burning the CD at a speed of 4x or less and then try again?

---

### Post by Waka Jawaka on 2008-04-20
> I have moved this thread to the Development CD/DVD Image Testing
> section where it may receive better attention.

... thanks for this. I hope they can do something about the problem
before the final release of Hardy comes out.

> About the splash problem did you try booting with "nosplash"?

... yes, I did. But it didn't make a difference. The boot time was
still extremeley long.

> Oh and one thing, while you may consider 8x to be conservative,
> in actuality it isn't for a Live CD ...

... I know. I would have chosen a slower speed. But I burned the
CD on a Windows machine using Nero, which strangely didn't
offer any slower speeds. 8x was the slowest available.

---

### Post by PmDematagoda on 2008-04-20
Did you check the CD using the CD check utility provided?

---

### Post by Waka Jawaka on 2008-04-20
> Did you check the CD using the CD check utility provided?

... Nero does an automatic CD verification. I didn't run any additional tools
to check the CD. But I don't think the problem is caused by a corrupt ISO
or a corrupt CD. Over the past couple of days I've also downloaded and
burned CD and DVD images of Mint and Sidux which all worked fine. It
would be a strange sort of corruption that shows exactly the same
error with two different ISOs and two different CDs (beta and rc).
:-)

---

### Post by orange2k on 2008-04-20
I have a similair problem with the RC. I burned the 64-bit version (downloaded via bittorent) and did use the CD-check utility and it went fine.

However, even with nosplash option enabled it doesnt boot properly, after a minute or so it stops with some kind of strange text and it continues only when I press ctrl+alt+del. When booting finally comes to an end it reports another error: "internal error - cant initialize HAL"...:(

---

### Post by Waka Jawaka on 2008-04-20
> When booting finally comes to an end it reports another
> error: "internal error - cant initialize HAL"

... I'm not sure the Development CD/DVD Image Testing group are the
right people to deal with issues like these. Your HAL problem and the
hardware detection issue I'm having with a non-existing Floppy drive
seem to be related to the new kernel. Eventually reports like these
will end up with the right people ... hopefully in time for the new
release.

---

### Post by wgrant on 2008-04-22
Can you please try booting with clocksource=hpet added to the kernel line? That fixed the problem for a number of people with similar hardware.

---

### Post by Waka Jawaka on 2008-04-23
Thanks for the hint, William.

I can't alter the kernel command line at the moment
as I'm still only booting from the 8.04
Release Candidate CD.

Tomorrow I'll download the final Ubuntu release and
install it properly on my hard drive. If the
problem still persists I will try out
"clocksource=hpet".

I'll let you know whether this solves the problem
or not.

---

