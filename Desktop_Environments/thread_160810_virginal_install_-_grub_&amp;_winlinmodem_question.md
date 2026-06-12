---
title: "virginal install - grub &amp; ?win/linmodem? questions."
date: 2006-04-15
forum: Desktop Environments
---

### Post by VSFH on 2006-04-15
I'm currently a 56k dialup user (let's hear the groans) and am downloading the BB iso. This will take me a while, so I'm informing myself in the meantime.

Questions: I only used lilo before (my redhat partition died some time ago and due to harddrive failure, it could not be resurrected), and have done a bit of reading on GRUB.

device setup: hda = windows XP boot drive, hdb = windows XP program drive, hdc = 1.2 gig (yeah, I know) drive, partitionless, to be made into an ubuntu drive, hdd = cdrom.

I'm hoping to install grub to the 1st sector fo hdc and set it as the initial boot drive in my bios, and to add an XP entry to grub and not need to use NT/XP's foul bootloader, because I hate it. Also should something go awry I have an easy primary fix. Is this possible with grub?

2nd - unfortunately, my modem is not even a win/linmodem at all; it's likened to an AGP, but is for a modem. Check out via's VT8235 chipset and you may be able to see what I mean. I'm guessing that it won't be supported, but does anyone have any ideas that could help, other than a) buy a regular modem and b) ditch dialup altogether ;) ?

Looking forward to my install and will hopefully post a success story in about 2 days when I'm finally done downloading it. lol.

---

### Post by az on 2006-04-15
[QUOTE=VSFH]I'm currently a 56k dialup user (let's hear the groans) and am downloading the BB iso. This will take me a while, so I'm informing myself in the meantime..[/QUOTE]

[https://wiki.ubuntu.com/forum/GiveAway](https://wiki.ubuntu.com/forum/GiveAway)
Someone can mail you a home-burned cd.  Just ask.

[QUOTE=VSFH]
Questions: I only used lilo before (my redhat partition died some time ago and due to harddrive failure, it could not be resurrected), and have done a bit of reading on GRUB..[/QUOTE]

Grub better.

[QUOTE=VSFH]
device setup: hda = windows XP boot drive, hdb = windows XP program drive, hdc = 1.2 gig (yeah, I know) drive, partitionless, to be made into an ubuntu drive, hdd = cdrom..[/QUOTE]

1.2 gig too small.  I hope you will be using some space from another drive for your ubuntu partition.

[QUOTE=VSFH]
I'm hoping to install grub to the 1st sector fo hdc and set it as the initial boot drive in my bios, and to add an XP entry to grub and not need to use NT/XP's foul bootloader, because I hate it. Also should something go awry I have an easy primary fix. Is this possible with grub?.[/QUOTE]

Yes, but not neccessary.  Grub will work fine and be easily removed.

[QUOTE=VSFH]
2nd - unfortunately, my modem is not even a win/linmodem at all; it's likened to an AGP, but is for a modem. Check out via's VT8235 chipset and you may be able to see what I mean. I'm guessing that it won't be supported, but does anyone have any ideas that could help, other than a) buy a regular modem and b) ditch dialup altogether ;) ?
[/QUOTE]

You must mean an AMR modem.  You will need the smartlink drivers.

[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=BinaryDriverHowto%2FSmartLinkModem](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=BinaryDriverHowto%2FSmartLinkModem)


Should work fine.

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=VSFH]
2nd - unfortunately, my modem is not even a win/linmodem at all; it's likened to an AGP, but is for a modem. Check out via's VT8235 chipset and you may be able to see what I mean. I'm guessing that it won't be supported, but does anyone have any ideas that could help, other than a) buy a regular modem and b) ditch dialup altogether ;) ?[/QUOTE]
check out the second link in my signature and read and use scanmodem to find out whether your modem is supported. if not supported, I'd go with (b) if you have the money.

edit: just saw that azz' link redirects to mine.

---

### Post by VSFH on 2006-04-15
I actually had already read that link in your signature. But yeah, I'll be doing that; here's hoping. I hope the 1.2 gig is enough, I was hopin to have my install done some time sunday and have a 5 day eval done (obviously) friday. if it's not enough space, that sucks, and I'm screwed til I get a new drive, unless ubuntu can smart-partition already partition space (like ntfs XP space) without destroying what's already partitioned. Wow, I'm lazy; the modem is mentioned on linmodems.org - the one PCchips uses (PCTel). should be fun ;) thanks for the help dudes. o/

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=VSFH]I hope the 1.2 gig is enough, I was hopin to have my install done some time sunday and have a 5 day eval done (obviously) friday.[/QUOTE]
sorry about my link, I didn't know azz' link redirects to mine :oops:

