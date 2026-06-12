---
title: "Install Fedora Without a CD"
date: 2007-09-04
forum: Fedora/RedHat and derivatives
---

### Post by tuxcantfly on 2007-09-04
Main Website At [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

**What This Does**

It's an installer for Windows or Linux users that lets you install Fedora (released versions 8 or 7, or the Rawhide development version) or CentOS (5.1) without a CD. The way it works is that a small (8 MB) installer places the PXE (netboot) version of the Fedora installer on your hard drive, and configures your boot loader, either NTLDR if using Windows, or GRUB if using Linux, to boot from the PXE installer, and downloads and installs Fedora from the net.

**Requirements**

You will need to either have a Windows (95-Vista) or Linux (any distro that uses GRUB) install already on your hard drive. You'll also need an internet connection. Apart from that, the requirements are the same as the standard Fedora requirements.

**Instructions: Fedora 8**

Download the appropriate installer package from [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

If using Windows, download the .exe file, if using Fedora or another rpm-based distro, download the .rpm file, if using Ubuntu or another deb-based distro, download the .deb file, and if using a distro that doesn't support rpm or deb, download the sh file.

Then, install the package, and reboot. A menu entry should appear in the boot menu, titled "UNetbootin". Select that entry, and boot. When asked for a source of installation media, select "FTP".

You will then be prompted to specify a server and folder.

server: **download.fedora.redhat.com**
folder: **pub/fedora/linux/releases/8/Fedora/i386/os**

Or, if you would like to install 64-bit Fedora, for the folder, specify:

folder: **pub/fedora/linux/releases/8/Fedora/x86_64/os**

Then, the main installer will start, and wait as Fedora is downloaded and installed.
[B]
Instructions: Fedora Rawhide[/B]

Download the Fedora Rawhide package, then follow the same instructions as above, only for the server and folder, put:

server: **download.fedora.redhat.com**
folder: **pub/fedora/linux/development/i386/os**

or, if you want a 64-bit install, for the folder, specify:

folder: **pub/fedora/linux/development/x86_64/os**

**Instructions: Fedora 7**

Download the Fedora 7 package, then follow the same instructions as above, only for the server and folder, put:

server: **download.fedora.redhat.com**
folder: **pub/fedora/linux/releases/7/Fedora/i386/os**

or, if you want a 64-bit install, for the folder, specify:

folder: **pub/fedora/linux/releases/7/Fedora/x86_64/os**

**Instructions: CentOS 5.1**

Download the CentOS 5.1 package, then follow the same instructions as above, only for the server and folder, put:

server: **mirrors.kernel.org**
folder: **centos/5.1/os/i386**

or, if you want a 64-bit install, for the folder, specify:

folder: **centos/5.1/os/x86_64**

**Troubleshooting**

If you get an error like this:

```
could not retrieve images/stage2.img
```

Try inputting the IP address of download.fedora.redhat.com into the "server" field instead. You can determine the IP address using:

```
host download.fedora.redhat.com
```

**More**

UNetbootin also supports Ubuntu, openSUSE, Mandriva, Slackware, Arch Linux, and Debian. Post a reply if you need any help, new features, or another supported distro. The website is located at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by tuxcantfly on 2007-09-04
Also, the main thread, for Ubuntu, is posted at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540) this thread is for Fedora-specific instructions.

---

### Post by tuxcantfly on 2007-09-05
Whoops, forgot to subscribe to this thread, ignore this post

---

### Post by tuxcantfly on 2007-09-15
If anyone is having issues with specifying the FTP and server information, it is this:

server: **download.fedora.redhat.com**
folder: **pub/fedora/linux/releases/7/Fedora/i386/os**

I've updated the first post accordingly.

Also, I also posted this thread at fedoraforums, at [http://forums.fedoraforum.org/showthread.php?p=859216](http://forums.fedoraforum.org/showthread.php?p=859216)

---

### Post by Frak on 2007-10-05
Great job TuxCantFly =D>

Very Helpful :)

---

### Post by mindtrick on 2007-10-05
Is it possible to install Fedora 8 Beta version with this method? 

I mean if I change the directory to pub/fedora/linux/releases/test/7.92/Fedora/i386/os/

---

### Post by tuxcantfly on 2007-10-06
> **mindtrick said:**
> Is it possible to install Fedora 8 Beta version with this method? 

I mean if I change the directory to pub/fedora/linux/releases/test/7.92/Fedora/i386/os/

Yes, you can install Fedora 8 test builds, but it's not exactly that easy... you'll first need to install the Fedora 7 version of UNetbootin, then you need to obtain the netboot kernel and initrd (it's on the ftp server for fedora), you'll need to rename them to ubnkern and ubninit, and replace those of Fedora 7 (either in /boot or C:\unetbootin), then reboot, and do the procedures you posted, and that'll do the trick.

---

### Post by tuxcantfly on 2007-10-10
I've uploaded some 64-bit Fedora UNetbootin builds. Check the download page... Since the packages are all marked as "noarch/all", you don't need to necessarily install 32-bit from a 32-bit OS, or 64-bit from a 64-bit OS; you can install 64-bit if your processor is capable of it (amd64 or intel core2 and above), even if you're running a 32-bit Windows or Linux install.

---

### Post by tuxcantfly on 2007-10-28
I've added support in UNetbootin for installing from Windows Vista. See the usual download [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

I'll be adding Fedora 8 builds as soon as it's released in 12 days.

---

### Post by tuxcantfly on 2007-11-08
Fedora 8 has been released, so I've accordingly added UNetbootin builds to allow for no-CD Fedora installs. You can download the Fedora 8 version at [https://sourceforge.net/project/showfiles.php?group_id=198821&package_id=251761](https://sourceforge.net/project/showfiles.php?group_id=198821&package_id=251761)

If installing Fedora, select "FTP" as the installation source, and for the server, specify:

    **download.fedora.redhat.com**

and for the folder, if using the standard (32-bit) version, specify:

    **pub/fedora/linux/releases/8/Fedora/i386/os**

or if using the 64-bit version, specify:

    **pub/fedora/linux/releases/8/Fedora/x86_64/os**

---

### Post by Incense on 2007-11-08
Thanks for the information! I have an older PC without a DVD drive that I would love to test some newer distros on, and this is perfect.

Cheers!

---

### Post by tuxcantfly on 2007-12-20
I've added UNetbootin builds for performing no-cd installations of CentOS 5.1 from Windows or Linux as well. It's not Fedora, of course, but given that it's basically a free, rebranded version of RHEL 5, it might be useful for some Fedora and RHEL users. Usual download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

**Instructions: CentOS 5.1**

Download the CentOS 5.1 package, then follow the same instructions as above, only for the server and folder, put:

server: **mirrors.kernel.org**
folder: **centos/5.1/os/i386**

or, if you want a 64-bit install, for the folder, specify:

folder: **centos/5.1/os/x86_64**

---

### Post by tuxcantfly on 2008-01-11
I've added UNetbootin builds for installing Fedora Rawhide (the development version) without a CD. Since Rawhide is constantly undergoing development, and contains the latest, bleeding-edge software, it is unsuitable for usage in a production environment, and, depending on the release cycle, it may not work or install at all. Thus, these builds are only meant for those wanting to test the latest snapshot of the upcoming Fedora release. Since Rawhide's kernel is constantly changing, the UNetbootin build for Rawhide does not bundle the kernel nor initrd; rather it downloads the latest one off the official Fedora mirrors; thus the size of the package is reduced, but interenet access is required for usage.

The Rawhide builds can be downloaded from [https://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240555](https://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240555)

**Fedora Rawhide Install Instructions**

Install the UNetbootin package, reboot, and select UNetbootin on the GRUB boot menu. After rebooting, start the installation, and when prompted for an installation source choose 'Network' as the source, choose 'HTTP' as the protocol, and when prompted for a server, enter:

```
download.fedora.redhat.com
```

When asked for the folder, if installing the 32-bit (i386) version, enter:

```
/pub/fedora/linux/development/i386/os
```

Or, if installing the 64-bit (x86_64) version, enter:

```
/pub/fedora/linux/development/x86_64/os
```

---

### Post by Romanus81 on 2008-02-02
What happens if my computer is getting it's internet by encrypted wi-fi? Can I still use this?

---

### Post by tuxcantfly on 2008-02-02
> **Romanus81 said:**
> What happens if my computer is getting it's internet by encrypted wi-fi? Can I still use this?

Yes, but instead of installing directly from the internet, pre-download the Fedora DVD iso to a partition other than the one you aim to install to and specify that using the "hard drive" installation source option when the Fedora installer begins, rather than "http". Remember to pre-partition your drives (see [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4) ); you cannot resize them if using a pre-downloaded iso as the installation source

---

### Post by whitefang5412 on 2008-02-05
What advantages of doing this are there over just using a regular dvd with the ISO burned onto it?

---

### Post by tuxcantfly on 2008-02-05
> **whitefang5412 said:**
> What advantages of doing this are there over just using a regular dvd with the ISO burned onto it?

The very purpose is to spare you the need for the DVD (and thus is most useful if you can't boot from CD/DVD or don't have a spare CD/DVD, or just don't want to burn one), so if you already have the DVD burned and ready to go, just use the DVD since this is otherwise the same as the standard DVD install procedure (only without the DVD).

---

### Post by maybeway36 on 2008-02-05
I have used this to install Fedora on computers w/out a DVD drive. I boot Knoppix and copy the ISO from another computer to a hard drive partition, then boot the kenrel and initrd and select "hard drive" as the installation media.

---

