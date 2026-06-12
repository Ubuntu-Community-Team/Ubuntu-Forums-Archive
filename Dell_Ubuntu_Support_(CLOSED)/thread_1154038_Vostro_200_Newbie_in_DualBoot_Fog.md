---
title: "Vostro 200: Newbie in DualBoot Fog"
date: 2009-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by factoid on 2009-05-09
Hoping to try Ubuntu at last - I've been ubuntu-curious for some time.

I'd be very grateful if anyone can give me some confidence, please!

I'm installing onto a Dell Vostro 200 desktop running Win XP SP3.
I've just upgraded the hard drive, and haven't allowed Dell recovery tools or partitions onto the new drive. It's a plain vanilla drive, so its firmware hasn't been modified to listen for keyboard interrupts; it's not like a new Dell boot drive (I learned about that the slow, hard way).

I needed to deploy this drive before I could study the Ubuntu 9.4 setup routine. I guessed what it would want to find, and I partitioned the drive with two primary partitions. XP is working fine in the first one. I made the other one 30GB size, formatted it to NTFS, and labelled it "ubuntu". It's empty and waiting.

The rest of the drive is now populated with 1TB of stuff in two logical drives within an extended partition. That stuff took an age to copy from external USB drives, so I'm hoping to behave cautiously here and not mess up the data partitions!

Now, on dual boot install day, I've just read about problems people had installing Ubuntu 7x and possibly 8x on Vostro 200's. "Can't be done"!

1. Any help with the following would be much appreciated.
Are the Vostro 200 problems exclusive to Dell hard drives which have the Dell 'restore at bootup' keyboard interrupts tattooed into their firmware?, and 

2. If it *is* feasible to install onto a plain SATA HDD, which Ubuntu install pathway will leave all existing partitions intact?, and 

3. Would it be easier if I deleted the partition I'd reserved, and offered it to the LiveCD installer as unused space?

I've tried to find help in FAQs and on YouTube. People talk mostly about converting existing XP installs on one-partition drives. My first attempt with the Live CD munched into a large data partition, and I want to avoid repeating that mistake.

If it sounds like I partly know what I'm doing here, well that's mostly untrue. My learning to date has been a fizzy mix of tears and pain. Ubuntu does look cool though, and I'd like to give it a go before I'm too old to remember why I don't like Windows.

Thanks in advance if anyone can tell me if I need to trick the Vostro, and if so, how!

---

### Post by coffeeaddict22 on 2009-05-09
Can't comment on the Vostro, but I've got a Studio laptop and an Inspiron 530 both on Ubuntu; the Inspiron is a triple boot and the Laptop a dual boot.
Lessons I learnt the hard way: 
1) the best way to shrink the Windows partitions is with the Vista partitioner; it'll shrink space for you.
2) Yep, you're right.  DON'T format in one OS and expect it to work in the other.  Linux plays nicer in this regard, but save your stomach ulcer for something more difficult.  Shrink the partition, but leave it empty space.  If you've already formatted, go back and delete the partition again.
3) The Live CD is a great way of making sure all your hardware is going to behave.
4) In the linux install, if you use the manual partitioner, you'll be able to set up the partitions the way you want.  I strongly advise three partitions; one swap (double the size of your memory); one has "/" as its mountpoint(20GB is more than enough); the last has "/home" as its mountpoint.  The reason for the separate /home partition is if you ever want to completely reinstall, you can do so without trashing your data if it's in a separate partition.

There's an excellent series on setting up dualboot: [here]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")

---

### Post by factoid on 2009-05-09
Thanks a million, **coffeeaddict22**, for passing on that advice.

I really like the sound of the 'three partitions' approach - it took me a long time to realise that Windows would get through its reinstalls smoother if I had system and data on two partitions, and (portable) applications on a third. It's good to hear how to work in a similar way with Ubuntu. Plus it sounds like reinstalls aren't such a feature of the OS.

That dual-boot guide, too - very clear, covers many permutations, and thank you for it.

I followed the suggestion to delete the partition i'd reserved, and to then let Ubuntu install into the emptied space. That went well right up until grub announced it had failed to install. I'm hoping that this failure isn't something that's inevitable with this Vostro, though. Solutions for grub failures are documented elswhere in this forum, I'll try them next.

I was surprised to see that after installing from Live CD, the new ubuntu partitions had been created within the *extended *partition - which had been stretched into the free space for the purpose. My very limited understanding is that booting has to be from a primary partition, not an extended one. I was therefore expecting to find a second primary had been created. Perhaps I missed something at install time to force creation of a new primary, and perhaps grub wouldn't install because the  installation was in an extended partition. Any suggestions much appreciated.

And if grub can't be persuaded to install, I wonder if anyone could please tell me whether some other boot choice software can take its place. I think there's something in Acronis True Image Home 11 for XP, though I've never needed to check it out. My knowledge stops well short of understanding whether the process must be handled by grub, or whether a substitute can deliver the needed result.

---

### Post by coffeeaddict22 on 2009-05-10
Have a look at [this]("http://www.dedoimedo.com/computers/grub.html"), and the GRUB manual.  If at all possible, I'd use GRUB.  It stands for the Grand Unified Bootloader; anyting else is unlikely to do as good a job.  I'd guess when you installed you did something unusual with the partitions; there is a spot after you select "manual install" where you get the option of what filesystem, and from memory there's another option(just below that) for primary etc if you want.  A primary partition isn't strictly necessary- after all, if you can have 100 different OS on one PC, some of them must be in the same partition...

Good luck!

---

### Post by jjacobs2 on 2009-05-10
I have no experience with it but you might have better luck with wubi.  It's supposed to install ubuntu from within windows somehow.

---

### Post by factoid on 2009-05-10
Thanks again, **coffeeaddict22**, that guide is so well written, and I reckon it'll get me there. (And a lot more on the site besides).

And **jjacobs2 **- thanks for suggesting wubi. I think you're right - it would be a painless way to avoid setting up the full dual boot. In the end, though, I'd like to be able to run independently of Windows. Still, looks like Wubi would get me running while i learn some background. Thanks.

---

### Post by QKC on 2009-07-30
Hi all, 
I have Vostro 200 also and wish to try out ubuntu 9.04 on my system.But when I run the system using the Live CD,I found that the card reader is not able to work.Does anyone have any solution  that can be shared?Assuming I want to do a dual boot and install ubuntu 9.04 on another new HDD,will that possible?

Thanks

---

