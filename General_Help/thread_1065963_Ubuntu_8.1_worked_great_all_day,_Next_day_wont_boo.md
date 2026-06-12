---
title: "Ubuntu 8.1 worked great all day, Next day wont boot...(after loadscreen)"
date: 2009-02-10
forum: General Help
---

### Post by JDMB20TDA on 2009-02-10
I am now running it in live mode inorder to post this message.
computer specs:
amd sempron 3200+
ati radeon x1300pro
1.2g ram
1 main linux HDD, 2 other ntfs mountable drives.
I have tried:
sudo dpkg-reconfigure xserver-xorg and It gives me no graphics option past the first menu, all keyboard options.
startx; gives me a fatal server error.
Ive modified the boot kernal at the boot os screen to (delete quiet) and nosplash, it seems to get further in the loading process, but never to the login.

The black screen doesnt go away unless I cntl+alt+f# and then prompts me to login.

I had installed the ati drivers for the card and changed a few display options in bizcomp(sp?), then shut it down.
Upon restarting it today it wont load anything.
hope this is a common or known issue, thanks in advance.

---

### Post by JDMB20TDA on 2009-02-10
I am now able to run the ubuntu off the boot drive, I ran partion editor check on the drive and it said it was ok, and I am now able to boot.
Does that sound right or will this be a reoccuring problem?
I did notice before I had all the special effects on using compiz, and now it is disabled and back to "simple" mode.
Could this be the cause of the problem?
the Ati driver I had downloaded for the x1300 pro card is also inactive.

---

### Post by JDMB20TDA on 2009-02-10
What test could I run to determine the cause of the no boot.
I am going to reinstall the ati driver.
is there another driver from ATI I maybe able to download instead of running the suggested ubuntu driver.

---

### Post by jonlemur on 2009-02-10
I'm using the xorg-xserver-video-radeon driver and it's working well for me.  I switched to it so I could use compiz with my dual monitors, and I'm pretty pleased with it.  It's not as fast as the fglrx driver that I had, but that may very well be because its working twice as hard with the second monitor.  Compiz is working though with dual monitors and the ATI Radeon X600 card.

---

### Post by JK3mp on 2009-02-11
You mean 8.10?

---

### Post by JK3mp on 2009-02-11
> **JK3mp said:**
> You mean 8.10?

nvm :( dumb question.

---

### Post by JDMB20TDA on 2009-02-12
How could I revert back to the original video driver?
I was configuring my dual monitor setup when the screen went all corrupted then didnt show anything but snow/colors.
I restarted it and am now running off the live cd, Ive tried all the option in recover consule and xserver fix still nothing.

---

### Post by jonlemur on 2009-02-12
I would try ```
sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure -phigh xserver-xorg
``` and restart or just start the x server (startx).  That should reinstall the driver, unless you're wanting to avoid fglrx.

---

### Post by JDMB20TDA on 2009-02-12
would there be any reason to avoid that particular driver?
I figured I was just going to reinstall the driver I had before and try to figure out exactly what causes it to go bad.
Thanks for the help.

---

### Post by jonlemur on 2009-02-12
The main reasons to avoid it are 1.) it's closed source, so it's not supported by the Ubuntu community, and  2.) you can't get dual monitors working with it.  I used it very happily for a couple of years, switching only recently to the open-source drivers for dual monitor support.  I think fglrx is supposedly faster than the open-source drivers, so if you don't have dual monitors, I would recommend it.

---

### Post by JDMB20TDA on 2009-02-13
unfortunatly I run this computer as my home theater and clone the display to a TV.
So if that cannot be enabled I will have to find something that is a bit more stable.

---

### Post by jonlemur on 2009-02-13
You can clone the screen with fglrx, just not have different displays on both.  I'm also not sure how easy it is to set up different resolutions for your computer and your TV.  I would at least try fglrx, if that doesn't work, you would just have to uninstall fglrx, and maybe add ```
# prevent the fglrx driver from loading into the kernel
blacklist fglrx
``` to /etc/modprobe.d/blacklist
Then (if you're not using fglrx) in /etc/X11/xorg.conf, you need something like: ```
Section "Device"
        Identifier      "Configured Video Device"
        Driver "ati"
        BusID "PCI:1:0:0"
EndSection

``` I don't know if you need the BusID part, but if you do, you can make sure you have the right PCI thing by running ```
lspci | grep VGA
``` For me, that gave ```
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
```  Note that the 01:00.0 had to be formatted as PCI:1:0:0 in xorg.conf.

---

### Post by JDMB20TDA on 2009-02-13
All I do is run a cloned display and at the same resolution and that shouldnt be a problem then.
I will give that a try as soon as Im back from work and let you know how it goes.
Thanks for all the help, Im new to all this and I appreciate you spending the time to help me out.

---

### Post by JDMB20TDA on 2009-02-13
It says the fglrx, is currently installed, upgraded and does nothing different.
How could I reload the stock drivers and then Ill try switching some settings in the fglrx driver to avoid it not booting the GUI...
or giving me nothing but black screen until I cntrl alt F1.

---

### Post by jonlemur on 2009-02-14
The stock drivers are probably still installed.  I think they are xserver-xorg-video-radeon and xserver-xorg-video-ati, so you can check in synaptic to see if they're installed, and you can even reinstall them.  Probably the best way to avoid using fglrx is to go to System->Administration->Hardware Drivers and disable the ATI fglrx driver there.

---

### Post by JDMB20TDA on 2009-02-14
I cant access the gnome desktop.
I get a black screen after kernal begins loading then I have to cntrl+alt+F1 to login and access terminal.
so there is no way I could system/admin/hardware; Right now im using the live cd to access the internet.

Xorg.conf and a few other commands do not work, Unless Im doing something completely wrong.

---

### Post by jonlemur on 2009-02-14
Try ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```  This will make it so Ubuntu will try to autodetect everything.  Make sure fglrx is uninstalled (unless you want to try it) with ```
sudo apt-get remove xorg-driver-fglrx
```  And just to make sure that fglrx doesn't try to get loaded into the kernel, ```
su
(enter root password, if it's not set, you may be able to use your password)
echo "blacklist fglrx" >> /etc/modprobe.d/blacklist
exit
```  You may have to set the root password before you can run the above command.  Do this with sudo passwd and follow the prompts.  Then make sure the open-source drivers are installed with ```
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install xserver-xorg-video-radeon
```  Then reboot and see what happens.

---

### Post by JDMB20TDA on 2009-02-14
I reinstalled windows as I needed to use the computer.
But I will be dual booting as of tonight.
So I will avoid running that driver, Im just suprised no one has had a similar problem or a fix so that it can be used.
thanks for all the help I will reply back when everything is running back to normal.

---

### Post by owtlaw on 2009-02-15
I just installed ubuntu 8.10 and the same thing happened to me.
It installed fine, then rebooted and when the loading screen goes away, the monitor looses signal.
i have an older ati radion

i am a newb at linux whatcan i do to fx this?

---

