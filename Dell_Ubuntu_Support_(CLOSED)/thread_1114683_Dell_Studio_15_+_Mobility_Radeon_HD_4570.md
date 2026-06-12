---
title: "Dell Studio 15 + Mobility Radeon HD 4570"
date: 2009-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by akhilpakkath on 2009-04-03
Hi folks,

I have my dell studio with Mobility Radeon HD 4570. any idea on where I can get the drivers for this one

---

### Post by tr33m4n on 2009-04-03
4570? I was under the impression the Studio 15 comes with hd 3450/3650!! Never heard of a studio with a 4570... when did u buy it?

Cheers
Dan

---

### Post by tr33m4n on 2009-04-03
In fact I just checked up, your graphics card is the radeon hd 3450... unless uve got the onboard intel chip. If it is a radeon however, you should be able to install the drivers via System > Administration > Hardware Drivers... if it is not there (activated or unactivated) then you may have to download the binary from the ati website...

Hope this helps
Cheers
Dan

---

### Post by trampster on 2009-04-19
Did you have any luck getting this graphics card to work.

(and no it is a 4570) at least the one sold in New Zealand is.

I am interested in buying a dell laptop with this card but dont want to do it if I can not use compiz.

---

### Post by tr33m4n on 2009-04-19
Ha! *******, I should of bought mine from New Zealand! They only do the 3650 in the UK :( ah well... Erm I'd probably still suggest the same proceedure as I mentioned before... if that doesnt work, google is your friend :)

Cheers
Dan

---

### Post by trampster on 2009-04-20
Just looked up the ATI driver website...
The latest linux driver is
ATI Catalyst Display Driver version 9.4

This card is not listed as a supported card.

So I guess we are out of luck...

does anyone know if it will ever be supported and if so in what time frame.

---

### Post by leobuntu on 2009-05-21
I'm planning to buy this unit and notice that 4570 uses RV710 chip. Support for this chip has been added in v1.2.4 of radeonhd driver. Jaunty uses v. 1.2.3 afaik. So you need to install the newer version of radeonhd from source and hopefully you'll have a working notebook.

):P

---

### Post by bainorama on 2009-05-23
I'm looking at getting one of those as well, so would be keen to hear how it worked after the upgrade.

---

### Post by louca on 2009-05-26
Mine, with the same card, will be here either by Friday or early next week. Will post here and let you know how it is working.

---

### Post by jonaz on 2009-05-29
9.04 has the proper drivers included but I've had major issues (sound, network, etc...) so I installed 8.04

You can download working drivers for the 4570 from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

to install them go to where you saved them and type:

sudo sh ./ati* --listpkg

this will give you instructions on how to build custom packages for your distro
for Ubuntu/8.04 this is:

sudo sh ./ati* --buildpkg Ubuntu/8.04

after this 6 new packages should be created: just install them all with synaptic, enable your driver in Hardware Drivers and reboot.

---

### Post by chammer on 2009-05-30
i've had my dell studio 15 (1555) for about 2 weeks now and this morning finally getting around to put ubuntu on it along side vista. i also got the hd4570 video card option, and experienced no issues with it. upon initial boot up after install it told me that the proprietary driver was available and i allowed it to get it for me. rebooted, and compiz/opengl working without issues. this is under 9.04. im located in the united states btw - so im guessing this is standard now for the studio 15's wherever they are sold(?).

from lspci:
```

01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

```

the only issue i had was the built in hd sound:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

```

chris@hiroshi:~$ cat /proc/asound/card0/codec#0|grep -i codec
Codec: IDT 92HD73C1X5

```

