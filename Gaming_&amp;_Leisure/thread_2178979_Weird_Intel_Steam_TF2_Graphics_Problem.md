---
title: "Weird Intel Steam TF2 Graphics Problem"
date: 2013-10-06
forum: Gaming &amp; Leisure
---

### Post by muddpup64 on 2013-10-06
I installed Team Fortress Two on my T410 Lenovo laptop. The game itself works fine but the graphic aren't doing so well. I have found some resoucres ([here]("http://forums.steampowered.com/forums/showthread.php?t=3108479")) but the launch option didn't seem to change anything, might be because I didn't do it right, I don't know. (A pic of the main menu is attached to this thread.) Furthermore, I have run Team Fortress on another laptop, using the hard drive from my T410, and it ran perfectly.

If anybody has any ideas on the problem it would be a big help to me.

---

### Post by snafu006 on 2013-10-06
> **muddpup64 said:**
> I installed Team Fortress Two on my T410 Lenovo laptop. The game itself works fine but the graphic aren't doing so well. I have found some resoucres ([here]("http://forums.steampowered.com/forums/showthread.php?t=3108479")) but the launch option didn't seem to change anything, might be because I didn't do it right, I don't know. (A pic of the main menu is attached to this thread.) Furthermore, I have run Team Fortress on another laptop, using the hard drive from my T410, and it ran perfectly.

If anybody has any ideas on the problem it would be a big help to me.


i am guessing your video card. next time need more system info.

Video chipsets: 
[LIST]
[*]Intel HD Graphics 
[*]256MB NVIDIA® Quadro® NVS3100M 
[/LIST]
**Notes:**

