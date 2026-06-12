---
title: "HOWTO: switch from XGL to the new ATI 8.2.3 driver with AIGLX"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by jsully1 on 2007-10-23
**Can a mod please update the thread title to 8.4.2?  I'm not sure how I came up with 8.2.3**

This is a brief guide for anyone who already has Compiz Fusion working with ATi and XGL.  Switching from XGL to the built in AIGLX proved to be incredibly easy, and worked first try for me.  I should note that right now I am *not* impressed with the performance so far - it's noticably slower and choppier, however I no longer have XGL sucking down 40% of my CPU when I rotate screens.

EDIT: Be warned that [a number of people (link)](http://www.phoronix.com/forums/showthread.php?t=5947&page=16) are experiencing slow 2D performance.

Anyway - onto the HowTo!

A brief overview of the steps required:
- Remove XGL
- Reboot
- Download ATi's new driver, make it executable, and run it
- add the restricted driver manager's FGLRX driver to the disabled modules list
- edit xorg.conf to ensure compositing is no longer disabled
- edit the compiz-manager configuration file to allow all GPU types
- reboot
- enjoy!

The first step will be to remove XGL, so fire up Synaptic, search for xgl and remove xserver-xgl, or do a ```
sudo apt-get remove xserver-xgl
```  
Reboot to be safe and make sure that you can still get back into X!

Next step, download the ATi driver from [here](http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run).

Find the file in your terminal and issue this command to make it executable:

```
sudo chmod 755 ati-driver-installer-8.42.3-x86.x86_64.run
```

now run it with
```
sudo ./ati-driver-installer-8.42.3-x86.x86_64.run
```
Follow the on screen prompts and complete the driver installation.  When finished we have a few more steps before we want to reboot.

We need to tell Ubuntu not to use the driver from the restricted manager, and to do that you'll want to add the driver to the disabled modules list by doing:
```
sudo nano /etc/default/linux-restricted-modules-common
```
Here is the contents of my file - yours may have other modules listed as well however:
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="fglrx"
```

Next we need to tweak xorg.conf to enable compositing - all those years of having it disabled, gone!
```
sudo nano /etc/X11/xorg.conf
```
Scroll to the bottom of the file and you should have a bit that looks like this:
```
Section "Extensions"
       Option          "Composite"     "0"
EndSection
```
Note that your specific setup may have "disabled" or something else other than 0.  We want to disable this - I'm just going to comment it out however in case we need to go back to XGL for some reason.  Simply add "#" before each line like so:
```
#Section "Extensions"
#       Option          "Composite"     "0"
#EndSection
```


Now we need to make sure that Compiz is going to allow us to run with this new driver.  By default there is a list of hardware that your GPU needs to show up on or Compiz won't let you run it.  To get around this (AT YOUR OWN PERIL):
```
sudo nano /etc/xdg/compiz/compiz-manager
```
and add the following line to the end of the file:
```
WHITELIST="nvidia intel ati radeon i810 fglrx"
```
This will allow it to run on just about anything - you can likely just include the ATi bits.

That's it - now reboot, and cross your fingers!  When you get back into X you should still have desktop effects, however you'll now be running without XGL.  To confirm, do an "fglrxinfo" - your output should be similar to this:
```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 1.4 (2.0.6958 Release)
```

So to recap:
- Remove XGL
- Reboot
- Download ATi's new driver, make it executable, and run it
- add the restricted driver manager's FGLRX driver to the disabled modules list
- edit xorg.conf to ensure compositing is no longer disabled
- edit the compiz-manager configuration file to allow all GPU types
- reboot, and profit!

**Update from flackmonkey**
If you need to uninstall this new driver and roll back to the version in the Restricted Drivers Manager.  I have not tested this personally - please give feedback if you do this!
```
#Remove fglrx from DISABLED_MODULES
sudo nano /etc/default/linux-restricted-modules-common

#Uninstall 8.4.23 driver.
sudo /usr/share/ati/fglrx-uninstall.sh

#Cleanup any left over stuff from restricted drivers. (Just in case apt thinks it's still installed.)
sudo apt-get remove xorg-driver-fglrx

#Reinstall restricted drivers.
sudo apt-get install xorg-driver-fglrx

#Reboot
sudo shutdown -r now
```
Then you should be able to install the driver again through the restricted manager.

---

### Post by CalcProgrammer1 on 2007-10-23
I'm gonna try this now :)  I have needed this for a LONG time (it was like a year ago that I bought my Radeon X1600Pro).

---

### Post by IHateSnow on 2007-10-23
is it the same if I have a 32-bit processor?

---

### Post by jsully1 on 2007-10-23
This was done on the 32 Bit version of Ubuntu.

---

### Post by CalcProgrammer1 on 2007-10-23
Umm...

Just rebooted with everything installed.  Trying to run Compiz makes it whitescreen entirely and won't come out.  I'm using an X1600Pro AGP with a 32 bit AthlonXP 2600+.

---

### Post by ruscoe on 2007-10-23
AIGLX at last.  I got it working easily enough with your guide. Thanks.

I'm using a Radeon Xpress and noticing a slight choppiness as well. Videos are too choppy to watch full-screen with Compiz enabled, but just three clicks disables it and I can keep it on for normal PC use. Much less hassle than XGL.

---

### Post by flawedreality5 on 2007-10-23
I got:

fglrxinfo 
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

I did not have xgl at all on my system I don't think. I did a fresh install of Gusty and tried to install the ATI drivers using your instructions.

---

### Post by cywhale on 2007-10-23
Thank you, worked like a charm, switched from the free radeon driver (radeon 9700 mobile) to fglrx.
BUT: Scrolling sites in firefox is really, really slow again (like in beryl one year ago), compiz benchmark shows ~200fps but scrolling and resizing gets slower every second - not usable on my 9700 mobile.
I'll try to find a solution but I think I'll be back to the free radeon driver (compiz benchmark shows ~50-100fps but everything works very, very smooth) until tomorrow...

Greets

---

### Post by eternalperson on 2007-10-23
Would this work with a Radeon XPRESS 200?

---

### Post by jsully1 on 2007-10-23
> **cywhale said:**
> Thank you, worked like a charm, switched from the free radeon driver (radeon 9700 mobile) to fglrx.
BUT: Scrolling sites in firefox is really, really slow again (like in beryl one year ago), compiz benchmark shows ~200fps but scrolling and resizing gets slower every second - not usable on my 9700 mobile.
I'll try to find a solution but I think I'll be back to the free radeon driver (compiz benchmark shows ~50-100fps but everything works very, very smooth) until tomorrow...

Greets
Yeah I'm having the same problem - disabling visual effects in the Appearance Preferences tab fixes it, but that's hardly a solution.  I tried going back to xgl (apt-get reinstall xserver-xgl, uncomment those bits in xorg.conf) however on rebooting it seems that the poor scrolling is related to the driver.  Time to roll back!  Anyone know the best way of going about uninstalling this new driver?

---

### Post by guillepb on 2007-10-23
Could someone post instructions on how to roll back and uninstall the latest driver in case we screw up? (I know I probably will...)

---

### Post by Lorenz on 2007-10-23
Any experience with an ATI x1300?
I got it to work nicely with Xorg and wouldn't want to mess it up now.

---

### Post by jsully1 on 2007-10-23
I'm running an X1300 - stay away for now, and go the XGL route.  This is performing miserably - scrolling in Firefox is unusable like the old days.

---

### Post by Lorenz on 2007-10-23
Thanks for the quick reply!
I'll wait then, perhaps there is a fix coming up from Compiz or ATI (next month).

---

### Post by jsully1 on 2007-10-23
Can a mod update the thread title that I typo'd?  This should obviously be ATI 8.4.2 :(

---

### Post by teabeartom on 2007-10-23
I installed it, but now it says that I have the mesa 3d driver...

I attached a screenshots of the control panel.  Any suggestions?

---

### Post by Nukeador on 2007-10-23
Same here (ati 9600 XT):

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

So if compiz is enabled I get a blank screen :S

---

### Post by Good_Newz on 2007-10-23
Enable restricted drivers in ubuntu control panel :) It took me a while to figure this out.

---

### Post by Brandito101 on 2007-10-23
Same here:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


Also, I have like 14 different xorg.conf. Which (if any) can I safely delete? Where is my normal xorg.conf? What did I do?
Thanks

app-defaults                  xorg.conf.1                               xorg.conf.fglrx-0
cursors                         xorg.conf.2                               xorg.conf.original-0
default-display-manager  xorg.conf.20070922191247        Xresources
fonts                             xorg.conf.20070922191827        xserver
rgb.txt                           xorg.conf.20070922192415        Xsession
X                                  xorg.conf.20071022142507        Xsession.d
xinit                              xorg.conf.20071022143452        Xsession.options
xkb                               xorg.conf_backup                      XvMCConfig
xorg.conf~                    xorg.conf.failsafe                      Xwrapper.config
xorg.conf~~                  xorg.conf.failsafe.bak

---

### Post by changty on 2007-10-23
I just got my system busted with this. I have HD2600, inside latest iMac, and every time i even think about using "glxinfo" or "fglrxinfo" my x-server crashes. 

dmesg:
```
[   69.912000] [fglrx] PCIe has already been initialized. Reinitializing ...
[   69.948000] [fglrx:firegl_unlock] *ERROR* Process 5984 using kernel context 0
[  178.164000] [fglrx] PCIe has already been initialized. Reinitializing ...
[  178.200000] [fglrx:firegl_unlock] *ERROR* Process 6220 using kernel context 0

```

Damn ATI :(

---

### Post by ba5e on 2007-10-23
I have got it all installed well, but I built deb packages witht he ATI isntaller....makes it a bit easier to uninstall ;P

Scrolling is slow...etc etc destop effects are slow, even on my C2D and X1950Pro - but it is a step forward!

I will be rolling back until the AIGLX driver is a little more mature!

---

### Post by phrizek on 2007-10-23
This did not work for me. Compiz doesn't want to turn on. My terminal outputs this when I try to run compiz:

Checking for Xgl: not present. 
Blacklisted PCIID '1002:5955' found 
aborting and using fallback: /usr/bin/metacity 

How do I get it to default to AIGLX?

---

### Post by Nukeador on 2007-10-23
You have to add fglrx in the white list:

sudo gedit /etc/xdg/compiz/compiz-manager

Add:
WHITELIST="nvidia intel ati radeon i810 fglrx"

---

### Post by phrizek on 2007-10-23
> **Nukeador said:**
> You have to add fglrx in the white list:

sudo gedit /etc/xdg/compiz/compiz-manager

Add:
WHITELIST="nvidia intel ati radeon i810 fglrx"

I did this. Still not working for me.

---

### Post by darkshadow on 2007-10-23
phrizek the top sticky about blacklisting will fix that for you

Now my question. Everything seems to work but I no longer have a xvideo extension, how can I fix this?

---

### Post by somabc on 2007-10-23
Sorry If I am being a bit slow here but can anyone check that I am following this OK?

My System - C2D, ATI X1900

So, a few days ago -
I installed Ubuntu 7.10 (Gutsy) for AMD64
I enabled restricted drivers manager and installed ati driver from repo's

Today -

Downloaded  - ati-driver-installer-8.42.3-x86.x86_64.run 
Unticked ATI accelerated driver in restricted drivers manager
Restarted PC

Tried to build .deb package by 
> sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy

Got error
> Created directory fglrx-install.HS6859
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.bt6937/debian/control.template ]; then \
                cat /tmp/fglrx.bt6937/debian/control.template > /tmp/fglrx.bt6937/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.bt6937/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.bt6937/debian/driver.$i > \
              /tmp/fglrx.bt6937/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.bt6937/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.bt6937/debian/10fglrx.template > /tmp/fglrx.bt6937/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.bt6937/debian/fglrx.default ]; then \
          mv /tmp/fglrx.bt6937/debian/fglrx.default /tmp/fglrx.bt6937/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.bt6937/debian/control.template ]; then \
                cat /tmp/fglrx.bt6937/debian/control.template > /tmp/fglrx.bt6937/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.bt6937/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.bt6937/debian/driver.$i > \
              /tmp/fglrx.bt6937/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.bt6937/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.bt6937/debian/10fglrx.template > /tmp/fglrx.bt6937/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.bt6937/debian/fglrx.default ]; then \
          mv /tmp/fglrx.bt6937/debian/fglrx.default /tmp/fglrx.bt6937/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.bt6937/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.bt6937/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/sbin \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                etc/acpi \
                etc/acpi/events \
                etc/default \
                etc/X11/Xsession.d
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.HS6859


Next ran installer and install via GUI instead
> sudo ./ati-driver-installer-8.42.3-x86.x86_64.run

disabled old fglrx module as per instructions
> sudo nano /etc/default/linux-restricted-modules-common
DISABLED_MODULES="fglrx"

Added fglrx to whitelist for compiz

Restarted Computer

Driver was not active so ran
> sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Restarted Computer

Ran fglrxinfo
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


Compiz will not run!!

Please help me?
Thank You!

---

### Post by Nukeador on 2007-10-23
The only problem I noticed is that opengl applications in non full-screen-mode blink. It's really annoying now to play a opengl game in windowed mode, I've to disable compiz.

Also slow scrolling in Firefox (just in Firefox :S).

EDIT: The people using the "ati" driver, should open restricted manager AFTER installing the new driver and enable fglrx and then edit xorg.conf and remove Composite "0". This will tell Ubuntu to use the fglrx driver instead of mesa.

---

### Post by teabeartom on 2007-10-23
> **Good_Newz said:**
> Enable restricted drivers in ubuntu control panel :) It took me a while to figure this out.

Well, I blacklisted Ubuntu's fglrx, so it wasn't showing up in the restricted manager anymore.  I de-blacklisted it, then installed it in ubuntu's restricted manager, restarted, and then re-installed the 8.42.3 driver.  Now, I still have the Mesa 3d showing up. 

In xorg.conf, the driver is listed as fglrx, and in the ati catalyst control center, it shows that I have 8.42.3 installed (see screenshot on page 2), yet my opengl acceleration is still using mesa...

Any other suggestions?

---

### Post by reedb42 on 2007-10-23
I've followed all the same steps as somabc and encountered the same problem, Ubuntu seems to be using the mesa glx driver instead of fglrx. There is one key difference, though. When I try to log in under a normal session, gnome disappears (crashes? I'm not sure) and the desktop white-screens. So I need to switch to a failsafe session to do anything after installing fglrx 8.42.3.

In case it's important, my card is a Radeon 9600 Pro, which works great when I install 8.37.6 through the restricted drivers manager.

---

### Post by teabeartom on 2007-10-23
> **Nukeador said:**
> The only problem I noticed is that opengl applications in non full-screen-mode blink. It's really annoying now to play a opengl game in windowed mode, I've to disable compiz.

Also slow scrolling in Firefox (just in Firefox :S).

EDIT: The people using the "ati" driver, should open restricted manager AFTER installing the new driver and enable fglrx and then edit xorg.conf and remove Composite "0". This will tell Ubuntu to use the fglrx driver instead of mesa.

When we open the restricted manager AFTER installing the new driver, there is no entry for fglrx since we had already blacklisted it...  I attached another shot of this.  

If anyone knows the solution for this, please help!  Thanks!

---

### Post by darkshadow on 2007-10-23
I got the xvideo extension working using "sudo aticonfig --overlay-type=Xv" but it only works in full screen mode and is blank when windowed. What could be causing this.

---

### Post by cor2y on 2007-10-23
yes that is true.
ATI X850XT is my card.
Followed the steps no 2d effects slow downs that i have noticed.
But i have no fglrxinfo or ATI control panel after the install . removal of the official restricted driver.
From the terminal 
```

 fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found

```

Puting back/re-enabling the restricted driver after removing the black listing.
Just gives me of course regular metacity.
removing it and not black listing and just installing the one from ati gives me regular metacity as well.
But blacklist fglrx and reboot and i have compiz-fusion working of course i don't know if its the open drivers or the ati one as fglrx is not installed.

---

### Post by ubuntu dave on 2007-10-23
Ubuntu Gutsy x86_64 with x800xt vivo working with 8.42.3 pretty well so far.
Compiz seems to be running flawlessly - benchmark on OS ati drivers was 175ish FPS 'standing still', and on the 8.42.3 drivers is 375ish FPS standing still.
Haven't tested any games yet.
Video seems to be CPU dependent at the minute - will be fiddling/tweaking my xorg.conf in due time to see how that goes.

\\:D/ So far!

---

### Post by superyounan1 on 2007-10-23
arrrgghhhh whyyyy

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6958 Release



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6958 Release

*** glibc detected *** fglrxinfo: double free or corruption (!prev): 0x08062060 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d0fd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d13800]
/usr/lib/dri/fglrx_dri.so[0xb79bac92]
/usr/lib/libGL.so.1[0xb7f1ec61]
/usr/lib/libX11.so.6(_XFreeExtData+0x25)[0xb7e1d7d5]
/usr/lib/libX11.so.6(_XFreeDisplayStructure+0x2f6)[0xb7e29df6]
/usr/lib/libX11.so.6(XCloseDisplay+0xea)[0xb7e16eea]
fglrxinfo[0x8048a3b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cbc050]
fglrxinfo[0x80488f1]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 03:42 1589707    /usr/bin/fglrxinfo
0804b000-0804c000 rw-p 00002000 03:42 1589707    /usr/bin/fglrxinfo
0804c000-08475000 rw-p 0804c000 00:00 0          [heap]
a5fad000-a5fae000 rw-p a5fad000 00:00 0 
a6270000-ae270000 rw-s 00003000 00:0e 19460      /dev/dri/card0
ae270000-ae532000 rw-p ae270000 00:00 0 
ae532000-ae538000 rwxp ae532000 00:00 0 
ae538000-ae5ab000 rw-p ae538000 00:00 0 
ae5ab000-aecab000 rw-s 00005000 00:0e 19460      /dev/dri/card0
aecab000-aecbb000 rw-s 00004000 00:0e 19460      /dev/dri/card0
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6ca1000-b6cab000 r-xp 00000000 03:42 491587     /lib/libgcc_s.so.1
b6cab000-b6cac000 rw-p 0000a000 03:42 491587     /lib/libgcc_s.so.1
b6cbb000-b6cde000 r-xp 00000000 03:42 525587     /lib/tls/i686/cmov/libm-2.6.1.so
b6cde000-b6ce0000 rw-p 00023000 03:42 525587     /lib/tls/i686/cmov/libm-2.6.1.so
b6ce0000-b6ce7000 r-xp 00000000 03:42 525609     /lib/tls/i686/cmov/librt-2.6.1.so
b6ce7000-b6ce9000 rw-p 00006000 03:42 525609     /lib/tls/i686/cmov/librt-2.6.1.so
b6ce9000-b7aa2000 r-xp 00000000 03:42 4161553    /usr/lib/dri/fglrx_dri.so
b7aa2000-b7b27000 rw-p 00db9000 03:42 4161553    /usr/lib/dri/fglrx_dri.so
b7b27000-b7c81000 rw-p b7b27000 00:00 0 
b7c81000-b7c83000 r-xp 00000000 03:42 525585     /lib/tls/i686/cmov/libdl-2.6.1.so
b7c83000-b7c85000 rw-p 00001000 03:42 525585     /lib/tls/i686/cmov/libdl-2.6.1.so
b7c85000-b7c89000 r-xp 00000000 03:42 1590579    /usr/lib/libXdmcp.so.6.0.0
b7c89000-b7c8a000 rw-p 00003000 03:42 1590579    /usr/lib/libXdmcp.so.6.0.0
b7c8a000-b7c8b000 rw-p b7c8a000 00:00 0 
b7c8b000-b7c8d000 r-xp 00000000 03:42 1590568    /usr/lib/libXau.so.6.0.0
b7c8d000-b7c8e000 rw-p 00001000 03:42 1590568    /usr/lib/libXau.so.6.0.0
b7c8e000-b7ca2000 r-xp 00000000 03:42 525605     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7ca2000-b7ca4000 rw-p 00013000 03:42 525605     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7ca4000-b7ca6000 rw-p b7ca4000 00:00 0 
b7ca6000-b7dea000 r-xp 00000000 03:42 525579     /lib/tls/i686/cmov/libc-2.6.1.so
b7dea000-b7deb000 r--p 00143000 03:42 525579     /lib/tls/i686/cmov/libc-2.6.1.so
b7deb000-b7ded000 rw-p 00144000 03:42 525579     /lib/tls/i686/cmov/libc-2.6.1.so
b7ded000-b7df0000 rw-p b7ded000 00:00 0 
b7df0000-b7dfd000 r-xp 00000000 03:42 1590583    /usr/lib/libXext.so.6.4.0
b7dfd000-b7dfe000 rw-p 0000d000 03:42 1590583    /usr/lib/libXext.so.6.4.0
b7dfe000-b7eeb000 r-xp 00000000 03:42 1590562    /usr/lib/libX11.so.6.2.0
b7eeb000-b7eef000 rw-p 000ed000 03:42 1590562    /usr/lib/libX11.so.6.2.0
b7eef000-b7f75000 r-xp 00000000 03:42 901308     /usr/lib/xorg/libGL.so.1.2
b7f75000-b7f77000 rw-p 00086000 03:42 901308     /usr/lib/xorg/libGL.so.1.2
b7f77000-b7f7a000 rw-p b7f77000 00:00 0 
b7f85000-b7f87000 rw-s 00002000 00:0e 19460      /dev/dri/card0
b7f89000-b7f8a000 rw-p b7f89000 00:00 0 
b7f8a000-b7fa4000 r-xp 00000000 03:42 491540     /lib/ld-2.6.1.so
b7fa4000-b7fa6000 rw-p 00019000 03:42 491540     /lib/ld-2.6.1.so
bf8dc000-bf8f0000 rwxp bf8dc000 00:00 0          [stack]
bf8f0000-bf8f1000 rw-p bf8f0000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


```

---

### Post by thinkcow on 2007-10-23
Works perfectly for the ATI Radeon X1200!

Thanks for the instructions!!

):P

