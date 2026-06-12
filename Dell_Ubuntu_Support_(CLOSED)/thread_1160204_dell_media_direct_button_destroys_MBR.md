---
title: "dell media direct button destroys MBR"
date: 2009-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by levymichel on 2009-05-15
T've heard that pressing the dell media button can modify the MBR.
Did you know if it's possible to inactivate this button : more precisely, 
is it safe to use the command "dellMediaDirectCtl -r" to unactivate this button ? 
I am unable to find a clear explanation of the effect of this command of the package libsmbios-bin.

---

### Post by coffeeaddict22 on 2009-05-16
Sounds like an urban myth.  For a start, Linux file permissions would normally be strong enough to make this not possible.
libsmbios is part of a package that allows updating your BIOS from inside Linux.  I can vouch for it working, but you need to be a bit careful playing- read [this]("http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate") at least before you get too carried away, and make sure you've got a system that it is known to work for.

I guess, if you push a button during a BIOS upgrade, anything could happen, but then you'd have to be pretty brave to want to find out (or be in need of some expensive bricks)

---

### Post by anjilslaire on 2009-05-17
Actually, it's true that the MediaDirect button can destroy an Ubuntu installation if the system originally had Windows from the factory. It involves a partion that is hidden even from GParted, etc. I successfully wiped it on my 1420 by zeroing the drive before installing Ubuntu.

Generally, what happens is that when pressed, the MediaDirect button overwrites the MBR and causes the system to be unable to boot if Windows is not installed. You can read up on it here:
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
more light reading:
[http://ubuntuforums.org/search.php?searchid=59501151&pp=25&page=1](http://ubuntuforums.org/search.php?searchid=59501151&pp=25&page=1)

---

### Post by Dangger on 2009-09-05
> **anjilslaire said:**
> Actually, it's true that the MediaDirect button can destroy an Ubuntu installation if the system originally had Windows from the factory. It involves a partion that is hidden even from GParted, etc. I successfully wiped it on my 1420 by zeroing the drive before installing Ubuntu.

Generally, what happens is that when pressed, the MediaDirect button overwrites the MBR and causes the system to be unable to boot if Windows is not installed. You can read up on it here:
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
more light reading:
[http://ubuntuforums.org/search.php?searchid=59501151&pp=25&page=1](http://ubuntuforums.org/search.php?searchid=59501151&pp=25&page=1)


How can I find out if it's safe to press? I had windows pre-installed

**Update:** I sometimes press the button by accident, specially when trying to suspend the machine. Because I wasn't waiting for an accident to happen, I pressed it after backing everything up (monthly backup) and it's ok, nothing happened.

---

### Post by RedRat on 2009-09-05
> **levymichel said:**
> T've heard that pressing the dell media button can modify the MBR.
Did you know if it's possible to inactivate this button : more precisely, 
is it safe to use the command "dellMediaDirectCtl -r" to unactivate this button ? 
I am unable to find a clear explanation of the effect of this command of the package libsmbios-bin.

After reading anjilslaire there is the possibility of damage. Unless you have some very clear reason for using it, why would you? It all depends on your willingness to take risks and end up fooling around with a wounded machine. Unless you have some very dire problem, I would leave the damn button alone. Sometimes conservatism can be the best move.

---

### Post by yookoala on 2009-12-02
I have just ruined my MBR by pressing MediaDirect button accidentally.

Oh... I hate reinstalling.

---

### Post by yookoala on 2009-12-02
Fixed.

In my new installation:
1. I used "method 2" to make partitions with MediaDirect CD, which means not using all spaces in harddisk as Windows partition.

2. I minimized the Windows partition. (This is really up to you)

3. My partition table looks like this then:

   /dev/sda1 - somehow used by system. we'd better leave it alone
   /dev/sda2 - Windows
   /dev/sda3 - extended partition. contains the following logical partitons
   /dev/sda4 - empty unused partition
   /dev/sda5 - MediaDirect partition


3. I installed Ubuntu in 3 new partitions I made out from /dev/sda4. I left the last partition (MediaDirect partition) alone. So my partition table looks like this:

   /dev/sda1 - somehow used by system. we'd better leave it alone
   /dev/sda2 - Windows
   /dev/sda3 - extended partition. contains the following logical partitons
   /dev/sda4 - /boot
   /dev/sda5 - SWAP
   /dev/sda6 - /
   /dev/sda7 - MediaDirect partition


4. When installing Ubuntu, I installed GRUB to /dev/sda2

5. After my installation, everything looks fine!!!!

---

