---
title: "Dell Inspiron Mini 9 Dual Boot"
date: 2008-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by notwen on 2008-10-28
I just ordered my mini and was able to get this maxed out spec for right at $350 shipped(online coupons rule).  =]  Unfortunately, the coupon only worked w/ the XP installed models.

Once I receive it, I'm wanting to partition the 16GB SSD between the pre-installed Windows XP and Ubuntu(Dell's Mini 9 image) and was wondering if these stripped down versions had a minimum partition size as well?  Also do these Mini 9s also come w/ the restore partitions like my Inspiron 1420n?  Just curious as to how difficult of a time I'm going to have to get everything setup the way I want.

From what I've seen in threads regarding the Inpsiron Mini 9s, I should be able to use the image released by Dell to cover the Ubuntu side of things, but was curious if this image would simply restore the system to factory defaults or would it also give me the option of setting up my partition table to setup my dual boot?  All of the custom Ubuntu images Dell has released for their N series models only wipe and restore to factory defaults that I've tried(Feisty and Hardy).

Specs are as follows:
> -- Inspiron Mini 9 (910) Laptop: Intel Atom Processor N270 (1.6GHz/533Mhz FSB/512K cache) No DVD or CD Drive
-- 4 Cell Primary Battery
-- McAfee Security Center, 30 Day
-- 30W AC Adapter
-- Software
-- No WAN card Slot
-- Obsidian Black
-- Dell Support 2.0 Software
-- Processor Label
-- Intel Integrated Graphics Media Accelerator 950
-- Service Software
-- Information
-- Dell Solution Center Software
-- Information
-- Operating System DVD
-- Processor Label
-- Integrated 1.3M Pixel Webcam
-- Shipping Material
-- 1 GB DDR2 SDRAM 533MHz (1 DIMMs)
-- Miscellaneous
-- Genuine Windows XP Home
-- Glossy 8.9 inch LED display (1024X600)
-- Notebook Keyboard
-- Microsoft Works 9.0
-- Built-in Bluetooth 2.1 capability
-- 16 GB Solid State Drive
-- Adobe Acrobat 8.1 Reader
-- Operating System DVD
-- ISP Search Assist
-- Wireless 802.11g Mini Card

---

### Post by notwen on 2008-10-30
*bump*

> Once I receive it, I'm wanting to partition the 16GB SSD between the pre-installed Windows XP and Ubuntu(Dell's Mini 9 image) and was wondering if these stripped down versions had a minimum partition size as well? Also do these Mini 9s also come w/ the restore partitions like my Inspiron 1420n?

---

### Post by Rallg on 2008-11-01
On my mini 9 (with XP, 16 G): I installed Ubuntu 8.10 usung unetbootin. Originally, I gave Ubuntu 4 G. I don't need many storage-hungry programs, and I don't work with big files, so it would be possible to squeeze ubuntu into about 2.6 G with enough room to download updates and do some work. No swap. No separate /home partition.

I installed Grub to the Ubuntu partition (not the root of the hard drive), then used XP's own bootloader to load Ubuntu. This method is described elsewhere on the Internet.

I have the mini 9 and a Dell Vostro 1000 regular laptop. The Vostro came with a small Dell partition at the start of the drive, and so does the mini 9. The Vostro has a Windows restore partition, but the mini 9 does not. My mini 9 came with XP reinstallation CD, if I ever need it (I would also need to get a USB CD drive). Also, the i386 folder (which contains most of the stuff needed to reconstruct XP) is pre-installed.

If you do not intend to use XP much, consider turning off its System Restore feature (to save drive space) and shrink it to 6 to 8 G. That leaves a healthy amount of drive for Ubuntu.

Also consider upgrading your RAM to 2G if you have no swap. I just ordered mine but haven't installed it yet (I am told it works). Dell cannot ship the mini 9 that way.

---

