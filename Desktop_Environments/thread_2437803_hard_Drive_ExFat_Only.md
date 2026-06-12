---
title: "hard Drive ExFat Only"
date: 2020-02-29
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-02-29
Folks,  I am hoping the knowledgeable Ubuntu users can enlighten me.

A friend of mine is an Ubuntu Mate user, he was having some trouble with an external USB hard drive he purchased recently (cheap and full refund due to problems), it apparently showed up in Windows but not in Ubuntu.  Gparted just seemed to hang, various command line tools were unable to see device.

We tried terminal dd writing zeros to entire drive then trying to create partition table then format, still no luck.

He pointed out instructions received with the device as follows;

>                        [SIZE=3]   [FONT=Arial Unicode MS][FONT=Arial Unicode MS][COLOR=#000000]The drive [/COLOR][/FONT][FONT=Arial Unicode MS][COLOR=#ff0000]can only be[/COLOR][/FONT][FONT=Arial Unicode MS][COLOR=#000000] formatted with [/COLOR][/FONT][FONT=Arial Unicode MS][COLOR=#ff0000]Exfat[/COLOR][/FONT][FONT=Arial Unicode MS][COLOR=#000000] and [/COLOR][/FONT][FONT=Arial Unicode MS][COLOR=#ff0000]cannot be[/COLOR][/FONT][FONT=Arial Unicode MS][COLOR=#9bbb59] formatted in other for mats, suchas NTFS, FAT32, FAT. [/COLOR][/FONT][FONT=Arial Unicode MS][COLOR=#000000]Otherwise it will cause the hard drive t be unusable![/COLOR][/FONT][/FONT][/SIZE]

  



I've not heard such a thing before, can anyone throw some light on this for me?

Geffers

---

### Post by yetimon_64 on 2020-02-29
> **Geoff_Lane said:**
> ...I've not heard such a thing before...
Same here, sounds both an unusual and interesting case.
With respect to...
> **Geoff_Lane said:**
> ...an external USB hard drive...
and
> **Geoff_Lane said:**
> ...can anyone throw some light on this for me?...
**Question:** What is the brand and model number of the device?

Even if we don't know about the issue offhand such details can give a starting point for a bit of research on Google. My first thought is that there may be some built in hardware/firmware protections to force the use of exfat only, though that doesn't fully explain why ubuntu can't even see the device :-k. In which case it would be good to know the make and model even if only to avoid such a device on Linux.

Regards, yeti.

---

### Post by yancek on 2020-02-29
In addition to answering the above questions, which version of windows was it attached to and was it (windows) fully shut down or left in the default hibernated state.  There aren't many (if any) Linux operating systems which have software to access exfat filesystems installed in a default installation.

---

### Post by DuckHook on 2020-02-29
When I hear stuff like this, the first thought that crosses my admittedly paranoid mind is: "is this one of those fake low capacity drives that have had its firmware replaced so as to falsely report higher capacities?" They were a big problem on ebay not so long ago and there are plenty of unscrupulous people still pulling that con.

Such drives may be specially formatted to fool Windows, but won't even be recognized by Linux.

Web searching doesn't reveal much in the way of legitimate drives with such limitations. There are hints of cheap far east drives that do not have the internal circuitry to handle journaling, but that is a head scratcher to me, as journaling is just a data structure like any other. Or is it?

And what would account for its inability to format to FAT or FAT32? They are both non-journaling.

---

### Post by CelticWarrior on 2020-02-29
> **DuckHook said:**
> Such drives may be specially formatted to fool Windows, but won't even be recognized by Linux.

You're probably right, it smells fake.

But why exFAT?
AFAIK, those fakes from years ago were FAT32 (sticks) or NTFS ("HDDs"). So the file systems aren't a limitation for making fakes.:mrgreen:

---

### Post by Geoff_Lane on 2020-03-01
> **yetimon_64 said:**
> Same here, sounds both an unusual and interesting case.
With respect to...

and

**Question:** What is the brand and model number of the device?

Even if we don't know about the issue offhand such details can give a starting point for a bit of research on Google. My first thought is that there may be some built in hardware/firmware protections to force the use of exfat only, though that doesn't fully explain why ubuntu can't even see the device :-k. In which case it would be good to know the make and model even if only to avoid such a device on Linux.

Regards, yeti.

Thank you for prompt reply.

The owner was out today so unable to get details but hopefully tomorrow.

Geoff

---

### Post by Geoff_Lane on 2020-03-01
> **DuckHook said:**
> When I hear stuff like this, the first thought that crosses my admittedly paranoid mind is: "is this one of those fake low capacity drives that have had its firmware replaced so as to falsely report higher capacities?" They were a big problem on ebay not so long ago and there are plenty of unscrupulous people still pulling that con.

Such drives may be specially formatted to fool Windows, but won't even be recognized by Linux.

Web searching doesn't reveal much in the way of legitimate drives with such limitations. There are hints of cheap far east drives that do not have the internal circuitry to handle journaling, but that is a head scratcher to me, as journaling is just a data structure like any other. Or is it?

And what would account for its inability to format to FAT or FAT32? They are both non-journaling.

I wouldn't be surprised at all, it was bought from ebay, ridiculously cheap, in a case and 2TB, he has already been reimbursed and seller didn't want device returned so it is curiosity now - CrystalDiskInfo on Windows 10 apparently reported it as a pretty new drive as very few 'start ups' reported on the smart drive info.

He is out today so I'll get more info tomorrow.

Geffers

---

### Post by DuckHook on 2020-03-01
> **Geoff_Lane said:**
> I wouldn't be surprised at all, it was bought from ebay, ridiculously cheap, in a case and 2TB, he has already been reimbursed and seller didn't want device returned so it is curiosity now - CrystalDiskInfo on Windows 10 apparently reported it as a pretty new drive as very few 'start ups' reported on the smart drive info.

He is out today so I'll get more info tomorrow.

Geffers

Doesn't pass the "smell" test, does it?…

---

### Post by Geoff_Lane on 2020-03-02
> **yetimon_64 said:**
> Same here, sounds both an unusual and interesting case.
With respect to...

and

**Question:** What is the brand and model number of the device?

Even if we don't know about the issue offhand such details can give a starting point for a bit of research on Google. 

Regards, yeti.

**From CrystalDiskInfo;**

Enclosure : JMicron Tech USB Device (V=152D, P=0578, sa1)
           Model : SAMSUNG HM201HI

Geffers

---

### Post by CelticWarrior on 2020-03-02
I couldn't find anything about a "Samsung HM**201**HI" but one result for HM**250**HI, a 250GB SATA II 5400rpm HDD. The HM201HI, assuming it's correct, maybe is 200GB (?). A lot less than 2TB...

Still wondering about the same. Why exFAT?

---

### Post by Autodave on 2020-03-02
I have a thumb drive that claims it is a one terabyte.  But, it is actually an 8G.

---

### Post by Geoff_Lane on 2020-03-02
> **DuckHook said:**
> Doesn't pass the "smell" test, does it?…

It was sold as 'new', the SMART info from CrystalDiskInfo shows Power On Hours : 29 hours.  I'm guessing it was, maybe, a malfunctioning disk returned to original seller and now resold as new in a new enclosure.

However, he was given a full refund and not asked to return disk so now questions are curiosity only.

Geoff

---

### Post by Geoff_Lane on 2020-03-02
> **CelticWarrior said:**
> I couldn't find anything about a "Samsung HM**201**HI" but one result for HM**250**HI, a 250GB SATA II 5400rpm HDD. The HM201HI, assuming it's correct, maybe is 200GB (?). A lot less than 2TB...

Still wondering about the same. Why exFAT?

Yes, that is odd.

Another entry from the CrystalDiskInfo;

Health Status : Caution

Dodgy drive all round.

Strange thing is, he did a dd writing zeros on the disk, would have thought that maybe erased the SMART disk info, unless that it separate.

Geffers

---

### Post by CelticWarrior on 2020-03-02
Yes, I think it is separated. AFAIK they do it with a modified firmware that reports a much higher than real capacity.

---

### Post by DuckHook on 2020-03-02
> **CelticWarrior said:**
> Yes, I think it is separated.
If I recall, smart data resides on a tiny dram module on the drive's control circuitry. It isn't part of the physical HDD/SSD.
> AFAIK they do it with a modified firmware that reports a much higher than real capacity.
And if they are installing a fraudulent firmware anyway, why not also show the drive as brand new?

---

### Post by lwalper on 2020-03-09
Similar problem noted with 16Gb thumb drive. Windows would read the drive but not Linux. In Win10 would only format in exFAT or NTFS, no FAT32 option given. Could that be due to the 4Gb file size limit for FAT32? I jus copied all the data off to the HDD, formatted the USB in NTFS and copied the data back onto the USB. Now Linux reads the drive no problem.

What's the process for enabling Linux to read the exFAT format?

---

### Post by yancek on 2020-03-09
> What's the process for enabling Linux to read the exFAT format? 		 

I'm not sure any Linux has the software to read/write to exfat as it is not commonly used so you need to install the software.  See the link below.

[https://itsfoss.com/mount-exfat/](https://itsfoss.com/mount-exfat/)

> But for Linux Kernel 5.3 and lower versions, it remains a proprietary  software. Ubuntu and many other Linux distributions don’t provide the  proprietary exFAT file support by default. This is the reason why you  see the mount error with exFAT files 

---

### Post by CatKiller on 2020-03-09
> **lwalper said:**
> What's the process for enabling Linux to read the exFAT format?

[https://www.phoronix.com/scan.php?page=news_item&px=New-exFAT-For-Linux-5.7](https://www.phoronix.com/scan.php?page=news_item&px=New-exFAT-For-Linux-5.7)

---

### Post by lwalper on 2020-03-11
> **yancek said:**
> I'm not sure any Linux has the software to read/write to exfat as it is not commonly used so you need to install the software.  See the link below.

[https://itsfoss.com/mount-exfat/](https://itsfoss.com/mount-exfat/)

That works. Thanks!

---

