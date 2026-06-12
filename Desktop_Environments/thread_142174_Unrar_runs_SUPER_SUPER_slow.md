---
title: "Unrar runs SUPER SUPER slow"
date: 2006-03-09
forum: Desktop Environments
---

### Post by evilregis on 2006-03-09
I'm trying to unrar an archive.  First I tried just using the GUI by double-clicking the archive.  The files all appeared properly and with their proper sizes.  They vary in size from 1.5MB to 125MB.  So I right clicked the largest file (the one I need) and told it to extract it.

I sat... and sat... for a few minutes all the while my computer was grinding to a halt.  So I cancelled it.  I thought maybe it was just the GUI.

So I opened up the terminal (which I actually prefer as I find I learn a lot more in there than in any GUI) to try that.

$ unrar x ~/media/animations.rar

It created the file's directory structure and started extracting.  The largest file happens to be the first file alphabetically.  So it starts to extract it.  And it was literally taking 5-10 seconds per 1 percent.

That can't be right, can it?

In Windows I could extract the entire contents of this archive in the time it was taking this to do 1% of one of the files in the archive.

Am I doing something wrong?

Nothing else hangs my system.  It's been running beautifully so far so I'm at a loss as to what might be causing this other than it being business-as-usual as far as unrar'ing goes.

---

### Post by evilregis on 2006-03-10
Upate:  I uninstalled rar and then reinstalled it and I receieved the same results as noted above.

Is rar just THAT SLOW in linux?  I have a hard time believing that it is.  I can't imagine anyone using it if it is.  No other archive formats are running this slow.

When I was running Windows I archived most of my documents and media in rar format and I am fearing the time wasted when I am required to extract a particular archive.

ANY help or ideas?

---

### Post by magnusbb on 2006-03-10
Install WINE and run WinRAR through it. It's super fast, and works great.

---

### Post by evilregis on 2006-03-10
Thanks.  I will try that.  I wonder if I can get PokerStars.net running in wine too.  :D  I smell a distraction coming on.

---

### Post by KnottyMan on 2006-03-10
Just to chime in here, I've never had speed issues with rar under linux.  "rar x <archive>" and it tears through single and multi part archives just fine.

How is the rest of the system?  Can you play DVDs ok?  Might look at DMA settings.  hdparm -i /dev/hda

---

### Post by Lord Illidan on 2006-03-10
[quote=KnottyMan]Just to chime in here, I've never had speed issues with rar under linux.  "rar x <archive>" and it tears through single and multi part archives just fine.

How is the rest of the system?  Can you play DVDs ok?  Might look at DMA settings.  hdparm -i /dev/hda[/quote]

Here is a link : [https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

rar works fine with me, unrarred a bunch of avis in seconds.

---

### Post by evilregis on 2006-03-10
Everything else is running great.  I've not watched any DVDs on it yet, but there's been no problems as far as system speed so far.  As I said, extracting bz2 or tars is lightning.  Just rar has been hanging me up.

I tried installing WinRAR in wine to no avail.  From the looks of the error and some google searches I need to downgrade Xorg?  Yeah.  May as well tell me to split atoms.  :D  I've done the DMA thing that was linked to and I'm going to see how that works out.

Thanks for the help thus far.

---

### Post by oLdsk3wL on 2006-11-10
Hi,

we also have a discussion going on about unrar/unace/unzip in the German ubuntu forum. Unrar runs very slow, and according to the German moderators there is no alternative. We have to just deal with it. My question is, why there is no alternative. I mean extracting is daily business and very important, so I can't believe that there is no better solution to just use wine. Is it really true that Linux/Ubuntu do not have a good and fast extractor.

Also the progress bar is not very user friendly. Ok, it indicates that there is something going on, that's it. The progress bar should show how much work is done, and how much work has to be done. :D 

Is it not possible to use an existing extractor (like 7zip), and simply create a Linux version? I could imagine that this is not that hard. The core (the algorithm of the extractions( should be portable, so the only thing that needs to be done, should be the GUI.

---

### Post by Efros on 2007-02-25
Just to chime in, it is ridiculously slow, also extremely uninformative, no progress on unrarring is reported not even a dialog indicating success. Anyone tried an alternative?

---

### Post by frc on 2007-11-06
Unrar has become even more slowly when I upgraded to gutsy form feisty.
It takes about 5 to 6 minutes for 700Mb
On a dual core 2.66ghz 1gb memory
And yes the  progress bar should at least show how much work is done, and how much work has to be done.  [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by nlindblad on 2007-11-17
> **oLdsk3wL said:**
> Hi,
My question is, why there is no alternative. I mean extracting is daily business and very important, so I can't believe that there is no better solution to just use wine. Is it really true that Linux/Ubuntu do not have a good and fast extractor.

I'm sure developers would love to develop a better and improved utility for handling RAR-archives. The problem is that the file format (and compression algorithm) is proprietary.

The 'unrar' program distributed as freeware by RARLAB is obviously slower and offers less usability, because they want people to buy the shareware version (which is not available for *NIX as far as I know). 

But I agree with you, unpacking multi-volume RAR-archives is a nightmare.

---

### Post by devotee on 2007-11-25
Something wrong is happening with rar/unrar on modern Linux distributions.

I archived about 3GB+ in a multi part (1GB / part) rar archive. I tried to extract it on two different Linux systems I'm running:

Slackware 11.0.0
Linux test 2.4.34.2 #1 Wed Mar 28 02:45:31 MEST 2007 i686 pentium4 i386 GNU/Linux
Using rarlinux-3.60

real    1m7.715s
user    0m17.810s
sys     0m5.750s

Slackware 12.0.0
Linux test2 2.6.21.5-smp #1 SMP Tue Jun 19 14:52:25 CDT 2007 i686 Intel(R) Pentium(R) 4 CPU 1.60GHz GenuineIntel GNU/Linux

It's been running for more than 20 minutes and is still stuck somewhere in the middle of the second volume (r00). It's going on, but it lags to desperation.

The most ridiculous thing is that I didn't use compression (-m0, store), so the extraction should be very fast. It's not a dma/system problem, the rar process is almost inexistent (1.9 %cpu, 0.0 %mem, 7132 VSZ, 1132 RSS) so it's not a high-demanding process problem.

On Slackware 11.0.0 (2.4 kernel), the process uses more resources while extracting (33.2 %cpu, 0.1 %mem, 7432 VSZ, 596 RSS). No wonder why it's so fast there :P

I would say that the problem kicks in when using rar with a recent 2.6 kernel. I don't know if the problem is somewhere in the kernel, or if the rar command line application has been poorly ported to/compiled on 2.6 kernel.

The fact is rarlinux + 2.4 = fast, rarlinux + 2.6 = sloooooooow.

While writing this it went on to another volume, it's taking about 15+ minutes per volume (when the whole lot was extracted in about 2 minutes on the other system). Something is definitely wrong here. My bet? Rarlinux don't like 2.6 kernels. Do the folks at rarlabs know about this issue?

Kind regards.

---

### Post by gfg on 2007-12-20
Having the same problem. Does anyone know if there is a solution to this? It's a bit over the top when it takes 5 minutes to extract an archive of 300mb.

---

### Post by likeatim on 2008-02-14
shouldn't the 7zip archiver be able to work with rar?
and isn't it opensource?

[www.7-zip.org](www.7-zip.org)

---

### Post by confy on 2008-03-24
same problem here!
It's interesting that my IOwait jumps very high!

confy@live:~$ uname -rm
2.6.22-14-generic x86_64

---

