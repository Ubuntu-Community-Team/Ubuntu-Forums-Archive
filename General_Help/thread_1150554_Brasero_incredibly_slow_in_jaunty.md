---
title: "Brasero incredibly slow in jaunty"
date: 2009-05-06
forum: General Help
---

### Post by nimajiman on 2009-05-06
I am trying to burn a DVD with Brasero but finding it INCREDIBLY slow... like over an hour for 4.1gigs on 4x speed. In the past this would usually take me about 15-20 mins max. Not sure if it's accurate but the speed at the bottom reads at about 0.3x for the process. 

There is also a weird bug where it gets halfway through burning, and then the progress bar disappears and it says it's at 0%, however looks and sounds like it's still burning. I cancelled the first one but when it did it the second time I left it. After what seemed like AGES it started to finalise, then did a 'creating image checksum' which it's been working on for about 20mins now.

I've seen lots of other posts regarding issues with Brasero in Jaunty but none that seemed to be the same as mine.

I'm about to try gnomebaker and see if I have any luck with that but anyone have any clues why it might be doing this?

Cheers

---

### Post by danwood76 on 2009-05-06
I am having similar issues on my desktop.

Not really sure though as mine could very well be a hardware issue, my burner is old and well (ab)used. My laptop doesnt suffer from this.
Although my laptop uses 32 bit and desktop uses 64, so it could be an issue between the architectures.

---

### Post by mick316 on 2009-05-06
Sounds like an issue with DMA - For some reason they decided not to enable it from default, but I cannot find where or how to enable it permanantly.
I have to put this into a terminal (without the quotes) before I can burn a disc at normal speeds:
su
"echo 1 > /sys/module/pata_ali/parameters/atapi_dma"

After a reboot it has to be entered again.

I have not worked out how to load this automatically at startup yet, but it may help you.

---

### Post by danwood76 on 2009-05-07
dma is already enabled on my drive , as it should be for most.
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by nimajiman on 2009-05-07
Yes I checked using commands from the above link and it looks like DMA was enabled for me by default also, so that doesn't explain it.

I tried Gnomebaker last night and besides randomly crashing a few times whilst selecting files for the disk (which appears to be a separate issue in itself!) it burnt as per normal speeds. That is, about 25mins or so for a full DVD at 4x speed.

Not sure why Brasero is playing up but I hope future updates may fix this. I have never had this kind of trouble burning in past releases of Ubuntu, but particularly now that Brasero is more integrated into Ubuntu it would be good to see it working smoothly.

---

### Post by nimajiman on 2009-05-07
> Although my laptop uses 32 bit and desktop uses 64, so it could be an issue between the architectures

Oh yeah I forgot to add I am using 32 bit Ubuntu.

---

### Post by Confuzius on 2009-05-07
I've got the same problem in 64bit Jaunty.
I've only tried brasero so far though.
This has not been an issue in 32bit Fiesty, 32bit Gustsy or 64bit Intrepid.

---

### Post by quickk on 2009-05-07
I have exactly the same problem.  I'm running Ubuntu 9.04.  With 8.10, right-clicking an iso file and selecting "burn to disk" was fast and didn't cause me any problems.  Now, right-clicking brings up a brasero dialogue window instead of whatever program ubuntu 8.10 used to use.  It takes over an hour to burn 3 gigs!  

Is there any way to return to the previous iso burning program that was used in Ubuntu 8.10?

---

### Post by Confuzius on 2009-05-08
I just tried gnomebaker and it works perfectly fine, this seems to be a brasero issue.

---

### Post by wojnicki on 2009-05-08
It's presumably because of the plugins for calculating checksums. There are two plugins. One for file checksums and the other for image checksum. Try to disable them and see whether the performance increases (go to Edit/Plugins)

It helped me a lot! With checksums disabled brasero works as a charm.

---

### Post by nimajiman on 2009-05-09
> **wojnicki said:**
> It's presumably because of the plugins for calculating checksums. There are two plugins. One for file checksums and the other for image checksum. Try to disable them and see whether the performance increases (go to Edit/Plugins)

