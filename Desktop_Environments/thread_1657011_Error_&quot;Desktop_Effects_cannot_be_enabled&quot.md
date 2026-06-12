---
title: "Error: &quot;Desktop Effects cannot be enabled&quot;"
date: 2010-12-31
forum: Desktop Environments
---

### Post by Valkyr333 on 2010-12-31
So I just got a new computer, which uses an nVidia GT218 [GeForce 310H] (rev a2) graphics chip, and I found out by using [CompizCheck]("http://forlong.blogage.de/entries/pages/Compiz-Check") that the driver is called "nouveau." My system is Kubuntu Lucid/10.04, and I'm using the 32-bit version available at,

[http://www.ubuntu.com/desktop/get-ubuntu/download#currentrelease](http://www.ubuntu.com/desktop/get-ubuntu/download#currentrelease)

I've been trying to install and enable Compiz Fusion and get the Desktop Cube up and running the way I had it with my last computer. Compiz check was forced to skip the last two of its checks, so I didn't end up getting the info on why it won't currently work. Currently, whenever I go through the first steps, I come to a grinding halt with enabling Desktop Effects. By default, it's set on "None," which is different than the last computer on which I did this, where the default was "Normal." Trying to get it to be either "Normal" or "Extra" (preferably the latter) causes a relatively short driver search to happen, followed by the windows on my screen jumping/flashing, and then an error message, "Desktop Effects could not be enabled."

Extra Info: When I open up the "nVidia X Server Settings", it tells me,

" You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server" 

^This, despite the fact that when I look in System> Administration> Hardware Drivers, the nVidia components don't show any problems at all. 

My intuition tells me this is probably the source of the problem, but I've been strongly cautioned to never run -anything- as Root, so I haven't tried that yet.

What advice would you give?

Thanks!

-Val

*Update - In tinkering around a bit, I wound up restarting the computer only to return to a really low-res, tweaky version of the login screen. It said I was currently running in low-graphics mode, and the display looked as though the left and right sides were cut apart and then switched with one another, if that makes any sense. Going back to the default graphics configuration gets me back to where the display is usable again, but I'm still right where I started.

---

### Post by BicyclerBoy on 2010-12-31
The nouveaux driver is the default *buntu shipped/installed. 
It is supposed to be quite good now. 
Would have thought some minimal desktop effects possible.

If you want to dump it & go with closed source binary blob:
You need to install nvidia driver.
The nouveaux driver sometimes needs to be blacklisted as well as un-installed because it's kernel component causes the nvidia driver to fail to start.

Check your xorg log files & dmesg output for clues.
If you see messages about nvidia failed to load & nouveaux is still mentioned then try blacklisting the module.

sudo gedit  /etc/modprobe.d/blacklist.conf
& paste  these lines at the end of  the file

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

---

### Post by Valkyr333 on 2011-01-01
Hey, thanks for your response.

I think the problem might not be with the nVidia and noveaux, but rather with the missing X Driver mentioned in the error message. I'd like to install this, or configure it properly, etc, and see if that fixes the problem, but once again I need a way to do that without logging in as Root.

Is there a command along the lines of "sudo apt get-install (name of driver)" that I could use to install it, or activate it if it's already there?

Sorry if I come off totally clueless here. I'm almost totally new to all this. =\

-Val

---

### Post by Valkyr333 on 2011-01-01
I mean, how likely is it that the default setting for Desktop Effects really was "None"? Isn't it more likely I accidentally *disabled* something necessary for that?

---

### Post by Krytarik on 2011-01-01
The desktop effects are generally disabled if there is no video driver activated which provides hardware-acceleration.

1. Backup your existing "xorg.conf":
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup-02.01.2010
```2. Generate a new one:
```
sudo nvidia-xconfig --force-generate
```3. If that doesn't help, try re-installing the driver via "Hardware Drivers" or Synaptic.

If that all doesn't work, please post the content of "/var/log/Xorg.0.log", within Code-tags or as attachment (zipped).

---

### Post by Valkyr333 on 2011-01-01
Hi, Krytarik...

The first command there, for backing up xconfig, returns "command not found." The second one, for force-generating the file, seems to work. It returns,

"New X configuration file written to '/etc/X11/xorg.conf' "

I've seen this^ message before, though, and upon restart of the computer, nothing changes. Does "Restart X Server" therefore mean performing some action other than restarting the computer? Maybe this is old Windows Mindset that needs to be defeated. Still, if the commands you've listed need to be performed in that order, I need to know how to remedy the "command not found" error.

Also, I tried re-installing everything associated with nVidia via Synaptic. After this point, nothing had changed (trying to enable desktop effects still produces the same results, and "nVidia X Server Settings" still reports that the driver is not in use.) Is it worth trying to use Synaptic to -completely- remove them all before trying to reinstall again?

---

### Post by BicyclerBoy on 2011-01-02
Just FYI

The x driver from nvidia is the nvidia-glx-260 package (for example)
So for nvidia graphics driver should have (synaptic package manager)

nvidia-glx-260
nvidia-260-modaliases
nvidia-260-kernel-source
libvdpau1
nvidia-settings

The nvidia kernel module must compile against your kernel version..
You need the kernel headers package that matches your kernel.

linux-headers-2.6.32.....something

uname -r    will indicate your kernel version.

When installing in synaptic you can click "details" to see any error messages...



The previous message 1st command failed because it is missing the copy cmd: "cp"

---

### Post by logangorence on 2011-01-02
It may not be a good Graphics Card.
Or maybe Ubuntu thinks it isn't.
Maybe Ubuntu just doesn't like it. My Laptop doesn't allow me to enable it either.

---

### Post by Valkyr333 on 2011-01-02
Hey, again!

It seems that in Synaptic, only those last two are available when I search for "nvidia"

Not showing up are...

nvidia-glx-260
nvidia-260-modaliases
nvidia-260-kernel-source

Does this mean that I need to enable another repository, or when you said "for example" did you mean that those weren't necessarily the package names as apply to my system?

uname -r returned "2.6.32-27-generic", I made sure I had everything marked as the same in Synaptic.

---

### Post by TrevP on 2011-01-03
> **Valkyr333 said:**
> So I just got a new computer, which uses an nVidia GT218 [GeForce 310H] (rev a2) graphics chip, and I found out by using [CompizCheck]("http://forlong.blogage.de/entries/pages/Compiz-Check") that the driver is called "nouveau." My system is Ubuntu Lucid/10.04, and I'm using the 32-bit version available at,

[http://www.ubuntu.com/desktop/get-ubuntu/download#currentrelease](http://www.ubuntu.com/desktop/get-ubuntu/download#currentrelease)

I've been trying to install and enable Compiz Fusion and get the Desktop Cube up and running the way I had it with my last computer. Compiz check was forced to skip the last two of its checks, so I didn't end up getting the info on why it won't currently work. Currently, whenever I go through the first steps, I come to a grinding halt with enabling Desktop Effects. By default, it's set on "None," which is different than the last computer on which I did this, where the default was "Normal." Trying to get it to be either "Normal" or "Extra" (preferably the latter) causes a relatively short driver search to happen, followed by the windows on my screen jumping/flashing, and then an error message, "Desktop Effects could not be enabled."

Extra Info: When I open up the "nVidia X Server Settings", it tells me,

" You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server" 

^This, despite the fact that when I look in System> Administration> Hardware Drivers, the nVidia components don't show any problems at all. 

My intuition tells me this is probably the source of the problem, but I've been strongly cautioned to never run -anything- as Root, so I haven't tried that yet.

What advice would you give?

Thanks!

-Val

*Update - In tinkering around a bit, I wound up restarting the computer only to return to a really low-res, tweaky version of the login screen. It said I was currently running in low-graphics mode, and the display looked as though the left and right sides were cut apart and then switched with one another, if that makes any sense. Going back to the default graphics configuration gets me back to where the display is usable again, but I'm still right where I started.

Hi Val,

You are currently running the Nouveau driver which has no support for 3D hardware acceleration and so it won't support visual effects which rely on Compiz. If you want visual effects to run, you need to install the proprietary nvidia driver. Go to:

System > administration > additional drivers and select the current driver version then click "activate". This should automatically install the closed source driver.

Development on the Nouveau driver is progressing very quickly and 3D support will eventually be added via Gallium3d. I have the experimental Nouveau 3d driver on my desktop (running an Nvidia 7600 card). The 3d driver is in an early stage of development and not recommended by the developers for general use, but it works very well on my system and is very stable (it even allows 3d acceleration on my windows XP installation on VirtualBox!) and runs Compiz with no problems.

People running version 10.10 of Ubuntu can try it by installing libgl1-mesa-dri-experimental from synaptic package manager (if you don't see it there you will need to enable "proposed updates" from the update tab in the settings window in the update manager). However - be warned - installation of experimental drivers at this stage of development has the potential to trash your system! The current version is not optimised for maximum framerate so gamers (and probably all sensible people) should use the proprietary driver. On the other hand, if you are curious, like living dangerously and prefer to use open source rather than closed source software, then it might be worth a try.

All the best,
Trev

---

### Post by Krytarik on 2011-01-03
I meant:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup-02.01.2010
```
forgot the actual command ("mv") over the path, sorry.

Like TrevP said, check in "Hardware Drivers" if the appropriate proprietary driver is activated.

Driver version 260 is not aviable in the Lucid archives, others are.

---

### Post by Valkyr333 on 2011-01-03
@TrevP - The funny thing is, that's the driver that was selected by default, and it worked even worse than the older one I've currently got enabled. This problem started because I was using the recommended/proprietary driver and it wouldn't enable desktop effects. Problem is, neither that one nor this one (96) seem to want to allow me to use the nVidia X-Driver (or maybe that's a separate problem), but whichever driver I'm using in "Hardware Drivers", System> Administration> NVIDIA X Server Settings turns up the same message, "You do not appear to be using the X-Driver... etc." It also gives me instructions on how to remedy this, but the difference between to two drivers (96 and proprietary/recommended) here is that when I perform the action it gives me (replacing a root login with "sudo", of course), restarting the computer gives me a message stating Ubuntu is in low-graphics mode, 96 shows the message whole and orderly, and the proprietary driver shows it as though it were cut down the middle with the two halves placed on the opposite sides of the screen. The right half of the box is hanging off the far-left of the screen, and vice-versa, and I have to read it a mix of right to left and left to right to understand all the words.

