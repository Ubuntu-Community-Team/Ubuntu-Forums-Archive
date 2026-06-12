---
title: "ATI Graphics Card"
date: 2008-04-15
forum: Gaming &amp; Leisure
---

### Post by Commander Bosko on 2008-04-15
Every 3d game I try to run just goes nuts with the textures, to the point where its unplayable. Is there any way to get games even the slightest bit playable?

---

### Post by Commander Bosko on 2008-04-15
Here is a screenshot of Urban Terror.

[IMG]http://i14.photobucket.com/albums/a308/CommanderBosko/Screenshot-ioUrbanTerror.png[/IMG]

That's how bad it is.

---

### Post by acoustibop on 2008-04-15
If it happens only in certain games, Commander Bosko, and happens immediately you start the game, it may well be game specific, so we need to know which games this happens with and with which it doesn't.

If it happens more or less randomly, it's most likely the card overheating - this can be exacerbated by the card's having been handled and installed without proper antistatic precautions.  It could also be something else in your system, eg your CPU, overheating.

**Edit:** what card is it, and what driver are you using with it?

---

### Post by Commander Bosko on 2008-04-15
Thanks for the reply :)

It happens with every 3d game I try to play, the card itself is fine because every game works great in Windows.  I have tried to play Guild Wars, Warcraft III, Urban Terror, and Nexuis.  The only game that I can see properly is Warcraft III, I'm guessing because it's not too graphicly stressful... However the game will randomly crash.

Also I'll add that Guild Wars/Warcraft III were both run with the latest version of wine, while Urban Terror/Nexuis were both run using only Linux (being Linux based games).

My card is the RV380 [Radeon X600 (PCIE)], I don't know how to figure what driver I'm using with it.

---

### Post by Tomatz on 2008-04-15
You need to disable compiz when playing 3d games.

To do this type in a terminal:

```
metacity --replace
```

---

### Post by Commander Bosko on 2008-04-15
I entered that in a terminal, I don't really know what it did or what I was supposed to do with it.  I left the terminal open and attempted to run Urban Terror again, it made little difference in quality.

---

### Post by Perfect Storm on 2008-04-16
The command replaces the 3D decoration with a 2D decoration of the Desktop. Why? Because sometimes it interfere with the game(s). All the 3D eyecandy is "new" and there may be bugs etc. - also older games aren't build for it.

As far as I know (I'm a nvidia user not ATI), there's two diffrent kind of drivers. One of them are good to do all the 3D eyecandy stuff the other good with games (correct me if I'm wrong, that's what I've heard). 
You might want to try Envy to get the latest driver (a quick search in our forum should do it).

---

### Post by SandmanXC on 2008-04-16
I have the exact same problem. I have an ATI Radeon x1100 card. I believe the problem is related to the fgrlx driver.

---

### Post by Saint Angeles on 2008-04-16
did you get the latest fglrx (8.3?) from the ati website?

i'm using it with hardy heron and it works really really good.

---

### Post by Commander Bosko on 2008-04-16
It says I have to install it as the super user, how do I do that?

---

### Post by Perfect Storm on 2008-04-16
use the command **sudo** infront.

eg.
sudo <command you want to execute>

---

### Post by Commander Bosko on 2008-04-16
I installed envy, installed my driver, and now I'm even worse off.  I'm getting this code
```
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  495
  Current serial number in output stream:  496
```

Every game crashes before anything happens, now I'm totally lost :confused:

---

### Post by Commander Bosko on 2008-04-16
Bump

---

### Post by Tomatz on 2008-04-17
You will still need to disable compiz to play games with the new drivers:

```
metacity --replace
```

Hopefully thats the problem.

;)

---

### Post by Commander Bosko on 2008-04-17
Nah it's not working, even linux itself is running slow.  Maybe I'm just doomed to never play games on linux.

---

### Post by Tomatz on 2008-04-17
maybe try installing the new ati drivers (they are probably newer than the ones envy uses). I heard that they fixed a few issues on hardy.

**Do this to make sure you remove the original driver completely**

```
sudo apt-get remove xorg-driver-fglrx
```

**Then download the driver:**

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

**Then to install do this:**

> Taken from [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

**_[COLOR="Red"]You will have to adjust filenames accordingly for the driver you downloaded[/COLOR]_**

Method 2: Install the Catalyst 8.3 Driver Manually

[B]sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms[/B]

If using 64bit make sure to collect package "ia32-libs" before you continue!

Create .deb packages:

**Open a terminal in the same directory as the driver (put the driver in home and open a terminal).**

**sudo sh ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy**

note: if this step fails with a signal being caught, and you are running the script on an NFS-mounted directory, copy it to a local partition, and it will work. The same error may result from insufficient disk space.

As an alternative, you can just use

sudo ./ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu --autopkg

which will download all the needed packages by itself and also automatically detects the Ubuntu version used.

If this step fails on amd64/x86_64 with a No such file or directory message about missing files in X11R6/lib, follow these instructions and come back here. Also check that your download path does not contain spaces.

Blacklist old fglrx module from linux-restricted-modules:

As Ubuntu Gutsy's linux-restricted-modules package includes the fglrx module from an old driver version (8.37.6), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

Ubuntu/Gnome users type in:

**gksu gedit /etc/default/linux-restricted-modules-common**

Kubuntu/KDE users type in:

kdesu kate /etc/default/linux-restricted-modules-common

[B]Add "fglrx" to the line "DISABLED_MODULES"
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"[/B]

Please note that after the modification above, the "Restricted Driver Manager" will signal "ATI accelerated graphics driver" not enabled (unticked). This is perfectly correct. At the end of the installation procedure it will signal in Status: "in use" (green light), but NOT enabled. It simply means that the fglrx module contained in the linux-restricted-modules package is not enabled, but another fglrx module (8.3) is in use.

You may also need to edit the file (if it exists):

**gksu gedit /etc/modprobe.d/blacklist-restricted**

**Put a # in front of the line "blacklist fglrx", if it is present. Otherwise, the kernel module will not load automatically, and you will not get 3D acceleration.**

Remove any old fglrx debs from /usr/src/:

**sudo rm /usr/src/fglrx-kernel*.deb**

**Install .deb packages:**

**sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb**

[I]Additional 64-bit instructions

If you have a 64 bit install, the above dpkg command will likely complain that "Errors were encountered while processing: fglrx-amdcccle". This is because of a dependency of the amdccle package on 32 bit libraries. If you receive this error, issue the following command after the above dpkg command, which will force the installation of all of the 32 bit dependencies, and then the amdccle package:

sudo apt-get install -f

Catalyst 8.3 on 64-bit systems requires the --force-overwrite command in the above dpkg command:

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb[/I]


Hopefully that will install the drivers correctly. I have put what you need to do in bold. ;)

---

### Post by Commander Bosko on 2008-04-17
Thanks alot Tomatz! However, I don't want to screw it up on the last part, I have this from the terminal.
```
Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? 

```
Which do I pick?

---

### Post by Tomatz on 2008-04-17
I would go with:

**Y**

But don't shout at me if it borks LOL

Doing N will keep your original compiz-manager file if in doubt to backup your original:

```
sudo cp /etc/xdg/compiz/compiz-manager ~/Desktop
```

;)

