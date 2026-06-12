---
title: "Can't get my screen over 800x600"
date: 2009-03-11
forum: General Help
---

### Post by Daywalker42 on 2009-03-11
I have just started using ubuntu in the last week, at the advice of a friend, I downloaded ubuntu and virual box, so I can try linux out before wiping my drive. I cannot get the settings to allow me to go to my monitor's 1280x800 max. I have tried several things, and have looked around the forums for a solution, and have tried modifying the xorg file. Does anyone have any ideas??

---

### Post by cariboo on 2009-03-11
If you go to System-->Administration-->Hardware Drivers, is there a recommended driver for your graphics adapter?

I would suggest you dual boot, instead of wiping windows from your hard drive. You never know when you will need WIndows to fall back on if something doesn't work as expected.

Running Ubuntu in a vm does not give you a true idea of how it will run on your computer as it is using virtual hardware. I would suggest booting up the LiveCD and make sure all your harware is detected and working. Using the LiveCD doesn't change anything on your hard drive so it is safe to use Ubuntu,

Jim

---

### Post by Nxion on 2009-03-11
May I suggest going another route?

Check this out - [http://wubi-installer.org/](http://wubi-installer.org/)

This will install Ubuntu in Windows like an application. It will set it up so you can either boot to Ubuntu or Windows. And after you try it and figure that Ubuntu is not for you, you can uninstall it and its gone. This will let you dual boot with out having to worry about messing with partitions.

---

### Post by markofealing on 2009-03-11
I know the feeling, it can be a pain, however there is a utility called XRANDR which can help fix the problem. I'm assuming that you are using an open source graphics driver rather than one supplied by Nvidia or ATI. If unsure check xorg.conf and under the "device" section check what it says for "Driver". For an ati card it should say radeon.

I've currently writing some documentation on it's use, I've reproduced it below. Please note that making the changes permanent in xorg.conf seems to be tempremetal. I'm looking at using the xrandr command to change mode in a script which will automatically run at start-up to set my monitor to 1280x1024:



**[SIZE="6"]How to Use XRANDR to Manage your Monitors[/SIZE]**



Introduction

Since late 2007, most modern Linux distributions have shipped with XRANDR which provides computer monitor auto-detection and in most instances avoids the need to edit the xorg.conf file to get the correct layout and resolution. Therefore, on a modern Linux distribution, the contents of xorg.conf are minimal.

However, sometimes computer monitors will fail to correctly report their EDID information, resulting in a incomplete list of resolutions for RANDR to utilise.

This “How to...” will show you how to test configure your monitors using RANDR and then show how to take that configuration information and place it in xorg.conf to make it work every time your PC is booted.

For the following example, the PC is configured wit the following hardware:

ATI Radeon 9600 with VGA, DVI and S-video outputs using the Ubuntu Radeon open source driver

Main Monitor – Hitachi 17MVXPro2 (CM1711ME) which is a CRT with VGA plug
			Synch:		Horizontal: 24.8 – 82kHz
						Vertical: 50 – 120Hz
			Max Resolution: 	1280x1024
		
Secondary – HP F70 which is a 17” TFT with DVI plug
			Max Resolution: 	1280x1024 @ 75Hz (native)

This documentation was written for verson 1.2 of xrandr, to check you version go to Terminal and enter

 xrandr -v
you should get something similar to 

	Server reports RandR version 1.2 

The main reference source for this guide is the Debian [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

Finally, XRANDR will only work with the open source drivers. The proprietary drivers from the likes of ATI and Nvidia come with their own set of command line utilities and graphical interfaces.
How to....
To establish what graphics card you have and whether the second video output has been detected correctly enter 

lspci

In the list of devices you will find something like this:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600] 
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary) 

In this particular example we have an ATI Radeon 9600 (also known as RV350) with two outputs, and although not detected by lspci, there is actually a S-video output as we shall see later.

From Terminal to display the display and resolution settings which have been automatically detected enter

xrandr -q

You will get something like this displayed

Screen 0: minimum 320 x 200, current 2048 x 768, maximum 3000 x 2000 
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
DVI-0 connected 1024x768+1024+0 (normal left inverted right x axis y axis) 359mm x 287mm 
   1280x1024      60.0 +   60.0     60.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis) 