[LIST]
[*]Support for a external monitor is through VGA DB-15 connector 
[*]Support for digital monitor via DisplayPort (supports single-link DVI-D via cable 45J7915) 
[*]Maximum   external resolution: 2560x1600 (DisplayPort)@60Hz; 2048x1536   (VGA)@75Hz; 1920x1200@60Hz (single-link DVI-D via cable 45J7915 
[*]All displays are measured diagonally. 
[/LIST]

Did you ever install the Video drivers for Nvidia if thats what the laptop has.

if you have intel then instll the official intel drivers here.
[B][Official Intel Linux Graphics Installer Available For Ubuntu 13.04]("http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html")
[http://www.webupd8.org/search?updated-max=2013-09-09T16:38:00%2B03:00&max-results=10&start=10&by-date=false](http://www.webupd8.org/search?updated-max=2013-09-09T16:38:00%2B03:00&max-results=10&start=10&by-date=false)[/B]

This link is the main download page.
[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)

---

### Post by snafu006 on 2013-10-06
oh and you need this as well it help with some thinkpads power management.
**[COLOR=#ff0000]ONLY USE THIS IF YOU ARE ON UBUNTU 12.04 [/COLOR][COLOR=#000000][/COLOR]**
But you maybe able to us this on up to 13.04. 

[http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)


There are various tweaks that you can apply to your laptop to save  battery power, but many of them depend on the hardware, Linux  distribution, some are outdated or too hard to apply for regular users  and so on. **[TLP]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html")  is an advanced power management command line tool for Linux that tries  to apply these settings / tweaks for you automatically, depending on  your Linux distribution and hardware**.

**TLP applies the following settings depending on the power source (battery / ac):**

[LIST]
[*]Kernel laptop mode and dirty buffer timeouts; 
[*]Processor frequency scaling including "turbo boost" / "turbo core"; 
[*]Power aware process scheduler for multi-core/hyper-threading; 
[*]Hard disk advanced power management level and spin down timeout (per disk); 
[*]SATA aggressive link power management (ALPM); 
[*]PCI Express active state power management (PCIe ASPM) – Linux 2.6.35 and above; 
[*]Runtime power management for PCI(e) bus devices – Linux 2.6.35 and above; 
[*]Radeon KMS power management – Linux 2.6.35 and above, not fglrx; 
[*]Wifi power saving mode – depending on kernel/driver; 
[*]Power off optical drive in drive bay (on battery). 
[/LIST]

**Additional TLP functions:**

[LIST]
[*]I/O scheduler (per disk); 
[*]USB autosuspend with blacklist; 
[*]Audio power saving mode – hda_intel, ac97; 
[*]Enable or disable integrated wifi, bluetooth or wwan devices upon system startup and shutdown; 
[*]Restore radio device state on system startup (from previous shutdown); 
[*]Radio device wizard: switch radios upon network connect/disconnect and dock/undock; 
[*]Disable Wake On LAN; 
[*]WWAN state is restored after suspend/hibernate; 
[*]Undervolting of Intel processors – requires kernel with PHC-Patch; 
[*]Battery charge thresholds – ThinkPads only; 
[*]Recalibrate battery – ThinkPads only. 
[/LIST]

TLP applies these settings  automatically on startup and every time you change the power source. To  use it, all you have to do is install TLP, however, there are some  settings that you can apply manually, overwriting the TLP default  settings, such as enabling or disabling the WiFi, Bluetooth or Wwan (3G  or UMTS) radios, switching between AC or battery settings, ignoring the  actual power source, apply autosuspend for all attached USB devices or  power off the optical drive. 


There are also some TinkPad-only  settings that you can use, like temporarily changing the battery charge  thresholds, temporarily set battery charge thresholds to factory  settings, recalibrating the battery and more.


For more about these settings, see the TLP [homepage]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html") or consult the TLP manpage (type "*man tlp*" in a terminal).


I've only been using TLP for a  couple of hours so I can't say yet how efficient this tool is regarding  battery life, but I've noticed that my laptop's temperature is lower  than before using TLP. You may have seen an icon on my Unity launcher in  some posts on WebUpd8, which displays a number that's usually around 65  - that's [Psensor]("http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html") and it displays the CPU temperature (Celsius; it's 165 degrees Fahrenheit) - here's an [example]("http://www.webupd8.org/2013/04/get-ubuntu-touch-feeling-on-unity.html").  Well, after installing TLP, the CPU temperature didn't go past 55  degrees Celsius (135 degrees Fahrenheit), at least not yet, with regular  desktop usage: using a browser with quite a few tabs open, a text  editor and a few AppIndicators running, under Unity. This, of course,  depends on various factors but so far this tool seems to do its job.  Also, some Reddit users have [reported]("http://www.reddit.com/r/Ubuntu/comments/1cdg2h/ubuntu_battery_draining_issues/") that TLP makes quite a big difference.



**Install TLP in Ubuntu**


**Before proceeding with the installation, there are a couple of things you need to do:**

[LIST]
[*]firstly, if you've added any power saving settings / scripts (e.g.: in */etc/rc.local*), remove them or else TLP may not work properly; 
[*]remove laptop-mode-tools ("sudo apt-get remove laptop-mode-tools"). 
[/LIST]

**Ubuntu (and Linux Mint, etc.) users  can install TLP by using its official PPA. Add the PPA and install TLP  using the following commands:**
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw
TLP will automatically start  upon  system startup, but to avoid having to restart the system to get it  running for the first time, you can start it (required only the first  time) using the following command:
sudo tlp start
**There are some optional packages you can install for some extra features:**

[LIST]
[*]*smartmontools* - needed to display disk drive S.M.A.R.T. data; 
[*]*ethtool* - needed to disable wake on lan. 
[/LIST]

Install these tools (available in the Ubuntu repositories) using the following command:
sudo apt-get install smartmontools ethtool
**There are also some ThinkPad only, optional packages you may need:**

[LIST]
[*]*tp-smapi-dkms* - needed for battery charge thresholds and ThinkPad specific status output of tlp-stat; 
[*]*acpi-call-tools* -  acpi-call is needed for battery charge thresholds on Sandy Bridge and newer models (X220/T420, X230/T430, etc.). 
[/LIST]

Install these packages using the following command:
sudo apt-get install tp-smapi-dkms acpi-call-tools
**Other Linux distributions: there are TLP packages for Debian 6.0+, Arch Linux, openSUSE 11.4+, Gentoo, Fedora 16+** - see the TLP [homepage]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html") for installation instructions. You can grab the source / report bugs @ [GitHub]("https://github.com/linrunner/TLP") 

Make sure to also read the [TLP FAQ]("http://linrunner.de/en/tlp/docs/tlp-faq.html").

---

### Post by muddpup64 on 2013-10-06
> **snafu006 said:**
> i am guessing your video card. next time need more system info.

Video chipsets: 
[LIST]
[*]Intel HD Graphics 
[*]256MB NVIDIA® Quadro® NVS3100M 
[/LIST]
**Notes:**

[LIST]
[*]Support for a external monitor is through VGA DB-15 connector 
[*]Support for digital monitor via DisplayPort (supports single-link DVI-D via cable 45J7915) 
[*]Maximum   external resolution: 2560x1600 (DisplayPort)@60Hz; 2048x1536   (VGA)@75Hz; 1920x1200@60Hz (single-link DVI-D via cable 45J7915 
[*]All displays are measured diagonally. 
[/LIST]

Did you ever install the Video drivers for Nvidia if thats what the laptop has.

if you have intel then instll the official intel drivers here.
[B][Official Intel Linux Graphics Installer Available For Ubuntu 13.04]("http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html")
[http://www.webupd8.org/search?updated-max=2013-09-09T16:38:00%2B03:00&max-results=10&start=10&by-date=false](http://www.webupd8.org/search?updated-max=2013-09-09T16:38:00%2B03:00&max-results=10&start=10&by-date=false)[/B]

This link is the main download page.
[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)


I'm not sure what drive it is specificly, all I know is that it's Intel. I have installed Nvidia but saw no change. Also I'm running 12.04 LTS. (Forgot to mention that, sorry.)
How do I find graphics card info so I can get that to you?

---

### Post by snafu006 on 2013-10-06
Open terminal enter : sudo lshw -c display enter password then give terminal a sec and then post back the reed out here

---

### Post by muddpup64 on 2013-10-06
> **snafu006 said:**
> Open terminal enter : sudo lshw -c display enter password then give terminal a sec and then post back the reed out here

I entered the command and it printed this:

*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f2000000-f23fffff memory:d0000000-dfffffff ioport:1800(size=8)

---

### Post by snafu006 on 2013-10-06
you have am intel Video card. uninstall any nvidia drivers you install search google and then do every thing i posted GL

---

### Post by muddpup64 on 2013-10-06
Intel Graphics Installer doesn't support 12.04, maybe there is another place I can download a 12.04 version?

---

### Post by muddpup64 on 2013-10-06
Installed the 12.10 version, ran it, and this is what I got:
[ATTACH=CONFIG]246792[/ATTACH]

---

### Post by snafu006 on 2013-10-07
Ok lets do this open terminal

> sudo apt-get update
sudo apt-get upgrade

thats is to make sude you are all up to date

next we are going to install some  Graphics Drivers 
> sudo add-apt-repository ppa:oibaf/graphics-drivers 
sudo apt-get update
sudo apt-get dist-upgrade


cheack to see if they installed

> glxinfo | grep OpenGL

last thing 

> sudo apt-get install libgl1-mesa-dri-experimental

all this is on this link i keep getting a smilly face up there fing ubuntu forum 
i run this driver and there better then ATi drivers 
[http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

---

### Post by snafu006 on 2013-10-07
also even tho the first page of that fourm is not updated the Phoronix[COLOR=blue][/COLOR][COLOR=#000000][/COLOR]Team keep that driver up to date

---

### Post by snafu006 on 2013-10-07
just a quote from that forum 

> [COLOR=darkgreen]**Mesa packaging improvements:**[/COLOR]

[LIST]
[*]support for **S3TC texture compression**[SIZE=1]*[/SIZE] (Recommends included libtxc-dxtn) 
[*]support for **floating-point textures**[SIZE=1]*[/SIZE] 
[*]**llvm** support (for faster gallium drivers) 
[*]**gallium llvmpipe** as the default software renderer rather than classic swrast 
[*]**i915 and nouveau gallium** drivers in the **experimental** package 
[*]**--enable-debug** flag (to better debug mesa and games bugs) 
[*]better package compression with 50% binary size reduction (for faster download) 
[*]custom *OpenGL version string* to make sure you are running drivers from this PPA 
[/LIST]

 
you have a intal i915 video chip set

---

### Post by muddpup64 on 2013-10-07
Runs like a champ. Thanks :D

---

### Post by snafu006 on 2013-10-07
Good to know have fun and welcome to linux.

---

