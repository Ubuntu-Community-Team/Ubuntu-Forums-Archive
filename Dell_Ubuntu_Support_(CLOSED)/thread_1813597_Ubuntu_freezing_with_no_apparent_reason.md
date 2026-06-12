---
title: "Ubuntu freezing with no apparent reason"
date: 2011-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kkharinarayanan on 2011-07-28
hello 
am  using an dell studio 1558 with Ubuntu 10.10 . 
the problem am facing is that my laptop freezes frequently . 
then nothing works .
no mouse or keyboard.
i dont know if entire system freezes or just gnome ?
can any body tell me why this happens.
advance thanks for any help:D:D


the lshw report is attached

---

### Post by vittau on 2011-08-04
My Dell Inspiron N5110 (i5 Sandy Bridge, Intel HD 3000) is doing the same thing. Not even *CTRL+ALT+BACKSPACE* or *ALT+SYSRQ+R-E-I-S-U-B* works. I'm using Unity, still haven't tested Gnome because I suspect it has nothing to do with this.

EDIT: Tested with GNOME, no luck...

I wonder if it would happen with the x86 version?

---

### Post by d.burba on 2011-08-04
The same problem to me and no idea how to solve it.

---

### Post by vittau on 2011-08-10
Any ideas?

(I just noticed the OP is using 10.10, in my case it's 11.04.)

---

### Post by SonicSteve on 2011-08-14
I have the same problem,

I'm using an asus p7h55-m board, kingston ram, core i3 intel. 

x86 install of 11.04 

It may be happening upon screen turn off, power saving. I've disabled this, even though I didn't run a screen saver it may be this. 

I have x86 version running at work and it doesn't do this. 
Asus P5g41-LE, intel core 2 duo, kingston ram. It also turns off the screen but for some reason it hasn't done this.  From a quick search on the net, this seems to be happening to quite a few people.

---

### Post by SonicSteve on 2011-08-18
I decided to revert to a previous kernel. I let everyone know the results. It will likely take a few days to know if it worked.

---

### Post by w4rh4wk on 2011-08-19
> **SonicSteve said:**
> I decided to revert to a previous kernel. I let everyone know the results. It will likely take a few days to know if it worked.


i have a similar problem:
computer has an Asus P7H55-M with Intel(R) Core(TM) i5 CPU which serves as file and mail server. But when somebody moves huge files (about 4GB+ ) over the network, the system freezes without reason. This problem is reproduce-able. I didn't find anything in the logfiles.. everything is cutoff, frozen, not even a kernel panic message.

Current kernel is: 2.6.38-10-generic

i need to find a fix soon... anybody has an idea?

---

### Post by SonicSteve on 2011-08-19
I have reverted to 2.6.38-8

Still testing it out to see if the kernel matters.

---

### Post by kkharinarayanan on 2011-08-19
i don't think problem is with current kernel , the problem had been with me since 10.10 was released , i did not notice it before that
:confused:

---

### Post by SonicSteve on 2011-08-19
> **kkharinarayanan said:**
> i don't think problem is with current kernel , the problem had been with me since 10.10 was released , i did not notice it before that
:confused:

It only started for me a few weeks ago. I didn't even notice it when I first installed 11.04. At least  I can't remember it being there.

---

### Post by SonicSteve on 2011-08-20
> **kkharinarayanan said:**
> hello 
am  using an dell studio 1558 with Ubuntu 10.10 . 
the problem am facing is that my laptop freezes frequently . 
then nothing works .
no mouse or keyboard.
i dont know if entire system freezes or just gnome ?
can any body tell me why this happens.
advance thanks for any help:D:D


the lshw report is attached

I'm starting to wonder if it has something to do with networking chipset. 

My system has the same Realtek 8111/8168B network controller.

Another post in this thread mentions it happening when transferring large files over the network. 

My work computer (also running 11.04) has an atheros chipset and does not suffer from this problem.

---

### Post by SonicSteve on 2011-08-20
> **w4rh4wk said:**
> i have a similar problem:
computer has an Asus P7H55-M with Intel(R) Core(TM) i5 CPU which serves as file and mail server. But when somebody moves huge files (about 4GB+ ) over the network, the system freezes without reason. This problem is reproduce-able. I didn't find anything in the logfiles.. everything is cutoff, frozen, not even a kernel panic message.

Current kernel is: 2.6.38-10-generic

i need to find a fix soon... anybody has an idea?

Can you please confirm your lan chipset. I bet you have the same realtek chip as the OP and myself. You have the same mainboard as I do so you likely have the same chip, but we should confirm. 

In case you don't know, terminal then lspci and somewhere in the list will be your Ethernet contoller.

---

### Post by in·ter·punct on 2011-08-20
Im using 11.04 and Ubuntu has frozen thrice now. Nothing works when it's  frozen as other people have mentioned and the only way to get back to  work is to hard reboot.
My computer is a Dell Vostro 3350 Laptop with an Intel Core i5-2410M CPU @ 2.30GHz.
> **SonicSteve said:**
> 
...
In case you don't know, terminal then lspci and somewhere in the list will be your Ethernet contoller.
This is what I get if it is of any help: 05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by SonicSteve on 2011-08-20
> **in·ter·punct said:**
> Im using 11.04 and Ubuntu has frozen thrice now. Nothing works when it's  frozen as other people have mentioned and the only way to get back to  work is to hard reboot.
My computer is a Dell Vostro 3350 Laptop with an Intel Core i5-2410M CPU @ 2.30GHz.

This is what I get if it is of any help: 05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

My Ethernet controller is the exact same even (rev 06) the common task I've seen is relating to transferring files on the network, for me it happens when I'm on the internet browsing around. For others it's transferring large files. 

So far since reverting to a previous kernel I've had uptime of more than 2 days. I'll keep you posted. Kernels do have drivers for these cards, it would be interesting to see if the recent kernel updates had anything in them that would obviously relate to our controller.

I may also change my network card and disable the realtek card in my BIOS. I can't stay on an old kernel forever even if it does fix it.

---

### Post by Matifou on 2011-08-21
Hi

I am sad to have myself on the list of victims: I have a Dell Studio 1557. Screen freeze, screen black and random reboot became now usual phenomenon!!! This was both under 10.4, 10.10 and now on an external 11.04!! I suspect it often happens with network manager, can almost reproduce by plugging to the net..

Any idea how to track problem? Should I look on /var/log/syslog? Or on others?

Also, I wuld like to test if not a hardware problem... do you know how I can fgo to the BIOS checks?

Thanks!

---

### Post by SonicSteve on 2011-08-21
> **Matifou said:**
> Hi

I am sad to have myself on the list of victims: I have a Dell Studio 1557. Screen freeze, screen black and random reboot became now usual phenomenon!!! This was both under 10.4, 10.10 and now on an external 11.04!! I suspect it often happens with network manager, can almost reproduce by plugging to the net..

Any idea how to track problem? Should I look on /var/log/syslog? Or on others?

Also, I wuld like to test if not a hardware problem... do you know how I can fgo to the BIOS checks?

Thanks!

You really need to start a new thread on this one.  I would suggest that keep an eye on this thread but your issues have been going on for some time now, I can't speak for everyone is this thread but mine are recent, starting only a few weeks ago. 

I suggest you use the terminal,

then in the terminal type lspci and press enter. This will list all the hardware in your computer. With that information you should start a new thread.

---

### Post by Wiretrap on 2011-08-22
This is a Gnome problem what it seems like, However nautilus strikes too !
ED!T : I have Dell 1018 Netbook. :popcorn:

---

### Post by fromwintolinux on 2011-08-22
hey ; i wanna ask sth.. theese problems/errors usually shown in all dell models? there is chronic error?? i am gonna buy a dell inspiron n5110 and its important 4 me

---

### Post by SonicSteve on 2011-08-22
> **fromwintolinux said:**
> hey ; i wanna ask sth.. theese problems/errors usually shown in all dell models? there is chronic error?? i am gonna buy a dell inspiron n5110 and its important 4 me

I personally don't own any dells.

One HP laptop running 10.10 still
One self made pc running with an Asus p7h55-m running 11.04 has the issue.
One self made pc running with an Asus p5g41-le running 11.04 hasn't frozen once.

Both self made PC's have similar software installed, just different hardware. 

I can also confirm that last night I froze again after 3 days of uptime. 3 days seems to be magic #.

---

### Post by SonicSteve on 2011-08-22
> **Wiretrap said:**
> This is a Gnome problem what it seems like, However nautilus strikes too !
ED!T : I have Dell 1018 Netbook. :popcorn:
Have you seen threads about this or is it just your best guess?

---

### Post by azmyth on 2011-08-22
I just updated my PC today and I've had two or three freezes and it never freezes. I'm using the same Realtek. The syslog says no eth0 as the last statement so it must have to do with this. I may try dropping the kernel to the last one.

---

### Post by azmyth on 2011-08-22
Well it's not the kernel as it's even worse with the previous one. It's freezing to the point where it's unusable.

---

### Post by Idefix82 on 2011-08-22
I had the same issue with my ThinkPad Edge 13, and the problem was the wireless chipset, or rather the open source driver:

```

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```
I solved it by installing the driver that Realtek kindly provides for their card. I went to the [driver download website]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE"), downloaded the driver (the current version is 0003.0620.2011), saved it in my home folder, then did
```

sudo apt-get install linux-headers-generic build-essential
cd rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011/ #(replace with the correct name)
sudo make
sudo make uninstall #deletes the old driver
sudo make install

```

Now, they also provide [a driver for the ethernet controller]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2") that you guys have. So you should give that a shot.

---

### Post by azmyth on 2011-08-23
The new ethernet controller driver didn't fix my problem since 15 minutes later it froze. Don't know what to do. Freezing every 10 minutes is unusable.

Now I'm getting spontaneous reboots.

---

### Post by Idefix82 on 2011-08-23
Is your wireless controller switched on? If it is, what model is it?

---

### Post by fromwintolinux on 2011-08-23
as i know ; well-known brand that supports the linux systems is Dell.. they have subdomain like [http://linux.dell.com]("http://linux.dell.com").

But why there r so many problems? is it normal? or it is caused by user??

---

### Post by SonicSteve on 2011-08-23
> **azmyth said:**
> The new ethernet controller driver didn't fix my problem since 15 minutes later it froze. Don't know what to do. Freezing every 10 minutes is unusable.

Now I'm getting spontaneous reboots.


Did these problems only occur with 11.04? Did they ever happen with previous versions?

---

### Post by azmyth on 2011-08-23
I'm not using any wireless device on this computer. I've been using 11.04 since it came out. I just did an update and about 15 or so packages were updated and this is where my troubles began. Not sure what else to do. I can barely use my computer now.

---

### Post by SonicSteve on 2011-08-23
> **azmyth said:**
> I'm not using any wireless device on this computer. I've been using 11.04 since it came out. I just did an update and about 15 or so packages were updated and this is where my troubles began. Not sure what else to do. I can barely use my computer now.

Wow that's the best info we've had yet to go on. My issues aren't anywhere near as severe as yours but it if only started after your recent update do this.

Go to "software centre" 
Click history and it will give you a day by day blow of what updates were installed. Depending on how often you update your machine you may have a huge list of updates listed under each day or very few. Obviously depends on your machine, software installed etc. 

While I'm unsure of how you can uninstall the updates, you may be at least able to get a list which update (s) caused the trouble. It's a starting point.

---

### Post by azmyth on 2011-08-23
Looks like it's bad memory. Ran memtest and got some errors.

---

### Post by azmyth on 2011-08-23
Yup that was my problem. RAM isn't even a year old. Go figure.

---

### Post by SonicSteve on 2011-08-24
> **azmyth said:**
> Yup that was my problem. RAM isn't even a year old. Go figure.


I hope that sorts it out for you. My work desktop started doing it today. I'll check the ram also but I think it's likely something else. I may have to revert to 10.10 or maybe 10.04 if I don't find a fix soon. My uptime is over usually at 3 days.

---

### Post by w4rh4wk on 2011-08-26
have you checked out this bug report

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661294](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661294)

--> update realtek driver for nic

---

### Post by vittau on 2011-08-27
I've just updated my Realtek RTL8101E/RTL8102E Ethernet driver, and also updated to the new 2.6.39-11 kernel (does it nullify my manual driver update?), and so far so good. If the freezing still happens I'll edit this post. ;)

