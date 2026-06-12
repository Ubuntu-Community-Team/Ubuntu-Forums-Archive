---
title: "Computer crashes like crazy"
date: 2006-09-28
forum: Desktop Environments
---

### Post by caimex on 2006-09-28
Like the title of this thread suggests my computer crashes **WAY** too much. The main problem that I'm having is that Firefox, or any other browser for that matter, crashes when viewing one of out every ten websites. It's a complete joke by now, for example: Firefox will crash 100% of the time when searching something in Amazon and trying to click on one of the results, Opera never crashes in Amazon, and Epiphany crashes randomly in Amazon. There are a lot of websites that pretty much crash completely no matter what browser like download.com, among others. Flash seems to be the main culprit here but it is in no way limited to flash, my computer will crash even while viewing some text websites and other websites that (seem) to not have any flash (some I'm sure of).

Now here comes the weird twist that might help explain everything. Back when I used Windows XP (ugh), my computer **also crashed** like described above, but it was mainly just isolated to flash and quicktime (quicktime crashed 100% of the time). It was selective, like for example some flash games would work and some would crash (specific ones). Windows didn't always crash like that, it started happening one day, and I have no idea what could have caused it. I even tried **reinstalling** and the problem was not resolved.

Another problem I'm having with instability not related to the above problems is getting KDE apps to work under Gnome. The only KDE app that I'm using right now successfully is Ktorrent, I want to use Scribus and/or Kword, but neither of them work properly. Both of them start perfectly and everything seems to work but they will crash randomly when attempting to do almost **anything.** (Scribus crashes half the time due to a signal 11 error which has to do with a font directory error, I added my .fonts directory to the list and this didn't help.)

I am very glad I switched to Linux but its not even funny how many times I have to press my reset button in one day. Sometimes when I HAVE to view a troublesome website I have to view it Lynx or some other text browser (dillo also seems to work in **SOME** cases).

**ANY** help at all or any troubleshooting tips are be gladly appreciated.

Edit: Using Ubuntu Dapper

---

### Post by meng on 2006-09-28
Tough problem you have there. I wonder if it would help to run your apps from the terminal (e.g. type "firefox") and then look for an error message if/when it crashes. Same with other apps.

---

### Post by wirelessman on 2006-09-28
What is your computer?
What's the amount of ram, the cpu and hard drive?

---

### Post by caimex on 2006-09-28
I have an amd64 3200+ (2.2Ghz)
Running Dapper 32 bit though.
1gb RAM
ASRock socket 939 dual sata2 motherboard.
EVGA 6800GS
250Gb WD SATAII hdd

I forgot to explain what happens when it crashes.
Two things happen:

1. It just hangs, sometimes I can move the mouse and sometimes I can't.
2. Screen goes black and it either reboots or goes back to login screen.

Edit: My guess is it has something to do with the video drivers because when my screen goes black I get the weird lines that I've gotten before when I messed up my drivers or my xserver or something. (that was another install of dapper so thats not affecting the problem)

---

### Post by rfruth on 2006-09-28
I'd remove or completely unplug all non essential hardware  (NICs, CD ROM drives etc) and try to narrow it down ?  Have any Diagnostic tools (memory,  CPU test) ?

---

### Post by caimex on 2006-09-28
I've run memtest, but not much besides that. What diagnostic programs do you guys recommend? I'll try unplugging the non-essentials and get back to you.

---

### Post by CaveRat on 2006-09-28
I'm curious to know if the problem could be with the EVGA video. Do you have on board video you can switch to for a test? Sounds to me like this is a hardware issue since you were having crashes in Windoz too.

---

### Post by genesis[OFT] on 2006-09-28
This sounds very hardware related.  It's either your RAM slowly going dead...which is fairly possible, however, if memtest says it's good then it's either video card...or even PSU.  If the voltage to your mobo is fluctuating too much, it can cause erratic behaviour and reboots, like what you are experiencing.

---

### Post by enopepsoo on 2006-09-28
are you overclocked by chance? :D

---

### Post by caimex on 2006-09-29
I suspect that it is hardware related as well, but I dont think its something like the PSU going bad, because its specific things that make it crash not just randomly out of the blue.

I got no onboard video that I could try, but I'm gonna borrow my friends video card soon if I cant find the source of the problem.

I had both my processor and my videocard overclocked but I dont think its related to this because none of them are overclocked anymore and the crashing 
didn't start when the overclocking started and didnt end when the overclocking ended.

Got nothing better to do right now so I'm gonna try unplugging all I can.

---

### Post by nthdegree on 2006-09-29
Running any binary drivers by any chance?
Examples:  nVidia or ATI proprietary (non-free) drivers

Have you used software like EasyUbuntu or Automatix?

If you are using any proprietary drivers GET RID OF THEM!!!  My system crashes approximately once every 2-3 hours with proprietary drivers and about once every 6 months with open-source drivers.

If you are using any software from restricted or multiverse try using only main software and see how things go.

Also what file system are you using? File systems like ReiserFS, XFS and JFS are not as reliable as Ext3 and can corrupt very easily, so after a few crashes bugs may appear.

Also if it is supported try stepping down your processor speed a little bit and increasing fan speeds, if there are any overheat problems that should cut down on heat.

---

### Post by ashokpappu on 2006-09-29
I ran into such problems.  This happens when the RAM is having issues( mem test will be OK).  If u have two chip's try removing one of them.  if it does not fix it then try it with the other one.  This worked for me.  Good luck.

---

### Post by tibbar on 2006-09-29
> **caimex said:**
> I had both my processor and my videocard overclocked but I dont think its related to this because none of them are overclocked anymore and the crashing 
didn't start when the overclocking started and didnt end when the overclocking ended.

maybe you have caused permanent damage by overclocking.

---

### Post by genesis[OFT] on 2006-09-30
Yeah...although you might not see any 'surface-like' problems when overclocking a video card or cpu, unfortunately, it can cause permanent damage.  Nevertheless, I doubt this is the case....again, sounds mostly like a RAM issue.

---

### Post by blueturtl on 2006-09-30
For effectively ruling out the different possibilites you have to be systematic in your approach. If you're not, you're going to get haywire results. Questions I'd be asking:

1. If the browser crashed, does it always crash on the same page or in the same situation (aka is the problem re-creatable)?
If it does, it may be a bug and you should report the conditions in which the bug appears to others to test. If other people do not experience crashing under the same conditions look further. 

2. Does removing all plug-ins solve the issue? If it does, try adding them back one by one and see which one starts the crashing frenzy. You may also want to remove/reset your browser profile (don't forget to save bookmarks.html!) If it doesn't keep looking further...

3. Does increasing your memory latency or lowering cpu clockspeed  fix the problem? If the crashing is totally random based on experience, most of the time random crashes are caused by faulty or malfunctioning hardware. If you've launched Firefox through terminal is the error you get a 'segfault'? If it is this may in fact be a memory problem. Bad RAM or overclocked RAM hinders application stability significantly. If you're system is running at certified speeds you may have to recodnize the ugly fact that not all hardware is created equal: As I understand you have an Asrock motherboard. ASrock is the cheap spin-off of ASUS. For cheaper price, also expect lower quality construction. A poor quality motherboard can be the heart of all cpu and memory related issues, although this is hard to test (for obvious reasons). You may also want to try switching RAM sticks or if you have more than one, try and see that they're identical.

Hope this helps.

---

### Post by caimex on 2006-09-30
All that I can unplugg is the dvd drive and my other hdd, this didnt fix anything. I am almost 100% positive that overlcocking didnt cause any permanent damage.

Some of the crashing is almost complete recreatable. Especially specific websites such as amazon and like half of websites running flash. Its very strange that my main problem is flash and I've been having problems with flash with XP, amd64 Ubuntu, and 32bit ubuntu. Flass = sucks.

I am using binary Nvidia drivers, and I have installed some stuff with automatix. Will running open source drivers affect performance with programs such as Blender? I don't care about games but I do care about Blender.

I'm using Ext3.

Nothing is overclocked at the time.

Gonna run memtest again, and try removing one stick of ram at a time. I'll report back in a bit :P

**_EDIT:_** I ran memtest again, everything was fine. Haven't tklen out the ram yet, but I recreated the crashing on mtv.com with firefox and copied the system logs from the spicifc moment of the crash, did it two times; I attached the txt files to this post: (they're not very long, they are all within the same second)

**_EDIT2:_** Anyone know how to see firefox logs?

---

### Post by ropers on 2006-09-30
When you say you ran memtest, do you mean you booted from the Ubuntu 6.06 LTS install CD and ran a "burn-in" test overnight? Because a lot of intermittent RAM errors will only show up in a **burn-in memory test**; ie. in continual testing over at least 12 hrs. Try that if you haven't already.

Other than that, can you post a **dmesg**? Is there anything funny in there?

---

### Post by lawina on 2006-09-30
Your computer can crash if the cooling system fails.

I have a HP laptop with a desktop P4 processor. The laptop crashes like crazy whenever i run a video clip or vist a website like youtube to see the same. At the time of the crash I can literally hear the cpu fan running fast and the laptop abruptly shuts down. After checking out in the web, I went to a electronics store and got a laptop cooler (the plate like thing with two fans beneath) and put my laptop on top and connected the cooler to the usb connector. Since then i am able to play videos for several hours without any crashes and  my CPU stopped overheating.

So don't dismiss of any cooling related problems these 'modern' cpus can create.

Have fun, guys.

---

### Post by firebadger on 2006-09-30
If possible, do not use the reset button on your computer - it should be the absolute last resort.  With journaling file systems this can cause data loss and you could have a thoroughly wrecked OS.
Try to restart the X-server (ctrl-alt-backpace) if you are stuck.  Another thing you could try (if you are on a network) is to ssh in from another computer and restart from there - "sudo shutdown -r now".

If it is firefox that seems to be the source of you issues it's probably worth removing it and then reinstalling it using synaptic.  You might also be advised to try it with a fresh profile in case there is something corrupt in there.  Just move the ~/.mozilla file to ~/.mozilla_backup and start firefox - you can always move it back if that is not the issue.

---

### Post by fatsheep on 2006-09-30
If you are overclocked please remove the overclock completely for the time being to see if that remedies the problem.  When I first swtiched to Ubuntu I crashed a lot too because of my overclock.  I removed it and the crashing stopped.  I have now worked my overclock back up to a bit below where I was before and I am perfectly stable.

---

### Post by caimex on 2006-09-30
OMG GJKneasrhresjgbawjhbshbf!!!!! rsghbdsgfjigsdjgn sdjkgndsgmdsfhk

Removing a stick of ram worked perfectly :D !

But of course theres a twist, **BOTH** sticks work separately. I've tried each of them alone on the same DIMM slot and the crashing was completely gone, I tried various websites that had a 100% crash rate and nothing!

Hahhahaha, any ideas on how to get them both working :p .
And how do I run memtest as burn-in memory test? That might reveal some errors when running on both of them.

And BTW, when I have to hard-reset I always try ctrl-alt-backspace, but my computer is like completely frozen, can't even turn off the numlock :p

**_EDIT:_** Results are 100% reproductable. 1 stick of ram = good, 2 sticks of ram = crash. Gonna try like every single ram configuration later. Thank you everyone for such wonderful help, this is why I love the Ubuntu commuinty!

---

### Post by ropers on 2006-10-01
> **caimex said:**
> And how do I run memtest as burn-in memory test? That might reveal some errors when running on both of them.


"burn-in test" is just a way of saying run that test continually, for a long period of time.
Ubuntu's included memtest does this by default, if you let it run long enough. Just boot from your install CD, select memory test at the boot menu and then let the test run for at least 12 hrs. Don't worry about the Test and Pass *percentages* it gives you in the top right, these just tell you what part of the current test/pass has been completed and they will go back to zero when a new test and/or pass starts. What you want to look at is the number of passes, that's in the table roughly in the middle of the screen. And of course the number of errors. None = acceptable.

If I were you I would run a twelve hour test each:
- with only the 1st RAM module in there.
- with only the 2nd RAM module in there.
- with both RAM modules in there.

Then come back and post the results.

If all 3 tests burn-in tests show no errors, then you really need to post a dmesg (open Terminal, maximize your Terminal window, type *dmesg* and copy and paste all that info).

---