@Krytarik - Running that one in the terminal returns "mv: cannot stat `/etc/X11/xorg.conf': No such file or directory"

I'm really sorry if this is getting to be a hardcore pain in the ***, guys. I really do appreciate your help. =)

---

### Post by Krytarik on 2011-01-03
> **Valkyr333 said:**
> 
"mv: cannot stat `/etc/X11/xorg.conf': No such file or directory"
This output indicates that there is no xorg.conf.

Please post the output of
```
dpkg -l |grep nvidia
```EDIT: And you did check if the linux-headers package is installed?!
```
 dpkg -l |grep linux-headers
```

---

### Post by Valkyr333 on 2011-01-04
Hey again,

The following is the result of dpkg -l |grep nvidia

ii  nvidia-173                                173.14.22-0ubuntu11                             NVIDIA binary Xorg driver, kernel module and
ii  nvidia-173-kernel-source                  173.14.22-0ubuntu11                             Transitional package for nvidia-glx-173-kern
ii  nvidia-173-modaliases                     173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-180-kernel-source                  185.18.36-0ubuntu9                              Transitional package for nvidia-glx-185-kern
ii  nvidia-185-kernel-source                  195.36.24-0ubuntu1~10.04                        Transitional package for nvidia-glx-185-kern
ii  nvidia-96                                 96.43.17-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and
ii  nvidia-96-kernel-source                   96.43.17-0ubuntu1                               Transitional package for nvidia-glx-96-kerne
ii  nvidia-96-modaliases                      96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                             0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current                            195.36.24-0ubuntu1~10.04                        NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current-modaliases                 195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-kernel-common                      20080825+1ubuntu2                               NVIDIA binary kernel module common files
ii  nvidia-settings                           195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv

And this was the result of dpkg -l |grep linux-headers

ii  linux-headers-2.6.32-24                   2.6.32-24.43                                    Header files related to Linux kernel version
ii  linux-headers-2.6.32-25                   2.6.32-25.45                                    Header files related to Linux kernel version
ii  linux-headers-2.6.32-27                   2.6.32-27.49                                    Header files related to Linux kernel version
ii  linux-headers-2.6.32-27-generic           2.6.32-27.49                                    Linux kernel headers for version 2.6.32 on x
ii  linux-headers-generic                     2.6.32.27.29                                    Generic Linux kernel headers

---

### Post by TrevP on 2011-01-04
Hi again,

I think I've read somewhere that the Nouveau drivers can interfere with the correct installation of the closed source Nvidia driver. You might have to purge the Nouveau drivers before you can properly install the Nvidia driver (I can't give you detailed instructions because if I get it wrong it might break your system, but if you search the forum, there might be some official help on this). 

Trev

---

### Post by Krytarik on 2011-01-04
I am using the version 96 (old video card), my packages are:
```
ii  nvidia-173-modaliases                 173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96                             96.43.17-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and
ii  nvidia-96-modaliases                  96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                         0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases             195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-settings                       195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv

```
So there are definetely way to much packages installed at your machine, try removing (purge) the unnecessary ones and re-install the remaining ones.

PS: I also have the nouveau driver installed, so it apparently doesn't interfere, but you may try to purge it as well, like TrevP said. The package is called "xserver-xorg-video-nouveau".

---

### Post by Valkyr333 on 2011-01-04
Okay, so uninstalling everything that looked unnecessary and then marking for reinstall/reinstalling the ones that were still left hasn't worked. In retrospect it would've been better of me to take notes on which ones I got rid of, etc. so I could keep you on the same page. I'm gonna have to remember that from now on.

---

### Post by Krytarik on 2011-01-04
> **Valkyr333 said:**
> Okay, so uninstalling everything that looked unnecessary and then marking for reinstall/reinstalling the ones that were still left hasn't worked. In retrospect it would've been better of me to take notes on which ones I got rid of, etc. so I could keep you on the same page. I'm gonna have to remember that from now on.
Please write a new xorg.conf through "System -> Administration -> NVIDIA X Server Settings" or "sudo nvidia-xconfig --force-generate".

Post it along with /var/log/Xorg.0.log, if that didn't work either.

PS: The log of apt is stored in /var/log/apt/history.log .

---

### Post by swatsbiz on 2011-01-05
I have an issue here with ati and being unable to enable effects.

I added a dodgy apt source for ati drivers and now after trying to revert I still seem unable to get the effects to re-enable.

Usually I'd just reinstall Ubuntu, but I should really learn some more by investigating what went wrong and how to fix it.

---

### Post by realzippy on 2011-01-05
@ swatsbiz

since this thread is nvidia-driver related I highly recommend to open an own thread,or things might get complicated here...

---

### Post by swatsbiz on 2011-01-05
> **realzippy said:**
> @ swatsbiz

since this thread is nvidia-driver related I highly recommend to open an own thread,or things might get complicated here...

Thanks will do ... :-D

---

### Post by Valkyr333 on 2011-01-30
I'm back, finally.

@BicyclerBoy - So I'm ready to give the blacklisting idea a shot here. I'm at a loss for other options. If I blacklist the Noveaux Driver, will I need to reverse this once things are working properly? If so, how would I do that?

Thanks,

-Val

---

### Post by Forlong on 2011-01-31
Before you go about trying random things, you should try to narrow down the problem.

First of all, please post the current output of compiz-check.
Additionally the output of
```
dpkg -l | grep "nvidia\|fglrx"
```
In both cases, please use the forum's [CODE] tag (# button in the editor)

The installed packages you posted earlier indicate that you were trying to install the nvidia driver "manually" or by script, is that the case?

---

### Post by Valkyr333 on 2011-02-10
"compiz-check" returns "command not found."

dpkg -l | grep "nvidia\|fglrx" 
returns:

