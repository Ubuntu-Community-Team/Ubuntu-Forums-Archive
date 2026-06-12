---
title: "System very slow after upgrade to 9.04"
date: 2009-05-04
forum: General Help
---

### Post by inspired on 2009-05-04
Hi folks,
I did the automated upgrade to 9.04 the other day. Since then my system has been really slow... it'S like the CPU is overloaded or I am running a heap of applications all at once... even when I have just booted up.

The actual boot time seems quick... perhaps even quicker than 8.10, as promised. But once I log in, it can then takes up to a few minutes before I can start using the system.

After that it's just like it is running heaps of stuff and is overloaded... before I even start doing anything with applications.

If I have Firefox and Thunderbird running, then the machine goes pretty sluggishly. Compiz effects are slow enough that they seem unresponsive. 
8.10 ran sweet and fast enough with way more apps going at one time.

I'd love to sort this out.

Watching videos is no longer an option. The system can't render the video quick enough... so it stops and chops and jumps and gets patchy... and so on. I have to watch videos on a Windows XP machine at the moment.

I have a compaq nx7010 with 2GB ram, 4GB of Swap (hardly ever gets touched), and heaps of free disk space. It has a ATI Mobility Radeon 9200. I read about the Intel graphics chip has a known bug that slows compiz down. I gather that does not apply to my ATI radeon chip though.

I have hunted for info on this, and will continue to do so.

For the record: Tracker started giving me a Database corrupted error since the upgrade. It is repetitive. I'll look for solutions to that elsewhere.

I'd greatly appreciate any tips or pointers to info.

Cheers,

Jonathan

---

### Post by freonchill on 2009-05-04
upgrading has been a mixed bag from the posts i have read on the forums here...

if you can (and it seems like it might want to be the thing that you do, due to all of your problems) backup your data and install 9.04 clean rather than upgrade.

---

### Post by NCLI on 2009-05-04
I'd try doing a clean install instead of an upgrade if I were you(you can keep your home directory though), if nothing else works.

---

### Post by inspired on 2009-05-04
Well... it looks like this might be a bug with 9.04 and the ATI drivers.
[http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351186](http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351186)

It seems odd it didn't emerge during all the beta testing... or that no one mentioned it.

Still looking for a solution.  :popcorn:

Jonathan

---

### Post by sinned3k on 2009-05-05
I am experiencing the same problems. 

To date I have uninstalled applications I think might have compatibility issues associated with 9.04 but nothing seems to work.

As suggested above I think a fresh install might help

Any further ideas on this?

---

### Post by lloptor on 2009-05-05
Hi,
I have same problem with ATI MOBILITY RADEON 9200 and open source driver. Maximizing/Minimizing windows is slow and CPU consuming.
I wait for the bug solution.

Regards,
Nacho.

---

### Post by inspired on 2009-05-06
> **NCLI said:**
> I'd try doing a clean install instead of an upgrade if I were you(you can keep your home directory though), if nothing else works.

From what I have read this is a known issue with older ATI chips and Jaunty. Numerous people report that it makes no difference if they do a fresh install or upgrade. Many have tried an upgrade first, and then a fresh install once they ran into the problem. The problem persisted though.

---

### Post by inspired on 2009-05-06
Here is an update..
I following instructions to install the 9.3 ATI catalyst drivers manually (fglrx).
That made my system unusable. It would get a bunch of rainbow colored boxes and mess at the top of the screen once the GUI loaded.

I then followed instructions on uninstalling those drivers.
Got that info from here:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#4._Install_.debs](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#4._Install_.debs).

I got the uninstall info elsewhere.

My system after that is back to more or less how it was before this 9.04 issue.

I know that the xorg file was cleaned out during the install and uninstall. It has no settings in it now. Perhaps that sorted the issue... or perhaps Ubuntu reverted to some other drivers without me knowing what... when I did the fglrx uninstall.

Now I move on to sorting out other issues 9.04 has introduced.

---

### Post by stippi on 2009-05-12
> **inspired said:**
> Well... it looks like this might be a bug with 9.04 and the ATI drivers.
[http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351186](http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351186)

It seems odd it didn't emerge during all the beta testing... or that no one mentioned it.

Still looking for a solution.  :popcorn:

Jonathan

Hi folks,

I too have this problem here and it really helps what Joseph Chereshnovsky@launchpad wrote:
"[...] To avoid this bug I've disabled my desktop effects. Very annoying bug."
I strongly recommend doing so. It helped me to solve the problem for the moment and I will wait till updates and fixes arrive.
greetings
stippi
**++update+++update+++update++**
Found another repository @ launchpad. Insert 'deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main' to your /etc/apt/sources.list'. It helped me a lot on  IBM R51 with ATI Radeon RV250 [Mobility FireGL 9000] :-)
Had some updates installed for the last 5 days. It seems to me as if it works better, now.

---

### Post by utnubuuser on 2009-05-12
Hi  -- I don't suppose:> sudo dpkg-reconfigure -phigh xserver-xorg
helps?

---

### Post by inspired on 2009-05-12
So I managed to fix a big part of the issue by doing a clean removal and reinstall of the opensource ATI videodrivers.

Even though many ATI users are stating they have not found a solution, that pretty much resolved the screen and video issues and the slowness caused by that.

The other part of the issue I discovered is that Tracker has a major bug in 9.04. This is being discussed here: 
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912)
And here:
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560)

I have tried the suggested fix for tracker and shall see how that goes. If it still broken I will uninstall until it is resolved. This was brining many peoples' systems to a standstill.

If you have Tracker installed then look into this also.

Now I just have to resolve the fact that Pulseaudio worked and then completely crapped out.

I shall update here as and when there is news from me on this.

---

### Post by DeMus on 2009-05-12
Have you tried running Jaunty without Compiz? This also is a reason PC's are running slow. Just right-click on your desktop, choose Change Desktop Background, on tab Visual Effects choose none.
Compiz is still installed but all the effects are set to none so you should see a difference.
You could try uninstall Compiz (which you don't need afterall) completely and see if that makes another difference.

---

### Post by cybrsaylr on 2009-05-12
I did an online upgrade to 32bit 9.04 on my dsektop and all went fine, no problems really and 9.04 runs better than 8.10.

This was not the case with my Toshiba AMD laptop.
I did a clean install going to 64bit 9.04 from 32bit 8.10.
Had to fix Adobe and still can't get Opera browser running fast, it lags now but FF is OK. Overall 9.04 boots a bit faster and runs faster but I had to do more tweaking than with my desktop that for the most part just ran good after the online upgrade to 9.04.

---

