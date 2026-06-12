---
title: "Dell Vostro V131"
date: 2011-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by erlguta on 2011-08-19
I open this post to discuss about the new Vostro 131 and Ubuntu installation.
Somebody is planning to install Ubuntu in this laptop?
Would be nice to make a review about:
- Overall performance
- Peripherals (wifi, vga)
- suspend/hibernate
- Battery life with ubuntu
- Fan noise
- media buttons and fingerprint
etc.

---

### Post by svenskmand on 2011-08-21
I was thinking about buying this laptop, so it would be nice with some updates. According to the [Ubuntu Certification it seems to only work with the preinstalled Ubuntu]("http://www.ubuntu.net/certification/hardware/201105-8048:201105-8049:201105-8050").

---

### Post by DIFORT on 2011-08-26
Same question. I want to buy this laptop but I am not sure because some sites say that the screen is bad, isn't it?

And I am interested to install Ubuntu too.

---

### Post by svenskmand on 2011-08-30
Bump

---

### Post by erlguta on 2011-09-01
seems that nobody wants to take the risk being the first in buying it and test it with ubuntu...

---

### Post by mervinb on 2011-09-02
I was just waiting for delivery ;) ;)
Installed xubuntu natty on my i5 vostro v131.

- Boot, networking, touchpad seem fine
- Performance good, not stellar (expected an i5 to feel much snappier than my Studio 1537, but actually feel similar)
- xorg-edgers drivers seem to boost graphics measurably (extreme tux racer up 50% in fps)
- matte display cuts down reflections, but has a narrow field of view. Outside this FOV the screen looks weak. Within the FOV it's ok, but not great.
- Cool, quiet
- Happy with 3.0 liquorix kernels 
- Love the keyboard

Under investigation:
- resume after suspend: sometimes cannot login after wakeup (keyboard seems to 'jabber' on xscreensaver re-login)
- keyboard autorepeat lost after resume

Summary:
Good performance, generally good linux compatibility, except for keyboard resume from suspend.

---

### Post by erlguta on 2011-09-02
Thank you for your review mervinb!.
When you say networking seem fine, is that wifi works out of the box?.
It is needed some restricted drivers for the wifi or video?.
The overall performance and compatibility seems good.
Hope you fix the resume from suspend because suspend is one very important feature for one laptop.
What about hibernate?. Have you tested it?
Stay us tunned, please!
Thenk you.

---

### Post by mervinb on 2011-09-02
My bad... the resume problem appears only with liquorix kernels. It seems to work with the generic ubuntu kernel.

Wifi works out of the box.

I've not used hibernate for several versions of ubuntu, since the suspend behaved properly. 

Given that the vostro v13 had touchpad issues that only got fixed recently, the v131 works really well with natty. I'll be testing a usb image of oneric beta next.

---

### Post by erlguta on 2011-09-02
And the battery life is so good in Ubuntu as they say in windows?.
9.5 hours for one Dell...mmm I don't believe if I don't see it...
If this is true I think I am going to order mine today!

---

### Post by mervinb on 2011-09-03
I hope that everyone takes my comments with a pinch of salt... YMMV!

Ubuntu power consumption seems determined by kernel versions (see phoronix posts), and I saw ~4 hrs with a 3.0 kernel, which has the power regressions. Seems to me that I'd get ~5+ or 6 hrs with 2.6.38, again depending on usage. Whatever it is, it is hugely better than the V13 or other Dells I have.

I doubt I'd see 9 hours on W7. Perhaps 7-8 hrs??

Suspend update: there are still some resume problems (keyboard repeat) occurring intermittently. These days boot time is good enough that I'm getting much less sensitive to it, and the more users of v131 are on ubuntu, the better the chance of tracking down and squashing the bug.

---

### Post by svenskmand on 2011-09-04
Thank you very much for the details, now I will definitely buy this notebook :)

Could you give all the specs of the laptop you bought please? (Cpu, graphics, wifi, etc.)?

And also its model number, e.g. like N0913101, the last two digits is variable across model, i think.

Thanks :D

---

### Post by mervinb on 2011-09-06
Please don't use my specs or anyone else's, as Dell may sell different configurations in various geographies.

I have the i5 CPU, 4G ram, upgraded to 500G disk. Graphics is always intel onboard graphics, HD3000 or HD2000 depending on CPU.

Very important: red exterior casing! ;)

---

### Post by nbr on 2011-09-08
Thanks, mervinb, for this write up!

Would you mind commenting on fan noise and activity on your V131?
I read somewhere that the fan kicks in with light activities like web browsing. Do you notice this in your unit?

Just to confirm, the touchpad works fine? You can even disable clicking with double tap (unlike the problematic V130)?

Thanks again!

---

### Post by mervinb on 2011-09-08
The fan noise is excellent (low / very low, by my ears). I have an awful Studio 15 1537 that makes a huge noise (W7 and ubuntu, with latest BIOS). The V131 is much quieter, close(r) to silent.

