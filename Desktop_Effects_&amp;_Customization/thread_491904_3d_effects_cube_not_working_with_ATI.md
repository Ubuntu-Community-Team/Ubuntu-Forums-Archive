---
title: "3d effects cube not working with ATI"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by lukanikos on 2007-07-04
Hi

I have a problem with the 3d effects.
I downloaded Envy and installed it...from there I installed the ATI drivers and restart the system for me to be able to work with the 3d effects and there appeared the problem.."desktop effects arent working"
I get the messege
"The Composite extension is not available"


can someone help please

---

### Post by scxtt on 2007-07-04
you need to "turn off" composite in your /etc/X11/xorg.conf ... add this to the bottom of it:
```
Section "Extensions"
       Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
       Option  "AIGLX" "off"
EndSection
```

---

### Post by lukanikos on 2007-07-04
tried to change the last bit on the file with the one you gave me and got the following msg

Could not save the file /etc/X11/xorg.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

the command i found before changing it was 

Section "Extensions"
	Option "Composite" "Disable"
EndSection

without the rest you gave me

Section "ServerFlags"
       Option  "AIGLX" "off"
EndSection

---

### Post by lukanikos on 2007-07-04
seems to be read only

I cant do anything.....

The problem is still there..


Please can somebody help me??

---

### Post by KevinW on 2007-07-04
from the terminal type:    sudo gedit /etc/X11/xorg.conf

This will open up  your xorg.conf file and allow you to edit and save.

---

### Post by lukanikos on 2007-07-04
where is the terminal....?

Can you direct me please...

Thanks!!:p

---

### Post by jamesey on 2007-07-04
I had the same issue until I followed the instructions here. you don't have to go through with the compiz/beryl stuff. 

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by lukanikos on 2007-07-05
I had a problem after installing the ATI graphic card drivers with envy software on ubunto with the 3d effects would not work so I have uninstalled it with the same software(envy).
The First reboot after the uninstall with envy ubuntu wont start properly and keeps on entering into a command prompt enviroment.
How can I get it to work again properly by entering into the GUI environment?

---

### Post by lukanikos on 2007-07-05
> **jamesey said:**
> I had the same issue until I followed the instructions here. you don't have to go through with the compiz/beryl stuff. 

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

I changed
```
Section "Extensions"
       Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
       Option  "AIGLX" "off"
EndSection

```

I followed the first guide

```
Guide:

After installing Feisty, make sure your system is completely updated. Paste this into a terminal:

Code:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

First step is getting your drivers set up. To do this use the Restricted Driver Manager.

Code:

System >> Administration >> Restricted Drivers Manager

Enable your ATI driver (By clicking the little box) and let it do its thing. Once finished , reboot the computer and make sure fglrx loaded correctly. There should be an icon (small and green) in the notification area telling you that you have restricted modules loaded.

Now we need to install XGL.

Code:

sudo apt-get install xserver-xgl

Good now, XGL won't load on its own so we need to write a few scripts to have it start.

Code:

sudo gedit /usr/local/bin/startxgl.sh

Now copy and paste this into the file that pops up:

Code:

#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

SAVE THIS FILE! Once its done saving, make that fire executable (like a program) by pasting this into a terminal:

Code:

sudo chmod a+x /usr/local/bin/startxgl.sh

Now we need to make a way to start that session from your login menu, paste this into a terminal:

Code:

sudo gedit /usr/share/xsessions/xgl.desktop

And paste this into the file:

Code:

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

Now make this script executable by pasting this into a terminal:

Code:

sudo chmod a+x /usr/share/xsessions/xgl.desktop

Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close.

The first thing we need to do is add the security key, do this by pasting into a terminal:

Code:

sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -

Then type in:

Code:

sudo gedit /etc/apt/sources.list

This will open a file, add this to the very bottom by pasting:
Code:

deb http://download.tuxfamily.org/3v1deb feisty eyecandy

Then save and exit.

You will need to update again, so paste into a terminal:

Code:

sudo apt-get update



```

and I still get this messege while trying to enter System --->Preferences---->Desktop Effects 

```
"The Composite extension is not available"


```

How can I fix this problem in the end?

Is there a way to be fixed or I have to forget it.....?

---

### Post by stillwaters130 on 2007-07-05
I had the same problem you did.  You have to install the fglrx driver for your graphics card:
[http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty](http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty)

This link is unique; it's the only site I found that could help me.

You'll probably also need to create an xgl session, or at Ieast I had to to get 3d acceleration completely working.  You can do that here:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session)

To open the terminal, press alt+F2 and enter gnome-terminal.

If it ever says you don't have permissions to do something, enter sudo at the beginning of your command.

Hope this helps!

---

### Post by lukanikos on 2007-07-06
Hi stillwaters130

I installed the fglrx driver for the graphics card from:

