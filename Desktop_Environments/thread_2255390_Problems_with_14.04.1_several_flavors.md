---
title: "Problems with 14.04.1 several flavors"
date: 2014-12-04
forum: Desktop Environments
---

### Post by de Bacon on 2014-12-04
In trying to load a fresh install.  I do this to have newer software and realizing that 12.04 is soon to be expired (my interpretation of soon).  

I have tried xubuntu 14.04.1 64 bit, ubuntustudio 14.04.1 64 bit, and then tried kubuntu 14.04 32 bit.  All these systems have proven troublesome.  I have in the past used all of these flavors: xubuntu 12.04, kubuntu 12.04, and ubuntustudio 10.10 all with success.  

I have an 8 year old box now, AMD 64 bit, 2 Gb ram 4 HDDs (for separation of OS partitions on differing discs and facilitation of data backups).  With 14.04 I have not had success with any of these systems being stable.  They tend to lock up completely causing repeated hard boots and or run extremely slow.  The last OS I tried (a couple days ago) kubuntu I chose the 32 bit system just to see if that would work better but no.  It was the slower of the three, and seemed to use up a majority of my processors in running simple tasks.  It seemed silly to me how the processor use was so high with only evolution (email) running (between 80 -100%).  

So I concluded that my choice between 64 and 32 bit systems was not a problem.  I would try straight ubuntu but I dislike unity to the degree that it is outside my will to use at all.  

My question is this: is my oldish 2006 (date) system beyond functioning well with these newer operating systems?  I think it remains within the requirements stated, but I am not very knowledgeable about these kinds of things.  

I hope someone can shed some light on this.  I really wish to run a lightweight system that functions well.  I will not do much with this main everyday system.  Watch video (via mplayer or youtube and equivelants) play .mp3 audio (amarok preferred), do some light graphics photo alteration with gimp and communicate via a pop3 email (evolution preferred) and occasionally skype.  

Thanks

---

### Post by ajgreeny on 2014-12-04
What exact hardware have you got?

OK, it's old, but that is not much help, and you don't even mention the graphic card, which could well be the cause of the unstable system.

---

### Post by de Bacon on 2014-12-04
I would tell those specifics if I knew?   I don't know what graphics card is in the box or how to find out.  I know it is some simple command but what that is?  I don't know the commands well enough to wing it.   I used to have a different graphics card, but finally got a different one due to conflicts, at which time I looked through the list to find one that was supported.  It has an intel chip(?) proprietary but has a work around driver.  I may not be using the correct language because I don't know computer ease.  **** edit in->  I found the graphics card info.  Nvidia G84 [GeForce 8600 GT]  ****/edit in

I have an *ABIT* KN8 SLI motherboard, which wasn't supported well back in 06 but became that way by the time 8.04 hardy came out.  I was able to find good function with it from then on. 

Other than the graphics card, singular, and the mother board, the remaining hardware is the DVDRs, the floppy drive and the HDDs.  I don't do gaming.  The sound card in in the motherboard.  

Since starting this thread, I have wiped the partition that had kubuntu and re-installed ubuntustudio 14.04.1 and am in the process of setting it up.  We'll see?  I have not tested anything yet, ie video or audio.  

Cheers - thanks

---

### Post by kansasnoob on 2014-12-05
The following two commands will show the actual cpu and graphics chip info:

```
cat /proc/cpuinfo | head -10
```

```
lspci | grep VGA
```

I have a lot of oldish hardware running Ubuntu 12.04 or 14.04 using the classic/flashback desktop with the metacity window manager:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

Ubuntu Precise is supported until April 2017 and Trusty is supported until April 2019. I've found Precise to be less resource hungry than Trusty. The other flavors of Precise mostly reach EOL by next April, but Edubuntu has the full 5 years of support and the classic/flashback DE is offered by Edubuntu so it should be good until April 2017 - I hope.

---

### Post by de Bacon on 2014-12-05
My processor model name = AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ 
Cash size = 512 KB

The graphics card = VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1)

I have been working in Ubuntustudio 14.04.1 since late yesterday (and again) this time it seems to be running better.  It has only locked up once thus far, but I relate that to operator error.  It was a challenging evening, setting users, I erred causing a problem but I figured it out and corrected the issues I think.  