Thinkcow

---

### Post by rjregenold on 2007-10-23
I've got the x300 and I'm having the same issue as a couple other people here.

```

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

Does anybody know why this is?

Thanks.

---

### Post by sdowney717 on 2007-10-23
yes, sot of.
I had same problem. Aftr you follow the gide then
DISABLE resticted driver, then enable resticted
then reboot

Still, I cant run compiz
root@scott-desktop:~# compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e50 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

now I have
root@scott-desktop:~# glxgears
5271 frames in 5.0 seconds = 1054.192 FPS
11599 frames in 5.0 seconds = 2319.783 FPS
11602 frames in 5.0 seconds = 2320.361 FPS
11599 frames in 5.0 seconds = 2319.794 FPS
11376 frames in 5.0 seconds = 2275.198 FPS
root@scott-desktop:~# 

root@scott-desktop:~# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer

---

### Post by num3thod on 2007-10-23
I also would like to know how to roll back to xgl. X1300 performance is terrible : (

Cheers,

---

### Post by timdog219 on 2007-10-23
I was having a similar problem to some of the other people where I followed the instructions step by step but I was still having the mesa driver show up when I checked the ATI control panel or ran fglrxinfo.  I was able to get around this by doing the following (I'm still pretty much a noob so not sure if this was the "right" way of doing things :)):

First I found that the fglrx module was not loading:

```
lsmod | grep fglrx
```

There was no output from this command indicating that no kernel module named "fglrx" was loaded.

trying to load the module manually was giving me an error:
```
sudo modprobe fglrx
```

This was saying that it could not find the file:

/lib/modules/2.6.22-14-generic/volatile/fglrx.ko

So I went to find where the module was in the filesystem.  I checked the ati driver install log (/usr/share/ati/fglrx-install.log) and saw that it had compiled the kernel modules into the directory /lib/modules/fglrx.  Exploring that directory I found a file called

fglrx.2.6.22-14-generic.ko 

I assumed that this was the file I needed.  So I just created a symbolic link to this file in the /lib/modules/2.6.22-14-generic/volatile directory:

```
sudo ln -s /lib/modules/fglrx/fglrx.2.6.22-14-generic.ko /lib/modules/2.6.22-14-generic/volatile/fglrx.ko
```

After this I was able to load the fglrx module with:

```
sudo modprobe fglrx
```

and checking with lsmod gives:

```
lsmod | grep fglrx
fglrx                1480044  24 
agpgart                35016  2 fglrx,intel_agp
```

Restarting X and checking fglrxinfo showed that the ATI driver was loading properly.  

EDIT:

Upon further exploration, apparently the system doesn't like you modifying files in the modules directory, because when I restarted the link to the fglrx module had disappeared from the volatile/ directory.  I tried just copying the module over from the fglrx/ directory and same deal, it was gone when I restarted.  So how can I point the system to the proper module location??

---

### Post by reedb42 on 2007-10-24
I can't claim to be any kind of expert on the inner workings of Ubuntu or Linux in general, but I would imagine that the name "volatile" would imply that the contents of that directory are only there while the system is running. They're likely copied there at startup or something similar. I think you're on the right track to a solution, though.

---

### Post by aggiemarine07 on 2007-10-24
Worked great Thanks!
One minor thing, I had to go into the xorg.conf file and enable AIGLX because I was getting a white screen for a while until I enabled that.

---

### Post by Poene on 2007-10-24
I might actually try Ubuntu again, but I keep booting up to Windows to play Team Fortress 2. The game is addictively fun.

---

### Post by Akre on 2007-10-24
Tried on nx6125 notebook (xpress 200m card) x64 edition.
Packaging script for 64 bits is broken. Instaling without using package went smooth. (removed restricted modules pkg first)

Compiz working, slow FF scrolling.

I did not check video playback yet.

---

### Post by XAsmodeanX on 2007-10-24
Acer Aspire w/ X1100 here.

I tried your instructions and got a white screen when trying to start the desktop effects.  fglrxinfo tells me that it's using mesa.  I've never installed xgl and I tried enabling and disabling fglrx in the Restricted Modules dialog.  White screens everytime.  

Also with : [http://ubuntuforums.org/showthread.php?t=589075](http://ubuntuforums.org/showthread.php?t=589075)
When I attempted to create the directories and link the modules symbolically, i got a file exists error.  Even though it already exists I'm still getting the Mesa 3d when I do fglrxinfo.

No matter what I do I cannot stop getting a white screen or the Mesa 3d to go away.  I have enabled compositing and AIGLX in xorg.

---

### Post by viriatus on 2007-10-24
I have a Acer Aspire 1692WLMI with a ATI X700

i was using XGL and the desktop effetcs were working ok. I used the ati driver from the repositories. But performance was bad i was getting 30fps max in Urban Terror (in XP i get 70fps) but now i followed this HOWTO and now desktop effects aren't working. And if i do fglrx i get the mesa thing. I'm really getting tired of LInux....

:confused::confused::mad::mad:

---

### Post by Trevster on 2007-10-24
Been messing with the new driver for an hour now and no luck so far. It seems to install fine, the restricted drivers manager says it's in use and enabled. I still get "OpenGL renderer string: Mesa GLX Indirect".

lsmod | grep fglrx
fglrx                 656352  0 
agpgart                35016  2 fglrx,amd64_agp

I am using a ati 9600xt seems the 9600 is causing problems for many. I am using dual screens, my xorg.conf shows only fglrx for the drivers.

 I sure someone will figure it out.

---

### Post by cor2y on 2007-10-24
Well the good news is i believe i have hardware 3d acceleration with compiz-fusion (my screensavers that use opengl run smoothly and fast)
However according to the mod probe fglrx is not installed.
So its a complete mystery to me what is going on.
Also no slowdowns with firefox scrolling or other 2d things video playback is as it was before in plain metacity.

---

### Post by flacmonkey on 2007-10-24
I had this same problem with the mesa 3d. What I found was that my computer was still looking for the restricted modules version of the fglrx kernel module. The fix is pretty easy.

First make sure that you have blacklisted fglrx in /etc/default/linux-restricted-modules-common

Next edit the modules.dep for your kernel.

```
sudo nano /lib/modules/2.6.22-14-generic/modules.dep