---

### Post by w4rh4wk on 2011-08-28
> **vittau said:**
> I've just updated my Realtek RTL8101E/RTL8102E Ethernet driver, and also updated to the new 2.6.39-11 kernel (does it nullify my manual driver update?), and so far so good. If the freezing still happens I'll edit this post. ;)



another option is to insert a new nic (i recommend intel) and use it rather than the onboard nic

---

### Post by Idefix82 on 2011-08-28
> **w4rh4wk said:**
> another option is to insert a new nic (i recommend intel) and use it rather than the onboard nic

But why? Realtek is one of the best in terms of providing drivers for Linux.

---

### Post by w4rh4wk on 2011-08-28
> **Idefix82 said:**
> But why? Realtek is one of the best in terms of providing drivers for Linux.

refering to the bugreport, the problem isn't really the realtek chip itself but the driver... the driver present inside the kernel isn't up to date.. so if you download the current driver for the realtek nic, and install it. the kernel will use the new driver.

this helped me.. right after i installed the driver and rebooted the server (had to, otherwise i couldn't use the nic) i could transfer big files to the server without freezing..

hope it helps you too

---

### Post by slcooper on 2011-08-28
Same problem, Inspiron N5110, Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller.

We'll see if the new drivers do the trick.

---

### Post by SonicSteve on 2011-08-31
Just thought I'd check in to see how everyone is doing. Strangely both my affected machines are now onto 6 days uptime. I'm not sure but I think the updates on the 24th may have fixed things.

There was a new kernel and some firefox updates. One or both could have been a fix. There was also a xorg update. 

So how about the rest of you? 

I'll keep you posted on any more freezes. It might not sound like much but I haven't seen more than 3 days of uptime for a while now.

---

### Post by slcooper on 2011-09-01
Update: it froze again, system is up-to-date, new Realtek drivers were on. Uptime was less than a day. I'll keep tracking.

---

### Post by Alan.Brown on 2011-09-01
I had this problem some months ago and found a solution relating to the use of wireless drivers.

See 
[B][http://ubuntuforums.org/showthread.php?t=1694262](http://ubuntuforums.org/showthread.php?t=1694262)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103)
[/B]
This fixed my problem until recently but it is back again.

When I try **sudo modprobe -rf rt2860sta **I now get 
> **FATAL: Module rt2860sta is in use.**I am not using a wireless connection.  This means that I can no longer remove the module and the error persists.

All system is up to date and the logs show no errors (presumably because the system freezing prevents errors being written to logs).

I have used Ubuntu for years and would not like to change distros because of a bug even though it is very annoying.

Thanks for any help

Alan

Useful info here
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

---

### Post by Angelsoul on 2011-09-02
Hi all.
I'm facing the same problem, but i think that the problem is linked to power management. in fact i have this problem only when i work without power AC, only with battery.

If i use my pc with power AC the freeze not happens.

---

### Post by Idefix82 on 2011-09-03
@Alan.Brown: maybe some other module is also using the wireless module? Try
```

lsmod | grep rt2860sta

```
to see whether that module is used by something other than your wifi card.

---

### Post by in·ter·punct on 2011-09-09
> **SonicSteve said:**
> Just thought I'd check in to see how everyone is doing. Strangely both my affected machines are now onto 6 days uptime. I'm not sure but I think the updates on the 24th may have fixed things.

There was a new kernel and some firefox updates. One or both could have been a fix. There was also a xorg update. 

So how about the rest of you? 

I'll keep you posted on any more freezes. It might not sound like much but I haven't seen more than 3 days of uptime for a while now.
I haven't had a freeze for quite some time now.

---

### Post by vittau on 2011-09-10
> **in·ter·punct said:**
> I haven't had a freeze for quite some time now.
Everything's fine here too.

Thanks guys! :)

---

### Post by SonicSteve on 2011-09-16
It seems that there are 2 groups in this thread. I now fall into the mysteriously fixed group. Then there seems to be some that have a similar problem but it must be caused by a different issue. 

I haven't had a freeze for a few weeks now, my machines are again stable and uptime is now routinely 7 days or more.

---

### Post by vittau on 2012-03-06
The problem returned here. :evil:

Same deal, 10.10, now with kernel version 2.6.38-13-generic. Any ideas?

**EDIT:** I think it has the wrong driver installed now, it says RTL-8169 while it should be RTL-8105E-VB, I think... How do I fix this mess?

**EDIT 2:** I have download the RTL-8105E driver and ran the autorun.sh, but now my Ethernet disappeared completely. All I have now is wlan0. WTF happened?

**EDIT 3:** After some random install and uninstalls, r8101 is loaded and running. Now let's see how it goes...

---

### Post by w4rh4wk on 2012-03-06
bump for interest, haven't found a fix for this problem.

---

### Post by vittau on 2012-03-06
> **w4rh4wk said:**
> bump for interest, haven't found a fix for this problem.If you don't use the ethernet (most people only use wifi these days anyway), maybe you could try removing the module entirely.

* # sudo rmmod r8****

Where r8*** is your Realtek Ethernet controller. I suppose this should work (but I'm no Linux geek)...
If you don't know the name, try *lsmod | grep r8*, it should return the name of your ethernet controller.

---

### Post by vittau on 2012-04-02
I still have the problem. This is really pissing me off... ](*,)

---

### Post by veroslav on 2012-04-10
I am also experiencing the same issues (I've posted a related thread here: [http://ubuntuforums.org/showthread.php?t=1942219](http://ubuntuforums.org/showthread.php?t=1942219)), my specs are as follows:

Ubuntu 11.10 (64-bit)
Dell Inspiron n7110 17R
Intel i7-2670QM (2.20 Ghz, 6 MB, 4 cores)
nVidia GeForce GT 525M (2 GB)
6 GB DDR3 SDRAM

My ethernet controller is also the famous Realtek one (being mentioned in this thread), however, I am using a wireless connection (Atheros driver) so I don't know whether my problem is related to Realtek.

I am experiencing freezes randomly, and as everybody else mentioned here, nothing helps when they occur (not Alt+SysRq+REISUB, nor Ctrl+Alt+F1..F6, nor Ctrl+Alt+K, really nothing) and I am forced to perform a hard shutdown.

I am wondering whether this really is a kernel issue or whether it is a hardware related issue specific for the Dell brand. Does anybody runs Windows in dual-boot with Ubuntu and if yes, do you experience freezes in Windows as well? 

Just curious whether anybody has any more info about this.

Really hoping that Ubuntu 12.04 will fix this issue but somehow I doubt it.

Thanks.

Regards,
Veroslav

---

### Post by lisanels47 on 2012-04-18
When it freezes, can you do anything besides power off?  Does ctr-alt-F2 get you a logon screen?

Can you ping the system from another computer?  If either of these two things work, then it has to be related to the OS locking up.  

If nothing works, even the mouse won't move, then it's more likely to be hardware related.  Laptops run hot, and when they over-heat, they will lock.  I've also seen bad memory lock a system.  Try the memtest to verify it.

How much time does it take to lockup?  Use a small burst of canned air to cool the proccess every 5 minutes... does that keep it running?

---

### Post by veroslav on 2012-04-19
Hi lisanels47 and thank you for your comment.

I am unable to do anything after a freeze has occured (see my previous post). Ctrl-Alt-F1 through Ctrl-Alt-F6 does not have any effect at all.

I haven't tried pinging the freezed computer from another one, might try out that the next time a freeze occurs.

I'we run the Dell provided diagnostics boot utility and performed a thourogh test of the hardware, is that an equivalent of performing a memtest from grub? The Dell test came back negative, no hardware errors.

I'v used lm-sensors in order to monitor the temperatures, and mostly they have been in the range of 45-55 (with 86 being high). The fan is barely working all the time.

However, i think I managed to find the cause, hopefully, for what is the reason behind the freezes I am experiencing. Have a look at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)

It is the same architecture as my computer. After I first installed Ubuntu 11.10 I didn't experience any freezes for a week. However, the temperatures were a bit high so I read (see also the bug report above) that adding i915.i915_enable_rc6=1 to kernel parameters would solve the overheating issue. It did, but it seems it was also what started causing the freezing issues for me.

This has now been fixed in Ubuntu 12.04 (again according to the last few comments in the bug above) and after reading that I installed Ubuntu 12.04. Since then, for the last 5 days, I haven't experienced any freezes and the temperatures seem to be cool as well.

Keeping my fingers crossed!

Regards,
Veroslav

---

### Post by lisanels47 on 2012-04-19
Excellent!  I'm also running 12.04, and it's working well.  Lots of updates every day, but overall, it's doing good.

---

