---
title: "Digikam hotplug mini-HOWTO"
date: 2006-01-16
forum: General Help
---

### Post by olale on 2006-01-16
I was trying to use the hotplug scripts for launching digikam (linked from the howto on [http://digikam.free.fr/hotplug/howto.html](http://digikam.free.fr/hotplug/howto.html)) but couldn't get it to work straight away. However, after debugging the launch process yesterday I found out a few potential problems and found fixes that worked for me so I thought I'd share my experience.

Whenever my digital camera is connected to my computer via a USB cable, I want digikam to launch automatically and show me the photos available so that I can download them straight away with a minimum of hassle.

Now, if the instructions on [http://digikam.free.fr/hotplug/howto.html](http://digikam.free.fr/hotplug/howto.html) don't work straight away, try follow those I give here and see if that helps:

Whenever a USB device is connected to the computer, the script /etc/hotplug/usb.agent tries to find config scripts in /etc/hotplug/usb/ by looking at the various files named*.usermap which tell the agent how to initialize usb devices. The lines in each usermap file map a "driver", or config script, to a hotplug device. Each file lists a number of devices, and more than one may list a specific device, if there are several configurations that need to be done for it.

Now, in my case I had already files called libgphoto2 and libgphoto2.usermap after installing digikam and all required packages for it.

The instructions on digikam.free.fr told me to run 

```
/usr/lib/libgphoto2/print-usb-usermap > /etc/hotplug/usb/usbcam.usermap

```

in order to obtain a usermap for my digikam hotplug scripts. This won't work straight away however, because the print-usb-usermap script produces a usermap that lists libgphoto2 as the driver for all usb cameras, and we already have the libgphoto2 installed. What we want is to have an additional script run the and launch digikam for us. The usb.agent script doesn't care that the usermap is called usbcam.usermap, it only looks at the contents of the file and will discover that camera is supposed to be handled by a file called "libgphoto2", which, coincidentally, already exists!

The solution is to replace all occurrences of "libgphoto2" with "usbcam" in usbcam.usermap. The print-usb-usermap script should already have run during the installation of libgphoto2 and given you /etc/hotplug/usb/libgphoto2.usermap as I mentioned above.

Take this file and produce a new one by using the commands

```

sudo bash
sed -e 's/libgphoto2/usbcam/g' /etc/hotplug/usb/libgphoto2.usermap >/etc/hotplug/usb/usbcam.usermap 
exit

```

Now unpack the tarball with the two hotplug scripts from digikam.free.fr ([http://digikam.free.fr/hotplug/usbcam.tar.gz)](http://digikam.free.fr/hotplug/usbcam.tar.gz)). Choose the scripts with version numbers 0.3.2 since they work with the Kubuntu version of digikam.

Put the digikam-hotplug.0.3.2 and usbcam.0.3.2 into /etc/hotplug/usb/ directly, not in a subdirectory usbcam. Rename the scripts to digikam-hotplug and usbcam, respectively.

Now all we have to do is making these scripts work properly, which they didn't do for me.

Look for a section of the usbcam script where you find this:

```
CMD=`ps -ef |grep kdeinit..kdesktop`
log 3 "ps -ef |grep kdeinit..kdesktop: ${CMD}!"
USER=`ps -ef |grep "kdeinit..kdesktop" |grep -v grep |awk '{print $1}'`

```

Replace it with

```
CMD=`ps -eo user,fname | grep kdesktop`
log 3 "ps -eo user,fname | grep kdesktop: ${CMD}!"
USER=`ps -eo user,fname | grep kdesktop | awk '{print $1}'`

```

so that the script knows which user is currently running KDE on your computer (hopefully only one).

Look for a section in the digikam-hotplug script that says

```
system("DISPLAY=$display digikam --detect-camera 1>/dev/null 2>/dev/null&");

```

This will launch digikam, but not use your own locale setting. This is too bad, since I like all applications to use the same language. As an ugly workaround, find out which language setting you use by executing

```
env|grep LANG

```

On my system, that gives me

```
LANG=sv_SE.UTF-8

```

Prepend that to the launch command above, which in my case became

```
system("LANG=sv_SE.UTF-8 DISPLAY=$display digikam --detect-camera 1>/dev/null 2>/dev/null&");

```

When this is done, just make sure the following is correctly set up:
[LIST]
[*] The script /etc/hotplug/usb/digikam-hotplug is owned by the group users and executable by the group.
[*] The script /etc/hotplug/usb/usbcam is owned by root and only executable by root.
[/LIST]
Now, it should work to plug in your camera and have digikam launch automatically!

If it doesn't, check the debugging messages in syslog by:

```
sudo tail /var/log/syslog

```

---