```

Find the line that reads:

```

/lib/modules/2.6.22-14-generic/volatile/fglrx.ko: /lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/agpgart.ko

```

And change it to:

```

/lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/fglrx.ko: /lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/agpgart.ko

```

If you are using a different kernel, then replace 2.6.22-14-generic with the path to your kernel.
Reboot and your problem should be fixed. :)

---

### Post by timdog219 on 2007-10-24
Well I was able to fix that module loading problem.  I had to edit my /lib/modules/2.6.22-14-generic/modules.dep file.  There was a line pointing at fglrx.ko in the volatile/ directory, and I just changed that to /lib/modules/fglrx/fglrx.ko (which is just a symbolic link to the file fglrx-2.6.22-14-generic.ko)

BTW I read that the volatile/ directory is where the restricted driver modules are stored.

FWIW the performance is good on my ATI Mobility Radeon X1400 - the only issue I have so far is that video has been flickering with totem.

---

### Post by rjregenold on 2007-10-24
> **flacmonkey said:**
> I had this same problem with the mesa 3d. What I found was that my computer was still looking for the restricted modules version of the fglrx kernel module. The fix is pretty easy.

First make sure that you have blacklisted fglrx in /etc/default/linux-restricted-modules-common

Next edit the modules.dep for your kernel.

```
sudo nano /lib/modules/2.6.22-14-generic/modules.dep

