---
title: "Edgy concurrent boot speed"
date: 2006-11-04
forum: Desktop Environments
---

### Post by boban on 2006-11-04
Hi!

I have question about concurrent boot in Edgy. How can I configure it? Is it default? Can it be disabled?

And most important:
While rumbling through my config files I saw in /etc/init.d/rc:

```

# Specify method used to enable concurrent init.d scripts.
# Valid options are 'none', 'shell' and 'startpar'
CONCURRENCY=none

```

What does it mean? Is this another concurrency option in edgy/linux?

---

### Post by K.Mandla on 2006-11-04
Nice find. I'm going by what I scraped up from [Debian Administration]("http://www.debian-administration.org/articles/199"), but it looks like you might see a boot time decrease if you change that line to

```
CONCURRENCY=shell
```
I'll try it when I get home and see if it has any effect. 

I just **love** speed tweaks! :biggrin:

---

### Post by kerry_s on 2006-11-05
I wouldn't mess with that bad things happen. ;)

---

### Post by K.Mandla on 2006-11-05
Well, I tried it anyway and my boot time went from 28 seconds to 25.5 seconds on a dual 2.8Ghz P4 Xeon machine. No problems or errors as of yet. I'm going to see what happens when I try it on an older laptop ... :D

Cheers!

---

### Post by boban on 2006-11-05
I did some googling and found, that the main difference between using CONCURRENCY=startpar and CONCURRENCY=shell in /etc/default/rcS is that the latter doesn't care about the order in which messages are printed to the screen[1].

According to some other sites boot speed increase varies from 2-6 sec. 

But how can I check/test that normal booting procedure is parallel? Really - I didn't see any boot speed improvement between Dapper and Edgy (but I didn't measure time either, so that is very subjective).

And another thing - about single core cpus... I am a programmer myself and according to my previous experience adding concurrency to programs actually slows them [on single processor/core system] a bit. It's because additional overhead of concurrency control mechanisms and task switching. Parallel execution is only beneficial if some external delays are introduced, like waiting for ip address from dhcp server. So I assume that only some tasks are booting concurrent in Edgy boot-up process... Can I control it somehow or at least see execution order? 

[1] [http://bootdebian.blogspot.com/2006_07_01_bootdebian_archive.html](http://bootdebian.blogspot.com/2006_07_01_bootdebian_archive.html)

---

### Post by boban on 2006-11-05
> **K.Mandla said:**
> Well, I tried it anyway and my boot time went from 28 seconds to 25.5 seconds on a dual 2.8Ghz P4 Xeon machine. No problems or errors as of yet. I'm going to see what happens when I try it on an older laptop ... :D

Cheers!

Cool! I can't wait to try it by myslef (but I cannot do it right now, because I'm compiling OpenOffice, and I don't want to interrupt the process :( )

---

### Post by K.Mandla on 2006-11-05
> **boban said:**
> But how can I check/test that normal booting procedure ais parallel? 
Good question. Personally, I just used the Timex method and got a slightly faster boot time. (Actually, 2.5 seconds on this machine is a huge improvement. Most tweaks have no effect at all.) Would [bootchart]("http://packages.ubuntu.com/edgy/admin/bootchart") give any indication of what was working at any given moment?

> **boban said:**
> I didn't see any boot speed improvement between Dapper and Edgy (but I didn't measure time either, so that is very subjective).
Really? I thought the Edgy startup was quite a bit faster than Dapper. Of course, I thought Dapper was faster than Breezy, too. ;)

> **boban said:**
> And another thing - about single core cpus... I am a programmer myself and according to my previous experience adding concurrency to programs actually slows them [on single processor/core system] a bit. It's because additional overhead of concurrency control mechanisms and task switching. Parallel execution is only beneficial if some external delays are introduced, like waiting for ip address from dhcp server. So I assume that only some tasks are booting concurrent in Edgy boot-up process... Can I control it somehow or at least see execution order? 
That's fairly complex stuff, and not anything I'm really proficient at. However, there is the [sysv-rc-conf]("http://packages.ubuntu.com/edgy/admin/sysv-rc-conf") tool that allows you to arrange runlevels for some services. And again, bootchart might give you a clue when things are triggered and if they're actually being executed in an efficient manner.

Let me know what you come up with. I really do enjoy tweaking machines for speed, and anything that helps is something I like to try. Cheers!

---

### Post by boban on 2006-11-05
> **K.Mandla said:**
> 
Let me know what you come up with. I really do enjoy tweaking machines for speed, and anything that helps is something I like to try. Cheers!