I have a different OS set up that will be strictly for a DAW.  I have come to recognize either rightly or incorrectly in assumption, that there are serious software conflicts when having all the programs available in the type of DAW I want, and a fully functional every day computer system.  Thus I shall keep the two seprarated and hopefully the computer issues I have had will no longer occur.  
Time will tell.

Thanks for your help!   I do wish I knew the command structures well for using a terminal interface.  Knowing the commands you supplied seems impossible to me due mostly to the irregularity of my need to use them. 

cheers

When I am sure this issue is fully resolved, I will change the thread status to solved.

---

### Post by Darth Riker on 2014-12-05
Hmm. If your question is around the hardware you are using perhaps this thread - about "Old hardware brought back to life" - might be of use:

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

Post #4 in that forum - [http://ubuntuforums.org/showthread.php?t=2130640&p=12580294#post12580294](http://ubuntuforums.org/showthread.php?t=2130640&p=12580294#post12580294) - recommends using the following command to gather information about your computer:

```
sudo lshw -sanitize > lshw.txt
```

---

### Post by de Bacon on 2014-12-18
Hi,  
I have been trying to pay attention to programs running and the such (with my leaky old mind), while going about doing regular daily computing tasks.  There is still a problem with this OS (UbuntuStudio 14.04.1) and my system, be it hardware or otherwise.  I really don't know how to troubleshoot it. 

In the past week numerous times the system has locked up, causing need for a hard boot.  My paying attention (above) is less than perfect, like my typing.  I think the issue may be with a flash player, but even that doesn't track at times (or so I think).  More often than not, the lock up occurs when using Firefox and viewing some form of video, yet that is not always true.  Equally true it could be a conflict with evolution (email program), as I use a pop type of email delivery.  I say equally true because evolution is on most all the time.  Yet the system has locked without viewing video, working on web design with mp3 format music playing in the background.  I have and use a large library (>200 GB) of mp3 formated music, (delivered through Amarok) yet this is generally not in use when the system crashes.  There is one more thing that I note, which may simply be coincidence, that being the duration of time between start-up and lock up.  That too is not consistent, but when it occurs seems to be near 10 minutes post boot.  Again this time idea is something that happens occasionally rather then repetitiously. 

I have gone through the links provided above trying to glean what I can from that during some free time in the past week. Nothing pops out as problematic with the age of the system and its hardware. I actually don't know how to post the results of those tests into this forum.  I now have a lshw.txt file which I could directly copy paste into here but it is quite long and in my opinion unremarkable.  Still as a computer guy, I am an idiot, actually knowing little of what happens behind the curtain.

So I really don't know how to remedy this lock up problem and feel it will likely damage a HDD if I continue this way.  I have some time reserved for tinkering now where last week that was not really true.  Work to be done in real life, with the computer as a tool, locking up at random times and somewhat expected times over the course of the week.  

Thank for reading, and for the suggestions above.

---

### Post by fantab on 2014-12-20
Why are you using UbuntuStudio on that machine? I ask because UbuntuStudio comes loaded with media studio sofware and a different kernel then regular *buntus. 
With only 2gb RAM XUbuntu could be a better choice, if you are not into media intensive computing.
How much Swap space do you have or in other words, how big is your swap partition? Generally studio machines have more juice.

To see the swap size use:
```
sudo parted -l
```

To show a large file, like yours, on this forum you can use [http://paste.ubuntu.com/](http://paste.ubuntu.com/)
After you have pasted note down the** url** from the address bar and paste it back here.

---

### Post by de Bacon on 2014-12-20
I'll say good Morning as it is that here. Thanks for the reply fantab. 
Okay, I use ubuntustudio because I am a musician and do a lot of audio recording.  I am also doing some video editing to make music videos.  You see my old (really old 2000) windows box that I have dedicated to recording music, runs Win98 SE having cakewalk pro audio 9.3 for that purpose.  But that machine is so archaic that its function as a Digital Audio Workstation (DAW) is less than ideal.  I am poor financially, thus I switched to Linux on this newer (2006) box, totally free of windoz :), with the hope of having a fully functional DAW.  It has been a real struggle with issues quite similar to what I have now.  