anyway, 1.2 is definitely not enough. Once you download the iso (and check its md5sum and burn to cd in a slow speed):

1. Make a backup of all files (this is important, don't trust to partitioning tool too much though no one reported any problems afaik)

2. tell windows to check your hdb for errors (checkdisk? I forgot what it was called). it will want you to reboot. reboot and it will check the disk

3. reboot again but choose "safe mode" to run Windows. Thi has the info [http://www.computerhope.com/issues/chsafe.htm](http://www.computerhope.com/issues/chsafe.htm) (though I didn't test it, and don't remember how to)

4. in safe mode, tell windows to defragment hdb. Do this twice (to my experience, twice is better than once)

5. in partitioning section of ubuntu, tell it to shrink the hdb ntfs so you gain about 3-4 gb on top of your 1.2 gb space (your defragmentation in windows will give you an idea about how much you can shrink it). You'll combine these two into one partition for ubuntu + swap (?300-500MB?). Although a better partitioning would be 
/ (ubuntu's own partition)
/home (your own partition)
swap
you seem not to have enough space for all this... 

Also, you'll find a usb flash card very nice for sharing files between ubuntu and windows (more specifically, transferring files from ubuntu to windows -> you won't have the ability to write to your windows partitions in ubuntu, although you'll be able to see files and copy them over to ubuntu). Usually, a fat32 partition is used for transferring files but you don't have space. 

Note about swap: if you have less than 300MB RAM, it might be a good idea to have a swap twice your RAM size. For example, if you have 218MB RAM, have swap about 500MB.

---

### Post by az on 2006-04-15
[QUOTE=VSFH]I actually had already read that link in your signature. But yeah, I'll be doing that; here's hoping. I hope the 1.2 gig is enough, I was hopin to have my install done some time sunday and have a 5 day eval done (obviously) friday. if it's not enough space, that sucks, and I'm screwed til I get a new drive, unless ubuntu can smart-partition already partition space (like ntfs XP space) without destroying what's already partitioned. Wow, I'm lazy; the modem is mentioned on linmodems.org - the one PCchips uses (PCTel). should be fun ;) thanks for the help dudes. o/[/QUOTE]

Yes, Ubuntu can safely partition your ntfs and free up some space, but you may have to use the manual partitioning tools.

And your modem is an ac97 codec modem, which may have been branded by pctel on some hardware, but in AMR form will work with the smartlink drivers, and most propbably not with the pctel linux drivers.  The PCchips drivers for windows probably run it as a v.90 modem (HSP micromodem?), and could easily make it do v.92, but they don't.  The linux drivers work at v.92 speeds.

---

### Post by VSFH on 2006-04-16
When I was on RH I had no problem using equal amounts of swap to physical memory (512), I don't know that I'll even use swap, but if I do I'll use 256. I'm not a total noob ;) by shrink you mean use disk compression? and why is NTFS not supported for readwrite ? I was using incredibly old RH 7.2 and NTFS was still only supported read-only; I would've thought it would be rw by now.

Also, I had already read your signature because I lurked for a while before posting my question, so had already read after reading a post by you. Azz: it's a HSP modem, which is supposedly v92 - the difference between v90 and v90 is not speed, it's the "modem on hold" ability, which also has to be supported by your ISP. What is shown on my end is "HSP56 (VIA)"; there are bountiful amounts of help and readmes around ;) although many links off of linmodems.org sent me to pron sites and sites telling me to click links to see girls with huge... anyway.

What I meant about it being able to partition space is that usually to create a new partition inside an existing logical (not extended) partition, the original (logical) partition is deleted; maybe this is not so any more. Maybe I should have been more clear; hda = 4 gb single-partition NTFS win XP system drive, compressed. hdb = 40gb single-partition NTFS win XP program drive; if it Ubuntu had NTFS read/write capable I could mount this as a home partition, but I won't be deterred; I won't be installing tons of programs as this is mostly to satisfy my curiousity and be a demo. if I really enjoy ubuntu (and I'm sure hoping to), it'll be the primary OS in my new PC (in a month or so).

Also, my drives are chkdsk'd (it's chkdsk for NT/XP flavors, exceptionally pathetic program) and defrag semi-regularly, along with my registry cleaned by various cleaners and checked for spywares, etc. So tough to get real 'bang for your buck' inside XP.