I'll do it... And I'll answer your post in more details later (this might be tomorrow). Now I have to get back to work (yeah, I know it's Sunday, but I have no other choice right now :( )...

---

### Post by boban on 2006-11-06
> **K.Mandla said:**
> Would [bootchart]("http://packages.ubuntu.com/edgy/admin/bootchart") give any indication of what was working at any given moment?

I'll check that package soon... it looks cool :)

> **K.Mandla said:**
> 
[sysv-rc-conf]("http://packages.ubuntu.com/edgy/admin/sysv-rc-conf") tool that allows you to arrange runlevels for some services. And again, bootchart might give you a clue when things are triggered and if they're actually being executed in an efficient manner.

I know this tool, but I thought it can only enable/disable services at certain runlevel (that is some control). But how could I control that one service has to be run before another within the same runlevel?

> **K.Mandla said:**
> 
Let me know what you come up with. I really do enjoy tweaking machines for speed, and anything that helps is something I like to try.

I have some issue with mounting disk during boot - I saw it just today (I don't reboot my system often). It hangs for about 15 seconds during boot on "mounting local filesystems" (or something like that). It drops even to console  :/. But everything is working fine... (I'll dwell into that mater later). 

My stats are:
* Ubuntu without concurrency - 56 sec
* Ubuntu with concurrency (shell) - 56 sec too :(
* Ubuntu with concurrency (startpar) - couldn't reboot my system after changing it (it started rebooting, then dropped to console - logged in as root! It looked like it was booted in 'single' mode)
* Gentoo without concurrency - 30 sek
* Gentoo with concurrency - 29 sek
* Windows Xp - 34 sek

When I resolve issue with mounting Ubuntu boot time should be shorter.

I'll optimise my boot services soon (haven't time to do that after switching to Edgy) and then post my new boot time :)

---

### Post by K.Mandla on 2006-11-06
> **boban said:**
> I know this tool, but I thought it can only enable/disable services at certain runlevel (that is some control). But how could I control that one service has to be run before another within the same runlevel?
That's a tough one. You'll probably have to hit Google to find an answer to that. Or maybe the [Debian forums]("http://forums.debian.net/"). 

> **boban said:**
> I'll optimise my boot services soon (haven't time to do that after switching to Edgy) and then post my new boot time :)
I've put that tweak on a couple of machines and I usually see a slim cut in boot times, and still haven't run into any problems. I haven't used the *startpar* option though; I've been sticking with *shell*.

I used it on a straight Dapper Xubuntu build and saw a slight improvement, then reversed it only because I don't really care how long it takes to boot that machine (it's an always-on laptop).

I mostly have been putting it on Edgy Openbox builds which are already tuned for speed, but the results have been good. This GX260 (2.26Ghz, 512Mb, 10Gb 7200rpm) dropped three seconds on its start time, with no side effects that I've seen. 

Cheers and thanks again! :-D

---

### Post by boban on 2006-11-07
I think I have resolved mounting problem... It was some issue with automatic /etc/fstab file. It worked for some time... And then it stopped... Maybe because I installed additional hdd after Edgy installation? (but it wasn't accessible by default under ubuntu, no entry for it in fstab)

I rewritten it from scratch and during boot mounting is almost instant... But that gave me "only" 3 seconds...

---

### Post by kerry_s on 2006-11-07
I finally got the concurrent=shell to work on mine, i disabled automounting with noauto in fstab and i also had to add some boot parameters to menu.lst, i added> mem=1000M vga=normal dma <and now it looks like it's working. Before it wouldn't even boot, it would just fill the screen with error... :-k i'm guessing you guys are using ext3, i'm using jfs.

---

### Post by boban on 2006-11-07
> **kerry_s said:**
> I finally got the concurrent=shell to work on mine, i disabled automounting with noauto in fstab and i also had to add some boot parameters to menu.lst, i added> mem=1000M vga=normal dma <and now it looks like it's working. Before it wouldn't even boot, it would just fill the screen with error... :-k i'm guessing you guys are using ext3, i'm using jfs.

I'm using reiserfs...

---

### Post by K.Mandla on 2006-11-08
> **kerry_s said:**
> I finally got the concurrent=shell to work on mine, i disabled automounting with noauto in fstab and i also had to add some boot parameters to menu.lst, i added> mem=1000M vga=normal dma <and now it looks like it's working. Before it wouldn't even boot, it would just fill the screen with error... :-k i'm guessing you guys are using ext3, i'm using jfs.
ext3 with dir_index, noatime and journal_data_writeback. I get the best results on sub-1Ghz machines with that mix. It's a pain to set up though.

---

### Post by K.Mandla on 2006-11-08
Right on! I've managed to trim my boot time to 27.5 seconds on a 2.26Ghz machine running Edgy Openbox with this. Thanks boban! :biggrin:

---

### Post by boban on 2006-11-08
> **K.Mandla said:**
> Right on! I've managed to trim my boot time to 27.5 seconds on a 2.26Ghz machine running Edgy Openbox with this. Thanks boban! :biggrin:

Wow... That is better then my Gentoo  \\:D/ Congratulations!!!

---

### Post by boban on 2006-11-10
K.Mandla thanks for the bootchart :)

I've managed to trim mine's ubuntu time to 40 sec on 1.8GHz + Gnome. And I think I could easy got another 4 sec according to bootchart (change network config from dhcp to static and disable automounting). In some time I'll mess with boot sequence a little more, for now I'm content :)

---

