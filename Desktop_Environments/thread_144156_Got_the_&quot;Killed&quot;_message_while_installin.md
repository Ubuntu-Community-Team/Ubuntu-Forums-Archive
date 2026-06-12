---
title: "Got the &quot;Killed&quot; message while installing"
date: 2006-03-13
forum: Desktop Environments
---

### Post by RaicesRadicales on 2006-03-13
First of all I'd like to mention that I am another Linux newbie. Currently I'm running my computer under Windows 98 SE. My computer is a Pentium III 650 mhz, 64 MB shared with the onboard graphic adapter (8 mb) and a 20 Gb HD, partioned in two, with 10 Gb each.
I download the ISO file from the site and burned it to a cd. So, I'm booting through the cd.
The first time I'd tried to install Ubuntu everything worked fine until "Detecting Network Adapter". It freezed on 0% and then a black screen poped up, dos like, with a recurring line saying "Killed" between every 5 seconds. In order to do that and set the network later, which by the way is a SiS900 ethernet card, I unplugged the DSL modem and booted the computer from the Ubuntu cd. This time I got passed the network thing, I even got to choose the hostname and then I pressed the "not configure the network at this time". After that, according to the manual, it was supposed to start the partition set up. And it does, for a moment, and the same thing that happened to me before happens this time. The killed message. I'm clueless about how to solve this. I've checked as many threads and the wiki as I could, but couldn't find nothing like this. So, I'd be glad with anyone can help. The win98 runs on the primary partition. The other partition has only random files and it has 4Gb free of space. I thank you all, in advance.

---

### Post by Zelut on 2006-03-13
I've actually never heard of that issue before.. I would assume that your hardware would be supported.  I've installed Ubuntu on at least 15 machines (old and new) and never had any big issues.

The first thing that comes to mind is that possibly your copy or burn of the CD is bad.  Maybe try another CD and see if that handles things any better?

---

### Post by engla on 2006-03-13
The installer has an option to "check media integrity" or something similar, be sure to run that and see if something is missing or was misburnt.

---

### Post by RaicesRadicales on 2006-03-13
I've run the integrity check and it didn't show any errors and continued the installation. And then the same thing happened again. I've noticed that the black screen comes up on 24% of the "preparing partition" or something like that. I've also noticed that when the Killed thing keeps coming up, and press ctrl alt del to boot the system, it won't boot right away, it first echoes two more lines, which is basically the same thing, but it happens so fast that I didn't manage to get both of the lines. One of them said "Sending SIGNKILL to hardware" if I'm not mistaken, and the SIGNKILL was uppercased like I've wrote. The only thing different on the other line is the uppercased word, but I do believe it was another SIGN something, and after that the system reboots.
Well, I think this is happening because the system is trying to access an unavailble source, like the time it tried to configure the network adapter. When I unplugged my modem it proceeded just fine. Maybe I have a somewhat bad partition, I would format the whole thing. However, I am much too frightened to format the whole HD for nothing (if it don't solve whatsoever). Well, thank you guys for taking the time. I'll still be waiting for some solutions. ;)

---

### Post by RaicesRadicales on 2006-03-14
Ok, I tried the server command at the start of the boot to do that install the base system. So, when it got to the partition part, it got passed to 29% and then something different happened. The dos-like screen appears again and got severel of lines and it kept coming up. I took note of some of them. They all hade numbers before and after what I wrote, but it was appearing so fast that it scrabbled my vision, so I didn't take note of all the numbers and I can't assure the ones I did is right. So, here we go:

Call Trace:
wake_up_process+0xd/0xf
pagebuf_daemon_wakeup+0x1d/0x20 [xfs]
shrink_slab (at this point I couldn't make out the numbers anymore)
__aloc_pages
do_annonymous
do_no_page
common_interupt
handle_mm_fault
do_page_fault
do_shmem_fault
shmem_file_read
file_read_actor
vsf_read
sys_read
do_page_fault
error_code

(and then it finishes with "Segment Fault" and it starts all over again, and again, and again)

Can anyone make a meaning out of this? If the numbers are relevant I'll take note of it next time.

---

### Post by Mustard on 2006-03-14
Your RAM is quite low, so I wonder, when you set up your partitions in the install are you setting up a swap partition?

---

### Post by RaicesRadicales on 2006-03-14
Well, I didn't actually got to that part. It freezes about 24% when it is preparing the partition thing... Are you suggesting me to reduce the shared memory to, say 2mb?

---

### Post by Mustard on 2006-03-14
[QUOTE=RaicesRadicales]Well, I didn't actually got to that part. It freezes about 24% when it is preparing the partition thing... Are you suggesting me to reduce the shared memory to, say 2mb?[/QUOTE]

Actually I was searching around at launchpad.net in the bug reports and found two bug reports in which it was determined that the partitioner was having trouble with low RAM systems.  One fellow seems to have worked around the installation issue somehow by mounting a swap partition from an existing ubuntu installation, from command line while running the installer, which allow him to get past the troublesome partitioning section.

A comment from the person handling the bug seems to indicate that a number of fixes have been made to the partitioning tool in the installer so that it will function with systems that have as little as 32 mb of RAM.  Currently there are no plans to fix this issue on the Breezy installer, but the Dapper Drake installer will have these fixes included.

So I guess you could either muck around with a live CD and repartition the hard drive manually, adding a swap partition, then attempting to mount that swap partition during the install process, or you could try installing with the Dapper Drake version of Ubuntu, either when the stable release becomes available or using the current unstable development version.

-edit-

'Flight 5' of the Dapper Drake development release has become available just recently.  Obviously using the unstable development release could have issues of its own, since Dapper is still being developed.

---

### Post by StoneBob on 2006-04-19
I have the same problem. Interesting to note that I too have only 65MB of ram. 
I will go search my junkyard for some more and see if that cures it.

---

### Post by StoneBob on 2006-04-19
Yep, Mustard's guess was correct. I added memory to get it above 65MB (actually is at 256MB now) and the "Killed" problem went away.

---

### Post by Mustard on 2006-04-19
[QUOTE=StoneBob]Yep, Mustard's guess was correct. I added memory to get it above 65MB (actually is at 256MB now) and the "Killed" problem went away.[/QUOTE]

Thanks for the confirmation on that StoneBob.  It should help to point others in the right direction, in the future. :)

---