It helped me a lot! With checksums disabled brasero works as a charm.

Thanks I will give that a try and see how it goes. Fingers crossed it works better for me too.

---

### Post by ok_dr on 2009-05-10
I have the same identical thing happening to me but for the ending. It starts to burn showing a x0.3 speed (but the remaining time doesn't seem to correspond as it shows 20 min and the progress bar moves faster than it should with 0.3).
Then around 50% it starts again from 0% just as described in the thread, at 2-3% it suddenly starts finalising but in my case finalisation is pretty quick and the burned files seem to have been burned all right and the total time for the 2 DVD's I've burnt is 17 min for the first (4.3gb) and 14 min for the second (4.1gb).
So in the end everything has ended well but it still bugs me not to have an idea of the actual progress of the process. I've used previous versions of Brasero (same drive) and have been happy with them, never any problem with dvd (some issues with cd's in version 0.8.1 which resolved installing 0.9).

---

### Post by joey-elijah on 2009-05-13
Ahhh! I, too, am experiencing MORONICALLY slooooow speeds with Brasero: 20 mins to burn a 700mb .iso, burn progress bar dissapering at 50% to 0%, 4gb DVD's take hours and speed reported at 0.3x. 

I will try disabling checksums as per the tip above, thanks!

---

### Post by danwood76 on 2009-05-13
I noticed something quite strange the other day.
Although it was reporting 0.6x 780KB/s the written data was incresing much higher at more like 4 MB/s. Obviously this is still not that fast but I have a feeling this might idicate where the problem lies.

---

### Post by keypox on 2009-05-21
yeah another problem for jaunty, this must be the worse ubuntu release in years...

---

### Post by quickk on 2009-05-24
> **mick316 said:**
> Sounds like an issue with DMA - For some reason they decided not to enable it from default, but I cannot find where or how to enable it permanantly.
I have to put this into a terminal (without the quotes) before I can burn a disc at normal speeds:
"echo 1 > /sys/module/pata_ali/parameters/atapi_dma"

After a reboot it has to be entered again.

I have not worked out how to load this automatically at startup yet, but it may help you.

I tried this and it fails with a "Permission denied" message (and yes, I've typed in "sudo echo 1 > /sys/module/pata_ali/parameters/atapi_dma").   I've never had a permission denied message when using sudo!

---

### Post by quickk on 2009-05-25
I found a solution that worked for me.  I followed the instructions in [this thread]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/328053") (which I quote below).  

> 


Hi,

I had similar speed problems (due to missing dma setting) in my Ubuntu Jaunty installation with my 2 x ATAPI LG DVD Drives on an ASUS A8R32-MVP Deluxe (ULi M1575 Southbridge). I tried these workarounds:

Added
1) "options pata_ali atapi_dma=1" in /etc/modprobe.d/options (new file for me!)
2) "echo 1 > /sys/module/pata_ali/parameters/atapi_dma" in /etc/rc.local

and finally I added
 "pata_ali atapi_dma=1" to "/etc/initramfs-tools/modules"

All these to be sure! :)

After the reboot (the dmesg messages still appear!) the problem was finally solved.
Now I can watch and write DVDs at full speed.

