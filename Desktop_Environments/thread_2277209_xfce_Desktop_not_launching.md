---
title: "xfce Desktop not launching"
date: 2015-05-07
forum: Desktop Environments
---

### Post by Jonners59 on 2015-05-07
I hope someone can assist me.
I upgraded from 14.10 to 15.04 vivid using the update facility, but that didn't work, left me with 14.10 still running, so I then downloaded the iso and burnt to a DVD and so upgraded again. This time it upgraded perfectly except in Unity.  I downloaded xfce components via "Synaptic" and everything seems fine, until I rebooted for the first time.  Now when I log in I find that I have no panels and the desktop is also a mess.  Fortunately, xfce has an "Application" menu in the desktop right click, so I can chose "Settings".

If I select "Panel" immediately I get a message to say gnome-panel was not loaded, would I like to "Execute" it, which i do and the desktop is restored.  I have saved the session in  "Session and Startup", but it makes no difference.

To note: I have a separate directory for my /Home and I am running x86_64
Any other information required, please ask and any cmd required.

```
baronipc@BaroniPC:~$ lspci -vnn | grep VGA -A 12
```
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GTX 650] [10de:0fc6] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:362b]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at fb000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:362b]
[CODE]baronipc@BaroniPC:~$ sudo lshw -C display
```
 ```
 *-display               
       description: VGA compatible controller
       product: GK107 [GeForce GTX 650]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:42 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff


```

---

### Post by tgalati4 on 2015-05-07
I would back up my personal files, wipe the disk then install Xubuntu.  [http://xubuntu.org/](http://xubuntu.org/)

---

### Post by Jonners59 on 2015-05-07
Oh, no....  That's not a solution.  It'll be a simple config somewhere, always is.

---

### Post by tgalati4 on 2015-05-07
True, it might be a configuration file setting, but loading full Ubuntu to get XFCE seems like overkill.  Perhaps open a terminal and run:

```
xfce4-panel
```

Take note of any errors.

Exactly how did you install xfce4?

> tgalati4@Mint17 ~ $ apt-cache depends xfce4
xfce4
  Depends: xfwm4
  Depends: xfconf
  Depends: xfce4-settings
  Depends: xfce4-panel
  Depends: xfdesktop4
  Depends: thunar
  Depends: gtk2-engines-xfce
  Depends: xfce4-session
  Depends: xfce4-appfinder
  Depends: xfce4-mixer
  Depends: orage
  Depends: libxfce4ui-utils
  Suggests: xfce4-goodies
  Suggests: xfce4-power-manager
  Suggests: gtk3-engines-xfce
  Recommends: xorg
  Recommends: desktop-base
  Recommends: thunar-volman
  Recommends: tango-icon-theme
  Recommends: xfce4-notifyd


There are a lot of pieces that need configuration to get XFCE to work properly.

---

### Post by Bucky Ball on 2015-05-07
> **Jonners59 said:**
> Oh, no....  That's not a solution.  It'll be a simple config somewhere, always is.

All depends what you did. Tacking it together from bits is not the way to go and can produce a dog's breakfast that's far from a simple tweak to fix.

You install xfce4 if you want the xubuntu desktop only. Nothing else. That's it. Then log out, choose 'xfce session' from the Sessions menu and log in. That simple. You can easily switch between xfce and Unity by logging out and in again. 

The other option is to install xubuntu-desktop. Nothing else required. That will drag in ALL of Xubuntu and you may as well just start from the beginning and install Xubuntu. Despite that, changing between Unity and xfce is the same procedure as outlined above.

If you made a list of the bits you installed, uninstall them, open a terminal and:

```
sudo apt-get autoremove
```

Reboot. About the best I can come up with for the moment on the given information. ;)

---

### Post by Jonners59 on 2015-05-08
Thanks guys.
Normally I use a set of cmds I found and kept a couple of years ago.  And that is what I had used to build and run the machine these past few years perfectly happily, but after the 14.10 upgrade to 15.04 didn't go so smoothly, I searched again and took some new commands from the forum.  They may well have done the same, but for this one issue...

tgalati4
I noted your list of dependencies and did a check in Synaptic, and 3 were missing.  I had just created an auto start cmd in the Application Startup app, but have just disabled it upon your nice list, which I have check are now installed.  just about to try a re-boot to test it.

---

### Post by Jonners59 on 2015-05-10
OK tried all that and also tried to log in to GNOME, GNOME (Compiz), GNOME(Meta), xUBUNTU.....  Each had it's flaws.

So xfce4 works, but with two error messages (which I can ignore, though they may give a clue to the problem) and I have to go in to "preferences" and then close it for Panel 1 to work - no changes required.

The messages are:
[HTML]Modifying the panel is not allowed
Because the panel is running in kiosk mode, you are not allowed to make changes to the panel configuration as a regular user[/HTML]
 
[HTML]Failed to show the preferences dialogue
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken[/HTML]

```
apt-cache depends xfce4xfce4
  Depends: xfwm4
  Depends: xfconf
  Depends: xfce4-settings
  Depends: xfce4-panel
  Depends: xfdesktop4
  Depends: thunar
  Depends: gtk2-engines-xfce
  Depends: xfce4-session
  Depends: xfce4-appfinder
  Depends: xfce4-mixer
  Depends: orage
  Depends: libxfce4ui-utils
  Suggests: xfce4-goodies
  Suggests: xfce4-power-manager
  Suggests: gtk3-engines-xfce
  Recommends: xorg
  Recommends: desktop-base
  Recommends: thunar-volman
  Recommends: tango-icon-theme
  Recommends: xfce4-notifyd

