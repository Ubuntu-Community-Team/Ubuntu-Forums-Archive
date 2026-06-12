---
title: "Changing brightness does not work in Ubuntu 11.10 after upgrading."
date: 2011-11-04
forum: Desktop Environments
---

### Post by khosro on 2011-11-04
Hello,
I 
After upgrading to Ubuntu 11.10 in my Sony Vaio Laptop(VGN-CS) and using Unity as a desktop environment,increasing and decreasing  brightness via fn+f5 and fn+f6 does not worked any more.
I remember that i did not installed any NVIDIA driver in my laptop,
but it seems that Ubunut itself installed it in new version after upgrading to 11.10.
I also test [http://ubuntuguide.net/change-screen-brightness-with-fn-key-in-ubuntu-11-0410-10]("http://ubuntuguide.net/change-screen-brightness-with-fn-key-in-ubuntu-11-0410-10"),but it does not work.
I can not worked with my laptop any more because brightness of my 
screen is too high now.

Khosro.

---

### Post by typhoon_tip on 2011-11-04
If you open "Additional Drivers", does it say that the NVIDIA driver is currently activated ?

---

### Post by khosro on 2011-11-04
Yes ,it is.
I have attached a related screenshot picture.

Khosro.

---

### Post by matt_symes on 2011-11-04
Hi

What is the make and model of your latop and graphics card ?

Open a terminal and type

```
ls /sys/class/backlight
```

Copy and paste the results back here.

Then type

```
lsmod | grep video
```

and do the same thing.

Lastly

```
cat /proc/cmdline
```

Post back as well.

Kind regards

---

### Post by khosro on 2011-11-04
Hi matt_symes,
My laptop is Sony Vaio VGN-CS and graphic cards is NVIDIA.

The following is the commands and also output that you asked me to run :
 
```

khosro@khosro-laptop:~$ ls /sys/class/backlight
sony

khosro@khosro-laptop:~$ lsmod | grep video
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
video                  19412  0 

khosro@khosro-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=0095c4f7-3bae-490d-be19-3f907855199c ro quiet splash vt.handoff=7

```

Khosro.

---

### Post by matt_symes on 2011-11-04
Hi

Open a terminal and type

```
sudo nano /etc/default/grub
```Enter your password. It will not be echoed to the screen.

Look for the line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it so it says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=*vendor***"
```Press ctrl + o to save and ctrl + x to exit.

Then type

```
sudo update-grub
```Reboot your PC and check your function keys. Post back if it doesn't work.

Edit: Just in case you missed it i have highlighted what you need to enter.

Kind regards

---

### Post by khosro on 2011-11-04
matt_symes,
I changed what you said,but unfortunately it does not work.:-(
The following is my grub

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=vendor"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by matt_symes on 2011-11-04
Hi

Try

```
acpi_backlight=vendor
```

and not
[FONT=monospace]
[/FONT]```
acpi_osi=vendor
```

and then update grub again.

Kind regards

---

### Post by khosro on 2011-11-04
Still does not work.](*,)#-o
my grub :

[HTML]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=vendor"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
[/HTML]

---

### Post by matt_symes on 2011-11-04
Hi

Lets check something out.
[FONT=monospace]
Open a terminal and type

[/FONT]```
ls /sys/class/backlight/sony
```

If you see a file in there called brightness then type

```
echo 5 | sudo tee /sys/class/backlight/sony/brightness
```

Enter your password. It will not be echoed to the screen.

If this lower the brightness the substituting 9 in the command above should set it back.

If there is no brightness file then post the output of

```
ls /sys/class/backlight/sony
```

Post back results.

Kind regards

---

### Post by khosro on 2011-11-04
```

khosro@khosro-laptop:~$ ls /sys/class/backlight/sony
actual_brightness  brightness      power      type
bl_power           max_brightness  subsystem  uevent
khosro@khosro-laptop:~$ echo 5 | sudo tee /sys/class/backlight/sony/brightness
[sudo] password for khosro: 
5
khosro@khosro-laptop:~$ 
khosro@khosro-laptop:~$ 
echo 9 | sudo tee /sys/class/backlight/sony/brightness
9
tee: /sys/class/backlight/sony/brightness: Invalid argument
khosro@khosro-laptop:~$ 

```

I do not really know where the problem is?It seems every configuration is OK,but i can not increase or decrease brightness.
I am really confusing.

---

### Post by matt_symes on 2011-11-04
Hi

I have to say i am not sure what the problem is either in this case. If writing to sysfs blacklight brightness is not working then it may be a bigger problem.

Let's see if anybody else has any other ideas.

An upgrade as opposed to a fresh install can be problematic.

Kind regards

---

### Post by khosro on 2011-11-05
Thanks matt_symes for your help.
I remember i had the same issue after upgrading from 10.10 to 11.04,but one of benefit of 11.04 was that we could use Ubuntu classic rather than Unity.I remember that in Ubuntu classic i uninstalled NVIDIA accelerated graphic drivers and then brightness worked and i could increase and decrease brightness via fn+(f5/f6).But it seems Ubuntu Unity needs NVIDIA accelerated graphic drivers to run properly,so that i can not do the same in Ubuntu 11.10.
So that due to this issue and some other issues(such as suspending Ubuntu does not work any more) that i discovered using Ubuntu Unity after upgrading to Ubuntu 11.10 , maybe in future i can not use Ubuntu for my development environment and all of my work,and i really disappointed now,i am not sure but maybe i must again  migrate to Windows :cry:#-o

Khosro.

---

### Post by khosro on 2011-11-09
Hello,
I am sure the brightness problem  is related to NVIDIA graphic driver that Ubuntu installed it after upgrading.Because after uninstalling NVIDIA graphic driver and install GNOME Desktop environment(Ubuntu classic) ,and log in in Ubuntu classic ,increasing and decreasing brightness works.
I do not know why brightness problem related to NVIDIA graphic driver?
I would be appreciate if any one can help me.

Khosro.

---

### Post by matt_symes on 2011-11-09
Hi

> **khosro said:**
> Hello,
I am sure the brightness problem  is related to NVIDIA graphic driver that Ubuntu installed it after upgrading.Because after uninstalling NVIDIA graphic driver and install GNOME Desktop environment(Ubuntu classic) ,and log in in Ubuntu classic ,increasing and decreasing brightness works.
I do not know why brightness problem related to NVIDIA graphic driver?
I would be appreciate if any one can help me.

Khosro.

This is interesting and may be due to an incompatibility between the nvidia driver and the sony video ACPI platform driver.

This is only a suggestion and may not work but it's worth a try.

Reinstall the nvidia driver.

Open a terminal and type

```
sudo nano /etc/default/grub
```Look for the lines that say
[FONT=monospace]
[/FONT]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```and change to 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=video"
```Run ```
sudo update-grub
``` and reboot your PC.

What we are trying to do here is use the standard ACPI video.ko driver and not sonys platform driver.

I don't know if this will work but it's worth the 5 minutes to give it a go.

Kind regards

---

### Post by khosro on 2011-11-09
Hello matt_symes,
I test it,but it does not work.

Khosro.

---

### Post by daniel.t.miles on 2011-11-17
After searching in other places, I found a solution that solved this problem for me. In your /etc/X11/xorg.conf file, find the "Default Device" section and add the EnableBrightnessControl line. After I restarted X (sudo service lightdm restart ... apparently ubuntu 11.10 doesn't use GDM anymore), my FN-key brightness controls worked just fine.

Section “Device”
Identifier	“Default Device”
Option	 “NoLogo”	 “True”
**Option “RegistryDwords”	“EnableBrightnessControl=1&#8243;**
EndSection

---

### Post by khosro on 2011-11-17
Hello Daniel ,
I have upgraded from Ubuntu 11.04 to 11.10.And as i said in one of my last post,i had the same problem in 11.04,and i solved it by uninstalling NVIDIA driver.
Any way,after upgrading to 11.10,there is not any file named xorg.conf in /etc/X11 folder,only files with following name exist:

"xorg.conf.backup" "cursors","xorg.conf.dist-upgrade-201111041549","default-display-manager" ,"xorg.conf.failsafe".

And also ,i remember that i have test your solution in Ubuntu 11.04,but it did not work,and still there is a line that i have inserted in xorg.conf(In Ubuntu 11.04) ,and it seems xorg.conf file in Ubuntu 11.04 renamed to xorg.conf.backup during upgrade to 11.10.
And the following lines reside in xorg.conf.backup :
```


Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
#	Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection


```

Khosro.

---

### Post by khosro on 2011-12-02
Hi,
I think the following links are related to my problem.
I am not sure whether this comment is true [http://www.techrepublic.com/forum/discussions/102-351775-3527078]("http://www.techrepublic.com/forum/discussions/102-351775-3527078").This comment is in this article [http://www.techrepublic.com/blog/opensource/linux-mint-12-a-much-needed-much-improved-linux-desktop/3226]("http://www.techrepublic.com/blog/opensource/linux-mint-12-a-much-needed-much-improved-linux-desktop/3226").

Khosro.

---

### Post by fernandodabadia on 2012-01-28
> **khosro said:**
> Hello Daniel ,
I have upgraded from Ubuntu 11.04 to 11.10.And as i said in one of my last post,i had the same problem in 11.04,and i solved it by uninstalling NVIDIA driver.
Any way,after upgrading to 11.10,there is not any file named xorg.conf in /etc/X11 folder,only files with following name exist:

"xorg.conf.backup" "cursors","xorg.conf.dist-upgrade-201111041549","default-display-manager" ,"xorg.conf.failsafe".

And also ,i remember that i have test your solution in Ubuntu 11.04,but it did not work,and still there is a line that i have inserted in xorg.conf(In Ubuntu 11.04) ,and it seems xorg.conf file in Ubuntu 11.04 renamed to xorg.conf.backup during upgrade to 11.10.
And the following lines reside in xorg.conf.backup :
```


Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
#	Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection


```

Khosro.

Hi Khosro.

Thank you so much. It worked so fine. I just changed de section. In my case I added the Option  "RegistryDwords" "EnableBrightnessControl=1" in section "Screen".

---

### Post by markbl on 2012-01-28
I have had a Dell laptop updated with each Ubuntu version for years as a clean install. Brightness control has always worked (with some slight issues) except for Ubuntu 11.10 so I suspected something was broken in Ubuntu although I could not find an exactly similar problem around the forums. I eventually thought to update the bios version in my laptop and then brightness control worked fine. So something did change in Ubuntu 11.10 (or 11.04 which I skipped), but an updated bios may fix some peoples brightness control issues?

---

### Post by WaNaBePi on 2012-02-24
So I have a *problem* I have the "xorg.conf" file in *addition to* the "xorg.conf.backup" file and others.

I have attached a screen shot.

I was thinking of deleting the others as they are updates and only keeping "xorg.conf.backup" as that seems to be the one I'm *supposed* to have and editing that.

Should I uninstall nvidia as well? My fn keys do work in so far as they show the brightness meter go up and down, but the brightness it self doesn't change.

Advice?

[http://ubuntuforums.org/showthread.php?t=1680872](http://ubuntuforums.org/showthread.php?t=1680872)

The advice in the above link worked for me, a little long but it worked, follow it verrrry carfully.

---

### Post by hypermax on 2012-03-12
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo nano /etc/default/grub
```Enter your password. It will not be echoed to the screen.

Look for the line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it so it says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=*vendor***"
```Press ctrl + o to save and ctrl + x to exit.

Then type

```
sudo update-grub
```Reboot your PC and check your function keys. Post back if it doesn't work.

Edit: Just in case you missed it i have highlighted what you need to enter.

Kind regards

This fixed the problem for me on a Dell XPS L401x.

Thank you!!

---

### Post by fallenstar on 2012-03-13
Hi, I have the same problem, have tried all the solutions, nothing working. I can't handle this brightness, my eyes hurt, is there anything else I can try?

Sony Vaio E series, 11.10 unity.

---

### Post by tippf2011 on 2012-03-14
If you open "Additional Drivers", does it say that the NVIDIA driver is currently activated ? [COLOR=White][goldfish]("http://www.aquariumfishhome.com")[/COLOR]

---

### Post by fallenstar on 2012-03-14
> **tippf2011 said:**
> If you open "Additional Drivers", does it say that the NVIDIA driver is currently activated ? [COLOR=White][goldfish]("http://www.aquariumfishhome.com")[/COLOR]

Yes, the NVIDIA accelerated graphics driver (version current) [recommended] 

is activated and currently in use. Should I try the other

NVIDIA accelerated graphics driver (post-release updates) (version current-updates)

????

Will my laptop spontaneously combust, or never come back to life?

):P

---

### Post by fallenstar on 2012-03-14
Changed the driver to the post release nvidia, no difference. Installed xbacklight, ran it from terminal, nada. Before the above work arounds I at least had a little gui that displayed the level of backlight, despite not affecting it. Reversed the workarounds, can't get it back.

---

### Post by fallenstar on 2012-03-14
this is a bug fix but it only works on certain NVIDIA cards:

[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444)

---

### Post by khosro on 2012-05-07
Really bad,i am really disappointed using Ubuntu,because after upgrading to 12.04 increasing and decreasing brightness does not work any more.In 11.04 it worked if i uninstall NVIDIA driver but in 12.04 it does not work anymore at all.
:confused:](*,)
Khosro.

---

### Post by jppinto on 2012-05-11
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo nano /etc/default/grub
```Enter your password. It will not be echoed to the screen.

Look for the line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it so it says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=*vendor***"
```Press ctrl + o to save and ctrl + x to exit.

Then type

```
sudo update-grub
```Reboot your PC and check your function keys. Post back if it doesn't work.

Edit: Just in case you missed it i have highlighted what you need to enter.

Kind regards

This solved my problem. I hava a Toshiba portege R830 with ubuntu 11.04 and after an update the brightness stopped working.

Thanks matt for the solution, and the original thread creator fos posting the question.

---

### Post by mohammadamingh on 2012-05-13
hello every one


i have this problem too 

please help me

i enter "sudo gedit /etc/default/grub" in terminal and my result is:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```i insert this " sudo gedit /etc/X11/xorg.conf " and result is:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@allspice)  Fri Feb 25 14:42:07 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony Nvidia Default Flat Panel"
    HorizSync       29.0 - 56.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```i do any thing but my problme exist yet


tip:
    my laptop is vaio cw26fg

---

### Post by matt_symes on 2012-05-14
Hi

@mohammad


Open a terminal and type


```
ls -l /sys/class/backlight
```
Please post the output back here.


Kind regards

---

### Post by mohammadamingh on 2012-05-14
hi

thank alot dear matt

i inserted and result is:
```
total 0
``` 




best regard

---

### Post by matt_symes on 2012-05-14
Hi

Your computer is not a model that i have ever owned, however you do not seem to have a device node for changing the brightness. That is the usual way to change the backlight brightness on models i have come across.


Can you post the output of these two commands.


```
lsmod | grep ^video
```


```
modprobe -l | grep video.ko
```


That is a small L after modprobe.


I am not sure if your laptop requires its own ACPI module or not.


Kind regards

---

### Post by mohammadamingh on 2012-05-15
hi 

Result of  "lsmod | grep ^video" is:

```