```
Actually, my instructions are based on the howto I mentioned above. Please read it for more detail.

   1.

      Disable Composite extension by adding below lines in /etc/X11/xorg.conf.

      Section "Extensions"
          Option  "Composite" "Disable" 
      EndSection

   2.

      Install necessary tools.

      sudo apt-get update
      sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5
      sudo apt-get install linux-headers-$(uname -r) wget

   3.

      Download ATI driver.

      mkdir -p ~/fglrx
      cd ~/fglrx
      wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.35.5-x86.x86_64.run

   4.

      Remove existing *.deb.

      rm xorg-driver-fglrx*.deb
      rm fglrx-kernel-source*.deb
      rm fglrx-control*.deb

   5.

      Create .deb packages.

      sh ./ati-driver-installer-8.35.5-x86.x86_64.run --buildpkg Ubuntu/feisty

   6.

      Install the .deb packages.

      sudo dpkg -i xorg-driver-fglrx*.deb
      sudo dpkg -i fglrx-kernel-source*.deb
      sudo dpkg -i fglrx-amdcccle*.deb

   7.

      Remove exisiting fglrx driver in /usr/src.

      sudo rm /usr/src/fglrx-kernel*.deb

   8.

      Patch the display driver.

      cd ~/fglrx
      wget http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.35.5-for-2.6.20.patch
      cd /usr/src
      sudo cp fglrx.tar.bz2 fglrx.tar.bz2-original
      sudo tar xvjf fglrx.tar.bz2
      cd /usr/src/modules/fglrx
      sudo patch -p0 < ~/fglrx/fglrx-8.35.5-for-2.6.20.patch
      cd /usr/src
      sudo tar cvjf fglrx.tar.bz2 modules/fglrx

   9.

      Compile and install fglrx module.

      sudo module-assistant prepare
      sudo module-assistant update
      sudo module-assistant build fglrx
      sudo module-assistant install fglrx

  10.

      Disable fglrx bundled with linux-restricted-module by adding fglrx to /etc/default/linux-restricted-modules-common.

      DISABLED_MODULES="fglrx"

  11.

      Regenerate module dependencies.

      sudo depmod -a

  12.

      Modify /etc/X11/xorg.conf to use fglrx instead. You may safely use my configuration as follows.

      Section "ServerLayout"
          Identifier     "Default Layout"
          Screen         "Default Screen" 0 0
          InputDevice    "Generic Keyboard"
          InputDevice    "Configured Mouse"
          InputDevice    "stylus" "SendCoreEvents"
          InputDevice    "cursor" "SendCoreEvents"
          InputDevice    "eraser" "SendCoreEvents"
          InputDevice    "Synaptics Touchpad"
      EndSection
      Section "Files"
          FontPath     "/usr/share/fonts/X11/misc"
          FontPath     "/usr/share/fonts/X11/cyrillic"
          FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
          FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
          FontPath     "/usr/share/fonts/X11/Type1"
          FontPath     "/usr/share/fonts/X11/100dpi"
          FontPath     "/usr/share/fonts/X11/75dpi"
          FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
      EndSection
      Section "Module"
          Load  "bitmap"
          Load  "dbe"
          Load  "ddc"
          Load  "dri"
          Load  "extmod"
          Load  "freetype"
          Load  "glx"
          Load  "int10"
          Load  "type1"
          Load  "vbe"
      EndSection
      Section "InputDevice"
          Identifier  "Generic Keyboard"
          Driver      "kbd"
          Option      "CoreKeyboard"
          Option      "XkbRules" "xorg"
          Option      "XkbModel" "pc104"
          Option      "XkbLayout" "us"
      EndSection
      Section "InputDevice"
          Identifier  "Configured Mouse"
          Driver      "mouse"
          Option      "CorePointer"
          Option      "Device" "/dev/input/mice"
          Option      "Protocol" "ExplorerPS/2"
          Option      "ZAxisMapping" "4 5"
          Option      "Emulate3Buttons" "true"
      EndSection
      Section "InputDevice"
          Identifier  "Synaptics Touchpad"
          Driver      "synaptics"
          Option      "SendCoreEvents" "true"
          Option      "Device" "/dev/psaux"
          Option      "Protocol" "auto-dev"
          Option      "HorizScrollDelta" "0"
      EndSection
      Section "InputDevice"
          Identifier  "stylus"
          Driver      "wacom"
          Option      "Device" "/dev/wacom"       # Change to 
          Option      "Type" "stylus"
          Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
      EndSection
      Section "InputDevice"
          Identifier  "eraser"
          Driver      "wacom"
          Option      "Device" "/dev/wacom"       # Change to 
          Option      "Type" "eraser"
          Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
      EndSection
      Section "InputDevice"
          Identifier  "cursor"
          Driver      "wacom"
          Option      "Device" "/dev/wacom"       # Change to 
          Option      "Type" "cursor"
          Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
      EndSection
      Section "Monitor"
          Identifier   "Builtin LCD"
          HorizSync    28.0 - 70.0
          VertRefresh  43.0 - 60.0
          Option      "DPMS"
      EndSection
      Section "Device"
          Identifier  "ATI Technologies Inc M22 [Radeon Mobility M300]"
          Driver      "fglrx"
          Option      "VideoOverlay" "on"
          Option      "OpenGLOverlay" "off"
          BusID       "PCI:1:0:0"
      EndSection
      Section "Screen"
          Identifier "Default Screen"
          Device     "ATI Technologies Inc M22 [Radeon Mobility M300]"
          Monitor    "Builtin LCD"
          DefaultDepth     24
          SubSection "Display"
                  Depth     1
                  Modes    "1400x1050"
          EndSubSection
          SubSection "Display"
                  Depth     4
                  Modes    "1400x1050"
          EndSubSection
          SubSection "Display"
                  Depth     8
                  Modes    "1400x1050"
          EndSubSection
          SubSection "Display"
                  Depth     15
                  Modes    "1400x1050"
          EndSubSection
          SubSection "Display"
                  Depth     16
                  Modes    "1400x1050"
          EndSubSection
          SubSection "Display"
                  Depth     24
                  Modes    "1400x1050"
          EndSubSection
      EndSection
      Section "DRI"
          Mode         0666
      EndSection
      Section "Extensions"
          Option      "Composite" "Disable"
      EndSection

  13.

      Optionally, add fglrx to /etc/modules. Note that you should not need to do it but give it a try if fglrx is not loaded automatically.

      lp
      psmouse
      sbp2
      sr_mod
      rtc
      fuse
      fglrx

  14.

      Reboot your computer.




```

After reboot the computer is with black screen and wont start.....


I think Ubuntu doesn't like my ATI card.

---

### Post by stillwaters130 on 2007-07-06
After you reboot, do you get to the login screen first, and then go black after you login?  Or does it go black before you can even do that?

---

### Post by lukanikos on 2007-07-06
No login screen 
Just ubuntu boot line
Then black

---

### Post by lukanikos on 2007-07-06
do I have to reinstall ubuntu or there is a way to restore the whole thing?

---

### Post by stillwaters130 on 2007-07-06
This sounds like your problem:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/95874](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/95874)

I don't think that you have to reinstall ubuntu, you just need access to your files.  Did you install ubuntu using a live cd?  If not, then download it ([https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)) and boot to the cd (you can change the boot order in your bios).  You'll have the option to install, but don't.

Open the terminal, and enter this command:
sudo dpkg-reconfigure xserver-xorg

Use the defaults if you don't know what to enter.  Try keeping fglrx as your driver first, and if that doesn't work, try it with mesa.  After you're done going through that, reboot, take the cd out, and see if you can boot up :-)

I really hope this works for you!

---

### Post by lukanikos on 2007-07-06
Thanks a lot.....

I am in againand loging into obuntu but now I get this msg when I do: System--->Preferences---->Desktop Effects(more problems):

Desktop effects could not be be enabled


I really cant believe what is happening with this ATI card.....

I think there is no future for me and the ATI with Obuntu....

I am trying everithing but I think it dosen't really want me....

If you habe any ideas it will be really helpful.

---

### Post by lukanikos on 2007-07-06
Also when I try to go into the restricted drivers I get this msg for the first time...


Your hardware does not need any restricted drivers.

While before it was the ATi  restricted drivers


Is there a solution for all this problems or I need to change my graphic card?

---

### Post by stillwaters130 on 2007-07-06
Unfortunaly, because ati doesn't make open source drivers and thus don't cover every operating system, it's not surprising that ubuntu doesn't like ati cards too much.  It seems like a lot of people with ati cards have trouble with 3d effects in linux.  However, I don't think you need to go to the extreme of getting a new card... it probably will just take some more searching.  It took me almost 3 whole days to figure mine out :-/  There's probably a solution out there; it'll just take some digging to find.

Ok, I have some questions...

1) What did you do to get the black screen to go away and login?
2) What exactly is your card (model #)? i.e. I have an ATI Mobility Radeon X1400.  It's possible that you have an ati card that just isn't compatible with fglrx... in which case you're screwed, and you will have to either live without 3d or get a different graphics card... but for the moment we can hope that's not the case and see what we can do to get it working :)
3) Did you try reconfiguring xorg? (sudo dpkg-reconfigure xserver-xorg)  If you didn't, it seems to work better if you login into the failsafe terminal and do it that way.

---

### Post by scxtt on 2007-07-06
i could get 3d effects just fine using the radeon driver w/ my x850pro ... this was w/ 2 different distros that enable that stuff by default - PCLOS2007 and Sabayon 3.2 ... i've NEVER felt compelled to get beryl running on a OS that doesn't do it 'out of the box' ...

i would concentrate on getting it working w/ the radeon driver and seeing if you can enable beryl ...

if i used fglrx, i had to use XGL
if i used radeon i could use AIGLX
^ as far as i can remember ...

---

### Post by lukanikos on 2007-07-07
1) What did you do to get the black screen to go away and login?

I did : sudo dpkg-reconfigure xserver-xorg  and then all the default except the 1024x768 resolution and auto detect monitor

2) What exactly is your card (model #)? i.e. I have an ATI Mobility Radeon X1400. It's possible that you have an ati card that just isn't compatible with fglrx... in which case you're screwed, and you will have to either live without 3d or get a different graphics card... but for the moment we can hope that's not the case and see what we can do to get it working

ATI Radeon 9600 series

3) Did you try reconfiguring xorg? (sudo dpkg-reconfigure xserver-xorg) If you didn't, it seems to work better if you login into the failsafe terminal and do it that way.