```

FYI to install xfce4 I used:
xfce4 in Synaptic
and then when having some problems I used 
```
sudo apt-get install xfce4
```
which just told me I had the latest version.

Please remember, I had and was using xfce for a number of years and all my settings and prefs were already installed.  It was the upgrade that caused the problems.

I wonder if there is a conf file or who owns it....

---

### Post by Jonners59 on 2015-05-12
OK, so tried everything I could.  I think the GNOME configs were confusing it so went with your make and break approach, rather than fix it.

Downloaded the iso for xUbuntu and ran the install, selecting "Other" for the HD burn as I have a separate Home directory.  Selected the / directory and to format and install, and /Home without format.  The install froze and had loads of error messages at something to do with CUPS.  So I aborted, and tried again.  The next time without formatting, but after the install completed and I did a reboot it wouldn't let me in, so I tried again.  This time I used gParted to delete and recreate the /directory, then installed the new xUbuntu to the same and my /Home to my existing without formatting.

Booted fine, but spent the day getting the basics back up and running.  I still have GNOME directories, and maybe others that I think are not needed any more, but worried about deleting anything.

The desktop will not allow me to put icons where I want them.  I have two screens, and I like to put a few key launchers and bits n bobs on the desktop.  I can move them about screen 1 but it will not allow me to put anything on screen 2!

The mouse is also a bit flaky.  It seems to stick a bit and certainly does not move smoothly all the time.

Thunderbird is very slow and freezes up.

Any thoughts.

---

### Post by Jonners59 on 2015-05-13
OK, this is going from bad to worse!
So, I have problems in that:
1. mouse gets sticky (sorry only way I can describe it).
2. A vitral Excel workbook I have been using for months keeeps crashing, but it may not be just that ap.  WHat happens is the ap stops working, I then try and kill it with xkill, but it still appears on the desktop and when I change desktops it flashes up every where....  Really spooky.
3. icons do not stay where I left them and that I can only get them on the left screen/monitor

And now, in trying to fix all this I can not launch my second monitor.  I just have 1.

this is wasting so much time.  I don't want to go through yet another rebuild.

Any one help, PLEASE!!!!
```
xrandr
```
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      77.0* 
```

Actual xml, which may have come from the previous settings
```
<?xml version="1.0" encoding="UTF-8"?>
<channel name="displays" version="1.0">
  <property name="Notify" type="bool" value="true"/>
  <property name="Default" type="empty">
    <property name="DVI-D-2" type="string" value="2. AOC Intl 19&quot;">
      <property name="Active" type="bool" value="true"/>
      <property name="Resolution" type="string" value="1280x1024"/>
      <property name="RefreshRate" type="double" value="60.019740"/>
      <property name="Rotation" type="int" value="0"/>
      <property name="Reflection" type="string" value="0"/>
      <property name="Primary" type="bool" value="true"/>
      <property name="Position" type="empty">
        <property name="X" type="int" value="1280"/>
        <property name="Y" type="int" value="0"/>
      </property>
    </property>
    <property name="DVI-D-1" type="string" value="1. Goldstar Company Ltd 19&quot;">
      <property name="Active" type="bool" value="true"/>
      <property name="Resolution" type="string" value="1280x1024"/>
      <property name="RefreshRate" type="double" value="60.019740"/>
      <property name="Rotation" type="int" value="0"/>
      <property name="Reflection" type="string" value="0"/>
      <property name="Primary" type="bool" value="false"/>
      <property name="Position" type="empty">
        <property name="X" type="int" value="0"/>
        <property name="Y" type="int" value="0"/>
      </property>
    </property>
    <property name="DVI-D-0" type="string" value="1. Goldstar Company Ltd 19&quot;">
      <property name="Active" type="bool" value="true"/>
      <property name="Resolution" type="string" value="1280x1024"/>
      <property name="RefreshRate" type="double" value="60.019740"/>
      <property name="Rotation" type="int" value="0"/>
      <property name="Reflection" type="string" value="0"/>
      <property name="Primary" type="bool" value="false"/>
      <property name="Position" type="empty">
        <property name="X" type="int" value="0"/>
        <property name="Y" type="int" value="0"/>
      </property>
    </property>
    <property name="default" type="string" value="default">
      <property name="Active" type="bool" value="true"/>
      <property name="Resolution" type="string" value="1280x1024"/>
      <property name="RefreshRate" type="double" value="77.000000"/>
      <property name="Rotation" type="int" value="0"/>
      <property name="Reflection" type="string" value="0"/>
      <property name="Primary" type="bool" value="false"/>
      <property name="Position" type="empty">
        <property name="X" type="int" value="0"/>
        <property name="Y" type="int" value="0"/>
      </property>
    </property>
  </property>
</channel>



```

