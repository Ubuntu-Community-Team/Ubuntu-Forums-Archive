---
title: "Fresh chance at dual boot install: U14.04.2&amp;W8.1 who controls what?"
date: 2015-08-03
forum: Desktop Environments
---

### Post by Lucypie on 2015-08-03
I have read guide after guide for installing Windows 8.1 and Ubuntu 14.04 alongside each other. 90% of them start with "This is for computers preinstalled with Windows". Well, boohiss! My dad couldn't figure out how to make it dual boot with windows so he deleted everything. For his birthday, he's getting the perfect solid state drive with me preinstalling everything he loves right there. 

I have purchased a 256GB PNY Solid State Drive. May or may not be a good brand, whatever. He's never had a solid state and practically any solid state is better than non solid state.
His current setup: 2TB normal HDD, Dual screens, HP Envy Desktop [(700-406)]("http://www8.hp.com/h20195/v2/GetPDF.aspx/c04513370.pdf") <- manual

About him so you can recommend what he needs: He is in his fifty's and is a die-hard linux user. It started when I was very young. My parents bought me a laptop and I fell while holding it, ultimately frying the mobo and killing the laptop. My dad simply said "If you want a computer, build it". We had multiple dead computers in our old trailer behind the house. So I did. That is why I am a computer tech now. Well, windows wasn't free so he was like "I saw on the internet this cool thing... its called linux... figure it out and you'll have a OS". Well, that wasn't so easy.... I ended up installing a ripped Windows on it just so I could use what I knew. I never gave up though, and when I figured it out he immediately switched. This was just when 10.04 came out. He doesn't truly care for windows, he despises them, but he thought since Windows 8 came out and he's never even seen it, he might should at least play with it a little. You know, keep up with the times. So Windows is NOT important in this setup. It is just a "play partition". He primarily surfs the webs with his computer. No gaming. He does a little bit of web design, not much anymore though. He uses firefox/chromonium and thunderbird... I don't think he uses many other programs. Maybe wine? He also watches videos on the facebook and other websites. 

I figure his "old" 2TB HDD can hold any files or anything else... maybe even a thousand other OS's cause he really likes to play with them. 
What I want to know is which direction should I install these? I know I can just install Windows 8.1 to the whole dang drive and then shrink it later, like all the guides do for preinstalled OS's. I want Ubuntu to control as much as possible since it is the primary, but if it really doesn't matter, I'll do it the "normal" way. Is it better to install Ubuntu first? What kind of partition setup should I have? I used the Microsoft Installation Media download tool to download Windows 8.1 x64. I downloaded Ubuntu 14.04.2 desktop from the Ubuntu website. Should I use a different version? 

I just want your opinion and advice. Not super serious at all, as there's a million ways to do it. No right or wrong really, as long as we can use both. It's been a while since I was in the Ubuntu world, as I live in the tech-repair world dominated by older people, older windows, and lots of mistakes. If there's any kind of programs or other recommendations, let me know! Let's get my dad a real good birthday present!

---

### Post by grahammechanical on 2015-08-03
So, what is your question, again? It got lost in all that family history.

A Solid State Drive in many ways is no different from the usual hard drive when it comes to the matter of installing Ubuntu. There is the matter of something called "Trim" and if you really want to be baffled by science then you can read all about it.

