---
title: "Have both grub and mediadirect in the mbr. Boot mediadirect without utility partition"
date: 2007-09-25
forum: Dell  Ubuntu Support
---

### Post by silverdarkness on 2007-09-25
Hi, im not sure if this has been done before but im just gonna post it anyway. I use a lot of different oses so i wanted a way to use the power  button to load grub, and the media direct button to load media direct. 

Also since i boot so many oses i didnt want to  waste a primary partition on some useless dell utility partition so i found an unconventional way to boot media direct without the dell utility partition and still have grub in the mbr.

Here is my setup:
0 12gb primary ntfs for windows xp
1 15gb primary ntfs for windows vista
2 12gb primary hfs+ for mac os x
3 64mb logical ext3 for geexbox
4 512mb logical for linux swap
5 10gb logical ext3 for ubuntu
6 30gb logical ntfs for data
7 30gb logical ntfs for data
8 2gb logical ntfs for mediadirect

Im working on a guide that i will post a guide here if this is at all new or useful to ppl. If there is already a method to boot mediadirect without the dell utility partition and along with grub in the mbr then tell me and i will stop ranting :)

---

### Post by GIFRATE on 2007-09-26
Hey,

I'm really interested to know how you did that. I was thinking about doing that, now I'm just waiting for your guide.

Thanks in advance.

---

### Post by neptho on 2007-09-27
Killing the Utility partition will inhibit you from performing future BIOS upgrades.  I strongly suggest against it.

---

### Post by silverdarkness on 2007-09-27
What does tha bios have to do with the utility partition? I have the xps m1210 and i have updated the bios sucessfully even without the dell utility partition.

---

### Post by silverdarkness on 2007-09-29
Ok, i can confirm that you will still be able to update the bios without the utility partition. I just updated from a07 to a08 sucessfully.

In order for this to work you need a primary windows xp partition. When i first made this work i did a lot of experimentation but only one thing was really needed.  Just boot from the mediadirect 3 cd and type the command:

```
setupmd /diskno=xx /logno=yy /type=87
```

Where xx is the disk no (first disk is 0) and the yy is the logical partition where mediadirect is installed (first logical partition is 1)

It turns out that this has absolutely nothing to do with the mbr, it just tells the mediadirect button to boot that selected logical partition. 

Windows XP Embedded(what mediadirect is based on) cannot boot from a logical partition unless ntldr is on a primary partition therefore you will will need to change the boot.ini in the mediadirect partition to point to the primary xp partition.(Replace the '4' in the mediadirect boot.ini with the location of your primary xp partition)

After that you can delete your utility partition without problems.

Sorry if the guide is a bit unclear, pm me or post here if you need any help. Good Luck :)

---

### Post by jordoex on 2007-09-30
Ok, so do you know how I should set up my partitions? This is on an inspirion 1520
How my disk is set up:

Before mediadirect stopped working:
0 - EISA partition - FAT16
1 - primary Recovery partition (d:\) - resized from 10GB
 free space - will use for swapspace or shift vista over
2 - primary about 75GB OS (vista)
 about 25GB free space - for ubuntu
3 - logical 2.5 GB FAT32 mediadirect partition

Now:
Unallocated space(EISA partition, hidden? - see link below)
0 - primary Recovery partition
1 - primary Vista - shifted over using Gparted
empty space
2 - logical MediaDirect
3 - primary ? MediaDirect or Norton System restore

