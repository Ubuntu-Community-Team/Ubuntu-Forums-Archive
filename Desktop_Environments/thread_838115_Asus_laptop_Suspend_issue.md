---
title: "Asus laptop Suspend issue"
date: 2008-06-23
forum: Desktop Environments
---

### Post by olaf_nz on 2008-06-23
Hi there

I have installed Ubuntu 8.04 a couple of days ago and everything was very painless. In fact it is all fantastic, except when I try to suspend (haven't tried hibernate as I've heard its dicey).

Suspending appears to work fine, but when I try to restart, the laptop makes noises, the hard disk flashes and the optical mouse lights up... and nothing more.

I have looked around the forums, and played a little with my /etc/defaults/acpi-support file - separately, and together, but with no noticeable improvement, I have changed:
# ACP ACPI_SLEEP_MODE=mem
ACPI_SLEEP_MODE=standby

# ACP SAVE_VBE_STATE=true
SAVE_VBE_STATE=false

# ACP POST_VIDEO=true
POST_VIDEO=false

Does anybody please have some more suggestions for me?

I am running an Asus Z92U (Z9200), which among other things is a Turion 64 with around 1 Gig RAM, SI7012 sound, but I'm not sure what graphics (how do I detect under Linux?). I am running the AMD 64-bit desktop edition of Ubuntu.

Thanks in advance,
Anton

---

### Post by olaf_nz on 2008-06-23
I since tried hibernate. Strangely, it mostly works, although my USB disk drive requires unplugging and replugging.

No joy on the suspend yet, though.

---

### Post by blueturtl on 2008-06-25
To see what hardware you have you can use the command 'lspci' without the ' in a terminal (you can find Terminal in the Applications->Accessories menu). Among the listed hardware should be your video card.

This is the support page for your particular laptop:
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U](https://wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U)

According to this page your laptop has a Sis video card.
I have a completely different laptop but for me the following changes in /etc/default/acpi-support did the trick:

SAVE_VBE_STATE=false
USE_DPMS=false
POST_VIDEO=false

You can always give those a shot. It worked for me with an Ati video card.

---

### Post by olaf_nz on 2008-06-25
Hi blueturtl

Thanks for your reply. I had been to the support page for my laptop, but it didn't seem to mention any suspend issues (although I haven't had my camera working yet, as it says). There's no specific forum for my laptop, is there?

Thanks for the tip about the lspci. It does certainly appear to be SiS hardware:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
00:0a.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Anyway, I have tried those settings you've suggested with no noticeable improvement, but thank you for the ideas anyway.

I've also flashed my BIOS to the latest, which also didn't do anything for me.

I hope somebody somewhere has an idea - it's not exactly a show-stopper, but it's definitely part of my habit to suspend rather than shutdown every night.

---

### Post by blueturtl on 2008-06-25
Did you also try: USE_DPMS=false ? You didn't list that one in your original post.

Just to rule out the obvious, the settings will be applied only after you have rebooted, so have you tried that?

Apparently the issue has to do with the video card on your laptop not having any dedicated memory of it's own. My Ati video has the same issue, so it should not be a showstopper.

When the support page was last updated there was no particular driver for your video card, so the generic VESA one was used instead. I wonder if that is still the case with Ubuntu 8.04.

I remember stumbling over a suspend option for VESA card somewhere in the video configuration file (xorg.conf), but I don't have it handy. I will post again when I find the option so you can try that one as well.

---

### Post by olaf_nz on 2008-06-26
Hi there

Yes, I did try:
USE_DPMS=False

So far the full list I have (of altered settings):
ACPI_SLEEP_MODE=standby
SAVE_VBE_STATE=false
POST_VIDEO=false
USE_DPMS=false
DOUBLE_CONSOLE_SWITCH=true

I was not aware that I had to restart after altering this file, so I tried that, but it seems to not have had an effect either, unfortunately.

Do you think it may be worth installing a generic VESA driver or other protected driver for my card and if so, how would I go about this?

Thanks again,
Anton

---

### Post by blueturtl on 2008-06-26
If you're currently using the Sis driver, it's probably better to keep it. The VESA driver gives you worse performance!

If you are using the VESA driver, this option might do the trick:
```
acpi-support:

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

```

Another thing to try:
You could restore all the changes made and try just the ones I've listed (and of course reboot before trying to suspend).

Yet another thing I found:
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

I haven't tried, but it might be worth a shot.

edit: Everywhere I look, people are complaining about Sis graphics under Linux. Don't loose any sleep over this, there's a good chance it simply does not work at the moment!

---