```
ii  fglrx                                     2:8.723.1-0ubuntu5                              Video driver for the ATI graphics accelerato
ii  fglrx-amdcccle                            2:8.723.1-0ubuntu5                              Catalyst Control Center for the ATI graphics
ii  fglrx-modaliases                          2:8.723.1-0ubuntu5                              Identifiers supported by the ATI graphics dr
ii  nvidia-173                                173.14.22-0ubuntu11                             NVIDIA binary Xorg driver, kernel module and
ii  nvidia-173-kernel-source                  173.14.22-0ubuntu11                             Transitional package for nvidia-glx-173-kern
ii  nvidia-173-modaliases                     173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96                                 96.43.17-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and
ii  nvidia-96-kernel-source                   96.43.17-0ubuntu1                               Transitional package for nvidia-glx-96-kerne
ii  nvidia-96-modaliases                      96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                             0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current                            195.36.24-0ubuntu1~10.04                        NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current-modaliases                 195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-kernel-common                      20080825+1ubuntu2                               NVIDIA binary kernel module common files
ii  nvidia-settings                           195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv
```

And yes, I was using both the terminal and synaptic, the latter mostly if not only in Gnome.

---

### Post by Forlong on 2011-02-11
Compiz-Check is the script you linked in your first posting, you'll most probably have to run it like this in the terminal:
```
./compiz-check
```
Post it's output here, because wee need to know exactly what hardware is detected. You have both an ATI as well as several nvidia drivers installed. This is a problem.

---

### Post by Valkyr333 on 2011-02-11
Thanks for the clarification. The result of ./compiz-check is...

```
 Distribution:          Ubuntu 10.04
 Desktop environment:   KDE4
 Graphics chip:         nVidia Corporation GT218 [GeForce 310M] (rev a2)
 Driver in use:         nouveau
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

Okay, so would the idea be to remove the ATI and all but the most relevant of the Nvidia drivers?

---

### Post by Forlong on 2011-02-11
Yeah, I'd recommend un-installing all of them:
```
sudo apt-get purge fglrx fglrx-amdcccle nvidia-173 nvidia-173-kernel-source nvidia-173-modaliases nvidia-96 nvidia-96-kernel-source nvidia-96-modaliases nvidia-current nvidia-current-modaliases nvidia-kernel-common
```
Afterwards, run this for a clear config:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Finally, **reboot** and see if there's a driver listed at **System &#8594; Administration &#8594; Additional Drivers**

Edit: sorry, missed that you are on KDE. I'm not sure where it's located there, in case you don't know either, running this command should do the job:
```
jockey-kde
```

---

### Post by HTMLCrazy on 2011-02-15
I am having the same problems and ran the compiz check and now gnome do isn't working, no titles on any windows are showing up.

Fixable?

---

### Post by HTMLCrazy on 2011-02-15
I rebooted and my title bars are back, but still no desktop effects.

I have been told that there is a command taht will let ubuntu automatically detect your graphics card and download needed drivers. I was told it started with "dpkg" and had something to do w/ xorg.

---

### Post by Forlong on 2011-02-15
Compiz-Check does not change anything on your system (unless you specifically tell it to in certain cases).

Post its output here, so people can try to help you with your case.

---

### Post by HTMLCrazy on 2011-02-15
> **Forlong said:**
> Compiz-Check does not change anything on your system (unless you specifically tell it to in certain cases).

Post its output here, so people can try to help you with your case.
i tried and it said that current display alreadyhad a window manager and that it was falling back on default window manager and that was when everything stopped working. I couldn't do anything and had to reboot the computer.

---

### Post by Forlong on 2011-02-15
> **HTMLCrazy said:**
> i tried and it said that current display alreadyhad a window manager and that it was falling back on default window manager
Then you were most certainly running ```
compiz
``` in a terminal and not Compiz-Check. Compiz-Check does not run Compiz (or any other window manager for that matter) for you.

Please follow the steps here: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by HTMLCrazy on 2011-02-15
Here is the output code:
```
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
```

---

### Post by Forlong on 2011-02-15
As I said, you are not running Compiz-Check but the compiz binary.

---

### Post by Krytarik on 2011-02-15
> **HTMLCrazy said:**
> 
I have been told that there is a command taht will let ubuntu automatically detect your graphics card and download needed drivers. I was told it started with "dpkg" and had something to do w/ xorg.
What you are meaning is "System -> Administration -> Additional Drivers".

---

### Post by HTMLCrazy on 2011-02-15
I did what Forlong said on his blog w/ downloading the file, etc.
This is the output that I got.
```
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon IGP 330M/340M/350M
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

```

It then proceeded to check for a proprietary driver but "no proprietary drivers were in use on the system."

What should I do next?

I already have a feed at: [http://ubuntuforums.org/showthread.php?t=1682736](http://ubuntuforums.org/showthread.php?t=1682736)
Please put any further posts for me there. Krytarik has been helping me.
Make sure that you go to the last page.
I tried to go through the get additional drivers but there is nothing there.

---

### Post by Valkyr333 on 2011-02-21
> **Forlong said:**
> Yeah, I'd recommend un-installing all of them:
```
sudo apt-get purge fglrx fglrx-amdcccle nvidia-173 nvidia-173-kernel-source nvidia-173-modaliases nvidia-96 nvidia-96-kernel-source nvidia-96-modaliases nvidia-current nvidia-current-modaliases nvidia-kernel-common
```Afterwards, run this for a clear config:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Finally, **reboot** and see if there's a driver listed at **System &#8594; Administration &#8594; Additional Drivers**

Edit: sorry, missed that you are on KDE. I'm not sure where it's located there, in case you don't know either, running this command should do the job:
```
jockey-kde
```

The following is the result of jockey-KDE:
```

/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/valkyr/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
```A "Hardware Drivers" window opens up which states that "No proprietary drivers are in use on this system."

*Edit - Uninstallation of the unneeded drivers and any "no longer needed" automatically installed packages was successful.

---

### Post by Forlong on 2011-02-21
After you have rebooted, run Compiz-Check again and post its output here, so we'll see what driver is in use now.

---

### Post by Valkyr333 on 2011-02-21
O____O WHOA, NELLEH!! ::falls over::

Everything looks much different as of said reboot. Images are much sharper, and fonts seem much more compact. "compiz-check" returned "command not found" so I gather this means some part of the earlier process removed either Compiz or a component thereof which was essential to doing this.

*Also, Desktop Effects are now showing as enabled, which makes sense because everything seems a great deal more animate.

---

### Post by Forlong on 2011-02-21
See here: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by Valkyr333 on 2011-02-21
Got it. Compiz-Check returned...

```
 Distribution:          Ubuntu 10.04
 Desktop environment:   KDE4
 Graphics chip:         nVidia Corporation GT218 [GeForce 310M] (rev a2)
 Driver in use:         nouveau
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 
```

I also notice that several desktop effects (explosion, blur, desktop cube, desktop cube animation, *et al*) can't be enabled at present.

---

### Post by Krytarik on 2011-02-21
Too soon spoken. Was already posting a congrats-post concurrently.

If you removed any driver packages related to nvidia or fglrx, then just try re-installing the proper proprietary nvidia driver via "Additional Drivers".

EDIT: Or "jockey-kde", if that works out for you.

---

### Post by Forlong on 2011-02-21
Is there still no driver available in
```
jockey-kde
``` ?

---

### Post by Valkyr333 on 2011-02-21
> **Krytarik said:**
> Too soon spoken.

Okay, I'll keep that in mind. Thanks, btw. It's more to manage, but I know I'll get the hang of it. =)

Is there anything else that's left to do here, or would you guys say the thread should be marked "Solved"?

---

### Post by Valkyr333 on 2011-02-21
@Forlong - Yeah, it still says "There is no proprietary driver in use on this system."

---

### Post by Krytarik on 2011-02-21
> **Valkyr333 said:**
> Okay, I'll keep that in mind. Thanks, btw. It's more to manage, but I know I'll get the hang of it. =)

Is there anything else that's left to do here, or would you guys say the thread should be marked "Solved"?
Seen my editited post? Sometimes you should just wait longer before posting, to avoid such an overlap, sorry.;)

---

### Post by Valkyr333 on 2011-02-21
Okay. I'm gonna go look for the right proprietary driver.

---

### Post by Valkyr333 on 2011-02-21
Alright, so in Synaptic, I searched "nvidia" and added nvidia-glx-173 (which was listed as the driver for Ubuntu 10.04) I closed Synaptic without reloading after I finished installing, and then re-opened it and reloaded when I realized this. At this point, jockey-kde still shows the "no proprietary drivers" message.

---

### Post by Forlong on 2011-02-21
You definitely need the proprietary nvidia driver. Nouveau is currently not able to run Compiz on Ubuntu.
I read that there might be a driver available suitable for some cards in the backports.
Rund this command to add them to your sources:
```
echo deb http://archive.ubuntu.com/ubuntu maverick-proposed restricted main multiverse universe | sudo tee -a /etc/apt/sources.list
```
Afterwards, do an update:
```
sudo apt-get update && sudo apt-get upgrade
```
Finally, see if there is an additional driver available in jockey now.

---

### Post by Forlong on 2011-02-21
> **Valkyr333 said:**
> Alright, so in Synaptic, I searched "nvidia" and added nvidia-glx-173 (which was listed as the driver for Ubuntu 10.04) I closed Synaptic without reloading after I finished installing, and then re-opened it and reloaded when I realized this. At this point, jockey-kde still shows the "no proprietary drivers" message.
This is not the proper way to install a graphics driver on Ubuntu - DO NOT INSTALL THOSE PACKAGES MANUALLY (unless you know what you are doing).
Please remove the package again.

---

### Post by Valkyr333 on 2011-02-21
Okay. Packages uninstalled, codes run. jockey-kde still returns the same message. I noticed that the code you listed included "maverick." Does it matter that I'm running 10.04 and not 10.10 for the purposes of that command line?

---

### Post by Forlong on 2011-02-21
> **Valkyr333 said:**
> I noticed that the code you listed included "maverick." Does it matter that I'm running 10.04 and not 10.10 for the purposes of that command line?
Whoa, sorry. Run a text editor being root
```
kdesu kate /etc/apt/sources.list
```
and remove the line again, then save and update once more.

---

### Post by Valkyr333 on 2011-02-21
This returns "kdesu: command not found"

---

### Post by Krytarik on 2011-02-21
> **Valkyr333 said:**
> This returns "kdesu: command not found"
It should be "kdesudo".

Btw., you should include your Ubuntu version in your profile to avoid such things.

---

### Post by Valkyr333 on 2011-02-21
"kdesudo" gets me a notification,

p, li { white-space: pre-wrap; }```
No command arguments supplied!
 Usage: kdesudo [-u <runas>] <command>
 KdeSudo will now exit...