As I answered the first question I entered  sudo dpkg-reconfigure xserver-xorg from ubuntu rescue entrance and reconfigured 2 parts  the 1024x768 resolution and auto detect monitor.

How do I reconfigure the xorg and what exactly I need to do to fix it?

---

### Post by lukanikos on 2007-07-07
> **scxtt said:**
> i could get 3d effects just fine using the radeon driver w/ my x850pro ... this was w/ 2 different distros that enable that stuff by default - PCLOS2007 and Sabayon 3.2 ... i've NEVER felt compelled to get beryl running on a OS that doesn't do it 'out of the box' ...

i would concentrate on getting it working w/ the radeon driver and seeing if you can enable beryl ...

if i used fglrx, i had to use XGL
if i used radeon i could use AIGLX
^ as far as i can remember ...


Can you please be more specific on what I have to do?

---

### Post by scxtt on 2007-07-07
make sure the radeon driver is installed: **aptitude search xserver-xorg-driver-radeon** (should see an "i" in the leftmost column if it is) ...

run **sudo dpkg-reconfigure xserver-xorg** and you should have a choice for either "ati" or "radeon" ...

from what i can remember, the NEWER the version of fglrx, the less likely older ATI cards will still be supported - the AMD/ATI download site should say ...

i guess 1 good way to see if it's possible would be to download (and burn) an iso of PCLOS or Sabayon and see if it works ... that's what i did, i wasn't too big on the 3D desktop, effects - so there was no way i was going to go through the hassle of getting it working (having NO idea if it even would) on a distro that didn't do all the dirty work for me - Sabayon was the 1st to get it working (via fglrx) and PCLOS was the first that showed i could use AIGLX ... but in the end, i'm not finding any reason to use 3D desktop, effects ...

---

### Post by lukanikos on 2007-07-07
Here is what I get:


```
lukanikos@lukanikos:~$ aptitude search xserver-xorg-driver-radeon
v   xserver-xorg-driver-radeon  
```

 ```
You should choose this option if you would like to attempt to autodetect  &#9474;  
 &#9474; the recommended X server and driver module for your video card.  If the   &#9474;  
 &#9474; autodetection fails, you will be asked to specify the desired X server    &#9474;  
 &#9474; and/or driver module.  If it succeeds, further configuration questions    &#9474;  
 &#9474; about your video hardware will be pre-answered.                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you would rather select the X server and driver module yourself, do    &#9474;  
 &#9474; not choose this option.  You will not be asked to select the X server if  &#9474;  
 &#9474; there is only one available.                                              &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Attempt to autodetect video hardware?                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>   
```

I choose YES

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; For the X Window System graphical user interface to operate correctly,    &#9474;  
 &#9474; it is necessary to select a video card driver for the X server.           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Drivers are typically named for the video card or chipset manufacturer,   &#9474;  
 &#9474; or for a specific model or family of chipsets.                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; X server driver:                                                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                              apm              &#8593;                           &#9474;  
 &#9474;                              ark              &#9646;                           &#9474;  
 &#9474;                              ati              &#9618;                           &#9474;  
 &#9474;                              chips            &#9618;                           &#9474;  
 &#9474;                              cirrus           &#9618;                           &#9474;  
 &#9474;                              cyrix            &#8595;                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;


```

I choose ATI

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; The X server configuration file associates your video card with a name    &#9474;  
 &#9474; that you may provide.  This is usually the vendor or brand name followed  &#9474;  
 &#9474; by the model name, e.g., "Intel i915", "ATI RADEON X800", or "NVIDIA      &#9474;  
 &#9474; GeForce 6600".                                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Identifier for your video card:                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; ATI Technologies Inc RV350 AP [Radeon 9600]______________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;  
```

I choose OK
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; The X server configuration file associates your video card with a name    &#9474;  
 &#9474; that you may provide.  This is usually the vendor or brand name followed  &#9474;  
 &#9474; by the model name, e.g., "Intel i915", "ATI RADEON X800", or "NVIDIA      &#9474;  
 &#9474; GeForce 6600".                                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Identifier for your video card:                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; ATI Technologies Inc RV350 AP [Radeon 9600]______________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 You may wish to use the "lspci" command to determine the bus location of  &#9618;  
 &#9474; your PCI, AGP, or PCI-Express video card.                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; When possible, this question has been pre-answered for you and you        &#9646;  
 &#9474; should accept the default unless you know it doesn't work.                &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                       &#9474;                                                               &#9474;  
 &#9474;                                                                           &#9474;  
```

I choose OK

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; Video card's bus identifier:        &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474; PCI:1:0:0__________________________ &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
```


I choose OK

```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; Typically, the amount of dedicated memory used by the video card is       &#9474;  
 &#9474; autodetected by the X server, but some integrated video chips (such as    &#9474;  
 &#9474; the Intel i810) have little or no video memory of their own, and instead  &#9474;  
 &#9474; borrow main system memory for their needs.                                &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; This parameter should usually be left blank and specified only if the     &#9474;  
 &#9474; video card lacks RAM, or if the X server has trouble autodetecting the    &#9474;  
 &#9474; RAM size.                                                                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Amount of memory (kB) to be used by the video card:                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; _________________________________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;  
```

Blank the amount of memory and OK


```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Rather than communicating directly with the video hardware, the X server  &#9474;  
 &#9474; may be configured to perform some operations, such as video mode          &#9474;  
 &#9474; switching, via the kernel's framebuffer driver.                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; In theory, either approach should work, but in practice, sometimes one    &#9474;  
 &#9474; does and the other does not.  Enabling this option is the safe bet, but   &#9474;  
 &#9474; feel free to turn it off if it appears to cause problems.                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Use kernel framebuffer device interface?                                  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;                                                                           &#9474;  
```

 I choose NO

 ```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; The default keyboard layout selection for the Xorg server will be based   &#9474;  
 &#9474; on a combination of the language and the keyboard layout selected in the  &#9474;  
 &#9474; installer.                                                                &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Choose this option if you want the keyboard layout to be redetected.  Do  &#9474;  
 &#9474; not choose it if you want to keep your current layout.                    &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Autodetect keyboard layout?                                               &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;                                                                           &#9474;  
 
```


I choose NO

```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; For the X server to handle the keyboard correctly, a keyboard layout      &#9474;  
 &#9474; must be entered.  Available layouts depend on which XKB rule set and      &#9474;  
 &#9474; keyboard model were previously selected.                                  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Experienced users can use any layout supported by the selected XKB rule   &#9474;  
 &#9474; set.  If the xkb-data package has been unpacked, see the                  &#9474;  
 &#9474; /usr/share/X11/xkb/rules directory for available rule sets.               &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Users of U.S. English keyboards should enter "us".  Users of keyboards    &#9474;  
 &#9474; localized for other countries should generally enter their ISO 3166       &#9474;  
 &#9474; country code.  E.g., France uses "fr", and Germany uses "de".             &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Keyboard layout:                                                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; us_______________________________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>      
```


OK

                                                                                
```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; For the X server to handle the keyboard correctly, an XKB rule set must   &#9474;  
 &#9474; be chosen.                                                                &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Users of most keyboards should enter "xorg".  Users of Sun Type 4 and     &#9474;  
 &#9474; Type 5 keyboards, however, should enter "sun".                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Experienced users can use any defined XKB rule set.  If the xkb-data      &#9474;  
 &#9474; package has been unpacked, see the /usr/share/X11/xkb/rules directory     &#9474;  
 &#9474; for available rule sets.                                                  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; When in doubt, this value should be set to "xorg".                        &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; XKB rule set to use:                                                      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; xorg_____________________________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;  
```

