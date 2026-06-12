---
title: "Dell XPS 13 ultrabook compatibility"
date: 2012-02-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by erlguta on 2012-02-28
Hello.

Now that the new Dell XPS 13 ultrabook is out I open this post to discuss about Ubuntu installation & compatibility.
Somebody is planning to buy and install Ubuntu in this nice ultrabook?

It would be nice to make a review about:
- Overall performance
- Peripherals (wifi, ports)
- suspend/hibernate
- Battery life with ubuntu
- media buttons
- boot speed
etc.

I hope that some brave of you dare to buy and test it with ubuntu ;)

---

### Post by Mark Phelps on 2012-02-28
Guess you didn't notice that there is a Dell Ubuntu support forum here.  You would do better posting this there.

---

### Post by querolus on 2012-02-29
I'm planning to buy the dell XPS 13 ultrabook and install ubuntu, but i'm new to Ubuntu and would like to wait until somebody tests it. I don't think it takes long. If you know about anybody testing it or having it installed already tell him/her to share the experience.

By the way, i've tried to find this post in Dell thread and couldn't find it...

---

### Post by erlguta on 2012-03-01
Hello.

Now that the new Dell XPS 13 ultrabook is out I open this post to discuss about Ubuntu installation & compatibility.
Somebody is planning to buy and install Ubuntu in this nice ultrabook?

It would be nice to make a review about:
- Overall performance
- Peripherals (wifi, ports)
- suspend/hibernate
- Battery life with ubuntu
- media buttons
- boot speed
etc.

I hope that some brave of you dare to buy and test it with ubuntu ;)

---

### Post by erlguta on 2012-03-01
Yes, it is true. I have opened one new thread in the Dell section:

[http://ubuntuforums.org/showthread.php?t=1933864](http://ubuntuforums.org/showthread.php?t=1933864)

---

### Post by howefield on 2012-03-01
Threads merged.

---

### Post by happicow on 2012-03-02
I managed to install Xubuntu 11.10 on the base Dell XPS 13 model without any issues that I have found.  There are power consumption issues and the battery does not last as long as it should.  But as I understand it, a lot of power issues will be resolved in 12.04 due out in a month or two.

---

### Post by querolus on 2012-03-02
And which XPS 13 are you using? The i5 i7? Which hard drive?

Thanks for the help

---

### Post by Paerez on 2012-03-06
Hey All,

I've put Xubuntu 11.10 on the Dell XPS 13 128gb i5 version. I'm noticing the following issues out of the box:

[LIST=1]
[*]Unable to adjust brightness
[*]two finger scrolling does not work
[*]I'd like to enabled "tap to click" instead of using the click pad. not sure how.
[*]turning off bluetooth via nm turns off wireless
[/LIST]

That's all I've got so far. I'm looking into xorg options for the intel i915 now.

---

### Post by Paerez on 2012-03-06
ok, to fix brightness, run as root:

echo 0 > /sys/class/backlight/intel_backlight/brightness

Then the keyboard brightness controls work.

EDIT: I put this script into /etc/init/backlight.conf:

```
start on runlevel [23]
task
exec /bin/echo 0 > /sys/class/backlight/intel_backlight/brightness
```

It works when I run "sudo start backlight" but it doesn't happen on boot. Not sure why. I'm new to upstart. Any tips?

---

### Post by Paerez on 2012-03-06
Thought I'd drop another note here. Dmesg says the trackpad is ImPS/2:

```
[    3.258400] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input11
```

Anyone know what kind of trackpad it really is and how to have it detect the right driver? I'm guessing that will fix up the touchpad scrolling issues.

---

### Post by erlguta on 2012-03-07
Paerez, can you make one more complete review of the installation in the new Dell ultrabook?
Is this one?: [http://www.dell.com/html/global/xps13/xps-13-ultrabook.html?c=us&l=en&s=dhs&ref=usen-XPS13-tile]("http://www.dell.com/html/global/xps13/xps-13-ultrabook.html?c=us&l=en&s=dhs&ref=usen-XPS13-tile")
- The installation was clean?
- What about touchpad, wifi, battery life?
- Does it suspend/hibernate ok?

It would be apreciate more info ;)
Thank you

---

### Post by Paerez on 2012-03-07
Yes, that's the one.

Install was clean. 12.04 beta was touchy, so I stuck with 11.10.

As I said farther up, touchpad is not recognized properly. This means no two-finger scrolling or multitouch. But it works as a clickpad well. I can rest my thumb on the bottom and mouse around and it works great. No right-side-scrolling like on older touchpads either.

Wifi works great.

Battery life I'm not sure yet. Rough estimate is that you'll get 5h on medium brightness not taxing the cpu constantly. So web browsing, typing, that sort of thing.

Suspend works perfectly and quickly. Haven't hibernated yet.

Also as I mentioned above, the brightness controls don't work until you run the command I posted. You have to run it every time it boots or comes back from sleep.

---

### Post by Paerez on 2012-03-07
Hmm, some bad news.

Looks like the touchpad is a Cypress, which was previously used in the 15z. It's closed source and there's no linux driver and no reverse-engineered driver.

At the very least I'm hoping to get scrolling down the side of the trackpad working.

---

### Post by Paerez on 2012-03-08
It does not seem to hibernate out of the box. The pm log shows it hibernating but then waking right back up. Doesn't crash it or anything. Just doesn't work.

I don't really care though because it's supposed to be able to sleep for days.

The next thing that's important to me is if displayport => vga adapter works. I'll let you know.

---

### Post by opasnost on 2012-03-09
> **Paerez said:**
> It does not seem to hibernate out of the box. The pm log shows it hibernating but then waking right back up. Doesn't crash it or anything. Just doesn't work.

I don't really care though because it's supposed to be able to sleep for days.

The next thing that's important to me is if displayport => vga adapter works. I'll let you know.

It should hibernate did you dedicate a swap partition with enough space?

Has anyone moved/mounted their temp folder into ram to reduce the number of read write cycles to save the ssd a bit? I remember reading an article about that but I don't remember where. Any thoughts???

---

### Post by Paerez on 2012-03-09
Yeah, I setup swap for hibernate. I really didn't look into it much. I don't use hibernate.

---

### Post by tterb on 2012-03-09
Thanks for posting your experience here!

Does the backlit keyboard work?

---

### Post by Paerez on 2012-03-09
Keyboard works perfectly. It's pure hardware.

---

### Post by tterb on 2012-03-09
Right, I was just wondering if the backlight worked and turned on and off

---

### Post by Paerez on 2012-03-09
yup. There are 3 modes that it cycles between via the key. High, Low, Off.

---

### Post by erlguta on 2012-03-13
Paerez thank you for your information.
How long is the battery life with ubuntu?
Have you tested the minidisplay to vga/dvi port yet?

Thank you

---

### Post by Paerez on 2012-03-13
You are welcome!

I'm still not sure about the battery life. I've been sleeping it, charging, rebooting, so nothing "clean".

My estimate is 5h of "normal use". I'm in Xubuntu and I use powertop.


I just tested minidisplay to vga, and it works perfectly. No setup needed. Just go to ubuntu's display config and the external monitor works great.

I bought the [dell adapter]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=331-2972&baynote_bnrank=0&baynote_irrank=0&~ck=baynoteSearch") (item 331-2972).

---

### Post by Boumy on 2012-03-13
Quick Thanks to Paerez for tests and backlight commands, everything runs great on my new machine !

Just for information on my side the battery was around 3 hours without the backlight command, surely more now !!

---

### Post by Dell-Bill B on 2012-03-14
> **Paerez said:**
> It does not seem to hibernate out of the box. The pm log shows it hibernating but then waking right back up. Doesn't crash it or anything. Just doesn't work.


Hi all. I'm not a Linux expert, but while I was Googling around looking for posts about hibernate on XPS 13, I ran across this thread. Just wanted to drop in a note that may clear things up. I'm sure you all would have figured it out eventually if you haven't already.

We're marketing Intel Rapid Start pretty prominently in places for this platform. iRST will not wake a system from hibernate, hence a BIOS setting change is needed to re-enable hibernate in any OS. You can get to the setting from the Advanced screen in the BIOS via the "Intel Rapid Start Technology" sub menu. You just need to change the "iRST Support" value to Disabled. In Windows this brings the Hibernate option back automatically. Not sure what additional steps are needed in Linux.

Hope this helps in some way.

---

### Post by Paerez on 2012-03-14
Cool thanks Bill. I'll give it a shot. Although I prefer the sleep mode.

My guess is that just flipping that switch in the bios will make linux happy. Usually intel drivers are easy to get along with :-)


Also I wanted to drop some of the benchmarks I took on startup:

Cold boot to stock windows 7 installed by dell: 12 seconds
Cold boot to ubuntu (mashing enter for grub): 10 seconds
Cold boot to windows 8 consumer preview: 6 seconds
Wake from suspend: 1 second or less (all oses)

Really, really impressive. Well done!

---

### Post by erlguta on 2012-03-15
Wow, i love this ultrabook.
I think I am going to wait for your news about touch pad issues. When they are resolved I will order mine instantly!

---

### Post by daihard on 2012-03-18
Glad I've found this thread. I am thinking about buying an XPS 13 and installing Kubuntu 12.04 on it. (I've always been a KDE guy.) Looks like I won't need to worry too much about compatibility issues. Thanks all for the useful information.

---

### Post by ufrocks on 2012-03-18
I'm on Gentoo but I have to enter:

echo 0 > /sys/class/backlight/intel_backlight/brightness

every time my XPS 13 turns off its screen for a bit.  I'm not sure how to figure out what is causing this.  Any ideas?  I'm using xfce4.

---

### Post by jayrod on 2012-03-18
I have been watching and waiting for the release of the Dell XPS 13.

Paerez, thank you for sharing your experiences with it.

Bill B from Dell, thank you for your input.  It is always nice to see Dell active on the Linux side of things.

I am not surprised there are touchpad issues.  I expected this when I heard it was integrated.  Hopefully, Dell can use their influence and help make some progress with Cypress touchpads on the Linux side of things.

According to AnandTech, the Dell XPS 13 gets 8.5 hours of battery life at idle, just over 6 on the internet, and just under 4.5 on H.264.

I am still undecided, and I will probably wait for Ivy Bridge availability.

---

### Post by ufrocks on 2012-03-18
I found another clue to my backlight control problem on Gentoo.  It stops working whenever I shut the screen and I have to issue the command again.  Does everyone else's backlight control keep working after shutting and opening the screen?

---

### Post by Boumy on 2012-03-20
Same for me, and I have no clue how to fix it.

---

### Post by diegosax on 2012-03-20
Hi, on my just installed ubuntu the brightness almost works, the problem is that when I use the fn keys to make the screen darker it starts to blink, it gets dark(what I set) and max bright, and just stops blinking if I set the brightness to max light. Anyone have any ideas on how to resolve this?

I also need to find a way to make the scrolling work, just this would be enough for me to keep with ubuntu.

Besides these problems the system is running smooth and VERY fast, specially with gnome, I have no other complaint about ubunu on Dell xps 13

P.S I'm using Ubuntu 11.10 32 bits

---

### Post by ufrocks on 2012-03-20
Extremely fast here too.  Issue this command as root to fix the brightness:

echo 0 > /sys/class/backlight/intel_backlight/brightness

---

### Post by diegosax on 2012-03-20
Thanks!

The brightness got to te minimium but if i try to change it with the fn key it starts blinking again and just stops if set to minimum or max

---

### Post by ufrocks on 2012-03-20
Hmmm, I have different behavior but I'm on Gentoo.  I think there are some people here on Ubuntu with my same behavior though.

---

### Post by diegosax on 2012-03-21
I dont know why, but after I restarted the system and run the command above the brightness control works. But I have to run the command every time I log on.

What about the scrolling? Does anyone have any ideas?

---

### Post by ufrocks on 2012-03-21
> But I have to run the command every time I log on.
You also have to run it every time you close your screen.  I'd love to find a way around that.

---

### Post by Wi11iwaw on 2012-03-21
Hi all,
I am very new to Linux and was hoping I could get some help.  
I recently bought a Dell XPS 13 and would like to dual boot Ubuntu with it.  I have installed Ubuntu before, but I have never tried a dual boot.

My first question:  Can I partition 1 for Windows, 1 for Window recovery, 1 for Ubuntu and then 1 partition to store all data (photos, docs, ect..) to be used for both OS at any given instance.  Is this possible or ideal?

Also, I was wondering what your thoughts were on partition sizes for the above set up.  I am currently using Ubuntu and am using about 10GB total.

I have been looking around and have read this ([https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)).  It seem pretty strait forward, but I was wondering if anybody else had some instructions to recommend...eg: booting into Unbutu first.

Thanks all for your help...and sorry for being such a noobie.

---

### Post by stevebeaulac on 2012-03-21
I've had my XPS 13 for just about a week and I'm liking it a lot.

I seem to be having some issue with Bluetooth, brightness and trackpad. 

Bluetooth sometime, randomly, disconnect and won't allow me to turn it back on. I can use the hcitool to reset it and then it works again.

Brightness, same issue as everybody else, I wrote this script

```
cat /etc/pm/sleep.d/10_dell_xps_ultrabook 
#!/bin/sh

# Action script to enable backlight on Dell XPS 13.3 ultrabook

case "${1}" in
	resume|thaw)
		/bin/echo 0 > /sys/class/backlight/intel_backlight/brightness
		;;
esac

```

seem to help.

Looking into the cypress i2c drivers to see if we can get more function out of this trackpad.