```

I've tried looking up this "command arguments" business before, but I don't think I quite understand it.

PS - I will be editing my profile to reflect my Ubuntu Version immediately after posting this reply.

---

### Post by Krytarik on 2011-02-21
> **Valkyr333 said:**
> "kdesudo" gets me a notification,

p, li { white-space: pre-wrap; }```
No command arguments supplied!
 Usage: kdesudo [-u <runas>] <command>
 KdeSudo will now exit...

```I've tried looking up this "command arguments" business before, but I don't think I quite understand it.

PS - I will be editing my profile to reflect my Ubuntu Version immediately after posting this reply.
Hey!! :-k
```
kdesudo kate /etc/apt/sources.list
```

---

### Post by Valkyr333 on 2011-02-21
Yeah, sorry I realized that was what I was supposed to be doing a minute after posting. I should've updated/edited my post. I ran that and it opened up kate for me. I removed the bad line at the end with maverick, and ran the update.

---

### Post by Krytarik on 2011-02-21
And the "jockey" doesn't offer you to install/activate a proprietary driver?

If so, try removing the "nouveau" driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Recommended%20step%20for%20Ubuntu%2010.04%20or%20higher]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Recommended%20step%20for%20Ubuntu%2010.04%20or%20higher")

Then reboot (to be sure) and run the jockey again.

---

### Post by Valkyr333 on 2011-02-21
Okay, so I uninstalled the novaeu driver, rebooted and checked jockey again. The result was the same, but now things look a little sloppier around the desktops. I opened up "system settings" because it was the first thing that came to mind for a window to look and see if there was any change since the uninstallation and reboot. It's kinda hard to describe how it changed, but I could get you a screencap if you think it might help.

---

### Post by Krytarik on 2011-02-21
It's naturally that the video gets worse when you uninstall the nouveau driver, because now the lowest tier driver designed for nvidia cards is in use.

However it's disappointing that the jockey even now doesn't give a driver option.
Do you have any remnants of a manual driver installation around? If so, remove them as well, following the install instructions.

---

### Post by Valkyr333 on 2011-02-22
I never installed any drivers manually, if that's what you're asking. If the term means something else, then I don't know how to answer the question.

---

### Post by Krytarik on 2011-02-22
> **Valkyr333 said:**
> I never installed any drivers manually, if that's what you're asking. If the term means something else, then I don't know how to answer the question.
That's what I meant. If *Forlong* doesn't comes up with a better idea, I would try to install the correct driver packages through Synaptic. Though it is the second-least way to install the proprietary driver.

I posted you my installed packages before:
[http://ubuntuforums.org/showthread.php?p=10316304#post10316304](http://ubuntuforums.org/showthread.php?p=10316304#post10316304)

I searched for the correct driver version for your chip, but it isn't specifically named anywhere, that may also be the reason why the jockey doesn't offer one.
However I believe the "current" driver is appropriate, version 260.

So, it should be sufficient to install the following packages, they will pull other packages if necessary:
- nvidia-current
- nvidia-settings

I assume you don't need to install "nvidia-common" and "nvidia-current-modaliases", since they are apparently only needed by the jockey.

After the installation, run the following command in the terminal, to create a proper xorg.conf, just to be sure:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```

---

### Post by Valkyr333 on 2011-02-22
Thanks a bunch. I'll give it a few days and see if Forlong has any other ideas, if not, I'll do that. =)

All the best,

-Val

---

### Post by Valkyr333 on 2011-02-23
Okay, I tried the steps you mentioned above. Nothing really changed about the way things were working, except that suddenly flash video (really, flash anything) was even more quick to crash and need re-loading, and began to crash anytime I tried to maximize/fullscreen a window. I figured (clearly wrongly) that uninstalling the things I just installed would get me back to where I was where at least I could use flash and things were looking pretty good, until a better fix could be found. Now, my Ubuntu won't start up at all. Attempts to log in cause my screen to flash on and off twice and then return to the login screen. Restarting in failsafe/recovery mode got me the message that the "novuaeu" driver no longer exists so the display is unable to run. I've gotta admit, I'm getting pretty frustrated here. I'm writing this from another computer logged on in bloody Windows. I'm not about to give up, but I can't imagine what else I should be doing from here.

*Edit - This may or may not be a given, but I can't even get in in recovery mode. Also, somehow I was able to get in to kde desktop once after having uninstalled the recent packages. A lot of my settings were gone, and a lot of the configuration editing screens weren't acessible (giving me an error message referring to nonexistant files) but it still let me into the desktop. I don't know if this means something has changed since then, but I'm hoping the extra details will paint a better picture of what's happening.

---

### Post by Krytarik on 2011-02-23
I would also try the driver provided by Ubuntu-X-Swat, they are more up-to-date:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

It is up to you to decide, wether you want to revert to the previous state, that was apparently not bad at all, or install the driver provided by the aforementioned.

If you want to revert,
- boot into recovery mode
- choose "root shell prompt"
- remove the "/etc/X11/xorg.conf"
- install the "nouveau" driver
- reboot

If you want to try Ubuntu-X-Swat's driver package,
- boot into recovery mode
- choose "root shell prompt"
- add the PPA, update the package-db
- install "nvidia-current" and "nvidia-settings"
- configure the xorg.conf as before
- reboot

**EDIT:** I now saw your (most recent) edit. Did you inadvertedly remove more than the driver packages? See "/var/log/apt/history.log".

---

### Post by Valkyr333 on 2011-02-23
I'm booted in recovery mode, using root shell prompt. I used the commands,

```

apt-get remove /etc/X11/xorg.conf
```

and 

```
apt-get install nouveau
```

These returned,

```
E: couldn't find package
```

and

```
E: Couldn't find package nouveau
```

And I may have accidentally done that, but to be sure, how do I access/view "/var/log/apt/history.log" from the root shell prompt?

---