```
                                                     [xfdesktop-version-4.10.3+-rcfile_format]            
            4.10.3+=true            
                        [/home/baronipc/Desktop/flegita.desktop]            
            row=2            
            col=39            
                        [/home/baronipc/Desktop/BaroniPC Hardware info.docx]            
            row=6            
            col=9            
                        [/home/baronipc/Desktop/simple-scan.desktop]            
            row=3            
            col=39            
                        [/home/baronipc/Desktop/Q3]            
            row=0            
            col=14            
                        [/home/baronipc/Desktop/Server.desktop]            
            row=0            
            col=0            
                        [/home/baronipc/Desktop/SKy and 3]            
            row=0            
            col=13            
                        [/home/baronipc/Desktop/AC of WW2 OUTSTANDING.xlsx]            
            row=5            
            col=10            
                        [/home/baronipc/Desktop/fstab.conf]            
            row=5            
            col=9            
                        [/home/baronipc/Desktop/chrome-hmjkmjkepdijhoojdojkdfohbdgmmhki-Default.desktop]            
            row=0            
            col=29            
                        [/home/baronipc/Desktop/Documents]            
            row=4            
            col=0            
                        [/home/baronipc/Desktop/Asia-Talent-Insights.pdf]            
            row=5            
            col=8            
                        [/home/baronipc/Desktop/evince-previewer.desktop]            
            row=1            
            col=39            
                        [/home/baronipc/Desktop/Reboot.desktop]            
            row=0            
            col=31            
                        [/home/baronipc/Desktop/Windows7.desktop]            
            row=0            
            col=39            
                        [/home/baronipc/Desktop/retrieved1.pdf]            
            row=5            
            col=7            
                        [/home/baronipc/Desktop/Cloud Info]            
            row=6            
            col=0            
                        [/home/baronipc/Desktop/tmp]            
            row=7            
            col=0            
                        [/home/baronipc/Desktop/dolphin.desktop]            
            row=4            
            col=39            
                        [/home/baronipc/Desktop/June 2014 to May 2015]            
            row=0            
            col=15            
                        [/home/baronipc/Desktop/56528 ATR 540208 Lead Project Manager Cardiff.xlsx]            
            row=5            
            col=6            
                        [/home/baronipc/Desktop/CV0.desktop]            
            row=5            
            col=0            
                        [/home/baronipc/Desktop/Force Quit.desktop]            
            row=0            
            col=30            
                        [/home/baronipc/Desktop/copy of Server.desktop]            
            row=1            
            col=0            
                        [/home/baronipc/Desktop/GAMES]            
            row=0            
            col=38            
                        [Rubbish Bin]            
            row=15            
            col=39            
                        [/]            
            row=2            
            col=0            
                        [/home/baronipc]            
            row=3            
            col=0             
                        

```
```
uname -m
x86_64
```

---

### Post by tgalati4 on 2015-05-14
What are the SMART parameters of your disk drive? 

```
sudo smartctl -a /dev/sda
```

Xubuntu is a pretty solid distro and the fact that you are having so many problems might indicate a hardware problem.

Did you perform a media check on the USB or DVD that you created to install Xubuntu?

---

### Post by Jonners59 on 2015-05-14
> **tgalati4 said:**
>  
tgalati4
Thank you for helping out.

> **tgalati4 said:**
> What are the SMART parameters of your disk drive? 
```
sudo smartctl -a /dev/sda
```
That didn't work
```
sudo: smartctl: command not found
```

> **tgalati4 said:**
> Xubuntu is a pretty solid distro and the fact that you are having so many problems might indicate a hardware problem.

Did you perform a media check on the USB or DVD that you created to install Xubuntu?

It was all working fine until the latest upgrade.  As a result I tried to reinstall xfce and it has all gone down hill from there.  5th attempt.

I now have my desktop working.  As of this AM I had the keyboard in GB, but the keys were all over the place.  I think I have that sorted now too. - soon know when I reboot!

BUT:
I can't get Libre working, it says it didn't complete the install, I have retried installing several times.
AND
I can't play DVDs, though not too important on this machine at this stage.
I am also a bit p155ed off as I have done a more thorough install this last time and now i have lost all my apps and their settings, built up over the past 4 years...
And the Microsoft Office apps in crossover are now hard to find, not displaying in the menu as they used to.  I have tried editing it, but they never show.

I do not think this is to do with the DVD or HW, I think this is a combination of configs, maybe conflicting and reinstalling apps.

---

### Post by tgalati4 on 2015-05-14
Sorry, you need to install *smartmontools* first.

```
sudo apt-get install smartmontools
```

Yes, upgrading can be painful.  In-place upgrades can cause problems.  Clean installs mean you have to reconfigure everything.  Sometimes you get lucky and an in-place upgrade will work as you expect.  My suggestion of a clean install comes from a troubleshooting background--it's easier to fix things from a known condition.  A clean install gives you that.  An in-place upgrade leaves old and new libraries and configuration files on your system, which can make troubleshooting problematic.

There is an XFCE menu editor.  You will have to search for a tutorial on how to use it.