[http://lwn.net/Articles/456366/](http://lwn.net/Articles/456366/)

Using Ubuntu 12.04.

---

### Post by Wi11iwaw on 2012-03-21
I don't know if this helps the track pad situation out, but Dell just release a BIOS (thermal management) and track pad driver update today.

[http://www.dell.com/support/drivers/us/en/555/DriverDetails/DriverFileFormats?DriverId=TP26N&FileId=2905995340&productCode=xps-13-l321x&urlProductCode=False](http://www.dell.com/support/drivers/us/en/555/DriverDetails/DriverFileFormats?DriverId=TP26N&FileId=2905995340&productCode=xps-13-l321x&urlProductCode=False)

[http://www.dell.com/support/drivers/us/en/19/DriverDetails/DriverFileFormats?DriverId=C0VG5&FileId=2902722114&productCode=xps-13-l321x&urlProductCode=False](http://www.dell.com/support/drivers/us/en/19/DriverDetails/DriverFileFormats?DriverId=C0VG5&FileId=2902722114&productCode=xps-13-l321x&urlProductCode=False)

---

### Post by diegosax on 2012-03-22
The problem is that these updates are for windows only

---

### Post by openecho on 2012-03-25
I bought my XPS 13 Ultrabook on Friday and spent the weekend backing up the recovery and dell utility partitions and dual booting it with Windows 7/Ubuntu 11.10.

I have to say, this is the first time I have been happy with a dell notebook since the M1330 (Last XPS 13 I think). The build quality of this guy is great and its perfect if you need to carry a work notebook and want one of your own.

For me, 11.10 worked pretty much straight out of the box. I will apply the brightness scripts in the previous posts.

> 
@stevebeaulac
Looking into the cypress i2c drivers to see if we can get more function out of this trackpad.

[http://lwn.net/Articles/456366/](http://lwn.net/Articles/456366/)


If you find anything please let us know. The touch pad is great hardware.. but sad its all closed.

---

### Post by svenole on 2012-03-28
I've been sitting here with my XPS 13 ultrabook running standard 11.10, reading about the issue with brightness. My system installed fine, runs fine, suspend fine, hibernate fine, works fine on wireless, runs on battery for between 3 and 4 hours, etc etc. I have the same two issues mentioned in this thread. Trackpad and brightness. I do not care much about the trackpad at this time. But brightness comsumes battery...

Well. The command suggested does not work. Despite using sudo, the command responds with "no access". I did cat the file and it contains only this "0". 

Running the job: "sudo start brightness" gives "start: unknown job brightness". Well. Maybe this last one was a script that I've not put in...

Anyway, I am not able to fix this brightness issue. Using the hot keys, gives the brightness window on screen reporting brightness up and down. But nothing really happens...Screen stays the same.

Is there something that I missed here?

Rgds, 

svenole

---

### Post by yoblin on 2012-03-29
To confirm... you can't do any scrolling using the touchpad, such as using the right hand side with one finger? Or is it just that you can't do it using the multitouch gestures but the side of the touchpad works?

Does middle-clicking work by pressing both mouse keys? (Must have this for chromium!)

Thanks.

svenole: did you create the script that stevebeaulac posted? Place it in /etc/pm/sleep.d/10_dell_xps_ultrabook, the first line should be #!/bin/sh. (You might need to do chmod +x on it to make it executable?)

---

### Post by svenole on 2012-03-29
Well. There isn't much use in creating this script if testing the command in a terminal doesn't work... ;-)

---

### Post by pbarta on 2012-03-30
The XPS 13 ultrabook doesn't have a internal CDROM drive. I have managed to get the system to boot from the dell external optical drive and get started on the alternative CD installation (because I want to set up encryption on the disk), but got stuck about one minute into install with the "Your installation CD-ROM couldn't be mounted." error.

I also tried install from a flash drive, and ended up in the same state.

I tried adding cdrom-detect/try-usb=true to the boot parameters, but that doesn't work in either scenario.

What am I doing wrong? Clearly, others appear to have gotten this to work.

Thanks.

---

### Post by erlguta on 2012-03-31
> **svenole said:**
> runs on battery for between 3 and 4 hours, etc etc. I have the same two issues mentioned in this thread. Trackpad and brightness. I do not care much about the trackpad at this time. But brightness comsumes battery...


svenole

Svenole, 3/4 hours is very poor, isnt it?. given that in windows Dell promises 8/9 hours... 
That will be for the issue of the brightness?
Maybe with 12.04 LTS, the brightness is resolved and with the new module that improves battery consumption I hope the battery last longer...

---

### Post by garak on 2012-03-31
> **pbarta said:**
> The XPS 13 ultrabook doesn't have a internal CDROM drive. I have managed to get the system to boot from the dell external optical drive and get started on the alternative CD installation (because I want to set up encryption on the disk), but got stuck about one minute into install with the "Your installation CD-ROM couldn't be mounted." error.

I also tried install from a flash drive, and ended up in the same state.

I tried adding cdrom-detect/try-usb=true to the boot parameters, but that doesn't work in either scenario.

What am I doing wrong? Clearly, others appear to have gotten this to work.

Thanks.

I just enabled USB in boot sequence (in BIOS settings).
Then downloaded the iso, copied to USB pendrive (using USB creator), and installed from pendrive.
The only issue I had was while trying to create new partition during installation process: so I stopped it, created partition with gParted and then tried again.
So smooth.

---

### Post by cps19 on 2012-03-31
Hi!  Has anyone else noticed that their XPS 13 Ultrabook runs noisier when running Ubuntu  than the Windows 7 that comes with it?  The fan seems to kick in to medium speed almost constantly whereas in Windows it spins much slower most of the time.

---

### Post by crashbit on 2012-03-31
> **cps19 said:**
> Hi!  Has anyone else noticed that their XPS 13 Ultrabook runs noisier when running Ubuntu  than the Windows 7 that comes with it?  The fan seems to kick in to medium speed almost constantly whereas in Windows it spins much slower most of the time.

[http://www.engadget.com/2012/03/21/dell-xps-13-ultrabook-bios-update-download/](http://www.engadget.com/2012/03/21/dell-xps-13-ultrabook-bios-update-download/)

---

### Post by cps19 on 2012-03-31
> **crashbit said:**
> [http://www.engadget.com/2012/03/21/dell-xps-13-ultrabook-bios-update-download/](http://www.engadget.com/2012/03/21/dell-xps-13-ultrabook-bios-update-download/)

Thanks crashbit, that was the first thing I did when I got the xps.  ;)

Whenever there's a process running at >20% CPU for more than approx 10 seconds, the fan kicks in to medium speed.  Is this normal?

---

### Post by crashbit on 2012-03-31
cps19,

You can install sensors and control the cpu temperature

---

### Post by pbarta on 2012-03-31
> **garak said:**
> I just enabled USB in boot sequence (in BIOS settings).
Then downloaded the iso, copied to USB pendrive (using USB creator), and installed from pendrive.
The only issue I had was while trying to create new partition during installation process: so I stopped it, created partition with gParted and then tried again.
So smooth.

Thanks for the reply. I gave up on a 11.10 install, so I didn't try what you have suggested here.

I burned a 12.04 beta (alternate) install disc and everything worked just as expected without any need to do anything special. No problems with the CD not being recognized during the boot. No need for any special boot command line switches. I didn't try a USB install once I got things running.

My experience with the machine so far--about 4 hours--is that everything other than the problems already discussed here works fine. 

I've got the i5 chip, and, so far, I haven't managed to saturate the cpu except when I was creating a big truecrypt volume. 

Fun machine to use. 4 Gb of memory does everything I need.  Runs 15 tabs on Chrome without swapping. I bought this for work. Think I'll buy another one for home...

---

### Post by ufrocks on 2012-04-03
Does anyone know if the BIOS update should be installed to a machine with the i5 proc or if it's just for i7?

---

### Post by erlguta on 2012-04-04
> **pbarta said:**
> 
My experience with the machine so far--about 4 hours--is that everything other than the problems already discussed here works fine. 

pbarta, so problems with brightness are solved with 12.04 without scripts?. or is it allways at maximun brightness?
What about the noise?. Is this laptop silent?

---

### Post by garak on 2012-04-04
> **erlguta said:**
> pbarta, so problems with brightness are solved with 12.04 without scripts?. or is it allways at maximun brightness?
What about the noise?. Is this laptop silent?

Noise is really low. You can hear it only in a very very quiet place

---

### Post by Paerez on 2012-04-04
12.04 still needs the backlight script. Noise is silent until you start doing something intense (like run updates or programming or a flash game).

---

### Post by ufrocks on 2012-04-06
I was having trouble with the USB 3.0 port until I updated to the linux-3.4-rc1 kernel.

---

### Post by gensym on 2012-04-06
> **erlguta said:**
> pbarta, so problems with brightness are solved with 12.04 without scripts?. or is it allways at maximun brightness?
What about the noise?. Is this laptop silent?

The way I  work around the brightness issues is adding the 

```

echo 0 > /sys/class/backlight/intel_backlight/brightness

```

line to /etc/rc.local

and the script stevebeaulac posted (#40) to /etc/pm/sleep.d/.

The greatest annoyance so far is the touchpad.

---

### Post by ufrocks on 2012-04-07
I added stevebeaulac's script to /etc/pm/sleep.d/ and made it executable but my screen still goes to maximum brightness when I close the top.  Does anyone know what I'm doing wrong?

---

### Post by ufrocks on 2012-04-08
> **ufrocks said:**
> I was having trouble with the USB 3.0 port until I updated to the linux-3.4-rc1 kernel.

3.3.1 seems to fix it too and 3.3.0 didn't so the patch must have been applied between those releases.

---

### Post by gensym on 2012-04-11
Today I replaced the stock kernel of 12.04 with the Liquorix kernel (3.3.0-1), the battery lasts at least an hour longer now, which is very nice.

---

### Post by mustafaerdinc on 2012-04-12
> **gensym said:**
> Today I replaced the stock kernel of 12.04 with the Liquorix kernel (3.3.0-1), the battery lasts at least an hour longer now, which is very nice.

how exactly you did? will you please tell me step by step what to do.

---

### Post by bdugan on 2012-04-12
I have one of these XPS 13's, too (the i5 model) and basically agree with everything written above here: it works very well with Ubuntu (I was running 11.10 but switched to the 12.04 pre-release).

I do have the screen brightness issue, which is mostly resolved with the sleep script (I say "mostly" because there seem to be times when it doesn't work, but I'm not certain about that yet.)

As someone else said, the trackpad is the main annoyance: it works but only as a circa 1990 click & drag kind of thing: no tap-to-click and definitely no mutli-touch.  I wish Cypress would help with some linux drivers.

I really like this laptop from a design standpoint except for one serious gripe:  the ventilation on the bottom!  I think this means it has to be used on a hard surface, otherwise the air flow is stopped.  That seems really stupid to me, and completely negates the claims Dell makes about the "coolness" of the graphite lower body.

But there's always been some problem with any laptop I've had, so I'll live with it.  And I care more about it being fast, which it is.

---

### Post by gensym on 2012-04-12
@mustafaerdinc


Add the liquorix repo  to your sources
```

# paste this in /etc/apt/sources.list.d/liquorix.list
deb http://liquorix.net/debian sid main
deb-src http://liquuorix.net/debian sid main
```Download the keyring

```
apt-get update
apt-get install '^liquorix-([^-]+-)?keyring.?'
```
Download the kernel image (assuming that you've installed the 64 bit version ubuntu)

```
apt-get install linux-image-liquorix-amd64
```Reboot.

PS: Liquorix is a kernel that is originally designed for debian, so using it with Ubuntu may be a bit experimental.
At the time being, this causes some problems with fsck (so the boot process takes like a second longer), but that might as well be caused by my encrypted drives. I will post a solution if I find a workaround for that. 

The Jupiter applet (a power management thingy) can also be helpful to improve battery life:
```
add-apt-repository ppa:webupd8team/jupiter
apt-get update 
apt-get install jupiter 
```Edit:

I also use the following grub switches to ease up the power usage

```
i915.i915_enable_rc6=1 
i915.i915_enable_fbc=1 
i915.lvds_downclock=1
```

---

### Post by ccfiel on 2012-04-13
Hello guys,

I have install ubuntu 12.04. I have a problem of xps 13 getting hot in the lap. I did not get this problem in windows 7. any ideas how to solve this one?

Chris Ian

---

### Post by ufrocks on 2012-04-13
Here is more info on gensym's grub parameters:

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

gensym, have you tested those and not found any problems?  Have you tried  pcie_aspm=force?

ccfiel, these parameters could solve your overheating problem.

---

### Post by gensym on 2012-04-13
@ufrocks
Yes, they seem to work fine for me. I didn't try forcing active state power management, but it seems like a good idea, I shall give it a try.

---

### Post by Rob F on 2012-04-14
gensym, others,

Can you tell me exactly where you add those three powersavign lines to the grub.cfg file?

I happily opened up grub.cfg with sudo gedit but then got a bit nervous about putting the wrong line in the wrong place and stuffing everything up..

thanks in advance

RF

---

### Post by ufrocks on 2012-04-14
I'm a Gentoo guy, but for me this line in grub.conf:

kernel /boot/kernel-3.3.1-hardened-r1 root=/dev/sda2

becomes this line (all of this on the same line):

kernel /boot/kernel-3.3.1-hardened-r1 root=/dev/sda2 i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 pcie_aspm=force

BTW, huge difference in temperature and fan noise with these options turned on.  Windows obviously uses this stuff.  I haven't tested battery life yet but I bet there's a large improvement.

Has anyone figured out if the BIOS update can be installed for i5 machines?

---

### Post by ccfiel on 2012-04-14
ufrocks it works my xps 13 its not overheating. Thanks

> **ufrocks said:**
> Here is more info on gensym's grub parameters:

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

gensym, have you tested those and not found any problems?  Have you tried  pcie_aspm=force?

ccfiel, these parameters could solve your overheating problem.

---

### Post by ccfiel on 2012-04-14
i have install the bios update in i5 its ok. :)

> **ufrocks said:**
> I'm a Gentoo guy, but for me this line in grub.conf:

kernel /boot/kernel-3.3.1-hardened-r1 root=/dev/sda2

becomes this line (all of this on the same line):

kernel /boot/kernel-3.3.1-hardened-r1 root=/dev/sda2 i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 pcie_aspm=force

BTW, huge difference in temperature and fan noise with these options turned on.  Windows obviously uses this stuff.  I haven't tested battery life yet but I bet there's a large improvement.

Has anyone figured out if the BIOS update can be installed for i5 machines?

---

### Post by Rob F on 2012-04-14
Thanks. I'll try it. I'm assuming your grub.conf is my grub.cfg..

RF

---

### Post by gensym on 2012-04-14
I think with grub2 it is bad practice to edit grub.cfg directly

I added those switches to /etc/default/grub

I changed the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 pcie_aspm=force"
```And then ran
sudo update-grub

Edit: Out of curiosity: which fstab switches are you using? It is my first time using an SSD  and the only two that I have found that seemed to be of use were noatime and discard. Is there another switch that I should be aware of?

---

### Post by crashbit on 2012-04-14
Hi!

I found a bug open in launchpad, for dell xps 13 touchpad problem. No solution yet, but I expected

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/978807](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/978807)

---

### Post by Rob F on 2012-04-14
gensym,

thanks - followed your advice, edited grub, ran grub update and rebooted the machine. so... how do I actually tell if it worked? 

[realises he is, despite 15 years of linux, still a noob]

aha, viewed kernel parameters with grub customizer and it seems to have worked.

thanks

RF

---

### Post by gensym on 2012-04-14
^II generally press 'e' at the grub boot screen, to see whether those changes have taken effect.

---

### Post by ccfiel on 2012-04-14
battery life is not good. I got only 2-3 hours. is this normal?

> **erlguta said:**
> Hello.

Now that the new Dell XPS 13 ultrabook is out I open this post to discuss about Ubuntu installation & compatibility.
Somebody is planning to buy and install Ubuntu in this nice ultrabook?

It would be nice to make a review about:
- Overall performance
- Peripherals (wifi, ports)
- suspend/hibernate
- Battery life with ubuntu
- media buttons
- boot speed
etc.

I hope that some brave of you dare to buy and test it with ubuntu ;)

---

### Post by ufrocks on 2012-04-15
> i have install the bios update in i5 its ok.
How are you guys installing from the .exe file?

---

### Post by ccfiel on 2012-04-15
I have installed it before I have install ubuntu. so the OS was win7.

> **ufrocks said:**
> How are you guys installing from the .exe file?

---

### Post by ufrocks on 2012-04-16
After a lot of frustration with trying different methods, I finally got the BIOS updated via unetbootin.  It's really easy.  Just mount a USB key, start unetbootin, select FreeDOS and install, copy the BIOS update file to the USB key, reboot into the USB key, switch to the C drive with "c:" and execute the BIOS file.

Does anyone else hear a very slight but eventually very annoying whining sound from their laptop after this update?  I think it's the fan running at a low speed and constantly oscillating between a slightly lower and slightly higher speed.  It's getting on my nerves and wasn't there before the update.

---

### Post by gensym on 2012-04-16
@ufrocks

Is there a noticeable performance increase, once you install the upgrade or is it just placeboish?

Edit: Holy cow, my computer is really really silent now!
Edit2: I got really crappy wifi connection quality under Ubuntu (I am sitting right next to my wireless router and the signal power is %60). Is there a way to improve this?  (@ufrocks, is it the same under gentoo too, if so would you be kind enough to name the wireless driver you are using (ofc. if it is not iwlwifi as it is in ubuntu)).

---

### Post by ufrocks on 2012-04-17
Call me crazy but I try to minimize my exposure to radiation so I've removed the laptop's internal wireless card and I only use a USB wifi dongle so I can physically remove it when it's not in use and I can attach it to the end of a 5 meter USB extension cable when it is in use.  I know for a fact that some or all devices with a wifi transmitter pump out radiation as long as they're powered.

Anyway, yeah the BIOS update makes it super silent but do you get that weird oscillating fan noise after the update?

---

### Post by gensym on 2012-04-17
Yes, I can hear a silent whistling if I  try listening  very hard, but it isn't too big of an issue for me.

---

### Post by ufrocks on 2012-04-17
Whistling, yeah it does kind of sound like that.  Does the tone of your's rise and fall slightly every 3 seconds?  That's the part that drives me nuts.

---

### Post by gensym on 2012-04-17
No there is no oscillation, at least not on my machine.

---

### Post by cmont899 on 2012-04-23
Paerez

> [*]turning off bluetooth via nm turns off wireless

This is controlled in the bios. You can set the switch to control Bluetooth, Wifi, Cellular Card (if you have one) or any combo of the 3.

Chris

---

### Post by ccfiel on 2012-04-24
Hello Guys,

Any update in the trackpad. for now does not support multitouch, tapping, scrolling. only the basic mouse function moving the mouse and right,left button are working. any workaround? :)


chris

---

### Post by ufrocks on 2012-04-25
Does anyone else have trouble with their trackpad jumping around and doing crazy things?  I think it's because of my palm brushing against it, but I think drivers try to fix that, right?

---

### Post by bekirserifoglu on 2012-04-28
I know this is not related to ubuntu but here is [a great video guide]("http://blog.parts-people.com/category/dell-xps-13-ultrabook-repair-manual/") if you ever have to tear your xps 13 open.

And here is [the owner's manual]("http://www.google.com.tr/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CD0QFjAB&url=http%3A%2F%2Fsupport.dell.com%2Fsupport%2Fedocs%2Fsystems%2FxpsL321x%2Fen%2Fom%2Fpdf%2Fom_en.pdf&ei=QcabT7P_M4mJ4gSL6eGpDg&usg=AFQjCNE0A36f1eSYEiMTlHjeWP_eE62wkA&sig2=XM1sLkoXX7yk5W-_Q-PKYg"), which I didn't get with my xps 13. It also contains the steps to fix your xps by opening its chasis.

---

### Post by garak on 2012-04-29
BTW, anyone has found a good case for this laptop?
I would love to buy one from Canonical (see [http://shop.canonical.com/product_info.php?products_id=870](http://shop.canonical.com/product_info.php?products_id=870)) but unfortunately none of proposed measures seems to fit :(

---

### Post by solidsnake666 on 2012-05-01
> **garak said:**
> BTW, anyone has found a good case for this laptop?
I would love to buy one from Canonical (see [http://shop.canonical.com/product_info.php?products_id=870](http://shop.canonical.com/product_info.php?products_id=870)) but unfortunately none of proposed measures seems to fit :(

I ended up using a 13" incase neoprene sleeve for a macbook. It's got a little extra space but fits it well enough and has good cushion to it.

---

### Post by ufrocks on 2012-05-02
Firmware A04 is out.

BTW, the Windows folk on the Dell forum are complaining about the Cypress trackpad too which must be bad news:

[http://en.community.dell.com/support-forums/laptop/f/3518/p/19439101/20097694.aspx#20097694](http://en.community.dell.com/support-forums/laptop/f/3518/p/19439101/20097694.aspx#20097694)

---

### Post by Rob F on 2012-05-03
What's in firmware AO4? I did AOs 1 through 3 from windows and then nuked it to install ubuntu 12.04. I've been using it on this machine for ~3 weeks now, and am on my second business trip with it, and I have to say its working like a dream. OK the touchpad isn't great, but its completely useable (and anyway I travel with a mini wireless mouse), the OS overall is extremely fast, everything works including the output to a projector via a minidisplayport->VGA adapter (and that did NOT work on my last Dell laptop without lots of faffing around in NVIDIA settings). Hardware wise the screen is beautiful (why the reviewers whinged about not high enough resolution I don't know - I work with scientific imaging and its excellent), the keyboard is great (have typed many 1000s of words on it already) and I'm now getting 5+ hr battery life (seems to have got better with time). Best laptop I've had for quite some years. Also, I raced it in some scientific data reduction against a couple of collleagues' Macbook Pros, and it beat both of them :) 

Finally... I have the official Dell leather slip case and its very nice.

---

### Post by gensym on 2012-05-03
I just use one of those 13" Case Logic sleeves,  it is a bit baggy, but it doesn't disturb me that much.

---

### Post by gtr_golf on 2012-05-06
XPS 13 still can not remember a brightness value in Ubuntu 12.04 LTS. Although, I've tried to echo x > /sys/class/.../brightness, but it gets stuck at Maximum every time I reboot.

---

### Post by yoblin on 2012-05-07
This might be interesting --

[http://www.ideastorm.com/Idea2SessionIdea?v=1336396592542&id=a017000000hIx3bAAC](http://www.ideastorm.com/Idea2SessionIdea?v=1336396592542&id=a017000000hIx3bAAC)

Someone might want to install the ISO they released and see if it has any custom drivers or anything.

EDIT:

Nevermind, blog post ([http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/](http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/)) says it has not fixed the touchpad issues. HOWEVER, it looks like Dell is pestering the touchpad manufacturer for an update and working with Canonical! So not bad news..

---

### Post by erlguta on 2012-05-08
I hope touchpad issues are resolved soon.
It is interesting the projetc Sputnik ([http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/](http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/))

A question about the battery. Somebody around here say that the battery life lasts 4 hours, others only two, Del says 8 with windows. So, how long is the battery life with normal use in ubuntu?
It is still no clear...

---

### Post by Rob F on 2012-05-10
I'm getting 4-5 hours battery life. My typical usage is 4-6 active desktops, with email, browser, editing/scripting, presentation preparation and occasional number crunching. Regardless of what they advertised, I'm pretty pleased with it - its considerably better than my last couple of laptops.

---

### Post by ufrocks on 2012-05-10
Firmware A04 reported fixes are:

1.Increased coverage of supported AC adapters

2.Updated LED behaviors for the keyboard backlight and the charge indicator

3.Improved S3 resume behavior

4.Further refinement of fan acoustics

---

### Post by denniswisnia on 2012-05-15
Hope we get any news in a few days. Really love my XPS with Ubuntu. But with an additional mouse is it annoying.

The FAN is very nervous. I have the BIOS Version A04 and he runs often. And what you do to increase the battery lifetime?

---

### Post by gensym on 2012-05-19
> **denniswisnia said:**
> Hope we get any news in a few days. Really love my XPS with Ubuntu. But with an additional mouse is it annoying.

The FAN is very nervous. I have the BIOS Version A04 and he runs often. And what you do to increase the battery lifetime?

I posted some grub switches (2/3 pages ago) which makes things smoother.
If the battery time isn't still good enough you can try installing  the liquorix kernel,  or install the stock kernel and apply the ck patches...
I also have the Jupiter applet installed which does some additional power management.
With those installed, I get nearly 6-7h in Kubuntu.

On  another note, what is the average CPU temp you guys get under Linux? 
In windows I get 50 celcius degrees but in Linux it is around 60 celcius degrees (which is bugging me a little, am I doing something wrong?).

---

### Post by ufrocks on 2012-05-20
I'm usually around 62-64 Celsius.

Has anyone tried controlling the fans in userspace?

---

### Post by gensym on 2012-05-21
> **ufrocks said:**
> I'm usually around 62-64 Celsius.

Has anyone tried controlling the fans in userspace?

 Nope... Another weird thing I noticed: The computer shuts down due to overheat every time I "force" matlab to solve some complex equations... Did anyone experience something similiar and/or know a work around?

---

### Post by ufrocks on 2012-05-22
I've had a few unexplained shutdowns myself.  It is probably the same thing.

---

### Post by Ishtumba on 2012-05-23
I'm actually running Mint 12 on mine (sorry, this is the only real active forum for the dell xps13 linux stuff) and the battery life is horrible - less than 3 hours.

The touchpad though is the main area of contention for me as well - makes my Google CR48 still feel like the better device. :/

Good news that Dell is working with Cypress - I hope something comes soon.

---

### Post by bdnewman997 on 2012-05-24
Has anyone tried the Sputnik ISO yet?  I am awaiting the arrival of my xps13 and plan on installing Sputnik.  any suggestions, tips, hints?

-Bryan

---

### Post by tshack on 2012-05-24
Hi everybody!

Excellent thread.  I also can't wait for the touchpad driver to come!

Anyway, here is my input on recent messages:


@gensym:
Interesting regarding your random shutdowns while running Matlab.  For what it is worth, over the last couple of days I have built ITK, Qt, VTK, Slicer4 and an array of other large software packages using make -j 5 (which has pretty much ensured that all 4 cores are incredibly busy for hours).  I have experienced no random shutdowns although the fan has kicked into high gear and the unit is pretty hot.

I am using the "bottom rung" i5 configuration with the 128GB SSD.  Are you experiencing your issues on the i7 configuration or do you also have the i5?

As a side note, I am using the kernel found here:
[https://launchpad.net/~kamalmostafa/+archive/dellxps](https://launchpad.net/~kamalmostafa/+archive/dellxps)

and I am also passing the kernel parameters:
  i915.i915_enable_rc6=1
  i915.i915_enable_fbc=1
  i915.lvds_downclock=1
  pcie_aspm=force

I am on the latest BIOS firmware (A04)


@bdnewman997:
I did try the Sputnik "Demo" ISO (sputnik-iso-20120502-1.iso.bz2), but only after trying to convert it to a USB thumbdrive image.  In short, my advice is to forget it and just do the few extra XPS 13 specific tweaks yourself.

1st Try:
I first tried to go from ISO -> USB using the 10.04 (Lucid's) "Startup Disk Creator."  This failed.  The image would not boot properly.

2nd Try:
I booted up an Oracle VirtualBox 4.1 VM with USB passthrough running Windows XP and followed the directions here:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

This resulted in a USB drive that actually booted.  The option to test the image as a "Live-CD" without installing worked fine, however, you are not given the option to install while in the mode, you have to reboot and select "Install" from the grub boot menu. 

**[COLOR="Red"]**BEWARE**[/COLOR]**
In my experience (using a USB image created as described above in "2nd Try") and selecting the "Install" option started the installer in "OEM Mode," which pretty much means, "Unattended Install, we don't ask you any questions and we hose your current partitioning scheme without asking."  This would have been fine except that the installer (ubiquity) was unable to initialize apt after hosing my partition table and insisted on just exiting and restarting the machine... naturally this resulted in "No Operating System Found."   ...kinda embarrassing for Ubuntu.

So, no problem, I just created a normal Ubuntu 12.04 LTS (Precise) USB installer from the AMD64 iso and everything installed fine.  I then added the following PPAs (as given in the Sputnik documentation):
* [https://launchpad.net/~kamalmostafa/+archive/dellxps](https://launchpad.net/~kamalmostafa/+archive/dellxps)
* [https://launchpad.net/~vanhoof/+archive/policykit-d-p-hibernate-enabled](https://launchpad.net/~vanhoof/+archive/policykit-d-p-hibernate-enabled)

and everything is working find and I couldn't be happier.  Honestly.  I have been using Linux for my desktop OS for nearly 15 years now and I think I am in love with my Dell XPS 13 running Ubuntu.  (...except for the Touchpad). ;)



IMHO, messing with the Sputnik "Demo" ISO is currently more of a headache than it is worth (unless, maybe, you have a USB CD-ROM drive).  Installing plain 12.04 LTS from USB is very simple and straightforward.  Adding the two additional PPAs is also simple and straightforward to get backlight and hibernation working.  My understanding of Sputnik is that other than including these two PPAs it just comes with a different set of default packages aimed towards some generic developer persona... but I'm sure you are more than capable of just installing git or svn or emacs or whatever when you actually need them.

For more details see:
[http://hwe.ubuntu.com/uds-q/dellxps/README.html](http://hwe.ubuntu.com/uds-q/dellxps/README.html)

I think the Sputnik Project is a great idea, and I would love to see Dell sell an Ubuntu branded machine.  I definitely like what is going on between Dell, Ubuntu, and Cypress in terms of getting this touchpad driver straightened out.  However, I don't think the "Demo" ISO is ready quite yet.

---

### Post by ufrocks on 2012-05-24
You made a slight typo.  It's:

i915.i915_enable_fbc=1

Did you use unetbootin to create the USB image?  Also, there's an XPS13 wiki here:

[http://wiki.gentoo.org/wiki/Dell_XPS_13_Ultrabook](http://wiki.gentoo.org/wiki/Dell_XPS_13_Ultrabook)

---

### Post by tshack on 2012-05-24
@ufrocks:
Thanks.  Typo Fixed.  Disaster averted.

No.  The binary for "Startup Disk Creator" on Ubuntu 10.04LTS is provided by "usb-creator-gtk"

As documented in the link I provided, the Windows USB creator used was "Universal USB Installer," which is the Ubuntu prescribed method.

Thanks for the Wiki link.

---

### Post by Njubi on 2012-05-24
Hello there,

I've recently got my Dell XPS 13 Laptop and so far I'm really happy with it. It's running Ubuntu 12.04 and almost all the components have worked out of the box. There are only a few things which don't work yet or that I'm not happy with.

Here's a list with some problems I hope to solve by posting this reply:

1. The brightness adjustment keys don't work yet. I hope that this will get fixed soon so I can control the battery consumption better. Does anybody know something about that particular part? It surprisingly works in BIOS but not in Ubuntu. 

2. The fan still kicks in too often and when it does, it's very noisy. I have also recognized that the air blown out by the fan is quite hot. 
Plus, when I'm charging the laptop and using it at the same time, the keyboard also gets quite hot and it's unpleasant too type with. I've read some posts by people here who seem to have a similar problem. Does anybody know, if that's a commonly known problem with this laptop in particular and if Dell is working on a better BIOS update?
I've got the A03 version installed. I know that there's an A04 version available but Dell lists it for Windows only so I don't think that there is any improvment for a Linux system. Any ideas?

3. I really miss the trackpad multitouch functions. So far it's fine for me but I'm really looking forward to the new driver which I hope is coming soon. 

Everything else is nice and smooth :)

Regards,

Njubi

---

### Post by tshack on 2012-05-24
Hi Njubi,

I use the kernel provided by the PPA:
[https://launchpad.net/~kamalmostafa/+archive/dellxps](https://launchpad.net/~kamalmostafa/+archive/dellxps)

which fixes the brightness adjustment problem.

The installer for the A04 bios is a Windows executable, but installing it will benefit you.

ufrocks has provided a method for doing the update in [Post #82]("http://ubuntuforums.org/showpost.php?p=11847920&postcount=82") in this thread:
[http://ubuntuforums.org/showpost.php?p=11847920&postcount=82](http://ubuntuforums.org/showpost.php?p=11847920&postcount=82)

Touchpad issue is still outstanding, I believe.  However, at the bottom of the Gentoo Wiki link just posted by ufrocks, there is an interesting patch to the mainline kernel provided by Cypress in 2011 (which was for some reason rejected).  I have no had time to look at it yet, but it is indeed, intriguing.

---

### Post by tshack on 2012-05-24
...

---

### Post by Njubi on 2012-05-24
@tshack:

Thank you for your fast response. I'm thinking about the kernel-ppa but I'm not sure about it. I haven't got much experience with that sort of stuff. I'll probably wait a bit longer and come back to your suggestion if Ubuntu doesn't implement it themselves. 

I installed A03 with freeDOS as posted in this thread some days ago and it worked perfectly but I was once told that you should be careful with BIOS updates.
Is the A04 also suitable for Linux? I'm a bit confused because on the official Dell support site they list A03 as the latest BIOS update for "BIOS" which probably means "Not dependent on OS". A04 is only listed under OS Win7. Have you tried A04 it yourself and can you recommend it? 
I just want to play safe, you know ;)

Anyway thank you very much. I'm glad to have people around here, who are competent and who can help me a little.

Regards,

Njubi

---

### Post by tshack on 2012-05-24
Hi Njubi,

I understand if you are uncomfortable.  If you decide to give it a try, then you will have working backlight control.  Otherwise, you can give the fix described in the gentoo wiki a shot (I haven't tried it).  The link was given by ufrocks a few links ago.

I am using A04.  Works great.

---

### Post by bdnewman997 on 2012-05-25
Thanks for the info, I will try the Ubuntu LTS install this weekend (assuming my XPS13 gets delivered).

-Bryan

---

### Post by gensym on 2012-05-25
> **tshack said:**
> 
**[COLOR=Red]**BEWARE**[/COLOR]**
In my experience (using a USB image created as described above in "2nd Try") and selecting the "Install" option started the installer in "OEM Mode," which pretty much means, "Unattended Install, we don't ask you any questions and we hose your current partitioning scheme without asking."  This would have been fine except that the installer (ubiquity) was unable to initialize apt after hosing my partition table and insisted on just exiting and restarting the machine... naturally this resulted in "No Operating System Found."   ...kinda embarrassing for Ubuntu.


I don't know whether it is relevant, but today after deciding to replace the beta installations with clean installs, I managed to get an unbootable system.

When I try booting I get a message saying "Operation System Not Found" (no not operating but operation).
I tried fixing this by reinstalling (didn't work), boot-repair (didn't work), messing with my bios settings (didn't work), trying to reinstall grub (didn't work).

Is there someone out there who had the same problem and knows how to solve it?

Edit: Arghhhh! It was ubiquity not setting the bootable flag for my operating system partitions! Once I set them using cfdisk everything started to work just fine.

---

### Post by bdnewman997 on 2012-05-25
Got my new XPS 13 in earlier today.  I just finished up installing Linux Mint to it.  I like the appearance of Mint over Ubuntu so I went that way.  


I had to make the additions to rc.local and add the script to sleep.d to get the backlight to work.  Remember to set the permission once you get the script.

The trackpad doesn't work, but from everything I have read so far, I would have been surprised if it had.

I don't see the issue with Hibernate yet, but I haven't played much with it as of yet.

All in all very few issues really. The XPS is a nice piece of hardware.

---

### Post by bdnewman997 on 2012-05-25
> >[*]turning off bluetooth via nm turns off wireless

This is controlled in the bios. You can set the switch to control Bluetooth, Wifi, Cellular Card (if you have one) or any combo of the 3.


I don't see any settings for this in the BIOS. anyone else have a fix for the F2 function key turning off all wireless?

---

### Post by tshack on 2012-05-25
Alright you guys getting 5+ hours of battery life...  I'm curious. ;)

As I said before, I am using the kernel from:
[https://launchpad.net/~kamalmostafa/+archive/dellxps](https://launchpad.net/~kamalmostafa/+archive/dellxps)
with kernel parameters I listed a few posts ago.

I am also using Jupiter 0.1.2.  When on battery I use the "Power Saving" governor.


My power statistics for today are approximately:
MIN: 8W
MAX: 15W
AVG: 12W

Given that the battery design capacity is 47.3Wh with an actual capacity of 44.3Wh (for my battery "health" of 93.7%), it then stands that I get about 4 hours of usage on average.  This is more or less true as long as I don't do a lot of compiling.

So, you guys getting the crazy 5+ hours of battery life, what does your power usage look like in watts?  Are you guys somehow actually managing to get between 7W and 8W AVG? :confused:

If so, I wanna see some gnome-power-statistics "rate" screenshots and configuration parameters.
:P

**EDIT:**
I feel it is useful/interesting to mention that under no load, the unit charges at 14W (~3.2hrs).  Under high load, it charges somewhere between 6W to 8W (~7.3 to 5.5hrs).

**EDIT:**
In my search to find the "proper" way to set **/sys/devices/system/cpu/sched_mc_power_savings** to **1**, I installed the package **laptop-mode-tools** and have edited **/etc/laptop-mode/laptop-mode.conf** to disable all hard-drive related power saving optimizations. I have also moved /tmp and ~/.cache/google-chrome/ to tmpfs (ramdisk). My non-scientific testing leads me believe the system is now averaging a Watt or two lower than before. I will update my impressions after a few days of normal use running on battery power.

---

### Post by gensym on 2012-05-26
[[img]http://ompldr.org/tZHhyNw[/img]](http://ompldr.org/vZHhyNw)

---

### Post by tshack on 2012-05-26
Thanks gensym, here is what I am currently getting:

[[img]http://ompldr.org/tZHhzNg[/img]](http://ompldr.org/vZHhzNg)

Installing the **laptop-mode-tools** package seems to have made a HUGE difference for me.

Also, I have determined that the LED backlighting on the keyboard takes 1W on low and 2W on high, which can have a pretty decent impact on battery life.

It seems that your kernel has a less frequent tick_sched_timer than mine, although we seem to be getting similar battery life now that I installed laptop-mode-tools.

Makes me wonder if the "deferrable timers" kernel patch is worth trying:
[http://www.lesswatts.org/projects/tickless/downloads.php](http://www.lesswatts.org/projects/tickless/downloads.php)

---

### Post by gensym on 2012-05-27
> **tshack said:**
> Thanks gensym, here is what I am currently getting:

[[img]http://ompldr.org/tZHhzNg[/img]](http://ompldr.org/vZHhzNg)

Installing the **laptop-mode-tools** package seems to have made a HUGE difference for me.

Also, I have determined that the LED backlighting on the keyboard takes 1W on low and 2W on high, which can have a pretty decent impact on battery life.

It seems that your kernel has a less frequent tick_sched_timer than mine, although we seem to be getting similar battery life now that I installed laptop-mode-tools.

Makes me wonder if the "deferrable timers" kernel patch is worth trying:
[http://www.lesswatts.org/projects/tickless/downloads.php](http://www.lesswatts.org/projects/tickless/downloads.php)

I am using the stock kernel. Gave the dellxps kernel a shot, but I wasn't very satisfied with it.
Would you be kind enough to share your laptop-mode.conf file (preferably through pastebin or sprunge)? Activating it in my machine only makes it consume more power :P

---

### Post by tshack on 2012-05-27
Interesting, perhaps I am merely perceiving better battery life due to my extreme wishful thinking. :p

It is also possible that I am subconsciously changing my usage habits to be more conservative.

Here is my current laptop-mode.conf:
[http://pastebin.com/7qkVrGdv](http://pastebin.com/7qkVrGdv)

I have found that with laptop-mode enabled, "casual usage" such as text editing and surfing the web give better battery life.  I don't feel that I see (or should expect) better battery life when performing processor intensive operations such as compiling, non-"hardware accelerated" video decoding, etc.  This coincides with what I understand the intended behavior of the **sched_mc_power_savings** scheduler parameter to be, however it could also just be a placebo effect for that matter. ;)

I believe that the laptop-mode package also does some TX power management for iwlwifi, but I have not attempted to confirm/quantify any benefit.

Also, I found my high tick_sched_timer event rate was tied to indicator-multiload's default 500ms sampling rate.  Reducing the rate to a sample per every 1 to 2 seconds tames the tick_sched_timer event rate back down to negligible (and still allows me to spot runaway processes). ;)

---

### Post by Njubi on 2012-05-27
@tshack:

I installed the A04 BIOS version successfully today and everything works fine so far. I've got the feeling that the fan runs more silently than before, at least during normal tasks such as reading a pdf-file or similar stuff. The unit still gets warm though. I hope that Dell will be able to fix this or reduce the heat because the warm air also blows out from under the keyboard and it can get quite uncomfortable from time to time (especially when it's charging at the same time). Have you or anyone else noticed the same behavior?

However, things are getting better and that's great :)

Regards,

Njubi

---

### Post by gensym on 2012-05-28
@tshack

Does setting NOATIME 0 in laptop-mode set noatime off for good? If so isn't that bad for your hd?

---

### Post by tshack on 2012-05-28
> **gensym said:**
> @tshack

Does setting NOATIME 0 in laptop-mode set noatime off for good? If so isn't that bad for your hd?

I set noatime manually in fstab.

Setting CONTROL_NOATIME=0 seems to just tell laptop-mode to not control it -- not to remove it from fstab if it is already there.

You can query the kernel for the current mount flags with:
cat /proc/mounts

When on battery power (i.e. laptop mode enabled), here is my output for cat /proc/mounts:

rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1958016k,nr_inodes=489504,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,relatime,size=786720k,mode=755 0 0
**/dev/disk/by-uuid/fd72fe90-7a76-408e-a120-cd3d3c4111b9 / ext4 rw,noatime,errors=remount-ro,user_xattr,barrier=1,data=ordered,discard 0 0**
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
tmpfs /tmp tmpfs rw,noatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /home/tshack/.cache/google-chrome tmpfs rw,noatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/tshack/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0

---

### Post by tshack on 2012-05-28
I ran powertop long enough to get process and device power estimates.

On AC power:
[[img]http://ompldr.org/tZHlvMQ[/img]](http://ompldr.org/vZHlvMQ)

On battery power (laptop-mode enabled):
[[img]http://ompldr.org/tZHo5OQ[/img]](http://ompldr.org/vZHo5OQ)

It seems that
**Audio codec hwC0D0: Realtek**
will draw less power when
**Enable Audio codec power management = Good**
in PowerTop's "Tunables".

This seems to happen automatically on battery power if laptop-mode is enabled or not.  However, laptop-mode does seem to add some intelligent USB power management, according to PowerTOP.

On AC power:
[[img]http://ompldr.org/tZHo5cw[/img]](http://ompldr.org/vZHo5cw)

On battery (ENABLE_LAPTOP_MODE_TOOLS=0):
[[img]http://ompldr.org/tZHo5bw[/img]](http://ompldr.org/vZHo5bw)

On battery (ENABLE_LAPTOP_MODE_TOOLS=1):
[[img]http://ompldr.org/tZHo5cQ[/img]](http://ompldr.org/vZHo5cQ)

and even though I am using laptop-mode's recommended virtual memory write-back settings, PowerTOP still seems them as bad (as shown in the above screen shots).

Also, to set the record strait, I completely removed the laptop-mode-tools package and realized that you get
/sys/devices/system/cpu/sched_mc_power_savings=1
on battery power automatically without the package as well.  (Don't know what my problem was earlier.)  PoweTOP calls this "Power Aware CPU scheduler".

---

### Post by tshack on 2012-05-28
**[COLOR="Red"]_Notice_: This method will not survive a reboot.  I recommend the method in the next post instead: [Found Here]("http://ubuntuforums.org/showpost.php?p=11978187&postcount=131").[/COLOR]**


Alright guys, it isn't much but I found a way to make the mouse a little bit more usable -- mousewheel emulation. :)

_Step 1 - Install GPointing Device Settings_
sudo apt-get install gpointing-device-settings 

_Step 2 - Run it_
gpointing-device-settings

You will get this:
[[img]http://ompldr.org/tZHprYQ[/img]](http://ompldr.org/vZHprYQ)

Checking "Use wheel emulation" and selecting "Button 3" (as shown) will allow you to scroll by swiping your finger on the touchpad while holding down the second mouse button.


_Note:_
If you would rather have middle click X11 style copy-and-paste, you can use these settings instead:
[[img]http://ompldr.org/tZHprZA[/img]](http://ompldr.org/vZHprZA)

For some reason, if both boxes are checked, you will only get scrolling.  Emulated middle click will stop working.

---

### Post by tshack on 2012-05-29
**How to setup mouse wheel emulation that will survive a reboot**

_Step 1_
```
$ sudo mkdir /etc/X11/xorg.conf.d/
```

_Step 2_
```
$ sudo cp /usr/share/X11/xorg.conf.d/10-evdev.conf /etc/X11/xorg.conf.d/
```

_Step 3_
```
$ sudo gedit /etc/X11/xorg.conf.d/10-evdev.conf
```

_Step 4_
Edit the first "InputClass" section to look like this:

```

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
[COLOR="Blue"]        Option      "EmulateWheel"      "true"
        Option      "EmulateWheelButton"    "3"[/COLOR]
EndSection

```

(the 2 Option lines are the new additions)

_Step 5_
Restart X11 (or your entire computer)

_Step 6_
Enjoy scrolling by holding right click and swiping.

_**To undo:**_
```
$ sudo rm /etc/X11/xorg.conf.d/10-evdev.conf 
```

---

### Post by mooselander on 2012-05-29
> **tshack said:**
> **How to setup mouse wheel emulation that will survive a reboot**


Thanks! The trackpad was starting to remind me of 2003 again.  

Until a proper cypress driver becomes available, your workaround is refreshing.

---

### Post by bekirserifoglu on 2012-05-29
> **tshack said:**
> **[COLOR="Red"]_Notice_: This method will not survive a reboot.  I recommend the method in the next post instead: [Found Here]("http://ubuntuforums.org/showpost.php?p=11978187&postcount=131").[/COLOR]**


Alright guys, it isn't much but I found a way to make the mouse a little bit more usable -- mousewheel emulation. :)

_Step 1 - Install GPointing Device Settings_
sudo apt-get install gpointing-device-settings 

_Step 2 - Run it_
gpointing-device-settings

You will get this:
[[img]http://ompldr.org/tZHprYQ[/img]](http://ompldr.org/vZHprYQ)

Checking "Use wheel emulation" and selecting "Button 3" (as shown) will allow you to scroll by swiping your finger on the touchpad while holding down the second mouse button.


_Note:_
If you would rather have middle click X11 style copy-and-paste, you can use these settings instead:
[[img]http://ompldr.org/tZHprZA[/img]](http://ompldr.org/vZHprZA)

For some reason, if both boxes are checked, you will only get scrolling.  Emulated middle click will stop working.

Oh god! Thank you very very much for this workaround. It'll be of great use until a real driver is here.

---

### Post by tshack on 2012-05-29
**Palm Rejection Service - Experimental**

I have managed to put together a hack for disabling the mouse when using the keyboard. Let's call it experimental for now, although it works just fine for me (no problems yet).

It is a system service that directly reads the keyboard event device, which I assume it is the same for you all as it is for me:
**/dev/input/event4**
(if not, the service is a bash script, so feel free to edit it).

When keyboard activity is detected, the mouse is disabled -- when the keyboard activity stops, the mouse is re-enabled.  Keyboard activity is checked for every 1 second.

Unfortunately, [COLOR="Blue"]the minimum delay I could manage was 1 second[/COLOR] -- this is due to a limitation of the bash "read" command, sorry guys.

Perhaps I can whip up something better in C if I can find the time.


**Instructions**

_Step 1_
Copy the script into your /etc/init.d/ directory
```
$ sudo cp ~/Downloads/xps_touch_man.sh /etc/init.d/
```

_Step 2_
Remove the .sh extension (ubuntuforums.org required it, sorry)
```
$ sudo mv /etc/init.d/xps_touch_man.sh /etc/init.d/xps_touch_man
```

_Step 3_
Make the script executable
```
$ sudo chmod 755 /etc/init.d/xps_touch_man
```

_Step 4_
The root user will need to be able to access your Xsession. So, with the user you normally login as, run the following command:
```
$ xhost SI:localuser:root
```

_Step 5_
Start the service:
```
$ sudo service xps_touch_man start
```


If all went well, you will now have some form of touchpad protection when typing.  Like I said earlier, it takes 1 second for the touchpad to come back on, so it can be a little annoying (depending on what you are doing).  Again, this is a limitation of bash and I apologize.  Help regarding this issue is appreciated.

Personally, I recommend just starting the service if you have a lot of typing to do and then stopping the service when you are done.

As you may have guessed, stopping the service is just as easy as starting it:
```
$ sudo service xps_touch_man stop
```

_**Notes**_
[1] Keyboard polling delay is 1 second

[2] Assumes keyboard on /dev/input/event4

[3] The service generates a log file in /var/log/xps_touch_man.log

[4] The service generates an error log in /var/log/xps_touch_man.err

[5] Step 4 and Step 5 will have to be repeated if/when you reboot to re-enable the palm rejection. (See [next post]("http://ubuntuforums.org/showpost.php?p=11978814&postcount=135"))

:guitar:

---

### Post by tshack on 2012-05-29
Here is how I have set myself up to use the xps_touch_man service.

I appended the following to the end of my ~/.profile
```
xhost SI:localuser:root
```

which will automatically give the root user permission to access your Xsession when you login.


Then I use the attached script to simply toggle the palm rejection when I need it / don't need it / find it annoying:

```
xps_touch_toggle.sh
```

**[COLOR="Red"]If you guys from Dell, Ubuntu, or Cypress are reading this.  I would love to see a real driver!  Nothing would make me happier than to scrap all this and enjoy some multi-touch![/COLOR]**
:lolflag:

---

### Post by tshack on 2012-05-29
> **mooselander said:**
> Thanks! The trackpad was starting to remind me of 2003 again.  

Until a proper cypress driver becomes available, your workaround is refreshing.


> **bekirserifoglu said:**
> Oh god! Thank you very very much for this workaround. It'll be of great use until a real driver is here.

Happy to help. :p

And thank you two for taking the time to reply!  Your responses are very much appreciated!

---

### Post by tshack on 2012-05-29
**How to automatically turn off Bluetooth upon login**

I nearly forgot.  The other day I grew tired of manually turning off Bluetooth everytime I logged into my laptop.  I hardly ever use it.

Adding the following to the bottom of your ~/.profile will do the trick:
```
rfkill block bluetooth
```

You will still have the bluetooth icon at the top of your screen and you will still be able to toggle the bluetooth radio on/off via the icon just as before.  Only difference is that it won't be on by default when you login.

**Additional (potential) fix for WiFi**
Once I rebooted my machine and wifi refused to come back up.  The following finally did the trick:
```
rfkill unblock wifi
```

Consequently, I have also appended this to by ~/.profile just to be safe. Couldn't hurt.

---

### Post by tshack on 2012-05-30
Some good news. :p

Barton George, of project Sputnik, hopes to receive a "completed" Touchpad driver from Cypress by the end of June:

[http://bartongeorge.net/2012/05/29/sputnik-wow/](http://bartongeorge.net/2012/05/29/sputnik-wow/)

---

### Post by gensym on 2012-06-01
I have been playing with boot parameters lately... I have noticed that booting with the parameter noapic does give me a smoother experience (which is weird though).

---

### Post by naex on 2012-06-03
> Unfortunately, the minimum delay I could manage was 1 second -- this is due to a limitation of the bash "read" command, sorry guys.

According to "help read", arguments to the -t parameter can be fractional. An argument of "0.1" seems to work.

---

### Post by tshack on 2012-06-04
> **naex said:**
> According to "help read", arguments to the -t parameter can be fractional. An argument of "0.1" seems to work.

Hmmm, thanks for the tip.  For some reason I don't remember it working for me... oh well, perhaps I was just being crazy! ;)

Anyway, are you getting good results?  Have you found the "sweet spot" for -t ?

---

### Post by naex on 2012-06-04
> Anyway, are you getting good results? Have you found the "sweet spot" for -t ?

Not yet. I spent about 30 minutes working on a Python solution when I decided to try fractional -t (because time.sleep(seconds) accepts floats) and then immediately left once I made the post. I'll experiment over the next couple of days and see what I find.

I did notice that 0.3-0.5 seconds still seemed annoyingly long. So far 0.1 seems to be fairly good but I must admit that I am at least slightly intoxicated...

Just in case, here's the output of "bash --version":

```
GNU bash, version 4.2.24(1)-release (x86_64-pc-linux-gnu)
```

---

### Post by naex on 2012-06-04
I had to do one more thing to make the touchpad script work properly. It was failing to work after a suspend/resume. It looks like /dev/input/event4 was vanishing during suspend causing cat to die.

In order to fix this, I added a couple of lines to my /etc/pm.d/sleep/10_dell_xps_ultrabook script. I still had it around since before we had the Dell kernel. Here's what it looks like:

```


#!/bin/sh
case "${1}" in
    resume|thaw)
        /etc/scripts/brightness.sh

        DISPLAY=":0" su naex -c "xhost SI:localuser:root"
        /etc/init.d/xps_touch_man restart
        ;;
esac

```

---

### Post by svenole on 2012-06-06
I've run the DELL XPS 13 ultrabook with ubuntu 12.04 for some time now. At some stage I added a Kensington Universal Docking Station with VGA/DVI/HDMI/and ethernet to it. I've not even started to try to get the display part of this replicator to work. It seems to me that the DisplayLink support in Linux generally is shabby. However I've used the USB ports for eksternal mouse and keyboard without trouble. 

The real trouble is the ethernet port. It seems like running this ethernet port in the port replicator through the USB interconnect, works well for some minutes. But after say 6 - 7 minutes, this ethernet port dies, comes back again, dies, comes back again, etc etc. 

Now, I am not very familiar with the protocol and driver that does the underlying communication with the different hardware components (USB ports, DVI/VGA/HDMI and ethenret), but I suspect the whole thing is implementaed in the DisplayLink driver (?). If this is so, there obviously must be something wrong with this driver under 12.04 and I just wanted to check if somebody out there have experienced the same problem and have found a solution  or work around... ?

---

### Post by emagar on 2012-06-06
12.04 is out. Any updates on battery life?

---

### Post by tshack on 2012-06-08
12.04 has been out for a while now (since April 26th).

All these posts refer battery life on 12.04:
[#121]("http://ubuntuforums.org/showpost.php?p=11968959&postcount=121")
[#122]("http://ubuntuforums.org/showpost.php?p=11972039&postcount=122")
[#123]("http://ubuntuforums.org/showpost.php?p=11972180&postcount=123")
[#124]("http://ubuntuforums.org/showpost.php?p=11972940&postcount=124")
[#125]("http://ubuntuforums.org/showpost.php?p=11973922&postcount=125")
[#129]("http://ubuntuforums.org/showpost.php?p=11976494&postcount=129")

---

### Post by psypher on 2012-06-13
> **tshack said:**
> **How to setup mouse wheel emulation that will survive a reboot**

_Step 1_
```
$ sudo mkdir /etc/X11/xorg.conf.d/
```

_Step 2_
```
$ sudo cp /usr/share/X11/xorg.conf.d/10-evdev.conf /etc/X11/xorg.conf.d/
```

_Step 3_
```
$ sudo gedit /etc/X11/xorg.conf.d/10-evdev.conf
```

_Step 4_
Edit the first "InputClass" section to look like this:

```

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
[COLOR="Blue"]        Option      "EmulateWheel"      "true"
        Option      "EmulateWheelButton"    "3"[/COLOR]
EndSection

```

(the 2 Option lines are the new additions)

_Step 5_
Restart X11 (or your entire computer)

_Step 6_
Enjoy scrolling by holding right click and swiping.

_**To undo:**_
```
$ sudo rm /etc/X11/xorg.conf.d/10-evdev.conf 
```


Hi. I would prefer having middle mouse click to paste. What do I set in the 10-evdev.conf to enable that part and not the scroll?

---

### Post by tshack on 2012-06-13
> **psypher said:**
> Hi. I would prefer having middle mouse click to paste. What do I set in the 10-evdev.conf to enable that part and not the scroll?

Hi psypher!

The man page for the evdev driver lists the available options:
[http://www.x.org/archive/X11R7.5/doc/man/man4/evdev.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/evdev.4.html)

You should be able to set:

```
Option "Emulate3Buttons"     "True"
```

to achieve the desired result.

You may also want to experiment with the [FONT="Courier New"]Emulate3Timeout[/FONT] option as well (to tune the behavior to your liking).

Cheers! :D

---

### Post by psypher on 2012-06-14
> **tshack said:**
> Hi psypher!

The man page for the evdev driver lists the available options:
[http://www.x.org/archive/X11R7.5/doc/man/man4/evdev.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/evdev.4.html)

You should be able to set:

```
Option "Emulate3Buttons"     "True"
```

to achieve the desired result.

You may also want to experiment with the [FONT="Courier New"]Emulate3Timeout[/FONT] option as well (to tune the behavior to your liking).

Update:
Nope, added those 2 commands and hashed out the wheel emulate and does not paste using middle mouse. If I go into gpointer app and unselect and reselect it then it works. Weird

Cheers! :D

Thanks.I did just add ```
Option "Emulate3Buttons"     "True"
``` but that didn't work. I can see the setting set in the gpointer app but it doesn't work. Will try again later.

Has anyone tried using a mobile broadband 3G USB dongle? I plugged one in yesterday and despite listing in lsusb, it does not become available in the network indicator to create a BB connection. This is with the Sputnik image. USB dongle worked fine on my Dell L701x with 12.04, not Sputnik image on there.


Update:

Adding the above lines and removing the wheel emulate lines does not work. if I use the gpointer app and uncheck and check the option again, then it works. Until next boot

---

### Post by luor_d on 2012-06-17
> **ufrocks said:**
> Does anyone know if the BIOS update should be installed to a machine with the i5 proc or if it's just for i7?

Both are OK. You can update A04 BIOS for XPS 13 now.

---

### Post by luor_d on 2012-06-17
I am also using a Dell U2410 display and resolution is 1920X1200.
Using a mini-DP to VGA cable, my Dell XPS 13 output video to this U2410 only get 1024X768 resolution. How to solve this problem?

---

### Post by luor_d on 2012-06-18
I am from Dell China and I think this thread is very helpful.
[Kamal Mostafa PPA]("https://launchpad.net/~kamalmostafa/+archive/dellxps") fixed display brightness control key issue. I love such easy way.
For battery usage. Here is my data.
Power on at 10:00am, run firefox, ubuntu one, download about 60MB patches and update. Reboot at 11:35am, Stay at blank desktop till 1:30pm. Then run firefox and chromium, play web radio music at low volume till 3:15pm. Then battery status is red. It is quite acceptable for me.

---

### Post by mediamind on 2012-06-20
Hi Everyone,

I just installed a stock version of Ubuntu 12.04 64-bit on my XPS 13 Ultrabook running BIOS A04. Almost everything works out of the box outside of the screen brightness keys and multitouch. Re the latter, **[according to Barton George]("http://bartongeorge.net/2012/06/18/sputnik-update-profile-tool-and-touchpad/")** of **[Project Sputnik]("http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/")**, we should see an updated touchpad driver very soon. 

> Probably the area we’ve gotten the most amount of inquiries into is the status of the driver being written for the touchpad to allow multi-touch support.  Last week Dell and Canonical received two code drops from the vendor and they are looking very good.  Its only a matter of time now before we have driver in the XPS enablement PPA.  Stay tuned.


To fix Screen Brightness, I added **[Kamal Mostoafa's kernel PPA]("https://launchpad.net/~kamalmostafa/+archive/dellxps")**:

```
sudo apt-add-repository ppa:kamalmostafa/dellxps
sudo apt-get update
sudo apt-get upgrade

```

I also disabled bluetooth at boot (to save a little battery life) by adding the rfkill command to my rc.local file:
```
sudo nano /etc/rc.local

```

Add the following line (above the "exit 0" line):
```
rfkill block bluetooth

```

---

### Post by psypher on 2012-06-20
> **mediamind said:**
> Hi Everyone,

I just installed a stock version of Ubuntu 12.04 64-bit on my XPS 13 Ultrabook running BIOS A04. Almost everything works out of the box outside of the screen brightness keys and multitouch. Re the latter, **[according to Barton George]("http://bartongeorge.net/2012/06/18/sputnik-update-profile-tool-and-touchpad/")** of **[Project Sputnik]("http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/")**, we should see an updated touchpad driver very soon. 



To fix Screen Brightness, I added **[Kamal Mostoafa's kernel PPA]("https://launchpad.net/~kamalmostafa/+archive/dellxps")**:

```
sudo apt-add-repository ppa:kamalmostafa/dellxps
sudo apt-get update
sudo apt-get upgrade

```

I also disabled bluetooth at boot (to save a little battery life) by adding the rfkill command to my rc.local file:
```
sudo nano /etc/rc.local

```

Add the following line (above the "exit 0" line):
```
rfkill block bluetooth

```


I recommend adding "rfkill unblock wifi" else my wifi does not work.

Also just re-installed mine with stock 12.04 64bit instead of the sputnik image to see if the issue with mobile broadband is fixed. It didn't fix it. Still does not detect the 3g dongle despite lsub picking it up and apport pops up saying that modem-manager failed. This does not occur on my Dell L701x with same version of Ubuntu.

Can anyone else try a 3g dongle and see if it works? I cannot log a bug when apport pops up as for some reason it no longer allows you to log a bug. No reason as to why, I suspect it's been disabled by Canonical which I think is silly as there any many bugs I would like to log about 12.04.

Oh just want to add to anyone looking at buying this laptop for Ubuntu.
It's....
Just....
AWESOME!!!

Probably just the SSD making it runs so damn fast, but yeah, really impressed with the whole desktop. EVEN HIBERNATE AND SUSPEND WORKS!!! Well hasn't failed yet. First linux PC I have ever used where hibernate worked properly. No doubt thanks to these 2 PPA's:

* [https://launchpad.net/~kamalmostafa/+archive/dellxps](https://launchpad.net/~kamalmostafa/+archive/dellxps)
* [https://launchpad.net/~vanhoof/+archive/policykit-d-p-hibernate-enabled](https://launchpad.net/~vanhoof/+archive/policykit-d-p-hibernate-enabled)

Waiting patiently for the trackpad driver :)

---

### Post by newcolour78 on 2012-06-21
A trackpad driver has been released and it is available in the new kernel by Kamal.

However it does not work for me. I don't see any difference between before and after the kernel update. As far as I understand (and I hope I am wrong...) it should work out-of-the-box with the new kernel, which means that some people are still out of luck. 

Some other people (see the bug report) are experiencing more major issues, like touchpad not working at all.

Anyway, worth trying. Hopefully in a few days there will be a more stable version available.

S.

---

### Post by psypher on 2012-06-21
> **newcolour78 said:**
> A trackpad driver has been released and it is available in the new kernel by Kamal.

However it does not work for me. I don't see any difference between before and after the kernel update. As far as I understand (and I hope I am wrong...) it should work out-of-the-box with the new kernel, which means that some people are still out of luck. 

Some other people (see the bug report) are experiencing more major issues, like touchpad not working at all.

Anyway, worth trying. Hopefully in a few days there will be a more stable version available.

S.

getting there. If you created the /etc/X11/xorg.conf.d/10-evdev.conf file as described earlier in the forum to make scrolling work, delete it and reboot. Got some features working now. Check the latest on the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/978807](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/978807)



UPDATE: 2 finger scrolling is actually working. had to actiavte in mouse settings, touchpad tab. Just pinch and zoom not working now but thats a minor

---

### Post by tshack on 2012-06-21
> **psypher said:**
> getting there. If you created the /etc/X11/xorg.conf.d/10-evdev.conf file as described earlier in the forum to make scrolling work, delete it and reboot. Got some features working now. Check the latest on the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/978807](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/978807)



UPDATE: 2 finger scrolling is actually working. had to actiavte in mouse settings, touchpad tab. Just pinch and zoom not working now but thats a minor

I can confirm.

Kernel 3.2.0-26 from Kamal Mostafa's PPA has working multi-touch scrolling.

Like psypher said, don't forget to enable "Two-finger Scrolling" in "Mouse and Touchpad Settings."  Otherwise, you will get edge scrolling by default, which some may prefer.

**Edit:** At first I thought that the 2-finger scrolling sensitivity was frustratingly low. Then I realized that it works much better if you "flick" with two fingers...

---

### Post by gensym on 2012-06-21
After installing the 3.2.0-26 from Kamal Mostafa's PPA,  I have an obscene amount of CPU acitivity (and loud fans et al.).
Is it just me? Can someone confirm this?
Edit: Hm weird, after deleting the evdev configuration file CPU activity returned to normal [though I still am having a hard time to correlate between the two]. The new kernel fixed the multitouch issue, but the touchpad feels painfully choppy now, and for some reason the laptop feels much more warmer now.

---

### Post by bekirserifoglu on 2012-06-21
The new touchpad driver is certainly good progress but scrolling and double tap still have some way to go. Another problem with the driver is that movement with the cursor seems to feel a bit choppy.

---

### Post by tshack on 2012-06-21
> **bekirserifoglu said:**
> ...movement with the cursor seems to feel a bit choppy.

I am also getting this at times.

Also, I am sometimes getting "right-clicks" without pushing the right mouse button -- I don't believe there is a gesture for right-click ...or is there? :rolleyes:

(Usually happens when using 2-finger scrolling).

Also, has anybody else noticed that 3-finger tap gives temporary handles for more easily moving and resizing windows? 8)

[[img]http://ompldr.org/tZWZqaw[/img]](http://ompldr.org/vZWZqaw)

**Edit:** Here are the gestures supported by Unity:
[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

---

### Post by Mr. Picklesworth on 2012-06-21
> **tshack said:**
> I am also getting this at times.

Also, I am sometimes getting "right-clicks" without pushing the right mouse button -- I don't believe there is a gesture for right-click ...or is there? :rolleyes:

(Usually happens when using 2-finger scrolling).

Also, has anybody else noticed that 3-finger tap gives temporary handles for more easily moving and resizing windows? 8)

[[img]http://ompldr.org/tZWZqaw[/img]](http://ompldr.org/vZWZqaw)

**Edit:** Here are the gestures supported by Unity:
[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

A two finger click (or tap) right clicks, so could that be what you're doing?

It's really exciting to see actual touchpad gestures reaching as far as the window manager!
The three finger gestures are a little tricky, though. I suspect there may just be too many of them, so I end up triggering the wrong ones sometimes. Three finger pinch definitely seems to be misbehaving,. Dragging three fingers _up_ will maximize a window (not really a pinching motion), but I can't find a similar gesture to unmaximize.

I had the clunky pointer movement as well, but it got better when I adjusted sensitivity / acceleration in system settings. The defaults weren't working for me, and I suspect the ugly feeling could have just stemmed from that.

---

### Post by D43m0n on 2012-06-22
Has anyone tried a USB 3.0 port replicator? Like the [Targus USB 3.0 Docking Station]("http://www.targus.com/us/productdetail.aspx?regionId=7&sku=ACP70USZ&PageName=Docking%20Stations%20by%20Targus&productCategoryId=13&bucketTypeId=0&searchedTerms=&navlevel1=products&cp=&bannertxt=Docking%20Stations") or the [Lenovo USB 3.0 Dock]("http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:item.detail?GroupID=460&Code=0A33970")?

Does it work at all? Any experience is welcome!

---

### Post by psypher on 2012-06-22
> **tshack said:**
> I am also getting this at times.

Also, I am sometimes getting "right-clicks" without pushing the right mouse button -- I don't believe there is a gesture for right-click ...or is there? :rolleyes:

(Usually happens when using 2-finger scrolling).

Also, has anybody else noticed that 3-finger tap gives temporary handles for more easily moving and resizing windows? 8)

[[img]http://ompldr.org/tZWZqaw[/img]](http://ompldr.org/vZWZqaw)

**Edit:** Here are the gestures supported by Unity:
[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)


i don't seem to get it right to actually do anything once the grab handles appear. Also four finger dash open works.

But it all seems a bit clunky, doesn't always work. maybe cos I'm just not used to the mutitouch gesture stuff. I just use scroll, paste and click. I use alt left click  and hold for drag and alt middle click to resize apps.

---

### Post by tshack on 2012-06-22
> **Mr. Picklesworth said:**
> A two finger click (or tap) right clicks, so could that be what you're doing?


Thanks, I figured out the 2-finger tap.  But, it seems I was having problems due to a hardware issue with the touchpad where **the bottom right corner on the touchpad becomes unresponsive**.  I am curious to see if anybody else experiences this, so I am bolding it :KS

I am not sure what causes the corner to go dead, but it has happened to me about 3 times (2 when still using the evdev driver).  The dead corner survives soft reboots.  Only completely powering down the machine brings the corner back to life.

Needless to say, this confuses the gesture recognition and was giving me choppy performance...

Anybody else seeing this?  Particularly people who use suspend or who otherwise have long system uptimes?



> **psypher said:**
> i don't seem to get it right to actually do anything once the grab handles appear. Also four finger dash open works.

It took me a bit of time to figure it out because I discovered the feature in fullscreen Chrome, where it doesn't really do much.  I found that once you 3-tap you can then grab the handles with a normal click to resize and move.  You can also try to do a 3-drag to move the window around, but the Cypress driver seems to have buggy 3-drag at the moment.

---

### Post by KananYan on 2012-06-23
> **mediamind said:**
> Hi Everyone,

I just installed a stock version of Ubuntu 12.04 64-bit on my XPS 13 Ultrabook running BIOS A04. Almost everything works out of the box outside of the screen brightness keys and multitouch. Re the latter, **[according to Barton George]("http://bartongeorge.net/2012/06/18/sputnik-update-profile-tool-and-touchpad/")** of **[Project Sputnik]("http://bartongeorge.net/2012/05/07/introducing-project-sputnik-developer-laptop/")**, we should see an updated touchpad driver very soon. 



To fix Screen Brightness, I added **[Kamal Mostoafa's kernel PPA]("https://launchpad.net/~kamalmostafa/+archive/dellxps")**:

```
sudo apt-add-repository ppa:kamalmostafa/dellxps
sudo apt-get update
sudo apt-get upgrade

```

I also disabled bluetooth at boot (to save a little battery life) by adding the rfkill command to my rc.local file:
```
sudo nano /etc/rc.local

```

Add the following line (above the "exit 0" line):
```
rfkill block bluetooth

```

Hi,

I'm updated the system and than reboot.
but the mouse can nat to move......

---

### Post by CyclounsJ on 2012-06-24
I am using these PPAs on my XPS 13.

* [https://launchpad.net/~kamalmostafa/+archive/dellxps](https://launchpad.net/~kamalmostafa/+archive/dellxps)
 * [https://launchpad.net/~vanhoof/+archive/policykit-d-p-hibernate-enabled](https://launchpad.net/~vanhoof/+archive/policykit-d-p-hibernate-enabled)

Brightness, touchpad and the hibernation all work great. But the problem is the wireless network when connecting to WAP2 Enterprise.

When I am running live CD of 11.04, the WAP2 Enterprise wireless works great.

Anybody is seeing the same issue?

---

### Post by tshack on 2012-06-24
> **CyclounsJ said:**
> 
...the problem is the wireless network when connecting to WAP2 Enterprise.

When I am running live CD of 11.04, the WAP2 Enterprise wireless works great.

Anybody is seeing the same issue?

I have this also.  Where I work uses a WPA2 enterprise configuration, so I have to resort to using the guest network and then SSHing or VPNing back... very frustrating.

There is a bug in launchpad for this issue.  It is not specific to the XPS, but Ubuntu 12.04 in general:
[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/971753]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/971753")

the problem seems to be with the version of openssl that Precise builds wpasupplicant against:
[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343)

some people have reported success by rolling back their version of openssl, but I haven't had time to try it since I can only troubleshoot it at work. #-o

---

### Post by thaletterb on 2012-06-27
In case anybody was noticing intermittent issues with the Cypress trackpad driver, there's a new kernel at the Project Sputnik PPA.  

sudo apt-add-repository ppa:kamalmostafa/dellxps 
sudo apt-get update 
sudo apt-get upgrade

Should fix any issues on either 32 bit or 64 bit builds related to the system having trouble recognizing the touchpad as the new CyPS/2 Cypress Touchpad after upgrading.

---

### Post by CyclounsJ on 2012-06-28
> **tshack said:**
> I have this also.  Where I work uses a WPA2 enterprise configuration, so I have to resort to using the guest network and then SSHing or VPNing back... very frustrating.

There is a bug in launchpad for this issue.  It is not specific to the XPS, but Ubuntu 12.04 in general:
[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/971753](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/971753)

the problem seems to be with the version of openssl that Precise builds wpasupplicant against:
[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343)

some people have reported success by rolling back their version of openssl, but I haven't had time to try it since I can only troubleshoot it at work. #-o

It looks like this is not same issue. So I just file a new bug here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019081)

Please vote for it if you are seeing the same issue, so we can get some attention to get this fixed.

---

### Post by gensym on 2012-06-29
> **CyclounsJ said:**
> It looks like this is not same issue. So I just file a new bug here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019081)

Please vote for it if you are seeing the same issue, so we can get some attention to get this fixed.

At the uni I am connecting to a WPA2 Enterprise Network (Authentication: PEAP, Inner authentication: MSCHAPv2) with no problems. What sort of authentication mechanisms are you dealing with?

PS: I am booting with the noapic option, and I turn the wirless power management off at boot (/sbin/iwconfig wlan0 power off).

---

### Post by CyclounsJ on 2012-06-29
> **gensym said:**
> At the uni I am connecting to a WPA2 Enterprise Network (Authentication: PEAP, Inner authentication: MSCHAPv2) with no problems. What sort of authentication mechanisms are you dealing with?

PS: I am booting with the noapic option, and I turn the wirless power management off at boot (/sbin/iwconfig wlan0 power off).

Could you show me your "uname -a" output?

Here is what I have, I will turn off noapic and disable wireless power management.

Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'ssid' value 'wireless2' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'scan_ssid' value '1' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'key_mgmt' value 'WPA-EAP' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'password' value '<omitted>' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'eap' value 'PEAP' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'fragment_size' value '1300'
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'phase2' value 'auth=MSCHAPV2' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'identity' value 'cjia' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'bgscan' value 'simple:30:-45:300' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.

---

### Post by CyclounsJ on 2012-06-29
> **CyclounsJ said:**
> Could you show me your "uname -a" output?

Here is what I have, I will turn off noapic and disable wireless power management.

Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'ssid' value 'wireless2' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'scan_ssid' value '1' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'key_mgmt' value 'WPA-EAP' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'password' value '<omitted>' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'eap' value 'PEAP' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'fragment_size' value '1300'
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'phase2' value 'auth=MSCHAPV2' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'identity' value 'cjia' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Config: added 'bgscan' value 'simple:30:-45:300' 
Jun 28 16:33:36 cjia-xps NetworkManager[763]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.

Using the v3.5-rc4-quantal kernel fixed my problem, I am asking help to back port upstream kernel fix to [https://launchpad.net/~kamalmostafa/+archive/dellxps](https://launchpad.net/~kamalmostafa/+archive/dellxps).

---

### Post by CyclounsJ on 2012-06-29
> **CyclounsJ said:**
> Using the v3.5-rc4-quantal kernel fixed my problem, I am asking help to back port upstream kernel fix to [https://launchpad.net/~kamalmostafa/+archive/dellxps]("https://launchpad.net/%7Ekamalmostafa/+archive/dellxps").

OK, now it is more strange, after getting my wireless working with v3.5-rc4 kernel, my wireless continues working even switching back to the kamal's PPA kernel. :-)

---

### Post by emagar on 2012-07-04
> **Rob F said:**
> I did AOs 1 through 3 from windows and then nuked it to install ubuntu 12.04. I've been using it on this machine for ~3 weeks now... and I'm now getting 5+ hr battery life (seems to have got better with time). 

How did you manage to get such battery life? I get 2+ hours at most running 12.04 on xps 13 (i5) with low brightness control and little CPU demand. 

What needs to be twisted to improve battery life?

Thanks in advance for suggestions.

---

### Post by opensas on 2012-07-20
I've added the ppa and updated the system. Now the pad and the bright button work fine.

I'm currently running the following kernel>
uname -a
Linux ubuntu 3.2.0-26-generic #41+kamal4~DellXPS-Ubuntu SMP Tue Jun 26 19:18:20 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

But I have the linux kernel version 3.2.0-27 waiting to be upgraded

I guess that if I issue a sudo apt-get dist-upgrade

I will loose all the enhancements of the kamal kernel...

So I have to stick with the kamal ppa, until those changes are integrated into the official kenerl..

Am I right?

saludos

sas

---

### Post by Rob F on 2012-07-22
Morning all,

Have 12.04 running fine on this laptop, but noticed in recent weeks that I've got the old brightness control problem again, having to manually run the script rather than it 'just working' as it had been for the last month.. bit odd. Is this due to some updates - did anyone else experience this? Also I haven't checked this forum for a while but it seems that the trackpad is still not solved - personally the thing I miss the most is tap-to-click..

Also, is it still the consensus that vanilla 12.04 + tweaks is as good, if not better, than trying the project sputnik ISO?

ta

R

---

### Post by emagar on 2012-07-22
> **Rob F said:**
> Also I haven't checked this forum for a while but it seems that the trackpad is still not solved - personally the thing I miss the most is tap-to-click..


Sputnik claims that trackpad issue is solved. Check 2nd link here: [http://ubuntuforums.org/showthread.php?t=2029216](http://ubuntuforums.org/showthread.php?t=2029216)

I personally don't use the trackpad, but still would like to hear if this has solved the issue. 

Good luck.

---

### Post by gensym on 2012-07-24
> **Rob F said:**
> Morning all,
<snip>
Also, is it still the consensus that vanilla 12.04 + tweaks is as good, if not better, than trying the project sputnik ISO?
</snip>


I would like to know that as well.
Also: How does sputnik exactly differentiate from Ubuntu aside from the extra packages and the different kernel? Would I still be able to update to 12.10 when the time comes, regardless of the direction the sputnik people decide to take?

---

### Post by gensym on 2012-08-04
A quick update,

The sputnik iso seems very stable. Disabling the rc6 option seems like a good thing to do. Now that I disabled it, the computer works more quietly.

---

### Post by Rob F on 2012-08-17
So, gensym, you had to install from scratch to test the sputnik iso right?
I don't think I want to do that right now - my laptop is loaded up with loads of extra software, a lot of which isn't from the USC. 

Getting really annoyed at the auto-backlight thing not working anymore though..

Have you found anywhere else where they're discussing Ubuntu on this laptop - this thread seems to be dead/dying.

ta,

R

---

### Post by paterijk on 2012-09-24
Hi, 

I'm planning to buy an XPS13 from Dell and install Ubuntu on it. I would also like to buy a dock, and the Dell site suggests the Kensington SD400 Dock for that ([snip[](snip[)). It says that it "universally" supports all laptops with USB ... but ... well.

I was wondering if anybody has some compatibility issues with Ubuntu and this dock ? Especially for the video part and the ethernet part, because I would like to use an external monitor and plug an ethernet cable in it. 

Thank you for any hints, 

Patrick

---

### Post by garak on 2012-09-24
> **paterijk said:**
> Hi, 

I'm planning to buy an XPS13 from Dell and install Ubuntu on it. I would also like to buy a dock, and the Dell site suggests the Kensington SD400 Dock for that ([http://accessories.euro.dell.com/sna...gen&sku=627297](http://accessories.euro.dell.com/sna...gen&sku=627297)). It says that it "universally" supports all laptops with USB ... but ... well.

I was wondering if anybody has some compatibility issues with Ubuntu and this dock ? Especially for the video part and the ethernet part, because I would like to use an external monitor and plug an ethernet cable in it. 

Thank you for any hints, 

Patrick

My personal dock is just like this:

- a mini-display adapter with DVI (of course, you can use a VGA one)
- a 4-ports USB hub with mouse and keywbord plugged
- an ethernet cable with USB adapter

the first two on right side, the third on left side.

Nothing more :)

---

### Post by paterijk on 2012-09-25
> **garak said:**
> My personal dock is just like this:

- a mini-display adapter with DVI (of course, you can use a VGA one)
- a 4-ports USB hub with mouse and keywbord plugged
- an ethernet cable with USB adapter

the first two on right side, the third on left side.

Nothing more :)

Thx for the advice.

---

### Post by acruxksa on 2012-09-27
Just wanted to say that I'm pretty happy with my xps 13 ultra book running Ubuntu 12.04 desktop amd64 with dells project Sputnik PPA updates.  There are some refinements that can be made, but generally it was a painless install and everything is working.  

The touch pad could use some tweaking but is completely usable in my opinion.

The brightness issue is gone with kamal's kernel from project Sputnik.  

Battery life seems great as well, but is hard to pin down due to battery times fluctuating depending on how heavily you use your system.  In general I would guess I'm seeing at least 5 hrs and probably closer to 6hrs with normal Internet surfing and network usage.

I'm using the 5ghz band for wireless and sometimes it takes 30 or 40 seconds to reconnect after waking from suspend, but that's truly not a big deal.

I'm currently troubleshooting a wake from suspend ata1 com error, but suspect its because I'm using a non stock 256gb crucial m4 ssd rather than the 128gb Samsung ssd included with the xps 13.  The error doesn't prevent wake from suspend, but does seem to delay it by 10 or 15 second so it's not a big deal, just an annoyance really.

All in all, I'm ecstatic with this setup and dells commitment to supporting linux on the xps 13.

---

### Post by newcolour78 on 2012-10-08
Does anybody know if the xps13 kernel development is going to continue when Quantal will be released? I am happy with the LTS at the moment, but there are a few quirks I like about 12.10, and I'd like to upgrade as soon as it comes out.

Thanks in advance.
S.

---

### Post by garak on 2012-10-09
> **newcolour78 said:**
> Does anybody know if the xps13 kernel development is going to continue when Quantal will be released? I am happy with the LTS at the moment, but there are a few quirks I like about 12.10, and I'd like to upgrade as soon as it comes out.

Thanks in advance.
S.

I dist-upgraded just today.
So I'm using 12.10 since a few hours, so far so good :)

---

### Post by gensym on 2012-10-13
Did anyone try installing another Linux based OS (or FreeBSD for that matter) on the XPS 13?

If so, I would very much like to know how the experience turned out to be.

---

### Post by soilenrok on 2012-10-16
I purchased the XPS 13 last month and have installed the official Ubuntu 12.04 LTS with the Sputnik PPA added. So far I am VERY pleased with the performance. The only issue I have had is that screen brightness settings revert back to the default after reboot, and act up a bit after waking from suspension. I'm fairly certain that this is being worked on (and may even have been resolved), but it hasn't bothered be enough for me to fix it yet. Keep up the excellent work everyone!

---

### Post by nmaster on 2012-10-19
Does anyone have any comments on the palm detection of the cypress touchpad?

---

### Post by opensas on 2012-10-19
anybody tried with ubuntu 12.10???

clean install and/or upgrading...

saludos

sas

---

### Post by acruxksa on 2012-10-22
> **opensas said:**
> anybody tried with ubuntu 12.10???

clean install and/or upgrading...

saludos

sas

See post #186 (4 posts above yours)

Hoping everything works with the refreshed xps 13 shipping October 26th. As well because I can't stand windows 8 ............

---

### Post by gensym on 2012-10-22
Today I upgraded from 12.04 to 12.10. My only problem was the system update messing with my fonts settings (which was relatively easy to solve with some 5/10 minutes of tinkering around).

Kamals PPA also supports the 12.10.

---

### Post by JaxJags on 2012-11-16
My wireless is acting very weird. When I'm at home, my computer is always connected to my router. It's fast, and works fine. However, when I am at school, or far away from my router at home, the internet works for only a short amount of time. Then, it disconnects. I have to delete the connection, and restart the computer to get the connection back. Very frustrating. Any ideas?

---

### Post by Mr. Picklesworth on 2012-11-16
> **JaxJags said:**
> My wireless is acting very weird. When I'm at home, my computer is always connected to my router. It's fast, and works fine. However, when I am at school, or far away from my router at home, the internet works for only a short amount of time. Then, it disconnects. I have to delete the connection, and restart the computer to get the connection back. Very frustrating. Any ideas?

I haven't had any issues with wifi, but you could try either connecting your computer to AC, or turn off wifi power saving like so:
```
sudo iwconfig wlan0 power off
```

If the behaviour changes as a result, that might indicate something :)

---

### Post by sanette on 2012-11-17
> **JaxJags said:**
> My wireless is acting very weird. When I'm at home, my computer is always connected to my router. It's fast, and works fine. However, when I am at school, or far away from my router at home, the internet works for only a short amount of time. Then, it disconnects. I have to delete the connection, and restart the computer to get the connection back. Very frustrating. Any ideas?

I had the same issue.
I followed the instructions there:
[http://ubuntuforums.org/showthread.php?t=2012228](http://ubuntuforums.org/showthread.php?t=2012228)
namely:

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

The idea is to disable the "n" protocol ( = very high speed )
So, yes, you don't get top speed (max is now 54Mb/s)
but it seems much more stable

hope this helps

---

### Post by sanette on 2012-11-17
So I have just received my xps 13, and I'm going to have a few questions.

So far it works pretty well.

First question: is there a way to get the "middle button" from the touchpad ?

---

### Post by sanette on 2012-11-17
> **sanette said:**
> there a way to get the "middle button" from the touchpad ?

I'm replying to myself: in the kubuntu system settings, I can choose
to emulate middle button with 3-finger tap (this works well) or
with a corner tap (this does not work all the time)

Ok, next step: I am upgrading to 12.10... fingers crossed!

---

### Post by qualtch on 2012-12-05
> **sanette said:**
> Ok, next step: I am upgrading to 12.10... fingers crossed!

Wonder how this went. Two weeks and no response :P

---

### Post by garak on 2012-12-05
I'm on 12.10 since a while, and I just experiencing a couple of annoying issues.

First one: disk is checked at every boot. Looks like shutdown is not so clean (at least, I found a bug on launchpad mentioning it) and so the disk is not unmounted properly.

Second (and more annoying) one: sometimes lightdm crashes on start. So, I have to go in tty1, login and make it start by hand (sudo start lightdm).

---

### Post by ales004 on 2012-12-06
Hi everybody,
I have just bought a brand new Dell Xps 13. I made a fresh install of Ubuntu 12.10 and added the sputnik ppa.
Everything works very well (trackpad, wifi,..) the only problem I have is that I can't change the brightness. 
It seems that the brightness is fixed when I switch on the computer (low brigthness if using battery, high brigthness otherwise) and I can't change it inside Ubuntu. Has someone any idea how I could solve this?

Thank you very much
Alessandro

---

### Post by Paerez on 2012-12-06
Read the first page of this thread, solution is there.

---

### Post by ales004 on 2012-12-07
> **Paerez said:**
> Read the first page of this thread, solution is there.
Thank you for your answer! I readed the first pages of this thread but unfortunately no method functioned...

** I added the script ini /etc/init/backlight.conf like you suggested in #10.

** I added the line echo 0 > /sys/class/backlight/intel_backlight/brightness in /etc/rc.local

** I added the script of #40 in /etc/pm/sleep.d/10_dell_xps_ultrabook that is executable.

I Rebooted every time, no change. 

If I write sudo start backlight the answer is stop/waiting. Why do you thing is this?

When I change /sys/.../backlight the indicator (Fn+F4) is at minimum but no change in the brightness and no change with (Fn+F5).

---

### Post by Paerez on 2012-12-07
hmm that's too bad. the "stop/waiting" is fine, because it just runs real quick and stops.

Looking over on the dell forums, it may be related to bios or kernel:

[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19472057.aspx](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19472057.aspx)

Are you fully up to date? You could also try the sputnik ppas.

---

### Post by ales004 on 2012-12-08
I already added the sputnik ppa (or at least I think...)
uname -a gives back:
Linux 3.5.0-19-generic #30+kamal11~DellXPS-Ubuntu SMP
dmidecode -s bios-version gives back
A06
Could be one of these the problem?
I took the kernel from here:
[https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel](https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel)

Thanks!

---

### Post by seebach on 2012-12-10
Since this weekend I've started getting an warning from Software Update that tells me these sources are unavaible. Anyone else getting this?

[PHP]W:Failed to fetch http://ppa.launchpad.net/canonical-hwe-team/sputnik-policykit/ubuntu/dists/quantal/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/canonical-hwe-team/sputnik-policykit/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/canonical-hwe-team/sputnik-policykit/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/PHP]

Has someone moved the PPA's?

---

### Post by blackstripes on 2012-12-14
I just purchased a refurbished XPS 13 from Dell (2nd generation), and I cannot for the life of me get Ubuntu to install via USB.  For the last few hours I've tried every utility I can find to help create a Ubuntu USB stick, and they complete the stick without issue, but when booting from USB the system simply says "Operation System not found". 

I have made literally no progress and am super frustrated.  Anyone have any idea what in the world could be going on?

---

### Post by blackstripes on 2012-12-14
Using another laptop i have verified that my USB stick properly boots ubuntu when booting via USB, but I still get "Operation System not found" when booting from USB on the XPS 13.  I've tried both USB ports - no dice...

---

### Post by blackstripes on 2012-12-15
I've seen some talk about XPS 13 ultrabooks not being able to boot GPT partitions and am wondering if this is somehow related?  Although it appears as if all the USB keys I've created were FAT32 filesystems.  

I'm caving in and am going to go buy a USB DVD Drive!

---

### Post by blackstripes on 2012-12-15
Just to close the loop on this, I bought a USB DVD-RW drive and installed Ubuntu (12.04 Sputnik iso) without a hitch.  So weird.

---

### Post by opensas on 2012-12-15
Hi

I usually format the whole pen drive to a fat32 partition, and just use Unetbootin

always worked fine so far. try with another usb stick

---

### Post by blackstripes on 2012-12-15
> **opensas said:**
> Hi

I usually format the whole pen drive to a fat32 partition, and just use Unetbootin

always worked fine so far. try with another usb stick

I'm good to go now thanks to the USB DVD-RW drive, but before I purcahsed that I had tried multiple pen drives as well as unetbootin, still didn't work.

My trackpad gestures seem to work just fine, but I'd like to customize them.  Currently the following works:

- Two finger scroll (vertical and horizontal)
- Two finger right-click
- Three finger; Up - launches the lens, Down - Moves windows around
- Four finger; Left - hides Unity dock, Right - Reveals Unity dock

I'm happy with the 2-finger gestures, but I'd love to enable three finger left/right gestures as backward and forward in browsers, nautilus, etc.

Also, I'd like to use 4-finger (up/down) to launch Compiz' Scale and Workspace switching, respectively.

Anyone have any luck customizing these inputs?

:-s

---

### Post by mdye on 2012-12-17
Hey there - I just ordered this laptop last week to replace an old Lenovo that was donated to my sister. It will be arriving today, and I'm really excited. I was just curious, if anyone knows, what would be the best, most efficient harddrive partition scheme for this laptop? I have no plans to keep Windows (I wish I could afford to just buy the Ubuntu version, but that was prohibitively expensive) so I'm really up for anything. Usually I have /home on its own partition, but my last laptop had to have /boot on its own as well (I never really figured out why that was and only figured it out after a lot of trial and error.) So I'm wondering if anyone has any recommendations. Thanks!

---

### Post by guggi on 2012-12-18
does the dell xps 13 have line-in? 
Would i be able to record with audacity using the kombo-jacks line-in?

cheers

---

### Post by SeanBlader on 2012-12-19
On all my Dell's I've only ever done 2 partitions, / and /home. People talk about "needing" swap, but that's a bunch of crap. While running on a 4 gig machine you'll never get to use swap unless you're running several VM's at once, just don't do that. Also you'll hear about "needing" swap if you want to hibernate, but with this machine's startup time, that's mostly pointless, and if you absolutely must hibernate, well the system will use space it can find for it. I forget if I read it was under / or if it went in your home folder but basically while it's recommended to have swap that's double your ram, I am unwilling to use a boatload of SSD just in case.

Also reports from Dell are that the headphone port also acts as input, but you can bet that it's mono-only input, not ideal for actual recording of anything. If I were you I'd get some sort of external sound processor to get stereo.

---

### Post by guggi on 2012-12-19
> Also reports from Dell are that the headphone port also acts as input, but you can bet that it's mono-only input, not ideal for actual recording of anything. If I were you I'd get some sort of external sound processor to get stereo.

to bad, so the dell xps wont be an option, thx.

---

### Post by omar abdullah on 2012-12-23
What is the best version of this XPS-L321X  ultrabook compatibility

---

### Post by cathalcummins on 2013-01-04
Hi there,

I am considering buying an XPS13. I will use it for doing light scientific computing on-the-go. I run 12.04 on my desktop and laptop and think it's great and wish to use it on the new device.

I'm living outside the US so don't have access to the developer edition.

My questions are:

1. Is there a preferred hardware (i.e. i5 rather than i7) to minimise fan noise and extend battery life... or, even better, has the issue of fan noise been eliminated altogether?

2. Is there any sense in waiting for the Developer edition to enter Eurpoean markets if I've no interest in developer tools?

3. Is there a big BIOS or hardware change coming up from the Trackpad manufacturer/Dell which I should wait for?

4. Any other general advice before buying? 

I should mention also that I've never installed from anything other than a CD...

---

### Post by Paerez on 2013-01-04
You can use the sputnik ppa

[https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel](https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel)

For a lot of hardware compatibility.

Both i5 and i7s used in the XPS 13 have a tdp wattage of 17w, so no difference in fan heat.


The only reason to hold out for the dev edition would be to leverage dell's support, since they'd support ubuntu on it.

Installing from usb is really easy, and ubuntu has instructions when you download it for usb install.

---

### Post by cathalcummins on 2013-01-05
Thanks for your reply Paerez. Do you know if there are install issues when Win8 is installed first? I [read]("http://news.efytimes.com/e1/96550/Will-Windows--Secure-Boot-Help-Dell-Sell-Ubuntu-Ultrabook") that it was difficult to get rid of 8 once it's installed. If so, do you know if Dell can sell it without an os?

---

### Post by Paerez on 2013-01-05
I'm not exactly sure on that. I have the previous gen xps 13 and it came w/ win 7.

Seems like you can turn off secure boot in the bios, then you're fine:

[https://bbs.archlinux.org/viewtopic.php?pid=1201185#p1201185](https://bbs.archlinux.org/viewtopic.php?pid=1201185#p1201185)

Also, looks like Ubuntu 12.10 will boot on secure boot. My guess is they got secure boot keys for it:

[https://help.ubuntu.com/community/UEFIBooting#efilinux](https://help.ubuntu.com/community/UEFIBooting#efilinux)

However, 12.04 does not boot w/ secure boot. So dell's sputnik probably has secure boot keys in it that dell got from MS.

So, I think you're safe, just disable secure boot if 12.10 doesn't work right away.

---

### Post by opensas on 2013-01-05
about the windows uninstall

I bought an XPS 13 in a best-buy store in Boston, US. I repartitioned the hard drive to install an ubuntu 12.04 from a pen drive.I had no trouble doing it.

BUT I had to change the equipment because of a glitch in the screen, and the people at best buy insisted that in order to receive the equipment the boot sector should be exactly the way they gave it to me.

That is, they wouldn't accept the machine booting with grub.

I hope that when sputnik releases, with ubuntu support, these problems should be solved. If not, just keep a backup copy of the whole drive just the way it comes when you buy it, just in case.

(Once I got back home, hey offered me support in Argentina for 2 years for an extra U$S 200.)

On the other hand, I bought an i5 with 128 SSD and 4GB memory. I would recommend upgrading it to 256 GB SSD, and if you are working with heavy stuff (which is not your case) adding another 4GB ram woudln't be bad either

BTW, The ultrabook works wonderfully great with ubuntu.

---

### Post by cathalcummins on 2013-01-10
Great stuff guys, thanks for all your help. I'm going to get onto Dell soon.

---

### Post by mdye on 2013-01-18
Hey has anyone heard what's going to be happening with the Sputnik PPA under Raring?  Will the PPA get updated?  Or is it Quantal the end of the line?

The Sputnik kernal is pretty awesome, btw.  For the heck of it I tried Fedora and it couldn't do even as well as Ubuntu without the Sputnik business.

---

### Post by cathalcummins on 2013-02-04
Hi guys, on the strength of the advice here I went off and got an XPS 13. I'm pretty happy; installing ubuntu was a doddle. I am having trouble connecting to the Sputnik ppa and I'm wondering if someone could help me.

I'm running 12.04 64bit (3.2.0-37-generic).

I went to

[https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel](https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel)

and followed instructions to add the precise sources to sources list (I did this through the terminal). I checked my sources file and sure enough the ppa lines are there...

Since (presumably) I don't have any sputnik software installed, a simple "update" probably won't be enough. Is there something I need to do to tell my update manager to get the hardware software (Cypress, for example)? I did try sudo apt-get upgrade too but nada...

---

### Post by Paerez on 2013-02-04
Check out the packages page for the ppa:

[https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel/+packages](https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel/+packages)

And click on "linux" for precise. It says which packages are provided.

You may have to go into a package manager and choose the version from sputnik, if the one from the official ppa is ahead of it.

It looks like Kamal (who's the owner of the sputnik ppa) is getting the new cypress drivers pulled into raring:

[http://ubuntu.5.n6.nabble.com/Raring-PULL-Cypress-PS-2-Trackpad-driver-td5009970.html](http://ubuntu.5.n6.nabble.com/Raring-PULL-Cypress-PS-2-Trackpad-driver-td5009970.html)

That was the main issue I had, so hopefully raring will have it out of the box!

---

### Post by cathalcummins on 2013-02-04
>> You may have to go into a package manager and choose the version from sputnik, if the one from the official ppa is ahead of it.


Not sure what you mean by this. I'm in synaptic and I can see none of these packages; or am I misunderstanding what you're saying?

---

### Post by henrx on 2013-02-04
Samsung laptops can brick if ubuntu 12.10 or later is attempted.  luckily i could restore windows and am using VirtualBox.

---

### Post by Paerez on 2013-02-04
look for packages that start with "linux-image-" there should be a bunch of versions. Use the page I posted as a reference to find the version from sputnik.

The issue is that if the sputnik version is older than the official one, the official one gets install (because it's newer). So you have to pick the sputnik one directly, and potentially uninstall the official one (hopefully this can be done simply). Then you may have to lock the version to the sputnik one so updates don't replace it.

Sorry it's not super easy, but that's why they're trying to incorporate this directly into raring.

---

### Post by cathalcummins on 2013-02-04
Okay, that type of work is new to me and I don't want to break my system so I think I'll jut hold off until the upgrade comes out... thank you for your help, it's much appreciated :)

---

### Post by alexporto90 on 2013-02-04
Hello,

I'm trying to dual boot with ubuntu 12.10 and windows 8, the result was:

[http://paste.ubuntu.com/1610578/](http://paste.ubuntu.com/1610578/)


But when I choose ubuntu in grub is caught in the initial purple screen before starting the load.

Thank you.

---

### Post by cathalcummins on 2013-02-06
Hi there,

I upgraded to 12.10 and added the relevant sputnik ppas.

When I type uname -a

Linux xps 3.5.0-23-generic #35+kamal11~DellXPS-Ubuntu

which looks promising. How do I know that the relevant software is installed; Cypress drivers for example?

---

### Post by rsthau on 2013-02-21
Hi.  I'm thinking of getting one of these, and am curious about mouse gesture support --- particularly whether there's  three-button mouse emulation (either configurable, or just out of the  box).  There are days when I use mouse-middle (well, actually  three-finger-tap on my current ASUS, but that's how it's treated) more  than the equivalent of mouse-right.

Thanks!

---

### Post by vuarnet on 2013-03-13
> **rsthau said:**
> Hi.  I'm thinking of getting one of these, and am curious about mouse gesture support --- particularly whether there's  three-button mouse emulation (either configurable, or just out of the  box).  There are days when I use mouse-middle (well, actually  three-finger-tap on my current ASUS, but that's how it's treated) more  than the equivalent of mouse-right.

Thanks!

afaik, the cypress touchpad is fully supported with use of the ppas, and will be fully integrated into the source starting with 13.04 (which I've tried, and despite a few *tiny* bugs, is *awesome* on the xps13 ... but of those one of which was mouse settings lol). My guess is that if the feature is supported in ubuntu, it will work with either 12.04 or 12.10 with the ppas added. Starting with 13.04 there will be no need for the custom sputnik kernel ppas bc they've been merged into source.

---

### Post by Nittalope on 2013-03-21
Just bought a XPS Sputnik with the new HD sceen (by the way: awsome!).

I've installed Kubuntu 12.04 and the Sputnik ppa. My kernel with uname -a is:

Linux ******* 3.2.0-39-generic #62+kamal15~DellXPS-Ubuntu SMP Mon Mar 4 19:08:48 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Everything is working fine except for the wifi, that appears to be quite slow. Has anybody the same issue?

Edit: Found a solution to my problem following [this]("http://ubuntuforums.org/showthread.php?t=2012228") post. Only I've not disabled the power saving options (I just did the terminal part 
 	Code:
 	
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf sudo modprobe -rfv iwlwifi sudo modprobe -v iwlwifi )

[FONT=arial]And everything is really clicking now on this wonderful machine!
[/FONT][FONT=arial] [/FONT]

---

### Post by mpw on 2013-03-30
Hello guys,

just got one for my girlfriend. Ubuntu 13.04 runs everything ootb with battery performances up to 8,5 hours in idle.

Kernel 3.8 rules it :)

Touchpad with multi touch (2 finger scrolling, right click with two fingers and even 3 fingers guestures work), wifi, just everything. I only activated the touchpad features in the system settings. 


Bye
MPW

---

### Post by cr45h on 2013-03-30
What do you mean by 3 finger "gestures"? I can't seem to find the way to change any of the pre-set gestures. With 3-fingers, it only has one gesture. It shows these weird arrows all over the selected window and allows you to drag the window around. Nothing else and no settings. On maximized windows, 3 fingers do nothing. For 4 fingers, a single tap brings up the search window. No other 4 finger gestures as far as I can tell. 

If you've figured out something else, PLEASE let us know how to do it. Thanks!

---

### Post by mpw on 2013-03-31
Well, I just said that the driver detects 3 finger guestures. And thanks for the hint with 4 fingers. 

Probably you can change the action in the xorg.conf. Did Not try it. 

Anyway, the touchpad is pretty lazy and unexactly. Same for you?

---

### Post by cr45h on 2013-03-31
Ok... so It's not just me. The touchpad recognizes multi-touch but the built-in gestures are mostly useless. Thanks for the hint about xorg.conf. I did some googling and found this: [snip](snip). It looks like we may have a way of adding custom gestures after all. I'm going to look at it later when I have some time. As far as the overall smoothness of the touchpad, mine isn't too bad. It's not as good as a mac touchpad but much better than my previous Dell one. Also, my XPS 13 isn't the developer version. It's the one that came with Win 8... so I can tell you that it wasn't any better on Windows 8 than it is on Ubuntu 13.04. Overall, I'm satisfied with it, but it's still far from perfect. Hopefully, they'll keep improving the smoothness of the driver over time.

---

### Post by dsat on 2013-03-31
> **mpw said:**
> Hello guys,

just got one for my girlfriend. Ubuntu 13.04 runs everything ootb with battery performances up to 8,5 hours in idle.

Kernel 3.8 rules it :)

Touchpad with multi touch (2 finger scrolling, right click with two fingers and even 3 fingers guestures work), wifi, just everything. I only activated the touchpad features in the system settings. 


Bye
MPW

Hi mpw,

I also work on this great machine now, but actually with 12.04.

Battery life with "normal" work is about 3-4hours.

Are both usb ports working? In my case only the right side is ok, the left give's power, but no mouse nor other usb device doesn't run on the left...

Greets,
Pete

---

### Post by cr45h on 2013-03-31
My usb ports seem to be working fine (tested with flash drives). However, I also got about 4 hours of battery today while doing "normal" work (i.e. nothing that would stress the processor). I'm actually quite unhappy with this. Part of the problem seems to be that the auto-dimming feature is not functional. You have to remember to dim the screen when not plugged in or else battery life will go to hell. I'm also wondering if the Intel Speed Step technology is working right. If it isn't, that would explain the ****** battery life.

Edit... I only got 4 hours even after manually dimming my screen.

---

### Post by cr45h on 2013-04-01
Unfortunately, I have to report yet another problem. My computer is crashing about 70% of the time coming out of resume and requires a hard boot. I hope this is because I'm using the latest daily builds and that the problem will be fixed by the time the stable 13.04 is released. Has anyone else been having this issue?

---

### Post by dsat on 2013-04-01
I have tested left usb port successfully with 2.0 usb sticks, which are working fine. The problems seems to be usb 3.0 devices... any suggestions?

I also think, that these are prerelease-bug's. I wait to to get a stable lts update end of April :)

---

### Post by mpw on 2013-04-02
Hello again,

well I tested if for a few days now and got to say that this Cypress Touchpad is horrible. In standard settings it is damn slow, you would need 4-5 times flipping over it to get the mouse from the left to the right side of the screen.

I then speeded it up with gpointing-device-settings. But that thing only scales it. Instead of moving 1 pixels for example, it moves now 2 or 3. Just as you set it, but the touchpad becomes extremly unexactly that way. Hitting small buttons like the X to close a window becomes hardly impossible.

And tapping small buttons does not work, because the cursor moves of the hitting zone, when you tap!

Does someone know, if this is a linux driver issue or is the Windows driver that horrible too? Does it have something to do with the full hd screen resolution? I mean hd ready has less pixels so obviously you would get the intention, that the touchpad is more exactly. As far as my technical understanding goes...

My girlfriend wants to return the XPS13 (it's brandnew) and I'm really upset too that dell build that **** in that expensive laptop.

As I read, all improvesments from the repos where already build in to 13.04, so repos wouldn't fix my problem right now.

Any ideas for me? I catch myself trying to do everything with the keyboard and searching for Hotkeys all the time...That gerenerally a good and effective handling strategy, but you can't do everything with hotkeys. And I wouldn't spend 1299,- &#8364; für that experience.

Bye
MPW

/edit: With the help of a friend of mine, I found out, that Ubuntu 12.04.2 WITHOUT the Cypress-Driver runs much much smarter. The touchpad's quite fine without the Cypress Driver. And multitouch works aswell. I can just suppose to not to upgrade to 13.04.

---

### Post by dsat on 2013-04-03
> **mpw said:**
> 
...
/edit: With the help of a friend of mine, I found out, that Ubuntu 12.04.2 WITHOUT the Cypress-Driver runs much much smarter. The touchpad's quite fine without the Cypress Driver. And multitouch works aswell. I can just suppose to not to upgrade to 13.04.

I have got my xps 13 in April with 12.04 from Dell with working touchpad also. Also multiouch works perfect. At the moment I struggle a bit with receiving files via bluetooth, the not working usb 3.0 connect on the left usb port. accu power with 3 to 4 hours could be better. 
but hey, it's a delicacy to work with this fast ultrabook, I love my xps : )

---

### Post by mpw on 2013-04-03
> **vuarnet said:**
> Starting with 13.04 there will be no need for the custom sputnik kernel ppas bc they've been merged into source.

Obviously you did not read my post. In 13.04 the touchpad driver is horrible! It is NOT usable. With 12.04 ootb it works far better.

Right now I'm experiencing a little wifi performance issue. I don't get more than 600KB/s which is not enough to stream hd video. Does someone has any issues like that?

---

### Post by ping-wu on 2013-04-06
I was soooooo looking forward to getting a Dell XPS13 (despite its already disappointing video resolution), but now I would be fooling to stick to my original plan.

Our department buys four to five new notebooks a year.  So far this year, we have purchased two ASUS notebooks (with 64-bit Windows pre-installed and secure boot as default), both have been working very satisfactorily (both are running Raring now).  The only problem we have was that, with one of the two machines, we couldn't use the functional keys to adjust screen brightness.  But we are able to circumvent this problem by locking the screen brightness adjectment app on the launcher.

---

### Post by mdye on 2013-04-07
Has anyone noticed the backlight regression in Raring kernel?  Has it been fixed yet?  *Is* there a fix for it?  There's a bug report for it ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1163720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1163720)) but I've never been able to make heads or tails of Launchpad.  The Sputnik kernel PPA says it's not necessary in Raring, and it seemed to work fine for awhile, but it stopped working for quite some time.  Just wondering if anyone know's what's up?

---

### Post by jacki on 2013-04-13
Yesterday I got my sputnik II (the new version), since then I upgraded to 12.10 and then - mainly because my phone didn't work with mtp in 12.10 - also to 13.04 kubuntu. Now I'm running kernel 3.8.0-18, and most things are working as they should. In particular, keyboard lights, screen brightness (with the keys and automatic when on low battery), trackpad (with gestures for up to 3 fingers, i.e. horizontal/vertical scrolling, 2- and 3-finger tab for mouse buttons, tab and drag; configured via the kde system settings). for fine movements the trackpad is a little painful, and it's also easy to hit it accidentally while typing. suspend works fine, hibernate I haven't tried yet. the wifi connection was unreliable at first, but improved with the tweaks suggested in this thread. I had a lot of fan noise, but hope that is due to all the installing/downloading dropbox etc, still have to check how the fan behaves under normal conditions.
So generally speaking, I am quite happy with the machine!

---

### Post by beerfan on 2013-04-14
> **jacki said:**
> the wifi connection was unreliable at first, but improved with the tweaks suggested in this thread.

Can you point me to the tweaks you mention, or at least the page it can be found on? I have slow wifi speed also and I'd love to know how to fix it.

---

### Post by Mr LJ on 2013-04-14
Hello,

I have a Dell XPS 12 that - I hope - is very similar to  the XPS13 device. After booting the display-brightness is set to minimum  - unfortunately brightness level 0 means backlight off - this is a  little bit annoying. However the brightness-keys work fine and after  resuming from standby the previous backlight-level is restored. Could  the XPS 13 workaround work here as well? 
The daily build from 2013-04-10 with 3.8.0-18 kernel is installed. 
The horrible trackpad is the same with the XPS12, I'm using a Gigabyte m7700 bluetooth-mouse now (the touchscreen is precise but suffers from a touch-end bug...).
With the A05 BIOS my i7 stays quiet nearly all the time.

thanks in advance
best regards

---

### Post by jacki on 2013-04-15
> **beerfan said:**
> Can you point me to the tweaks you mention, or at least the page it can be found on? I have slow wifi speed also and I'd love to know how to fix it.

I was referring to post #195 (on page 20) in this thread.

---

### Post by Snake231088 on 2013-04-20
I have little sound noise when the brightness is not at the maximum with Ubuntu 12.10, while when the brightness is at the max no sound noise. I don't know to fix it.
Like [http://en.community.dell.com/support-forums/desktop/f/3515/p/19248824/19397368.aspx](http://en.community.dell.com/support-forums/desktop/f/3515/p/19248824/19397368.aspx)

---

### Post by blackstripes on 2013-04-20
I'm running 13.04 now on the XPS 13 and noticed that horizontal two-finger scroll isn't working??  Anyone know how to enable this?  

Also... and this is a longshot, has anyone figured out how to customize the gestures? I'd love to get three-finger left=back right=forward working...

---

### Post by yeez on 2013-04-20
> **blackstripes said:**
> I'm running 13.04 now on the XPS 13 and noticed that horizontal two-finger scroll isn't working??  Anyone know how to enable this?  

Also... and this is a longshot, has anyone figured out how to customize the gestures? I'd love to get three-finger left=back right=forward working...

I'm using xSwipe, works pretty good. You can read more here: [http://en.community.dell.com/techcenter/os-applications/f/4613/t/19467783.aspx](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19467783.aspx)

---

### Post by opensas on 2013-04-20
a nice review...
[http://arstechnica.com/gadgets/2013/04/it-just-works-dell-xps-13-developer-edition-linux-ultrabook-review/]("http://arstechnica.com/gadgets/2013/04/it-just-works-dell-xps-13-developer-edition-linux-ultrabook-review/")

---

### Post by Mr LJ on 2013-04-21
Do you all have the little power supply shown in the review? The power supply that came with my xps12 seems to be somehow bigger..

---

### Post by yeez on 2013-04-21
> **Mr LJ said:**
> Do you all have the little power supply shown in the review? The power supply that came with my xps12 seems to be somehow bigger..
I don't have the Sputnik version myself (FHD, i7 8gb ram 128SSD Windows edition) and I do have the little power supply, just as the one shown in the review.
Anyone know where I can grab a similar one as a spare? (Doesn't have to be OEM)

---

### Post by jacki on 2013-04-22
> **blackstripes said:**
> I'm running 13.04 now on the XPS 13 and noticed that horizontal two-finger scroll isn't working??  Anyone know how to enable this?  

Also... and this is a longshot, has anyone figured out how to customize the gestures? I'd love to get three-finger left=back right=forward working...

running kubuntu, you can configure it in the kde system settings. for me, horizontal two finger scrolling works. But I'd also like to see more advanced configuration possibilities for the trackpad. Is it capable of four finger gestures actually?

---

### Post by yeez on 2013-04-23
Quick question. How hot does your XPS run? Mine is about 60C. Sometimes goes to 70, sometimes drop to 50.. I find it kind of high? Fan kicks in at 60.

---

### Post by abxps on 2013-04-23
I have the exact same issue.  There is a humming depending on the brightness.  At maximum the noise is faint but still there.  One step below max and you really hear it.  I had a engineer come to replace the motherboard thinking it was a faulty capacitor:  no change.  A second engineer came to change the display:  the noise disappeared but the display was blank (maybe a wrong part).  Another engineer came to try another display:  again, no noise, but the display still wouldn't work.  At this point I was too frustrated and wanted a replacement laptop.  Dell customer care is good and they sent me a new laptop.  Unfortunately, the new one has the exact same issue.  To make things worse, using a usb stick also gives a strange noise as well as the ssd.   Sounds a bit like a dial up modem!

I'm glad I'm not the only person with this issue -- if more people report this problem maybe they'll listen.  Can you add to my thread on the Dell forums:
[http://en.community.dell.com/support-forums/laptop/f/3518/t/19500507.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/t/19500507.aspx)



> **Snake231088 said:**
> I have little sound noise when the brightness is not at the maximum with Ubuntu 12.10, while when the brightness is at the max no sound noise. I don't know to fix it.
Like [http://en.community.dell.com/support-forums/desktop/f/3515/p/19248824/19397368.aspx](http://en.community.dell.com/support-forums/desktop/f/3515/p/19248824/19397368.aspx)

---

### Post by Snake231088 on 2013-04-25
I've installed new Ubuntu 13.04, but the fn keys for brightness doesn't work, and the brightness is always at the min. Any help?

---

### Post by abxps on 2013-04-25
> **Snake231088 said:**
> I've installed new Ubuntu 13.04, but the fn  keys for brightness doesn't work, and the brightness is always at the  min. Any help?

It was reported as a regression and there is a temporary fix offered:

[https://bugs.launchpad.net/dell-sputnik/+bug/1169376](https://bugs.launchpad.net/dell-sputnik/+bug/1169376)

---

### Post by AdamWill on 2013-05-02
Hey, folks. I got one of these laptops then put Fedora on it. I'm currently fiddling with the cursor speed problem - someone back on page 25 noted the same thing, the cursor speed seems very slow, it takes multiple scrubs of the touchpad to get across the screen.

Are other Ubuntu users also seeing this? Does it differ between Ubuntu releases / PPAs / etc?

I'd be interested in seeing the output of this command:

xinput list-props "CyPS/2 Cypress Trackpad"

from Ubuntu systems, if anyone feels like obliging :) thanks!

---

### Post by opensas on 2013-05-03
I hope this helps

--

$ xinput list-props "CyPS/2 Cypress Trackpad"
Device 'CyPS/2 Cypress Trackpad':
	Device Enabled (132):	1
	Coordinate Transformation Matrix (134):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (256):	1
	Device Accel Constant Deceleration (257):	2.500000
	Device Accel Adaptive Deceleration (258):	1.000000
	Device Accel Velocity Scaling (259):	12.500000
	Synaptics Edges (260):	44, 1056, 33, 587
	Synaptics Finger (261):	25, 30, 256
	Synaptics Tap Time (262):	180
	Synaptics Tap Move (263):	55
	Synaptics Tap Durations (264):	180, 180, 100
	Synaptics ClickPad (265):	1
	Synaptics Tap FastTap (266):	0
	Synaptics Middle Button Timeout (267):	0
	Synaptics Two-Finger Pressure (268):	282
	Synaptics Two-Finger Width (269):	112
	Synaptics Scrolling Distance (270):	25, 25
	Synaptics Edge Scrolling (271):	0, 0, 0
	Synaptics Two-Finger Scrolling (272):	1, 0
	Synaptics Move Speed (273):	1.000000, 1.750000, 0.158479, 40.000000
	Synaptics Edge Motion Pressure (274):	30, 160
	Synaptics Edge Motion Speed (275):	1, 100
	Synaptics Edge Motion Always (276):	0
	Synaptics Off (277):	0
	Synaptics Locked Drags (278):	0
	Synaptics Locked Drags Timeout (279):	5000
	Synaptics Tap Action (280):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (281):	1, 1, 0
	Synaptics Circular Scrolling (282):	0
	Synaptics Circular Scrolling Distance (283):	0.100000
	Synaptics Circular Scrolling Trigger (284):	0
	Synaptics Circular Pad (285):	0
	Synaptics Palm Detection (286):	0
	Synaptics Palm Dimensions (287):	160, 200
	Synaptics Coasting Speed (288):	20.000000, 50.000000
	Synaptics Pressure Motion (289):		... of unknown type CARDINAL

	Synaptics Pressure Motion Factor (290):	1.000000, 1.000000
	Synaptics Resolution Detect (291):	1
	Synaptics Grab Event Device (292):	1
	Synaptics Gestures (293):	1
	Synaptics Capabilities (294):	1, 1, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (295):	10, 11
	Synaptics Area (296):	0, 0, 0, 0
	Synaptics Soft Button Areas (297):	0, 0, 0, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (298):	6, 6
	Device Product ID (250):	2, 16
	Device Node (251):	"/dev/input/event6"
sas@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-38-generic #61+kamal15~DellXPS-Ubuntu SMP Mon Feb 25 23:43:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
sas@ubuntu:~$ lsb_release -d
Description:	Ubuntu 12.04.2 LTS

--

---

### Post by goebel85 on 2013-05-06
Has someone succeeded using the touch-pad to copy & paste?

Thanks

---

### Post by tibere86 on 2013-05-15
Any fixes for Dell XPS 13 running Ubuntu 13.04 + 3.10 kernel backlight keys not working? My backlight is stuck at 100% and can not be adjusted via the Fn keys. I've Googled and tried a handful of posted fixes, but to no avail.

---

### Post by AdamWill on 2013-05-28
> **opensas said:**
> I hope this helps--

Thanks! Sorry to be so late replying, I got distracted by other work. Does the touchpad on that system seem to be very slow, as others have mentioned, or does it feel OK to you?

---

### Post by Robyr on 2013-06-07
I just picked one of these up, and as of 13.04, I am simply amazed by the feature-completeness. It works perfectly, and in some cases (as with the fan and sleep/resume), Ubuntu outperforms Windows by a wide margin. 

Battery life is also excellent. I don't have much to add, but I wanted to make it clear that THIS is the notebook to have if you are after a Ubuntu-based MacBook Air of sorts.

---

### Post by tinle on 2013-06-08
> **Robyr said:**
> I just picked one of these up, and as of 13.04, I am simply amazed by the feature-completeness. It works perfectly, and in some cases (as with the fan and sleep/resume), Ubuntu outperforms Windows by a wide margin. 

Battery life is also excellent. I don't have much to add, but I wanted to make it clear that THIS is the notebook to have if you are after a Ubuntu-based MacBook Air of sorts.

Do you buy the editor version or the normal one and install 13.04 yourself? Do you dual boot with win8 or just 13.04? Thanks!

---

### Post by tinle on 2013-06-08
I've just ordered an xps13, will received it next week. It only has 128gb sdd. Not sure if I should keep win8 along with Ubuntu13.04 or just erase win8 (if so, I may not get supported from Dell customer service if anything happens). Any advice? Thanks.

---

### Post by opensas on 2013-06-09
I can share with you my sad experience.

I bought a dell XPS in a best-buy store in boston (US). A soon as I got my hands on it, I installed ubuntu in a different partition. After a couple of days, I realized the screen had a small scratch and the keyboard wasn't responding as it should.

So I tried to change it for another equipment. They were out of stock, so I returned them the equipment, but when they found the grub boot screen they told me they couldn't receive it. I showed them that the win partition was there, that it worked flawlessly, and I even erased the ubuntu partition, but just because grub was at the boot sector they couldn't take. 

The dell machine machine has a recovery partition, but you can't restore it from there, you have create a recovery pen-drive and only then you can restore the partition.

I didn't have a pen drive with enough space (I think the recovery partition was about 7 GB, if I'm not mistaken... boy, you have a miserable 128 GB drive and they expect you to give away 7GB to restore an operating system you didn't want in the first place) to create the recovery usb.

It was late, I just wanted to handle them the equipment and to get my money back (they didn't have other ultrabook to exchange it)

Then they told me that they could do it for U$$ 100 !!! 

I was really pissed of. Not only I had to pay in the first time for an operating system I didn't want to have on my ultrabook (and there was no refund!), but know they wanted to charge me for restoring it, just because THEY claim that it has to be installed in order to fix what clearly was a hardware problem.

In the end, I had to buy a 32 GB pen drive, take away the ultra book, spend a good couple of hours at my hotel (BTW, I wasted time of my holidays on this) and go back to the store the next day so that they coudl finally accept the faulty equipment.

I've been charged for an OS I didn't want in the first place and for which I had no use. They wouldn't refund me in case I wanted to give that license back. I had and obvious hardware problem (you could see the scratched screen and the falty keyboard). The OS was even there, fully functional and working as expected. But they saw a funny purple startup screen so they wouldn't accept it. They wanted to charge me for restoring an OS I didn't ask for, and that wasn't needed to see the fault or to fix it. In the end I had to buy a pen drive, and waste MY time restoring an os that DELL support would surely wipe out. What would have happend if a virus (pretty common stuf in the win world, BTW) would have erased my whole drive before I could create a usb backup? Would they charge me for even another unwanted windows license just to fix a hardware issue? And why the heck do I have to waste a pen-drive just to get the support?

Sorry for the rant. It just pisses me off because it makes no sense to me.

This happened a year ago, perhaps by now they might have made things better.

In the end I could finally return the equipment and bought another XPS in another store. The machine runs perfectly with Ubuntu, I'm awfully satisfied with it.

It's just a real pitty that they worked so hard in the technical aspects and were so careless in this comercial issues.

On other hand, back here in Argentina I had a problem with the mother, and they changed it without any problem whatsoever. And of course there's no traces of windows in my ultrabook.

I would advice you to create and keep a restore usb at least for a couple of months, and if you have some other machine with spare space I would try to save it there.

saludos

sas

---

### Post by tinle on 2013-06-09
Hi Sas, sorry to hear about your story. These people just want a reason to get more money from you. Thanks for the advice, I have a 32GB usb and will create a recovery partition before completely removing win8. So I guess I'll go with Ubuntu 12.04 instead of 13.04 then. I've heard of few problems with installing eclipse or emacs on 13.04 so 12.04 is a more reasonable choice for programming purpose and long-term support.

---

### Post by opensas on 2013-06-09
I'm using 13.04, for development purposes too, and havent had any trouble. Besides hardware support is included right with the current kernel.

If you go with the 12.04 I think you'll have to install dell ppa (kamal).

BTW, to develop I just download the java jdk direcltly from oracle site, and I do the same with eclipse. I try to avoid package managers to have complete control of the versions I'm using.

So far now I never had any troubles with these approach, on any distro. Besides having all your development libraries and executables in a folder will make it really easy to share it among different partitions.

In fact I always keep a small partition (10GB) to play around with different distros.

---

### Post by tinle on 2013-06-09
> **opensas said:**
> I'm using 13.04, for development purposes too, and havent had any trouble. Besides hardware support is included right with the current kernel.

If you go with the 12.04 I think you'll have to install dell ppa (kamal).

BTW, to develop I just download the java jdk direcltly from oracle site, and I do the same with eclipse. I try to avoid package managers to have complete control of the versions I'm using.

So far now I never had any troubles with these approach, on any distro. Besides having all your development libraries and executables in a folder will make it really easy to share it among different partitions.

In fact I always keep a small partition (10GB) to play around with different distros.

I like your idea of keeping a common partition for different systems. But I read in the link below and it seems that it may not be a good idea (or it may not be easy, at least for beginner like me) to do so.
[http://askubuntu.com/questions/55224/a-common-home-partition-for-multiple-linux-distributions](http://askubuntu.com/questions/55224/a-common-home-partition-for-multiple-linux-distributions)

Like you said, I will give 13.04 a try then. I'm not intended to use multiple distros on my Dell (It only has 128GB). May be I'll just use Dropbox if I have to share the excuatables between different systems then (not likely).

---

### Post by opensas on 2013-06-10
[offtopic answer, sorry] Well, my setup is simpler than that

I just have a ~/devel folder in my home directory which is in fact a symlink to /media/data/Copy (could be dropbox or ubuntuOne)

in ~/devel I save the libraries (sdk, eclipse, node, maven, ant, etc) and also my work

/media/data is the partition available to every distro

/media/data/Copy is where I installed Copy, an alternative to DropBox that gives you more space for free (check [this review]("http://opensas.wordpress.com/2013/05/04/multiplatform-dropbox-alternative-with-lots-of-gb-for-free/"))

on every distro I try I just create the symlink, and adjust the path from ~/.profile... and it works

---

### Post by tinle on 2013-06-20
Did anyone have the sound problem with ubuntu 13.04 on XPS13 and know how to fix it? I've fixed the wifi problem, but still been helpless with no sound on my XPS13 at all

---

### Post by cyrus_the_virus on 2013-06-22
Does the Intel 4000 HD video chip perform well for ordinary desktop work?

I'm considering to buy this laptop. I currently own an old XPS m1530 with a Nvidia card. The compiz window animations look really bad on that machine. Furthermore, there is an annoying bug with gnome terminal causing the terminal output to be not refreshed properly. Very annoying because I use the terminal in my everday work.

However, I have read that both problems are related to the Nvdia driver. So I was wondering if the Intel video chip in the new XPS 13 is better.

---

### Post by beerfan on 2013-06-24
> **cyrus_the_virus said:**
> Does the Intel 4000 HD video chip perform well for ordinary desktop work?

The Intel 4000 GPU is more than adequate for Compiz animations and refreshing terminal windows. It even runs some games well (though this generates lots of heat). I've tried running Skyrim with it but even on low settings it can't handle that (at least on Ubuntu). For development work you will have no worries though.

---

### Post by cyrus_the_virus on 2013-06-25
> **beerfan said:**
> The Intel 4000 GPU is more than adequate for Compiz animations and refreshing terminal windows. It even runs some games well (though this generates lots of heat). I've tried running Skyrim with it but even on low settings it can't handle that (at least on Ubuntu). For development work you will have no worries though.

Thanks a lot for your feedback :)

The Nvidia card in my current laptop should be able to handle at least ordinary development work but it doesn't due to driver problems. Glad to hear this is not an issue on the XPS 13.

Guess now I have to wait until it's available for purchase again.

---

### Post by Romu on 2013-07-05
Hi,
I've been running an XPS Full HD (L322x) for fews days now with Ubuntu Gnome 13.04 + Gnome 3 ppa. I see the LCD backlight butttons don't work, is there any fix somewhere? Thanks.

EDIT: Found, sorry, I should have searched before asking.

---

### Post by tibere86 on 2013-07-05
> **Romu said:**
> Hi,
I've been running an XPS Full HD (L322x) for fews days now with Ubuntu Gnome 13.04 + Gnome 3 ppa. I see the LCD backlight butttons don't work, is there any fix somewhere? Thanks.

EDIT: Found, sorry, I should have searched before asking.
I'm running Ubuntu 13.04 + 3.10 kernel and my backlight buttons do not work also. Mind pointing me to the fix you used?

---

### Post by pjssilva2 on 2013-08-05
I have a new XPS 13 (that came with Windows 8, then with UEFI). I wiped windows and  installed only Ubuntu 13.04. I am booting in legacy mode.

The machine is basically working under minor tweaks but there  is still a  major problem. Sometimes when I insert some usb devices the machine  turn off right away. No messages, nada. Just a black screen. This  happens always when I try to plug-in an external WD My Passaport 500Gb,  which is a USB 3.0 device. But it happened with other devices too (even  USB 2.0 memory keys, for  example it turned off once when trying to  format such a device, but this is much more rare).

Is anyone experiencing this kind of problem? Maybe the problem is with USB 3.0. Is there a way to turn it off?

---

### Post by alpha86 on 2013-08-06
Dear XPS13 users,

I have identified a problem with the left USB port of XPS13. I have done some read up on this issue and apparently there are a few people who had this problem as well. The current discussion is at [http://en.community.dell.com/techcenter/os-applications/f/4613/t/19491324.aspx](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19491324.aspx)

I'm running 12.04 LTS with the Dell Sputnik PPA.

The issue can be replicated when you connect specific devices into the left USB. 

USB2.0 devices generally have no problem (thumb drive, usb2.0 wd passport hdd...), they all work good on the left USB.

Example devices that are confirmed to be not working:
Logitech unifying receiver - if you connect to left usb, using a mouse 30cm away will make your cursor lags. This doesnt happen on the right USB
WD Passport USB3.0 external hard disk - cannot detect when connect to left USB, works perfectly on right USB

I did a search on this thread and I found user [dsat]("http://ubuntuforums.org/member.php?u=654539") actually raised this issue in post #242, [#239]("http://ubuntuforums.org/showthread.php?t=1932965&page=24&p=12582533&highlight=left%20usb#post12582533"), but there's not much discussion about it.

I'm trying to find out if this a ubuntu/driver issue or a hardware defect. It seems pretty weird to me that the right USB works perfectly but not the left (they should have the same driver right?)

May I know if any of you have this issue as well? and if you found no problem on the left USB (tested with USB3.0 hard disk/devices), please post along with your ubuntu version as well so I could narrow down the issue. 

Thanks!

---

### Post by RichardET on 2013-08-17
Guys, why are you wasting your money on this box?  The price is over $1500, anywhere from $1549 to $1599, (depending on which day of the week you scan the Dell site, I guess).  If you want a laptop designed for Ubuntu, go with System76, otherwise, buy Lenovo,
and run Ubuntu as a VM.  By the way, I am not trolling here, I own one New Dell desktop, a 660, and I have had two Dell laptops in the past 7 years, both of which run Linux flawlessly, any version greater or equal to Suse 11, but Dell is playing games with Linux supporters,
and is not a serious proponent of Linux, in my view.  Also Dell support is terrible - never buy anything from Dell, unless you know what you are doing 100% of the time.

---

### Post by danielglz on 2013-09-06
> **Paerez said:**
> ok, to fix brightness, run as root:

echo 0 > /sys/class/backlight/intel_backlight/brightness

Then the keyboard brightness controls work.

EDIT: I put this script into /etc/init/backlight.conf:

```
start on runlevel [23]
task
exec /bin/echo 0 > /sys/class/backlight/intel_backlight/brightness
```

It works when I run "sudo start backlight" but it doesn't happen on boot. Not sure why. I'm new to upstart. Any tips?

In my case, the command:

echo 0 > /sys/class/backlight/intel_backlight/brightness

turns the screen into black, and keyboard controls don't work, so be careful. You can replace "echo 0" by another number ranging from the minimum to maximum brightness (you can browse files in intel_backlight directory to discover a right number for your case).

Daniel.

---

### Post by Snake231088 on 2013-10-17
With Ubuntu 13.10, my L322X start but the resolution is very very bad like a frequency error.
I read and i found that the problem is something about dpp clamping or something else...
Any solution?

---

### Post by Suor on 2013-11-17
I booted with Ubuntu 13.10 usb on Dell XPS 13 and my screen looks like this

[ATTACH=CONFIG]247897[/ATTACH]

I managed to install it with a help of external screen (which works right), installed all updates and still have this. 

I don't have a clue even what I should try to do. Any hints?

---

### Post by creed186 on 2014-01-15
> **Suor said:**
> I booted with Ubuntu 13.10 usb on Dell XPS 13 and my screen looks like this

[ATTACH=CONFIG]247897[/ATTACH]

I managed to install it with a help of external screen (which works right), installed all updates and still have this. 

I don't have a clue even what I should try to do. Any hints?


I just bought an xps13 today and had the same problem. I turned off secureboot and it seems to boot fine now. I am having a few issues with the wireless (struggling to connect to certain networks) and the touchpad (no multitouch) though, but apart from that it seems to be running fine.

---

### Post by tuuk on 2014-01-16
I am also trying to put Ubuntu onto a new XPS 13 Haswell (i7, 256GB SSD, Intel 4400 Graphics).

I have originally run into the problem of built-in display not working with Ubuntu 13.10 (running on a USB stick).
[http://ubuntuforums.org/showthread.php?t=2198946](http://ubuntuforums.org/showthread.php?t=2198946)

I am testing Ubuntu 14.04 (on a USB stick for now). It seems to work fine (although there might be small problems such as the ones mentioned above). But brightness adjustment, tap-to-click, and disabling bluetooth works.

I am contemplating whether to install 14.04 (daily build) or put a newer kernel on 13.10 so that the display works.

I will be very happy to hear the experiences of the others and any suggestions.

Cheers,
tuuk

---

### Post by piperbarb on 2014-02-01
Hi all,

I know I do not post very often, but just wanted to add my 2 cents, for what it's worth, regarding the XPS13 developer edition with Haswell processor.  I bought the 256 GB version that comes with the touch screen.  I don't think you can get that version without the touch screen.  It does not bother me either way.  I do not use the touch feature often, so it is not an issue for me.  The screen is absolutely beautiful.  It was the higher resolution that made me go for this laptop instead of the Macbook Air.  This is not my main computer.  I have my Macbook Pro (dual boot OS X/Ubuntu) and a Dell XPS17 L702x (to Ubuntu only) to do my digital heavy lifting.  :)

It arrived on Wednesday and I have been using it since then.  I have had no problems with it.    When I took it out of the box and started it up, it booted up in just a few seconds.  It saw my wireless network and connecting to it was as easy as connecting my Macbook Pro when I first got it.  Absolutely no connection problems.  It ran through the updates, which can take a few minutes.  After a reboot, the XPS13 has been working without a hitch.  I have been able to install all the software I need to use on it, again, without issue.  In terms of battery life, I am getting about 6.5 to 7 hours doing basic stuff:  word processing, Web browsing, e-mail, photo editing, listening to music, and reading ebooks.  I am not a gamer, so I cannot tell you anything about how it behaves that way, but I am sure others have.  I have the screen brightness low but not minimum.  Even on the lower settings, the screen is quite bright.  I also turn off the backlit keyboard unless I need it.  Since I do not have any Bluetooth devices for this guy, yet, I turned that off, too.  I have no problem with the battery life, considering Ubuntu is not always the most efficient in energy usage.

I have not done any programming with it yet, but will do so soon.

Oh, and I did not upgrade it to a later version of Ubuntu.  It's running 12.04 LTS, just as my other laptops are.  I will upgrade it to the next LTS when it comes out.  I have not had any problems with hardware or software.  I know some people have.

Anyway, depending on your needs, it is worth taking a serious look at.  I realize that my posting is not a technical review, just my first impressions.  Just so you know, I am using it right now.

---

### Post by sanette-linux on 2014-02-18
Dear All

I have my XPS 13 since last year, it works great except for one thing:

the right USB port.
Almost every day, after a random time (1sec to several hours), the port completely stops working (ie is powered off).
It happens with various devices: usb_ethernet adapter, usb_hub, or even a simple usb mouse.
Ecah time,  I see this message in dmesg:

```
[ 1667.471143] timeout: still 3 active urbs on EP #1[ 1668.470438] timeout: still 3 active urbs on EP #1
[ 1669.469733] timeout: still 3 active urbs on EP #1
[ 1671.476282] xhci_hcd 0000:03:00.0: xHCI host not responding to stop endpoint command.
[ 1671.476300] xhci_hcd 0000:03:00.0: Assuming host is dying, halting host.
[ 1671.476435] xhci_hcd 0000:03:00.0: HC died; cleaning up
[ 1671.476500] usb 3-1: USB disconnect, device number 2
[ 1671.476506] usb 3-1.1: USB disconnect, device number 3
[ 1674.466198] xhci_hcd 0000:03:00.0: Timeout while waiting for configure endpoint command
[ 1674.466208] xhci_hcd 0000:03:00.0: Abort the command ring, but the xHCI is dead.
[ 1674.466217] usb 3-1.3: Not enough bandwidth for altsetting 0
[ 1674.491127] usb 3-1.3: USB disconnect, device number 4

```
I'm wondering if the issue is faulty hardware (and then I'll return to DELL) or a linux XHCI driver problem. Any hint ???

I'm using kubuntu saucy (13.10). I have also tried the more recent kernel 3.12.6, but its doesn't change the issue.

---