I don't use the touchpad other than in standard mode, and it works fine.

The sleep issues can be a problem for some. I'm using xfce or openbox with xscreensaver, and when xscreensaver kicks in (due to a signal??) the keyboard repeat issue appears. If I just suspend the system using pm-suspend, the resume works fine, with the keyboard waking up with autorepeat.

Even though the V131 is 'new', there are already a lot of driver updates from Dell (for Wind*ws) including a revised BIOS, most at 'urgent' level. I hope the V131 gains a lot of ubuntu users. It's a sure way of getting attention for the niggling keyboard wakeup issue.

---

### Post by RobertSwipe on 2011-09-12
Just installing on a new V131....

My V131 has no CD/DVD so I attached a USB DBD drive, but was unable to boot from this at first. The process would dump me into BusyBox (initramfs) saying "No media found" (or similar).

Eventually I read somewhere that the live CDs cannot boot in a USB3 socket, and when I switched to the single USB2 socket it all worked perfectly.

Right now, I'm obliterating the Windows 7 installation that came pre-installed, and replacing with 11.04. The Unity desktop has correctly identified the 3D graphics environment, sound seems to work, and the wifi has connected happily.

So far, so good!

---

### Post by Whoopie on 2011-09-20
Hi,

could someone post the lsusb and lspci output? I'm interested in the hardware details.

Nevermind, I found the information [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/852918").

Thanks in advance,
Whoopie

---

### Post by mervinb on 2011-09-22
Some good news. With the latest 2.6.38 generic kernel for natty pushed out a day or two ago, I now get perfect sleep and resume with gnome-power-saver. That addresses the only hardware compatibility issue I've noticed. 

Please be aware that I have not tested HDMI output yet though.

---

### Post by Whoopie on 2011-09-23
Hi,

I also bought the V131. The following components are not yet working:

- fingerprint reader (Validity VFS5011, no driver for fprint available)
- 3 function keys in the up right corner
- accelerometer (I haven't found out which STMicrosystems chip it is, it's shown as ACPI SMO8800 device)

Best regards,
Whoopie

---

### Post by nbr on 2011-09-26
Hi Whoopie, thanks for sharing this information!

How do you like the laptop with Ubuntu for now? What's your general impression?
Can you comment on heat and fan activity too?
Thanks a lot!

---

### Post by terraner on 2011-09-27
Hi,

just bought a V131, too. Now i wonder what to do to use cool multi touch gestures like pinch zoom under Natty just like under preinstalled W7? Does it work for anyone else? I can only enable two finger scrolling...

Thanks! =)

---

### Post by erlguta on 2011-09-28
How many hours is the battery life with one starndard ubuntu-desktop (11.04)?

---

### Post by Karl S. on 2011-10-14
Hi,

Mine just arrived a couple days ago, and now I'm very tempted to upgrade to 11.10. But I want someone else to do it first...

---

### Post by sojusnik on 2011-10-15
I would like to know how the fan is behaving with 10.11 and how silent the whole notebook is with an SSD installed?

---

### Post by svenskmand on 2011-10-16
> **Karl S. said:**
> Hi,

Mine just arrived a couple days ago, and now I'm very tempted to upgrade to 11.10. But I want someone else to do it first...

Just download it and run it from a USB Pen as a "Live CD", if it works there it should work fine if you upgrade ;)

---

### Post by Karl S. on 2011-10-17
I just ended up installing it! Which was perhaps foolish. But so far it seems to be working fine.

---

### Post by mervinb on 2011-10-29
> **sojusnik said:**
> I would like to know how the fan is behaving with 10.11 and how silent the whole notebook is with an SSD installed?
I'm using 11.04. The fan works fine, and the drive is bearly audible. All in all excellent compatibility, very good performance. I swapped to a Seagate Momentus XT (hybrid hard disk with small SSD onboard), and the performance improved noticeably. The maximum brightness of the screen could be better, but the keyboard is excellent.

---

### Post by Karl S. on 2011-10-31
11.10 report:

overall brilliant, no huge complaints. Some graphics problems: I get thin black bars across the screen from time to time, and occasionally the system freezes. I'm guessing it's a problem between this kernel and Sandy Bridge graphics...? I don't want to tweak anything yet, though, in the hopes that a fix will be showing up soon.

---

### Post by madsbola on 2011-11-04
I have been running 11.10 for two weeks, and did a clear install. (Wiped windows 7).

I am extremely happy with the Vostro, Intel I5, 2gb ram and 320gb harddrive.  Did not want to spend 400$ extra on the ssd-drive.

I bought it with backlight in the keyboard, which is extremely handy at night,

All shortcut keys are working ("fn+f2" etc).

So in my opinion  its a nice buy, though the fan is running at, what seems, 100% most at the time, though the CPU is "inactive". But I quess/hope there will be a fix soon.

:popcorn:
/Mads

---