OK

```
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; For the X server to handle the keyboard correctly, a keyboard model must  &#8593;  
 &#9474; be entered.  Available models depend on which XKB rule set is in use.     &#9646;  
 &#9474;                                                                           &#9618;  
 &#9474;  With the "xorg" rule set:                                                &#9618;  
 &#9474;  - pc101: traditional IBM PC/AT style keyboard with 101 keys, common in   &#9618;  
 &#9474;           the United States.  Has no "logo" or "menu" keys;               &#9618;  
 &#9474;  - pc104: similar to pc101 model, with additional keys, usually engraved  &#9618;  
 &#9474;           with a "logo" symbol and a "menu" symbol;                       &#9618;  
 &#9474;  - pc102: similar to pc101 and often found in Europe. Includes a "< >"    &#9618;  
 &#9474; key;                                                                      &#9618;  
 &#9474;  - pc105: similar to pc104 and often found in Europe. Includes a "< >"    &#9618;  
 &#9474; key;                                                                      &#9618;  
 &#9474;  - macintosh: Macintosh keyboards using the new input layer with Linux    &#9618;  
 &#9474;               keycodes;                            
 - macintosh_old: Macintosh keyboards not using the new input layer.      &#9618;  
 &#9474;  With the "sun" rule set:                                                 &#9618;  
 &#9474;  - type4: Sun Type4 keyboards;                                            &#9618;  
 &#9474;  - type5: Sun Type5 keyboards.                                            &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Laptop keyboards often do not have as many keys as standalone models;     &#9618;  
 &#9474; laptop users should select the keyboard model most closely approximated   &#9618;  
 &#9474; by the above.                                                             &#9646;  
 &#9474;                                                                           &#9618;  
 &#9474; Experienced users can use any model defined by the selected XKB rule      &#9618;  
 &#9474; set.  If the xkb-data package has been unpacked, see the                  &#9618;  
 &#9474; /usr/share/X11/xkb/rules directory for available rule sets.  

    Users of U.S. English keyboards should generally enter "pc104".  Users    &#9646;  
 &#9474; of most other keyboards should generally enter "pc105".                   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                      -
```                    
 

OK

```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; Keyboard model:                     &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474; pc105______________________________ &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>          
```

OK

                                                                                
```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; For the X server to handle the keyboard as desired, a keyboard variant    &#9474;  
 &#9474; may be entered.  Available variants depend on which XKB rule set, model,  &#9474;  
 &#9474; and layout were previously selected.                                      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Many keyboard layouts support an option to treat "dead" keys such as      &#9474;  
 &#9474; non-spacing accent marks and diaereses as normal spacing keys, and if     &#9474;  
 &#9474; this is the preferred behavior, enter "nodeadkeys".                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Experienced users can use any variant supported by the selected XKB       &#9474;  
 &#9474; layout.  If the xkb-data package has been unpacked, see the               &#9474;  
 &#9474; /usr/share/X11/xkb/symbols directory for the file corresponding to your   &#9474;  
 &#9474; selected layout for available variants.                                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Users of U.S. English keyboards should generally leave this entry blank.  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>   
```    

OK

---

### Post by lukanikos on 2007-07-07
```
                                                            
                    &#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; Keyboard variant:                   &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474; ___________________________________ &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;                     
                                                                                
```

OK


```
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; For the X server to handle the keyboard as desired, keyboard options may  &#8593;  
 &#9474; be entered.  Available options depend on which XKB rule set was           &#9646;  
 &#9474; previously selected.  Not all options will work with every keyboard       &#9618;  
 &#9474; model and layout.                                                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For example, if you wish the Caps Lock key to behave as an additional     &#9618;  
 &#9474; Control key, you may enter "ctrl:nocaps"; if you would like to switch     &#9618;  
 &#9474; the Caps Lock and left Control keys, you may enter "ctrl:swapcaps".       &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; As another example, some people prefer having the Meta keys available on  &#9618;  
 &#9474; their keyboard's Alt keys (this is the default), while other people       &#9618;  
 &#9474; prefer having the Meta keys on the Windows or "logo" keys instead.  If    &#9618;  
 &#9474; you prefer to use your Windows or logo keys as Meta keys, you may enter   &#9618;  
 &#9474; "altwin:meta_win". 


                                                <Ok>  
```

OK


```
  &#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; Keyboard options:                   &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474; ___________________________________ &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;                     
                                                                                

```

OK

 ```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; For the X Window System graphical user interface to operate correctly,    &#9474;  
 &#9474; certain characteristics of the mouse (or other pointing device, such as   &#9474;  
 &#9474; a trackball) must be known.                                               &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; It is necessary to determine which port (connection type) is used by the  &#9474;  
 &#9474; mouse. Serial ports use D-shaped connectors with 9 or 25 pins (a.k.a.     &#9474;  
 &#9474; DB-9 or DB-25); the mouse connector is female (has holes) and the         &#9474;  
 &#9474; computer connector is male (has pins).  PS/2 ports are small round        &#9474;  
 &#9474; connectors (DIN) with 6 pins; the mouse connector is male and the         &#9474;  
 &#9474; computer side female.  You may alternatively use a USB mouse, a           &#9474;  
 &#9474; bus/inport (very old) mouse, or be using the gpm program as a repeater.   &#9474;  
 &#9474; If you need to attach or remove PS/2 or bus/inport devices from your      &#9474;  
 &#9474; computer, please do so with the computer's power off.                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;  
```

OK

```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; Mouse port:                         &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;           /dev/input/mice           &#9474;                     
                    &#9474;           /dev/psaux                &#9474;                     
                    &#9474;           /dev/ttyS0                &#9474;                     
                    &#9474;           /dev/tts0                 &#9474;                     
                    &#9474;           /dev/gpmdata              &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```                     
                                                                                
                                                                                
Choose  /dev/input/mice and OK

 ```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474;                                     &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474; Mouse protocol:                     &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;            ImPS/2                   &#9474;                     
                    &#9474;            ExplorerPS/2             &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;   
``` 

Choose        ImPS/2    and OK

```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Most programs in the X Window System expect the mouse to have 3 buttons   &#9474;  
 &#9474; (left, right, and middle).  Mice with only 2 buttons can emulate the      &#9474;  
 &#9474; presence of a middle button by treating simultaneous clicks or drags of   &#9474;  
 &#9474; the left and right buttons as middle button events.                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; This option may also be used on mice with 3 or more buttons; the middle   &#9474;  
 &#9474; button will continue to work normally.                                    &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Note that mouse buttons in excess of five (counting a scroll wheel as     &#9474;  
 &#9474; two buttons, one each for "up" and "down", and a third if the wheel       &#9474;  
 &#9474; "clicks") are not yet supported with this configuration tool.             &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Emulate 3 button mouse?                                                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```  
           
                                                             
YES