[http://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/](http://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/)

[http://askubuntu.com/questions/443761/how-is-trim-enabled](http://askubuntu.com/questions/443761/how-is-trim-enabled)

As for the version of Ubuntu to install, well, in a few days time ubuntu.com will be offering Ubuntu 14.04.3 which is better with newer hardware than 14.04.2 because it will contain all the Linux kernel hardware upgrades that came with Ubuntu 15.04.

If you install Ubuntu 15.04 then it will need to be upgraded to 15.10 sometime between November this year and January next year because 15.04 reaches end of life in January 2016. My advice will be to install 14.04.3 and stick with it until Ubuntu 16.04 is released at the end of April next year.

If the motherboard has the UEFI boot system then you are still in the situation that is present when having a machine with windows 8.1 pre-installed.

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

That seems to say that if you install Ubuntu in legacy mode then expect difficulties if you then install Windows 8.1 or 10 because they will need to be installed in EFI mode.

You do not seem to have a good opinion of the capabilities of older people. Therefore, as I am 67 years old I recommend that you ignore my suggestions. I must be past it by now.

Regards.

---

### Post by oldfred on 2015-08-03
How you boot installers for both Windows & Ubuntu will be how it installs. And you then need to have both in same boot mode.

I would still install Windows first.  The only thing is that it does not make a generous ESP - efi system partition. It seems to default to 100MB which is ok, but 300 or even 500MB is better if multibooting. Do not know if you can create that in advance to make it large or not.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
But use Windows disk tools to shrink it and reboot immediately so it can run chkdsk and make repairs for its new size. Make sure its fast startup is off. That is always on hibernation which does not work with dual booting.

Not sure what settings your HP Envy has, but often settings in UEFI need to be changed. If you have a fast boot setting in UEFI best to turn it off. My Asus motherboard has several settings for quick boot, both cold boot power up and warm boot/reboot.
Best to check that UEFI/CSM is most current version from HP. Vendors also are finding many fixes to UEFI.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

If you install UEFI, drive will be gpt partitioned. You then want to make sure hard drive is gpt partitioned.

Lots more useful links & suggestions in link in my signature.

If planning multiple installs I keep my / (root) partition at 25GB. With my original SSD that was 60GB I had two / partitions for two installs. Then had several more installs on hard drive. But kept all data on a /mnt/data partition on hard drive. When I still had XP I also had a shared NTFS data partition at /mnt/shared so both Windows & Linux could use that partition for data.

HPs have not been friendly to booting other than Windows. One user with a new system did find buried real deep a setting to allow other systems. Most users have to do a work around to boot a hard drive entry. HP and others have modified UEFI to also use description and only description allowed is "Windows". That is not per UEFI standard.

---

### Post by Lucypie on 2015-08-03
> **grahammechanical said:**
> 

You do not seem to have a good opinion of the capabilities of older people. Therefore, as I am 67 years old I recommend that you ignore my suggestions. I must be past it by now.

Regards.

I do believe some older people are tech savvy. My dad is one of those. But honestly, many older people tend to not understand technology, or worse, not care to learn. Those are the people I have to work with on a daily basis. I do my best to try to teach, but the older clients don't care to learn. Some of my older clients, however, are extremely tech savvy. Even better is the fact that the owners of my business are all "older" and are all of extreme tech-intelligence. It truly hurts me that no matter how I word anything on the internet, there are always people that take it severely wrong. I apologize for offending, it was not my intent. I am young and without people older than I to teach, where am I to learn?

Moving past that, I do appreciate your suggestions. My primary question I suppose would be should I install Windows first or last, or does it even matter? Seeing my Dad's birthday is in two days, I might end up having to install .2 and upgrade to .3 if possible. I was hoping to install all the operating systems from my end on my computer so I could just stick the new hard drive in and it work. One of my computers is UEFI, but the laptop I intended on using as an install dummy is not. Guess I'll install it on this computer to configure it. I'll make sure to match his BIOS and mine. 

> **oldfred said:**
> How you boot installers for both Windows & Ubuntu will be how it installs. And you then need to have both in same boot mode.

I would still install Windows first. The only thing is that it does not make a generous ESP - efi system partition. It seems to default to 100MB which is ok, but 300 or even 500MB is better if multibooting. Do not know if you can create that in advance to make it large or not.
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


But use Windows disk tools to shrink it and reboot immediately so it can run chkdsk and make repairs for its new size. Make sure its fast startup is off. That is always on hibernation which does not work with dual booting.

Not sure what settings your HP Envy has, but often settings in UEFI need to be changed. If you have a fast boot setting in UEFI best to turn it off. My Asus motherboard has several settings for quick boot, both cold boot power up and warm boot/reboot.
Best to check that UEFI/CSM is most current version from HP. Vendors also are finding many fixes to UEFI.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

If you install UEFI, drive will be gpt partitioned. You then want to make sure hard drive is gpt partitioned.

Lots more useful links & suggestions in link in my signature.

If planning multiple installs I keep my / (root) partition at 25GB. With my original SSD that was 60GB I had two / partitions for two installs. Then had several more installs on hard drive. But kept all data on a /mnt/data partition on hard drive. When I still had XP I also had a shared NTFS data partition at /mnt/shared so both Windows & Linux could use that partition for data.

HPs have not been friendly to booting other than Windows. One user with a new system did find buried real deep a setting to allow other systems. Most users have to do a work around to boot a hard drive entry. HP and others have modified UEFI to also use description and only description allowed is "Windows". That is not per UEFI standard.

Thank you for giving me information on the ESP and MSR. I did not think about those and did not know order was important. I am going to do a bit of research on that so hopefully I get it right the first time. I know that I have already turned fast boot off because we currently run Ubuntu on there anyways. 
According to the article linked about the recommended partitions, it lists quite a few partitions. With the new UEFI way of doing it, is there any limit to partitions? I remember back when I was installing 10.04 I had to limit my partitions to 5 or 6. The "recovery" example alone shows 5, so I assume it at least would allow 5. 

Also, thank you for the suggestion about the linux partitions sizes. That is another thing I was curious about. Can Ubuntu install /mnt/shared to a completely separate hard disk? If it can't, that's okay, I'll just format that disk later and work with it.

HP is horrible for booting with other OS's. It was hell just trying to get Ubuntu to work... alone...

---

### Post by oldfred on 2015-08-03
With MBR(msdos) there is a limit of 4 primary partitions, but one primary partition can be the extended partition which then can hold an unlimited number of logical partitions.

With gpt(GUID) there is only one type of partition and a soft limit of 128 partitions. A user can change the limit by resizing the partition table, but I have no idea how as never seen anyone who needed more than 128 partition on one drive. 

My data partition is on my 1TB drive as sdb and main working install on sda.

Both my drives are gpt, and I have an efi partition on sdb drive. But grub seems to always install to sda, overwriting my default boot, so I have good backup of my efi partition on sda.

```
fred@trusy-ar:~$ df -Th | grep sd | sort
/dev/sda1      vfat      500M   16M  484M   4% /boot/efi
/dev/sda3      ext4       24G   11G   13G  46% /
/dev/sdb3      ext4       24G  4.3G   19G  19% /media/fred/vivid
/dev/sdb4      ext4      385G   83G  283G  23% /mnt/data
/dev/sdb5      ext4       28G  3.5G   23G  14% /mnt/backup
/dev/sdb9      ext4       23G  3.7G   19G  17% /media/fred/wily_b

```
I only mounted a few partitions that I occasionally use or other installs.
I normally try to label partitions, so those I do not auto mount with fstab I then have some idea of what they are. I was experimenting with homerun, but now that is available space on my hard drive also. I now use ISO booted from grub2 directly to install, so I am installing from one drive to another.

---

