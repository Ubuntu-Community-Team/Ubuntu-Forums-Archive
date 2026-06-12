---
title: "dell server ubuntu"
date: 2008-02-06
forum: Dell  Ubuntu Support
---

### Post by eDRoaCH on 2008-02-06
I have been running a wiki here at work powered by ubuntu off a desktop pc under my desk for some time now. I finally get to put it on an actual server in a rack.

It is a Dell Poweredge 2850 xenon 2.8ghz with 1024mb of ram. 4 raid 5 drives = 109gb called 'SCSI3' by the installer. This is obviously well before dell started shipping ubu so sorry if I am in the wrong place.

Anyway I did an install of 6.06LTS server which went smoothly. Upon first login i did sudo apt-get update then sudo apt-get install ubuntu-desktop (im nowhere near good enough not to need a gui) 

The gui runs for a few seconds to minutes and then the front LCD screen goes to "Processor 1 IERR" "Processor 2 IERR"  and the whole system locks. I went to the failsafe terminal and did apt-get dist-upgrade but even after that it still does the same thing. The problem does seem to be only when in GUI.

we have confirmed a windows disk runs fine. It is a 64bit proc, does that mean I HAVE to use a 64bit OS? I know it doesnt on the windows side, and I know windows 64bit isnt nearly as good as 32bit at this time. Any ideas? There are official drivers on Dells site for Suse and RH, but I would rather stick with ubuntu as I am beginning to know it pretty well!

If this is the wrong place for this, could you point me to the right one?

---

### Post by faulkes on 2008-02-06
> **eDRoaCH said:**
> This is obviously well before dell started shipping ubu so sorry if I am in the wrong place.


It's as good as place as any, although you might also want to ask in the server forum.

> 
The gui runs for a few seconds to minutes and then the front LCD screen goes to "Processor 1 IERR" "Processor 2 IERR"  and the whole system locks. I went to the failsafe terminal and did apt-get dist-upgrade but even after that it still does the same thing. The problem does seem to be only when in GUI.

we have confirmed a windows disk runs fine. It is a 64bit proc, does that mean I HAVE to use a 64bit OS? I know it doesnt on the windows side, and I know windows 64bit isnt nearly as good as 32bit at this time. Any ideas? There are official drivers on Dells site for Suse and RH, but I would rather stick with ubuntu as I am beginning to know it pretty well!


AFAIK, you can run the 32bit version just fine under a 64bit cpu.  However, the question comes, why not use the 64bit version of ubuntu?

As for your errors, I haven't seen the like before, however, you might want to check /var/log/Xorg.0.log (or whatever the file is called) and /var/log/messages for any errors the system was able to catch.

Faulkes

---

### Post by sr20ve on 2008-02-06
There's no reason that you have to run 64 bit, those intel EMT64 procs can handle both 32 and 64 bit.

Check whether all system firmware, DRAC firmware, RAID firmware, BIOS are the latest. 

Reseat cables, all peripheral cards, CDROM, hard drives, and riser. 

If you have a DRAC, pull it out. If you have two procs, try swapping them out individually to try to isolate one of them.

---

### Post by eDRoaCH on 2008-02-06
youll have to forgive me- whats a DRAC?

Had the system running fine in windows 2003 so I do not think its a real proc issue, also makes me think it has nothing to do with cabling (and as it is rack mounted, it would be a minor nightmare to play inside) was thinking maybe theres a patch to run on xenons?

I was going to check for an update bios when I get a chance today, but work doesnt offer too much playtime so I may have to stay late to do it

---

### Post by az on 2008-02-06
The server kernel may not support your desktop hardware.  (mouse, keyboard and video card.)

Boot into recovery mode and install the linux-generic kernel.  The Dapper installer uses the linux-386 kernel, but installs the linux-server kernel.

Dapper:  apt-get install linux-386

Anything after Dapper, the kernel was renamed to linux-generic.
apt-get install linux-generic

---

### Post by eDRoaCH on 2008-02-06
apt-get install linux-generic package not found?

er nevermind, trying to read while on the phone with customers isnt very conducive to understanding....

linux-386 seems to have done the trick, thanks much! I played around a bit and am leaving it running just to make sure.

---

### Post by sr20ve on 2008-02-06
> **eDRoaCH said:**
> youll have to forgive me- whats a DRAC?

Had the system running fine in windows 2003 so I do not think its a real proc issue, also makes me think it has nothing to do with cabling (and as it is rack mounted, it would be a minor nightmare to play inside) was thinking maybe theres a patch to run on xenons?

I was going to check for an update bios when I get a chance today, but work doesnt offer too much playtime so I may have to stay late to do it

DRAC = Dell Remote Access Controller.

Try this, these are RPMs, but you should be able to extract the files or use alien:

**ATI Radeon 7000M, Driver, Enterprise Linux 3, Enterprise Linux 4, English, Multi System, v.radeon7000_RH_A10, A10**
_[http://ftp.us.dell.com/video/r7000(m)-A10.tar.gz](http://ftp.us.dell.com/video/r7000(m)-A10.tar.gz)_

_Fixes and Enhancements _
 
MAJOR Fixes Carried over from A09: When launching RHL3 and RHL4 GUI (startx)
DFCT151964 - SERR issue which was related to a Bus Mastering Operation the ATI chip was performing when it should not have been.

DFCT153487 - **IERR issue** that was caused by the ATI chip's BAR being reprogrammed in Linux causing the ATI to respond to addresses that were not its own.

Minor Fixes:
Fixes Sev3 issues: Windowing issue and Mouse tracking failure on RH3.
-IERR patch provided by Dell which implements a workaround for an issue in radeon_bios.c
-"Conflicts" line to allow a newer ATI supplied .rpm to be installed over an older ATI suppled .rpm 
-Kudzu-hang fix (pcitable)
-Updated readme-file
 

taken from:
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R109502&SystemID=PWE_PNT_P3C_2850&servicetag=&os=LIN4&osl=en&deviceid=5859&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=6&fileid=144810](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R109502&SystemID=PWE_PNT_P3C_2850&servicetag=&os=LIN4&osl=en&deviceid=5859&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=6&fileid=144810)

---

### Post by eDRoaCH on 2008-02-06
right now everything seems to be working. I just went over and changed my background to 'dawn of ubuntu' from the web just to test things out, and so far so good.

Since everyone's so helpful, I am also interested in load balancing the 2 intel nics, any ideas on how to do that? One thing to keep in mind is when I am ready to 'go live' i need to give the IT dept a mac adress to reserve a dhcp address for.

---

### Post by faulkes on 2008-02-06
> **eDRoaCH said:**
> right now everything seems to be working. I just went over and changed my background to 'dawn of ubuntu' from the web just to test things out, and so far so good.

Since everyone's so helpful, I am also interested in load balancing the 2 intel nics, any ideas on how to do that? One thing to keep in mind is when I am ready to 'go live' i need to give the IT dept a mac adress to reserve a dhcp address for.

It depends what your definition of 'load balancing" is, or how you intend to apply it, if you want both nics to share all  traffic (send/receive), then that is a routing issue.  On the other hand, if you want to load balance the applications that bind to those nics, that is usually something external (i.e. a load balancer).

The simplest way if it was just routing, would be to create two equal path default routes in the routing table.  You should be able to do that without having to deal with any routing protocols (ospf, etc..) - the only real caveat is that you won't get to choose which one responds to a request and which one sends data out or vice versa (depending on if route caching is on).

Alternately, you could use DNS to round-robin

i.e. 
mymachine.com IN A 10.1.1.1
mymachine.com IN A 10.1.1.2

Faulkes

---