videodev               82052  1 uvcvideo
video                  19438  0 

```

and output of "modprobe -l | grep video.ko" is:

```

kernel/drivers/acpi/video.ko
kernel/drivers/media/rc/keymaps/rc-flyvideo.ko
kernel/drivers/media/video/uvc/uvcvideo.ko
kernel/drivers/staging/usbvideo/usbvideo.ko

```


thank matt for your attention

---

### Post by matt_symes on 2012-05-15
Hi

@mohammadamingh

A couple of questions.

Have you had the back light working on this laptop model under Linux/Ubuntu before ?

If so, what Ubuntu version ?

Is this a fresh install or an upgrade for Ubuntu ? If an upgrade, was it working in the previous version ?

EDIT: For future reference

[http://www.mjmwired.net/kernel/Documentation/laptops/sony-laptop.txt](http://www.mjmwired.net/kernel/Documentation/laptops/sony-laptop.txt)

Kind regards

---

### Post by mohammadamingh on 2012-05-16
hi matt

it very strange
I use the brightness key  and it works correctly  but i don't know how! 


tkanks  for your helps
thanks a lot

best regards

---

### Post by EulerianWalker on 2012-05-17
I don't know what's going on with my Dell XPS L702x.

Three days ago, I found a forum that told me about the "acpi_backlight=vendor" fix.
I did it, and it worked.
[FONT=monospace]
Then I reinstalled Ubuntu 12.04 (after destroying the kernel while messing around). So I went back to do the same thing, but now this brightness fix doesn't work for me.
[/FONT]

---

### Post by EulerianWalker on 2012-05-17
And not 5 minutes after the above post, I found a solution.

For the Dell XPS L702x running 12.04, do what this guy says:

[http://mikesubuntu.com/2010/05/how-i-finally-got-my-brightness-keys-working](http://mikesubuntu.com/2010/05/how-i-finally-got-my-brightness-keys-working)

It worked for me after rebooting.

---

### Post by oyster2no8head on 2012-09-11
> **matt_symes said:**
> 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=*vendor***"
```