Again, thanks a lot for the help all around, and hopefully by Monday you'll see a success post ;)  if not, I'll be sure to read through all the relevant topics before I post a "ahhh I'm dying!!!" question. You guys rock. o/

---

### Post by towsonu2003 on 2006-04-16
> **VSFH]When I was on RH I had no problem using equal amounts of swap to physical memory (512), I don't know that I'll even use swap, but if I do I'll use 256. I'm not a total noob  said:**
>  The info I have may be outdated (from times when people had 64MB RAM). I got that info from a Slackware 7 installation howto... I never checked the date and instead (to be safe), I have now a 2GB swap I never use ;)

[QUOTE=VSFH]by shrink you mean use disk compression?
no. shrink (or resize) is done during partitioning in ubuntu. I think its backend is ntfstools. 
> **VSFH]and why is NTFS not supported for readwrite[/quote]it's still experimental. 
[QUOTE=VSFH]
although many links off of linmodems.org sent me to pron sites and sites telling me to click links to see girls with huge... anyway.[/quote]
you can't be serious... that's weird :) if you'd like to, you can post your modemdata.txt for us to check it out. 
[QUOTE=VSFH]
Also, my drives are chkdsk'd (it's chkdsk for NT/XP flavors, exceptionally pathetic program) and defrag semi-regularly, along with my registry cleaned by various cleaners and checked for spywares, etc. So tough to get real 'bang for your buck' inside XP.[/quote]
a defrag or two right before shrinking ntfs thru ubuntu partitioning utility will boost the amount of space it can shrink. It needs defragmented free disk space at the end of the drive to resize it. 

You could do the resizing using gparted / qtparted from inside an ubuntu live cd. This will give you a better idea of what the partitioner is doing. I remember using RIP (a very small live cd, only command line) to resize ntfs. I dreamed about it (nightmares) for a few nights following the resize  said:**
> 
Again, thanks a lot for the help all around, and hopefully by Monday you'll see a success post ;)
good luck in advance :)

---

### Post by az on 2006-04-16
[QUOTE=VSFH]. Azz: it's a HSP modem, which is supposedly v92 - the difference between v90 and v90 is not speed, it's the "modem on hold" ability, which also has to be supported by your ISP. What is shown on my end is "HSP56 (VIA)"; there are bountiful amounts of help and readmes around ;) although many links off of linmodems.org sent me to pron sites and sites telling me to click links to see girls with huge... anyway.[/QUOTE]

Actually, v92 uses v44 which can go up to speeds of 53.3 while v90 uses v42 which uses less compression and is generally around 48.8 kps max.  The links at linmodems may encourage you to use the pctel driver which will not work for amr modems.  You would need to use the smartlink modem drivers.  I just wanna save you the headache.

---

### Post by VSFH on 2006-04-16
huh, I haven't heard that before; my apologies. I guess I'm stuck in between (my modem sticks on 50.6kbps just about every time). I appreciate you wanting to save me the headache; tell mirror.acs.anl.gov to stop screwing around. maybe NcFTP will let me resume from anywhere. I should've gotten over 100 megs downloaded (sounds piddly to you high-speeders) and got nothing.

And yeah, a lot of the links sent me to those irritating search pages (Find more info about modems, for example, but contain pointless, worthless links) and the others sent me to porn links, without images.

---

### Post by VSFH on 2006-04-19
Well, I said I'd be posting a success story, and I have success. Finally downloaded and finally installed (CDrws I had had small scratches; Ubuntu no like scratches on CD.); I have a server install now (so am writing in wind0ze).

Everyone who told me 1.2 gigs is too small, for a desktop install, this is true.

About shrinking the drive: I have a 41.2 gig drive, and the shrink/resize the drive and use freed space defaults to 20.6 (half of it).. Now, what if I accepted this ? Wouldn't I lose a bunch of data?

Also, where are good mount points for the partitions? I have the install w/ LVM so that there's 256 mb in /boot and the rest is /, I believe. I was thinking a 1 or 2 gig partition to /var, but maybe this isn't the best idea.

One last thing; I don't seem to be able to gain read-only access to my wind0ze partition when mounted; I make the directory it mounts to have readwrite access, try mounting the fs readonly, it mounts fine, yet the perms on the directory now give me no access. Maybe I just need to play with it.

Opinions, info, etc, are all welcomed. Thanks to azz and towsonu2003 specifically for all the help, and thanks in advance to everyone else.

One last thing, if anyone can tell me the packages to install (ubuntu-desktop?) and whether I could just install those to get gnome up or not, so then I could get into synaptic and install the goodies I want, and not everything else.

---

