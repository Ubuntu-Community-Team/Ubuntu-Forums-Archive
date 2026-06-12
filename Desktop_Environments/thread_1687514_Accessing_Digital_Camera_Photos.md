---
title: "Accessing Digital Camera Photos"
date: 2011-02-14
forum: Desktop Environments
---

### Post by razvanc87 on 2011-02-14
Hello all.

I tried finding information about this issue, but it seems that I hit a wall every time I try this.

I have a:
Bus 002 Device 015: ID 04cb:01bf Fuji Photo Film Co., Ltd FinePix F6000fd/S6500fd Zoom (PTP)
camera and I am trying to get it working with Ubuntu. I started having this issue from Ubuntu 10.04 (included), now I am on 10.10 with the same problem.

When I start F-Spot and try to access the camera from the import button it says: Received error "Could not lock the device" while connecting to camera.

And /var/log/messages gives this:
Feb 14 09:50:30 razvan-desktop kernel: [ 3845.808959] usb 2-3: new high speed USB device using ehci_hcd and address 16
Feb 14 09:50:30 razvan-desktop kernel: [ 3845.962084] usb 2-3: configuration #1 chosen from 1 choice
(in dmesg there is no entry about the camera whatsoever, no sd.. not nothing, and of course there appears no icon on the desktop / nautilus to interact with; preferences from nautilus are: "Ask what to do", which does nothing...)