### Post by realzippy on 2011-02-23
The package is named:
xserver-xorg-video-nouveau
so at root shell:

```
apt-get install xserver-xorg-video-nouveau
```


*view "/var/log/apt/history.log" * :

```
cat /var/log/apt/history.log
```

---

### Post by Krytarik on 2011-02-23
And to delete the xorg.conf:
```
rm /etc/X11/xorg.conf
```
I assumed you know this basic command, and the precise name of the nouveau driver package from your previous removal.

---

### Post by Valkyr333 on 2011-02-23
@Kytarik:

```
rm /etc/X11/xorg.conf
```Returns,

```
rm: cannot remove '/etc/X11/xorg.conf' : No such file or directory
```Does this mean it really isn't there anymore, or just that Ubuntu can't see it?

Edit: I've learned a few commands, but that wasn't one I'd yet run across. Also, my memory is nowhere near that photographic, and I have a hard time with specific details like those due to past dealings with mis-prescribed psychiatric drugs. I'm not trying to rub my issues in anyone's face, but at least it makes it a little clearer why I have such a need to write things down. I'll do that from now on.

---

### Post by Krytarik on 2011-02-23
> **Valkyr333 said:**
> 
```
rm: cannot remove '/etc/X11/xorg.conf' : No such file or directory
```Does this mean it really isn't there anymore, or just that Ubuntu can't see it?
Yes, given that you issued the command correctly, it means that the file isn't there.
> **Valkyr333 said:**
> 
Edit: I've learned a few commands, but that wasn't one I'd yet run across. Also, my memory is nowhere near that photographic, and I have a hard time with specific details like those due to past dealings with mis-prescribed psychiatric drugs. I'm not trying to rub my issues in anyone's face, but at least it makes it a little clearer why I have such a need to write things down. I'll do that from now on.
Thanks for clearing it up, I will take that into consideration from now on.

---

### Post by Valkyr333 on 2011-02-23
Thanks for your consideration, I really do appreciate how patient you've all been with me on this.

Okay. So, if the /etc/X11/xorg.conf file is not there, what would be the next step? At this point, rebooting still produces the same results I mentioned above (login attempts resulting in the flashing screen and landing back on the login-screen).

---

### Post by Krytarik on 2011-02-23
Did you already install the nouveau driver? What about the apt log?

---

### Post by Valkyr333 on 2011-02-23
I did install the nouveau driver. The apt-log reflects having removed the wallpapoz application which I no longer needed, installing and later purging nvidia-current (195.36.24-0ubuntu1~10.04), and nvidia-settings (195.36.08-0ubuntu2) before installing the nouveau driver.

---

### Post by Krytarik on 2011-02-23
I'm wondering why there was no xorg.conf, did you set it up with the given command after you installed the nvidia driver?