Thanks matt_symes, this worked on my ***Packard Bell Easy-note-TJ68*** first time, i did it in 12.04.

---

### Post by mansam153 on 2012-09-29
Hi
i have installed ubuntu 12.04 on my new lenovo g580 laptopt.this does not have any graphics card except intel hd 3000.i have tried the above solutions of adding the line  acpi_backlight=vendor to the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line, in /etc/default/grub 

it does not work for me...

kindly help.

Thanks

---

### Post by Jitarth on 2012-12-22
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo nano /etc/default/grub
```Enter your password. It will not be echoed to the screen.

Look for the line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it so it says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=*vendor***"
```Press ctrl + o to save and ctrl + x to exit.

Then type

```
sudo update-grub
```Reboot your PC and check your function keys. Post back if it doesn't work.

Edit: Just in case you missed it i have highlighted what you need to enter.

Kind regards

Helped me fix it. Thanks buddy :D

---

### Post by dzincha on 2013-02-19
Hi.
Just installed 3d laptop with ubuntu 12.04. 1st was without problem. 2nd has problem with wifi. 3rd had problems with wifi and still has problem with dimming. On display it shows brightness bar, but don't change intensity of backlight. 
Here is the output from terminal:

ance@ance-EasyNote-TE11HC:~$ ls /sys/class/backlight
acpi_video0  intel_backlight
ance@ance-EasyNote-TE11HC:~$ lsmod | grep video
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
video                  19068  1 i915
ance@ance-EasyNote-TE11HC:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic-pae root=UUID=7339d58a-236e-49d4-8b88-bc73d443ab8b ro quiet splash vt.handoff=7