```

Find the line that reads:

```

/lib/modules/2.6.22-14-generic/volatile/fglrx.ko: /lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/agpgart.ko

```

And change it to:

```

/lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/fglrx.ko: /lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/agpgart.ko

```

If you are using a different kernel, then replace 2.6.22-14-generic with the path to your kernel.
Reboot and your problem should be fixed. :)

I followed these directions. After I rebooted, modules.dep reverted back to the old entry using /lib/modules/.../volatile/fglrx.ko. How can I get it to remember my settings?

Thank you.

---

### Post by flacmonkey on 2007-10-24
rjregenold,
The only thing that I can think of is that fglrx is not blacklisted.

```

sudo nano /etc/default/linux-restricted-modules-common

```
Change the DISABLED_MODULES line from this
```

DISABLED_MODULES=""

```
To this:
```

DISABLED_MODULES="fglrx"

```

If you already have some disables modules listed just append fglrx to the end.
Like this:
```

DISABLED_MODULES="ath_hal fglrx"

```

Then edit the modules.dep file and reboot.

---

### Post by rjregenold on 2007-10-24
flacmonkey,

Thanks for the quick response; that was the issue. I had blacklisted it earlier, but I guess I did something that took it off the blacklist.

So now I have fglrx blacklisted, I updated the modules.dep file to point to /lib/modules/fglrx/fglrx.ko and I'm still getting Mesa indirect rendering. The ATI Catalyst Control Center says I'm running 8.42.3, but it's still using Mesa for the Open GL Renderer.

Not sure what else to do. Any more ideas?

Thanks.

---

### Post by flacmonkey on 2007-10-24
rjregenold,

See if the fglrx kernel module is loaded.
```