it took me a bit to find it, but i found it on [http://www.linlap.com/wiki/dell+studio+17](http://www.linlap.com/wiki/dell+studio+17) which also links back to [http://ubuntuforums.org/showthread.php?p=6543839](http://ubuntuforums.org/showthread.php?p=6543839)

basically you need to add

```

options snd-hda-intel model=dell-m6 

```

...to the end of your /etc/modprobe.d/alsa-base file.

---

### Post by greenie9 on 2009-06-12
I am from australia, also have a Dell studio with an ATI 4570 running 9.04
(also got the intel 5300 wireless card)

to get the wireless working, go here:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1172868](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1172868)
then run this one:
[http://ubuntuforums.org/showpost.php?p=7415234&postcount=3](http://ubuntuforums.org/showpost.php?p=7415234&postcount=3)
only issue i have seen so far is that it seems to re-set itself eachtime, but am working on that at the moment 
(this also fixed my issue where i couldnt adjust the brightness)
[COLOR="Red"]EDIT: take that back, the brightness buttons seem rather moody.... sometimes work, sometimes dont[/COLOR]

also did as chammer said above with the alsa base to get sound working
[COLOR="Red"]EDIT: sound works, but hitting mute/volume keys seems to have little to no affect on the computer beep
Fixed by turning off system beep[/COLOR]

next challenge is getting drivers working, but am not likely to be able to have a look at that until sunday, but will follow the previous advice given in this thread and update here with commands that i used

---

### Post by greenie9 on 2009-06-14
discovered weird issue...
thr brightness buttons work for first minute or so after booting, then just randomly stop, its very weird...
it just flashes like it is at max/min brightness, even if it isnt

---

### Post by theBlueNibble on 2009-06-15
> **greenie9 said:**
> discovered weird issue...
thr brightness buttons work for first minute or so after booting, then just randomly stop, its very weird...
it just flashes like it is at max/min brightness, even if it isnt

i have the exact same problem.... except that the brightness control keys dont work at all not even when the system boots up. i get the same flashing icon on the right corner of the screen....thanks for any help

---

### Post by greenie9 on 2009-06-15
> **theBlueNibble said:**
> i have the exact same problem.... except that the brightness control keys dont work at all not even when the system boots up. i get the same flashing icon on the right corner of the screen....thanks for any help

mine seems extremely "moody", some times it will allow me to do it only during the boot sequence (ie loading bar), other times it will also work for a little while after logging in, other times it never works

ive found i normally keep the brightness low, simply cause i mainly use it at night, and having it on full brightness is just terrible

this is the one thing i would like to sort out, and ill be making fulltime switch to ubuntu =)

---

### Post by hypersoar on 2009-06-17
I'm having the exact same problem with adjusting the brightness with integrated graphics. I would really like a solution.

EDIT: It also seems that it recognizes when I've closed the laptop if and only if the brightness control is working.

---

### Post by jonssoni on 2009-06-18
I also bought this laptop, and I'm going to get it in July. Going to follow this thread. ;)

---

### Post by Crazy Skinny on 2009-06-19
I'm also buying this laptop. I hope we could manage to get it working 100% with 9.04 'cause I hate Vista!!!!

---

### Post by freakwit on 2009-06-24
My 1555 also has the brightness issue.  It works fine for the first minute or so, and randomly stops working...  Anybody got any progress with it?

---

### Post by bucik85 on 2009-06-26
The same problem. I saw that brightness keys didn't work after this error.

dmesg command result:
```
[  327.960053] ACPI: EC: input buffer is not empty, aborting transaction
```

---

### Post by coffeeaddict22 on 2009-06-27
Hi, 
I'm running a Studio 17 on Jaunty.  The ATI proprietary graphics drivers have a lag in them opening a new window that reminds me of another operating system, otherwise it's all good.  And I like the wobbly windows enough to put up with the wait.
 There is a BIOS update on the Dell site ([have a look on this page)]("http://linux.dell.com/projects.shtml")that might be worth a punt.

---

### Post by Grawp on 2009-06-28
So it works with latest Catalyst?
I want to buy this laptop but I have to be sure that it really works! (full 3D acceleration, HDMI/Displayport....)

---

### Post by cknight on 2009-06-28
> **coffeeaddict22 said:**
> Hi, 
I'm running a Studio 17 on Jaunty.  The ATI proprietary graphics drivers have a lag in them opening a new window that reminds me of another operating system, otherwise it's all good.  And I like the wobbly windows enough to put up with the wait.
 There is a BIOS update on the Dell site ([have a look on this page)]("http://linux.dell.com/projects.shtml")that might be worth a punt.
Just a word of caution about BIOS updates.  They seem to require Windows Vista.  I've tried many other methods to update it (without installing Vista) and all failed.  The bios flasher program is a gui executable, so freedos is out of the question too.  But I'm sure some enterprising individual out there could figure it out.  As for me I reluctantly reinstalled Vista (and what a pain that was too!) to do the bios upgrade.  So my advice to those folk getting new Studios is to keep Vista as a dual boot option.

---

### Post by shiBBy2k7 on 2009-06-30
Even registered to write that message ;)

According to the Brightness-Key issue: I found a little & dirty but working workaround for that issue but you have to recompile your kernel.


Go to your kernel sources, usually /usr/src/linux/drivers/acpi
Then edit "ec.c" and comment the following line out:
```
static int acpi_ec_transaction(struct acpi_ec *ec, struct transaction *t,
                               int force_poll)                           
{                                                                        
        int status;                                                      
        u32 glk;                                                         
        if (!ec || (!t) || (t->wlen && !t->wdata) || (t->rlen && !t->rdata))
                return -EINVAL;                                             
        if (t->rdata)                                                       
                memset(t->rdata, 0, t->rlen);                               
        mutex_lock(&ec->lock);                                              
        if (ec->global_lock) {                                              
                status = acpi_acquire_global_lock(ACPI_EC_UDELAY_GLK, &glk);
                if (ACPI_FAILURE(status)) {                                 
                        status = -ENODEV;                                   
                        goto unlock;                                        
                }                                                           
        }                                                                   
        if (ec_wait_ibf0(ec)) {                                             
                pr_err(PREFIX "input buffer is not empty, "                 
                                "aborting transaction--\n");                
                status = -ETIME;                                            
                **//goto end; **                                                

        }
        status = acpi_ec_transaction_unlocked(ec, t, force_poll);
end:                                                             
        if (ec->global_lock)                                     
                acpi_release_global_lock(glk);                   
unlock:                                                          
        mutex_unlock(&ec->lock);                                 
        return status;                                           
}
```then go to /usr/src/linux and do the following commands:

```

make oldconfig
make prepare
make

```Go away and wait ;)

After finishing (without errors) you can copy your new kernel with:
```
cp /usr/src/linux/arch/x86/boot/bzImage /boot/vmlinuz-*YOURKERNELVERSION*
cp /usr/src/linux/System.map /boot/System.map-*YOURKERNELVERSION*
mkinitrd
```As I applied my patch the EC error message still appears but brigthness can still be controlled. Also detection whether ac is plugged or not works perfectly.

Hope this helps
Regards
shiBBy2k7

PS: It would be nice, if you could give some feedback ;)
My bugreport @ Novell: [https://bugzilla.novell.com/show_bug.cgi?id=517173](https://bugzilla.novell.com/show_bug.cgi?id=517173)

---

### Post by speaker219 on 2009-07-01
> **shiBBy2k7 said:**
> 
PS: It would be nice, if you could give some feedback ;)


I love you. This fixed my brightness key issue and also my other (ACPI-related) problem where the lidbtn event would never be triggered, making the screen backlight stay on even when the lid was closed. Your patch fixed both of these issues. Thanks!

---

### Post by hypersoar on 2009-07-01
Do you know where ec.c is in Ubuntu? I'm having trouble finding it.

---

### Post by speaker219 on 2009-07-01
> **hypersoar said:**
> Do you know where ec.c is in Ubuntu? I'm having trouble finding it.

You need to install the kernel sources first:
```
sudo -s
cd /usr/src
apt-get install linux-source
tar xvf linux-source-2.6.28.tar.bz2
ln -s linux-source-2.6.28 linux
cd linux/drivers/acpi
gedit ec.c
```

---

### Post by shiBBy2k7 on 2009-07-01
> **speaker219 said:**
> I love you. This fixed my brightness key issue and also my other (ACPI-related) problem where the lidbtn event would never be triggered, making the screen backlight stay on even when the lid was closed. Your patch fixed both of these issues. Thanks!

So it was worth registering here ;)

I found out, that this fix is very close to a msi-related fix. They call it poll-forcing. Hope there'll be some better implementation in the upcoming kernelversions.

---

### Post by hypersoar on 2009-07-01
Sorry to be a n00b, but I had to install initrd-tools to run mkinitrd. When I do, it just brings up a help dialog on usage. What do I do?

---

### Post by speaker219 on 2009-07-02
> **hypersoar said:**
> Sorry to be a n00b, but I had to install initrd-tools to run mkinitrd. When I do, it just brings up a help dialog on usage. What do I do?

Use
```
update-initramfs -c -k [kernel version]
```
once you have the kernel compiled and the package installed.

---

### Post by smurflich on 2009-07-02
Hi!
Maybe this is silly problem but I hope you'll help me: 
I followed your instructions and chose a new kernel in grub, it was loading and then, I saw, instead of Desktop etc., this crap:
[IMG]http://img18.imageshack.us/img18/8931/imgp0444n.jpg[/IMG]
My previous kernel was 2.6.28-13-generic
Can you help me?


Edit: I have disabled ATI driver and it works, now I can install it again.

So thank you very much [shiBBy2k7]("http://ubuntuforums.org/member.php?u=865920"), it works pretty nice! :)

---

### Post by hypersoar on 2009-07-02
When I try to boot the laptop now, it boots into low-graphics mode, and the touchpad doesn't work. It gives me the following error:

```
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) [drm] drmOpen failed.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
(EE) intel(0): Couldn't allocate video memory
```

Furthermore, my xorg.conf file just has things like "Configured Video Device" and "Configured Monitor."

---

### Post by shiBBy2k7 on 2009-07-03
You have to reinstall your fglrx-driver after installing and booting the new kernel.

Just do it on vt0 or so.

Boot with the following parameter: init 1
Log in as root
Install fglrx again
Edit xorg.conf, that it's using fglrx
reboot & have fun

---

### Post by hypersoar on 2009-07-03
I tried reinstalling xserver-xorg-video-intel (I have integrated graphics), but it didn't help.

---

### Post by shiBBy2k7 on 2009-07-04
hmm, and you compiled the kernel version, that was running before?

