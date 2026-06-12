---
title: "Repeated Full Freeze of OS during heavy matlab job, resulting in numerous file system"
date: 2010-06-16
forum: Education &amp; Science
---

### Post by bean5 on 2010-06-16
Hi Everyone,

repeatedly, while I run simulations and calculations in matlab, the my ubuntu crashes, fully.
Everything on display freezes, music I am playing is thrown into a approximately 1 second long loop (like it used to happen on the old vinyl decks). No response to any keys, mouse, power button.
I have to manually kill my laptop by holding the power button for longer than five seconds.

From here, two things were bound to happen:

[LIST]
[*]No full ubuntu boot with Graphical Interface. Instead a command line. After running fsck, and getting bone-chilling error messages, fixing them all: reboot, system works well again. Sometimes saved network connections were lost.
[*]File system check, from there again two possibilities: 1. System shuts restarts itself after, everything in order. 2. Errors found, option to start automatic or manual repair. Automatic gives error message "/tmp not mounted", option to do it manually throws me into command line, where I use fsck. Again, bone-chilling error messages, all fixed, reboot, system works fine, sometimes network connections lost.
[/LIST]
Today, it went to the next level - I booted: BIOS starts, dual boot starts. From here the different standard kernels as well as the recovery mode just give a blinking cursor, and a fully non-responsive system.

From here I used PartedMagic to fix my drive by booting into RAM and running fsck from there. This way I am able to write this message now...

The crashes happened with ubuntu 9.10 which I had before, and came to this new level of violence with ubuntu 10, that I am using now. Matlab is r2009b 64bit version. My system is a Thinkpad T60, Intel Core2Duo 1.66GHz. Dual Boot with WindowsXP, with all this weird thinkVantage stuff on there, if that's of any importance.

As for when the crashes seem to happen more frequently: Code that takes up one of my two processors, and a big share of my RAM, while I run other stuff, like amarok, firefox, document viewer, openoffice etc. in parallel. It seems like an issue in CPU or memory resource allocation.

I do not want to go into detail what this emotionally means. For a quick impression: I am working in a computational lab. My work life is on my hard drive. And I HAVE to run matlab.

Any ideas would be highly appreciated, as this seems to go to a level of understanding the inner workings of ubuntu, that I do not understand. Even if I do not get an immediate response to my personal problem, this seems to be a severe threat to system stability, so maybe someone with more skills than me can spot a real kink in the otherwise highly satisfying ubuntu, and make it a better system, that scientists and engineers can trust even with matlab.

PS I did perform searches before - "Matlab freeze ubuntu" "Matlab lucid ubuntu freeze" "Matlab memory freeze ubuntu lucid" "Matlab ubuntu unstable", also all this with "crash" instead of "freeze", on google and on the forum search. I was surprised no one ran into this before, as it seems...

---

### Post by gunksta on 2010-06-16
Yeah - you need to get to the bottom of this ASAP. Scary. If I were you - I would go out and buy a nice big USB drive (thumb drive, usb-key, etc.) and store all my important stuff on that until this issue gets resolved. If you manage to completely hose your hard drive first . . . . life could be painful and I tend to try to avoid pain.

Disclaimer - I don't have matlab and I haven't used it in about 10 years. Ahhh. College. Such sweet memories of those intro EE classes.

I would start looking for problems in your logs. Kernel sounds like a good place to start:


[LIST]
[*]/var/log/kern.log
[*]/var/log/kern.log.1
[*]/var/log/kern.log.2.gz
[*]/var/log/kern.log.3.gz
[*]/var/log/kern.log.4.gz
[/LIST]

Start with /var/log/kern.log. I might consider looking in the xorg files too. To get a nice complete listing you could use:

```
locate .log
``` OR you could just go to System -> Administration -> Log File Viewer. Your choice.

There are two ways to gaze at your actual logs. If you are stuck in command-line mode or just enjoy a little command-line-fu, 

```
less /var/log/kern.log 
```

Is a nice easy way to pull this up. Or just use the previously mentioned Log File Viewer. Words such as "panic" or "error" would be a good place to start. As you can see, these logs record EVERYTHING, so you need to go back to the logs for a time shortly before you remember crashing or go out and purposefully bring your computer to it's knees in the name of science and progress.

Your choice entirely.

Who owns this computer? That might play a factor in how you approach this. If it's not your computer - I vote for the crash it again for old time's sake approach.

