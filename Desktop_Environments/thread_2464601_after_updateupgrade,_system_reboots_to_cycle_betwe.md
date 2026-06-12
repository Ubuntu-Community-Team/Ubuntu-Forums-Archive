---
title: "after update/upgrade, system reboots to cycle between text &amp; graphical (cannot login)"
date: 2021-07-06
forum: Desktop Environments
---

### Post by Khelair on 2021-07-06
The problem that I am having is on Xubuntu 20.04.  Since approximately last week Wednesday, or even a little earlier, the machine, when rebooted, gets to the end of the boot process, flashes a text console with the filesystem attributes, then switches to a graphical console showing a black screen with a mouse cursor, and then endlessly cycles between the two.  After several times rebooting it, including multiple times into rescue mode, to try to diagnose the issue, it did, on one boot, display the session manager window asking for login/password credentials when cycling between graphical & text modes.  It cycles too quickly to be able to enter any information, even if it did stay on one of the ttys.  Trying to switch to a standard text console via keypress, or even console 7 (where my session manager or desktop normally resides) does nothing, the cycling behavior continues with no obvious changes.  Rebooting does not occur by simply pressing ctrl-alt-delete; you have to hold it down before it is able to signal shutdown, with whatever flags that are signaled with the repeated keypress detection.


Before this issue came up, the machine had been up for at least a couple of weeks, during which I had run '```
apt update; apt upgrade
```' several times.  One of the times was the same day that this reboot occurred, but I don't think there is any real way to know whether or not this issue was caused by any of the upgrades since the boot prior to that.  There had been no tinkering with any configuration files that would've had an effect in the X display manager loading process.


Googling this problem has not turned up anything that seems relevant.  However, there was one session manager cycling issue that kept turning up, no matter how I tried to reword my search terms, so it is definitely possible that this issue was masking the result(s) that I was looking for.  I followed at least a dozen different links that seemed like they had a chance (albeit small) of being related to what I had going on, but with more detailed examination none were related.


Also, it should be noted that I am utilizing an nVidia GTX 1080 graphics card.  I tried looking up information specifically relevant to that hardware, as well, and found nothing.  :(


I booted into rescue mode several times, examined everything that would be relevant in /var/log, and couldn't find the slightest indication of anything amiss.  At one point, I did realize that my root partition was below 5% available, so I freed up space on there, but this didn't change the situation at all upon rebooting.  I really don't have a clue where to go next in trying to diagnose this issue, let alone fix it.  Normally I can turn up something; I've been using Linux since the mid 90s, so I've usually got a fairly decent grasp on at least knowing how to look for the information that I need.


I had to sit with this issue a bit due to multiple 'roaring fire' level issues that I had to take care, of prior to concentrating on this more than just the couple of hours that I did previously.  The issue originally came up at some point early last week.  At this point I do have time to concentrate on it a bit, but summer school classes are just hitting full swing, and I can't really devote enough time to make sure my backups contain everything (including the class notes I've been taking on a wiki instance that I run on that machine)...  That'd entail detailed examination of 6-8TB of data, at this point.  So needless to say, I'm really hoping to avoid the 'windows solution' of reinstalling the operating system.  I mean that's one of the fundamental reasons I love linux, anyway; avoiding nuke & restart as a common method to solve configuration/OS issues, I mean.


Does anybody have any ideas of where I can find more detailed log information to assist in troubleshooting, or even where I might be better able to find information relevant to this particular issue?  I'm at a total loss here, and I really need to get this system up and running as soon as possible to access my data.  I would greatly appreciate anything that anyone might be able to offer!


TIA!

---

### Post by ActionParsnip on 2021-07-07
If you boot to an older kernel, does it help?

---

### Post by zircon_34 on 2021-07-07
Some infos on hardware/drivers may help trouble shooting. Please post output of:
 inxi -b

lately I had a problem with nvidia, during a kernel update. I had to tty and just typed startx, then could access the gui to fix my card drivers. A lot of times I see posts where users have to reinstall their nvidia driver which fixes the issue in most cases. Nvidia on linux is a real pain and works well on windows because of their proprietary drivers, which makes it hard to maintain on linux.

---

### Post by Khelair on 2021-07-07
Nope.

---

### Post by Khelair on 2021-07-13
> **ActionParsnip said:**
> If you boot to an older kernel, does it help?

Really sorry that it took me so long to respond here, I've just had one fire to put out after another here.  :(

Got a chance to try the previous kernel and it did nothing.  However, if you'll read down into the next reply I leave here, there is some more information that I've been able to get ahold of concerning the situation now.

---

### Post by Khelair on 2021-07-13
> **zircon_34 said:**
> Some infos on hardware/drivers may help trouble shooting. Please post output of:
 inxi -b

lately I had a problem with nvidia, during a kernel update. I had to tty and just typed startx, then could access the gui to fix my card drivers. A lot of times I see posts where users have to reinstall their nvidia driver which fixes the issue in most cases. Nvidia on linux is a real pain and works well on windows because of their proprietary drivers, which makes it hard to maintain on linux.

As I just mentioned to another helpful soul, sorry that it's taken me so long to reply here, I've had just one emergency after another to deal with for a ridiculously long time now.  Can't believe my stretch of luck.

I'll be posting in a bit with a little bit more information that I'm trying to compile from journalctl right now, too...

Here's the output that I got from 'inxi -b', after using 'sudo systemctl stop lightdm' to keep the display from constantly trying to switch between text & graphical:

[FONT=lucida console]sprite@d-resources:~$ inxi -b[/FONT]
[FONT=lucida console]System:    Host: d-resources.hopto.org Kernel: 5.4.0-77-generic x86_64 bits: 64 Console: tty 0[/FONT]
[FONT=lucida console]           Distro: Ubuntu 20.04.2 LTS (Focal Fossa)[/FONT]
[FONT=lucida console]Machine:   Type: Desktop System: Gigabyte product: B250M-DS3H v: N/A serial: <superuser/root required>[/FONT]
[FONT=lucida console]           Mobo: Gigabyte model: B250M-DS3H-CF v: x.x serial: <superuser/root required> UEFI [Legacy]: American Megatrends[/FONT]
[FONT=lucida console]           v: F6 date: 04/24/2017[/FONT]
[FONT=lucida console]CPU:       Dual Core: Intel Pentium G4600 type: MT MCP speed: 800 MHz min/max: 800/3600 MHz[/FONT]
[FONT=lucida console]Graphics:  Device-1: NVIDIA GP104 [GeForce GTX 1080] driver: nvidia v: 390.143[/FONT]
[FONT=lucida console]           Display: server: X.org 1.20.9 driver: nvidia unloaded: fbdev,modesetting,nouveau,vesa tty: 168x44[/FONT]
[FONT=lucida console]           Message: Advanced graphics data unavailable in console. Try -G --display[/FONT]
[FONT=lucida console]Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169[/FONT]
[FONT=lucida console]Drives:    Local Storage: total: 6.37 TiB used: 1.91 TiB (30.0%)[/FONT]
[FONT=lucida console]Info:      Processes: 212 Uptime: 19m Memory: 31.33 GiB used: 2.56 GiB (8.2%) Init: systemd runlevel: 5 Shell: bash


[/FONT]

---

### Post by Khelair on 2021-07-13
So, at this point, this is what I've got for additional troubleshooting information on this issue:

I'd love to post the output of *journalctl -xe *here, but it's a pretty damn long bit of reading... To summarize what I'm seeing right now, **lightdm **is failing with *status 1/FAILURE*, then scheduling a restart, and on, ad infinitum.


**gpu-manager.service** is doing the same with the only output in *journalctl* being '*Finished Detect the available GPUs and deal with any system changes.*'


**nvidia-persistenced** is doing the same; it gets a *signal 15* and helpfully adds '*The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced*'.


That's a really brief summary.. If you'd like me to post a relevant chunk that shows all of that from the full output, please let me know. Or I can post the whole thing, too, but I'm not even sure that that'll fit in the post max length here.


Very grateful for anything you may be able to offer here! Thank you!

---

### Post by him610 on 2021-07-13
> Graphics: Device-1: NVIDIA GP104 [GeForce GTX 1080] driver: nvidia v: 390.143
I believe driver: nvidia v: 390.143 has been deprecated. 
I am on LTS 20.04.2 this is what mine looks like...
```