Also, starting f-spot from the terminal gives this error:
Error Lock: LibGPhoto2.GPhotoException: Could not lock the device
  at LibGPhoto2.Error.CheckError (ErrorCode error) [0x00000] 
  at LibGPhoto2.Camera.Init (LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.InitializeCamera () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
cleanup context

I have no idea what to do anymore...

Hopefully there is someone there that can help me, thank you.

---

### Post by bergamot on 2011-02-14
I can't help you with the USB, but might I suggest you take the SD card out and plug that into the computer instead? If you don't have an SD card reader, you can get USB ones for <£10. It'll be much faster than accessing the camera by USB cable too.

Sorry if you've already though of this and have reasons for not doing it... ;)

---

### Post by razvanc87 on 2011-02-15
Yes, well... the thing with this solution is that it doesn't solve the software problem, which in my opinion is important. (I thought about it yes, but I was waiting for a solution, because this problem... appeared which means that prior to version 10.04 there was no problem and I thought that it is not that difficult to revert / check out the older code of the kernel that worked).

The thing is... If we are going to buy new Hardware for things that do not work in Linux, then we might as well go back to Windows... (which by the way I don't want to)... I want to make Linux work :)

But thanks for the reply at least.

---

### Post by inobe on 2011-02-15
> **razvanc87 said:**
> I want to make Linux work :)

unplug camera, install digikam in synaptic.

come back to tell us if it works.

---

### Post by razvanc87 on 2011-02-15
I doubt that this will work, but I'll give it a go after I get home. Thanks for the idea.

---

### Post by inobe on 2011-02-15
> **razvanc87 said:**
> I doubt that this will work, but I'll give it a go after I get home. Thanks for the idea.

my camera doesn't work without it, this guy had the same problem.

[http://ubuntuforums.org/showthread.php?p=10456595#post10456595](http://ubuntuforums.org/showthread.php?p=10456595#post10456595)

lets see what it does, if nothing, we can try some other things.

---

### Post by razvanc87 on 2011-02-17
So.. I finally could try the digikam thing.

As I suspected, this also doesn't work, and this application doesn't give any information about what's going on (in the terminal), I get only this:

[[IMG]http://img576.imageshack.us/img576/4007/screenshotthx.th.png[/IMG]](http://img576.imageshack.us/i/screenshotthx.png/)

If you have any ideas... or know of workaround for this bug (except card-readers)... please help? :)

---

### Post by inobe on 2011-02-17
open digikam via terminal by typing **digikam** then hitting enter.

now connect camera.

copy and paste the end results from terminal.

edit: once digikam is up, click import, hover over cameras, select camera!



i get no errors, example of my terminal output

```
linux-boss:~$ digikam
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
QSqlDatabasePrivate::removeDatabase: connection 'ConnectionTest' is still in use, all queries will cease to work.
Time elapsed: 85 ms
Model: Time elapsed: 0 ms
TextureColorizer::setSeaFileLandFile: Time elapsed: 15 ms
Time elapsed: 22 ms
Model: Time elapsed: 0 ms
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/duane/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
TextureColorizer::setSeaFileLandFile: Time elapsed: 8 ms
digikam(15371)/KIPI (general) Plugin_DebianScreenshots::setup: virtual void Plugin_DebianScreenshots::setup(QWidget*) 
Time elapsed: 8 ms
Model: Time elapsed: 1 ms
TextureColorizer::setSeaFileLandFile: Time elapsed: 8 ms
Time elapsed: 6 ms
Model: Time elapsed: 0 ms
TextureColorizer::setSeaFileLandFile: Time elapsed: 8 ms
Time elapsed: 6 ms
Model: Time elapsed: 0 ms
TextureColorizer::setSeaFileLandFile: Time elapsed: 8 ms
digikam(15371)/digikam (core) Digikam::StateSavingObjectPriv::getGroupFromObjectName: Object name for  Digikam::ImagePropertiesSideBarDB(0x97cb690)  is empty. Returning the default config group 
digikam(15371)/digikam (core) Digikam::StateSavingObjectPriv::getGroupFromObjectName: Object name for  Digikam::ImagePropertiesSideBarDB(0x9c96540)  is empty. Returning the default config group 
QPainter::begin: Widget painting can only begin as a result of a paintEvent
QPainter::setFont: Painter not active
QPainter::fontMetrics: Painter not active
QPainter::setPen: Painter not active
QPainter::setBrush: Painter not active
Time elapsed: 6 ms
Model: Time elapsed: 0 ms
TextureColorizer::setSeaFileLandFile: Time elapsed: 8 ms

```

---

### Post by razvanc87 on 2011-02-17
it actually sais nothing of interest:

razvan@razvan-desktop:~$ digikam
Time elapsed: 12 ms
Time elapsed: 2 ms
Model: Time elapsed: 38 ms
TextureColorizer: Time elapsed: 9 ms
Time elapsed: 2 ms
Time elapsed: 2 ms
Model: Time elapsed: 7 ms

---

### Post by inobe on 2011-02-17
have you noticed my edit?

i left out some details.

connect camera, once digikam is up, click import, hover over cameras, select camera!

now copy and paste the end results from terminal.

---

### Post by razvanc87 on 2011-02-17
hopefully this will help you... help me :):

```

razvan@razvan-desktop:~$ digikam
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Time elapsed: 115 ms
Time elapsed: 3 ms
Model: Time elapsed: 167 ms
TextureColorizer: Time elapsed: 61 ms
Time elapsed: 2 ms
Time elapsed: 2 ms
Model: Time elapsed: 7 ms
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_digikamdates.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
klauncher(6269)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(6269)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(6269)/kio (KLauncher): SlavePool: No communication with slave. 

kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
Time elapsed: 3 ms
Time elapsed: 2 ms
Model: Time elapsed: 8 ms
kdeinit4: preparing to launch /usr/bin/knotify4
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
knotify(6337) KNotify::event: 1  ref= 0

```

edit: I don't know what happened.... But after a quick server X kill, the kernel now detects the camera as it should have and I can access it from nautilus, although... digikam still gives the same error. WT...?

---

### Post by razvanc87 on 2011-02-17
Unfortunately.... I cannot reproduce this camera accessing... again. I don't know what happened, it just worked after a kill of X and then it stopped working again..

edit: I think I'm giving up, it gives me headaches

---

### Post by inobe on 2011-02-17
hang in there, i will do my best.

---

### Post by inobe on 2011-02-17
> **razvanc87 said:**
> Unfortunately.... I cannot reproduce this camera accessing... again.


this may seem irrelevant, but do you have other user accounts?

bare with me a bit more, if your exhausted, i'll see you tomorrow, till then i will research this.

---

### Post by razvanc87 on 2011-02-17
I have tow computers (the one at my work - PC and the one back home - laptop). The one on my work has 2 users (on Ubuntu 10.04) and the one back home has only one user (on Ubuntu 10.10). They both experience the same problem...

> **beardala said:**
> Take the memory card out, then plug it into the computer.You should then olny have the files on the camera itself.
my PC does not have a card reader for XD cards.

---

### Post by inobe on 2011-02-17
this is a command from an old bug, disconnect camera and run

```
sudo killall gvfs-gphoto2-volume-monitor
```

the command will not make any changes permanent, everything will start back up on reboot.

lets give it a go, if the camera works, i will find a permanent solution.

run the command and connect the camera.

---

### Post by razvanc87 on 2011-02-17
> **inobe said:**
> this is a command from an old bug, disconnect camera and run

```
sudo killall gvfs-gphoto2-volume-monitor
```

the command will not make any changes permanent, everything will start back up on reboot.

lets give it a go, if the camera works, i will find a permanent solution.

run the command and connect the camera.

Sorry, it seems that it isn't that easy. No luck. Still the same thing even with this command.

---

### Post by inobe on 2011-02-17
okay, so that you know, i'm researching the error, could not lock device.

i found similar errors and some cameras worked after **gvfs-bin** is installed.

is gvfs-bin installed?

also, if the cam is mounted, try unmounting then selecting again.

---

### Post by razvanc87 on 2011-02-17
I also read about those problems, which sounded familiar.

I do have **gvfs-bin** installed. Also, I cannot unmount the camera, because it is detected PTP (as I posted when I started this thread) without giving me the option to see it like a mass storage device. And by default, it does not get mounted and I cannot find any mount point (that should appear in /var/log/messages)... all of this are in the first message of this thread.

---

### Post by inobe on 2011-02-17
okay, last one for now, if cam is connected, disconnect and reconnect.

ignore or close any dialogs.

open terminal and run

```
gvfs-mount -l
```

highlight the url and copy it, example **//[usb:011,007]/**

now paste the url at the end of this command

```
$ sh -ex /usr/bin/f-spot-import gphoto2:
```

it'll look similar

```
$ sh -ex /usr/bin/f-spot-import gphoto2://[usb:011,007]/
```

run that

edit: keep in mind that i can't replicate any of these commands because i have kubuntu, if you have a problem due to typo comment out $ and space.

---

### Post by razvanc87 on 2011-02-17
I forgot to mention it, I also found the bug where this procedure was shown and I tried it, but I don't have any info given by gvfs-mount that can be used:

```

[b]razvan@razvan-desktop:~$ gvfs-mount -l
Drive(0): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)[/b]
razvan@razvan-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 002: ID 045e:0750 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 023: ID 04cb:01bf Fuji Photo Film Co., Ltd FinePix F6000fd/S6500fd Zoom (PTP)**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I think no further explanation is needed...

---

### Post by inobe on 2011-02-17
> **razvanc87 said:**
> I forgot to mention it, I also found the bug where this procedure was shown and I tried it, but I don't have any info given by gvfs-mount that can be used:


you plugged in camera and ignored the dialog or closed it?

if yes, i will be back on after 6pm eastern.

your first post you stated

> I started having this issue from Ubuntu 10.04

it worked prior?

---

### Post by razvanc87 on 2011-02-17
> **inobe said:**
> you plugged in camera and ignored the dialog or closed it?

There is no dialog that appears when the camera is plugged in. Nautilus is set to "Ask what to do" for all media type except Software, which I don't think it has any influence.

> **inobe said:**
> it worked prior?
Yes it did with the hole dialog thing etc. + f-spot + browse photos directly from the camera folder.

---

### Post by razvanc87 on 2011-02-18
Sorry for pushing this in front but I'm still waiting to see if there is someone there that may have an ideea about this issue...

---

### Post by inobe on 2011-02-18
i have been looking around and can't find anything, it's almost like your the only one with that camera.

but here are some options.

you could enable the backports repo, except you could experience both bad and good from it.

the good, it offers the patches for serious bugs that usually get fixed for next release, natty for example, well you can get them now with backports.

the bad, you may get some bugs that escaped testing, most tested apps are stable enough, some manage to slip threw untested.

you can enable the entire repo, or search for individual files, in your case, it could be anything from kernal modules to buggy apps.

read about it here [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

another would be to go back to 9.10 and stick with that till natty's release in less than two months.

---

### Post by razvanc87 on 2011-02-18
Well, I tried to find about this problem for about 1 year, just this few days ago I started this tread because I couldn't find any solution. But just now, I tried on Maverick (on my home laptop) just a few minutes ago and it worked... without me doing anything (just updates)... probably one of those corrected this problem (and I'm not using backports).

Thanks anyway for the support.

For Ubuntu Lynx (on my work PC) this issue is not resolved, but I don't really care about that any more.

So I will mark this as SOLVED (for the sake of Maverick).

---