Try to activate the nouveau driver following this post:
[http://ubuntuforums.org/showthread.php?p=9120571#post9120571](http://ubuntuforums.org/showthread.php?p=9120571#post9120571)

You may also want upgrade the nouveau driver to those provided by the xorg-edgers ppa, to get the most recent version:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```Or without "sudo" when running those command at the root shell prompt, the same is true for the commands given in the post.

---

### Post by Valkyr333 on 2011-02-23
> **Krytarik said:**
> I would also try the driver provided by Ubuntu-X-Swat, they are more up-to-date:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

It is up to you to decide, wether you want to revert to the previous state, that was apparently not bad at all, or install the driver provided by the aforementioned.

If you want to revert,
- boot into recovery mode
- choose "root shell prompt"
- remove the "/etc/X11/xorg.conf"
- install the "nouveau" driver
- reboot

If you want to try Ubuntu-X-Swat's driver package,
- boot into recovery mode
- choose "root shell prompt"
- add the PPA, update the package-db
- install "nvidia-current" and "nvidia-settings"
- configure the xorg.conf as before
- reboot

**EDIT:** I now saw your (most recent) edit. Did you inadvertedly remove more than the driver packages? See "/var/log/apt/history.log".

I followed the first list of instructions you gave above^ on how to revert to the nouveau driver. Are you referring to a command listed in an earlier response?

---

### Post by Krytarik on 2011-02-23
> **Valkyr333 said:**
> I followed the first list of instructions you gave above^ on how to revert to the nouveau driver. Are you referring to a command listed in an earlier response?
No, that was correct.

---

### Post by Valkyr333 on 2011-02-23
As of running the command for updating/upgrading the driver, and rebooting, the login situation remains the same. Where you mention the other post and trying to activate the nouveau driver, are you referring to the whole thread, or just the first post on the screen when that link is clicked?

---

### Post by Krytarik on 2011-02-23
> **Valkyr333 said:**
> As of running the command for updating/upgrading the driver, and rebooting, the login situation remains the same. Where you mention the other post and trying to activate the nouveau driver, are you referring to the whole thread, or just the first post on the screen when that link is clicked?
Only that exact post, #33.

---

### Post by Valkyr333 on 2011-02-23
I realize I've been sitting on top of this thing all day and I dunno about you, but I could use a break. I'm gonna get back at it tomorrow after work. Thanks again. =)

Edit: Okay, that'll be the first place I look tomorrow.

---

### Post by Valkyr333 on 2011-02-25
Okay, gave #33 a shot.

```
update-alternatives --config gl_conf
```

Returns...
```

There is only one alternative in link group gl_conf: usr/lib/mesald.so.conf
Nothing to configure.
```

---

### Post by Krytarik on 2011-02-25
Please recap the current state. You can normally boot into your desktop, but you can't enable desktop effects, is that right?
What is the output of the compiz script now, or of "lshw -c video"?

---

### Post by Valkyr333 on 2011-02-26
The current situation is that my graphics driver is uninstalled, and I can't log into my desktop. Whether in regular or low-graphics mode, attempts to login result in the splash screen showing for a second, then the screen flashing twice or three times, then dumping me back at the login screen. The most I can do right now is root shell prompt. I'm signed into the Ubuntu Forums right now  via my backup computer which is running Windows. "compiz-check" returns "command not found." "lshw -c video" returns,

```
*-display
description: VGA compatible controller
product: GT218 [GeForce 310M]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a2
width: 64 bits
clock: 33MHz
capabilities pm msi pciexpress bus_master cap_list rom
configuration: driver=nouveau latency=0
resources irq 16 memory:e2000000-e2ffffff memory: d0000000-dfffffff memory:e0000000-e1fffffff ioport:d000(size=128) memory:e3000000-e307ffff
```

---

### Post by Krytarik on 2011-02-26
As you can see, the "nouveau" driver is indeed already running.

So, are you getting to the graphical login screen (GDM), or are you *dumped* even before to the console login?

Please post the contents of "/var/log/Xorg.0.log" and "/home/USER/.xession-errors" after that happened.

---

### Post by Valkyr333 on 2011-02-26
I'm getting the screen where you pick a username and enter your password, and I do so. Then I start to see the splash screen before it flashes and puts me back where login information is to be entered.

Both of those commands return "bash: No such file or directory" with the name of the log file between "bash:" and "No such file or directory."

---

### Post by Krytarik on 2011-02-26
> **Valkyr333 said:**
> I'm getting the screen where you pick a username and enter your password, and I do so. Then I start to see the splash screen before it flashes and puts me back where login information is to be entered.

Both of those commands return "bash: No such file or directory" with the name of the log file between "bash:" and "No such file or directory."
I don't see any splash screen after I entered my login details. What do you see there?

The files MUST be there, of course you have to replace "USER" with your username in the path of the latter log.

EDIT: Remember, those are log files, not commands. So choose what ever way you have to get a copy of them out of there.

---

### Post by Valkyr333 on 2011-02-26
"I don't see any splash screen after I entered my login details. What do you see there?"

Wait, I'm confused. What do you mean? What do your login details and your screen have do to with my computer and my logging in? Just to clarify, I understand "Splash Screen" to mean the screen visible during login, between entering login information and the desktop w/ workspaces, etc. The screen in KDE where a few icons are seen fading into visibility before you get to the desktop.

And okay, it didn't occur to me before to put my username in there. When I enter that file name with my username in place of "USER" in root shell prompt, it returns "permission denied." As for "/var/log/xorg.o.log" what would I change about that to get it to give me the information needed? At this point, it just tells me there's no such file or directory. If the file absolutely -has- to be there, then I assume it means I'm not asking the computer for it in the right way. Is that steady reasoning in this context?

---

### Post by Krytarik on 2011-02-26
Ok, you use KDE, and obviously there is a splash after login. I use Gnome.

Note that "Xorg.0.log" is case sensitive, and there is a zero in the middle between the points.

At my system I would enter the following to see the logs, at the console:
```
more /var/log/Xorg.0.log
more /home/krytarik/.xsession-errors
```

---

### Post by Valkyr333 on 2011-02-26
Okay. So, those two things entered into my root shell prompt both return way more information than I'm able to transcribe manually, and since it's showing up on the other computer screen, I can't copy-paste it in here either. Is there a specific field or fields that you're thinking of which I could look for in the results, and then transcribe here?

---

### Post by Krytarik on 2011-02-26
I guess errors and warnings are usually logged with "EE" and "WW" in the line of the log.

So the following commands would filter those out of Xorg.0.log:
```
cat /var/log/Xorg.0.log |grep EE
cat /var/log/Xorg.0.log |grep WW
```
Do it for your users ".xsession-errors" accordingly.

---

### Post by Valkyr333 on 2011-02-26
cat /var/log/Xorg.0.log |grep EE

returns:

(WW) warning, (EE) error, (NI) not implemented, (??) unknown..
[        41.010] (II) Loading extension MIT-SCREEN-SAVER

(the two E's in "SCREEN-SAVER" are showing in red, the rest of the text in gray)

cat /var/log/Xorg.0.log |prep WW

returns:

(WW) warning, (EE) error, (NI) not implemented, (??) unknown
[          40.991] (WW) The directory "usr/share/fonts/X11/cyrillic" does not exist.
[          41.016] (WW) Falling back to old probe method for vesa
[          41.016] (WW) Falling back to old probe method for fbdev
[141060.520] (WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused.)

*Edit - once again, all the "(WW)" are with the letters WW in red, the rest in gray.

---

### Post by Krytarik on 2011-02-26
> **Valkyr333 said:**
> cat /var/log/Xorg.0.log |grep EE

returns:

(WW) warning, (EE) error, (NI) not implemented, (??) unknown..
[        41.010] (II) Loading extension MIT-SCREEN-SAVER

(the two E's in "SCREEN-SAVER" are showing in red, the rest of the text in gray)

cat /var/log/Xorg.0.log |prep WW

returns:

(WW) warning, (EE) error, (NI) not implemented, (??) unknown
[          40.991] (WW) The directory "usr/share/fonts/X11/cyrillic" does not exist.
[          41.016] (WW) Falling back to old probe method for vesa
[          41.016] (WW) Falling back to old probe method for fbdev
[141060.520] (WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused.)

*Edit - once again, all the "(WW)" are with the letters WW in red, the rest in gray.
Nothing serious or related in there. How about ".xsession-errors"?

---

### Post by Valkyr333 on 2011-02-27
".xsession-errors" returns "command not found." Is there some adaption I should be making to that command for better results?

---

### Post by realzippy on 2011-02-27
*.xsession-errors* is a file in your home directory,not a command.

the "."  in front indicates file as hidden.

Anyway,to see file's content from shell:

```
cat .xsession-errors
```

Open it with texteditor in gnome:

```
gedit .xsession-errors

```

---

### Post by Valkyr333 on 2011-02-27
cat .xsession errors also returns "no such file or directory."

I can't sign in with Gnome at the moment. Also, suddenly my ability to type on the login screen is gone. The keyboard just doesn't input the characters whether I select Gnome, Failsafe Gnome, KDE or otherwise... And for some reason, my computer just randomly shut itself off completely after sitting on that login screen for a minute, without any prompting whatsoever.

I'm really starting to think I might be better off deleting and then reinstalling Ubuntu, starting all over again and being more careful this time. Is that possible (or wise) in the current state?

*Edit - Yeah, it's just totally shutting down after about two minutes no matter what I do now. What the Hell? >.<

---

### Post by realzippy on 2011-02-27
[I]cat .xsession errors also returns "no such file or directory."
[/I]

You were at root shell?
File is in your user's home directory,had to navigate there.

Anyway,a fresh install takes a few minutes,and you have a vanilla system status which helps others helping you.

---

### Post by Valkyr333 on 2011-02-27
I would pay a king's ransom for a blank slate right now. PLEASE do tell me how I can go about doing this from here.

Note: The computer is double-partitioned with Windows 7 if it can be done more easily from there.

*Edit: *sigh* Even from Windows Logon, the keyboard is unresponsive. I'm srsly just about to blow my brains out, here.

---

### Post by realzippy on 2011-02-27
Where is the problem?
Insert Ubuntu CD and install it again.
make sure you are connected to the internet;
after first login run

```
sudo apt-get update

sudo apt-get upgrade
```

---

### Post by Valkyr333 on 2011-02-27
I don't have an Ubuntu CD, I installed it on my hard drive by downloading it from the website in Windows and then running the setup. In theory I could make an installation CD from this computer, then use it on that one, but the disk drive in this one doesn't often write things successfully anymore, and even if I could, the keyboard on the one that needs fixing won't type anything and will barely even respond to use of the arrow keys. That's the problem.

*Update - I thought of installing it by creating a USB Flash Drive version. I'm trying to do that from this computer, but I'm not sure what it means when it asks me to browse for my iso file. Is there some file I need to create prior to creating a USB Stick Installer?

---

### Post by realzippy on 2011-02-27
So you had a wubi install ?
Can't help you with your keyboard,if it is a hardware issue.
If it is a software/USB issue,switch off your computer completely for
a few seconds(Unplug power cable).

---

### Post by Valkyr333 on 2011-02-27
Yeah, it's been shut down and unplugged at least twice by now, the keyboard is still doing this.

---

### Post by realzippy on 2011-02-27
No idea for your keyboard.
Maybe *Krytarik* has an idea ?

---

### Post by Krytarik on 2011-02-27
Good morning to you both!

1.) You probably misspelled ".xsession-errors" (at least you posted it wrong), follow my earlier instructions/example

2.) I don't see the pressing need for a fresh install, even at this state. And before you are about to do that, you should better have a working keyboard.;-)  And maybe then we also advance on the old install.

3.) You have to download the CDs ISO to make the USB install.

4.) Move your currently used keyboard (or another one, if you have one handy) to the computer we are trying to fix. Check the keyboard even before booting by entering into the BIOS. And of course check the plug, if you haven't done it already.

---

### Post by Valkyr333 on 2011-02-28
What I typed in the root shell prompt was ".xsession-errors"

As for the keyboards: they're both laptop computers, so I don't have the option to switch the keyboards. I ended up taking the ailing computer to the store where I bought it for some tech-support. I'm sorry that I didn't see your latest post before I did. They're doing a factory-restore on it, and I'm going to start fresh with Ubuntu and be -much- more careful this time.

I also made sure to ask the guy how I could do such a thing myself if ever I needed to. I was kicking myself ten seconds later when he told me something I already knew about booting in safe-mode. I'm awake, I swear... x.x

When I'm getting started again, I'm going to use the contents of this post to remind me what was the best working option and get that squared away after all the basics are taken care of.

---

### Post by Krytarik on 2011-02-28
Ah, those smart guys.;-)

So, when you get the laptop back, I advise doing the following:
- choose 10.04 again
- do a *real* parallel install this time, meaning by using the CD/USB-flash
- after the installation go straight to "System -> Administration -> Hardware Drivers" to install the proprietary video driver, you may even be prompted before
- or may choose to stick with the nouveau driver if you want to play safe, make sure it is run by checking with "lshw -c video"

---

### Post by Valkyr333 on 2011-03-13
Okay. I'm ready to install, and I've burned the Disc Image File to a CD. I'm being given the advice on this page:

[http://seogadget.co.uk/the-ubuntu-installation-guide/#install-from-CD](http://seogadget.co.uk/the-ubuntu-installation-guide/#install-from-CD)

to run it from the disc in "My Computer." However, Windows doesn't give me the option to run it. My only option seems to be to burn another disc with the same image file when I try to open it. This is a freshly started Windows 7 OS I'm working with, so I figure it's either A: I've burned the disc wrong, or 2: Windows doesn't have the software to open it from CD yet.

What do you think? Obviously CD installation must have benefits over wubi installation, but are they significant enough that it's worth troubleshooting this?

---

### Post by Krytarik on 2011-03-13
Ok, I did not read the complete guide, but it obviously covers both Wubi and CD install.

Did you burn the image, instead of just burning the ISO to the CD? Do you see the various files and directories on the CD? If so, fine. Also see this guide: [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

So, you can't run the installer *inside* Windows, you need to reboot and choose the CD-drive as boot medium via your BIOS options, maybe simply pressing F12 at boot will work.

After doing so, the installer at the CD starts.

Be especially careful when it comes to choosing the partitions, at least for the system, and for swap. You may also choose an extra partition for the home directory, this is handy for later re-installs. The manual partioning may seem a bit tricky at the first time, but it will definitely pay off!

This guide is generally ok:
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
But you should create a swap partition at least of the size of your RAM.
And of course you may have to resize your Windows partition before you can even start following the guide. If so, I recommend doing it with Windows tools before.
Take yourself the time to create/select the partitions!

And yes, a normal, separate CD install is definitely to prefer over the Wubi install. With the Wubi install, Ubuntu is installed *inside* the Windows partition, and if you format the Windows partition, Ubuntu is also lost, also there are often errors when Grub gets updated.

Good luck and don't hesitate to ask questions! When you are in the InstallCD session, you can also establish an internet connection.

---

### Post by Valkyr333 on 2011-03-14
Actually, I burned the ISO to the CD, not knowing there was any difference. I'm going to find something to help me burn the disc-image in Windows 7 because obviously I'm going to need to. Thanks for clearing that up.

Okay, so then Wubi Vs. CD installation means the difference between a legit double-partition setup and including one OS within the other. I'll commit that to memory, I know it'll come in handy, especially when I go to remove Win7 from my Hard Drive. At the moment, though, I'm totally fragged from doing essentially a week's worth of my job in a half a day, which is especially sucky when you work in labor. I don't want to make any careless mistakes out of tiredness, so I'm gonna get on that when I can think straight.

Thanks for your encouragement!

-Val

---

### Post by hotrod6657 on 2011-03-14
I believe if you right click on the .iso image in Windows 7 you will have the option to "burn to disk" which should do what you want.

[http://windowsteamblog.com/windows/b/windowsexperience/archive/2009/04/13/burn-iso-images-natively-in-windows-7.aspx]("http://windowsteamblog.com/windows/b/windowsexperience/archive/2009/04/13/burn-iso-images-natively-in-windows-7.aspx")

There are also a few programs that let you mount iso images on "virtual" CD drives without requiring you burn the image to a real Cd.  This would be fine if you were just testing it out under WUBI.

Hope that helps.

---

### Post by Krytarik on 2011-03-14
> **Valkyr333 said:**
> I don't want to make any careless mistakes out of tiredness, so I'm gonna get on that when I can think straight.

Yeah, better do so. And regarding on how to burn the image, see this guide (included in the "BootFromCD" guide I posted):
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Also, when it comes to installation and you have questions, please start a new thread on those topic.

---

### Post by Valkyr333 on 2011-03-21
Okay, so I've reinstalled Ubuntu using a Live CD. I took your advice to go straight to System>Administration>Hardware Drivers and install the proprietary driver. This had the same result as earlier, in causing the screen to split into two halves which seemed to be on the opposite ends of the screen for where they should be. I rolled back to the generic/default configuration and am currently working through that. The result of lshw -c video was,

```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 310M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff(prefetchable) memory:e0000000-e1ffffff(prefetchable) ioport:d000(size=128) memory:e3000000-e307ffff(prefetchable)

```

Am I reading this correctly, to mean that the Nouveau Driver isn't installed?

*I posted this as a response to the same thread as opposed to opening a new one because it pertained to the original problem which inspired the thread, not because I was ignoring you, just so that you know. If you would still recommend taking it to a new thread, let me know and I will do so.

---

### Post by Krytarik on 2011-03-21
> **Valkyr333 said:**
> 
[/CODE]Am I reading this correctly, to mean that the Nouveau Driver isn't installed?
No, not necessarily, it just states the currently running driver.

Did you remove the proprietary driver again, after you noticed that it doesn't work?

Try to choose the "nouveau" driver with the earlier mentioned command. Then check again those ouput.
> **Valkyr333 said:**
> *I posted this as a response to the same thread as opposed to opening a new one because it pertained to the original problem which inspired the thread, not because I was ignoring you, just so that you know. If you would still recommend taking it to a new thread, let me know and I will do so.
Yeah, it's fine, since it is exactly the same matter, not an installation issue or such.

---

### Post by Valkyr333 on 2011-03-21
"Try to choose the "nouveau" driver with the earlier mentioned command. Then check again those ouput."

Just to be sure, are you referring to

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
as mentioned in response #74 of this thread?

---

### Post by Krytarik on 2011-03-21
Sorry, I didn't want to search yesterday.

You got the right post, but I mean actually the commands you find at the posted link:
[http://ubuntuforums.org/showthread.php?p=9120571](http://ubuntuforums.org/showthread.php?p=9120571)

But upgrading the "nouveau" driver is also a good idea, do it as well. ;-)

---

### Post by Valkyr333 on 2011-03-21
Okay, so I followed his instructions to go to comment #25 about switching from NVIDIA to nouveau, and updated the drivers after that, then rebooted. I realized after this you said the command lines and not the instructions he gives about the previous post, but doing everything up to that point got me to where the reboot takes me to a really screwed up version of the Gnome login screen which is a mish-mosh of purples, whites and seaweed greens. I obviously can't do anything from there, so is there something I can do before the login screen is reached that would allow me to roll it back to the last stable configuration?

Edit: Nevermind that. I remembered to boot it with the Live CD. (duh...) Now I can get back in, I need to know what to do from there. Would I just follow the originally intended instructions, or is there something else that should be done from here?

---

### Post by Krytarik on 2011-03-21
Actually I meant running those commands, and choosing the "nouveau" driver in between:
```
sudo update-alternatives --config gl_conf
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```Also, make sure that "nouveau" is not blacklisted.

When you are at the login screen now, can you press Ctrl+Alt+F1 to switch to a console?
And even see something? If so, run
```
lshw -c video
```to check if the "nouveau" driver is now running.

---

### Post by Valkyr333 on 2011-03-21
I've gotten into the Desktop using the Live CD's "Try Ubuntu" option. The results of lshw -c video appear to be the same, except for
```

configuration: driver=nouveau latency=0
```

---

### Post by Krytarik on 2011-03-21
Running those command from a LiveCD reflects *its* state, not that of your installed system.

How about my original question?

---

### Post by Valkyr333 on 2011-03-21
CTRL+ALT+F1 at the messy login screen takes me to a mostly black screen with a rapidly-flashing "underscore" looking thing at the top left. I can't seem to enter any characters or affect any change in the screen at all from this position.

---

### Post by Krytarik on 2011-03-21
> **Krytarik said:**
> 
Did you remove the proprietary driver again, after you noticed that it doesn't work?

If not, do it now, boot into "recovery mode" therefore.
Also, after doing so, check if the nouveau driver is blacklisted.

---

### Post by Valkyr333 on 2011-03-21
I did make sure I removed the Proprietary Driver, I did so the first time you asked that.

Okay, booted in recovery mode. What is the command to check the blacklist/non-blacklist status of the nouveau driver?

---

### Post by Krytarik on 2011-03-21
Then give the proprietary driver another try, this time with the one provided by Xorg-Edgers' PPA you added earlier.

- boot into "recovery mode"
- install the offered proprietary driver via "Hardware Drivers"

---

### Post by Valkyr333 on 2011-03-21
"lshw -c video" currently returns the same results as it did before, when it comes to "configuration" it's still "driver=nouveau latency=0"

^Adding this bit because you'd asked for the results of it before and I didn't know how to give it to you.

*Update - Wait, I just noticed that the proprietary driver from before is still installed, just currently deactivated. Should I just re-activate it, or does this potentially change a lot/everything? By my recollection, the proprietary driver has never worked properly with this computer and the way Desktop Effects were most functional before was with another one, I think it was the nouveau (which would explain why you said I might want to play it safe by sticking with that one before). Of course, you know better than I at all this. I guess I'm just a bit confused about it.

---

### Post by Valkyr333 on 2011-03-21
For the Xorg Edgers Driver, does [this]("https://help.ubuntu.com/community/RadeonHD") give accurate/safe instructions? I found it browsing around trying to learn more about the topic.

---

### Post by Krytarik on 2011-03-21
> **Valkyr333 said:**
> "lshw -c video" currently returns the same results as it did before, when it comes to "configuration" it's still "driver=nouveau latency=0"
Actually I'm wondering how that is possible in "recovery mode".
^Adding this bit because you'd asked for the results of it before and I didn't know how to give it to you.
> **Valkyr333 said:**
> By my recollection, the proprietary driver has never worked properly with this computer and the way Desktop Effects were most functional before was with another one, I think it was the nouveau (which would explain why you said I might want to play it safe by sticking with that one before). Of course, you know better than I at all this. I guess I'm just a bit confused about it.
Yeah, but since you have already chosen to try that way, and it messed it again, we can also try at least the most recent version right now.

I believe you did already upgrade those alongside upgrading the nouveau driver, but just to make sure```

sudo apt-get update
sudo apt-get upgrade
```
And this one to set up a respective xorg.conf:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```

---

### Post by Krytarik on 2011-03-21
> **Valkyr333 said:**
> For the Xorg Edgers Driver, does [this]("https://help.ubuntu.com/community/RadeonHD") give accurate/safe instructions? I found it browsing around trying to learn more about the topic.
Those guide covers the old "radeonhd" driver, for ATI/AMD cards/chips.

---

### Post by Valkyr333 on 2011-03-21
Okay. I got as far as "sudo apt-get upgrade" in that list. It says at the end,

```
The following packages have been kept back:
libcairo2 libgl1-mesa-glx xserver-xorg-video-intel
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```Does this mean there's a hangup, or should I continue by entering 

sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate

*I opened it up in recovery mode by holding shift as the computer booted. When I was given the option, I logged in with "low-graphics mode." Should I have done something differently?

---

### Post by Valkyr333 on 2011-03-21
> **Krytarik said:**
> Those guide covers the old "radeonhd" driver, for ATI/AMD cards/chips.

I probably should've recognized that. I think I'm getting to the "too groggy for the involved stuff" point. Maybe I should just call it a night and work on it tomorrow.

---

### Post by Krytarik on 2011-03-21
> **Valkyr333 said:**
> Okay. I got as far as "sudo apt-get upgrade" in that list. It says at the end,
```
The following packages have been kept back:
libcairo2 libgl1-mesa-glx xserver-xorg-video-intel
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```Does this mean there's a hangup, or should I continue by entering 

Then try upgrading via "Synaptic".
> **Valkyr333 said:**
> *I opened it up in recovery mode by holding shift as the computer booted. When I was given the option, I logged in with "low-graphics mode." Should I have done something differently?
No, it's just fine, I just thought that the "vesa" driver comes into use then, or at least "nv".

---

### Post by Krytarik on 2011-03-21
> **Valkyr333 said:**
> Maybe I should just call it a night and work on it tomorrow.
"Done when you are." ;-)