```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; This option is recommended to experienced users only.  In most cases,     &#8593;  
 &#9474; all of these modules should be enabled.                                   &#9646;  
 &#9474;                                                                           &#9618;  
 &#9474;  - glx   : support for OpenGL rendering;                                  &#9618;  
 &#9474;  - dri   : support in the X server for DRI (Direct Rendering              &#9618;  
 &#9474; Infrastructure);                                                          &#9618;  
 &#9474;  - vbe   : support for VESA BIOS Extensions. Allows to query              &#9618;  
 &#9474;            the monitor capabilities via the video card;                   &#9618;  
 &#9474;  - ddc   : support for Data Display Channel, respectively. Allows to      &#9618;  
 &#9474; query                                                                     &#9618;  
 &#9474;            the monitor capabilities via the video card;                   &#9618;  
 &#9474;  - int10 : real-mode x86 emulator used to softboot secondary VGA cards.   &#9618;  
 &#9474;            Should be enabled if vbe is enabled;                           &#9618;  
 &#9474;  - dbe   : enables the double-buffering extension in the server.          
             Useful for animation and video operations;                     &#9618;  
 &#9474;  - extmod: enables many traditional and commonly used extensions, such    &#9618;  
 &#9474; as                                                                        &#9618;  
 &#9474;            shaped windows, shared memory, video mode switching, DGA, and  &#9618;  
 &#9474; Xv;                                                                       &#9618;  
 &#9474;  - record: implements the RECORD extension, often used in server          &#9618;  
 &#9474; testing;                                                                  &#9618;  
 &#9474;  - bitmap: font rasterizer (so are freetype, and type1 modules).          &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For further information about these modules, please consult the X.Org     &#9646;  
 &#9474; documentation.                                                            &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                    
```

OK

                                                                       
```
          &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;           
          &#9474; X.Org server modules that should be loaded by default:  &#9474;           
          &#9474;                                                         &#9474;           
          &#9474;    [*] bitmap                                           &#9474;           
          &#9474;    [ ] dbe                                              &#9474;           
          &#9474;    [*] ddc                                              &#9474;           
          &#9474;    [*] dri                                              &#9474;           
          &#9474;    [*] extmod                                           &#9474;           
          &#9474;    [*] freetype                                         &#9474;           
          &#9474;    [*] glx                                              &#9474;           
          &#9474;    [*] int10                                            &#9474;           
          &#9474;    [ ] record                                           &#9474;           
          &#9474;    [ ] v4l                                              &#9474;           
          &#9474;    [*] vbe                                              &#9474;           
          &#9474;                                                         &#9474;           
          &#9474;                                                         &#9474;           
          &#9474;                         <Ok>                            &#9474;           
          &#9474;                                                         &#9474;           
```

Choose bitmat and OK

                                                                               
```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; The Files section of the X server configuration file tells the X server   &#9474;  
 &#9474; where to find server modules, the RGB color database, and font files.     &#9474;  
 &#9474; This option is recommended to experienced users only.  In most cases, it  &#9474;  
 &#9474; should be enabled.                                                        &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Disable this option if you want to maintain a custom Files section into   &#9474;  
 &#9474; the X.Org server configuration file.  This may be needed to remove the    &#9474;  
 &#9474; reference to the local font server, add a reference to a different font   &#9474;  
 &#9474; server, or rearrange the default set of local font paths.                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Write default Files section to configuration file?                        &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>      
```

YES
```
           &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Many monitors (including LCD's) and video cards support a communication   &#9474;  
 &#9474; protocol that allows the monitor's technical characteristics to be        &#9474;  
 &#9474; communicated back to the computer.  If the monitor and video card         &#9474;  
 &#9474; support this protocol, further configuration questions about the monitor  &#9474;  
 &#9474; will be pre-answered.                                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If autodetection fails, you will be asked for information about the       &#9474;  
 &#9474; monitor.                                                                  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Attempt monitor autodetection?                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;                                                                           &#9474;  
```

YES

                                                                               
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; The X server configuration file associates the monitor with a name that   &#9474;  
 &#9474; you may provide.  This is usually the vendor or brand name followed by    &#9474;  
 &#9474; the model name, e.g., "Sony E200" or "Dell E770s".                        &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Identifier for the monitor:                                               &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; NEC LCD1550V_____________________________________________________________ &#9474;  
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>            
```    

OK

 ```
         &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
  &#9474; Please keep only the resolutions you would like the X server to use.     &#9474;  
  &#9474; Removing all of them is the same as removing none, since in both cases   &#9474;  
  &#9474; the X server will attempt to use the highest possible resolution.        &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Video modes to be used by the X server:                                  &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;    [ ] 1280x800                                                      &#8593;   &#9474;  
  &#9474;    [ ] 1280x768                                                      &#9618;   &#9474;  
  &#9474;    [ ] 1200x800                                                      &#9618;   &#9474;  
  &#9474;    [ ] 1152x864                                                      &#9618;   &#9474;  
  &#9474;    [ ] 1152x768                                                      &#9618;   &#9474;  
  &#9474;    [*] 1024x768                                                      &#9618;   &#9474;  
  &#9474;    [*] 800x600                                                       &#9646;   &#9474;  
  &#9474;    [*] 640x480                                                       &#8595;   &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                  <Ok>                                 
```         

Choose [*] 1024x768  and OK

---

### Post by lukanikos on 2007-07-07
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; For the X Window System graphical user interface to operate correctly,    &#9474;  
 &#9474; certain characteristics of the monitor must be known.                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; The "simple" option will prompt about the monitor's physical size; this   &#9474;  
 &#9474; will set some configuration values appropriate for a typical CRT of the   &#9474;  
 &#9474; corresponding size, but may be suboptimal for high-quality CRT's.         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; The "medium" option will present you with a list of resolutions and       &#9474;  
 &#9474; refresh rates, such as "800x600 @ 85Hz"; you should choose the best mode  &#9474;  
 &#9474; you wish to use (and that you know the monitor is capable of).            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; The "advanced" option will let you specify the monitor's horizontal sync  &#9474;  
 &#9474; and vertical refresh tolerances directly.                                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                   
```  

Choose OK

---

