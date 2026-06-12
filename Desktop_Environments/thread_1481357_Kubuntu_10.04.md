---
title: "Kubuntu 10.04"
date: 2010-05-12
forum: Desktop Environments
---

### Post by linuxone on 2010-05-12
Hi,

Kubuntu 9.10 did run perfectly, no problems. Because this was an old system with several dist-upgrades, I deceided to buy a new hard disc and do a new installation for Kubuntu 10.04. Unfortunately I have a number of disturbing problems and can't find a solution. Any hint is welcome.

My system:
Intel Quadcore CPU Q6600 CPU
graphics: **Nvidia 9800 GTX+**
graphics driver: Nvidia-current (Ubuntu version 195.36.15) installed
X-Server config for Twinview (2 Monitors)
using Kubuntu 10.04 64-Bit
all currently available updates installed


#1 **Boot KDE**
After power on KDE hangs during boot. I see a blue KDE screen and nothing happens - even after waiting 30 minutes. No choice to switch to a Console terminal, I must use Reset and try it again. Mostly the 2nd or 3rd booting is successfull.

This should be the main error from kdm.log, see attachment:

```
Fatal server error:
xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call
```

ibus is installed. Twinview config was created from nvidia-settings.

#2 **Shutdown KDE**
KDE will not shutdown. Shutdown begins but does stop with a black screen and running computer. No choice to switch to a console terminal. I must press Power-off until the computer stops.
I can't find any notice into the log files related to this problem. IMO both problems could have the same reason.


#3 **Compiz fails, slow KDE system**
After launching KDE a system notice appears: Compiz is not usable and switched off. For a few minutes KDE seems to be frozen, no key press is accepted, nothing is usable. After displaying the notice the system is usable but slow.
Sometimes the Compiz notice appears again and the system is frozen for a
short time again.

Compiz wasn't installed automaticly. I installed it manually but the problems does happen several times each day.

Until Kubuntu 9.10 I had absolutly no KDE nor graphics problems. I could use any Compiz feature, destroying window and anything else, no freeze, no crash, everything works perfect.

I can't find any log entry for this problem. Using the current Nvidia driver and having an Nvidia 9800 GTX+ card, any graphics effect should be usable.

Any idea how I could solve these problems? Thanks!

Thomas

---

### Post by kellemes on 2010-05-12
Guess you installed your graphics-driver? (Kmenu -> System -> Hardware Drivers)
If so.. have you looked at /var/log/Xorg.0.log(.old) for hints about graphics-driver issues?
You have a special reason you use Compiz instead of Kwin for the special effects?
Is Kwin giving you the same trouble? Kwin is more stable and offers (almost) all Compiz-effects.
You can switch Window Manager like so..
KMenu -> Settings -> System Settings -> Default Applications -> Window Manager..

---

### Post by linuxone on 2010-05-14
Hi,

> **kellemes said:**
> Guess you installed your graphics-driver? (Kmenu -> System -> Hardware Drivers)
If so.. have you looked at /var/log/Xorg.0.log(.old) for hints about graphics-driver issues?

Xorg.0.* doesn't contain any usefull entries. Only kdm.log, see first post above.

> You have a special reason you use Compiz instead of Kwin for the special effects?

I installed compiz due to the error message ...
"*KDE Window Manager. Composite-System is too slow and will be stopped. If this is only a temporary problem you can continue Compositing by pressing Alt+Shift+F12.*"
and because it wasn't installed.

> Is Kwin giving you the same trouble? Kwin is more stable and offers (almost) all Compiz-effects.

I installed Kwin but got the same problems, again the Composite slow message and fails to shutdown. Kwin is the active Window manager.

Any other ideas?

Thomas

---

### Post by dabl on 2010-05-14
9800 GTX is a nice card -- it should work better than this.

I would first recommend this:

```
sudo apt-get remove --purge compiz
```

You need to have a smooth-running KDM and KDE before you install or configure compiz.

The KDM hang on booting is a sign that there's a problem with the driver installation, or else with the xorg.conf screen configuration.  I can't tell what the problem is.

I'm going to commit heresy and suggest you try (a) disabling the official System > Hardware Drivers version of the Nvidia driver (the glx package).  Then if you follow this guide you can download and install the 195.36.24 driver, which is what I'm running.  

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

