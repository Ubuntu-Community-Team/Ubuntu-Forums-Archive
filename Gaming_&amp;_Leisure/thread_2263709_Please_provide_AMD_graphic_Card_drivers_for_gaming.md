---
title: "Please provide AMD graphic Card drivers for gaming on UBUNTU desktop version."
date: 2015-02-02
forum: Gaming &amp; Leisure
---

### Post by mandarpowale on 2015-02-02
Hi,

I use an ASUS HD7750 1GD5 LE-V2 on my machine. I need supporting drivers for this graphic card so that I can use UBUNTU for gaming.

Hope that you will focus on this issue too.

Mandar D N Powale

---

### Post by Benjamin_Eunice on 2015-02-02
this should detect your graphics card and install your drivers: [http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86)

---

### Post by QIII on 2015-02-02
Hello!

These forums are populated by users just like you.  None of us are Canonical employees nor developers.  This is not a good place to try to get the attention of the developers.

Linux developers do not produce proprietary drivers for hardware.  OEMs do.  AMD/ATI already produces a proprietary Linux driver.

There is no need to go through the pain of downloading the driver from AMD/ATI.  It is already in the Ubuntu repos.  Just install it from there.  I recommend using the command line process I outline in the wiki in my signature.

If you install the driver from the AMD website, you will have to uninstall it every time there is a kernel update, apply the kernel update, reboot, reinstall the AMD driver, reboot.  If you install it from the Ubuntu repo, that will all happen automatically as part of your normal updates.

---

### Post by mandarpowale on 2015-02-03
Thanks Benjamin and QIII.

I have an assembled PC, not OEM :)

---

### Post by QIII on 2015-02-03
AMD is the OEM of your card.  They produce the proprietary driver for it.

---

### Post by mandarpowale on 2015-02-05
^^ Ok Thanks

Add: How to install proprietory drivers ? (they come in a zip but there is no deb file)

---

### Post by mastablasta on 2015-02-05
there is a .run script file.

---

### Post by QIII on 2015-02-05
Might I suggest going to the ATI link in my signature and following the command line instructions in section 2.1?

If you install from the direct AMD download without creating a .deb file (to make it dpkg aware), you will have to uninstall the driver before upgrading your kernel and reinstall it afterwards to avoid frustration.

The driver is available in the Ubuntu repos.

---

### Post by oldrocker99 on 2015-02-05
> **QIII said:**
> Might I suggest going to the ATI link in my signature and following the command line instructions in section 2.1?

If you install from the direct AMD download without creating a .deb file (to make it dpkg aware), you will have to uninstall the driver before upgrading your kernel and reinstall it afterwards to avoid frustration.

The driver is available in the Ubuntu repos.

If you do this before installing from the direct AMD download, you'll not have to reinstall if there is a kernel update (it works for me with the nVidia driver) if you do this first:
```
sudo apt-get install dkms
```
This will link the existing driver to any new kernel update.

---

### Post by mandarpowale on 2015-02-05
by _**Ubuntu repos.**_ do you mean UBUNTU SOFTWARE CENTER ?

*I had to install 'ATI binary x.Org driver' and a driver from 'additional drivers' of settings menu.*

---

### Post by oldrocker99 on 2015-02-05
You can install dkms from the Software Center, but read on.

The Ubuntu Software Center is one the ways you can install software, all of which is located in the Ubuntu repositories, which can be thought of as a big, free software store in the cloud. Every Linux distribution has its own set of repositories, and there are servers all over the world which can be accessed. Any Ubuntu user can find (using Synaptic's Repositories menu command--see below) the best, usually closest repository, which is the fastest for that user's physical location.

One of the coolest things about Linux is that you can also install any program you know the name of with```
sudo apt-get install (programname)
```

While the Software Center is, I guess, easy to use, I use Synaptic most of the time. Install it with```
sudo apt-get install synaptic
```

It allows you to select several programs without downloading each one at a time, instead downloading all the selected programs and installing them in one operation. It is also faster, lots faster, than the Software Center. There are some nice programs for sale (usually pretty low-priced) there, but I only use it to reinstall programs I have already bought earlier, and use Synaptic or the command line to install or remove anything else.

Please do use these forums to ask any questions, but it's a good idea to search for your problem first to see if it already has an answer. These forums are designed for us to help each other out with learning how to use Linux, which is a **BIG** upgrade from Windows.

---

### Post by Tattorack on 2015-02-06
Thanks man! I didn't know AMD had the same detection app for Linux as Windows.

---

### Post by mandarpowale on 2015-02-06
> **oldrocker99 said:**
> You can install dkms from the Software Center, but read on.

The Ubuntu Software Center is one the ways you can install software, all of which is located in the Ubuntu repositories, which can be thought of as a big, free software store in the cloud. Every Linux distribution has its own set of repositories, and there are servers all over the world which can be accessed. Any Ubuntu user can find (using Synaptic's Repositories menu command--see below) the best, usually closest repository, which is the fastest for that user's physical location.

One of the coolest things about Linux is that you can also install any program you know the name of with```
sudo apt-get install (programname)
```

While the Software Center is, I guess, easy to use, I use Synaptic most of the time. Install it with```
sudo apt-get install synaptic
```

It allows you to select several programs without downloading each one at a time, instead downloading all the selected programs and installing them in one operation. It is also faster, lots faster, than the Software Center. There are some nice programs for sale (usually pretty low-priced) there, but I only use it to reinstall programs I have already bought earlier, and use Synaptic or the command line to install or remove anything else.

Please do use these forums to ask any questions, but it's a good idea to search for your problem first to see if it already has an answer. These forums are designed for us to help each other out with learning how to use Linux, which is a **BIG** upgrade from Windows.

By Big I hope you mean better. Also I installed 'Synaptic Package Manager' from Ubuntu Software Center, does that suffice (is it the same thing as you have recommended)? I don't know how to use it for anything other than uninstalling softwares. I don't know how to use it for installing software.

Maybe i'll uninstall that and use the commands instead. I am really new to UBUNTU.

---

### Post by mastablasta on 2015-02-09
you mark packages for instalation and then you click in install. hwo hard can that be?

it also has advanced features. such as for example you can lock  package at a certian version etc.

---