### Post by krat on 2011-11-13
I did a clean install without even booting the windows setup so I don't know how long the battery it's supposed to last but I managed to get the battery life up to 6.30-7h on a v131 (without the SSD) using the jupiter applet and passing additional options to grub as suggested by [this post]("http://askubuntu.com/questions/38117/battery-life-decreased-after-upgrade-to-11-04/38194#38194"). Basically, you need to modify /etc/default/grub, replacing the GRUB_CMDLINE_LINUX_DEFAULT with this one (I also enabled usb autosuspend by default, which apparently isn't normally):

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force usbcore.autosuspend=1 i915.lvds_downclock=1 i915.i915_enable_rc6=1 i915.i1915_enable_fbc=1"
```

(you'll need to run update-grub2 after editing that file, or the changes won't be applied)

I had a couple of freezes since then, I believe it's one of the i915 options (the original post suggested that they are disabled by default because of some stability issues, so this may very well be the case). I'm now trying to understand which options causes the freeze by running the system with only one option enabled each time, but I still didn't figure it out at this time.

Other than that, everything it's working flawlessly except:
[LIST]
[*]the fingerprint reader isn't working, as there are no drivers available.
[*]the hand-over-keyboard sensor isn't working (is it a sensor, that thing just over the touchpad? I didn't boot into windows so I don't know for sure, but it looks like it). Anyway, enabling the relevant option on gnome3 (disable touchpad while typing), doesn't work.
[*]finally, the hybernation doesn't work. It works one out of ten times, the resuming step fails and the system reboots itself automatically. At least for me, this is the most prominent drawback.
[/LIST]

---

### Post by XwpisONOMA on 2011-12-08
Hello, after a long search in the forum I am posting in this thread hoping that #1 my questions are relevant and #2 I am not imposing since I am a complete novice with Ubuntu and my questions might be rudimentary to most of you.
 
I have recently purchased a Vostro V131 (i3 2330 cpu, 2Gb ram, 320Gb 7200rpm HD) with Ubuntu preinstalled. My question is: 
 
**How do I go about installing Windows 7, in dual boot mode, thus preserving the existing Ubuntu installation?**
 
At 1st boot, after the DELL - F2 screen, I was presented with a purplish screen with 4 selections. Two Ubuntu options (one normal one recovery) and two memory test options (one normal, one with console(?)). I went with #1, the defaul selection, after the 10 sec countdown, e.g. "Ubuntu, with Linux 2.6.38-8-generic".
 
It went through the DELL intitial setup and then the Ubuntu configuration. It also asked me if I wanted to created recovery media so I did that on a USB drive. This step took a while. Finally, it booted into the Ubuntu desktop.
 
I had never been in a Ubuntu environment before, but it felt intuitive enough. For the most part everything worked, including networking and wireless.
 
So, where and how do I go from here? I would like to keep this Ubuntu installation and get to know it, but in the meantime I need a "windoze" platform so I can do my work as well.
 
Can you please help me, I appreciate all responses in advance.
 
Thank you!

---

### Post by svenskmand on 2011-12-08
I also ended up buying this excellent laptop in speeding fast red :) and it works flawless only thing that does not work is hibernation, but I am sure that will work at some point, that was my experience with my last laptop, which was a HP Pavilion dv7.

Suspend works flawless and the fans are completely quiet, only think I can hear is the hdd spinning. Also I did not test the finger print reader, but I do not use it anyway.

Overall a very good buy :)

Also I can recommend buying some [Ubuntu Domed stickers (link)]("http://shop.canonical.com/product_info.php?products_id=718") and putting one on the big Dell logo on the back of the screen.

---

### Post by wgarider on 2011-12-08
Just got mine today - first impressions are that it's very good - does everything I need it to. Can't figure out why it won't upgrade to 11.10 though.....get an 'authentication failed' message when first starting the upgrade process.......

---

### Post by crey84 on 2011-12-09
Thanks all for the posts. I wasn't sure if buying the 3350 or the v131 but after all your positive comments (and the many issues showed by the 3350 under ubuntu) I amgoing to go for the v131. 

I was interesting on knowing if somebody had solved the accelerometre issue mentioned, since I'm quite clumsy and having that configured will give me some peace. 

Thanks in advance

---

### Post by pureblood on 2011-12-18
I have installed Kubuntu Oneric 11.10 on the Vostro V131. More or less everything works all right, but there are huge problems with the HDMI detection. If I turn on the laptop, plug the HDMI cable, and change the display to HDMI everything works fine. But if I turn on the laptop with the HDMI plugged in, KDE starts on both screens at low resolution, and if I change to display only on HDMI, everything goes dark and I have to manually restart KDE from one of the terminals. The same thing happens if the laptop goes to sleep or if the screen is sent to energy saving. The HDMI output does not come back and I have to restart the laptop. This is a huge mess. Is anybody having the same problem? I don't know if it is related, but I get this error on dmesg:
> [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

---

### Post by alias_knagg on 2012-01-02
Got mine 2 days ago. Put a fresh oneiric on it, dualboot.
So far everything important is working flawless.
Suspend, hibernate, bluetooth mouse (dell), sound, webcam, microphone.
Not tested hdmi yet.
Not bothered with the extra keys in the top right corner, but one of them works as the "windows key", so I expect them to be easily mapped, when I find a use for them.
Apparently no support for the fingerprint reader. ( quite odd, as it seems to be Ubuntu-certified [http://www.ubuntu.com/certification/catalog/make/usb:138A](http://www.ubuntu.com/certification/catalog/make/usb:138A) )

The only thing which I am not completely happy about is the battery life.
Only tested it once, but got only about 3,5 hours.
Almost certainly not the hardwares fault I understand.

---

### Post by alias_knagg on 2012-01-02
> **krat said:**
> the hand-over-keyboard sensor isn't working (is it a sensor, that thing just over the touchpad? I didn't boot into windows so I don't know for sure, but it looks like it).
Anyway, enabling the relevant option on gnome3 (disable touchpad while typing), doesn't work.


Hm.. is there anywhere that claims the v131 has such a sensor?
Could it be an ambient light sensor? 
Just curious.

"disable touchpad while typing" starts "syndaemon -i 0.5 -K -R".
In my experience syndaemon works just fine, but the arguments need to be more like " -t -i 2".
Unfortunately that seems to be hardcoded in c in gnome-control-center.
Not implemented a kludge yet..

---

### Post by Whoopie on 2012-01-03
It's a LED above the touchpad. A recent [commit]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=2d8b90be4f1cadd9921312e2983459f568d29cd1") added support for it.

---

### Post by pureblood on 2012-02-21
I still have this very* annoying problem with the HDMI output on this laptop. Mainly when I leave the laptop alone for a while the screen goes out and it doesn't come back to life. Sometimes changing to console mode and then back to the X screen solves the problem. Sometimes it doesn't. It is very stochastic. Sometimes going back and forth from HDMI to LVDS as follows fixes the problem:
```
xrandr --output LVDS1 --auto --output HDMI1 --off
xrandr --output LVDS1 --off --output HDMI1 --auto
```
When the HDMI problem arises occasionally I also fail to get anything on the laptop screen as well. It is like the graphic card is forgetting to send the output at all and in that case only rebooting brings it back to functioning properly. Does anybody else experience the same problem? I like to use the laptop attached to a big screen, but this issue can become very annoying. I don't see any interesting messages in dmesg. Any clue how to debug this?

---

### Post by mambro on 2012-03-03
I'm interested in this laptop. Some compatibility questions:
- Is the VGA and HDMI output working out of the box?
- Is the fingerprint reader still not working?
- Is the light sensor working to regulate the backlit keyboard and the display luminosity?
- What about the accelerometer?

---

### Post by stefanb21487 on 2012-03-31
Hello all,

I just recently setup a dual boot of Windows 7 64bit and Ubuntu 11.10 64bit. The Vostro v131 I bought has the following specs:

i3-2330M 2.20ghz
320 GB disk
8GB memory
6-cell battery

Here is my short review:

The intial setup of the partions was straight foward. I have set up my Ubuntu Partion table as 2gb for swap, 25gb for /root, 173 gb for /home. Windows 7 has 120 GB.

Operation:

1. I found that all function key's work except for the 3 hard keys at the very top right hand corner. I'm sure its possible to assign them.

2. Working devices include: Wifi, Ethernet, Bluetooth, HDMI, VGA, USB(not sure if 3.0 functionality is working), touch pad (no dual gestural),internal mic, web camera, keyboard back light, SD card reader, headphone jack, speakers.

3. Non working devices: fingerprint reader, 3 hard keys(again). Someone in this thread mentioned  monitor and keyboard back light sensors. I don't know if they work, but I can tell you that the screen will dim after 30 seconds of non use and the back light turns off after 10 mins of non use.

Performance:

1. I'm not finding Ubuntu 11.10 64bit to be the most efficient os. Its fast and smooth and great for running my research code, but the battery performance is awful. On best I can get about 3:30 hours of simply usage (i.e. no video or running code). I've tried to use powertop but didn't see much gain. Also the system fan is constantly running. Just for comparison I get about 5 hours in windows 7.

If you have any advice I'm all ears.

-SB

Update!!
I found on the Ubuntu wiki page that the sandy bridge intel processors are not by default set to reduce power consumption when idle in 11.10. This can be changed by editing the grub, see here [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

I did this at first using sudo, but it caused some issues. I did it again as root user(su) and now its flawless. I'm seeing about 5:30 hours with screen brightness at 30%.

---

### Post by santibatista on 2012-04-02
Hi everyone,

I got my v131 a few days ago and I just wanted to provide you guys with some feedback as well.

My configuration:
processor: i5 2450M @ 2.50 GHz
RAM: 6 GB
Disk: 500 GB
Standard battery.
WIth backlit keyboard and gestures on the touchpad.

* I wiped the whole disk and made a fresh Oneiric install, with encrypted partitions. Everything worked out of the box as I expected. As was mentioned in the previous post, one of the first things I did was to configure grub to use rc6. I can get up to 6 hours of battery life.

* Suspend and hibernate never failed.

* I modified in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"
```in case you want to try something similar. I had only 3 hours of battery life before doing it. I now get ~ 6 hours.

* For me, it is a very quiet laptop. The fan gets loud in a few occasions if I do something that is resource intensive.

* Amazing keyboard, super comfortable I have to say. The gestures on the touchpad are not smooth, but I understand that this is a software issue, not sue to the hardware.

* Tried Precise Beta2, Fedora 17 Alpha and everything seems to work as well, out of the box.

Overall, a great experience. Worth every penny.

Cheers!
Santiago

---

### Post by frandu on 2012-04-04
Hello all, I'm new to the forum.

I have a Dell Vostro V131, with Core i3 230 and 2GB of RAM.
I just installed Ubuntu 12.04 Beta and I am having issues with the poor battery life and some overheating.

I left my laptop updating all night long and in the morning I still noticed that it was hot and with the fan running. My battery is lasting 2 hours (versus 8h in Win 7).

Can please someone help me? I'm new at Linux and would love to keep Ubuntu with my Dell.

Best for all,
FRandu

---

### Post by santibatista on 2012-04-05
Hi Frandu,

I am surprised that you get such a limited battery life using 12.04 beta...

You could try to use rc6 in grub (to see if your battery life increases) as follows:

1) Open a terminal (Control + Alt + t)