It's the end of the work-day so I'm in a snarky mood. Sorry. But, I think this really will get you going in the right direction, if you ignore my stupid comments.

---

### Post by bean5 on 2010-06-16
Thanks Gunksta for the quick reply. No worries, you seem to perfectly understand my situation, and I happen to like your style of commenting...

Obviously, the first thing I did after my system was up and working again, was backing up all my stuff onto an external USB drive. Crashing on purpose will not happen - it is my own machine, and each crash is one crash too much. Error correction is never perfect.

So, I will give here now what happened in the log files you mentioned around the time the crash happened. It will be a long post. But - as said, maybe we can track down a real bugger there...

The crash should have happened somewhere around 10am, maybe a bit later. Then I tried rebooting from harddrive, which did not work. After, I managed to fix the hard drive by using PartedMagic from CD, booting into RAM-only mode.

[...] means that the files have lines before and after the excerpts I give here.

[B]kern.log
[/B][...][I]Jun 16 09:01:47 lhilbert-laptop kernel: [  106.602585] CE: hpet increasing min_delta_ns to 15000 nsec
Jun 16 09:01:53 lhilbert-laptop kernel: [  112.486878] CE: hpet increasing min_delta_ns to 22500 nsec
Jun 16 09:14:26 lhilbert-laptop kernel: [  864.977269] __ratelimit: 12 callbacks suppressed
Jun 16 09:14:26 lhilbert-laptop kernel: [  864.977275] npviewer.bin[1604]: segfault at c5fd81d5 ip 00000000c5fd81d5 sp 00000000c5fd81d5 error 14
Jun 16 09:31:02 lhilbert-laptop kernel: [ 1861.552234] npviewer.bin[1798]: segfault at 418 ip 00000000f6043a56 sp 00000000ffb886c8 error 6 in libflashplayer.so[f5df5000+b04000]
Jun 16 10:08:56 lhilbert-laptop kernel: [ 4134.902587] CE: hpet increasing min_delta_ns to 33750 nsec
Jun 16 12:02:30 lhilbert-laptop kernel: [10949.059046] npviewer.bin[2017]: segfault at 418 ip 00000000f6087a56 sp 00000000ffd878f8 error 6 in libflashplayer.so[f5e39000+b04000]
Jun 16 12:02:54 lhilbert-laptop kernel: [10973.712509] npviewer.bin[3066]: segfault at 418 ip 00000000f610fa56 sp 00000000fff29688 error 6 in libflashplayer.so[f5ec1000+b04000]
Jun 16 12:03:02 lhilbert-laptop kernel: [10981.687226] npviewer.bin[3100]: segfault at 418 ip 00000000f6102a56 sp 00000000ffbc2988 error 6 in libflashplayer.so[f5eb4000+b04000]
[...]

