---
title: "Dell Studio 15n Owner's Thread - Tweaking Guide"
date: 2009-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NTolerance on 2009-02-10
**_Introduction_**

If you want to get the most out of your Studio 15n you've come to the right place.  This guide will provide details on how to configure this laptop for use with Ubuntu 8.10 Intrepid Ibex.  The information here may be useful for but **does not** directly pertain to Studio 15 laptops shipped with any version of Microsoft Windows, it is intended for Studio 15ns pre-loaded with Ubuntu 8.04 Hardy Heron.  Dell's n-series of Ubuntu laptops have different hardware configurations than those shipped with Microsoft Windows.  Aside from screen resolution, almost all Studio 15ns have identical hardware configurations, save from software-agnostic things like battery size and HDD space.  Here are the specs of my system:

[FONT=Courier New]Intel Core 2 Duo T5750, 2.0GHz, 667Mhz, 2M L2 Cache
2GB, DDR2, 667MHz 2 Dimm
Hi Resolution, glossy widescreen 15.4 inch display (1920x1200)
Intel Graphics Media Accelerator X3100
250G 5400RPM SATA Hard Drive
Ubuntu 8.04 with DVD Playback
8X Slot Load CD / DVD Burner (Dual Layer DVD+/-R Drive)
Integrated High Definition Audio 2.0
Dell Wireless 1397 802.11g Half Mini Card
Integrated 2.0M Pixel Webcam
56 WHr 6-cell Lithium Ion Primary Battery
Dell Wireless 370 Bluetooth Module (2.0)[/FONT]

[U][B]Installation
[/B][/U]
First, boot into the pre-loaded Ubuntu 8.04 OS.  Insert a blank DVD-R disc and click on the desktop shortcut with the Dell icon.  This will burn a recovery DVD that will restore your hard drive to it's factory state.  Once you've made the recovery disc, insert your Ubuntu 8.10 CD and proceed to install Intrepid Ibex.  I chose the "guided - full" partitioning option.  This assigned a ~6GB swap partition, which is a bit too large in my opinion.  In the future I will choose a manual partition setup and assign a 1-2GB swap partition.  Install should complete without a hitch, with all hardware and screen resolution detected.  Immediately install all available updates, especially the 2.6.27-11-generic kernel which is current as of this post.  More on that later.

[U][B]Screen Resolution

[/B][/U]There are two screens available for this laptop, 1440x900 WXGA+ and 1920x1200 WUXGA.  WUXGA is detected and set properly on the Intrepid live CD and of course after installation is complete.  As with all Ubuntu installations, virtual terminal resolution is set to a very low 640x480, which is nigh unusable.  So let's fix that and get the highest resolution possible.  The following steps are intended for the 1920x1200 WUXGA screen, so if you have the 1440x900 screen you might want to hit _[u][this how-to]("http://ubuntuforums.org/showthread.php?t=258484")_[/U] to make sure you get the correct settings for your screen.
 