Each output is given a name, in the case of ATI graphics cards the 15-pin VGA 'D' socket is called VGA-0 and the DVI socket is called DVI-0. The S-video output has been detected, but is showing as disconnected. This is because nothing is plugged in to it.

Notice at the top of the command output that there is one screen which is called “Screen 0” and is allocated minimum, current and maximum sizes. 

Screen 0: minimum 320 x 200, current 2048 x 768, maximum 3000 x 2000 

The maximum size is set in /etc/X11/xorg.conf in the line Virtual 3000 2000, see the example below:

Section "Screen" 
        Identifier      "Configured Screen Device" 
        Device  "Configured Video Device" 
        SubSection "Display" 
                Virtual 3000 2000 
        EndSubSection 
EndSection 

Whilst it used to be necessary to configure your Keyboard, Display and Mouse through xorg.conf. In a standard configuration xrandr looks after the device “hot-plugging” and on the basis it gets the right information from the devices e.g. monitors, editing this file is not necessary. See Wikipedia for more information [http://en.wikipedia.org/wiki/Xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf).

In the above example, whilst the of the DVI-0 attached monitor's preferred mode  is 1280x1024 (marked with the + sign), it is defaulted to 1024x768 (marked with the * sign).
Change a Monitors Resolution Mode
To change the mode of the monitor attached to DVI-0 to its preferred resolution of 1280x1024, from Terminal enter:

xrandr --output DVI-0 --mode 1280x1024 

The displays should flicker and the monitor's resolution on DVI-0 should change to 1280x1024. If you now do a

xrandr -q 
the output for the line 1280x1024 should now look like

   1280x1024      60.0*+   60.0     60.0* 

Notice the location of the *.
Defining New Resolution Modes
As well as changing the resolution mode you can also define new resolution modes. 

NOTE: Please be aware that these have to be within the technical specifications of your monitor otherwise you can damage it. Check the manufactures specifications before making these changes.

If a Resolution Mode already exists, but is assigned to a different output, you can add it to another output by entering xrandr --addmode <output> --mode <mode>

However, in our example, the monitor in VGA-0 can run at 1024x768@75Hz rather than the 1024x768@60 Hz it is currently set. As there isn't a 75Hz option for this resolution but there is for the DVI-0 output we will need to assign this resolution  to the VGA-0 output. However, in our case there is a complication as there is already a 1024x768 setting with the same name which is incorrect and furthermore we are already using this setting for VGA-0.

If this wasn't a setting generated by the monitors EDID information then we could have:

1.change the mode of VGA-0 to 1152x864 by entering 
xrandr --output VGA-0 --mode 1152x864

2.Delete the old resolution mode for VGA-0 by entering
xrandr --delmode VGA-0 1024x768 

3.add in the resolution mode from DVI-0
xrandr –addmode VGA-0 1024x768

If you were to try to delete a EDID generated mode then you would get  an error similar to the following

X Error of failed request:  BadAccess (attempt to access private resource denied) 
Major opcode of failed request:  153 (RANDR) 
Minor opcode of failed request:  19 () 
Serial number of failed request:  16 
Current serial number in output stream:  17 

So, the way to get around this problem is to define a new resolution mode using the command 

	xrandr --newmode <ModeLine>
where <ModeLine> is the output from either GTF [http://GTF.sourceforge.net/](http://GTF.sourceforge.net/) or CVT [http://linux.die.net/man/1/cvt](http://linux.die.net/man/1/cvt) . Both utilities can be used to calculate VESA timing modes.

Here we will use GTF to produce the ModeLine and this is where the specifications of your monitor are required!

From Terminal enter

man gtf
this will display the Manual page for GTF. More detail on ModeLines and how to read them can be found at [http://m.domaindlx.com/LinuxHelp/resources/modelines.htm](http://m.domaindlx.com/LinuxHelp/resources/modelines.htm).

To calculate ModeLine settings for our monitor on VGA-0 we need to enter the following, bearing in mind the resolution limitations of your particular monitor, where 1024 is the horizontal resolution, 768 the vertical and 75 is the refresh rate.

gtf 1024 768 75 
The following result is returned.

# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz 
Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync 

As a double-check, ensure the hsync rate falls within the specification of your monitor. In our example this is fine as the monitor is rated from 24.8 - 82kHz

Now copy and past information on the second line of the result, after Modline, into the command --newmode so it looks like. Note that the "1024x768_75.00" will be the new name of the mode.

	xrandr --newmode "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
Now  as this  mode has not been assigned to any output, it will appear at the bottom of the list  if you were to enter xrandr -q at this point.

To add it to the VGA-0 output enter

xrandr –addmode VGA-0 1024x768_75.00
If you now do a xrandr -q you will see under VGA-0, at the bottom of the list of modes

1024x768_75.00   75.0 

Now make this mode the current mode for VGA-0 by entering

xrandr --output VGA-0 --mode 1024x768_75.00

Making the XRANDR settings Permanent (xorg.conf)
Whilst it can be convenient to change the monitor configuration on the fly, in fact there is no reason why you could not create a script to set-up the display settings, for most situations you would want the same settings every time your X server is started. It is at this point, having done the groundwork, we now look to xorg.conf to provide a permanent configuration.

Because on most modern Linux distros the xorg.conf file is virtually empty of settings the first thing you will need to do is generate a new file containing the settings from X.org.log file. However, if you are running an Ubuntu based distribution you will first need to install pp by entering in Terminal

sudo apt-get install libpar-packer-perl 
Once installed enter

cd /var/log
sudo pp Xorg.0.log Xorg.1.log 
you may get an error message /usr/bin/pp: Input file Xorg.1.log was not found , ignore and  enter

sudo Xorg -configure :1
Your screens will flicker and the following will be displayed

Your xorg.conf file is /home/fernsm1/xorg.conf.new 

To test the server, run 'X -config /home/fernsm1/xorg.conf.new' 

Enter cd to change to your home directory, and edit xorg.conf.new using your favourite text exitor.
Gtf 
Section "Device" 
	Identifier  "Card0" 
	Driver      "radeon" 
	BoardName   "RV350 AQ [Radeon 9600]" 
	BusID       "PCI:1:0:0" 
EndSection 

Section "Screen" 
	Identifier	"Configured Screen Device" 
	Device	"Card0" 
	SubSection "Display" 
		Virtual	3000 2000 
	EndSubSection 
EndSection 

Section "Monitor" 
    Identifier      "VGA-0" 
    Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync 
    Option "PreferredMode" "1024x768_75.00" 
EndSection 

Section "Monitor" 
    Identifier      "DVI-0" 
    Option "PreferredMode" "1280x1024" 
EndSection

---

### Post by wpshooter on 2009-03-11
> **Daywalker42 said:**
> I have just started using ubuntu in the last week, at the advice of a friend, I downloaded ubuntu and virual box, so I can try linux out before wiping my drive. I cannot get the settings to allow me to go to my monitor's 1280x800 max. I have tried several things, and have looked around the forums for a solution, and have tried modifying the xorg file. Does anyone have any ideas??

Have you tried to install from the ALTERNATE (texted based) CD version of Ubuntu instead of the live/desktop CD version ?

---

### Post by Neo_The_User on 2009-03-11
> **markofealing said:**
> I know the feeling, it can be a pain, however there is a utility called XRANDR which can help fix the problem. I'm assuming that you are using an open source graphics driver rather than one supplied by Nvidia or ATI. If unsure check xorg.conf and under the "device" section check what it says for "Driver". For an ati card it should say radeon.

I've currently writing some documentation on it's use, I've reproduced it below. Please note that making the changes permanent in xorg.conf seems to be tempremetal. I'm looking at using the xrandr command to change mode in a script which will automatically run at start-up to set my monitor to 1280x1024:



**[SIZE="6"]How to Use XRANDR to Manage your Monitors[/SIZE]**



Introduction

Since late 2007, most modern Linux distributions have shipped with XRANDR which provides computer monitor auto-detection and in most instances avoids the need to edit the xorg.conf file to get the correct layout and resolution. Therefore, on a modern Linux distribution, the contents of xorg.conf are minimal.

However, sometimes computer monitors will fail to correctly report their EDID information, resulting in a incomplete list of resolutions for RANDR to utilise.

This “How to...” will show you how to test configure your monitors using RANDR and then show how to take that configuration information and place it in xorg.conf to make it work every time your PC is booted.

For the following example, the PC is configured wit the following hardware:

ATI Radeon 9600 with VGA, DVI and S-video outputs using the Ubuntu Radeon open source driver

Main Monitor – Hitachi 17MVXPro2 (CM1711ME) which is a CRT with VGA plug
			Synch:		Horizontal: 24.8 – 82kHz
						Vertical: 50 – 120Hz
			Max Resolution: 	1280x1024
		
Secondary – HP F70 which is a 17” TFT with DVI plug
			Max Resolution: 	1280x1024 @ 75Hz (native)

This documentation was written for verson 1.2 of xrandr, to check you version go to Terminal and enter

 xrandr -v
you should get something similar to 

	Server reports RandR version 1.2 

The main reference source for this guide is the Debian [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

Finally, XRANDR will only work with the open source drivers. The proprietary drivers from the likes of ATI and Nvidia come with their own set of command line utilities and graphical interfaces.
How to....
To establish what graphics card you have and whether the second video output has been detected correctly enter 

lspci

In the list of devices you will find something like this:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600] 
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary) 

In this particular example we have an ATI Radeon 9600 (also known as RV350) with two outputs, and although not detected by lspci, there is actually a S-video output as we shall see later.

From Terminal to display the display and resolution settings which have been automatically detected enter

xrandr -q

You will get something like this displayed

Screen 0: minimum 320 x 200, current 2048 x 768, maximum 3000 x 2000 
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
DVI-0 connected 1024x768+1024+0 (normal left inverted right x axis y axis) 359mm x 287mm 
   1280x1024      60.0 +   60.0     60.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis) 

Each output is given a name, in the case of ATI graphics cards the 15-pin VGA 'D' socket is called VGA-0 and the DVI socket is called DVI-0. The S-video output has been detected, but is showing as disconnected. This is because nothing is plugged in to it.

Notice at the top of the command output that there is one screen which is called “Screen 0” and is allocated minimum, current and maximum sizes. 

Screen 0: minimum 320 x 200, current 2048 x 768, maximum 3000 x 2000 

The maximum size is set in /etc/X11/xorg.conf in the line Virtual 3000 2000, see the example below:

Section "Screen" 
        Identifier      "Configured Screen Device" 
        Device  "Configured Video Device" 
        SubSection "Display" 
                Virtual 3000 2000 
        EndSubSection 
EndSection 

Whilst it used to be necessary to configure your Keyboard, Display and Mouse through xorg.conf. In a standard configuration xrandr looks after the device “hot-plugging” and on the basis it gets the right information from the devices e.g. monitors, editing this file is not necessary. See Wikipedia for more information [http://en.wikipedia.org/wiki/Xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf).

In the above example, whilst the of the DVI-0 attached monitor's preferred mode  is 1280x1024 (marked with the + sign), it is defaulted to 1024x768 (marked with the * sign).
Change a Monitors Resolution Mode
To change the mode of the monitor attached to DVI-0 to its preferred resolution of 1280x1024, from Terminal enter:

xrandr --output DVI-0 --mode 1280x1024 

The displays should flicker and the monitor's resolution on DVI-0 should change to 1280x1024. If you now do a

xrandr -q 
the output for the line 1280x1024 should now look like

   1280x1024      60.0*+   60.0     60.0* 

Notice the location of the *.
Defining New Resolution Modes
As well as changing the resolution mode you can also define new resolution modes. 

NOTE: Please be aware that these have to be within the technical specifications of your monitor otherwise you can damage it. Check the manufactures specifications before making these changes.

If a Resolution Mode already exists, but is assigned to a different output, you can add it to another output by entering xrandr --addmode <output> --mode <mode>

However, in our example, the monitor in VGA-0 can run at 1024x768@75Hz rather than the 1024x768@60 Hz it is currently set. As there isn't a 75Hz option for this resolution but there is for the DVI-0 output we will need to assign this resolution  to the VGA-0 output. However, in our case there is a complication as there is already a 1024x768 setting with the same name which is incorrect and furthermore we are already using this setting for VGA-0.

If this wasn't a setting generated by the monitors EDID information then we could have:

1.change the mode of VGA-0 to 1152x864 by entering 
xrandr --output VGA-0 --mode 1152x864

2.Delete the old resolution mode for VGA-0 by entering
xrandr --delmode VGA-0 1024x768 

3.add in the resolution mode from DVI-0
xrandr –addmode VGA-0 1024x768

If you were to try to delete a EDID generated mode then you would get  an error similar to the following

X Error of failed request:  BadAccess (attempt to access private resource denied) 
Major opcode of failed request:  153 (RANDR) 
Minor opcode of failed request:  19 () 
Serial number of failed request:  16 
Current serial number in output stream:  17 

So, the way to get around this problem is to define a new resolution mode using the command 

	xrandr --newmode <ModeLine>
where <ModeLine> is the output from either GTF [http://GTF.sourceforge.net/](http://GTF.sourceforge.net/) or CVT [http://linux.die.net/man/1/cvt](http://linux.die.net/man/1/cvt) . Both utilities can be used to calculate VESA timing modes.

Here we will use GTF to produce the ModeLine and this is where the specifications of your monitor are required!

From Terminal enter

man gtf
this will display the Manual page for GTF. More detail on ModeLines and how to read them can be found at [http://m.domaindlx.com/LinuxHelp/resources/modelines.htm](http://m.domaindlx.com/LinuxHelp/resources/modelines.htm).

To calculate ModeLine settings for our monitor on VGA-0 we need to enter the following, bearing in mind the resolution limitations of your particular monitor, where 1024 is the horizontal resolution, 768 the vertical and 75 is the refresh rate.

gtf 1024 768 75 
The following result is returned.

# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz 
Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync 

As a double-check, ensure the hsync rate falls within the specification of your monitor. In our example this is fine as the monitor is rated from 24.8 - 82kHz

Now copy and past information on the second line of the result, after Modline, into the command --newmode so it looks like. Note that the "1024x768_75.00" will be the new name of the mode.

	xrandr --newmode "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
Now  as this  mode has not been assigned to any output, it will appear at the bottom of the list  if you were to enter xrandr -q at this point.

To add it to the VGA-0 output enter

xrandr –addmode VGA-0 1024x768_75.00
If you now do a xrandr -q you will see under VGA-0, at the bottom of the list of modes

1024x768_75.00   75.0 

Now make this mode the current mode for VGA-0 by entering

xrandr --output VGA-0 --mode 1024x768_75.00

Making the XRANDR settings Permanent (xorg.conf)
Whilst it can be convenient to change the monitor configuration on the fly, in fact there is no reason why you could not create a script to set-up the display settings, for most situations you would want the same settings every time your X server is started. It is at this point, having done the groundwork, we now look to xorg.conf to provide a permanent configuration.

Because on most modern Linux distros the xorg.conf file is virtually empty of settings the first thing you will need to do is generate a new file containing the settings from X.org.log file. However, if you are running an Ubuntu based distribution you will first need to install pp by entering in Terminal

sudo apt-get install libpar-packer-perl 
Once installed enter

cd /var/log
sudo pp Xorg.0.log Xorg.1.log 
you may get an error message /usr/bin/pp: Input file Xorg.1.log was not found , ignore and  enter

sudo Xorg -configure :1
Your screens will flicker and the following will be displayed

Your xorg.conf file is /home/fernsm1/xorg.conf.new 

To test the server, run 'X -config /home/fernsm1/xorg.conf.new' 

Enter cd to change to your home directory, and edit xorg.conf.new using your favourite text exitor.
Gtf 
Section "Device" 
	Identifier  "Card0" 
	Driver      "radeon" 
	BoardName   "RV350 AQ [Radeon 9600]" 
	BusID       "PCI:1:0:0" 
EndSection 

Section "Screen" 
	Identifier	"Configured Screen Device" 
	Device	"Card0" 
	SubSection "Display" 
		Virtual	3000 2000 
	EndSubSection 
EndSection 

Section "Monitor" 
    Identifier      "VGA-0" 
    Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync 
    Option "PreferredMode" "1024x768_75.00" 
EndSection 

Section "Monitor" 
    Identifier      "DVI-0" 
    Option "PreferredMode" "1280x1024" 
EndSection

Wow! Nice guide! I'm going to use this!

---