### Post by lukanikos on 2007-07-07
```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;             
             &#9474; Method for selecting the monitor characteristics:  &#9474;             
             &#9474;                                                    &#9474;             
             &#9474;                      Simple                        &#9474;             
             &#9474;                      Medium                        &#9474;             
             &#9474;                      Advanced                      &#9474;             
             &#9474;                                                    &#9474;             
             &#9474;                                                    &#9474;             
             &#9474;                       <Ok>                         &#9474;    
```      
OK   

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; Please enter either a comma-separated list of discrete values (for        &#9474;  
 &#9474; fixed-frequency displays), or a pair of values separated by a dash (all   &#9474;  
 &#9474; modern CRT's).  This information should be available in the monitor's     &#9474;  
 &#9474; manual.  Values lower than 30 or higher than 130 are extremely rare.      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Monitor's horizontal sync range:                                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; 31-60____________________________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>  
```

OK

```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; Please enter either a comma-separated list of discrete values (for        &#9474;  
 &#9474; fixed-frequency displays), or a pair of values separated by a dash (all   &#9474;  
 &#9474; modern CRT's).  This information should be available in the monitor's     &#9474;  
 &#9474; manual.  Values lower than 50 or higher than 160 are extremely rare.      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Monitor's vertical refresh range:                                         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; 55-75____________________________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>   
``` 

OK

```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   
  &#9474;                                                                         &#9474;   
  &#9474; The monitor synchronization ranges should be autodetected by the X      &#9474;   
  &#9474; server in most cases, but sometimes it needs hinting.  This option is   &#9474;   
  &#9474; for experienced users, and should be left at its default.               &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474; Write monitor sync ranges to the configuration file?                    &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                    <Yes>                       <No>   
```

YES

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; Usually 24-bit color is desirable, but on graphics cards with limited     &#9474;  
 &#9474; amounts of framebuffer memory, higher resolutions may be achieved at the  &#9474;  
 &#9474; expense of higher color depth.  Also, some cards support hardware 3D      &#9474;  
 &#9474; acceleration only for certain depths.  Consult your video card manual     &#9474;  
 &#9474; for more information.                                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; So-called "32-bit color" is actually 24 bits of color information plus 8  &#9474;  
 &#9474; bits of alpha channel or simple zero padding; the X Window System can     &#9474;  
 &#9474; handle both.  If you want either, select 24 bits.                         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Desired default color depth in bits:                                      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                   16     &#9646;                                &#9474;  
 &#9474;                                   24     &#8595;                                &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>  
```

Choose OK and 24

---

### Post by lukanikos on 2007-07-07
ABOVE all the configurations I did!!

---

### Post by lukanikos on 2007-07-07
```
i guess 1 good way to see if it's possible would be to download (and burn) an iso of PCLOS or Sabayon and see if it works ... that's what i did, i wasn't too big on the 3D desktop, effects - so there was no way i was going to go through the hassle of getting it working (having NO idea if it even would) on a distro that didn't do all the dirty work for me - Sabayon was the 1st to get it working (via fglrx) and PCLOS was the first that showed i could use AIGLX ... but in the end, i'm not finding any reason to use 3D desktop, effects ...
```
[COLOR="Red"]
download (and burn) an iso of PCLOS or Sabayon and see if it works[/COLOR]

What is PCLOS or Sabayon?and when you say if it works what do you mean?(If it works in what way?)

---

### Post by lukanikos on 2007-07-07
I think in the end I will have to buy an Nvidia graphic card

---

### Post by scxtt on 2007-07-07
ok, so you did all that - then what?  did you reboot?  did you type **startx** from the CLI? ... i see absolutely NO reason why your 9600 wouldn't work w/ the "ati" driver ... i'm almost considering putting my old 9200 in my box just too see :p

PCLOS and Sabayon are both KDE-centric distros of linux - ubuntu alternatives, if you will ... both have LiveCDs which will do all the grunt-work of configuring a 3D desktop ...

it also seems you don't have the radeon driver installed:
```
lukanikos@lukanikos:~$ aptitude search xserver-xorg-driver-radeon
v   xserver-xorg-driver-radeon
``` - there would be an "i" if it was instead of the "v" ...

---

### Post by stillwaters130 on 2007-07-07
No, you DON'T need to buy a new card, unless this card is actually defective...

>  Ati-Drivers >8.24.x and Radeon 9200 or Radeon 9600

If you are getting the following error

   [fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS

It seems the newest version of the ATI drivers break the libGL.so.1.2 library file Here's how to get a working copy of this library. (NOTE: [http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2) may not continue to exist)

   cd /usr/lib/opengl/ati/lib/
   mv libGL.so.1.2 libGL.so.1.2_broken
   wget [http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2)


You will now be able to use the GL programs again. See [http://www.linuxforums.org/forum/suse-linux-help/63678-ati-driver-going-crazy.html](http://www.linuxforums.org/forum/suse-linux-help/63678-ati-driver-going-crazy.html) and [http://ubuntuforums.org/showthread.php?t=185033](http://ubuntuforums.org/showthread.php?t=185033) 

I know that's Gentoo and not ubuntu, but others have gotten fglrx to work, so I think you can too.

I have to drive home from vacation today, but I'll be back later tonight to help :-)

---

### Post by lukanikos on 2007-07-07
> **scxtt said:**
> ok, so you did all that - then what?  did you reboot?  did you type **startx** from the CLI? ... i see absolutely NO reason why your 9600 wouldn't work w/ the "ati" driver ... i'm almost considering putting my old 9200 in my box just too see :p

PCLOS and Sabayon are both KDE-centric distros of linux - ubuntu alternatives, if you will ... both have LiveCDs which will do all the grunt-work of configuring a 3D desktop ...

it also seems you don't have the radeon driver installed:
```
lukanikos@lukanikos:~$ aptitude search xserver-xorg-driver-radeon
v   xserver-xorg-driver-radeon
``` - there would be an "i" if it was instead of the "v" ...

do you recon I should start the instalation from the begining?

---

### Post by lukanikos on 2007-07-07
OK!

I will take the Instructions from the beginjning and see If I do a mistake somewhere

```
I get into Applications-->Accessories-->Terminal and I write 

sudo sudo gedit /etc/X11/xorg.conf 

To Disable Composite extension by adding below lines in /etc/X11/xorg.conf.

Section "Extensions"
    Option  "Composite" "Disable" 
EndSection
```

Then I do all the commands as foolows:

```
lukanikos@lukanikos:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Get:2 http://gr.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://gr.archive.ubuntu.com feisty/main Translation-en_US
Ign http://gr.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://gr.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://gr.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://gr.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://gr.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://gr.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://gr.archive.ubuntu.com feisty Release
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://gr.archive.ubuntu.com feisty-updates Release             
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://gr.archive.ubuntu.com feisty/main Packages
Hit http://gr.archive.ubuntu.com feisty/restricted Packages
Hit http://gr.archive.ubuntu.com feisty/main Sources
Hit http://gr.archive.ubuntu.com feisty/restricted Sources
Hit http://gr.archive.ubuntu.com feisty/universe Packages
Hit http://gr.archive.ubuntu.com feisty/universe Sources
Hit http://gr.archive.ubuntu.com feisty/multiverse Packages
Hit http://gr.archive.ubuntu.com feisty/multiverse Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://gr.archive.ubuntu.com feisty-updates/main Packages
Hit http://gr.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://gr.archive.ubuntu.com feisty-updates/main Sources
Hit http://gr.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 3B in 0s (5B/s)  
Reading package lists... Done
lukanikos@lukanikos:~$ sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
module-assistant is already the newest version.
build-essential is already the newest version.
fakeroot is already the newest version.
dh-make is already the newest version.
debhelper is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lukanikos@lukanikos:~$ sudo apt-get install linux-headers-$(uname -r) wget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
wget is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lukanikos@lukanikos:~$ mkdir -p ~/fglrx
lukanikos@lukanikos:~$ cd ~/fglrx
lukanikos@lukanikos:~/fglrx$ wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.35.5-x86.x86_64.run
--16:27:34--  https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.35.5-x86.x86_64.run
           => `ati-driver-installer-8.35.5-x86.x86_64.run.2'
Resolving a248.e.akamai.net... 212.205.43.8, 212.205.43.6
Connecting to a248.e.akamai.net|212.205.43.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 57,314,907 (55M) [application/octet-stream]

100%[====================================>] 57,314,907   793.50K/s    ETA 00:00

16:28:43 (815.80 KB/s) - `ati-driver-installer-8.35.5-x86.x86_64.run.2' saved [57314907/57314907]

lukanikos@lukanikos:~/fglrx$
```

Then I continue with removing but one is not reoved cos does not exist.

```
lukanikos@lukanikos:~/fglrx$ rm xorg-driver-fglrx*.deb
lukanikos@lukanikos:~/fglrx$ rm fglrx-kernel-source*.deb
lukanikos@lukanikos:~/fglrx$ rm fglrx-control*.deb
rm: cannot remove `fglrx-control*.deb': No such file or directory
lukanikos@lukanikos:~/fglrx$ 
```

Creating a *.deb packages

```
lukanikos@lukanikos:~/fglrx$ sh ./ati-driver-installer-8.35.5-x86.x86_64.run --buildpkg Ubuntu/feisty
Created directory fglrx-install.We6773
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.35.5.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/feisty
Package /home/lukanikos/fglrx/xorg-driver-fglrx_8.35.5-1_i386.deb has been successfully generated
Package /home/lukanikos/fglrx/xorg-driver-fglrx-dev_8.35.5-1_i386.deb has been successfully generated
Package /home/lukanikos/fglrx/fglrx-kernel-source_8.35.5-1_i386.deb has been successfully generated
Package /home/lukanikos/fglrx/fglrx-amdcccle_8.35.5-1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.We6773
lukanikos@lukanikos:~/fglrx$ 
```

install the packages

```
lukanikos@lukanikos:~/fglrx$ sudo dpkg -i xorg-driver-fglrx*.deb
(Reading database ... 107611 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.35.5-1 (using xorg-driver-fglrx_8.35.5-1_i386.deb) ...
Stopping atieventsd: done.
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace xorg-driver-fglrx-dev 8.35.5-1 (using xorg-driver-fglrx-dev_8.35.5-1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up xorg-driver-fglrx (8.35.5-1) ...
Starting atieventsd: done.

Setting up xorg-driver-fglrx-dev (8.35.5-1) ...
lukanikos@lukanikos:~/fglrx$ sudo dpkg -i fglrx-kernel-source*.deb
(Reading database ... 107611 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.35.5-1 (using fglrx-kernel-source_8.35.5-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.35.5-1) ...
lukanikos@lukanikos:~/fglrx$ sudo dpkg -i fglrx-amdcccle*.deb
(Reading database ... 107611 files and directories currently installed.)
Preparing to replace fglrx-amdcccle 8.35.5-1 (using fglrx-amdcccle_8.35.5-1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Setting up fglrx-amdcccle (8.35.5-1) ...

lukanikos@lukanikos:~/fglrx$ 


```

Remove exisiting fglrx driver in /usr/src and Patch the display driver.
```

lukanikos@lukanikos:~/fglrx$ sudo rm /usr/src/fglrx-kernel*.deb
lukanikos@lukanikos:~/fglrx$ cd ~/fglrx
lukanikos@lukanikos:~/fglrx$ wget http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.35.5-for-2.6.20.patch
--16:45:25--  http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.35.5-for-2.6.20.patch
           => `fglrx-8.35.5-for-2.6.20.patch.2'
Resolving whoopie.gmxhome.de... 82.165.62.107
Connecting to whoopie.gmxhome.de|82.165.62.107|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,087 (5.0K) [text/plain]

100%[====================================>] 5,087         --.--K/s             

16:45:25 (54.51 KB/s) - `fglrx-8.35.5-for-2.6.20.patch.2' saved [5087/5087]

lukanikos@lukanikos:~/fglrx$ cd /usr/src
lukanikos@lukanikos:/usr/src$ sudo cp fglrx.tar.bz2 fglrx.tar.bz2-original
lukanikos@lukanikos:/usr/src$ sudo tar xvjf fglrx.tar.bz2
modules/
modules/fglrx/
modules/fglrx/firegl_public.c
modules/fglrx/drm_compat.h
modules/fglrx/agp_backend.h
modules/fglrx/drmP.h
modules/fglrx/libfglrx_ip.a.GCC4
modules/fglrx/drm_os_linux.h
modules/fglrx/agpgart.h
modules/fglrx/agp.h
modules/fglrx/Makefile
modules/fglrx/drm.h
modules/fglrx/i7505-agp.c
modules/fglrx/debian/
modules/fglrx/debian/postinst
modules/fglrx/debian/rules
modules/fglrx/debian/dirs.template
modules/fglrx/debian/changelog
modules/fglrx/debian/control.template
modules/fglrx/debian/copyright
modules/fglrx/debian/compat
modules/fglrx/make.sh
modules/fglrx/drm_proc.h
modules/fglrx/agpgart_be.c
modules/fglrx/libfglrx_ip.a.GCC3
modules/fglrx/nvidia-agp.c
modules/fglrx/libfglrx_ip.a.GCC2
modules/fglrx/agp3.c
modules/fglrx/firegl_public.h
lukanikos@lukanikos:/usr/src$ cd /usr/src/modules/fglrx
lukanikos@lukanikos:/usr/src/modules/fglrx$ sudo patch -p0 < ~/fglrx/fglrx-8.35.5-for-2.6.20.patch
patching file firegl_public.c
Hunk #3 succeeded at 4415 (offset 9 lines).
Hunk #4 succeeded at 5041 (offset 9 lines).
Hunk #5 succeeded at 5231 (offset 9 lines).
lukanikos@lukanikos:/usr/src/modules/fglrx$ cd /usr/src
lukanikos@lukanikos:/usr/src$ sudo tar cvjf fglrx.tar.bz2 modules/fglrx
modules/fglrx/
modules/fglrx/firegl_public.c
modules/fglrx/drm_compat.h
modules/fglrx/agp_backend.h
modules/fglrx/Module.symvers
modules/fglrx/drmP.h
modules/fglrx/libfglrx_ip.a.GCC4
modules/fglrx/drm_os_linux.h
modules/fglrx/agpgart.h
modules/fglrx/agp.h
modules/fglrx/Makefile
modules/fglrx/drm.h
modules/fglrx/i7505-agp.c
modules/fglrx/debian/
modules/fglrx/debian/postinst
modules/fglrx/debian/rules
modules/fglrx/debian/dirs.template
modules/fglrx/debian/changelog
modules/fglrx/debian/fglrx-kernel-2.6.20-16-generic.postinst
modules/fglrx/debian/control.template
modules/fglrx/debian/copyright
modules/fglrx/debian/compat
modules/fglrx/make.sh
modules/fglrx/firegl_public.c.orig
modules/fglrx/drm_proc.h
modules/fglrx/agpgart_be.c
modules/fglrx/libfglrx_ip.a.GCC3
modules/fglrx/nvidia-agp.c
modules/fglrx/libfglrx_ip.a.GCC2
modules/fglrx/agp3.c
modules/fglrx/firegl_public.h
lukanikos@lukanikos:/usr/src$ 
```

Compile and install fglrx module

```

lukanikos@lukanikos:/usr/src$ sudo module-assistant prepare
Getting source for kernel version: 2.6.20-16-generic
Kernel headers available in /lib/modules/2.6.20-16-generic/build
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
lukanikos@lukanikos:/usr/src$ sudo module-assistant update

Updated infos about 86 packages
lukanikos@lukanikos:/usr/src$ sudo module-assistant build fglrx
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Done with /usr/src/fglrx-kernel-2.6.20-16-generic_8.35.5-1+2.6.20-16.29_i386.deb .
lukanikos@lukanikos:/usr/src$ sudo module-assistant install fglrx
Version 8.35.5-1+2.6.20-16.29 of fglrx-kernel-2.6.20-16-generic already installed, skipping.
lukanikos@lukanikos:/usr/src$ 
```

---

### Post by lukanikos on 2007-07-07
I Disable fglrx bundled with linux-restricted-module by adding fglrx to /etc/default/linux-restricted-modules-common

```
After I I get into Applications-->Accessories-->Terminal and I write 

sudo sudo gedit /etc/X11/xorg.conf

and I write this command in the file

DISABLED_MODULES="fglrx"
```

---

### Post by lukanikos on 2007-07-07
and Regenerate module dependencies.

```
lukanikos@lukanikos:/usr/src$ sudo depmod -a
lukanikos@lukanikos:/usr/src$ 
```


and here comes the quastion

the next step says that I can use this settings but this settings have a very high resolution and my monitor is a 15 inch one.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection
Section "Files"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
Section "Module"
    Load  "bitmap"
    Load  "dbe"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "type1"
    Load  "vbe"
EndSection
Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option      "CoreKeyboard"
    Option      "XkbRules" "xorg"
    Option      "XkbModel" "pc104"
    Option      "XkbLayout" "us"
EndSection
Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "CorePointer"
    Option      "Device" "/dev/input/mice"
    Option      "Protocol" "ExplorerPS/2"
    Option      "ZAxisMapping" "4 5"
    Option      "Emulate3Buttons" "true"
EndSection
Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents" "true"
    Option      "Device" "/dev/psaux"
    Option      "Protocol" "auto-dev"
    Option      "HorizScrollDelta" "0"
EndSection
Section "InputDevice"
    Identifier  "stylus"
    Driver      "wacom"
    Option      "Device" "/dev/wacom"       # Change to 
    Option      "Type" "stylus"
    Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection
Section "InputDevice"
    Identifier  "eraser"
    Driver      "wacom"
    Option      "Device" "/dev/wacom"       # Change to 
    Option      "Type" "eraser"
    Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection
Section "InputDevice"
    Identifier  "cursor"
    Driver      "wacom"
    Option      "Device" "/dev/wacom"       # Change to 
    Option      "Type" "cursor"
    Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection
Section "Monitor"
    Identifier   "Builtin LCD"
    HorizSync    28.0 - 70.0
    VertRefresh  43.0 - 60.0
    Option      "DPMS"
EndSection
Section "Device"
    Identifier  "ATI Technologies Inc M22 [Radeon Mobility M300]"
    Driver      "fglrx"
    Option      "VideoOverlay" "on"
    Option      "OpenGLOverlay" "off"
    BusID       "PCI:1:0:0"
EndSection
Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies Inc M22 [Radeon Mobility M300]"
    Monitor    "Builtin LCD"
    DefaultDepth     24
    SubSection "Display"
            Depth     1
            Modes    "1400x1050"
    EndSubSection
    SubSection "Display"
            Depth     4
            Modes    "1400x1050"
    EndSubSection
    SubSection "Display"
            Depth     8
            Modes    "1400x1050"
    EndSubSection
    SubSection "Display"
            Depth     15
            Modes    "1400x1050"
    EndSubSection
    SubSection "Display"
            Depth     16
            Modes    "1400x1050"
    EndSubSection
    SubSection "Display"
            Depth     24
            Modes    "1400x1050"
    EndSubSection
EndSection
Section "DRI"
    Mode         0666
EndSection
Section "Extensions"
    Option      "Composite" "Disable"
EndSection
```

should I use this settings?

or should I leave it as it is?

the guy who wrote the walk through says "Modify /etc/X11/xorg.conf to use fglrx instead. You may safely use my configuration as follows."

What should I do to go to the next step?

Should I change or keep the once I alredy have??
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC LCD1550V"
	Option		"DPMS"
	HorizSync	31-60
	VertRefresh	55-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"NEC LCD1550V"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
       Option  "Composite" "Disable"
EndSection
```

Also please ha a look if all the steps have gone right??

Thanks

---

### Post by lukanikos on 2007-07-07
Also the walk through says

Optionally, add fglrx to /etc/modules. Note that you should not need to do it but give it a try if fglrx is not loaded automatically.

Which I did change it into

```
lp
psmouse
sbp2
sr_mod
rtc
fuse
fglrx
```

If not which is the right way to keep it?

---

### Post by lukanikos on 2007-07-07
OK 
Please can you tell where to find and how to install?

---

### Post by scxtt on 2007-07-07
you're switching gears again - now you're back to using fglrx instead of the ati/radeon driver ... it's your choice and all, but this thread is getting out of control ... what i was talking about was SIMPLY installing the ati/radeon driver from the repos - but you went off and did the whole fglrx thing again - it's going to get to the point where you've done X, Y, and Z so many times - no one can sort it out ...

my advice was to *start simple* - get the open source drivers working, then if you need it, use fglrx ...

it was as simple as: **sudo aptitude install xserver-xorg-driver-radeon**, then changing "Driver" to "radeon" ...

or **sudo aptitude install xserver-xorg-video-ati** and changing it to "ati" (this driver may already be installed) ...

i also see this (potential) error in your xorg.conf:
```
Section "Monitor"
	Identifier	"NEC LCD1550V"
	Option		"DPMS"
	HorizSync31-60
	VertRefresh	55-75
EndSection
```there's no SPACE b/t "HorizSync" and "31-60" ... but these types of errors should be in your Xorg.log and you should be told about them ...

---

### Post by lukanikos on 2007-07-07
Thanks for your help!!

on my xorg file it is typed as you see 

```
Section "Monitor"
	Identifier	"NEC LCD1550V"
	Option		"DPMS"
	HorizSync	31-60
	VertRefresh	55-75
```

As you can see in my post and not

```
Section "Monitor"
	Identifier	"NEC LCD1550V"
	Option		"DPMS"
	HorizSync31-60
	VertRefresh	55-75
EndSection
```

the corect is to have space or not because on my file there is no space.

---

### Post by scxtt on 2007-07-07
you want there to be a space, otherwise it's "all one word" ...
```
Section "Monitor"
	Identifier	"NEC LCD1550V"
	Option		"DPMS"
	HorizSync		31-60
	VertRefresh	55-75
EndSection
```looks like the "code" tags on this board are a little iffy w/ tabs sometimes ...

---

### Post by lukanikos on 2007-07-08
Ok my dear friend scxtt's !!!;)

I am thinking of re-installing the Ubuntu software from the beginning and would be very glad if you can tell me the step by step installation of the way you think right..!!\\:D/
I have tryed so many ways and now I am beginning to get confused.](*,)
I will follow the way you think is right and get in the end the ATI driver working.[-o<

Best regards and thanks for your intensive help.....:grin:
Great person..!!!!!!!=D>

---

### Post by scxtt on 2007-07-08
you're very welcome - i fought for quite a long time w/ my ATI card back when i decided to switch to Linux only (save a windows VM) - i was just happy back then to get 1600x1200 :p ... i think it was Dapper where i FINALLY got fglrx working (following someone's direction i found somewhere) ... let's make sure we're on the same page w/ what you're trying to accomplish:

1. get fglrx working, period
- or -
2. get a 3D desktop (using AIGLX) working (w/ radeon/ati driver)

once we get that sorted out, and you're willing to do a re-install - we should be square ...

i will say that i've never installed beryl myself in ubuntu - but i think it's as simple as installing all the beryl packages ...

---

### Post by lukanikos on 2007-07-08
I want to get a 3D desktop (using AIGLX) working (w/ radeon/ati driver)

I tried beryl before and didn't work so I dont know if it will work now.

Also I want to know what exactly is fglrx?

If I use fglrx can I not have  3D desktop?

What is the difference?

---

### Post by scxtt on 2007-07-08
i know even less about compiz / compiz-fusion, if that's what you're looking for ;)

---

### Post by lukanikos on 2007-07-08
let's follow your way then!!

Tell me the steps..

---

### Post by scxtt on 2007-07-08
> **lukanikos said:**
> I want to get a 3D desktop (using AIGLX) working (w/ radeon/ati driver)

I tried beryl before and didn't work so I dont know if it will work now.

Also I want to know what exactly is fglrx?

If I use fglrx can I not have  3D desktop?

What is the difference?fglrx is the CLOSED SOURCE driver provided by ATI/AMD ... it does NOT support AIGLX (which is "better" than XGL, which fglrx does support) ...

radeon/ati are open source, "reverse engineered" drivers that are widely available ...

you can have a 3d desktop w/ fglrx, but i think you'd prefer AIGLX ...

---

### Post by lukanikos on 2007-07-08
Ok scxtt...

My 3d effects are on your hands now....

Tell me what to do and I follow.

---

### Post by lukanikos on 2007-07-08
scxtt where did you disappear ?

---

### Post by lukanikos on 2007-07-08
working !!!

Great!!

I hade to change the logging option...

---

### Post by scxtt on 2007-07-08
everything is working?

---

### Post by lukanikos on 2007-07-09
All working,,,,

Thanks!!

---