Realizing the problems related to recording audio, the capacity needed for multi-track audio recording, and my seemingly troublesome computer, I have now 4 HDDs with a combined total capacity of 4.5 TB and with the individual HDDs partitioned so that there is a partition for an OS of between 40 - 50 GB and another (or two) for my personal data on each HDD. this allows me to have 4 functioning OSs and use GRUB to choose which system I run. Whether true or otherwise, I have decided that serious audio recording has a need to be totally isolated from other types of function,  so to facilitate this, I have a different OS that I boot to that has no bells or whistles, just the basic functionality to record music, browse the Internet to gain information at the linuxmusicians forum or here or other various websites.  When booted to this OS partition dedicated to be a DAW I don't do other things.   Still regardless of what OS the computer is running I want to be able to record rough drafts of music that might pop into my head at any given moment.  Thus I need the capability to do that in all the OSs so now matter which is currently in use, I can recored without having to reboot.  My own memory is questionable, thus this need is essential.

So I started using UbuntuStudio with 10.04.  Over time I became less than satisfied with its functionality, and switched to xubuntu a last year. I've tried kubuntu and was happy with it for a while, but its compatability with running audio DAW software seemed problematic and I found other personal preference  issues becoming a problem.  I quit straight ubuntu shortly after unity showed up, again personal preferences. Xubuntu seemed to work pretty well with 12.04 but in my own ignorance, I was unable to upgrade certain audio software to new stuff in the audio world (not offered in the confines of Synaptic for the 12.04.  So I decided to try 14.04.1 first in xubuntu, finding these lockup issues. Then I tried KXStudio, same thing, lockup issues. Then thought to try UbuntuStudio again.  

My goal is to have 2 OSs, one for stable regular use that allows my personal preferences in basic look and funtion (a condition met by xubuntu, kxstudio and ubuntustudio) and another that is dedicated strictly to being a DAW for serious music production.  I don't mind switching back and forth, but i realize now that lengthy audio production projects generally can't be done on a system of my preference that does it all.      

Maybe it is simply the ABIT motherboard that is the problem with what I am attempting to do? When I purchased it, I didn't recognize that there was such a thing as conflicts with proprietary software and drivers with linux, since I came fresh out of a rather oldish windoz world and have no formal computer education.

Along with what is stated above, on each of the HDDs I have space formated to linux swap.  Using system monitor, I can see there is 8GB swap.  Using the command you provided, "sudo parted -l" the following is its result: 


