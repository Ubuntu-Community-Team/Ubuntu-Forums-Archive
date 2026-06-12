---
title: "nvidia-current broken...at my wit's end...."
date: 2012-07-10
forum: Desktop Environments
---

### Post by mbobak on 2012-07-10
Runnng Ubuntu 12.04 x86-64, with:
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9500 GT] (rev a1)


So, a while ago (2-3 months?), I noticed that every time I  did an 'apt-get update' and 'apt-get dist-upgrade', I'd see that 'nvidia-current' was "held back".  Everything seemed to be working ok, so, I just let it be.

Tonight,I decided to try to dig into it.  (And now I'm regretting that decision.)

There seems to be a dependency on 'xorg-video-abi-11', which doesn't seem to exist?

I tried removing nvidia-current (which was successful), and re-installing (which failed), so now I have no nvidia-current at all.

Here's some info on where I currently stand:
```
mjb@mars:~/Downloads$ apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1
  Version table:
     295.40-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages
     295.33-0ubuntu1+xedgers~precise1 0
        100 /var/lib/dpkg/status
mjb@mars:~/Downloads$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11
E: Unable to correct problems, you have held broken packages.

```
I'm not sure where the xedgers reference in the apt-cache output is coming from?  I may have played with that repo a long time ago, but I definitely don't have any reference to it anywhere under /etc/apt/*.  Perhaps there's still something cached somewhere, from when I had that repo configured?  Not sure where to look or what to check.

Help!  I'm at the end of my rope here.  No idea where to turn next.

Been googling for hours, and so far nothing.

Any thoughts, ideas, or suggestions would be appreciated.

AdvThanksance,

-Mark

---

### Post by mbobak on 2012-07-10
Ok, I tried:
```
mjb@mars:/var/lib/dpkg$ sudo dpkg -P nvidia-current
[sudo] password for mjb: 
(Reading database ... 372835 files and directories currently installed.)
Removing nvidia-current ...
Purging configuration files for nvidia-current ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
```

and now apt-cache shows:
```
mjb@mars:/var/lib/dpkg$ apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1
  Version table:
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
```

with no odd references to xedgers, which I thought was a good thing.

However, I still get:```

mjb@mars:/var/lib/dpkg$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11
E: Unable to correct problems, you have held broken packages.
```

---

### Post by mbobak on 2012-07-10
Still stuck....any suggestions, anyone?

---

### Post by haresear on 2012-07-10
I'm not that knowledgeable with the current nvidia drivers, but I thought I read in another post that the current (Ubuntu 12.04) xorg xserver uses version xorg-video-abi-12. I'm pretty sure that the latest nVidia drivers are later versions than 295.40, but I guess Ubuntu hasn't incorporated them yet for some reason. You might find some useful information on recent nVidia drivers in this nVidia forum:

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

---

### Post by mbobak on 2012-07-10
Ok, well, I switched back to X edgers PPA, did an update/dist-upgrade/install nvidia-current, and it worked fine, and I'm on the much updated 320-17 version.

So far, so good.

-Mark

---

### Post by robtygart on 2012-07-11
> **mbobak said:**
> Ok, well, I switched back to X edgers PPA, did an update/dist-upgrade/install nvidia-current, and it worked fine, and I'm on the much updated 320-17 version.

So far, so good.

-Mark

Mark

Could you please post that PPA? 

With my Laptop when I use Nvidia-current Kubuntu will not load. Only in failsafe mode. 

So right now I am usings (post-release updates)

Maybe I can get that one to work..

Thanks 
Rob

---

### Post by markbl on 2012-07-11
> **robtygart said:**
> 
Could you please post that PPA?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Ensure you read the description there before you add it.

---

### Post by mbobak on 2012-07-11
Thanks Mark.

Yeah, you definitely want to go in with both eyes open. xorg-edgers is pretty bleeding edge stuff.  I'm happy that it got me past my problem, but, if Ubuntu ever resolves the dependency issue I was having, I'll probably switch back to stock Precise repositories.

-Mark

---

### Post by robtygart on 2012-07-11
Thanks Mark 

I know it says not to, :biggrin: But is it possible to only use that PPA's Nvidia-Current?

---

### Post by mbobak on 2012-07-11
I don't know.  I followed their advice.

So, I did the following:
1.)  Install PPA.
2.)  sudo apt-get update
3.)  sudo apt-get dist-upgrade  <-- This installed and upgraded a whole boatload of stuff.
4.)  sudo apt-get install ndivia-current

So far, so good, working great, I have a much upgraded kernel (3.5....something), among many other very bleeding edge (but so far stable) packages.

-Mark

---

### Post by markbl on 2012-07-11
> **mbobak said:**
> 
So far, so good, working great, I have a much upgraded kernel (3.5....something), among many other very bleeding edge (but so far stable) packages.
Be aware that xorg-edgers ppa is very volatile so be prepared for things to break. For example, I currently can not use nvidia driver due to bug [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096) so am using nouveau. However, currently nouveau driver locks up my system after a couple of hours if I use the 3.5 kernel installed by xorg-edgers, I have to pin back to the generic 3.2 kernel. These kind of bugs have happened to me on previous ubuntu releases where I have used xorg-edgers ppa.

---

### Post by mbobak on 2012-07-12
Thanks for the warning, Mark.

I'll probably just leave it w/ x edgers till something horribly breaks, then roll back to stock Ubuntu and hope my nvidia-current problem is solved there.

In my case, as a side effect, it actually fixed two other minor issues that I was suffering with.

This is a HTPC system, and, every time I booted, it would lockup with a blank screen, from cold boot.  I'd have to boot, wait for lockup, then warm reboot, and it would be fine.  No idea why.

Second, if I turned off my monitor, the system would lock up.

With x edgers, the 3.5 kernel and the new nvidia driver, both those problems have disappeared.

So, I'm a little bit afraid of new problems, but, so far, it's fixed multiple problems for me.

I'll keep a close eye on it.  As I said, it's an HTPC, and my primary way to watch TV, so, stability is pretty important to me.

-Mark

---

