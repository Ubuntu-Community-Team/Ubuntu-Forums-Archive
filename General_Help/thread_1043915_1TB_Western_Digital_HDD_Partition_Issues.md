---
title: "1TB Western Digital HDD Partition Issues"
date: 2009-01-19
forum: General Help
---

### Post by Matt_Rapp on 2009-01-19
[FONT="Arial"][/FONT]
I just got my new 1TB Western Digital Cavalier Black Drive from Newegg today and after setting up a primary partition through GParted 
that covers the entire drive the usage information on the drive was off. The title of the partition is "Data". 
Gparted and the "Data" properties window disagree. See the following Screenshot.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100352&stc=1&d=1232341835[/IMG]

What program is right and were are all of these used GB's going? - I just formated the drive, there's nothing on it! 
When I mount the partition the only thing I see is the Lost+Found folder. I know that you lose some of the 
advertised capacity due to the different definitions of a GB but this is ridiculous!

---

### Post by Gondee on 2009-01-19
use partmagic or somthing else.

I have one, and iv never had any problem like that, but iv never used gparted.

---

### Post by Gondee on 2009-01-19
My 1TB ends up being like 930 Gigs

---

### Post by caljohnsmith on 2009-01-19
It doesn't look like you posted the screen shot, can you maybe try again? Also, you may want to keep in mind how "1 TB" is defined by manufacturers: ```
1 TB = 1*10^12 bytes = 1,000,000,000,000 bytes
```
Whereas all OSes that I'm aware of use 1 TiB notation (base 2):
```
1 TiB = 1*2^40 bytes = 1,099,511,627,776 bytes
```
Thus for a 1 TB drive:
```
1*10^12 / 2^30 = [COLOR="Blue"]931 GiB[/COLOR]
```
That means when you look at a 1 TB drive in most OSes, it will appear to be only be 931 GiB. By using the decimal definition of Tera, that's basically a really underhanded trick the manufacturers use so they can claim the largest drive size possible.

---

### Post by Matt_Rapp on 2009-01-24
I have solved my problem, using a live CD of Gparted I tried creating an ext3  primary partition covering the whole drive. Back in Ubuntu I mounted the drive and the size was around where it should be, unfortunately I was unable to do anything on the drive- I could not create a new folder or file. The only thing on the drive was the Lost+Found as before. I found this odd because my 8.10 Installation is running of of a ext3 partition, so I backtracked and repartitioned the drive again, only this time using ext2. The same results occured, I did not have permission to read or write to the drive. So I tried again a third time and created a ntsf primary partition. That worked just fine. It still bugs me that the other two journaling file systems native to Ubuntu didn't work but I'm just happy that I am up and running now.

---

### Post by tsucol11 on 2009-01-24
> **Matt_Rapp said:**
> I have solved my problem, using a live CD of Gparted I tried creating an ext3  primary partition covering the whole drive. Back in Ubuntu I mounted the drive and the size was around where it should be, unfortunately I was unable to do anything on the drive- I could not create a new folder or file. The only thing on the drive was the Lost+Found as before. I found this odd because my 8.10 Installation is running of of a ext3 partition, so I backtracked and repartitioned the drive again, only this time using ext2. The same results occured, I did not have permission to read or write to the drive. So I tried again a third time and created a ntsf primary partition. That worked just fine. It still bugs me that the other two journaling file systems native to Ubuntu didn't work but I'm just happy that I am up and running now.

Same thing here. 

 Solution::

# going to root
sudo su
# for me admin = newton; files = my ext3 partition.
chown -R newton /media/files

worked great, 

Brian

---