[/I]**syslog**
[I][...]
Jun 16 09:25:58 lhilbert-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="759" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun 16 09:26:36 lhilbert-laptop anacron[867]: Job `cron.daily' terminated
Jun 16 09:26:36 lhilbert-laptop anacron[867]: Normal exit (1 job run)
Jun 16 09:31:02 lhilbert-laptop kernel: [ 1861.552234] npviewer.bin[1798]: segfault at 418 ip 00000000f6043a56 sp 00000000ffb886c8 error 6 in libflashplayer.so[f5df5000+b04000]
Jun 16 10:08:56 lhilbert-laptop kernel: [ 4134.902587] CE: hpet increasing min_delta_ns to 33750 nsec
Jun 16 10:17:01 lhilbert-laptop CRON[2684]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 16 11:17:01 lhilbert-laptop CRON[2896]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 16 12:02:30 lhilbert-laptop kernel: [10949.059046] npviewer.bin[2017]: segfault at 418 ip 00000000f6087a56 sp 00000000ffd878f8 error 6 in libflashplayer.so[f5e39000+b04000]
Jun 16 12:02:54 lhilbert-laptop kernel: [10973.712509] npviewer.bin[3066]: segfault at 418 ip 00000000f610fa56 sp 00000000fff29688 error 6 in libflashplayer.so[f5ec1000+b04000]
Jun 16 12:03:02 lhilbert-laptop kernel: [10981.687226] npviewer.bin[3100]: segfault at 418 ip 00000000f6102a56 sp 00000000ffbc2988 error 6 in libflashplayer.so[f5eb4000+b04000]
Jun 16 12:17:01 lhilbert-laptop CRON[3330]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 16 13:17:01 lhilbert-laptop CRON[3743]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)[/I]
[...]

**messages**[I]
[...]
Jun 16 09:01:47 lhilbert-laptop kernel: [  106.602585] CE: hpet increasing min_delta_ns to 15000 nsec
Jun 16 09:01:53 lhilbert-laptop kernel: [  112.486878] CE: hpet increasing min_delta_ns to 22500 nsec
Jun 16 09:14:26 lhilbert-laptop kernel: [  864.977269] __ratelimit: 12 callbacks suppressed
Jun 16 09:14:26 lhilbert-laptop kernel: [  864.977275] npviewer.bin[1604]: segfault at c5fd81d5 ip 00000000c5fd81d5 sp 00000000c5fd81d5 error 14
Jun 16 09:25:58 lhilbert-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="759" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun 16 09:31:02 lhilbert-laptop kernel: [ 1861.552234] npviewer.bin[1798]: segfault at 418 ip 00000000f6043a56 sp 00000000ffb886c8 error 6 in libflashplayer.so[f5df5000+b04000]
Jun 16 10:08:56 lhilbert-laptop kernel: [ 4134.902587] CE: hpet increasing min_delta_ns to 33750 nsec
Jun 16 12:02:30 lhilbert-laptop kernel: [10949.059046] npviewer.bin[2017]: segfault at 418 ip 00000000f6087a56 sp 00000000ffd878f8 error 6 in libflashplayer.so[f5e39000+b04000]
Jun 16 12:02:54 lhilbert-laptop kernel: [10973.712509] npviewer.bin[3066]: segfault at 418 ip 00000000f610fa56 sp 00000000fff29688 error 6 in libflashplayer.so[f5ec1000+b04000]
Jun 16 12:03:02 lhilbert-laptop kernel: [10981.687226] npviewer.bin[3100]: segfault at 418 ip 00000000f6102a56 sp 00000000ffbc2988 error 6 in libflashplayer.so[f5eb4000+b04000]
Jun 16 14:07:00 lhilbert-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.[/I]
[...]

---

### Post by sanderd17 on 2010-06-17
It looks like your swap space is inefficiently used. Can you put your swap off while your computing?

```

sudo swapoff -a

```

You should keep an eye on the used ram space.

As for your matlab code: make sure there is no memory leak and if it's possible to write temporary results to a file, do it.

To swich your swap back on, use
```

sudo swapon -a