maybe you have to run depmod -a

---

### Post by hypersoar on 2009-07-04
I installed linux-source, unpacked 2.6.28 and compiled it. The version I was running at the time was 2.6.28-13-generic. I'm running 2.6.28-11-generic now, which still works okay. 

Here's the output from depmod -a:

```
WARNING: Couldn't open directory /lib/modules/2.6.28.9: No such file or directory
FATAL: Could not open /lib/modules/2.6.28.9/modules.dep.temp for writing: No such file or directory
```

---

### Post by shiBBy2k7 on 2009-07-05
if you changed kernel version, you have to run:

make modules
make modules_install

Google for kernel build howto, there lots of hits

---

### Post by jonssoni on 2009-07-05
Should I install 9.04 Dell ISO or the original 9.04 Ubuntu on Studio 15?
The Studio 15 has Vista preinstalled, is it possible to install Ubuntu on the same hard disk? I would like to use both, Vista and Ubuntu.

---

### Post by Logorrhoe on 2009-07-06
It is possible to install 2 OS (Ubuntu and Vista) on the same Harddisk, Ubuntu-installer detects the partions and suggest the new layout automaticly. 

Be careful with the dell version, sometimes it means a complete roleback to OEM state (all your data will be lost)

cheers,

Logorrhoe

---

### Post by bucik85 on 2009-07-08
Check this: [http://ubuntuforums.org/showthread.php?p=7565186](http://ubuntuforums.org/showthread.php?p=7565186)

---

### Post by speaker219 on 2009-07-09
> **bucik85 said:**
> Check this: [http://ubuntuforums.org/showthread.php?p=7565186](http://ubuntuforums.org/showthread.php?p=7565186)

Can anyone confirm this is working (on the studio 1555)? Would be great if I didn't have to recompile the kernel every time ;p

---

### Post by shiBBy2k7 on 2009-07-09
You should first know what noapic disables... I think this isn't really a solution

---

### Post by dje on 2009-07-13
If anyone is having trouble with the built in microphones it is easy to fix. Right click the volume icon and select Open volume control, then click Preferences and tick Capture 1 and Capture 2 and click Close. On the Recording tab of the volume control unmute and turn up all and the microphone(s) should now be working! Tested working in Skype, Audacity and Gnome Sound Recorder

hope this helps anyone,
dje

---

### Post by Paool on 2009-07-21
hi guys

fallowing to the instructions I found here, i get the brightness keys work on my second kernel :) however... when i boot with this, i don't have any internet connection. just like there is no working wi-fi card or I don't know...

any ideas how to repair that? or what i done wrong?

and sorry for my english :)

---

### Post by speaker219 on 2009-07-21
I had to recompile the wl module from Broadcom.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Instructions are in the README. Everything worked fine for me after that :)

---

### Post by chinmaykamat on 2009-07-25
Using the dell-m6 option in /etc/modprobe.d/alsa-base.conf works for the audio. Thanks.

However, it does create one small problem. The "Mic as Output" option is no longer available. So no surround sound. :( Is there any workaround for this ? 

Thank You.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by ravisghosh on 2009-07-29
> **smurflich said:**
> Hi!
Maybe this is silly problem but I hope you'll help me: 
I followed your instructions and chose a new kernel in grub, it was loading and then, I saw, instead of Desktop etc., this crap:
[IMG]http://img18.imageshack.us/img18/8931/imgp0444n.jpg[/IMG]
My previous kernel was 2.6.28-13-generic
Can you help me?


Edit: I have disabled ATI driver and it works, now I can install it again.

So thank you very much [shiBBy2k7]("http://ubuntuforums.org/member.php?u=865920"), it works pretty nice! :)

After the first boot on my dell studio 1555 (ATI Radeon 4570), ubuntu asked me to install ATI drivers and I did, but after reboot I faced a problem similar to above wherein the screen showed white (some red/green, etc) lines and I could not boot into ubuntu. Then I booted in recovery mode and uninstalled various fglrx related packages and finally was able to get the ubuntu in GUI. 

Still many ATI related packages are installed on my system (radeontool, xserver-xorg-video-ati, xserver-xorg-video-radeon) along with xserver-video-vesa. Can someone help me find which video card is being used on my laptop, ATI or intel onboard?

How can we get the ATI Radeon 4570 card working on ubuntu? (Could we expect nOOb instructions :)

---

### Post by shiBBy2k7 on 2009-07-30
You have to reinstall your fglrx driver. Boot with the addition in the commandline: "init 1"

As boot finished log in as root and reinstall your fglrx. In SuSE there is a shell script that does that for you "fglrx-kernel-install.sh". Otherwise just rerun the setup via sh ati-......

---

### Post by ravisghosh on 2009-07-30
> **shiBBy2k7 said:**
> You have to reinstall your fglrx driver. Boot with the addition in the commandline: "init 1"