lsmod | grep fglrx

```
If fglrx is loaded, look through you xorg log file.
```

less /var/log/Xorg.0.log

```
See if you see any error with fglrx, version conflicts etc.

If fglrx module is not loaded, try running:
```

sudo modprobe fglrx

```
Do you get an errors after the modprobe?

One other thing, in my modules.dep changed the line to:
```

/lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/fglrx.ko

```

---

### Post by rjregenold on 2007-10-24
flacmonkey,

lsmod tells me that the fglrx module is not loaded. So I ran:

```

sudo modprobe fglrx

```

and it didn't output anything (which I believe means it loaded without error).

Then I started browsing through my xorg log and found this:

```

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver

```

which makes me think that it loaded the module. Then a little further down in the log file I found this:

```

(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

I guess I need to update X.org? I'll give that a shot and let you know the results. Thanks again for your help. I really appreciate it.

---

### Post by XAsmodeanX on 2007-10-24
Thanks to flacmonkey and rjregenold I've got the driver working correctly and desktop effects work flawlessly.

BTW I have no video playback errors with desktop effects enabled - even in fullscreen.

There are issues with firefox scrolling but I've found that you can just go into preferences -> Advanced tab and disable smooth scrolling.  It's not as pretty but it's not slow at all.

This is on an ATI X1100.

---

### Post by rjregenold on 2007-10-24
Hmm. I checked my Xorg version and it appears to be alright. I did find this though...

When I run:
```

/lib/modules/fglrx/build_mod$ sudo ./make.sh 
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
==============================

```

everything looks alright. Then I run:
```

/lib/modules/fglrx$ sudo ./make_install.sh 
- recreating module dependency list
- trying a sample load of the kernel modules
ERROR: Module fglrx does not exist in /proc/modules
done.

```

and get that error. Maybe that explains why lsmod shows that fglrx isn't loaded (even after I sudo modprobe fglrx)? I've run the installer, so I'm not sure why the module doesn't exist...

---

### Post by flacmonkey on 2007-10-24
rjregenold,

For some reason, the fglrx kernel module is not loading automatically at boot time.
Try this:
```

sudo nano /etc/modprobe.d/aliases

```
Add these line to the end:
```

#Autoload the fglrx module
alias char-major-226-0 fglrx

```
After that change, reboot and see if it worked.

Congratulations XAsmodeanX!!! :D
Happy to help.

---

### Post by rjregenold on 2007-10-24
flacmonkey,

Thanks again for taking the time to help me. I tried adding the alias line to /etc/modprobe.d/aliases, but it still doesn't load. I think for some reason the system can't find the fglrx module.

I tried reinstalling the driver, and when I try:
```

/lib/modules/fglrx$ sudo ./make_install.sh 
- recreating module dependency list
- trying a sample load of the kernel modules
ERROR: Module fglrx does not exist in /proc/modules
done.

```

it still gives me that error. Maybe I have some old fglrx driver files out there that are messing the new ones up? I'm not sure.

---

### Post by Neo4 on 2007-10-24
finally got it!
for those who have mesa

just edit the xorg.conf and in all sections called device change driver to fglrx

that do the trick for me

---

### Post by reedb42 on 2007-10-24
I must be doing something wrong. Even after trying every workaround thus far suggested in this thread, Ubuntu still adamantly refuses to load the fglrx module instead of mesa. I don't know where to even start trying to diagnose the problem, as "modprobe fglrx" gives me no errors and Xorg.0.log is too long and cryptic for me to pinpoint anything that might be going wrong.

This is extremely confusing to me, because the version up in the repositories works perfectly.

---

### Post by flacmonkey on 2007-10-24
rjregenold,

Sorry this still not working for you, I know how frustrating it can be. :(
The error "ERROR: Module fglrx does not exist in /proc/modules" is caused when the make_install.sh script is tries to remove any existing fglrx module from memory. It is just saying that the module is not loaded.

Try running:
```

slocate fglrx.ko

```
Post the result here. Also copy your modules.dep file to a text file and attach it to your response.

---

### Post by rjregenold on 2007-10-24
For some reason *slocate* didn't return anything. But this did:
```

/lib/modules/fglrx$ sudo find / -name fglrx.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/fglrx.ko
/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
/lib/modules/fglrx/build_mod/fglrx.ko
/lib/modules/fglrx/fglrx.ko

```

And I've attached modules.dep as requested. The file was too large, so I copied a few lines above and a few lines below the line where fglrx.ko was located. If you would like any other info, please don't hesitate to ask.

Thanks.

---

### Post by Neo4 on 2007-10-24
this fglrx is very very slow!

---

### Post by flacmonkey on 2007-10-24
rjregenold,

Everything looked OK from the modules.dep and the find that you ran.
I have one more thing for you to try.
First:
```

sudo modprobe fglrx
lsmod | grep fglrx

```
This should load fglrx into memory. If lsmod shows fglrx, then restart X.
```

sudo /etc/init.d/gdm restart

```
That should restart Xorg without rebooting your computer. See if X is still using mesa after that.
If it is still using mesa please post you /var/log/Xorg.0.log file.

If X is not using mesa change the /etc/modprobe.d/aliases from this:
```

#Autoload the fglrx module
alias char-major-226-0 fglrx

```
To this:
```

#Autoload the fglrx module
install fglrx /sbin/modprobe --ignore-install fglrx

```
And reboot.

---

### Post by xieu90 on 2007-10-24
hi this is a bit slow somehow, but it doesn't drink my cpu and ram like before, not so bad
but I have a problem now, whenever I press the red button (shutdown) on the right corner then my computer is dead, everything is there and I can move my mouse, but my keyboard and right click of mouse, left click and everything won't work, except ctrl alt back
so what is it now ?

can I somehow make things move smooth ?
it move like an almost freezing system

---

### Post by rjregenold on 2007-10-24
Yes!! Thank you very much flacmonkey.

I am happy to say that adding this line to my /etc/modprobe.d/aliases fixed the problem:
```

#Autoload the fglrx module
install fglrx /sbin/modprobe --ignore-install fglrx

```

Thank you!
```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6958 Release

```

---

### Post by riverfr0zen on 2007-10-24
Haven't tried the HOWTO yet, but don't reallty want to without knowing how to rollback to the current  Gutsy restricted driver - I went through this thread, but didn't see any directions on that - can someone provide those (or point me appropriately if I missed something)? Thanks.

---

### Post by geekphreak on 2007-10-24
I am running Gutsy on AMD64 with Xpress 200M. I finally got 8.42 to load instead of mesa, but I still have no direct rendering.
```
 LIBGL_DEBUG=verbose glxinfo |grep direct
libGL: XF86DRIGetClientDriverName: 8.42.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: fglrx_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```I have created symbolic links to fglrx modules as described in the thread but my xorg log shows ```
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
....
```Any ideas anyone?

Thanks!

---

### Post by geekphreak on 2007-10-24
Got it!

Followed this: [http://www.guiaubuntupt.org/wiki/index.php?title=ATI_fglrx_8.42.3](http://www.guiaubuntupt.org/wiki/index.php?title=ATI_fglrx_8.42.3)
I don't speak Portuguese but it's not hard to understand.
Pretty good performance. Yay!

---

### Post by flacmonkey on 2007-10-25
> **riverfr0zen said:**
> Haven't tried the HOWTO yet, but don't reallty want to without knowing how to rollback to the current  Gutsy restricted driver - I went through this thread, but didn't see any directions on that - can someone provide those (or point me appropriately if I missed something)? Thanks.

Well I haven't tested it, but there is an uninstall script. So probably something like this.
```

*#Remove fglrx from DISABLED_MODULES*
sudo nano /etc/default/linux-restricted-modules-common

*#Uninstall 8.4.23 driver.*
sudo /usr/share/ati/fglrx-uninstall.sh

*#Cleanup any left over stuff from restricted drivers. (Just in case apt thinks it's still installed.)*
sudo apt-get remove xorg-driver-fglrx

*#Reinstall restricted drivers.*
sudo apt-get install xorg-driver-fglrx

*#Reboot*
sudo reboot

```

Since I have not tested it, I make no guarantees about how well this works, if at all.
Caveat emptor

BTW, congrats rjregenold! Glad to hear it is working for you.

---

### Post by guillepb on 2007-10-25
If you have installed it using the .deb packages generated by the installer, would you still have to use the uninstall script? I guess you could also uninstall them from synaptic, right?

---

### Post by flacmonkey on 2007-10-25
if you installed from a .deb package then you should be able to uninstall with synaptic or dpkg -P, you should not need the script. I think you would still need to make the other changes I mentioned, unless the .deb package is setup to make those changes automatically.

---

### Post by jsully1 on 2007-10-25
> **flacmonkey said:**
> Well I haven't tested it, but there is an uninstall script. So probably something like this.
```

*#Remove fglrx from DISABLED_MODULES*
sudo nano /etc/default/linux-restricted-modules-common

*#Uninstall 8.4.23 driver.*
sudo /usr/share/ati/fglrx-uninstall.sh

*#Cleanup any left over stuff from restricted drivers. (Just in case apt thinks it's still installed.)*
sudo apt-get remove xorg-driver-fglrx

*#Reinstall restricted drivers.*
sudo apt-get install xorg-driver-fglrx

*#Reboot*
sudo reboot

```

Since I have not tested it, I make no guarantees about how well this works, if at all.
Caveat emptor


Thanks!  I've added these instructions to the first post, along with a bit requesting feedback to see if they actually work :).

---

### Post by flacmonkey on 2007-10-25
jsully1,
Thanks for adding me to the HOWTO. I have just tested the uninstall procedure. The steps I posted worked and I did need to re-enable the driver through the restricted drivers manager, as you suggested. I did run into one little snag. I got the old driver installed, but got stuck with mesa 3d instead of the ATI renderer. I had to add a line to the modules.dep file in /lib/modules/2.6.22-14-generic and reboot, to re-enable the ATI renderer.
```

sudo nano /lib/modules/2.6.22-14-generic/modules/dep
*#Insert the following row at the end of the file.*
/lib/modules/2.6.22-14-generic/volatile/fglrx.ko: /lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/agpgart.ko

*#Reboot the computer.*
sudo reboot

```
Of course everyone would need to substitute 2.6.22-14-generic for their kernel version.;)

---

### Post by dannns on 2007-10-26
Hi, I had to run the remove script to remove my previous try of installing an ATI driver, it seemed to have done a good job.


Now I was able to install the new driver, however I still can't start compiz on my HD2600XT. And I don't understand the following message that appears when I try fglrxinfo, and similar stuff appears if I try to start compiz from the terminal.

Does any body have any clue of what this means?

```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.0.6958 Release



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.0.6958 Release

*** glibc detected *** fglrxinfo: corrupted double-linked list: 0x000000000051ef40 ***
======= Backtrace: =========
/lib/libc.so.6[0x2ba0b246cda2]
/lib/libc.so.6(cfree+0x8c)[0x2ba0b24706fc]
/usr/lib/dri/fglrx_dri.so[0x2ba0b3bcae15]
/usr/lib/libGL.so.1[0x2ba0b1d0d2f6]
/usr/lib/libX11.so.6(_XFreeExtData+0x15)[0x2ba0b1f040c5]
/usr/lib/libX11.so.6(_XFreeDisplayStructure+0x30e)[0x2ba0b1f10dee]
/usr/lib/libX11.so.6(XCloseDisplay+0xcb)[0x2ba0b1efd13b]
fglrxinfo(XOpenDisplay+0x1b6)[0x400dce]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2ba0b2418b44]
fglrxinfo(XOpenDisplay+0x52)[0x400c6a]
======= Memory map: ========
00400000-00403000 r-xp 00000000 03:03 2747879                            /usr/bin/fglrxinfo
00502000-00503000 rw-p 00002000 03:03 2747879                            /usr/bin/fglrxinfo
00503000-01396000 rw-p 00503000 00:00 0                                  [heap]
2ba0b1cbb000-2ba0b1cd8000 r-xp 00000000 03:03 1815091                    /lib/ld-2.6.1.so
2ba0b1cd8000-2ba0b1cdb000 rw-p 2ba0b1cd8000 00:00 0 
2ba0b1ce6000-2ba0b1d61000 r-xp 00000000 03:03 3433922                    /usr/lib/xorg/libGL.so.1.2
2ba0b1d61000-2ba0b1e60000 ---p 0007b000 03:03 3433922                    /usr/lib/xorg/libGL.so.1.2
2ba0b1e60000-2ba0b1e79000 rw-p 0007a000 03:03 3433922                    /usr/lib/xorg/libGL.so.1.2
2ba0b1e79000-2ba0b1e7d000 rw-p 2ba0b1e79000 00:00 0 
2ba0b1ed7000-2ba0b1ed9000 rw-p 0001c000 03:03 1815091                    /lib/ld-2.6.1.so
2ba0b1ed9000-2ba0b1fe3000 r-xp 00000000 03:03 2748446                    /usr/lib/libX11.so.6.2.0
2ba0b1fe3000-2ba0b21e3000 ---p 0010a000 03:03 2748446                    /usr/lib/libX11.so.6.2.0
2ba0b21e3000-2ba0b21ea000 rw-p 0010a000 03:03 2748446                    /usr/lib/libX11.so.6.2.0
2ba0b21ea000-2ba0b21fb000 r-xp 00000000 03:03 2748467                    /usr/lib/libXext.so.6.4.0
2ba0b21fb000-2ba0b23fa000 ---p 00011000 03:03 2748467                    /usr/lib/libXext.so.6.4.0
2ba0b23fa000-2ba0b23fb000 rw-p 00010000 03:03 2748467                    /usr/lib/libXext.so.6.4.0
2ba0b23fb000-2ba0b254d000 r-xp 00000000 03:03 1815111                    /lib/libc-2.6.1.so
2ba0b254d000-2ba0b274c000 ---p 00152000 03:03 1815111                    /lib/libc-2.6.1.so
2ba0b274c000-2ba0b274f000 r--p 00151000 03:03 1815111                    /lib/libc-2.6.1.so
2ba0b274f000-2ba0b2751000 rw-p 00154000 03:03 1815111                    /lib/libc-2.6.1.so
2ba0b2751000-2ba0b2757000 rw-p 2ba0b2751000 00:00 0 
2ba0b2757000-2ba0b276d000 r-xp 00000000 03:03 1815187                    /lib/libpthread-2.6.1.so
2ba0b276d000-2ba0b296c000 ---p 00016000 03:03 1815187                    /lib/libpthread-2.6.1.so
2ba0b296c000-2ba0b296e000 rw-p 00015000 03:03 1815187                    /lib/libpthread-2.6.1.so
2ba0b296e000-2ba0b2972000 rw-p 2ba0b296e000 00:00 0 
2ba0b2972000-2ba0b2974000 r-xp 00000000 03:03 2748452                    /usr/lib/libXau.so.6.0.0
2ba0b2974000-2ba0b2b73000 ---p 00002000 03:03 2748452                    /usr/lib/libXau.so.6.0.0
2ba0b2b73000-2ba0b2b74000 rw-p 00001000 03:03 2748452                    /usr/lib/libXau.so.6.0.0
2ba0b2b74000-2ba0b2b79000 r-xp 00000000 03:03 2748463                    /usr/lib/libXdmcp.so.6.0.0
2ba0b2b79000-2ba0b2d78000 ---p 00005000 03:03 2748463                    /usr/lib/libXdmcp.so.6.0.0
2ba0b2d78000-2ba0b2d79000 rw-p 00004000 03:03 2748463                    /usr/lib/libXdmcp.so.6.0.0
2ba0b2d79000-2ba0b2d7a000 rw-p 2ba0b2d79000 00:00 0 
2ba0b2d7a000-2ba0b2d7c000 r-xp 00000000 03:03 1815130                    /lib/libdl-2.6.1.so
2ba0b2d7c000-2ba0b2f7c000 ---p 00002000 03:03 1815130                    /lib/libdl-2.6.1.so
2ba0b2f7c000-2ba0b2f7e000 rw-p 00002000 03:03 1815130                    /lib/libdl-2.6.1.so
2ba0b2f7e000-2ba0b2f80000 rw-p 2ba0b2f7e000 00:00 0 
2ba0b2f80000-2ba0b3cdf000 r-xp 00000000 03:03 1488043                    /usr/lib/dri/fglrx_dri.so
2ba0b3cdf000-2ba0b3dde000 ---p 00d5f000 03:03 1488043                    /usr/lib/dri/fglrx_dri.so
2ba0b3dde000-2ba0b3f96000 rw-p 00d5e000 03:03 Aborted (core dumped)

```

---

### Post by grouder on 2007-10-26
I have the same problem as flawedreality5.

fgl_glxgears 
Using GLX_SGIX_pbuffer
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't get an RGBA, Double-buffered visual

Any Idea?

---

### Post by enquiry on 2007-10-28
I got it working following the howto. Unfortunately videos and the 3d screen savers get all screwed up. Guess we'll just have to wait for better drivers from ATI.

---

### Post by Qualsdad on 2007-10-28
It seems as though the wind has to be blowing just right to get an ATI card to use AIGLX with 8.4.2.  I've spent a great deal of time trying and all I got was a white screen.  But i've found a very very simple solution to the problem.  Buy an Nvidia card, swap it with the ATI and presto!  I had a Radeon 9800 pro and I replaced it with a $50 Nvidia 6200 256mb.  I didn't even have to do anything to get it to work.  It just did!  Not only did it work, but it way out performed the 9800.  I'm very happy that compiz is working, but very sad that I waisted so much of my time with the ATI card.

Cheers!

---

### Post by obiwankamote on 2007-12-20
Hi guys, Try checking out [Forlong's blog ]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support"). It solved my problems. Actually it was just the last part. (#12). Hope this helps you guys. Thanks forlong :D

---

### Post by dark_harmonics on 2007-12-20
> **dannns said:**
> Hi, I had to run the remove script to remove my previous try of installing an ATI driver, it seemed to have done a good job.


Now I was able to install the new driver, however I still can't start compiz on my HD2600XT. And I don't understand the following message that appears when I try fglrxinfo, and similar stuff appears if I try to start compiz from the terminal.

Does any body have any clue of what this means?



I have seen posts all over the internet about this same problem (and in this same forum). So far i havent discovered any fixes for this. It happens when you run Dual-Head configurations with the new ATI drivers. To run Dual-Head I actually downgraded back to the 8.40 driver and use dual XGL sessions. 

Hopefully ATI can address this? I did submit a complaint email to them about it hoping that they might incorporate a fix into the next linux drivers release.

---

### Post by prince_niceguy on 2007-12-22
way to go... you guide was smooth... thanks... now no problems viewing the movies...
aiglx is way better than xgl...

thanks a ton!!!!!

---

### Post by glantucan on 2007-12-30
Hi, 
I followed a similar howto to yours
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I did essentially the same but creating a .deb package.
I didn't install compiz yet.

It worked fine:
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700
OpenGL version string: 2.1.7170 Release
```
and glxinfo says direct rendering is working.

But I get these warnings on   /var/log/Xorg.0.log :
```
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
...
```

Is that normal?
Could it be that my xorg.conf is not correct?
Is there, anyway, some tweaks to get a better fps rate?
```

Section "Module"
	# There's nothing here. Is that right?
EndSection
...
Section "Device"
	Identifier  "ATI Technologies Inc RV410 [Radeon X700 (PCIE)]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:2:0:0"
EndSection
```

Thanks in advance
Cheers

---

### Post by haydnv on 2008-01-13
Same problem with whitescreen here on my 1G macbook pro - anyone know of a fix?

---