If doing that does not solve the KDM problem, then it just about has to be some issue with your screen/monitor configuration in xorg.conf, and that is very specific to your display.

Hope this helps.

---

### Post by shaka_zulu on 2010-05-14
Did you try Kubuntu 10.04 Live version before installation? How did you install it from CD or some USB device?

---

### Post by kio_http on 2010-05-15
Did you install the updates?;)

---

### Post by linuxone on 2010-05-15
Thanks for your answers.

I'll replace the Ubuntu version of the Nvidia driver with the original driver.

Installation was done by using the CD ISO image. First time I used the Linux based installer - usually I prefered the Alternate CD with the much faster text based installation and more features to configure. (like encryption)

All current available updates are installed.

By the way ... in the meantime I explored some more problems. For example the system doesn't see any CD drive. This seems to be a problem between Kernel and Virtualbox. I'll check this more deeper when KDE is running.

Thomas

---

### Post by linuxone on 2010-05-15
Hi.

> **dabl said:**
> I'm going to commit heresy and suggest you try (a) disabling the official System > Hardware Drivers version of the Nvidia driver (the glx package).  Then if you follow this guide you can download and install the 195.36.24 driver, which is what I'm running.

using the original graphics driver from Nvidia the KDE/KDE problems seems to be solved. I tried a few Logout and Shutdown/Reboot and each time Kubuntu did what it should do. The Composite error message didn't appear again until now. Kwin is still the default Window manager. 

I still noticed a system freeze each time when launching Virtualbox, but I guess this a different problem.
And the mentioned CD drive problem has nothing to do with Virtualbox, the drives were gone lost short time after booting, no matter if Virtualbox is installed or not. This needs some deeper verifications, regarding the existing bug reports in Launchpad.

Thanks for help.
Thomas

---

### Post by kellemes on 2010-05-16
> **linuxone said:**
> I still noticed a system freeze each time when launching Virtualbox

Great you fixed some problems..
Personally I always installed the Binary Edition (not the Open Source Edition) of Virtualbox from it's website (not the Ubuntu repo) and although I currently don't have it installed I never had trouble with it, as far as I remember.
[Binary VB Edition downloads]("http://www.virtualbox.org/wiki/Linux_Downloads").

P.s: Running from cli may give some hints?

---

### Post by linuxone on 2010-05-16
Hi,

> **kellemes said:**
> Personally I always installed the Binary Edition (not the Open Source Edition) of Virtualbox from it's website (not the Ubuntu repo) and although I currently don't have it installed I never had trouble with it, as far as I remember.

in the meantime I did install Virtualbox 3.1.8 Binary, I want to test the new release and it didn't come as update. Because this didn't solve the Vbox problems I upgraded the VBox 3.2 Beta 3, but this also won't fix the freeze problem. And still no sound within Virtual Machines.

> P.s: Running from cli may give some hints?

right ...

```
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
Qt WARNING: QFileSystemWatcher: failed to add paths: /root/.config/ibus/bus
Qt WARNING: Bus::open: Can not get ibus-daemon's address.
```

but this doesn't help really. I did install ibus, which wasn't installed automaticly, but also this doesn't help and the same error appears again.

To be honest - I can't remember to have such strange problems since many years. I know, basic changings and new features may cause problems. But not so dramaticly serious problems :icon_frown: :

I can't use my CD drives nor burn any CD/DVD. I need to reboot to a previous Kubuntu version.

Right after installation I had serious Filesystem errors, which causes an automatic readonly re-mount with errors. This was caused by mounting an additional ext3 partition, I solved this by converting ext3 to ext4. Fortunately no corrupted data.

Kontact/KMail still reports an missing resource agent (brand new, fresh installation!). :confused: IMO all needed packages were installed and the Akonadi FAQ didn't help yet. Still had no time to explorer this, KMail is usable after appr. 2 minutes after launching (after displaying the error message), so it's disturbing but not urgent.

And sound does work only for a few minutes after booting. Then an error message appears "Photon sound .. doesn't work" ... no sound anymore. I've an expensive Asus board with Nvidia chipset and had no sound nor CD/DVD nor KDE/Xorg problems before.
Need some free time to explore also this issue, maybe later this month if I will really keep Kubuntu 10.04 alive. Maybe it's better to go back and wait til october? :(

Thomas

---