First we will install the "hwinfo" program which will tell us what resolutions are supported by the virtual console framebuffer:
```

sudo apt-get install hwinfo
```Now run this command to list possible resolutions:
```
sudo hwinfo --framebuffer | grep 'Mode'
```Here is the output from my system:
```

  Model: "Intel(r)GM965/PM965/GL960 Graphics Controller"
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
```1600x1200 at 16-bit color looks good to me, so let's back up our GRUB menu.lst file before we make changes:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```Now let's edit the file:
```
gksu gedit /boot/grub/menu.lst
```Find the line that looks like this:
```
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=ace57361-7e46-4d8e-b2bd-2ac6a9c33e99 ro quiet splash
```Append "vga=0x34B" to the end so it looks like this:
```
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=ace57361-7e46-4d8e-b2bd-2ac6a9c33e99 ro quiet splash vga=0x34B
```This will set the current kernel to boot at high resolution, but we need to make another change to the menu.lst file to force updated kernels to use it as well.  Find the line that says 
```
# defoptions=quiet splash
```And again add your new VGA mode to the end:
```
# defoptions=quiet splash vga=0x34B
```If you were to reboot at this point you'd see your fancy text resolution, but you'd also notice that your usplash progress bar would appear off-center.  We want to fix that as well, so let's edit our usplash.conf file:
```
gksu gedit /etc/usplash.conf
```We need to make the usplash resolution match the text resolution to fix the off-center problem.  Make the file look like this:
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1600
yres=1200
```Next we need to update your kernel with the new usplash resolution:
```
sudo update-initramfs -u -k `uname -r`
```Now you can reboot and witness the glory of your fully optimized boot screen and virtual terminals.  The usplash image will be slightly stretched, but it's worth it in my opinion.  

On a related note, why does this laptop not have an option in the BIOS to set non-native resolutions to be letterboxed and not stretched?  My old Dell Inspiron E1505 has this feature and it really helps text mode screens, games, etc...  

[U][B]Wireless

[/B][/U]I was a bit _[surprised](http://ubuntuforums.org/showthread.php?t=888697)_ to find out that the only option for Wireless networking on this laptop is the Broadcom BCM4312 card.  Fortunately the "wl" driver is automatically loaded by Intrepid.  It works well in my testing.  A Broadcom STA driver is offered by the Restricted Drivers Manager, but this is a bug as [ explained](http://ubuntuforums.org/showpost.php?p=6714817&postcount=2) by [superm1](http://ubuntuforums.org/member.php?u=44239).

**_Ethernet_**

The Broadcom NetLink BCM5784M gigabit LAN works fine.  I like to put my laptop into S3 suspend mode and wake it up remotely via Wake-on-LAN if I need it.  If you want this _[feature](http://ubuntuforums.org/showthread.php?t=234588)_, install ethtool:
```
sudo apt-get install ethtool
```

Create a startup script to enable Wake-on-LAN during boot:
```
gksu gedit /etc/init.d/wakeonlan
```

Paste this into the file:
```
#!/bin/bash
ethtool -s eth0 wol g
exit

```

Make the script executable:
```
sudo chmod +x /etc/init.d/wakeonlan
```

Add it to the system startup:
```
sudo update-rc.d /etc/init.d/wakeonlan defaults
```

Run the script manually or reboot to get your changes to take effect.  Your laptop should now wake up if Wake-on-LAN packets are sent to it while it is in S3 suspend mode.  Keep in mind that this will not enable Wake-on-LAN when the laptop is fully powered down.

**_Graphics_**

The only graphics option for this laptop is the integrated Intel X3100 chip. Intel provides solid, open source Linux drivers. If you're not into gaming but want smooth Linux performance, you can't go wrong here. The X3100 is supported by the i915 driver. Compiz Fusion works straight away on the Live CD and performs flawlessly.

**_Webcam_**

Works well.  Grab the "cheese" program to use it:

```
sudo apt-get install cheese
```

I found that I did not like cheese dumping all the webcam photos and videos directly into my home directory.  Open your configuration editor if you to change it:

```
gconf-editor
```

Navigate to the "apps->cheese" tree and change "photo_path" and "video_path" to a more prudent directory.

**_Sound_**

The kernel shipped on the Intrepid disc has _[issues](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/290549)_ with headphone jack detection.  Use Update Manager to grab the current 2.6.27-11-generic kernel.  Now, open your ALSA configuration file for editing:
```
gksu gedit /etc/modprobe.d/alsa-base
```

Add this line to the bottom of the file:
```
options snd-hda-intel model=dell-m6
```

Reboot, and now both headphone jacks should be detected and the built-in speakers should be muted when headphones are plugged in.

**_Power Management_**

This laptop was designed for Ubuntu, so this stuff better damn well work, and it does.  Hibernate and suspend work as expected.

**_Touchpad_**

This is a real sore spot.  Many users have _[reported](http://forum.notebookreview.com/showthread.php?t=309852)_ erratic and laggy touchpad movement.  Indications point to this being a hardware problem as it happens in both Windows and Ubuntu.  There is no known fix for the problem at this time. 

This situation goes from bad to ugly.  When your cursor isn't lagging behind, it's also way too slow and has very little acceleration.  To fix this we'll need to install and _[enable](http://forums.fedoraforum.org/showthread.php?p=1140547)_ the Gsynaptics touchpad control panel.  To allow Gsynapics to alter our touchpad settings we need to create a new HAL file for Ubuntu to use:
```
gksu gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi
```

Paste this into the new file:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

You will probably need to restart X to get this latest change to take effect.  Now let's install Gsynaptics:
```
sudo apt-get install gsynaptics
```

Now you will have a new "Touchpad" shortcut in "System->Preferences".  Use this to increase your touchpad speed and acceleration.  Don't get too excited, we're not done yet.  I've found that Gsynaptics settings will not survive hibernate or suspend.  Upon resuming, settings are lost.  We'll add a script to Ubuntu's power management system to reload Gsynaptics when resuming.  Create the new script:
```
gksu gedit /etc/pm/sleep.d/90-gsynaptics-init
```

Paste this into the file:
```
#!/bin/sh

