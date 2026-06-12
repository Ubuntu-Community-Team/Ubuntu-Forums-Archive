---
title: "runing dapper flight 6 still no sound"
date: 2006-04-23
forum: Desktop Environments
---

### Post by runefreak on 2006-04-23
i recently installed dapper drake flight 6 and still have no sound and it still will not detect  my ad1881 intgrated sound card .mark@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:03.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
mark@ubuntu:~$

---

### Post by bb002 on 2006-04-24
Intel Corporation 440LX/EX? that was the chipset of my old 266Mhz Pentium 2 MB.

My guess is your ad1881 is on the ISA bus (couldn't get a definitive answer on the web, too much win98 driver crap). If my guess is right you will require "isapnptools" to find and setup isa devices. IMO it would be much easier to disable the device if it is on-board or remove it if it is an add-on card and buy a cheap Creative PCI card for $20-30. Plus the card will kick the crap out of the ad1881 card and will be automagically setup.

my pII mb had a yamaha oplsa-3 (something like that...), I tried forever and failed to get it working proberly. I had issues with applications seeing it only the kernel and alsa would see it.  I finally replaced it with a Creative Sound Blaster Live! 24-bit PCI Sound Card" for $25 and it that sucker is still better that my current pcs on-board audio.

---

### Post by runefreak on 2006-04-24
ok i am not giving up yet i downloaded asipnptools but the install instructions are so patheticly vague i don`t understand them how do i install it?

---

### Post by Sef on 2006-04-24
There is a bug in Dapper Beta which kills sound for lots of people.   It has been reported.

---

### Post by bb002 on 2006-04-24
Yeah. the vague instructions were my problem. i finally got as far as telling isapnp what resources my card was using but it gave me 4 choices for each resource and there was like 6 of those. I had no idea, the bios didn't tell me and i didn't know how to probe the card to find out, i thought that what the isapnptools was supposed to do!!

So if you are really determined to go through with this I'm afraid I won't be of much help. I tryed looking around but i didn't find much. And all i can remember is 3 steps.

```

sudo -i
pnpdump > /etc/isapnp.conf

```
sudo -i will make you root.
pnpdump scans for isa devices and probes for possible resource options.
now you need to know what resources your card uses and uncomment those lines in isapnp.conf and i can't remember what's next after that.

---

### Post by runefreak on 2006-04-24
maybe someone else can make sense of this  i can`t
this is what i got from pnpdump
 $Id: pnpdump_main.c,v 1.27 2001/04/30 21:54:53 fox Exp $
# Release isapnptools-1.26
#
# This is free software, see the sources for details.
# This software has NO WARRANTY, use at your OWN RISK
#
# For details of the output file format, see isapnp.conf(5)
#
# For latest information and FAQ on isapnp and pnpdump see:
# [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/)
#
# Compiler flags:  -DREALTIME -DHAVE_PROC -DENABLE_PCI -DHAVE_SCHED_SETSCHEDULER -DHAVE_NANOSLEEP -DWANT_TO_VALIDATE
#
# Trying port address 0273
# Trying port address 027b
# Trying port address 0283
# Trying port address 028b
# Trying port address 0293
# Trying port address 029b
# Trying port address 02a3
# Trying port address 02ab
# Trying port address 02b3
# Trying port address 02bb
# Trying port address 02c3
# Trying port address 02cb
# Trying port address 02d3
# Trying port address 02db
# Trying port address 02e3
# Trying port address 02eb
# Trying port address 02f3
REALTIME operation timeout exceeded - Switching to normal scheduling
nanosleep failed: Interrupted system call
# Trying port address 02fb
# Trying port address 0303
# Trying port address 030b
# Trying port address 0313
# Trying port address 031b
# Trying port address 0323
# Trying port address 032b
# Trying port address 0333
# Trying port address 033b
# Trying port address 0343
# Trying port address 034b
# Trying port address 0353
# Trying port address 035b
# Trying port address 0363
# Trying port address 036b
# Trying port address 0373
# Trying port address 0383
# Trying port address 038b
# Trying port address 0393
# Trying port address 039b
# Trying port address 03a3
# Trying port address 03ab
# Trying port address 03b3
# Trying port address 03bb
# Trying port address 03e3
# Trying port address 03eb
# Trying port address 03f3
# No boards found

---

### Post by runefreak on 2006-04-25
guess microsoft is the only one who can make my soundcard work
i thought linux was superior?

---

### Post by Sef on 2006-04-25
> guess microsoft is the only one who can make my soundcard work
i thought linux was superior?

1) Dapper is still beta and there has been lots of problems with sound.  

2) If you feel that Windows is a better choice for you, then use it.

3) If you want to know how I solved my sound problems, click on the link below.

[http://ubuntuforums.org/showthread.php?t=160576]("http://ubuntuforums.org/showthread.php?t=160576")

You may need to adjust my directions a bit as to what to comment.

---

### Post by runefreak on 2006-04-27
nice to know that the support here is so lacking all these people here and no one will help me  it seems like the thing that is holding ubuntu back is the lack of dedication in support and i know i am not the first to have this problem
 i have found close to thirty posts with the same problem and different cards
but the same result little or no effort to help fix the problem .
 you can`t ignore people who need help and expect success.
 my god even Microsoft has decent support at least  .....
 don`t get me wrong i like ubuntu i think it has excellent potential and could even replace windows  but i have tried
breezy,kubuntu,suseand dapper and had this problem with them all i have wasted days of time and lord knows how many Cd's trying to figure this problem out with very little help if i did not know i was not the only one this has happened to it would be different but come on people I'm not i have scoured the web trying to find an answer to no avail and have all but begged for help also to no avail thanks to those who have made an effort to help .but not everyone is a computer programmer and can't fix every problem that may occur by themselves .

---

### Post by Sef on 2006-04-27
Since you are not happy with the support here, click the link below and you can get paid technical Ubuntu support.

[http://www.ubuntu.com/support/supportoptions/paidsupport]("http://www.ubuntu.com/support/supportoptions/paidsupport")

---

### Post by runefreak on 2006-04-27
didnt intend to sound mean or anything just said that seems like very few people seem to care if problems get fixed or not

---

### Post by Sef on 2006-05-01
> didnt intend to sound mean or anything just said that seems like very few people seem to care if problems get fixed or not

It is frustrating when you can't get an answer to fix your problem.  I have had that happen to me too.  On here, almost everyone does care, but we are not experts who know everything.  We just use what we know or have read about.

Have you done a clean install with Beta 2?  It has fixed almost all my sound problems.

[http://cdimage.ubuntulinux.org/daily/current/]("http://cdimage.ubuntulinux.org/daily/current/")

---