Also tried to change grub. Didn't helped.

---

### Post by dzincha on 2013-02-19
> **dzincha said:**
> Hi.
Just installed 3d laptop with ubuntu 12.04. 1st was without problem. 2nd has problem with wifi. 3rd had problems with wifi and still has problem with dimming. On display it shows brightness bar, but don't change intensity of backlight. 
Here is the output from terminal:

ance@ance-EasyNote-TE11HC:~$ ls /sys/class/backlight
acpi_video0  intel_backlight
ance@ance-EasyNote-TE11HC:~$ lsmod | grep video
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
video                  19068  1 i915
ance@ance-EasyNote-TE11HC:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic-pae root=UUID=7339d58a-236e-49d4-8b88-bc73d443ab8b ro quiet splash vt.handoff=7


Also tried to change grub. Didn't helped.
Just got update from update manager - restart - ok. 
During the day there were no any updates available.

---

### Post by chessmate on 2013-04-11
Hello, I have installed Ubuntu 12.04 and I have the same problem. I migrated from mac and even though I don't have all the basic knowledge in order to 'self install' everything I need yet, I believe the best way to do it is trying.

To the lio, this is the output I get:

username@computersname-MacBook:~$ ls /sys/class/backlight
apple_backlight
username@computersname-MacBook:~$ lsmod | grep video
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
username@computersname-MacBook:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-27-generic root=UUID=5f59014a-f5f9-4946-986d-652003df4751 ro quiet splash vt.handoff=7
username@computersname-MacBook:~$ sudo nano ect/default/grub



I tryied changing the grub and nothing and when I try 'sudo nano ect/default/grub' the file does not exist.

I need some help with this please. Thank you

---

### Post by oldos2er on 2013-04-11
chessmate, you're more likely to get help if you start a new thread.

---

### Post by chessmate on 2013-04-18
Thank you odos2er, I believe this thread is ended.?

---

### Post by ThatNewGuy on 2013-05-29
This worked for me(HP dv6 laptop)

Thanks

> Hi

Open a terminal and type

     Code:
     
sudo nano /etc/default/grub 
Enter your password. It will not be echoed to the screen.

Look for the line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it so it says

     Code:
     
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=*vendor***" 
Press ctrl + o to save and ctrl + x to exit.

Then type

     Code:
     
sudo update-grub 
Reboot your PC and check your function keys. Post back if it doesn't work.

Edit: Just in case you missed it i have highlighted what you need to enter.

Kind regards

---