As boot finished log in as root and reinstall your fglrx. In SuSE there is a shell script that does that for you "fglrx-kernel-install.sh". Otherwise just rerun the setup via sh ati-......

Searching for "ATI" in synaptic gives the following packages (along with dev and dbg versions of the packages):
> fglrx-amdcccle
fglrx-kernel-source
fglrx-modaliases
radeontool (installed on my system)
xorg-driver-fglrx
xserver-xorg-video-ati (installed on my system)
xserver-xorg-video-mach64 (installed on my system)
xserver-xorg-video-r128 (installed on my system)
xserver-xorg-video-radeon (installed on my system)
xserver-xorg-video-radeonhd

**Which ones do I need to install for ATI 4570 on Dell studio 1555?**

Apart from the above drivers for ATI, the following video drivers are also installed. > 

xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-ark
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-fbdev
xserver-xorg-video-i128
xserver-xorg-video-intel
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-v4l
xserver-xorg-video-vesa
xserver-xorg-video-vmware
xserver-xorg-video-voodoo

**Can I safely remove these additional drivers as ATI drivers are installed? **

Sorry for the noob questions..

---

### Post by shiBBy2k7 on 2009-07-30
You have to reinstall the following packages:

xorg-driver-fglrx
or
xserver-xorg-video-ati (installed on my system)

If you're noob you should keep those video-drivers as they dont consume much space on your hdd and you should keep the proverb in mind "Never change a running system". E.g. you shouldn't delete vesa&fbdev, because they are fallback devices.

---

### Post by coderjoe on 2009-08-18
Has anybody been able to confirm that the official ATI Proprietary Driver works with the ATI Mobility Radeon HD 4570 in the Studio 15?


ATI says they do not provide laptop drivers at all and that you must speak to the OEM. The OEM says they don't make drivers and that you should talk to ATI. 
Talk about a messed up customer service experience...     


As an aside, a new version of the proprietary linux driver has been released.  [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

---

### Post by shiBBy2k7 on 2009-08-18
Especially the new catalyst 9.8 works like a charm here :)

---

### Post by mvartic on 2009-08-22
Hello.
I'm planning to buy a Dell Studio 1555 with ATI Mobility Radeon 4570.
Can somebody confirm if :

1. The latest ATI drivers work well in Ubuntu 9.04?
2. There are some major issues in Ubuntu 9.04 for this notebook?

I'm asking this because at the moment I'm using an Inspiron 1501 the has the no-longer-supported-by-ATI Radeon Xpress 1150, and I would like to buy a laptop that works well in Unbuntu 9.04.
Thanks a lot,
Regards

---

### Post by shiBBy2k7 on 2009-08-22
Don't know if the latest catalyst works properly with ubuntu but with opensuse 11.1 it does.

Other issues are the problem with the brightness control, which can be easily workaround and the soundcard, but there's also a fix.

---

### Post by tyk on 2009-08-29
Hi I bought an ASUS K40AB with this card (Ati Radeon 4570). It seems the catalyst9.8 (version 8.632) doesn't yet play with this card. I found [this]("http://forums.amd.com/game/messageview.cfm?catid=260&threadid=117112&enterthread=y") on the AMD gaming forum where people are having trouble with windows as well, umm at least windows 7 64 bit.
For my part, I tried:
1. Jockey to get fglrx from the 'buntu repos
2. created 9.04 debs from the downloaded driver package from ati and
3. directly ran the downloaded catalyst 9.8

In all, no joy yet. It seems there is a wait involved. Some of you are saying that it works in Suse. How exactly? And is it the same card and driver as I mention? Any more info on this will be appreciated.

---

### Post by shiBBy2k7 on 2009-08-29
I use this driver:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-8-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-8-x86.x86_64.run)