case "$1" in
    thaw|resume)
	sleep 5
	DISPLAY=:0.0 su `who | grep tty7 | sed 's/\([a-z]*\).*/\1/'` -c 'gsynaptics-init --sm-disable' 
    ;;
esac

exit 0

```

Make the new script executable:
```
sudo chmod +x /etc/pm/sleep.d/90-gsynaptics-init
```

**_Hardware Monitoring_**

I like to keep tabs on my laptops temperature.  You can use the Sensors Applet to get this information:
```
sudo apt-get install sensors-applet
```

Now right-click on a GNOME panel and select the "Add to Panel" option.  Choose the "Hardware Sensors Monitor".  Right-click on the applet and select "Preferences".  Under the sensors tab you will find two detected sensors, "libsensors temp1" and "acpi THM".  On my system they both give near identical readings, so I have the Hardware Sensors Monitor only display the "THM" sensor.  

**_BIOS Updates_**

Being that this laptop has true factory-installed Linux support, you don't need Windows to flash the BIOS.  There are two published methods to flash the BIOS from within Ubuntu.  The method found in the _[Ubuntu wiki](https://wiki.ubuntu.com/DellBIOS)_ did not work for me.  It did not automatically find the latest available BIOS.  Instead I have used _[Dell's method](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)_ with success to updated to BIOS version A06.

**_Conclusion_**

This thread serves as a reference to myself and hopefully other Studio 15n owners.  I solicit comments and improvements on my tweaks and especially would like to see new tweaks that aren't yet listed here.

---

### Post by superm1 on 2009-02-11
Couple of comments:

1) You really shouldn't need that quirk for alsa-base in modprobe options.  The laptop should be properly detected without it on the latest kernel.
2) The WL driver is not fully open source.  It is the same driver as the STA driver.  There is a bug in hardware-drivers related to when the card is only supported by wl and not b43 causing it to be activated by still offered to activate again.

---

### Post by NTolerance on 2009-02-11
> **superm1 said:**
> Couple of comments:

1) You really shouldn't need that quirk for alsa-base in modprobe options.  The laptop should be properly detected without it on the latest kernel.
2) The WL driver is not fully open source.  It is the same driver as the STA driver.  There is a bug in hardware-drivers related to when the card is only supported by wl and not b43 causing it to be activated by still offered to activate again.

I'll test taking out the alsa-base setting out and see what I get.  I originally put it in there when running the 2.6.27-11 kernel from intrepid-proposed.  

Fixed section about the wireless drivers.  Thank you!

---