---

### Post by Valkyr333 on 2011-03-21
> **Krytarik said:**
> Then try upgrading via "Synaptic".

Okay. When I come back, what should I enter into the search field/what packages should I install in Synaptic?

Thanks again,

-Val

---

### Post by Krytarik on 2011-03-21
> **Valkyr333 said:**
> Okay. When I come back, what should I enter into the search field/what packages should I install in Synaptic?

Just click the items at the toolbar in that order:
- "Reload"
- "Mark All Upgrades"
- "Apply"
Then simply confirm.

---

### Post by Valkyr333 on 2011-03-22
Okay, I tried that. The results of a normal login attempt are the same. I'm gonna log it back in in low-graphics mode, but I'll wait to hear from you or anyone else with more expertise before I go fiddling with things.

---

### Post by Krytarik on 2011-03-22
Then, after logging into low-graphics-mode, disable/remove the proprietary driver via "Hardware Drivers". Make sure that there remains no "/etc/X11/xorg.conf" after that.

---

### Post by Valkyr333 on 2011-03-22
There seems to be no option in "Hardware Drivers" to -remove- the Proprietary Driver, now that I look at it. It just gives you the option to activate or deactivate it, and of course it's currently deactivated.

---

### Post by Krytarik on 2011-03-22
Then let's give the proprietary driver another try, I didn't mind that you disabled it before:
- activate it there
- run those command afterwards, just to make sure:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```

---

### Post by Valkyr333 on 2011-03-22
Okay, I'll do that. First, though, I think I should ask how I make sure there's no /etc/X11/xorg.conf? Is it just a matter of digging around in the folder where it would be stored?

---

### Post by Krytarik on 2011-03-22
If you plan to run the proprietary driver, you need a xorg.conf in any case, properly configured with the previously stated command.

If you don't want to run the proprietary driver, you don't necessarily need a xorg.conf.

It is stored in "/etc/X11", you need root access to rename/delete/modify it.
For example, to rename it:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup-22.03.2011
```
**EDIT:** Forgot to mention: The xorg.conf specifies the video driver and its options, among other things. So, if you want to use another driver as specified by it, you have either to modify it, remove it (to set the driver to the default one), or restore a backup of it.