---

### Post by Commander Bosko on 2008-04-17
Meh, it's impossible, its now the worst it's ever been, every step is backwards... hers the update

[IMG]http://i14.photobucket.com/albums/a308/CommanderBosko/Screenshot.png[/IMG]

---

### Post by Tomatz on 2008-04-17
Bummer.

Sorry that didn't work mate :(

I'm stumped other than getting an nVidia i really don't know where to go from here.

---

### Post by Commander Bosko on 2008-04-17
Np, I appreciate all your help.  I guess from now on I will be getting nVidia cards from now on.

---

### Post by Tomatz on 2008-04-17
> **Commander Bosko said:**
> Np, I appreciate all your help.  I guess from now on I will be getting nVidia cards from now on.

Yeah its the way to go with linux. They work pretty much perfect "out of the box".

P.s i noticed from your screenshot that you were running a game in wine. Have you tried a native linux game like open arena (open source quake 3 arena)? As the problem could be wine.

To install open arena:

```
sudo apt-get install openarena openarena-data
```

---

### Post by SandmanXC on 2008-04-18
Nah, it doesn't work with open arena either. I have the *exact* same problem. Let's just hope hardy will fix it. Not too plausable though.

---

### Post by Commander Bosko on 2008-04-18
Yeah the reason it was a wine game, is because if I tried running a linux game it would be full screen.  Thus impossible to take a screenshot because I can't see anything.

---

### Post by Tomatz on 2008-04-18
Do you have xserver-xgl running?

Check in system monitor.

If so in a terminal:

```
sudo apt-get remove xserver-xgl
```

Reboot

If you have any problem with compiz just reinstall it.

---

### Post by Commander Bosko on 2008-04-18
ATI is dead to me... I'll just have to hold off my linux gaming till I get a nVidia card.

---

### Post by oldjimsteele on 2008-04-26
I used to have that problem, it looked exactly like your screenshot in post #2.  I was running 7.10, ATI card, with compiz working fine.  i had to enter the command posted above, log out, and log back in:
sudo apt-get remove xserver-xgl
The result is no more compiz, however, 3D rendering in games or google earth works perfectly.  I don't know if previous commands you've entered would get in the way, but that command did the trick.

---

### Post by oldjimsteele on 2008-04-26
I used to have that problem, it looked exactly like your screenshot in post #2.  I was running 7.10, ATI card, with compiz working fine.  i had to enter the command posted above, log out, and log back in:
sudo apt-get remove xserver-xgl
The result is no more compiz, however, 3D rendering in games or google earth works perfectly.  I don't know if previous commands you've entered would get in the way, but that command did the trick.

---

### Post by SandmanXC on 2008-04-27
Well, okay, but this still isn't a solution. If installed correctly, the ati driver should have the 'Composite' extension, which allows compiz without xgl. That's the actual problem.

---

### Post by Melcar on 2008-04-27
First uninstall all the driver bits you may have in your system.  How to uninstall will depend on how you attempted to install them.  Then reconfigure your xserver to start off with a fresh xorg.conf:

```
sudo dpkg-reconfigure xserver-xorg
```

Chose vesa as the graphics driver, and just accept the default options for the rest.  Reboot (or just restart X with ctrl+alt+backspace).  Once back in, download the driver from ATI's website.  Open a terminal and do:

```
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)

 
cd ~/<location of the driver>

sudo sh ati-driver-installer-8-4-x86.x86_64.run

# let the installer run

cd

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv
```

... the reboot.

Remember that you can't use any desktop effects if you plan to game.

---

