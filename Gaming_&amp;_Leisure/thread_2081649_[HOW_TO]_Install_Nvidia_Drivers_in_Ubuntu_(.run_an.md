---
title: "[HOW TO] Install Nvidia Drivers in Ubuntu (.run and Ubuntu Provided)"
date: 2012-11-07
forum: Gaming &amp; Leisure
---

### Post by Dlambert on 2012-11-07
[FONT=Arial]

[B]Due to the large number of Install guides, all with different methods I decided to make one central guide with the methods that worked for me. This guide will Cover installing the Ubuntu provided drivers and also the binary drivers from Nvidia itself.

[/B]  
[/FONT][CENTER][FONT=Arial][SIZE=3]_**FOR UBUNTU PROVIDED DRIVERS**_[/SIZE][/FONT][FONT=Arial]
[/FONT][/CENTER]
       [FONT=Arial]

[B]To install Ubuntu provided Nvidia drivers ( If the sources "additional drivers" didn't work for you either):
[/B]
**1)** **Ctrl-Alt-F1 and login as your username**

[SIZE=2]**2)** [/SIZE][/FONT]   [FONT=Arial]

```
sudo apt-get install linux-source 
```[/FONT]

[FONT=Arial]**and headers** 

```
sudo apt-get install linux-headers-generic
```[/FONT]  [FONT=Arial]**3) [SIZE=2]Uninstall nvidia driver - this depends on which version you tried to install from additional drivers :[/SIZE]**

```
sudo apt-get remove nvidia-current
``````
sudo apt-get remove nvidia-current-updates
```[/FONT]```
  [FONT=Arial]
sudo apt-get remove nvidia-experimental-304 
[/FONT]
```[FONT=Arial][B]

4)[/B] **_NOTE:_** **You can install "nvidia-current" "nvidia-current-updates" or "nvidia-experimental-304" **

```
sudo apt-get install nvidia-current-updates
```[/FONT] [FONT=Arial][B]

5)[/B] 

```
sudo shutdown -r now
```**That should get the nvidia drivers of your choice working. **[/FONT][FONT=Arial]

[/FONT]   [CENTER][FONT=Arial][SIZE=3]_**FOR BINARY DRIVERS**_[/SIZE][/FONT][FONT=Arial]
[/FONT] [/CENTER]
[FONT=Arial][B]





I recommend that rather than installing the experimental branch of drivers, that you just go ahead and install the binary drivers from Nvidia.[/B]

[U][B]

At your own Risk![/B][/U][/FONT]   [FONT=Arial]

[B]

To Install Binary Drivers from Nvidia[/B][/FONT]   [FONT=Arial] [B](This is what worked for me):

[U]



This guide assumes you have the above Nvidia drivers working, if not skip step 1.[/U][/B] 


[/FONT][FONT=Arial][SIZE=3]_**But I believe you will still need to install the headers outlined in the above guide. ^^^ Step [SIZE=3]2[/SIZE]**_[/SIZE]

[B]

0)[/B][/FONT]   [FONT=Arial] **_Download the drivers from Nvidia depending on your card, and place the .run on your desktop. Right click and go into properties and find "Allow executing as a program" and click it._** 

[http://www.geforce.com](http://www.geforce.com)[/FONT]   [FONT=Arial]

**1) _NOTE:_**[/FONT][FONT=Arial]** Depends on which version you currently had above (nvidia-current-updates" or example)**

 [U][B]THIS STEP IS ONLY FOR USERS WITH NVIDIA DRIVERS ALREADY INSTALLED.

[/B][/U]** If not, please skip step 1. **

[/FONT]```
  [FONT=Arial]
[COLOR=#333333][COLOR=#333333]sudo apt-get purge nvidia-current nvidia-settings[/COLOR]
[/COLOR][/FONT]
``` [FONT=Arial][B]

2) [/B]```
[COLOR=#333333]sudo service lightdm stop[/COLOR]
```[B]