2) Type:
sudo gedit /etc/default/grub
and then enter your password.

3) A text file will open. Change the line that says: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"
You SHOULD include the quotation marks that I wrote!

4) Save the file and close it.

5) Again in the terminal, type: sudo update-grub

6) Reboot your computer, and hope that it works :)

---

### Post by frandu on 2012-04-08
Hello Santibastista,

thank you for the tip, but unfortunately no lucky for me. The fan is always on and the battery is dying very quickly.

So sad... Anyone can share the experiences with this laptop?

Best,
Frandu

---

### Post by frandu on 2012-04-11
Hi there,

Today I made another experiment and tried Ubuntu 11.10 32-bit from the following link:
[http://www.ubuntu.com/certification/hardware/201105-8049](http://www.ubuntu.com/certification/hardware/201105-8049)

It's certified for my laptop and altough my battery is not that great, it stills performs well and the lappy is not overheating. 

If somebody run into an issue like mine, give it a try. So far, so good.

A happy Ubuntu's user,
Frandu

---

### Post by subload on 2012-04-13
Any advice on how to enable the fingerprint reader, for login or security?
Anyone see any facial recognition software they would recommend?

And the latest UBUNTU upgrade, Ocelot? seems to fail authentication.
Any suggestions?   Have found the upgrade runs from Terminal mode. Apparently the distributed upgrade tries to execute from the wrong directory. (subload)

Please excuse dumb questions, Am very unfamiliar with LINUX.

---

### Post by frandu on 2012-04-15
Hello Subload,

AFAIK, there&#347; no solution for the fingerprint reader... What intrigues me is that in some countries the Dell Vostro V131 is sold with Ubuntu pre-installed, so the buyers simply get a fingerprint that does not work by factory....

Best

---

### Post by subload on 2012-04-16
Frandu, thanks! 
Yes I have the FPrint reader hardware on the V131, and there is even a FPrint demo app I downloaded. 
And Ubuntu has instructions for enabling a reader which I cannot follow. ([https://help.ubuntu.com/11.04/ubuntu-help/session-fingerprint.html](https://help.ubuntu.com/11.04/ubuntu-help/session-fingerprint.html)) all very frustrating.
Does Dell answer questions? I'm still under warranty, but they don't seem to answer the phone.

---

### Post by subload on 2012-04-16
Oneric Ocelot 11.10 fails authentication. 
I have a good, and fast connection. 
Any suggestions?

---

### Post by frandu on 2012-04-23
Sorry Subload.
I have no idea of what's going on with Oneiric...

But tell us about your experience in general with Ubuntu. How's the performance going? Battery? So far, so good?

Thank you.

---

### Post by pureblood on 2012-04-29
Since I upgraded to Ubuntu 12.04, I am experiencing random freezes. I leave the laptop alone for a long time and when I come back, it is on but nothing works, the screen is black, and I don't think I can ssh to it. It happened while I wasn't around it, so I have no useful information to debug this. Anybody experiencing anything similar? If this happens again, I will try to revert to kernel 3.0.0.

---

### Post by frandu on 2012-04-29
Hello Pureblood,

I'm still on 11.10 and upgrading now to the 12.04.... If I notice something unusual, I'll report here.


One quick question: Did you go for the 12.04 directly (fresh install)? Or from 11.10? If so, did you installed the general version or the certified one from Dell?

---

### Post by frandu on 2012-05-01
No HDMi for me...

I plug it and nothing happens in 12.04....

Anybody with the same issue?

---

### Post by pureblood on 2012-05-01
@frandu I just upgraded to 12.04 from a fresh 11.10 install. I never dared using anything from Dell. Do they provide certified versions? I probably should mention that I use my laptop on HDMI 99% of the time. I have no problems with that. Did you try the following command?
```
xrandr --output LVDS1 --off --output VGA1 --off --output HDMI1 --auto
```
I do have to say that last night the laptop froze while I was using it. Everything stopped, I couldn't even use the mouse anymore. Complete unresponsiveness. It must be a kernel bug, but I don't know how to debug it. I don't know if this is reproducible without plugging the laptop with the HDMI.

---

### Post by santibatista on 2012-05-03
Hello again,

An update to my previous post.

I did a fresh install of 12.04 on my v131. Again, everything worked out of the box.

I have to say that I am a bit disappointed with this version so far. It is as polished as they had promised. I guess we will ahve to wait to usual 2-3 months for things to get more stable.

Unity has a few glitches in my case, LibreOffice keeps crashing on me... But well, all of this is software related. The compatibility with the laptop is great.

I don't use HDMI so I cannot help you with that, nor do I care for the fingerprint reader.

On active use (browsing the internet, writing reports, etc.) I get between 5 and 6 hours of battery life (I didn't tweak anything).

Cheers everyone,
Santiago

---

### Post by frandu on 2012-05-05
Santibatista, are you using Unity 2d or 3d?

---

### Post by pureblood on 2012-05-07
I can now confirm that the total system freeze I am experiencing since I updated to Ubuntu 12.04 has nothing to do with HDMI. The only thing I do different is I use KDE rather than Unity. Anybody is experiencing the same problem? Anybody has a solution?

I am starting to think maybe I have an overheating problem, but this started exactly after I updated Ubuntu. Too much to be a coincidence. I find no useful log in /var/log. This is very frustrating.

---

### Post by frandu on 2012-05-07
Hello Pureblood,

I was experiencing overheating and a miserable battery life with the "standard" Ubuntu 11.10. But then I did a fresh install of the "Dell certified" Ubuntu:
[http://www.ubuntu.com/certification/hardware/201105-8049/](http://www.ubuntu.com/certification/hardware/201105-8049/)

Everything was OK, except the HDMI... Then I did an upgrade to 12.04 and so far, so good. The system is smooth and my battery is lasting 5hours at least.

I AM using Unity 2d tough...

Why don't you try to go Unity of Gnome to check if the issue stills happens?

Best and keep us updated!

---

### Post by Red Rob on 2012-05-09
Hi there,
I'm new to ubuntu and installed 12.04 on my vostro v131 a couple of days ago. All looks very slick and I think it will suit my needs.

However, I'd be very grateful if someone could help me with a wifi issue. 

Although, I'm apparently able to connect to my home wifi network I'm unable to get any internet connectivity. It worked fine when I connected on a friend's network, which doesn't need a password, and when I switch off security on my router then it also works fine on my home network.

So, any ideas on how to solve this?
Many thanks.

---

### Post by frandu on 2012-05-10
Hello Red Rob,

Seriously, I have no idea of what's going on... I would try to reset your router and try seeting up it inside Ubuntu...

Are you using Unity 3d or 2d? I've heard that 2d won't be supported in 12.10. Are there any way to install the Intel HD 3000 drivers for it?

Best and good luck

---

### Post by Red Rob on 2012-05-11
Thanks Frandu,
After a lot more pain, I did eventually find a fix on this thread:
[http://ubuntuforums.org/showthread.php?t=1970549](http://ubuntuforums.org/showthread.php?t=1970549)
I've no idea what it's done, but everything is now working. Thanks again for your help
Red Rob

---

### Post by frandu on 2012-05-18
Hello all,

I am still experiencing issues with the HDMI connection. When I try to plug in the HDMI, nothing happens.

Can someone help me? I am using 12.04

Thank you

---

### Post by rbarra on 2012-05-22
Hi all,

I am about to buy a notebook. It can be a Dell Vostro v131 or a Samsung Series 9 NP900X3A.

Both of them have problems with Ubuntu, but I would say that the Dell Vostro v131 seems to behave better, maybe because it's already certified with Ubuntu 11.10.

I've read the complete thread and still don't know if someone is having serious issues with Ubuntu 12.04.

What kind of problems are you having? Can anybody help me with some feedback on that?

Thank you very much.

---

### Post by olinart on 2012-05-22
My experience is with a vostro v13 i5, which is very similar to the 131 except for battery life. It came preloaded with Ubuntu 10.04 which worked quite well, more smoothly that the Fedora I ran on my old laptop.
I've recently upgraded to 12.04. Most laptop features continued to work fine esp sound, bluetube. HDMI, suspend.Battery usage is about the same as with 10.04 (which is really poor on the 130's. That's the main advantage of the 131.).
A larger problem was the failure of my wireless (Atheros AR9285) to associate with my accesspoint.
After some debugging I found that it recognises WPA-AES encrypted wireless but not TKIP encryption. Something to be mindful of....

---

### Post by frandu on 2012-05-23
Hello,

after yesterday's update, my touchpad gone dead. I think the update was something like linux_header_pea or similar and after that, no touchpad for me.

When I reboot, in the login window, the touchpad works well, but after inserting my password and entering in the system, no touchpad.

Has anyone noticed this issue?

---

### Post by rbarra on 2012-05-24
> **frandu said:**
> Hello,

after yesterday's update, my touchpad gone dead. I think the update was something like linux_header_pea or similar and after that, no touchpad for me.

When I reboot, in the login window, the touchpad works well, but after inserting my password and entering in the system, no touchpad.

Has anyone noticed this issue?

Hi, have you been able to solve this already? I really want to buy this laptop, but I'm scared it won't work as it should or could :(

---

### Post by frandu on 2012-05-24
Still trying!

I can only work using an USB Mouse....

---

### Post by frandu on 2012-05-25
I managed to solve my issue...

After doing another long update, the touchpad got alive finally...

So far, so good. Only the HDMI that does not work at all.

---

### Post by rbarra on 2012-05-27
Hi frandu. I'm glad you solved it! I think I'm going to buy it right now. What do you mean by "long update"?

Has someone else made the HDMI work?

Thanks!

---

### Post by pureblood on 2012-05-28
> So far, so good. Only the HDMI that does not work at all.
frandu, for the hdmi, have you tried:
```
xrandr --output LVDS1 --auto --output VGA1 --off --output HDMI1 --auto
```
if this doesn't work, can you show us the output of the command:
```
xrandr
```

---

### Post by udienz on 2012-05-29
> **rbarra said:**
> Hi all,

I've read the complete thread and still don't know if someone is having serious issues with Ubuntu 12.04.

What kind of problems are you having? Can anybody help me with some feedback on that?

Thank you very much.

Hi I just installed fresh Ubuntu precise on my Dell V131, no serious problem. As previous thread, battery lifetime, and fingerprint is the problems.

My Dell come with Natty, if i have upgraded to oneiric and also precise, i got many error in unity system. So, at this time i recommended you do fresh install instead of  upgrading to oneiric/precise.

Hopefully i have solutions soon

---

### Post by rbarra on 2012-06-10
Hi udienz,

How much battery life are you getting? What do you mean by "fingerprint"?

Hi frandu,

Did you solve the HDMI problem?

Regards!

---

### Post by richoffrails on 2012-06-17
Hey all. I've been using my Dell Vostro V131 on Xubuntu 11.10 and here a few observations so far:

- Kernel 2.6.38 appears to be the oldest Kernel I'm able to use. Anything older and I'll have boot issues or resolution problems.

- Kernel 3.2 gives Wifi issues. I'm not able to connect to any networks. Tried messing with the Realtek drivers but still wasn't able to get it work.

- Using Kernel 2.6.38 I get about 5 to 6 hours of battery life on 64-bit Xubuntu 11.10. Everything works except the fingerprint reader of course. One weird thing is Xubuntu thinks the laptop has bluetooth so that icon is always appearing.


I noticed the certified version of Ubuntu for this laptop is a 32-bit version of 11.10. I'm curious as to why it isn't 64 bit being that the laptop uses a 2nd gen Sandy Bridge i3 or i5. I added an extra 4GBs of RAM and a 120GB SSD to the laptop which is why I went with 64-bit... although I'm sure the 32-bit will install PAE to support the extra RAM. If anyone here is using the 32-bit 11.10 certified I'd love to hear your experience with battery life. If its better than the 5-6 hours I might consider switching and changing the UI to Xfce.

---

### Post by donalgodon on 2012-06-18
I tried 12.04 on my V131 with 8GB of memory and a 160GB SSD. The fan runs far too much under the standard kernel and the battery life suffers greatly. I can get 9 hours of real use out of it easily in Win-doze 7 and I actually need the fingerprint reader, so those issues make Ubuntu unusable for me.

---

### Post by frandu on 2012-06-20
Hello all,

sorry for disappearing in the forum. I still didn't solved the HDMI issue. In fact, I reinstalled Win 7 to another partition and upgraded my RAM to 8GB. Why I did this? Home-Work as video editor (Adobe Premiere, Illustrator and Photoshop are my main reasons).

Best for all,

---

### Post by frandu on 2012-07-02
Hello,

12.04 LTS 64 bit is now certified by Dell:
[http://www.ubuntu.com/certification/hardware/201105-8049/](http://www.ubuntu.com/certification/hardware/201105-8049/)

Anyone tried or planning to try it?

---

### Post by frandu on 2012-07-16
No one?

I did a fresh install and it runs quite good. Even the HDMI, my previous issue, is OK now.

---

### Post by spruzzer on 2012-08-23
Hi! I'm new here :)

I tried the Ubuntu 11.10 and 12.04 32 bit version on my vostro v131 but I can't say that the machine works well...
With the 12.04 I see improvements with the battery life, but the fan go continuously at the maximum speed and the laptop results too hot anyway. Do you have the same problem? If not you can explain me how can I fix it? 

After an hour the machine results uncomfortable to be used (the touchpad area seems like an electrical oven!) 

Thanks!

---

### Post by fuzzwahfuzz on 2012-08-24
why use i386 when you can use amd64 ?
i have amd64 12.04 LTS on my v131
yes, it runs hotter than i expected but nothing i'd worry about and i dunno how it behaves when running windows 7

overall i'm very satisfied with the laptop/ubuntu combo, runs super fast (i have an i5/ssd version)

---

### Post by spruzzer on 2012-08-25
Thanks for the answer! I will try the 64 bit version in the next days. 
I want to ask you if you have edited a proper power consumption profile to work efficently  with your machine.

---

### Post by fuzzwahfuzz on 2012-08-25
i did all the stuff like enabling rc6 etc, just google ubuntu power saving tweaks

---

### Post by griquelme on 2012-08-27
My Vostro V131 is unable to recognize an usb 3.0 hard drive connected at boot (I only using the command line interfase and fdisk -l only shows the internal drive). Just when it's disconnecting and reconnecting is recognized (and fdisk -l shows the drive), and only at a speed of USB 2.0. This happens with all distributions and kernels I've tried. In any case, using a USB 2.0 cable, the unit is recognized at boot and it works fine, but only as USB 2.0. How could this laptop be certified?

---

### Post by Whoopie on 2012-09-19
FYI, someone started to work on a driver for the freefall sensor:
[http://sonalsantan.blogspot.de/2012/09/dell-latitude-freefall-sensor-on-linux.html](http://sonalsantan.blogspot.de/2012/09/dell-latitude-freefall-sensor-on-linux.html)

EDIT: The updated version works perfectly. It includes the needed kernel module and userspace application.

---

### Post by spruzzer on 2012-10-15
Hi to all,

after some time spent with ubuntu I can say that with my everyday usage of the machine (working Eclipse IDE + Web surfing + reading some pdf) i can get around 4, 4,5 hours of battery life. 

I'm pretty satisfied, although there are some issue like LCD light/ wifi and bluetooth status that aren't stored after a reboot.

Now i have in mind to buy an ssd (samsung 830, 128gb), but I can't work with hybernation (I think that with an ssd device hybernation is an important thing). Do you have problem with hybernation too?

---

### Post by frandu on 2012-10-30
Anyone tried 12.10 fresh install?

---

### Post by spruzzer on 2012-10-31
I've installed ubuntu 12.10 (64bit) on my vostro v131 (core i5 sandy bridge, 8gb ram, 128 gb ssd) and i can assure you that the system works quite good! :D

Currently I discover only that the fan is continuously working....the Jupiter applet don't works properly (I removed it beacuse it notify continuously change of of status of screen/cpu that didn't happen and the boot time increase from 10s to ~30s).
To replace Jupiter I tried indicator-cpufreq, but I don't see changes in the power consumption. The fan is everytime working at the maximum speed, and also the processor; with 12.04 this didn't happen. With 12.04 I can get 5 hours of work with the battery, with 12.10 no more than 3,5.

---

### Post by merc82 on 2012-11-03
I upgraded a clean install xubuntu (64 bit) 12.04 system to 12.10. HDMI works very well, better than I remember on 12.04 although it's not something I used other than to test.

Suspend and hibernating seem noticeably slower with 12.10

---

### Post by donalgodon on 2012-11-07
Is there any way to increase the sensitivity of the brightness settings on the V131?

I'd like to have more than just FIVE levels of brightness. I have SEVENTEEN levels of volume.

This seems sort of silly. I'd love to have 17 levels with which to adjust brightness also, because 5 doesn't give me the best settings for my environment typically.

---

### Post by merc82 on 2012-11-10
The kernel upgrade to 3.5.0-18 improved the suspend and hibernate times. The system something returns from sleep with an unlocked screen. 

The fan runs more often than not even with no load on the CPU.

---

### Post by goo25 on 2013-01-03
Upgraded form presice to quantal and HDMI stoped working, previously with 12.04 worked perfectly.  But now WIFI started working on channel 12 and 13. There must be a trick to fix this!

3.5.0-21-generic

Cheers.

---

### Post by Whoopie on 2013-02-12
Experimental fingerprint reader support is available: [http://article.gmane.org/gmane.linux.fprint/2241](http://article.gmane.org/gmane.linux.fprint/2241)

---

### Post by donalgodon on 2013-02-12
> **Whoopie said:**
> Experimental fingerprint reader support is available: [http://article.gmane.org/gmane.linux.fprint/2241](http://article.gmane.org/gmane.linux.fprint/2241)

I'm not sure how to use it.

---

### Post by spruzzer on 2013-03-01
Hi guys,

what about battery life now with a standard ubuntu 12.10? I can't get more than 3 hours surfing the web, playing a couple of videos on youtube and coding in eclipse...It is annoying compared to a normal usage in windows - working in a windows environment is annoying too. ;)

---