I added a similar comment in an older but similar bug report, in case it helps somebody:
 [https://bugs.launchpad.net/ubuntu/+bug/292142](https://bugs.launchpad.net/ubuntu/+bug/292142)


I'm not why this worked, but it did.  When I type ```
https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/328053
``` I still get the same message about DMA being disabled, along with a bunch of new errors, but my system seems to be working fine now: no choppiness or slowness when I burn a dvd, and my dvd writing speed went from 1.5X to 7X which is pretty close the max speed of my drive.

---

### Post by brillytsang on 2009-07-22
I have the same problem and my DMA has already been enabled.  I've also unchecked the checksum and it's still having problem of 0.3x write speed.  It'll be great if they fix this soon.

---

### Post by bethnesbitt on 2009-07-24
That didn't work.  This is making me so mad, it worked and than all of a suddenly one day nothing out of nowhere.  I hadn't even burned a cd in two weeks and than when I did it would not burn.  My problem is it will not burn multiple files from a directory or an image file.  It will burn an iso to a dvdr but I do not need a dvd with a great big iso on it.  I tried growisofs, nero and braso and nothing works.  I can burn a cdr though with no problem, multiple files and iso.

It's just with the DVDR

:confused:> **Confuzius said:**
> I just tried gnomebaker and it works perfectly fine, this seems to be a brasero issue.

---

### Post by QIII on 2009-07-24
I hate to rain on the generalized "It's a Jaunty 64 bit problem" parade, but I have no problems whatsoever with Brasero -- even at the max speed of my drive.  I haven't made any changes to defaults.

Nevertheless, it could be that there are some incompatibilities with particular hardware.

(And no, Jaunty isn't the worst ever.  That has been said of every release since Warty, depending on who you listen to.  I had the most problems with Edgy.  If you want to complain, do so.  Or, as a more constructive effort, you could get involved with testing new releases.  Like Karmic.  Complaining after the fact is fruitless.  Making a difference at the beginning is valuable.  Let me now step down from my soap box.)

---

### Post by danwood76 on 2009-07-24
> **bethnesbitt said:**
> 
It's just with the DVDR

:confused:

As I said in the other thread I think your drive is at fault.
Try a different burner as it sounds like your DVD-R laser is dying!

---

### Post by aaronsegura on 2009-08-17
> **quickk said:**
> I tried this and it fails with a "Permission denied" message (and yes, I've typed in "sudo echo 1 > /sys/module/pata_ali/parameters/atapi_dma").   I've never had a permission denied message when using sudo!

The problem here is that all you're actually using 'sudo' for is to echo the '1'.  It's still performing the redirect as your user.  Try this:

```
echo 1 | sudo tee /sys/module/pata_ali/parameters/atapi_dma
```

---

### Post by andy350 on 2009-11-16
this just bumped me speed up to 6x
no errors
[http://blog.radevic.com/2009/08/workaround-for-brasero-error-when.html](http://blog.radevic.com/2009/08/workaround-for-brasero-error-when.html)

---

### Post by missmoondog on 2009-11-16
> **keypox said:**
> yeah another problem for jaunty, this must be the worse ubuntu release in years...


easily the worst one!!

brasero has always stunk also, imo.

don't know why in the world k3b isn't the default burning app?!!

---

### Post by NoGroidWare on 2010-07-10
They did it again, about two weeks ago (now running Lucid, FWIW).  Fortunately, it was obvious that it wasn't hardware related.  I had two DVD burners, both working fine, did an update, and instantly both went from burning at 10x to .4x.

This, plus the DOA flashplugin issue for Firefox on Lucid have me keen to look up the Ubuntu release policy.  Both seem like problems that never should have gotten out of the door.  If we're officially the beta testers, then updates need to be aged.  

Between the "we'll get to it eventually" attitude, the pompous groids that can't answer a straight question- or bother to read one right, and the idea that the release schedule is infinitely more important than end user considerations, this is getting more like Microshaft everyday.  If I get time it would be interesting to study the way this product evolved and what is happening in the culture that produces it.

---

### Post by dr20 on 2011-02-12
Brasero was incredibly slow for me in Jaunty as well.  un-installing Brasero and using Gnome Baker instead works great for me.

---

### Post by Scot_Bernard on 2011-04-13
Ubuntu 10.04 Lucyd with all updated, disabling the two checksum plugins goes from 4x to 11x speed in a 24x sony 7240s dvd burner.

Gnomebaker instead, records faster at 16x.

---

### Post by Enigmapond on 2011-04-13
Well I use Brasero in 10.04 and have since 9.04 and it's always worked well and just as a side note. Those of you who are using Jaunty...well, really need to do a fresh install of at least 10.04. Support stopped for apps AND security. So if you are connected to the internet using this version...STOP NOW or continue at your own risk.

Good Luck......

---

