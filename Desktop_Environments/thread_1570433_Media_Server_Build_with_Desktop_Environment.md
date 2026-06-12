---
title: "Media Server Build with Desktop Environment"
date: 2010-09-08
forum: Desktop Environments
---

### Post by talguy on 2010-09-08
I am planning to build a storage backend for XBMC (frontend windows).  I chose to use the desktop environment since I'm not that confident with using a all command line interface and don't know if all the programs that I want on the backend will work in the CLI.  My question is would the ZFS file system be the best choice for me to use.  I plan to have a 40TB system at some point and does ZFS support multiple drives of different sizes or should I wait and get all the same size drives in a Raid 6 configuration???

---

### Post by davrosuk on 2010-09-08
Its personal opinion, but I'd use ext4. Although it might not impact what you're doing, ext3 generally benchmarks better than ZFS. Also, its anecdotal, but my RAID set-up works very well with it.

As for what you're planning - you can use ext4 + RAID with different disk sizes quite happily. I assume that you've got a decent RAID controller, so it would probably be a non-issue mixing drive sizes, brands/types etc. Again, personally, I wouldn't do that. I'd use the same brand and size. You don't *have* to that, but if you use different size disks then you'll be wasting capacity, and using different brands can impact performance (lowest common denominator and all that).

---

### Post by talguy on 2010-09-08
I don't have a raid card I was thinking of using a software raid solution.  How much do raid cards go for do you know of a good cheap one.

---

### Post by davrosuk on 2010-09-08
Its almost unfair to talk about software RAID and hardware RAID in the the same paragraph, H/W is significantly better on performance and reliability - I'd never go near S/W RAID. 

Prices vary wildly depending on a number of factors... How many drives will you start with and how many would you like to be able to put in (in total)?

---

### Post by talguy on 2010-09-08
I was looking at [this case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811219033").  It has support up to 20 drives and was thinking of starting out with 5 to 10 1TB drives in the case.

---

### Post by davrosuk on 2010-09-08
Nice case!
Supporting lots of drives gets quite expensive - so it really does depend on your budget. I've got an Adaptec 3805 (which works out-of-the-box with Lucid) for my storage solution at home, which allows me to attach 8 SATA or SAS drives. At the time that card cost me about £300. 

To support up to 10 you'd be looking at the 31205 (it'll do 12 drives) - but its about £500. If you wanted the ability to fill the case with drives you'd have to go for something like the 52445 which is £1000!

Ultimately, you have to decide what performance you want/need, how much you value your data and put that against how much you are willing to spend. Yes, it could technically be achieved in software and yes, it would be significantly cheaper - but you have to weigh that against risk (ie there is a reason H/W RAID is expensive!)

---

### Post by talguy on 2010-09-08
I found Adaptec RAID 51645 supports 20 drives for US$1040 but will meet my needs.  Do you think Raid 6 is the best way to go for speed, uptime and prevent data protection on the event of a brown out?

---

### Post by davrosuk on 2010-09-08
With the amount of drives you are planning to install it'd probably be the best idea. Its rare that you lose two drives at once, but it *does* happen (I had it happen to me a few months ago at work and I had to rebuild a domain controller!).

Should the power fail, hardware RAID is very good at making sure nothing nasty goes on. R5 will give you peace of mind that should (when) a drive fails you'll be able to get another in and the array will rebuild - R6 simply increases that peace of mind that you can tolerate another disk failure. Its worth remembering that no amount of RAID can replace a backup though!

On my storage array (and this comes from working in the industry I guess) I offer myself "tiers" of storage. For example I have a volume which is RAID 0+1 which is for data I REALLY don't want to lose, and I have a RAID 5 tier that I'm slightly less worried about.

I just thought I should give one final word on ZFS (for the record and before someone quite rightly points out that it's an enterprise level solution): It really is a pretty awesome filesystem and I'd love to give RAID-Z a go at some point. However, at my last check it wasn't well supported on Linux and for that reason I couldn't recommend it.

---

### Post by talguy on 2010-09-08
thanks for all the useful tips

---

