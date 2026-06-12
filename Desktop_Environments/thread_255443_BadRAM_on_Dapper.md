---
title: "BadRAM on Dapper"
date: 2006-09-11
forum: Desktop Environments
---

### Post by rodrigochinaski on 2006-09-11
Greetings.

My laptop has some bad areas in memory, so I need a badram kernel patch to workaround this problem. 

Unfornately, i didn't find a patch that applies to the shipping linux-source package. 

So I ask:

1- Is there a BadRAM patch that I can apply flawlessly to the linux-source-2.6.15-26.46 shipped in ubuntu?

in case of negative answer, what is the best solution (meaning not modifying so much ubuntu's defaults):

- Use debian unstable's linux-source-2.6.17-8 package?
or
- Use a vanilla linux tree 2.6.17.13 fetched from ftp.kernel.org?

---

### Post by tipp98 on 2006-12-07
I am in the same boat. Whenever I get to writing the partition information to the disk my laptop locks up. It has 64MB of onboard memory and 128MB of removable memory. You guessed, the problem is in the 64MB portion.

---

### Post by digbysellers on 2007-02-05
Anyone have an answer to this?

---

### Post by broy55 on 2007-02-20
I have the same problem. Damn Gateway laptops, has 512mb on-board memory and its bad at the 381mb mark. I was able to install Mandriva using "mem=380mb" but then I waste 132mb of ram and no hopes for upgrading.

---

### Post by Gray Green on 2007-04-03
I've got fujisu fmv-book with broken 128M RAM stick. I tried to search some info and found one message talking about badram-patch. Then I have searched info for badram patch for Breezy or Dapper and found only for _[Warty]("http://packages.ubuntulinux.org/warty/devel/kernel-patch-badram")_ and nothing about later distros. Then I thougt, may be it included allrady into kernel. So, I tested my book whith memtest for 3 or 4 (!) days (at the end of test it still contunued found bad bits from time to time).It gave me a table of 20 (10 pairs) hexadecimal numbers, which I inserted into menu.list, updated grub and rebooted, trying to not breething :) ... :lolflag: 
May be, it was a gluk, bat my notebook worked yesterday about 2 hours whithout any errors. Now, how to test if patch is in the kernel and working or not?
PS: I have installed a Breezy (5.10) distro whith default kernel (2.6.12-9-386)
PPS: sorry for my English, hope you understand everything.
PPPS: Hey, I memtested it for a week, updated menu.list and now it's about 4 days switched on with firebird, xchat and... screensaver 8-) working without any errors!
Good luck!

---