```

I didn't se that in the logs but I know I had the same problem with some maple calculations.

---

### Post by gunksta on 2010-06-17
Sorry I've been out of the loop. Ironically, a couple of computers crashing here have kept me busy.

I'm not sure that playing with the swap will fix anything. But, it looks to me that matlab isn't what is killing your computer. It looks like flash is actually killing your computer. It may be that this only happens under the load you are giving the system while running matlab, but the segfaults are libflashplayer.

Try installing flashblock in Firefox. That might just stop the problem. If you use Chrome, you just need to turn off your browser. 

Eliminate flash and then see if your problem goes away. 

I'll look more closely tomorrow.

---

### Post by gunksta on 2010-06-18
After looking through these logs more carefully,  I still think flash is at the root of the problem. Is this, by chance, a 64-bit machine running a 32-bit flash (if you installed flash from the repos on a 64-bit machine the answer is yes).

Again, if you are running a 64-bit machine - Is matlab 64-bit?

While I am never ceased to be amazed at the clever work arounds found in things like the ia32libs, in my experience running lots of 32-bit apps in a 64-bit environment is less stable than running all 32-bit or all 64-bit. This is especially true for the steaming pile of poo we refer to as libflash. 

I should also ask - are you sure these correspond to a crash time? The reason I ask is that while libflash is a . . .  (see above) . . . it doesn't usually cause disk corruption. But, I suppose it's possible the disk corruption is caused by matlab which is crashing because of libslash.

I have also found that when computers do weird stuff - simplify things. To get a better handle on what is happening - turn off everything but matlab and the basic desktop. No browser, no music, no Wanda the magic fish. Nothing. Run your matlab code. Run it several times.

If it still crashes, then we need to look into this more closely. If it doesn't crash, you can somewhat let matlab off the hook. Now try running your code while listening to music. Still OK? Now try running your code while listening to music and browsing a couple of websites (no flash). Etc.

Narrow it down.

In closing, I want to reiterate something that sanderd17 said. IF you turn off swap, watch your ram closely. This is especially important if you are running computations that may push the limits of your memory. With swap turned off, your computer will crash HARD if it runs out of memory.

---

### Post by bean5 on 2010-06-20
Thanks to both your help and suggestions - first, I had no brutal crash experience since, but I also have not run any brutal matlab code in the meantime.

Turning swap off seems like a fix, not like a solution, and it is also not clear if this will really help.
The flash might be a problem, true. Also, matlab is the 64bit version, I checked.

So, I went for narrowing it down, and checked the logs of another day with a series of crashes. One thing was consistent, messages of type:
*Jun 16 10:08:56 lhilbert-laptop kernel: [ 4134.902587] CE: hpet  increasing min_delta_ns to 33750 nsec*

I googled for this. hpet is the default clocksource of the kernel. There is a series of bugs with different recent kernel versions. Seemingly hpet, the default clocksource, wreaks havoc. I found this post, on the "clocksource from hell":
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-)

I am following the instructions given there, though they had to be tweaked slightly for grub2, as the post is written for grub, I believe. Instead of changing /boot/grub/menu.lst I had to insert a
"hpet = disable"
in the
[B]GRUB_CMDLINE_LINUX_DEFAULT
[/B]entry in /etc/default/grub and then run update-grub from the terminal.

This should hopefully fix the problems with system freezes, and the resulting data error horror. I am posting this before I reboot with the new settings, to keep track of what I changed, before everything potentially falls to pieces.

---

### Post by bean5 on 2010-06-20
**Referring to the last post:**
Either I am impressed that someone can program such a good bot for such a useless thing as producing posts in a ubuntu forum,
or I am sad that an actual person has to do something like this - I thought we all had better ways to waste our time. Well, everyone his/her own type of hobby I guess.

If there is something in that post, that is of worth, I was not able to make it out in there, maybe my English just is not good enough, it seems to be on another level of proficiency than how I usually communicate.

At any rate - I had some amusement, and am still curious for any suggestions, thoughts etc. while I keep you posted how changing the clocksource affects my comuters behaviour.

---

### Post by cariboo on 2010-06-20
Instead of commenting on spam posts that will disappear, please use the report button and report them.

---

### Post by Azrael3000 on 2010-06-20
[deleted]

---

### Post by bean5 on 2010-06-20
I just had a very positive experience with the new clocksource - I ran matlab, accidentally started a code for about 100 times as big a matrix as I possibly should have, and in doing so heavily overloaded my system's capacity.

The result: Lags in the curser, slowed system - but NO CRASH!!!

I had to kill the machine though, because I could not manage to kill matlab with the system monitor. Still - no file system errors from the file system check.

This seems better than anything I experienced before. I would be sitting here, hoping for my hard drive not to be wasted. Nothing of that.

If anything in the contrary comes up, I will post.

---

### Post by Azrael3000 on 2010-06-21
Are you not able to kill the MATLAB code with a simple CTRL + C?

Anyhow great to hear it works.

---

### Post by gunksta on 2010-06-21
Very very interesting.

I would not have thought of changing the system clock. It concerns me that something like that could even get into a stable kernel release. This is - after all - Linux. Some of us LIKE to pound the #$@# out of our computers.

I don't deal with complex matrices much, but I have definitely pounded this system with some large data sets and R code and I have never experienced anything even remotely similar to what you report. It could be that what you are doing is more computationally demanding than what I am doing, since a lot of what I do tends to just eat RAM, but isn't too too difficult CPU-wise.

Interesting. Thanks for the information. I'll have to add that to my little bag of tricks.

---

### Post by bean5 on 2010-06-22
Further matlab/Ubuntu problems: Crash and consequent file system error again today, when running a video analysis in matlab. At least I could recover the thing relatively fast after.

So, what happened? I am clueless: Any segmentation faults of resetting of processor times do not appear in the system logs. No flash problems or similar either. There is only some stuff that seems like network address assignment messages.

From this point I really do not know how to go on - maybe get a desktop PC in my lab for the heavy computations...or do a clean reinstall of ubuntu, and dump all the dual boot stuff.

How sad.

This is is just to state:
The change of clocksource did NOT solve the problem, though some of the seemingly evil messages do not appear anymore in the kern.log

---

### Post by gunksta on 2010-06-22
Before giving up entirely - try the General Help Forum. 

More eyes == More better

It may be that with additional people looking at this, someone will know what's going on. This is a pretty small sub-forum.

---