### Post by DavidFourer on 2008-06-26
I'm trying to find a consolidated suspend thread.  There was one in the archives but I think there should be a current one.  Can we get all the suspend stuff into one place, one search?  
My suspend issue: 
I noticed my Dell Inspiron 6000 does something about 3 hours after suspend.  If I resume in less than 3 hours, it's fine.  If I resume after 3 hours,  I hear a screech from the audio, login is normal, and I get the warning box "Your computer failed to suspend" in the lower right of my screen.  Resume works, but Is the CPU running while I think it's sleeping?  In my readings I have not found any comments explaining the warning box.  What's the audio screech?

---

### Post by olaf_nz on 2008-06-27
Hmm, I'm not sure what you're meaning there... if the VESA driver might allow me to suspend, then that would be preferable to me as long as performance isn't absolutely terrible.

Either way, it's pretty important to me to have this work.

I've tried to install the uswsusp:

I tried both using the gui package manager and using:
sudo apt-get install uswsusp

and I got a message saying it couldn't find the swap file listed in its configuration and was this ok? I tried both yes and no at different times, but I end up without s2ram - from terminal typing "sudo s2ram" says it can't find it.

So firstly, where is the configuration file to set up to point to my swap file? (I ran "free | grep Swap" to test and it came up with some numbers not 0 0 0, so that means my swap file is ok, right?)

Secondly, why, when it is installed, can it not run?

Thanks,
Anton

---

### Post by blueturtl on 2008-06-30
To find out which driver you are using for the video card open the video configuration file (xorg.conf) in an editor:

```
sudo nano /etc/X11/xorg.conf
```

From the configuration file locate the entry for your video, on my system it looks like this:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection
```

If the driver part says something other than 'vesa' you're probably using an optimized driver. You can try changing it to vesa but there is a risk that after rebooting the system will not start in graphical mode. In that case simply changing the file back the way it was should do. Wise users do backups of their configuration files.

> I got a message saying it couldn't find the swap file listed in its configuration and was this ok? I tried both yes and no at different times, but I end up without s2ram - from terminal typing "sudo s2ram" says it can't find it.

If you're trying to suspend, you won't need to save anything to the disk so it's ok that swusp doesn't know the swap file location.

To try and locate s2ram type ```
which s2ram
``` in a terminal.
It should give you the path to the file, you can then try running it like this: 

```
sudo /path/to/s2ram
```

As far as the USWUSP package goes, I have not used it myself so I don't know what the problem with it might be. The advice I'm giving is based on educated guesses.

> So firstly, where is the configuration file to set up to point to my swap file? (I ran "free | grep Swap" to test and it came up with some numbers not 0 0 0, so that means my swap file is ok, right?)

Secondly, why, when it is installed, can it not run?

For these questions I suggest taking a look at the program's manual.
Do this by issuing a

```
man s2ram
``` or ```
man uswusp
```

edit:

To quit the editor nano, hit Ctrl+X (if you've edited a file first hit y and then enter to save the changes).

If you're viewing a man page, simply hit Q to quit and return to the command line.

---

### Post by olaf_nz on 2008-07-02
Hi there

Thanks for your patience in keeping going with this...

I've looked at my xorg.conf - there doesn't appear to be anything specific configured, so I'm unsure if it's just autodetecting each time or what?

[FONT="Arial Narrow"]-----------------------
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
-------------------------[/FONT]

So if I add:
[FONT="Arial Narrow"]Driver          "vesa"[/FONT]

Something may or may not happen?

As far as uswsusp goes, it is listed as installed in my package manager, however, the "which s2ram" command has no result, even if I change back to /. However, from "man which" it appears that "which" will only find things that are in the path to execute anyway - is this correct? How else can I search for the file, or where is it likely to be installed? I see that s2both and s2disk are in /sbin. Is it possible that I require a different version of uswsusp? (I have 0.6, cvs20070618 which doesn't seem that recent - 0.8 is available on [http://suspend.sourceforge.net/download.shtml](http://suspend.sourceforge.net/download.shtml) but I'm not sure how to install that without interfering with my package manager).

I will try s2disk and s2both after finishing this post. Of course they will then require the swap file to be correctly configured I assume.

Thanks again,
Anton

---

### Post by blueturtl on 2008-07-02
Hi again.

My guess is that since your video entry in xorg.conf is pretty much unspesified, X is falling to the VESA graphics by default. That said I don't see any harm in spesifying VESA spesifically, you can try it. Make your entry look like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection
```

After rebooting you can once again try the default suspend method.