I build a RPM-Package out of it (similar to ubuntu's debs) and install. Maybe you should deinstall your debs before installing the driver directly from the package. Also check if your xorg.conf is set up correctly, especially that driver fglrx is used.

You could post your modinfo of fglrx and (if existand) error messages.

---

### Post by tyk on 2009-08-30
Thanks for the reply. I am downloading it right now.. I must say, though that it looks like the one i already tried. 
Also, i not only uninstalled the deb packages, i reinstalled 'buntu coz X was borked really. This was repeated for each of the methods. To be sure, when I directly ran the package and rebooted, fail-safe X did start up. I replaced xorg.conf with the backup I'd made and then it again borked. Had to restart using Alt+PrtScr+RSEINUB.. and then reinstall.
The failsafe X did give out an error message, 3 in fact, and at least 2 had to do with BIOS something or the other. One time when i installed xorg-driver-fglrx from the repos, then I did get another failsafe screen which said that this driver 'fglrx' does not support this depth 8 or thereabouts. I am totally regretting not writing this down but it was 3am and i just wanted to plow through it i guess.
Now I have it running on newly installed 9.04 system with the default driver. Would really like to have my ati working though.
Cheers.

---

### Post by shiBBy2k7 on 2009-08-30
Did u run aticonfig --initial ?

Seems like your xorg.conf is false. Also try to start sax2 from vt0, it should repair your xorg.conf.

Or you could post your xorg.conf after installing fglrx.

---

### Post by tyk on 2009-08-30
Hi ShiBBy2k7
I ran aticonfig --initial and then when X borked, aticonfig --initial -f too. Post these it was the BIOS error (again I wish I had noted it down).. I also tried one version of xorg.conf with simlpy Driver "fglrx" in the Device section. I think thats when it gave me the depth error.
And I dont know of sax2 and vt0. I mean i'm not exactly a noob but neither am i qualified in computers really. Its just what I've learnt here and there, well mostly here :)
So what are these things? You could link to some tuts etc. I can go through them. As far as posting a borky xorg.conf, now thats gonna be a bit difficult coz
1. This is on my new lappy and I need it for out of town work starting tomorrow.
2. I really really don't wanna scr@#$ it up again, you know. Right now i got my old desktop for any opengl stuff and i'll bear with not having opengl on the lappy for a few days.. but wanna get it right. 
Thanks anyway,
cheers.

---

### Post by shiBBy2k7 on 2009-08-30
On a linux system u have several (6) consoles, which can be accessed with ctrl+alt+f1-6. On f7-11 are normally your x sessions. on f12 there is a debug-console.

If your x server is broken you can try to fix it following these steps:

Reboot and wait for grub bootloader. Add "init 1" to the commandline, which boots your system in administrative mode without any x-server. Now you can log on as root with your root-pw. To see which errors make X fail you can simply run "X". Otherwise you could run sax2, which (hopefully) fixes your xorg.conf. Your xorg.conf lies in /etc/X11/xorg.conf

Here is my xorg.conf:

```


# /.../
# SaX generated X11 config file
# Created on: 2009-06-27T15:32:17+0200.
#
# Version: 8.1
# Contact: Marcus Schaefer <sax@suse.de>, 2005
# Contact: SaX-User list <https://lists.berlios.de/mailman/listinfo/sax-users>
#
# Automatically generated by [ISaX] (8.1)
# PLEASE DO NOT EDIT THIS FILE!
#

Section "ServerLayout"

    #Option        "Clone" "off"
    Identifier     "Layout[all]"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    InputDevice    "Keyboard[0]" "CoreKeyboard"
    InputDevice    "Mouse[1]" "CorePointer"
    InputDevice    "Mouse[3]" "SendCoreEvents"
    Option        "Xinerama" "off"
    Option        "AIGLX" "off"
    #Option        "RandR" "off"
EndSection

Section "Files"
    InputDevices   "/dev/gpmdata"
    InputDevices   "/dev/input/mice"
    FontPath     "/usr/share/fonts/misc:unscaled"
    FontPath     "/usr/share/fonts/local"
    FontPath     "/usr/share/fonts/75dpi:unscaled"
    FontPath     "/usr/share/fonts/100dpi:unscaled"
    FontPath     "/usr/share/fonts/Type1"
    FontPath     "/usr/share/fonts/URW"
    FontPath     "/usr/share/fonts/Speedo"
    FontPath     "/usr/share/fonts/PEX"
    FontPath     "/usr/share/fonts/cyrillic"
    FontPath     "/usr/share/fonts/latin2/misc:unscaled"
    FontPath     "/usr/share/fonts/latin2/75dpi:unscaled"
    FontPath     "/usr/share/fonts/latin2/100dpi:unscaled"
    FontPath     "/usr/share/fonts/latin2/Type1"
    FontPath     "/usr/share/fonts/latin7/75dpi:unscaled"
    FontPath     "/usr/share/fonts/baekmuk:unscaled"
    FontPath     "/usr/share/fonts/japanese:unscaled"
    FontPath     "/usr/share/fonts/kwintv"
    FontPath     "/usr/share/fonts/truetype"
    FontPath     "/usr/share/fonts/uni:unscaled"
    FontPath     "/usr/share/fonts/CID"
    FontPath     "/usr/share/fonts/ucs/misc:unscaled"
    FontPath     "/usr/share/fonts/ucs/75dpi:unscaled"
    FontPath     "/usr/share/fonts/ucs/100dpi:unscaled"
    FontPath     "/usr/share/fonts/hellas/misc:unscaled"
    FontPath     "/usr/share/fonts/hellas/75dpi:unscaled"
    FontPath     "/usr/share/fonts/hellas/100dpi:unscaled"
    FontPath     "/usr/share/fonts/hellas/Type1"
    FontPath     "/usr/share/fonts/misc/sgi:unscaled"
    FontPath     "/usr/share/fonts/xtest"
    FontPath     "/opt/kde3/share/fonts"
EndSection

Section "Module"
    Load  "dri"
    Load  "dbe"
    Load  "freetype"
    Load  "extmod"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "AllowMouseOpenFail" "on"
    Option        "ZapWarning" "off"
    Option        "Xinerama" "off"
    Option        "AIGLX" "off"
    #Option        "RandR" "off"
EndSection

Section "InputDevice"
    Identifier  "Keyboard[0]"
    Driver      "kbd"
    Option        "Protocol" "Standard"
    Option        "XkbLayout" "de"
    Option        "XkbModel" "microsoftpro"
    Option        "XkbRules" "xfree86"
    Option        "XkbVariant" "nodeadkeys"
    #Option        "XkbOptions" ""
EndSection

Section "InputDevice"
    Identifier  "Mouse[1]"
    Driver      "mouse"
    Option        "Buttons" "5"
    Option        "Device" "/dev/input/mice"
    Option        "Name" "Dell USB Mouse"
    Option        "Protocol" "explorerps/2"
    Option        "Vendor" "Sysp"
    Option        "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier  "Mouse[3]"
    Driver      "synaptics"
    Option        "Buttons" "5"
    Option        "Device" "/dev/input/mice"
    Option        "Emulate3Buttons" "on"
    Option        "HorizScrollDelta" "0"
    Option        "InputFashion" "Mouse"
    Option        "Name" "Synaptics;Touchpad"
    Option        "Protocol" "explorerps/2"
    Option        "SHMConfig" "on"
    Option        "Vendor" "Sysp"
    Option        "ZAxisMapping" "4 5"
EndSection

Section "Modes"
    Identifier     "Modes[0]"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"

    #Option        "Mode" "1920x1080"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "TexturedVideo" "on"
    Option        "OpenGLOverlay" "off"
    Option        "VideoOverlay" "off"
    Option        "Textured2D" "on"
    Option        "TexturedVideoSync" "on"
    Option        "UseFastTLS" "1"
    Option        "TexturedXRender" "off"
    #Option      "XAANoOffscreenPixmaps" "on"
    Option        "DesktopSetup" "horizontal"
    #Option        "EnableRandR12" "false"
    Option        "UseInternalAGPGART" "on"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Group        "video"
    Mode         0666
EndSection

Section "Extensions"

    Option       "DAMAGE" "on"
    Option        "Composite" "off"
    #Option        "XVideo" "on"
    Option       "RENDER" "on"
EndSection

```