Model: ATA WDC WD10EZEX-00K (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  42.8GB  42.8GB  primary  ext4            boot
 3      42.8GB  43.9GB  1049MB  primary  linux-swap(v1)
 2      43.9GB  489GB   445GB   primary  ext4
 4      489GB   1000GB  511GB   primary  ext4


Model: ATA WDC WD10EZEX-00K (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  40.0GB  40.0GB  primary  ext4            boot
 2      40.0GB  42.0GB  2000MB  primary  linux-swap(v1)
 3      42.0GB  1000GB  958GB   primary  ext4


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  48.2GB  48.2GB  primary   ext3            boot
 2      48.2GB  49.6GB  1362MB  extended
 5      48.2GB  49.6GB  1362MB  logical   linux-swap(v1)
 3      49.6GB  1046GB  996GB   primary   ext3
 4      1046GB  2000GB  954GB   primary   ext3


Model: ATA WDC WD5000AADS-0 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  4195MB  4195MB  primary  linux-swap(v1)
 2      4195MB  46.4GB  42.3GB  primary  ext4            boot
 3      46.4GB  500GB   454GB   primary  ext3


The info from "lshw.txt" is located here: [http://paste.ubuntu.com/9582061/](http://paste.ubuntu.com/9582061/)

Thanks for reading!

---

### Post by fantab on 2014-12-21
I'd say, first check your mobo vendor's website for any firmware/Bios updates... If any updates are available then follow the update/upgrade steps to upgrade your firmware.
> *-core
       description: Motherboard
       product: KN8 SLI(NF-CK804)
       vendor: [http://www.abit.com.tw/](http://www.abit.com.tw/)
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD

If you say 12.04 was working better than perhaps you should go back to it as it will be supported till 2017. 

> I was unable to upgrade certain audio software to new stuff in the audio  world (not offered in the confines of Synaptic for the 12.04.
Did that upgrade work on newer versions and other flavours?
How are you trying to update this software?

Did you install the required Nvidea drivers? (System Settings - Additional Drivers)

> My goal is to have 2 OSs....
You can try another linux distro, like CentOS or Debian, for another OS.
Both OS's have very stable base and so sometimes have older verions of applications which are very solid.
See if you can get either or both to suit your demands, you can try them from DVD/USB.

In future conisder adding another 2gb RAM stick to the machine...

---

### Post by de Bacon on 2014-12-21
Evening,
The firmware.  The site is dead, as per the link provided.  But I was able to somehow get to it through a convoluted search.  It appears that ABIT no longer supports this board and its bios or at least if they do I was unable to find its location.  The search on their site for this particular mother board provides the user with a server error.  

I thought I said that I couldn't get the new versions of preferred software through ***synaptic*** as provided by synaptic as it comes set up in its original package.  I don't know enough about adding ppa s and or what is viable or can mix with what comes with a differing distro, in the case referred to then it was 12.04.  I don't remember the names of releases any more, they seem to be nonsense to my mind, somehow Hardy Heron remains in there though, the numbers work well though. I began using ubuntu with feisty something I think it was. After that the names sort of fizzled as meaningless. 
 
I don't use command line to do much of anything beyond changing permissions for my personal data.  Switching systems causes a lot of that.  Although I know it can be done for software installs, but I remain too ignorant to do that, and there can be dependencies involved, that I don't know about.  I have a hard enough time using synaptic.  

I didn't elaborate on the wish for two OSs enough.  I want them to be the same distro.  I can customize them both to suit my needs with where and how I access software, color scheme, etc.  I enjoy the way my personal set up is laid out.  One setup will have all the DAW software, office software, firefox, and almost nothing else, the other will have some light weight audio recording software along side other commonly used software for my normal every day use excluding the audio recording software.  When I want to do a day of serious audio recording, I can boot to the system that does only that and spend my hours hopefully without system failure snags and glitches.  It is big effort being a solo musical artist doing it all by one's self. 

 As to going back to 12.04, I question it as being satisfactory because I can't get Ardour 3.x  with its provided PPAs.  By this time next year that potential and equivalent with other packages will likely be worse yet.  

So this 14.04.1 is still doing the same or near the same.  Today when it locked up, it was effectively a complete lock up but the mouse could still move and the keyboard lights could still be changed, but nothing passed through as an action.  Mouse clicks did nothing and keyboard commands ALT+F4,  Esc, etc. did nothing.  Generally it is a complete lock.  I really don't understand the stuff.  I also seem to notice that when I reboot there isn't the old crash report showing up, maybe that was dropped with 14.04?  I don't know.  Again it was in that initial 15 or so minutes after boot-up in the morning.  I always shut the thing off at night.

Well cheers to you all and to all a good night :)

---

### Post by de Bacon on 2014-12-30
Fantab, 
Thanks for all your time and consideration with my problem.  It seems that one of these suggestions resolved the issue, nvidia drivers.  I am still unsure but the near habitual morning computer lock up did not occur today.  It seems that with 12.04 I was able to get away with using the open source driver, but with 14.04 that may not be the case.  In fact I am going to post this, then reboot to a 12.04 system and see if my memory is true or false.  I'll be back in a few minutes with that answer, to complete this communication.
~~
Back, It took a while to find additional drivers in kubuntu 12.04.5 (that is the only flavor of 12.04 remaining in my desktop).  It appears that there was a proprietary driver loaded in that system, my brain is crumbling with old age, sigh!  
And so that may (??) and likely does answer the question about 14.04.1 and the problems I have experienced.  Again I am not yet sure that this is a resolution to the problem.  I will have to shut the computer off for a couple of hours and then start it up and see what happens, repeat a few times before I will know for sure.  

Again thanks to all who try to assist in these things.

---

### Post by de Bacon on 2014-12-31
This is an up and running correctly system now.  Again thanks for the assistance!
Happy New Year, 
Live well!

---