Graphics:  Device-1: NVIDIA GK104 [GeForce GTX 760] driver: nvidia v: 460.80 

```
You should be able to upgrade your driver to v 460+ from Settings->Additional Drivers. You may need to purge/remove all currently installed nVidia drivers though.

Although some folks disparage nVidia graphics cards, I have never had any issues with them. I currently have two systems with older nVidia cards which work fine with latest drivers from repository.

---

### Post by Khelair on 2021-07-14
> **him610 said:**
> I believe driver: nvidia v: 390.143 has been deprecated. 
I am on LTS 20.04.2 this is what mine looks like...
```

Graphics:  Device-1: NVIDIA GK104 [GeForce GTX 760] driver: nvidia v: 460.80 

```
You should be able to upgrade your driver to v 460+ from Settings->Additional Drivers. You may need to purge/remove all currently installed nVidia drivers though.

Although some folks disparage nVidia graphics cards, I have never had any issues with them. I currently have two systems with older nVidia cards which work fine with latest drivers from repository.

Hrm, I thought I wasn't going to be able to access X at all with the way things were going.  I guess I haven't tried using 'startx' from the command line, though, since I got things somewhat more stable by stopping 'lightdm'.  You know, I'm a little ashamed to admit that with the lack of time I've had to pursue this issue, I haven't had much of a chance to research what individual package might be responsible for that driver version...  Do you have any idea of how to go about this with 'apt' on the command line if I'm still unable to access X?

TIA & thank you for the additional information!

---

### Post by him610 on 2021-07-15
Okay, here is what I think needs to be done - 
First, take a look to see what *nvidia* related files you have...
```
dpkg -l nvidia*
```
You will see a listing that looks similar to this... (Listing has been cropped)
```

$ dpkg -l nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version                    Architecture Description
+++-================================-==========================-============-==============================>
un  nvidia-384                       <none>                     <none>       (no description available)
un  nvidia-390                       <none>                     <none>       (no description available)
un  nvidia-common                    <none>                     <none>       (no description available)
un  nvidia-compute-utils             <none>                     <none>       (no description available)
ii  nvidia-compute-utils-460         460.80-0ubuntu0.20.04.2    amd64        NVIDIA compute utilities
ii  nvidia-dkms-460                  460.80-0ubuntu0.20.04.2    amd64        NVIDIA DKMS package

```
Second, you can remove some or all of the nvidia files. If it were me, I would remove them all - keeps one from playing guessing games. 
```

dpkg -r nvidia*

```
Third, reboot your machine so the open source driver for graphics loads then after it has booted:
```
sudo apt update
```
Fourth,  go to Settings->Additional Drivers; install the appropriate NVidia software
It should look similar to this ...
[https://imgur.com/ppatxdx.png]("https://imgur.com/ppatxdx.png")

Note: To anyone else who reads this post, if I have given faulty instructions - please provide corrections as necessary. Thanks

---