Remind that I own a Dell Studio 1555 with a 1920x1080 display.

---

### Post by tyk on 2009-08-30
That's very nice of you, shiBBY2k7. i've never seen such an xorg.conf. I will go through it at length. And thanks for the explanation too. I understand this is what's called 'runlevels'?
Have to rush now. But will post back soon.
Cheers.

---

### Post by cgarre on 2009-08-31
Can someone please compile the issues for Dell Studio 1555, with Mobility Radeon HD 4570 , and i am wondering if compiz runs on it.

---

### Post by cos85 on 2009-08-31
So, does this laptop/card work with the proprietary drivers or not?
I can see the 9.8 driver can support the HD 4550, but don't specifically see the HD 4570...

Would you say this is a good laptop to put Linux on?

---

### Post by pfanne on 2009-09-04
my dell works pretty much perfectly...
suspend/resume works.
with the noapic option brightness works for now.
with the fglrx driver issues you will have to life ;) (but they arent that big + the open source driver is leaping to a usable state)

---

### Post by fixxxer50 on 2009-09-06
Hi guys. I am planning to buy this laptop, can anyone give me any feedback on if the ATI driver is available for ubuntu for HD4570 and how the performance is. Also there is a Dell dvd available, do you guys think it is a better idea to use that for installing ubuntu. 

