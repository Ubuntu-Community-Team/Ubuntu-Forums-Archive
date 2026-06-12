---
title: "Failed to get size of gamma for output default when adding new screen resolution"
date: 2020-01-13
forum: Desktop Environments
---

### Post by galves58 on 2020-01-13
Hello everyone,


I was always a Windows user and started using linux 2 weeks ago, I'm still learning.

The first distribution I installed was LMint Xfce 19.3 (compatibility mode), but I noticed a slowness, probably caused by my PC hardware.

**Processor:** Intel Pentium 4 (Northwood) 2.60 GHz
**RAM:** 2 GB
**HD:** 146 GB
**Monitor:** AOC LM522 [Cod. TFT1560PSA] 15 inch LCD

**No additional drivers available** for download.

That's why I switched to Xubuntu 18.04. In the system live by the pen drive everything was fine, but when installing it permanently, the resolution of the monitor got problems. I searched some sites and could not solve using the command xrandr.* The current resolution is 640x480*, but my monitor is **1024x768**.

The terminal response to the **xrandr **command is:
```
gustavo@gustavo-STI:~$ xrandrxrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480       73.00* 

gustavo@gustavo-STI:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

gustavo@gustavo-STI:~$ sudo xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
[sudo] senha para gustavo: 
xrandr: Failed to get size of gamma for output default 
```[COLOR=#000000]
[/COLOR]Using the command **lshw -c video**, your answer was:
```
gustavo@gustavo-STI:~$ sudo lshw -c video  *-display DISPONÍVEL      
       descrição: VGA compatible controller
       produto: CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro]
       fabricante: VIA Technologies, Inc.
       ID físico: 0
       informações do barramento: pci@0000:01:00.0
       versão: 01
       largura: 32 bits
       clock: 66MHz
       capacidades: vga_controller bus_master cap_list
       configuração: latency=32 mingnt=2
       recursos: memória:d8000000-dbffffff memória:dc000000-dcffffff memória:c0000-dffff
```[COLOR=#000000]
[/COLOR]In **lspci**, one of the results is:
```
 01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01) 
```[COLOR=#000000]
[/COLOR]I also created the **xorg.conf** file with the code:
```
 sudo Xorg :1 -configure 
```
and sent it to /etc/X11 without changing with the code:
```
 sudo cp xorg.conf.new /etc/X11/xorg.conf
```
I restarted and nothing changed.

What can I do to fix this problem?

Best regards,
Gustavo

---

### Post by deadflowr on 2020-01-13
Try installing the openchrome driver (it's the driver package for via cards)
```
sudo apt install xserver-xorg-video-openchrome
```

Ubuntu typically ships with drivers, but only the more common ones such as intel, amd, and nvidia's open source versions.
via graphics cards are rather old now and so Ubuntu don't seem to include those with the default anymore.

---

### Post by galves58 on 2020-01-13
Thanks for the answer!

I used the command you told me:
```
 gustavo@gustavo-STI:~$ sudo apt install xserver-xorg-video-openchrome
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Alguns pacotes não puderam ser instalados. Isto pode significar que
você solicitou uma situação impossível ou, se você está usando a
distribuição instável, que alguns pacotes requeridos não foram
criados ainda ou foram retirados da "Incoming".
A informação a seguir pode ajudar a resolver a situação:


Os pacotes a seguir têm dependências desencontradas:
 xserver-xorg-video-openchrome : Depende: xorg-video-abi-23
                                 Depende: xserver-xorg-core (>= 2:1.18.99.901)
E: Impossível corrigir problemas, você manteve (hold) pacotes quebrados.
```

I restarted the PC, but the problem still persists!

---

### Post by deadflowr on 2020-01-13
You might require installing the original 18.04.
See: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

Unfortunately the openchrome driver doesn't seem to have a hwe version, so the system can only install the original version for 18.04.
But in order to install it it needs the original xserver-xorg-core package, but the newer 18.04 releases no longer has that by default.
It's messy.

The solution to that is to either try downgrading the package, which is a pain.
Or reinstall the older version 
(You can grab the older version from here:
[s][http://old-releases.ubuntu.com/releases/bionic/]("http://old-releases.ubuntu.com/releases/bionic/")[/s]

Oops. sorry, that's for Ubuntu if you want to older Xubuntu version you go to this page.
[http://cdimage.ubuntu.com/xubuntu/releases/18.04.1/release/]("http://cdimage.ubuntu.com/xubuntu/releases/18.04.1/release/")
You'll need to scroll down to the version marked as xubuntu-18.04-desktop-XXX.iso 
replace XXX with amd64 for 64-bit (cpu doesn't matter as it works for both intel and amd cpus), or i386 for 32-bit. (same thing as amd64, it works with both)
You can also use the version mark xubuntu-18.04.1-desktop.
But don't download for version higher than that like 18.04.2, as that will have the upgraded stacks.

Hope that sort of makes sense. Or is helpful...

---

### Post by galves58 on 2020-01-13
I went to [https://launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome](https://launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome) and in **The Bionic Beaver (supported)**, downloaded and installed the package **xserver-xorg-video-openchrome_0 .6.0-3_i386.deb (149.4 KiB)**


I confirmed with the command **apt-cache show xserver-xorg-video-openchrome**:
```
gustavo@gustavo-STI:~$ apt-cache show xserver-xorg-video-openchrome
Package: xserver-xorg-video-openchrome
Architecture: i386
Version: 1:0.6.0-3
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 542
Provides: xorg-driver-video
Depends: libc6 (>= 2.4), libdrm2 (>= 2.3.1), libx11-6 (>= 2:1.4.99.1), libxext6, libxv1, libxvmc1, xorg-video-abi-23, xserver-xorg-core (>= 2:1.18.99.901)
Filename: pool/universe/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.6.0-3_i386.deb
Size: 152968
MD5sum: 256367b9214c09ca540919a5addb8469
SHA1: a1887689e4611aaa8e6a85b76f9e4494561060e9
SHA256: a98535044258f44353c1da0490d836e686cf6ac1354aa2ff16c0f3fee4eb0d96
Homepage: https://www.freedesktop.org/wiki/Openchrome/
Description-en: X.Org X server -- OpenChrome display driver
 This package provides the 'openchrome' driver for the VIA Technologies
 UniChrome and Chrome9 IGPs chipsets. The following chips should be
 supported: CLE266, KM400(A), KN400(A), P4M800, K8M800, K8N800, PM800,
 PN800, PM880, CN333, CN400, P4M800 Pro, VN800, CN700, CX700, VX700,
 P4M890, VN890, CN800, K8M890, K8N890, P4M900, VN896, CN896, VX800, VX820,
 VX855, VX875, VX900.
 .
 This package is built from the FreeDesktop.org xf86-video-openchrome driver.
Description-md5: eb7e8a0af39146be33a143f7aa500d95
Supported: 3y
```
I restarted, but the problem persists. From this new information is still possible to do something?

I also got this link [https://packages.ubuntu.com/search?keywords=xserver-xorg-core](https://packages.ubuntu.com/search?keywords=xserver-xorg-core), 
went to [I]**bionic (18.04LTS) (x11)**: Xorg X server - core server
2: 1.19.6-1ubuntu4.2 [security]: amd64 i386
2: 1.19.6-1ubuntu4 [ports]: arm64 armhf ppc64el s390x[/I]
and downloaded and installed the i386 version.
I confirmed with the command **apt-cache show xserver-xorg-core**:
```
gustavo@gustavo-STI:~$ apt-cache show xserver-xorg-core
Package: xserver-xorg-core
Architecture: i386
Version: 2:1.19.6-1ubuntu4.3
Priority: optional
Section: x11
Source: xorg-server
Origin: Ubuntu
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4133
Provides: xorg-input-abi-24, xorg-video-abi-23, xserver-xorg-video-modesetting
Depends: xserver-common (>= 2:1.19.6-1ubuntu4.3), keyboard-configuration, udev (>= 149), libegl1-mesa | libegl1, libaudit1 (>= 1:2.2.1), libbsd0 (>= 0.7.0), libc6 (>= 2.17), libdbus-1-3 (>= 1.9.14), libdrm2 (>= 2.3.1), libepoxy0 (>= 1.0), libgbm1 (>= 10.2~0), libgcrypt20 (>= 1.8.0), libgl1, libpciaccess0 (>= 0.12.902), libpixman-1-0 (>= 0.30.0), libselinux1 (>= 2.0.82), libsystemd0, libudev1 (>= 183), libxau6, libxdmcp6, libxfont2 (>= 1:2.0.1), libxshmfence1
Recommends: libgl1-mesa-dri (>= 7.10.2-4), libpam-systemd
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xserver-xorg-input-evtouch, xserver-xorg-video-modesetting
Breaks: systemd (<< 226-4~), xserver-xorg (<< 1:7.7+10~)
Replaces: xserver-xorg (<< 1:7.7+10~), xserver-xorg-video-modesetting
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.19.6-1ubuntu4.3_i386.deb
Size: 1416332
MD5sum: 77f6c8847c8f23414a95b2e4f818dc8d
SHA1: 58c34529dad32aefa9f210a34c5581f593366f56
SHA256: 77e32f69c5fc8d4656feaeeb72e685816335921b43e07f518a87d5bef8b2c994
Homepage: https://www.x.org/
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:https://www.x.org>
 .
 This package is built from the X.org xserver module.
Description-md5: 018a15965c91ba9a09e0652c1c0fb9ac
Task: ubuntu-desktop, kubuntu-desktop, xubuntu-core, xubuntu-desktop, core-share, lubuntu-gtk-core, lubuntu-desktop-share, lubuntu-core, lubuntu-qt-core, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Supported: 5y


Package: xserver-xorg-core
Architecture: i386
Version: 2:1.19.6-1ubuntu4.2
Priority: optional
Section: x11
Source: xorg-server
Origin: Ubuntu
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4129
Provides: xorg-input-abi-24, xorg-video-abi-23, xserver-xorg-video-modesetting
Depends: xserver-common (>= 2:1.19.6-1ubuntu4.2), keyboard-configuration, udev (>= 149), libegl1-mesa | libegl1, libaudit1 (>= 1:2.2.1), libbsd0 (>= 0.7.0), libc6 (>= 2.17), libdbus-1-3 (>= 1.9.14), libdrm2 (>= 2.3.1), libepoxy0 (>= 1.0), libgbm1 (>= 10.2~0), libgcrypt20 (>= 1.8.0), libgl1, libpciaccess0 (>= 0.12.902), libpixman-1-0 (>= 0.30.0), libselinux1 (>= 2.0.82), libsystemd0, libudev1 (>= 183), libxau6, libxdmcp6, libxfont2 (>= 1:2.0.1), libxshmfence1
Recommends: libgl1-mesa-dri (>= 7.10.2-4), libpam-systemd
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xserver-xorg-input-evtouch, xserver-xorg-video-modesetting
Breaks: systemd (<< 226-4~), xserver-xorg (<< 1:7.7+10~)
Replaces: xserver-xorg (<< 1:7.7+10~), xserver-xorg-video-modesetting
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.19.6-1ubuntu4.2_i386.deb
Size: 1416632
MD5sum: 47523e1d0407bfff7748d3c635956469
SHA1: defb1cadcbe497033116b5ebe486db1c63f98ebf
SHA256: fe94da7129836f1683c45a428ebfb5f0ef5501bdaa2133928a41ac2ddd37f566
Homepage: https://www.x.org/
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:https://www.x.org>
 .
 This package is built from the X.org xserver module.
Description-md5: 018a15965c91ba9a09e0652c1c0fb9ac
Task: ubuntu-desktop, kubuntu-desktop, xubuntu-core, xubuntu-desktop, core-share, lubuntu-gtk-core, lubuntu-desktop-share, lubuntu-core, lubuntu-qt-core, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Supported: 5y


Package: xserver-xorg-core
Architecture: i386
Version: 2:1.19.6-1ubuntu4
Priority: optional
Section: x11
Source: xorg-server
Origin: Ubuntu
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4129
Provides: xorg-input-abi-24, xorg-video-abi-23, xserver-xorg-video-modesetting
Depends: xserver-common (>= 2:1.19.6-1ubuntu4), keyboard-configuration, udev (>= 149), libegl1-mesa | libegl1, libaudit1 (>= 1:2.2.1), libbsd0 (>= 0.7.0), libc6 (>= 2.17), libdbus-1-3 (>= 1.9.14), libdrm2 (>= 2.3.1), libepoxy0 (>= 1.0), libgbm1 (>= 10.2~0), libgcrypt20 (>= 1.8.0), libgl1, libpciaccess0 (>= 0.12.902), libpixman-1-0 (>= 0.30.0), libselinux1 (>= 2.0.82), libsystemd0, libudev1 (>= 183), libxau6, libxdmcp6, libxfont2 (>= 1:2.0.1), libxshmfence1
Recommends: libgl1-mesa-dri (>= 7.10.2-4), libpam-systemd
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xserver-xorg-input-evtouch, xserver-xorg-video-modesetting
Breaks: systemd (<< 226-4~), xserver-xorg (<< 1:7.7+10~)
Replaces: xserver-xorg (<< 1:7.7+10~), xserver-xorg-video-modesetting
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.19.6-1ubuntu4_i386.deb
Size: 1416632
MD5sum: ce0a358552c783869fbcc9389be67eec
SHA1: aca0e98cd93f851d99f56127bb50597e5c1e945f
SHA256: 03a61ae9a5242d94420f131931806d4ffa09dc1d993c5839a5d0547d96ef988a
Homepage: https://www.x.org/
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:https://www.x.org>
 .
 This package is built from the X.org xserver module.
Description-md5: 018a15965c91ba9a09e0652c1c0fb9ac
Task: ubuntu-desktop, kubuntu-desktop, xubuntu-core, xubuntu-desktop, core-share, lubuntu-gtk-core, lubuntu-desktop-share, lubuntu-core, lubuntu-qt-core, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Supported: 5y
```

I restarted and nothing has changed.


---
> [COLOR=#000000]Oops. sorry, that's for Ubuntu if you want to older Xubuntu version you go to this page.[/COLOR]
[http://cdimage.ubuntu.com/xubuntu/re....04.1/release/]("http://cdimage.ubuntu.com/xubuntu/releases/18.04.1/release/")
[COLOR=#000000]You'll need to scroll down to the version marked as xubuntu-18.04-desktop-XXX.iso[/COLOR]
[COLOR=#000000]replace XXX with amd64 for 64-bit (cpu doesn't matter as it works for both intel and amd cpus), or i386 for 32-bit. (same thing as amd64, it works with both)[/COLOR]
[COLOR=#000000]You can also use the version mark xubuntu-18.04.1-desktop.[/COLOR]
[COLOR=#000000]But don't download for version higher than that like 18.04.2, as that will have the upgraded stacks.[/COLOR]

I don't know if I fully understand what you said, but by not adding the xserver-xorg-core package by default I can't change the resolution of my monitor. The solution would be to keep an older version of Xubuntu by going to the indicated link, [http://cdimage.ubuntu.com/xubuntu/releases/18.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/18.04.1/release/), and downloading either **xubuntu-18.04-desktop-i386.iso** or **xubuntu-18.04.1-desktop-i386.iso**. This is it?

Thanks for listening!

---

### Post by deadflowr on 2020-01-13
> I also got this link [https://packages.ubuntu.com/search?k...rver-xorg-core](https://packages.ubuntu.com/search?k...rver-xorg-core),
went to bionic (18.04LTS) (x11): Xorg X server - core server
2: 1.19.6-1ubuntu4.2 [security]: amd64 i386
2: 1.19.6-1ubuntu4 [ports]: arm64 armhf ppc64el s390x
and downloaded and installed the i386 version.
I confirmed with the command** apt-cache show xserver-xorg-core**:
*apt-cache show* only shows the general information of a package, not whether it has been installed or not.
Use the command **apt-cache policy <package>** to see whether or not a package is installed.

That said, I'm fairly confident it would have still erred if you had tried to install it.

The reason it would have still erred is because it cannot be installed.
It cannot be installed because you already have an xserver-xorg-core package installed.
The version you already have would be the xserver-xorg-core-hwe-18.04 version.
This is the hardware enablement stack version I tried alluding to in the link
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

In order to install the xserver-xorg-core package you first have to remove the xserver-xorg-core-hwe-18.04 package,
but in order to do that the whole xorg system will have to be purged as well. (And not optionally)
So it's a whole big pain and easier to just reinstall...

> The solution would be to keep an older version of Xubuntu by going to the indicated link, [http://cdimage.ubuntu.com/xubuntu/re....04.1/release/](http://cdimage.ubuntu.com/xubuntu/re....04.1/release/), and downloading either **xubuntu-18.04-desktop-i386.iso** or **xubuntu-18.04.1-desktop-i386.iso**. This is it?
Yes, because those will have the proper xserver-xorg-core package (et al) that do not conflict.
And it's really much quicker and safer to reinstall it.
And then you can install the openchrome package.
Beyond that, it's unknown what state things will be for it,
It might improve things but that's indeterminate.

Does that make sense?

I know it's a lot to take in for something that's quite simple, really, and Ubuntu's whole hardware enablement stack infrastructure doesn't make things easy to explain.

---

### Post by galves58 on 2020-01-14
I installed xubuntu-18.04.1-desktop-i386.iso as suggested.
I created the xorg.config file and sent it to /etc/X11 and installed the openchrome driver as you instructed me in the first post. 
It is now working at 1024x768!!

```
gustavo@gustavo-STI:~$ sudo Xorg :1 -configure
X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic i686 Ubuntu
Current Operating System: Linux gustavo-STI 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:37:27 UTC 2018 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-29-generic root=UUID=620aa2b4-4178-4171-9ecc-a687a943b98b ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:08:02PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Jan 14 12:08:52 2020
List of video drivers:
    ati
    intel
    nouveau
    qxl
    radeon
    vmware
    vesa
    modesetting
    fbdev
    amdgpu
(++) Using config file: "/home/gustavo/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Xorg detected your mouse at device /dev/input/mice.
Please check your config if the mouse is still not
operational, as by default Xorg tries to autodetect
the protocol.

Your xorg.conf file is /home/gustavo/xorg.conf.new

To test the server, run 'X -config /home/gustavo/xorg.conf.new'

(EE) Server terminated with error (2). Closing log file.

gustavo@gustavo-STI:~$ sudo cp xorg.conf.new /etc/X11/xorg.conf
gustavo@gustavo-STI:~$ sudo apt install xserver-xorg-video-openchrome
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Os NOVOS pacotes a seguir serão instalados:
  xserver-xorg-video-openchrome
0 pacotes atualizados, 1 pacotes novos instalados, 0 a serem removidos e 496 não atualizados.
É preciso baixar 153 kB de arquivos.
Depois desta operação, 555 kB adicionais de espaço em disco serão usados.
Obter:1 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) bionic/universe i386 xserver-xorg-video-openchrome i386 1:0.6.0-3 [153 kB]
Baixados 153 kB em 0s (1.087 kB/s)                    
A seleccionar pacote anteriormente não seleccionado xserver-xorg-video-openchrome.
(Lendo banco de dados ... 145089 ficheiros e directórios actualmente instalados.)
A preparar para desempacotar .../xserver-xorg-video-openchrome_1%3a0.6.0-3_i386.deb ...
A descompactar xserver-xorg-video-openchrome (1:0.6.0-3) ...
Configurando xserver-xorg-video-openchrome (1:0.6.0-3) ...
A processar 'triggers' para libc-bin (2.27-3ubuntu1) ...
A processar 'triggers' para man-db (2.8.3-2) ...

gustavo@gustavo-STI:~$ apt-cache policy xserver-xorg-video-openchrome
xserver-xorg-video-openchrome:
  Instalado: 1:0.6.0-3
  Candidato: 1:0.6.0-3
  Tabela de versão:
 *** 1:0.6.0-3 500
        500 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) bionic/universe i386 Packages
        100 /var/lib/dpkg/status
```


Thank you so much for your help and attention!

---