3) [COLOR=#333333]ctrl-alt-f1[/COLOR][/B]

[COLOR=#333333]**4)** **Login**[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333]**5)** **Then switch to the directory where your drivers are (I put mine on my Desktop)**[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333]```
[COLOR=#333333]cd Desktop[/COLOR]
```[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333]**6)** **Then install the driver:**[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333]```
[COLOR=#333333]sudo ./N[/COLOR]
``` **Then hit tab and Ubuntu will automatically fill in the exact driver name so you don't have to type out the long name. (Granted you don't have another N-titled launcher)**[/COLOR][/FONT][FONT=Arial]

[COLOR=#333333]**7)** **Follow the prompts and install the driver.**[/COLOR]

[COLOR=#333333]:confused: _**If you get an issue with Nouveau (like I did at first) **_[/COLOR]     

[COLOR=#333333]```
[COLOR=#000000]sudo apt-get --purge remove xserver-xorg-video-nouveau[/COLOR]
```[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333]**9) Then reinstall the driver (If you can) and if even if you cannot, run:**[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333]```
[COLOR=#000000]sudo update-initramfs -u[/COLOR]
``` **and reboot.**[/COLOR][/FONT]      [FONT=Arial]

[B][COLOR=#333333]You should now have a _*working*_ Nvidia driver without messing with black lists and Nouveau drama. 

Closing thoughts: Please take note that with every kernel you will have to reinstall the Nvidia drivers of your choice if and only if you installed the .run file. 

Thank you for your time, and please let me know if this guide can be improved, or it didn't work for you. Both of which I will try to correct, thank you. -Dlambert
[/COLOR] [/B] 
**[COLOR=#333333]Sources:[/COLOR]**   

[COLOR=#333333][http://askubuntu.com/questions/202574/desktop-does-not-show-when-i-installed-nvidia-drivers](http://askubuntu.com/questions/202574/desktop-does-not-show-when-i-installed-nvidia-drivers)[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333][https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333][http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu](http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu)[/COLOR][/FONT]   [FONT=Arial]

[COLOR=#333333][http://askubuntu.com/questions/203429/how-to-install-nvidia-driver-in-ubuntu-12-10](http://askubuntu.com/questions/203429/how-to-install-nvidia-driver-in-ubuntu-12-10)[/COLOR][/FONT]

---

### Post by drmrgd on 2012-11-07
Very nice!  Thank you for this.  I agree there's a ton of different guides out there, and I think this is an issue that is going to come up even more often than it already does given the buzz with the new Nvidia drivers out now.

---

### Post by Dlambert on 2012-11-07
> **drmrgd said:**
> Very nice!  Thank you for this.  I agree there's a ton of different guides out there, and I think this is an issue that is going to come up even more often than it already does given the buzz with the new Nvidia drivers out now.
You're welcome! That's exactly why I made this. I wanted to install the new drivers. And every guide involved blacklisting nouveau with mixed success.So i compiled the steps it took me to get it working without blacklisting. I am now enjoying better performance brought from the new drivers.  :)

---

### Post by Dlambert on 2012-11-07
Updated to fix typos, the font issue, and overall flow of the guide. Enjoy!

---

### Post by holastickboy on 2012-11-07
Excellent guide, and thanks for posting!  I have no idea what Canonical was doing with Ubuntu 12.10, so many issues with video cards (not just Nvidia too, but the Catalyst drivers were horrible to install as well).  After my install, I still had problems (have a dual screen setup), but all was fixed after downgrading to 12.04. I hate regression!

---

### Post by Dlambert on 2012-11-07
No problem! But I'm glad jockey is gone.

---

### Post by billatub on 2012-11-10
Thank you for this. The large number of (often wrong, outdated or incomplete) guides spattered all over hyperspace lead to much frustration.

Might I ask an awkward question?

(How) can one get a change of driver to work when using a live dvd?
That re-boot step rather messes things up for a live user. 
Would restart X be enough?

Plus I tend to find that if I apply too much update in a live setting, swap does not comply; the live fs just fills up until it won't work any more. I confess I haven't tried your method yet, my own attempts having failed  so often before.

Alternatively, is there a way to install an nVidia driver permanently on a machine, and direct the boot from live dvd to pick up that version?

---

### Post by Dlambert on 2012-11-10
I honestly don't know about the live dvd thing. I would say no. Because the nvidia driver is built into the kernel. Your best bet would to run a os that builds in the proprietary drivers like sabayon. Manjaro linux or pc linux os. To name a few

---

### Post by MadMadness on 2012-11-30
Thank you very much for these instructions.  I was able to follow them to successfully install the latest nvidia linux drivers.  I do have a question, however;  Should the Nvidia X Control Settings still work with the native drivers?  The Nvidia control panel no longer worked for me after the native drivers were installed.

---

### Post by Dlambert on 2012-11-30
> **MadMadness said:**
> Thank you very much for these instructions.  I was able to follow them to successfully install the latest nvidia linux drivers.  I do have a question, however;  Should the Nvidia X Control Settings still work with the native drivers?  The Nvidia control panel no longer worked for me after the native drivers were installed.


Just reinstall the nvidia-settings:

```
sudo apt-get install nvidia-settings
```

But otherwise the settings should work, as you don't need to reinstall the cp with every new driver.

---

### Post by btocb on 2013-02-03
Thank you very much!

This works perfectly! I was kinda frustrated because there have been passed two days since I started my new fresh Ubuntu installation and I hadn´t been able to sort things out.

Thank you man, this was very useful :D

---

### Post by Derviansoul on 2013-02-24
Thank you so much your tutorial worked for me(i used the binary version since the ubuntu one is a few months behind).


Quick note, compiz broke everytime i tried to do this after installing nvidia-current or nvidia-current-updates from package manager.

Does anyone know hot to update the binaries file? or do we just run it again (sorry about the stupid question but i have been using windows for a few years now, all my linux knowledge is in deep sleep).

UPDATE:
Using Nvidia 310.32 drivers with the updated kernel 3.5.0-25-generic doesnt allow me to go past the login screen i suspect i broke compiz again:S.
UPDATE2: Installing the drivers again done the deed again.

Thanks

Ricardo

---

### Post by khat33b on 2013-03-17
I have a fresh installation of Ubuntu 12.10.When I tried to install nvidia drivers the following errors occurred. Please help.
Can I use Nvidia drivers with Unity?

```
khat33b@Oa:~$ sudo apt-get install nvidia-current-updates
[sudo] password for khat33b: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current-updates
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/67.7 MB of archives.
After this operation, 204 MB of additional disk space will be used.
Selecting previously unselected package nvidia-current-updates.
(Reading database ... 155992 files and directories currently installed.)
Unpacking nvidia-current-updates (from .../nvidia-current-updates_304.51-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current-updates (304.51-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current-updates/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-current-updates/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current-updates
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Dell Inc. with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Inspiron N5110 with Latitude E6530
DEBUG:Quirk doesn't match
Loading new nvidia-current-updates-304.51 DKMS files...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
```

I have Dell Inspiron N5110, RAM 3.8GB, Processor Intel® Core™ i5-2430M CPU @ 2.40GHz × 4, Graphics is shown Unknown, 64bit OS.

The result of ```
lspci |grep VGA
``` is:
```
khat33b@Oa:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
```

---

### Post by yorgmeister on 2013-04-05
Your install crashed my system, it became very unstable and kept freezing for about a minute and a half after each input. took over an hour to get the terminal open and type in the command to uninstall. I'm still getting error reports and compiz crashed but I seem to be able to use my system again. What happened? And how do I fix it without re-installing everything?

---

### Post by tad1073 on 2013-04-05
> **Dlambert said:**
> [FONT=Arial]

[B]Due to the large number of Install guides, all with different methods I decided to make one central guide with the methods that worked for me. This guide will Cover installing the Ubuntu provided drivers and also the binary drivers from Nvidia itself.

[/B]  
[/FONT][CENTER][FONT=Arial][SIZE=3]_**FOR UBUNTU PROVIDED DRIVERS**_[/SIZE][/FONT][FONT=Arial]
[/FONT][/CENTER]
       [FONT=Arial]

[B]To install Ubuntu provided Nvidia drivers ( If the sources "additional drivers" didn't work for you either):
[/B]
**1)** **Ctrl-Alt-F1 and login as your username**

[SIZE=2]**2)** [/SIZE][/FONT]   [FONT=Arial]

```
sudo apt-get install linux-source 
```[/FONT]

[FONT=Arial]**and headers** 

```
sudo apt-get install linux-headers-generic
```[/FONT]  [FONT=Arial]**3) [SIZE=2]Uninstall nvidia driver - this depends on which version you tried to install from additional drivers :[/SIZE]**

```
sudo apt-get remove nvidia-current
``````
sudo apt-get remove nvidia-current-updates
```[/FONT]```
  [FONT=Arial]
sudo apt-get remove nvidia-experimental-304 
[/FONT]
```[FONT=Arial][B]

4)[/B] **_NOTE:_** **You can install "nvidia-current" "nvidia-current-updates" or "nvidia-experimental-304" **

```
sudo apt-get install nvidia-current-updates
```[/FONT] [FONT=Arial][B]

5)[/B] 

```
sudo shutdown -r now
```**That should get the nvidia drivers of your choice working. **[/FONT][FONT=Arial][/FONT][FONT=Arial][/FONT]

Don't forget to do:
```
sudo nvidia-xconfig
```
before shutting down.

---

### Post by Hexxus on 2013-04-05
Quick question, my rig is an Alienware M17X R4 with the intel integrated on the 3610QM and I have a Nvidia GTX 660... right now it's not utilizing my Nvidia graphics chip at all, but if I follow this, can I expect it to act like windows and change between the two chips on the fly?

Thanks!

---

### Post by Crossbow on 2013-04-07
N00B here. Can you advise me? 

Got this far:

```
sudo service lightdm stop # to shut down the Xserver
```

Now I've got the message, "Starting Timidity++ ALSA midi emulation" and [OK]... then nothing.  I can't type anything in. Am I waiting for something?

PS. Tried rebooting and starting over, same thing happened.

---

### Post by arodulfo on 2013-05-12
@Dlambert: I tried to follow your recommendations as closely as psossible.

First approach suggested, using XUbuntu 12.10 provided driver, didn't work.
I ended with a 640x480 display resolution in my brand new laptop 1600x900 maximum display resolution.

Then, I tried NVidia-provided driver (319.17 these days). Same ending: low-res 640x480 display with no alternate options in "Settings Manager" => Display => Resolution.

Two remarks here: first of all, when installing the NVidia provided driver with its .run installer, it always says "The distribution-provided pre-install script failed! Continue installation anyway?" and I always hit Yes.

On the other hand, once the installer seems to have done its job, i use dmesg to see how things are going. This is what I get when looking for nvidia-related dmesg entries:

```

[   12.922578] nvidia: module license 'NVIDIA' taints kernel.
[   12.927568] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   12.927580] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   12.927594] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[   12.922578] nvidia: module license 'NVIDIA' taints kernel.
[   12.927709] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.17  Thu Apr 25 22:45:49 PDT 2013

```

lspci answer is:

```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de3 (rev a1)

```

I did a fresh install and the laptop has just the os itself. The system is based on i7, has 16 GB of SDRAM and an NVidia GeForce GT635M.

I am supposed to use 3D graphics in my work but the system refuses to cooperate. 
What do you suggest me to try now?

Thanks a lot in advance.
Kind regards,

---

### Post by Lightning Dragon on 2013-05-13
Hi,

I am unsure of the driver you are to use, but did you make sure you purged before you tried to install your GPU's driver? Would you be willing to try my instructions at installing? I had the same issues as you and it took me eleven fresh installs to finally get it down right. If you are willing, please see this post and switch out my driver with your driver. I know you said you get errors with the .run files, but I want to see if the below instructions make it so you do not get those errors while installing.

[http://ubuntuforums.org/showthread.php?t=1743535&p=12639552#post12639552](http://ubuntuforums.org/showthread.php?t=1743535&p=12639552#post12639552)

If not mine, have you see this thread yet? 

[http://ubuntuforums.org/showthread.php?t=2006716](http://ubuntuforums.org/showthread.php?t=2006716)

---

### Post by Brendon77 on 2013-07-13
This card is in your system Ge6150 SE graphics card. If this card is not your system, you should upgrade.

---

### Post by oldrocker99 on 2013-07-14
I will append to the excellent instructions given here:

Step 0: sudo apt-get install dkms

This way, you won't need to reinstall the nVidia .run drivers every time a kernel update occurs; it will be taken care of at the time of the kernel update.

---

### Post by nomi416 on 2013-09-29
I am completely new to Ubuntu. I installed ubuntu 13.04 recently. I installed nvidia drivers as you explained in STEP 1. But when i rebooted, launcher and panel were missing. Then i had to use
"sudo apt-get purge nvidia*" and
Reset unity:
dconf reset -f /org/compiz/
unity --reset-icons
can you please suggest what should I do? does it has to do anything with [FONT=Arial][COLOR=#333333]_**Nouveau**_[/COLOR][/FONT]

---

### Post by pwabrahams on 2014-03-18
Nice guide -- but it doesn't solve my first problem: when I boot a new 13.10 system for the first time, it soon hangs on a screen of graphics gibberish.  I never have the opportunity to get to a virtual console -- Alt-Ctl-F1 does nothing (and CapsLock is dead also).  This happens during the display of that blue screen with four icons.

---

### Post by matiche on 2014-06-21
just going to  put this here use it love it pass it on helps needing a updated list of xserver and nvidia xserver 

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

": xorg"  put together it put a stupid smiley emote for the :

---

### Post by aramil248 on 2014-06-22
whats better to use the repo drivers or the ones fron nvidia.com?

---

### Post by mudpie73 on 2014-07-01
I followed instructions in post 1. I also tried installing via "Additional drivers". It doesn't seem to work within tht session. And both times when I reboot, the computer stalls with a flashing cursor in the top left of screen.
The ubuntu driver works for some things e.g. Netflix runs fine. BUt playing videos or watching world cup on cbc is no go, have to minimise window size and the it's not choppy.

I have a Sony Vaio VGN FE41Z, running nvidia G 7600 card.  HELP very much appreciated. I will post anything else you may need, I'm a beginner BTW..you may have noticed already.

---