[http://ubuntuforums.org/showthread.php?t=1141757](http://ubuntuforums.org/showthread.php?t=1141757)

[http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

---

### Post by tyk on 2009-09-06
> **pfanne said:**
> my dell works pretty much perfectly...
suspend/resume works.
with the noapic option brightness works for now.
with the fglrx driver issues you will have to life ;) (but they arent that big + the open source driver is leaping to a usable state)

When?

---

### Post by andrek on 2009-09-06
Speaking of ubuntu compatibility, my dell 1555 works flawlessly with ubuntu 9.10 alpha 5. 3d acceleration works now almost out-of-box ( just install fglrx driver or use hardware drivers app ). Adding noapic to grub config makes changing brightness easy.

Haven't tested the webcam yet, though.

---

### Post by myk02k on 2009-09-10
Hey guys, I also have a Mobility Radeon HD 4570, but within my Toshiba Satellite A505.  I am currently running the fglrx driver installed from jockey-gtk, although there seems to be several different bugs I'm experiencing (X confusing desktop borders, system hangs, compiz segfaults, etc).

Do you guys really have the Radeon 4570 running with no issues using the fglrx drivers?  Is there instructions here that apply to the A505 as well?  My notebook is relatively new and does not have as much popularity as the Dell Studio, though any advice may help us fellow Radeon 4570 users.

---

### Post by tyk on 2009-09-20
Hi has anybody tried the catalyst 9.9 driver from ati? It was released recently but still doesn't mention the hd4570 as a supported card per se..

---

### Post by GuilouV on 2009-09-24
Sorry to disturb you with an Opensuse 11.1 question but I never find any response in other forums.

I have an Opensuse 11.1 + ati radeon hd4570. Using free driver my resolution cannot go over 1024x768 even if my screen supports 1366x768. So I installed catalyst 9.9 but it appears that now moving windows and using firefox are lagging. Have you got any idea about this? You are my last hope or I cannot use my new pc (dell 1555).

Sorry for my english (I am french).

---

### Post by xourge on 2009-09-25
i compared my xorg.conf with shiBBY2k7's
apparently the solution was to comment the line with horiz sync and vert sync 
now i have my ati working properly at 1920x1080 :)

---

### Post by GuilouV on 2009-09-25
Thanks for your reply. After 1 week of research I finally find the solution by myself. So I put it here, it seems to be necessary as I can see on forums.
I remember that is working on a Dell 1555 with Opensuse 11.1 and a radeon hd 4570.

1/ Install linux-kernel-headers package
Reboot

2/ Install DKMS (for Dell laptop users only)
Reboot

3/ Create Posix Shared Memory by adding this line in /etc/fstab:
*tmpfs   /dev/shm   tmpfs   defaults   0 0*
Reboot

4/ Install all these packages in 32bits (for 32bits system) and in 32 **_and_** 64bits (for 64bits system). Install also devel corresponding packages if existing:
*# glibc # libstdc++ # libgcc # fontconfig # freetype # zlib # gcc # qt3 # compat # xorg-x11-libs # xorg-x11-devel # Mesa **# MesaGLw *[I]# expat # freetype2 # zlib # libdrm
[/I]Reboot

5/ Install ATI driver (from here: [http://en.opensuse.org/ATI_Driver_HOWTO](http://en.opensuse.org/ATI_Driver_HOWTO))
Reboot

6/ Add this to your xorg.conf:
In device section:[I]
Option "OpenGLOverlay" "off"
Option "VideoOverlay" "on"
[/I]In extensions section:
*Option "Composite" "off"*
Log off

7/ In superuser, make:[I]
init 3
sax2 -r -m 0=fglrx
init 5[/I]

---

### Post by xourge on 2009-09-27
excuse me but turning Composite Extension Off wouldn't disable compiz effects?

---

### Post by GuilouV on 2009-09-28
I think so, but in my case I am using LXDE so it does not matter. But perhaps it would be work with *Composite on*...

---

### Post by mahantya on 2009-10-21
> **GuilouV said:**
> 

6/ Add this to your xorg.conf:
In device section:[I]
Option "OpenGLOverlay" "off"
Option "VideoOverlay" "on"
[/I]In extensions section:
*Option "Composite" "off"*
Log off

7/ In superuser, make:[I]
init 3
sax2 -r -m 0=fglrx
init 5[/I]

Well I ran into this very issue and did go as per the openSUSE HOWTO page but the last step i.e. **sax2 -r -m 0=fglrx** would render my screen blank so instead I configure the driver using 

**aticonfig --initial**

Works for me. I'm able to run using 1920x1080 and Compiz desktop effects work fine too. I've provided all the steps here:
[https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/dell-studio-1555-ati-radeon-4570-opensuse-11.1-64-bit-compiz-desktop-effects-763563/]("https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/dell-studio-1555-ati-radeon-4570-opensuse-11.1-64-bit-compiz-desktop-effects-763563/")

---

### Post by GuilouV on 2009-10-23
Proposed installation on Opensuse HOWTO has evolved and is much easier now.

This problem is solved but another remains. I can not used my brightness multimedia buttons, have you a suggestion about this?

---

### Post by pkl on 2009-12-02
Thank you all for this very useful thread. 
I have the same Laptop, Dell Studio 15 with **512 Mb ATI Radeon HD 4570** in which I am running **Ubuntu 9.04 64 bits.** I've also rectified the sound, brightness-key problems by following this thread. Everything was fine.

But, I noticed an **updated driver for ATI released on 11/17/2009** in [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx).

*Now the problem is that after installing the above driver I cannot enable compiz, video becomes  jerky and choppy, and is even more in full screen mode* while there has been an improvement in the clarity of text which was not so before.

Please help.

---