After looking at uswusp it looks like the package in the repositories might not contain s2ram. My mistake, however it should be in a newer package. You provided the link already, but here it is anyway:
[http://sourceforge.net/project/showfiles.php?group_id=45483](http://sourceforge.net/project/showfiles.php?group_id=45483)

If you wish to install a newer version of uswusp / Linux suspend, you will probably have to manually compile it. Usually this is no harder than extracting the downloaded .tar.gz file, then entering the directory in a terminal and giving the commands:

```
./configure
make
sudo make install
```

However sometimes the procedure deviates from the standard (you might not need to enter ./configure for example). Check the readme file included for installation instructions.

Now you're worried about what this might do to the package management. I've used a tool called checkinstall (you can get via apt-get) that replaces the final step in these compilation procedures. What it does, is generate a deb package of the files you're about to install, so that the package manager can be aware of the installed app. It also allows for easy removal of a self-compiled programs via Synaptic. All you have to do, is replace the final step in compilation so that instead of this:

```
sudo make install
```
it looks like this:
```
sudo make checkinstall
```

Obviously remove the old uswusp package before installing your own version to avoid conflicts.

Let me know how this goes. I'm gonna run out of ideas soon, but at least we've given it our all eh? :)

---

### Post by blueturtl on 2008-07-02
Oh hey, also could you please post the output of the command after suspend has failed:

```
dmesg | tail -20
```

There might be something helpful there.

Let's also look in /var/log/pm-suspend.log

---

### Post by olaf_nz on 2008-07-02
Ok, I added the "vesa" entry to my xorg.conf. When I rebooted it was obviously different, as 800x600 was the top resolution choice (640x480 being the only other one). Suspend still did not work, however I didn't try too many options as 800x600 is obviously unacceptable.

My dmesg output is below:
-----------------------------
pippin@Pippin:~$ dmesg | tail -20
[   50.869247] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MT-30 processors (1 cpu cores) (version 2.20.00)
[   50.869284] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0xe
[   50.869287] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1a
[   51.874387] ppdev: user-space parallel port driver
[   52.133281] audit(1214997174.045:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5016 profile="/usr/sbin/cupsd" namespace="default"
[   54.131132] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   54.311823] Clocksource tsc unstable (delta = -249998269 ns)
[   54.373882] Bluetooth: Core ver 2.11
[   54.377864] NET: Registered protocol family 31
[   54.377868] Bluetooth: HCI device and connection manager initialized
[   54.377872] Bluetooth: HCI socket layer initialized
[   54.517348] Bluetooth: L2CAP ver 2.9
[   54.517353] Bluetooth: L2CAP socket layer initialized
[   54.639238] Bluetooth: RFCOMM socket layer initialized
[   54.639253] Bluetooth: RFCOMM TTY layer initialized
[   54.639256] Bluetooth: RFCOMM ver 1.8
[   55.499924] NET: Registered protocol family 17
[   58.545849] NET: Registered protocol family 10
[   58.546243] lo: Disabled Privacy Extensions
[   63.768350] eth0: no IPv6 routers present
---------------------------

My var/log/pm-suspend.log is below:
---------------------------
Wed Jul  2 23:10:32 NZST 2008: running suspend hooks.
===== Wed Jul  2 23:10:32 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Wed Jul  2 23:10:32 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Wed Jul  2 23:10:32 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Wed Jul  2 23:10:32 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Wed Jul  2 23:10:33 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Wed Jul  2 23:10:33 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Wed Jul  2 23:10:33 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Wed Jul  2 23:10:35 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Wed Jul  2 23:10:35 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Wed Jul  2 23:10:35 NZST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Wed Jul  2 23:10:35 NZST 2008: done running suspend hooks.
-------------------------

Hope that is what you're after. I copied those directly after restarting (hold down power button for 5 seconds) following suspend failure.

I can press CAPS lock when the resume has failed, so presumably that helps confirm that it is a video issue?

I'm learning lots anyway... regarding compiling that package... I get the following:

-------------------------------
pippin@Pippin:~/suspend/suspend-0.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
-------------------------------

I attempted to do it as sudo, in case it was a rights issue, but it's the same. Why is gcc not able to create executables?

---

### Post by blueturtl on 2008-07-02
Sorry about the compile thing, I completely forgot you probably don't have the necessary utilities installed. Install all the essential compiling tools by entering

```
sudo apt-get install build-essential
```

After that in the same directory you were trying to compile type

```
make clean
```
(sudo maybe necessary, if you tried ./configure with sudo instead)

Now you should be able to compile the package without errors.

---

