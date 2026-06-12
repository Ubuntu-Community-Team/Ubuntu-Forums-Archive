---
title: "ATI Driver install help"
date: 2009-01-12
forum: General Help
---

### Post by kerbanoba on 2009-01-12
Hi there

I have just downloaded and ran ATI drivers for my laptop using the command

cd ~/Desktop
chmod 755 ati-driver-installer-8.34.8-x86.x86_64.run
sudo ./ati-driver-installer-8.34.8-x86.x86_64.run

It brought up the user interface, and appears to have installed
however,  when I go into hardware drivers, it still shows the old driver
installed.

Futhermore, I am unable to access aticonfig.

Any help is appreciated!

Cheers

---

### Post by mryerse on 2009-01-12
I used the --listpkg option to see that I could build the package for Ubuntu/8.10 with the --buildandinstallpkg option.  That worked for me, although I think there is a newer driver available somehow.

---

### Post by kerbanoba on 2009-01-12
How do I find out if there are newer drivers? or go about using the list package option? I am pretty new with ubuntu :P

Thanks

---

### Post by hangfire on 2009-01-12
> **kerbanoba said:**
> Hi there

I have just downloaded and ran ATI drivers for my laptop using the command

cd ~/Desktop
chmod 755 ati-driver-installer-8.34.8-x86.x86_64.run
sudo ./ati-driver-installer-8.34.8-x86.x86_64.run

It brought up the user interface, and appears to have installed
however,  when I go into hardware drivers, it still shows the old driver
installed.

Futhermore, I am unable to access aticonfig.


Unless the proprietary ATi driver download is a Debian/Ubuntu package, it is unlikely to show up as installed. Checking the contents of file **/etc/X11/xorg.conf** will show you if anything is there. There should be a backup file of your original xorg.conf.*something* in the same directory.

aticonfig may be somewhere not in your path. Try

```
locate aticonfig
```

I hope you have a recent ATi card. Futzing around with older 9xxx cards and newer drivers seems to be pointless.

-HF

---

### Post by kerbanoba on 2009-01-12
Alright I tried locating the driver and got this:

/etc/acpi/events/fglrx-ac-aticonfig
/etc/acpi/events/fglrx-lid-aticonfig
/usr/bin/aticonfig
/usr/share/doc/xorg-driver-fglrx/examples/etc/acpi/events/a-ac-aticonfig
/usr/share/doc/xorg-driver-fglrx/examples/etc/acpi/events/a-lid-aticonfig

It is not required to be logged into root to install, as my user should have sufficient permissions, correct?

Perhaps I installed it wrong?

---

### Post by WitchCraft on 2009-01-12
```

sudo apt-get install envyng-qt

```

That will download, configure and install your ATi driver.

---

### Post by hangfire on 2009-01-12
> **kerbanoba said:**
> Alright I tried locating the driver and got this:

/etc/acpi/events/fglrx-ac-aticonfig
/etc/acpi/events/fglrx-lid-aticonfig
/usr/bin/aticonfig
/usr/share/doc/xorg-driver-fglrx/examples/etc/acpi/events/a-ac-aticonfig
/usr/share/doc/xorg-driver-fglrx/examples/etc/acpi/events/a-lid-aticonfig

It is not required to be logged into root to install, as my user should have sufficient permissions, correct?

sudo or root permissions are required, and you must have had that to install to directories like /etc/ and /usr/bin.

Doing the install from ATi/AMD is the hard way, but may give you a newer/better or more broken driver than apt-get, depending on AMD's mood on Linux that month.

If the following gives some output:

```
sudo grep fglrx /etc/X11/xorg.conf
```

...then you might be a **Ctrl-Alt-Backspace** away from enjoying your new driver. Close all programs and save all work first, as this key-chord will restart X.

-HF

---

### Post by kerbanoba on 2009-01-12
Terminal accepted the command, and it restarted, however, I am not sure if it worked.

When I look under hardware drivers, it still shows ATI/AMD Proprietary (Not sure if these are the new drivers, or are these the drivers that came with the install?

The whole reason I am trying to get these working, is because for some reason, my scroll bars are unbelievably slow.. I set the CPU to performance, and it fixed it slightly, but the problem is still there

---

### Post by hangfire on 2009-01-14
> **kerbanoba said:**
> The whole reason I am trying to get these working, is because for some reason, my scroll bars are unbelievably slow.. I set the CPU to performance, and it fixed it slightly, but the problem is still there

Please list your hardware.

-HF

---