like this? [http://www.goodells.net/dellrestore/mediadirect.htm](http://www.goodells.net/dellrestore/mediadirect.htm)

And what I want to do:
Unallocated space(EISA partition, hidden?/make it normal?)
0 - primary Recovery partition
1 - primary Vista - shifted over using Gparted
2 - logical ext3 ubuntu
3 - logical swapspace
4 - logical MediaDirect
5 - primary ? MediaDirect or Norton System restore

Sooo, yeah, it's odd... maybe I'll get a new hard drive and just not install mediadirect or something like that.

---

### Post by silverdarkness on 2007-10-01
That drive setup you want is fine. Since you can still add one more primary partition, you can just put mediadirect on a primary partition and use grub to chainload it... Are you planning to install any more oses that require primary partitions? If you aren't its just easier to do that.

I made mediadirect boot using the ntldr from my primary winxp partition instead of the eisa utility partition, but it will probably work using the ntldr from the vista partition also. Once you have set up your partitions they way you want.

If you want to do that:
1. Boot into ubuntu and install ntfs-3g if you dont already have it (to enable write support if the mediadirect partition is ntfs)
2. Use gedit and change both of the '4' in the  boot.ini file to '2' (the primary vista)
3. Boot from the mediadirect cd and type:

setupmd /diskno=0 /logno=3 /type=87

in the command line

4. Shut down and start using the media direct button. It should work fine.


If this dosent work for you then i recommend trying GeeXboX ([http://geexbox.org/en/index.html](http://geexbox.org/en/index.html)). Its a very small linux distro (needs only about 20mb currently) that does basically the same thing as mediadirect and will happily boot from any partition with grub.

---

### Post by Wimme on 2007-10-08
hi silverdarkness!

your posts sound very interesting. I have got a problem creating addititional partitions.
My system is set up like this:

- Dell Utility (I'd like to keep that one)
- Recovery (can be deleted)
- OS: Vista  (keep)
- extended partition
  - 75GB free Space
  - MD (keep)

I need: 1 partition for data and one for linux. MD should be working and should boot, when I press its button.

Problem: When I allocated the space from Vista into the extended partition of MD, MD stopped working.
1. I didn't touch MD, it remained on the exact same sector. OS moved a bit because I got 4MB allocated space in front of it. 
Result: MD booted, but terminated with message "can't access hard drive"
2. I moved MD around a bit (inside the extended partition). Result: MD gives me the message "MD partition missin".

So I need to know how MD finds its partition and how I can tell that stupid program that its partition is still there and working :)

Sorry, your hints above didn't  help me much (please consider me as not very good in that matter)..

Cheers,
Wimme

---

### Post by silverdarkness on 2007-10-08
First use your favorite disk utility such as gparted or whatever and confirm logical disk no of media direct. (Remember the first logical partition is 1)

then boot using the media direct3 cd and type:

```
setupmd /diskno=0 /logno=xx /type=87
```

where xx the the logical disk no.

That should fix mediadirect for you . Please post here if it worked so other ppl who have similar problems know what to do. :)

---

### Post by Wimme on 2007-10-08
hi silverdakrness!

thank you for your quick answer. I confirmed that MD is the first logical partition, and it can't be any different, because it is the only logical partition i have so far.
i don't know how to take screenshots with gparted so I took one from windows:
[[IMG]http://img264.imageshack.us/img264/6470/neuod6.th.jpg[/IMG]](http://img264.imageshack.us/my.php?image=neuod6.jpg)

I booted from MD CD pressed q and entered your code:
setupmd /diskno=0 /logno=1 /type=87

Nothing happened, no error and no success message.

I tried to start MD with the button, but I still got the same error message:
"MD partition missin".

I then went back into the command line of MD and tried some other disk/logicalno combinations, just to make sure and see. Every combination I tried I got the error "Didn't update Media Direct".

Thats why I believe I did everything correctly but to no avail :(
I hope you have some other ideas or I did something wrong :(

Btw.: If everything would work out, I would create 2 more logical partitions in front of MD. So I would just simply need that command again, right?

---

### Post by jordoex on 2007-10-08
just a quick question, which version of mediadirect are each of you talking about? The brand new vista computers have mediadirect 3 but some of you might have mediadirect 2...
I just got rid of mediadirect (3) on my computer, i really don't need it, and maybe sometime dell will come out with a utility that lets you change what the md button boots.

---

### Post by Wimme on 2007-10-08
on my computer media direct 3.3 is installed.

@silverdarkness:

unfortunately that didn't work either :(
I created two more logical partitons out of my free space now and used the command:
setupmd /diskno=0 /logno=3 /type=87

this time it didnt give me an error message, but it didnt fix MD either.

---

### Post by toorima on 2007-10-10
Hi

Got my Vostro1500 yesterday and planing on installing gutsy RC tomorrow but not sure how to repartition the disk, 4 primary partitions are in use all ready.

P 78 mb EISA
P 10 gb recovery
P 75 gb vista (will shrink it to 25 gb)
  60 gb unallocated
P 2.5gb media direct (guessing)

So what would be the best option, moving the media direct to a logical partition or deleting the recovery partition? 
guessing recovery has to be primary to work?

Would the following work,
P 78 mb EISA
P 10 gb recovery
P 25 gb vista (ntfs)
L  2  gb swap
L 10 gb /
L xx gb data (ntfs or ext3)
L 2.5gb media direct

Can this be done without having to reinstall anything? I hardly ever use windows but sometimes its handy to have. 
I was planing on backing up the media direct partition and just put it back on a logical partition if it works.
Also can media direct be made to read ext3 like regular windows?

Thx in advance

---