### Post by blueturtl on 2008-07-02
> Ok, I added the "vesa" entry to my xorg.conf. When I rebooted it was obviously different, as 800x600 was the top resolution choice (640x480 being the only other one). Suspend still did not work, however I didn't try too many options as 800x600 is obviously unacceptable.

My dmesg output is below:
...

My var/log/pm-suspend.log is below:
...

So removing the vesa driver reference you're able to boot with a better resolution then? Just out of curiosity, you could try and see what happens if instead of 'vesa' you spesify the driver as 'sis'. Should the system hang while booting, hit the esc key the next time right before the system boots and then from the boot menu select the 'Safe mode' option. This will allow you to log into a text mode console and restore your original xorg.conf.

Not really sure what I'd be looking for in your system logs, but nothing to me seems out of the ordinary.

Btw. if you're worried about your file system with all this power-down without properly shutting off, you can use the following command to force a file systems check on the next boot:

```
touch /forcefsck
```

One thing of interest is that caps lock seems to respond. That may mean the system is not really locked up, but the monitor for whatever reason is not displaying anything.

Next time the system is in this "locked up" state, you could try entering another terminal by holding down the keys Ctrl + Alt + F1 (can be any key between F1 and F7). Also Ctrl+Alt+Backspace is supposed to restart the X server so you can try that as a last resort also (though this will close all the programs you may have had open in your session).

---

### Post by olaf_nz on 2008-07-03
I haven't tried the second posting yet, just trying to get uswsusp installed...

I installed the build-essential tools with no sweat, and now ./configure gets much further (make clean didn't work ("make: *** No rule to make target `clean'.  Stop.") so I just plunged onwards).

The final line in the configure is:
"configure: error: Required pciutils >= 2.2.4 not found"

I looked for pciutils and it appears I have 1:2.2.4-1.1ubuntu4, which looks ok to me.

---

### Post by olaf_nz on 2008-07-03
Specifying the driver as "sis" appears to have no change, so I assume that's what drivers I was using anyway (max resolution, etc all appear to be normal).

I tried suspending, both with all the acpi modifications and then back to the original file, but no real improvement. Ctrl-F1, etc don't bring up a text-mode terminal, and Ctrl-Alt-Bksp does nothing either. I'm sure when I tried suspend the very first time, my (optical) mouse at least lit up, but it hasn't through all these things I've being trying. Sometimes the hard disc light comes on and sometimes not, but no real change.

I'm keen to press on on the s2ram function, though, as I tried the s2disk, and despite a few weird mode changing artifacts (vertical bars, scrunched up ubuntu logos, etc) it seemed to come back ok (although I didn't use it much to see if the USB hard disk, etc had come back ok). But it gives me hope that s2ram might work if we can get it going.

---

### Post by blueturtl on 2008-07-03
> The final line in the configure is:
"configure: error: Required pciutils >= 2.2.4 not found"

I looked for pciutils and it appears I have 1:2.2.4-1.1ubuntu4, which looks ok to me.

When a configure script complains of a package missing, it actually means the equivalent development package (ie. the package with the source code to the component that you have installed).

You can find the development packages for practically everything in the repository by appending the -dev to the end of the name of the package you're looking. So in this case the package you'd be looking for is

pciutils-dev (1:2.2.4-1.1ubuntu4). Try installing that and then see if the configure script passes.

edit: I'm actually holding my breath in here to see how this goes. Getting that suspend thing to actually work would be a big thing after all that's gone into it. :)

---

### Post by olaf_nz on 2008-07-07
Just an update because I fear you must be getting rather blue in the face from holding your breath!

I managed to install the s2ram utility (although it didn't seem to work with the checkinstall I got it running just with install). There are multitudonous settings that seem roughly analogous to the ones we tried in the acpi config file. The reason its taken me a while to reply is that it takes a while to try each setting, and in fact I've only tried about a quarter of the combinations so far, unfortunately with no improvement.

So I'll keep trying all those and if all else fails, use the s2disk utilities.

Thanks heaps for your help, anyway. I've learned heaps in any case as to where various files and settings are located, etc.

---

### Post by blueturtl on 2008-07-08
> Thanks heaps for your help, anyway. I've learned heaps in any case as to where various files and settings are located, etc. 
Sure thing. Just trying to give the kind of advice I wish I'd gotten when I was n trouble (and in many cases did). Helping others after you learn is what has made Ubuntu such a great system. Hope you get a chance to do the same for someone else.

If you ever do find a solution, post it here and mark the thread solved so others can benefit.

I will post again if I can think of something that might help you. Good luck Ubuntuing!

---