[http://wiki.xfce.org/howto/customize-menu#create_sub-menus](http://wiki.xfce.org/howto/customize-menu#create_sub-menus)

[http://askubuntu.com/questions/76042/how-can-i-add-items-to-xfce-root-menu](http://askubuntu.com/questions/76042/how-can-i-add-items-to-xfce-root-menu)

If you made a backup of your /home folder, then you should still have the old configuration files, then you can cut and paste the changes.

Everything is fixable.  Patience is key.

---

### Post by matt_symes on 2015-05-14
Hi

tgalati4 is pretty good so work through the problems with him.

I wanted to point out the obvious last resort though; reinstall 14.10 :)

Kind regards

---

### Post by Jonners59 on 2015-05-15
> **tgalati4 said:**
> 
Sorry, you need to install *smartmontools* first.

```
sudo apt-get install smartmontools
```


```
sudo smartctl -a /dev/sda
```
```
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-16-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA
Device Model:     WDC WD2500AAJS-60M0A0
Serial Number:    WD-WMAV2A990502
LU WWN Device Id: 5 0014ee 056c980e4
Firmware Version: 02.03E02
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 3.0 Gb/s
Local Time is:    Fri May 15 10:19:50 2015 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 5580) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  68) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   133   129   021    Pre-fail  Always       -       4350
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2167
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       13233
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2086
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       65547
190 Airflow_Temperature_Cel 0x0022   055   043   040    Old_age   Always       -       45
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       393
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2167
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

> **tgalati4 said:**
> 
Yes, upgrading can be painful.  In-place upgrades can cause problems.   Clean installs mean you have to reconfigure everything.  Sometimes you  get lucky and an in-place upgrade will work as you expect.  My  suggestion of a clean install comes from a troubleshooting  background--it's easier to fix things from a known condition.  A clean  install gives you that.  An in-place upgrade leaves old and new  libraries and configuration files on your system, which can make  troubleshooting problematic.

There is an XFCE menu editor.  You will have to search for a tutorial on how to use it.

[http://wiki.xfce.org/howto/customize-menu#create_sub-menus](http://wiki.xfce.org/howto/customize-menu#create_sub-menus)

[http://askubuntu.com/questions/76042/how-can-i-add-items-to-xfce-root-menu](http://askubuntu.com/questions/76042/how-can-i-add-items-to-xfce-root-menu)

If you made a backup of your /home folder, then you should still have  the old configuration files, then you can cut and paste the changes.

Everything is fixable.  Patience is key.
I managed to fix the Menu, but also reinstalled MS Office in Crossover in the mean time.  Not ideal, and not as elegant as it was, but it works.

As per above scan, nothing wrong with the HW, never thought there was.  The issues I am having, that of keyboard language is a known issue.  I have seen a couple of blogs about it.  Seems that changes are not recognised and require a logout, login step with the change being made at the login screen which sets the default language/setting.  Then the two - and probably conflicting - keyboard settings tools need to be set to default, ignore all installed layouts downloaded.

As for desktop not remembering layout, that too is a recognised issue.  I have seen a bug or two about this, but I think my issue here is that the right screen will NOT allow anything to be saved to desk top SOMETIMES afterboot up, and other times it does.  So when it does the layout is made and saves, but when logging back in IF the second screen does not allow items on the desktop, then they are rejected and the whole config is recreated.  This is seen by the number of config files in the ./home/.conf/.xfce/desktop.  I do NOT know what causes this intermittent fault.  If the desktop right screen accepting items always was fixed could then see if that resolves the overall problem.

Screenlets opening in different places after reboot, don't know why it can't remember where to put items.

The screen save/flashing that comes up from time to time, is annoying.....

The freezing of apps, such as MS, Thunderbird, is also annoying.....

LibreOffice "installation not completed" issue...

These are other items that need a fix and I have no idea how to go about.

DVDs now play.  Installing the Restricted Extras is not the complete solution, a .sh cmd has to be installed.  But I found that hidden on the Ubuntu website.
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Getting there and now somewhat useable.

SOmething else I noticed, may be able to shed some light on:
[HTML]/home/baronipc/.config/xfce4/panel[/HTML]
There are loads of folders labelled "launcher-##" where ## is a number from 3 to 42, with some numbers missing.  I am assuming that these are cong files for verious panel settings from past and present.  Should they all be deleted and then let the system create 1 new one as with the desktop version?  If so how?

Thanks for the help...  :-)

---

### Post by tgalati4 on 2015-05-15
Your disk has 13K hours on it, so it has some age.  Your disk has 65k command time-outs--that is unusual.  Perhaps you need to reseat or replace a cable.  The rest of the disk looks OK.  So now on to the software problems.  Look through your log files for other errors.

```
less /var/log/syslog
```

Spacebar to page forward, "q" to quit.  Post any errors, no need to post the entire log file.

Before deleting the XFCE launcher files, examine the dates and see if the numbering is consistent with the calendar dates.  It's possible that if you have "Save Session" checked then every time you shut down, XFCE will keep track of each application that is open and try to open it when you reboot.  This doesn't work with every application.  If you want to preserve your desktop between work sessions, simply put your computer to sleep.  When you wake it, then all desktops and applications on those desktops should be exactly as you left them.  When shutting down, I normally have no expectation that my work session will be preserved correctly or at all.

So, I would turn off "Save Session" and see if you have a cleaner work space experience.

---

### Post by Jonners59 on 2015-05-18
Yesterday she wouldn't allow any changes to the 2nd monitor, so it screwed up my desktop again.  BUT she has booted up well today.  The 2nd monitor allows me to save to desktop, so was able to fix alignment from yesterday.  Overall she seems better.

> **matt_symes said:**
> Hi

I wanted to point out the obvious last resort though; reinstall 14.10 :)

Kind regards
Hiya Matt
Done that several times so far...  Really do not want to go through again!

> **tgalati4 said:**
> Your disk has 13K hours on it, so it has some age.  Your disk has 65k command time-outs--that is unusual.  Perhaps you need to reseat or replace a cable.  The rest of the disk looks OK. 
Wow, you could gleen all that from that log.  I have two HD did it say which one had the ify cable?  I'll look in to that, if you can tell me, please.

> **tgalati4 said:**
> So now on to the software problems. Look through your log files for other errors.

```
less /var/log/syslog
```

Spacebar to page forward, "q" to quit. Post any errors, no need to post the entire log file.
OK, this is any line with a Warning.  No errors.  Apologies if any lines are duplicated or missing.  I found it easier to just follow the path to the file and open it.  I did a search on error and this is what I got.  As today she opened better, I may need to do this again, if nothing is found if/when she doesn't behave.  Anyway.  Hope this helps.

[HTML]May 15 07:09:05 Baroni-PC colord[981]: (colord:981): Cd-WARNING **: failed to get session [pid 6372]: Unknown error -2
May 15 09:59:54 Baroni-PC colord[981]: (colord:981): Cd-WARNING **: CdMain: failed to emit DeviceAdded: failed to register object: An object is already exported for the interface org.freedesktop.ColorManager.Device at /org/freedesktop/ColorManager/devices/sysfs__null_
May 15 09:59:54 Baroni-PC kernel: [12348.103881] cdc_acm 4-1.4:1.1: ttyACM0: USB ACM device
May 15 09:59:54 Baroni-PC kernel: [12348.104284] usbcore: registered new interface driver cdc_acm
May 15 09:59:54 Baroni-PC kernel: [12348.104286] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adaptersMay 15 09:59:57 Baroni-PC colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1May 15 10:00:02 Baroni-PC kernel: [12356.108091] usb 4-1.4: USB disconnect, device number 5
May 15 10:00:02 Baroni-PC ModemManager[871]: <info>  (tty/ttyACM0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.4
May 15 10:00:02 Baroni-PC kernel: [12356.110397] cdc_acm 4-1.4:1.1: failed to set dtr/rtsMay 15 10:00:02 Baroni-PC systemd-udevd[328]: error opening USB device 'descriptors' file
May 15 10:00:03 Baroni-PC ModemManager[871]: <warn>  (Plugin Manager) (Via CBP7) [ttyACM0] error when checking support: '(Via CBP7) Missing port probe for port (tty/ttyACM0)'May 15 10:00:03 Baroni-PC ModemManager[871]: <warn>  (Plugin Manager) (Cinterion) [ttyACM0] error when checking support: '(Cinterion) Missing port probe for port (tty/ttyACM0)'
May 15 10:00:03 Baroni-PC ModemManager[871]: <warn>  (Plugin Manager) (Nokia) [ttyACM0] error when checking support: '(Nokia) Missing port probe for port (tty/ttyACM0)'
May 15 10:00:03 Baroni-PC ModemManager[871]: <warn>  (Plugin Manager) (Generic) [ttyACM0] error when checking support: '(Generic) Missing port probe for port (tty/ttyACM0)'
May 15 10:06:19 Baroni-PC systemd-udevd[336]: error: /dev/sdc: No medium found
May 15 10:06:19 Baroni-PC systemd-udevd[336]: error: /dev/sdd: No medium foundMay 15 10:06:19 Baroni-PC systemd-udevd[336]: error: /dev/sde: No medium foundMay 15 10:06:19 Baroni-PC systemd-udevd[336]: error: /dev/sdf: No medium found
May 15 10:06:20 Baroni-PC whoopsie[887]: [10:06:20] GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
May 15 10:06:21 Baroni-PC colord[1004]: (colord:1004): Cd-WARNING **: failed to get session [pid 889]: Unknown error -2
May 15 10:06:22 Baroni-PC gpu-manager[897]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
May 15 10:06:24 Baroni-PC NetworkManager[872]: <error> [1431680784.510236] [dns-manager/nm-dns-dnsmasq.c:398] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
May 15 10:06:21 Baroni-PC colord[1004]: (colord:1004): Cd-WARNING **: failed to get session [pid 889]: Unknown error -2
May 15 10:06:26 Baroni-PC colord[1004]: (colord:1004): Cd-WARNING **: failed to get session [pid 1013]: Unknown error -2
May 15 10:06:38 Baroni-PC org.gtk.vfs.Daemon[1128]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
May 15 10:06:38 Baroni-PC ca.desrt.dconf[1128]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
May 15 10:08:12 Baroni-PC systemd-udevd[336]: error opening USB device 'descriptors' file
May 15 10:20:48 Baroni-PC com.ubuntu.OneConf[1715]: WARNING:oneconf.hosts:Error in loading other_hosts file: [Errno 2] No such file or directory: '/home/baronipc/.cache/oneconf/e00ce5bfb0614272b4e9f1c60151b278/other_hosts'
May 15 10:21:08 Baroni-PC systemd[1]: Starting Cleanup of Temporary Directories...May 15 10:21:08 Baroni-PC systemd-tmpfiles[3676]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
May 15 10:21:08 Baroni-PC systemd[1]: Started Cleanup of Temporary Directories.
May 15 10:29:27 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[09:29:27.130119 WARNING]#033[0m sql.vala:350: SQL error: 5, database is locked
May 15 10:29:27 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[09:29:27.130207 WARNING]#033[0m engine.vala:200: DataInserter: destroyed with unflushed data
May 15 10:29:27 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[09:29:27.130217 WARNING]#033[0m engine.vala:200: DataInserter: destroyed with unflushed dataMay 15 10:29:27 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[09:29:27.130223 WARNING]#033[0m engine.vala:200: DataInserter: destroyed with unflushed data
May 15 10:29:27 Baroni-PC org.gnome.zeitgeist.Engine[1715]: ** (zeitgeist-datahub:2264): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: SQL error: 5, database is locked
May 15 10:33:47 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[09:33:47.813474 WARNING]#033[0m extension-store.vala:90: SQL error: 5, database is locked
May 15 13:06:55 Baroni-PC org.gnome.zeitgeist.Engine[1715]: ** (zeitgeist-datahub:2264): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: SQL error: 5, database is locked
May 15 13:08:47 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[12:08:47.802847 WARNING]#033[0m extension-store.vala:90: SQL error: 5, database is locked
May 15 13:09:06 Baroni-PC org.gnome.zeitgeist.Engine[2718]: ** (zeitgeist-datahub:2773): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
May 15 13:09:06 Baroni-PC org.gnome.zeitgeist.Engine[1715]: ** (zeitgeist-datahub:2264): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
May 15 13:09:06 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[12:09:06.598876 WARNING]#033[0m sql.vala:350: SQL error: 5, database is locked
May 15 13:09:06 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[12:09:06.598895 WARNING]#033[0m engine.vala:200: DataInserter: destroyed with unflushed data
May 15 13:09:06 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[12:09:06.598900 WARNING]#033[0m engine.vala:200: DataInserter: destroyed with unflushed data
May 15 13:09:06 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[12:09:06.598904 WARNING]#033[0m engine.vala:200: DataInserter: destroyed with unflushed data
May 15 13:09:06 Baroni-PC org.gnome.zeitgeist.Engine[1715]: ** (zeitgeist-datahub:2264): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: SQL error: 5, database is locked
May 15 13:10:49 Baroni-PC org.gnome.zeitgeist.Engine[1715]: ** (zeitgeist-datahub:2264): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
May 15 13:10:49 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[12:10:49.411118 WARNING]#033[0m sql.vala:350: SQL error: 5, database is locked
May 15 13:09:06 Baroni-PC org.gnome.zeitgeist.Engine[1715]: ** (zeitgeist-datahub:2264): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: SQL error: 5, database is locked
May 15 13:10:49 Baroni-PC org.gnome.zeitgeist.Engine[1715]: ** (zeitgeist-datahub:2264): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
May 15 13:10:49 Baroni-PC org.gnome.zeitgeist.Engine[1715]: #033[31m[12:10:49.411118 WARNING]#033[0m sql.vala:350: SQL error: 5, database is locked
May 18 07:50:19 Baroni-PC systemd-udevd[340]: error: /dev/sdd: No medium found
May 18 07:50:19 Baroni-PC kernel: [    0.000000]  [mem 0x400000000-0x41fffffff] page 2M
May 18 07:50:19 Baroni-PC kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xbf41efff]May 18 07:50:19 Baroni-PC kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
May 18 07:50:19 Baroni-PC kernel: [    0.000000]  [mem 0x00200000-0xbf3fffff] page 2M
May 18 07:50:19 Baroni-PC kernel: [    0.000000]  [mem 0xbf400000-0xbf41efff] page 4k
May 18 07:50:19 Baroni-PC kernel: [    0.000000] init_memory_mapping: [mem 0xbf5ce000-0xbf5cffff]
May 18 07:50:19 Baroni-PC kernel: [    0.000000]  [mem 0xbf5ce000-0xbf5cffff] page 4k
May 18 07:50:19 Baroni-PC systemd-udevd[340]: error: /dev/sdc: No medium found
May 18 07:50:19 Baroni-PC kernel: [    0.000000] init_memory_mapping: [mem 0xbf681000-0xbf7fffff]
May 18 07:50:19 Baroni-PC kernel: [    0.000000]  [mem 0xbf681000-0xbf7fffff] page 4k
May 18 07:50:19 Baroni-PC kernel: [    0.000000] BRK [0x01fe9000, 0x01fe9fff] PGTABLE
May 18 07:50:19 Baroni-PC kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
May 18 07:50:19 Baroni-PC systemd-udevd[340]: error: /dev/sde: No medium found
May 18 07:50:19 Baroni-PC kernel: [    0.000000]  [mem 0x100000000-0x3ffffffff] page 2MMay 18 07:50:19 Baroni-PC kernel: [    0.000000] BRK [0x01fea000, 0x01feafff] PGTABLE
May 18 07:50:19 Baroni-PC kernel: [    0.000000] RAMDISK: [mem 0x357fa000-0x36bf4fff]May 18 07:50:19 Baroni-PC kernel: [    0.000000] ACPI: Early table checksum verification disabled
May 18 07:50:19 Baroni-PC systemd-udevd[340]: error: /dev/sdf: No medium foundMay 18 07:50:19 Baroni-PC kernel: [    0.000000] ACPI: RSDP 0x00000000000F0420 000024 (v02 ALASKA)May 18 07:50:19 Baroni-PC kernel: [    0.000000] ACPI: XSDT 0x00000000BF46A068 00004C (v01 ALASKA A M I    01072009 AMI  00010013)
May 18 07:50:53 Baroni-PC org.gtk.vfs.Daemon[1162]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
May 18 07:50:53 Baroni-PC ca.desrt.dconf[1162]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
May 18 07:57:15 Baroni-PC systemd[1]: Starting CUPS Scheduler...
May 18 07:57:15 Baroni-PC colord[1008]: (colord:1008): Cd-WARNING **: failed to get session [pid 5199]: Unknown error -2[/HTML]

> **tgalati4 said:**
> 
Before deleting the XFCE launcher files, examine the dates and see if the numbering is consistent with the calendar dates. It's possible that if you have "Save Session" checked then every time you shut down, XFCE will keep track of each application that is open and try to open it when you reboot. This doesn't work with every application. If you want to preserve your desktop between work sessions, simply put your computer to sleep. When you wake it, then all desktops and applications on those desktops should be exactly as you left them. When shutting down, I normally have no expectation that my work session will be preserved correctly or at all.

So, I would turn off "Save Session" and see if you have a cleaner work space experience.
Understand, but I would rather shut her down.  There does seem to be an acknowledged bug, though I think my config goes up the creak, NOT because of the bug, but because sometimes the 2nd screen does not allow anything to save on it.  I strongly suspect that when that is identified and sorted all will be OK...

Of which, any thoughts on the LibreOffice issue.

THANK YOU.  Really helpful stuff.

Best
Jonners59

---

### Post by tgalati4 on 2015-05-18
Understand that there is no "second screen".  The Xorg Window Server uses a Super Desktop which is the summation of your horizontal and vertical resolutions of both displays.  The two screens become portholes to view parts of the same Super Desktop.  It's possible that the icons you are trying to save are simply hidden.  Try moving your displays so that they are side-by-side, or one on top of the other.  Then observe where the launchers are placed when you create them.  They don't behave the way you expect.  This is either a bug or a feature.

As far as determining which drive is which:

```
sudo fdisk -l
```

/dev/sda is the first disk on your system.
/dev/sdb is the second disk on your system.

/dev/sda is the one that I suspect has a cable issue.

---

### Post by The Cog on 2015-05-18
A number of your problems might be due to old configuration settings that aren't compatible with the more recent XFCE version. I ended up deleting the xfce4 settings ~/.config folder. In fact, I think I may have just deleted ~/.config and started all over again with my application settings too. Lots of bits didn't work right immediately after the upgrade. I upgraded by doing a new install to / and then once I'm happy it works, edit /etc/fstab to bring in my /home partition and reboot.

---

### Post by Jonners59 on 2015-05-18
tgalati4
Thanks for the feedback

> **tgalati4 said:**
> Understand that there is no "second screen".   The Xorg Window Server uses a Super Desktop which is the summation of  your horizontal and vertical resolutions of both displays.  The two  screens become portholes to view parts of the same Super Desktop.  It's  possible that the icons you are trying to save are simply hidden.  Try  moving your displays so that they are side-by-side, or one on top of the  other.  Then observe where the launchers are placed when you create  them.  They don't behave the way you expect.  This is either a bug or a  feature.

That makes a lot of sense and ties in with my observations of the "2nd" screen.

As for the icons.  They appear on screen 1 but if I try and move them to screen 2, then they just fly back to their original position.  Note.  this is NOT all the time, but when it does happen it messes up my config file and I have to reset them all after a login that works.  And apologies for using 1st and 2nd screen, but that's the best way to describe.

It is as if sometimes something is not loading correctly, probably in x11 or Lightdim or nVidia...  Beyond me.

> **tgalati4 said:**
> 
As far as determining which drive is which:

```
sudo fdisk -l
```

/dev/sda is the first disk on your system.
/dev/sdb is the second disk on your system.

/dev/sda is the one that I suspect has a cable issue.

I'll take a look at the cable on sda.......


```
 sudo fdisk -l

Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000a9a63

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048 350824447 350822400 167.3G  7 HPFS/NTFS/exFAT
/dev/sda2       350826494 455583743 104757250    50G  5 Extended
/dev/sda4       455583744 488396799  32813056  15.7G 82 Linux swap / Solaris
/dev/sda5  *    350828544 455583743 104755200    50G 83 Linux

Partition table entries are not in disk order.
Disk /dev/sdb: 465.8 GiB, 500106780160 bytes, 976771055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0009f620

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1              63 566050815 566050753 269.9G 83 Linux
/dev/sdb3       566050816 771809279 205758464  98.1G  7 HPFS/NTFS/exFAT
/dev/sdb4       771810795 976768064 204957270  97.7G  5 Extended
/dev/sdb5       771813376 976766975 204953600  97.7G 83 Linux

```

Cheers

jonners59

---

### Post by Jonners59 on 2015-05-18
> **The Cog said:**
> A number of your problems might be due to old configuration settings that aren't compatible with the more recent XFCE version. I ended up deleting the xfce4 settings ~/.config folder. In fact, I think I may have just deleted ~/.config and started all over again with my application settings too. Lots of bits didn't work right immediately after the upgrade. I upgraded by doing a new install to / and then once I'm happy it works, edit /etc/fstab to bring in my /home partition and reboot.

That is much the same as I did....  As per, it may be something else.  Nvidia is notoriously difficult, and there was a bug out about it not working after the upgrade to 14.10 and that may have continued on to 15.04 in some way.

---

### Post by Jonners59 on 2015-05-19
So first of all, I created a thread to fix the LibreOffice problem - seems that i am not the only one with this, and found a website with the solution.  So that is fixed, here
[http://ubuntuforums.org/showthread.php?t=2278818](http://ubuntuforums.org/showthread.php?t=2278818)

OK, this am, first boot up the 2nd screen would/does not allow the icons on it.  Screenlets are all fine now and seem to work every time.  So, hopefully in here somewhere there must be something that explains why it should be failing - the system log.


Error messages I could find:
[HTML]May 19 07:20:14 Baroni-PC whoopsie[882]: [07:20:14] Could not get the Network Manager state:
May 19 07:20:14 Baroni-PC whoopsie[882]: [07:20:14] GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files[/HTML]

[HTML]May 19 07:20:15 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 863]: Unknown error -2[/HTML]

[HTML]May 19 07:20:17 Baroni-PC gpu-manager[878]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf[/HTML]

[HTML]May 19 07:20:18 Baroni-PC NetworkManager[873]: <error> [1432016418.988851] [dns-manager/nm-dns-dnsmasq.c:398] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name[/HTML]

[HTML]May 19 07:20:15 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 863]: Unknown error -2
May 19 07:20:23 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 1005]: Unknown error -2[/HTML]

[HTML]May 19 07:20:51 Baroni-PC freshclam[875]: Downloading daily.cvd [100%]May 19 07:20:53 Baroni-PC ca.desrt.dconf[1297]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.May 19 07:20:53 Baroni-PC org.gtk.vfs.Daemon[1297]: A connection to the bus can't be madeMay 19 07:20:53 Baroni-PC org.gtk.vfs.Daemon[1297]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.[/HTML]

[HTML]May 19 07:20:59 Baroni-PC freshclam[875]: ERROR: NotifyClamd: Can't find or parse configuration file /etc/clamav/clamd.conf[/HTML]

[HTML]May 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead: /home/baronipc/Desktop/Documents/Documents/Dropbox/Images for appearence/Jonathan Harrison.JPG: Error retrieving chunk extents: Operation not supportedMay 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead: /home/baronipc/Desktop/Documents/Documents/Dropbox/Images for appearence/Photos/IMG_20110904_154245.jpg: Error retrieving chunk extents: Operation not supportedMay 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead: /home/baronipc/Desktop/Documents/Documents/Dropbox/Images for appearence/Photos/Jonathan & William: Error retrieving chunk extents: Operation not supportedMay 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead:samba: Ignored relative pathMay 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead:samba: Ignored relative pathMay 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead:.xsession-errors: Ignored relative pathMay 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead:.: Ignored relative pathMay 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead:tracing_on: Ignored relative pathMay 19 07:21:20 Baroni-PC ureadahead[271]: ureadahead:events/fs/open_exec/enable: Ignored relative path[/HTML]

and there are a lot of ureadahead lines....

Warning messages:

[HTML]May 19 07:20:09 Baroni-PC kernel: [    6.920298] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\_SB_.PCI0.SBRG.GPBX) (20141107/utaddress-258)May 19 07:20:09 Baroni-PC kernel: [    6.920303] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driverMay 19 07:20:09 Baroni-PC kernel: [    6.920305] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\_SB_.PCI0.SBRG.GPBX) (20141107/utaddress-258)May 19 07:20:09 Baroni-PC kernel: [    6.920307] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driverMay 19 07:20:09 Baroni-PC kernel: [    6.920308] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\_SB_.PCI0.SBRG.GPBX) (20141107/utaddress-258)May 19 07:20:09 Baroni-PC kernel: [    6.920310] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000050f (\_GPE.GPIO) (20141107/utaddress-258)[/HTML]

[HTML]May 19 07:20:14 Baroni-PC freshclam[875]: WARNING: Can't query current.cvd.clamav.netMay 19 07:20:14 Baroni-PC freshclam[875]: WARNING: Invalid DNS reply. Falling back to HTTP mode.May 19 07:20:14 Baroni-PC freshclam[875]: WARNING: Can't get information about db.local.clamav.net: Temporary failure in name resolutionMay 19 07:20:14 Baroni-PC freshclam[875]: WARNING: Can't download main.cvd from db.local.clamav.netMay 19 07:20:14 Baroni-PC freshclam[875]: Trying again in 5 secs...[/HTML]

[HTML]May 19 07:20:15 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 863]: Unknown error -2[/HTML]

[HTML]May 19 07:20:16 Baroni-PC exportfs[1014]: exportfs: No options for /home/baronipc/Desktop/Documents : suggest (sync) to avoid warning[/HTML]

[HTML]May 19 07:20:19 Baroni-PC dnsmasq[1096]: warning: no upstream servers configured[/HTML]

[HTML]May 19 07:20:23 Baroni-PC colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1May 19 07:20:15 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 863]: Unknown error -2May 19 07:20:23 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 1005]: Unknown error -2[/HTML]

[HTML]May 19 07:21:58 Baroni-PC rtkit-daemon[1454]: Supervising 1 threads of 1 processes of 1 users.
May 19 07:22:00 Baroni-PC org.gnome.zeitgeist.Engine[1654]: ** (zeitgeist-datahub:2084): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus![/HTML]

I am not convinced the nVidia card sw is installed correctly, on the basis that the settings manager is not complete, like I have on other machines.  Reinstalling can be quite a risk, especially on a hunch.

Any ideas, please?

---

### Post by tgalati4 on 2015-05-20
Well *colord* is the daemon that manages color profiles for printers and monitors.  It's possible that your video driver really is having problems.

---

### Post by Jonners59 on 2015-05-20
> **tgalati4 said:**
> Well *colord* is the daemon that manages color profiles for printers and monitors.  It's possible that your video driver really is having problems.

So you think it just might be this line
[HTML]May 19 07:20:15 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 863]: Unknown error -2 May 19 07:20:23 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 1005]: Unknown error -2 
[/HTML]

There have always been issues with nVidia cards, mostly blank screen after update/install, but I noticed that the manager was not complete when I opened it, which is something I have seen before and was advised by nVidia that it had not installed properly and to reinstall.  Not an easy thing and fraught with possible dangers.  But I will try and track down the lessons I had learnt and have a go.  Shall feed back what i did and if it worked.

Actually, on completing this reply, I was going to take a screen shot of it - before and after - but it has gone!!!  Checked the Menu Editor too, and it has definetly GONE!  ODD!

---

### Post by Jonners59 on 2015-05-22
> **Jonners59 said:**
> So you think it just might be this line
[HTML]May 19 07:20:15 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 863]: Unknown error -2 May 19 07:20:23 Baroni-PC colord[950]: (colord:950): Cd-WARNING **: failed to get session [pid 1005]: Unknown error -2 
[/HTML]

There have always been issues with nVidia cards, mostly blank screen after update/install, but I noticed that the manager was not complete when I opened it, which is something I have seen before and was advised by nVidia that it had not installed properly and to reinstall.  Not an easy thing and fraught with possible dangers.  But I will try and track down the lessons I had learnt and have a go.  Shall feed back what i did and if it worked.

Actually, on completing this reply, I was going to take a screen shot of it - before and after - but it has gone!!!  Checked the Menu Editor too, and it has definitely GONE!  ODD!

OK, I think I have success.
Simply I reinstalled the nVidia drivers..  As follows:

First remind yourself which card you have:
```
lspci -vnn | grep -i VGA -A 12
```

Then install the nVidia repository
```
sudo add-apt-repository ppa:xorg-edgers/ppa -y
```
And quick update:
```
sudo apt-get update
```

Then follow the link to the nVidia website, fill in the drop down questions to find the correct driver.  No need to download it, just note the number.
[http://www.nvidia.com/Download/index.aspx?ClickID=arrzsn0oksvnwspz0ykprt5pslvyvvsnosks](http://www.nvidia.com/Download/index.aspx?ClickID=arrzsn0oksvnwspz0ykprt5pslvyvvsnosks)

Then enter the cmd as below with the correct number in terminal - mine was 346 - to download and install the driver
```
sudo apt-get install nvidia-346
```
For safety and luck would have it, this worked better for me, I also did the following which installed a later version
```
sudo apt-get install nvidia-current
```

Then go in to Synaptic package manager (if you do not have it yet, then this is a good time to install the vital app) and then in to Settings -> Repositories -> Additional Drivers
Choose your driver and "Apply Changes".

Thanks **tgalati4** for helping identify the problem.

---

### Post by Bucky Ball on 2015-05-22
Excellent news, great persistence and well done to all! Have been following with interest. Thanks for marking as solved as this thread could certainly help future fellow travelers. Enjoy. ;)

---