---

### Post by Valkyr333 on 2011-03-22
Alright. Using the --force-generate command, I got

```
Invalid commandline, please run 'nvidia-xconfig --help' for usage information.
```

However, the other command (to rename it) returns "No such file or directory," so I gather the file was removed by an earlier process.

---

### Post by Krytarik on 2011-03-22
Sure that you didn't enter the command incorrectly? I just yet re-checked it:
[http://manpages.ubuntu.com/manpages/lucid/en/man1/nvidia-xconfig.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/nvidia-xconfig.1.html)

Also, please post the output of:
```
ls -al /etc/X11/xorg.conf*
```

---

### Post by Valkyr333 on 2011-03-22
Just re-typed/re-tried the command, and I guess either I did mistype it or something changed while I was out. It worked this time.

The output of ls -al /etc/X11/xorg.conf is,

-rw-r--r-- 1 root root 1420 2011-03-22 14:45 /etc/X11/xorg.conf.

---

### Post by Krytarik on 2011-03-22
> **Valkyr333 said:**
> 
The output of ls -al /etc/X11/xorg.conf is,

-rw-r--r-- 1 root root 1420 2011-03-22 14:45 /etc/X11/xorg.conf.
Note the "*" at the end of "ls -al /etc/X11/xorg.conf*". I want to check if there are any backup files.

Please reboot now, to see if the proprietary driver works now.

---

### Post by Valkyr333 on 2011-03-22
Okay, so I'm back to a state previous to the messed up login screen. Login screen looks and works fine at this point. Also, Desktop Effects are enabled and there seems to be no problem with that. Something I do notice is that on login, the "Ubuntu" logo looked sharper with the previous graphics driver that gave me the messy/unusable login screen, whereas this driver enables better/working general graphics, but the Ubuntu logo looks sloppier. Now, this alone isn't a big enough deal to me to make it worth screwing around more, but I wonder if you think it's a sign of anything potentially worth worrying about? If not, I'll just mark this thread as solved.

---

### Post by Krytarik on 2011-03-22
Cool that the proprietary driver seems to finally work! Those should yield the best possible performance.

I guess you mean the boot splash? Maybe it's a different screen resolution?

---

### Post by Valkyr333 on 2011-03-22
Maybe. That probably means it's not worth worrying about, then?

---

### Post by Krytarik on 2011-03-22
> **Valkyr333 said:**
> Maybe. That probably means it's not worth worrying about, then?
Yeah right, as long as there are no issues at the desktop.

---

### Post by Valkyr333 on 2011-03-22
Okay, then! Thank you -so- much for all your hard work and patience helping me resolve this. =)

All the best,

-Val

---

### Post by Krytarik on 2011-03-22
You're welcome! So long! ;)

---

