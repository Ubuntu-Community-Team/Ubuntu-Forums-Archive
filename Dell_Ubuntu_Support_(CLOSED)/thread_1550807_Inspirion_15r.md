---
title: "Inspirion 15r"
date: 2010-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by caarlos0 on 2010-08-11
I've been thinking to buy a Dell Inspirion 15R, with Core i5.

someone have one?

any issue?


sorry my english, tnx :)

---

### Post by xircon on 2010-08-11
I have a Inspiron 15R N5010:

Initial problems with wireless (now solved, there was a new release of the Broadcom-sta drivers).

The ATI graphics support is not spectacular.

Good fast machine, nice keyboard and a large hard drive, generally very happy with it.

---

### Post by caarlos0 on 2010-08-11
issues with Dell Wireless™ 1501 Half Mini Card (802.11n)?

The video of this laptop is Intel Integrated...

[http://configure.la.dell.com/dellstore/config.aspx?c=br&cs=brdhs1&l=pt&oc=ANI15RAP32&s=dhs](http://configure.la.dell.com/dellstore/config.aspx?c=br&cs=brdhs1&l=pt&oc=ANI15RAP32&s=dhs)


thanks

---

### Post by xircon on 2010-08-12
Yes, mine is a slightly higher spec.  Yes, the DW1501 did not work initially, but broadcom-sta v5.10.91.9.3-3 was released and now no problems.

Oh, suspend to ram doesn't work either, forgot about that :)

---

### Post by kushelmex on 2010-08-17
I have an Inspiron 15 r , everything its working fine . Wifi is working with the restricted drivers. Suspend to ram working normally . No problems with Ubuntu 10.04.

---

### Post by sandy8925 on 2010-09-06
my friend has an inspiron 15r and we tried to install ubuntu yesterday - BIG problem thanks to dell and/or windows 7.

installation worked fine - could boot ubuntu after install and everything was fine. was able to boot windows 7 properly as well - however on restarting, grub was messed up,there was no menu only a message saying modules not found - setup grub again using live cd - and was able to boot normally into ubuntu. booting into windows also worked perfectly as well - once again after restarting from windows grub was again messed up.

conclusion - F**K you windows.why the hell is it messing up grub? 

and then decided to restore normal windows bootloader - since we're able to boot into windows we try using bootrec and guess what - the f**king thing doesn't exist. and it doesn't exist in the recovery cd (drivers and utilities) either - so now we have to wait for 3-4 days for a windows installation dvd which should have been delivered along with the laptop itself.

basically windows and dell are at fault for: 
1. making it extremely difficult to install any other os
2. NOT providing any way to recover the system - why the hell can't windows 7 have bootrec? it's not the whole damn operating system it's only for fixing the boot record - why the hell does it have to be only in the recovery dvd (which is not provided at all nowadays) and NOT in windows?

Now my friend is thinking "why did I try to install Ubuntu? shouldn't have done it at all." so once again ubuntu gets the blame for shitty windows 7 problems.

any suggestions/links for installing ubuntu WITHOUT having windows 7 mess up everything?

---

### Post by xircon on 2010-09-06
Remove Dell Datasafe, it is a royal PITA.  It writes to the Master Boot Record apparently, then re-install grub.

---

### Post by jcolyn on 2010-09-06
> **sandy8925 said:**
> 

and then decided to restore normal windows bootloader - since we're able to boot into windows we try using bootrec and guess what - the f**king thing doesn't exist. and it doesn't exist in the recovery cd (drivers and utilities) either - so now we have to wait for 3-4 days for a windows installation dvd which should have been delivered along with the laptop itself.

You are responsible for building a set of recovery disks from the recovery partition. Very easy to do. It's called backing up...

Anytime you make major changes you should always BACKUP.....

---

### Post by caarlos0 on 2010-09-13
ok.

I bought the laptop.

Everything works fine, include suspend2ram, hibernate, etc...

Buuut, the same problem with windows 7 ****.

Tonight i'll try to remove the ****ing dell datasafe. That crap is useless even.

tnxs to all.

cheers

---

### Post by caarlos0 on 2010-09-14
I removed the dell datasafe, and WIN.

now, everything is ok..

thanks to all =)

---

### Post by crackbuntu on 2010-09-14
running ubuntu 10.4.1 lucid lynx ( sorry if i misspelt it) on oldschool dell inspiron 1525.

working fine, i am new to ubuntu :) and i fell in love with it!

can anyone write to me, a good stuff to start with on ubuntu?

like softwares, emulators, themes :) etc.

thanks in advance :)

CR4CKBUNTU
:-j

---

### Post by sandy8925 on 2010-09-17
@crackbuntu - install gnome-mplayer if you're using gnome or kmplayer if you're using kde.they'll play any videos or audio files that you have. try amarok for music. learn to program! (use python for easy introduction)

---

### Post by sceo on 2011-01-04
Got my 15R yesterday and it seems to be working quite well under Ubuntu 10.10 (Maverick) 64-bit.  

Have only tried to suspend once, though that didn't fully work for me.  I have 6GB RAM and a 7GB swap partition since I wanted to have the option to hibernate.

I have the Intel graphics card - works fine with Compiz & multiple monitors, except since my monitors are not the same size, "maximize" puts it beyond the screen edge in my smaller (laptop) monitor.  (I read somewhere that I believe there's a patch for the Intel driver to fix this but now I can't find it.)

I have the Kensington SD100 dock and so far everything seems OK with it.  Last night I was having some flakiness with the usb-to-ethernet, but it's better today.  Similarly, yesterday's boot didn't like the audio, but now it detects and plays through the dock's audio fine.

I got it with the Blu-Ray drive; someday I'll try and play Blu-Rays through Ubuntu.

---

