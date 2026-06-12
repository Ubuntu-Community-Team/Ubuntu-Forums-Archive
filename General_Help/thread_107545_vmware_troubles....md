---
title: "vmware troubles..."
date: 2005-12-23
forum: General Help
---

### Post by mztriz on 2005-12-23
```
mztriz@ubuntu2:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
mztriz@ubuntu2:~$ sudo apt-get install linux-headers-2.6.12-9-386
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.12-9
The following NEW packages will be installed:
  linux-headers-2.6.12-9 linux-headers-2.6.12-9-386
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/6725kB of archives.
After unpacking 70.1MB of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
ySelecting previously deselected package linux-headers-2.6.12-9.
(Reading database ... 74456 files and directories currently installed.)
Unpacking linux-headers-2.6.12-9 (from .../linux-headers-2.6.12-9_2.6.12-9.23_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-9-386.
Unpacking linux-headers-2.6.12-9-386 (from .../linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb) ...
Setting up linux-headers-2.6.12-9 (2.6.12-9.23) ...

Setting up linux-headers-2.6.12-9-386 (2.6.12-9.23) ...
mztriz@ubuntu2:~$ export CC=/usr/bin/gcc-3.4
mztriz@ubuntu2:~$ sudo ./vmware-install.pl
sudo: ./vmware-install.pl: command not found
mztriz@ubuntu2:~$ cd /tmp
mztriz@ubuntu2:/tmp$ cd vmware-player-distrib
mztriz@ubuntu2:/tmp/vmware-player-distrib$ ./vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

mztriz@ubuntu2:/tmp/vmware-player-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Player.

Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Player 1.0.1 build-19317 for Linux completed successfully.Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the library files?
[/usr/lib/vmware]

The path "/usr/lib/vmware" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want? [yes]





In which directory do you want to install the documentation files?
[/usr/share/doc/vmware]
The path "/usr/share/doc/vmware" does not exist currently. This program is goingto create it, including needed parent directories. Is this what you want?
[yes]
The installation of VMware Player 1.0.1 build-19317 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Player for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this
program to invoke the command for you now? [yes]
Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it.
END USER LICENSE AGREEMENT
FOR VMWARE(R) PLAYER

VMWARE, INC. LICENSES THIS DESKTOP SOFTWARE PRODUCT TO YOU SUBJECT
TO THE TERMS CONTAINED IN THIS END USER LICENSE AGREEMENT
("EULA"). READ THE TERMS OF THIS EULA CAREFULLY.  BY INSTALLING,
COPYING OR OTHERWISE USING THE SOFTWARE (AS DEFINED BELOW), YOU
AGREE TO BE BOUND BY THE TERMS OF THIS EULA.  IF YOU DO NOT AGREE
WITH THE TERMS OF THIS EULA, DO NOT DOWNLOAD, INSTALL, COPY OR USE
THE SOFTWARE.

NOTICE TO CUSTOMER
This EULA is a contract between you (either an individual or an
entity) and VMware, Inc. ("VMware"), which governs your use of
the VMware software product that accompanies this EULA and related
software components, which may include associated media, printed
materials, and online or electronic documentation.  This VMware
software product is designed for installation and use on a
personal computer only.  You may not install or use this VMware
software product on a server.

DEFINITIONS
VMware Player is a Desktop software product (the "VMware Desktop
Software") and includes Open Source Software components.   This
software package also includes additional modules ("Additional
Modules") that may be used in conjunction with the VMware Desktop
Software, subject to the acceptance of any applicable additional
license terms.  The VMware Desktop Software enables you to run
one or more instances of operating systems ("Guest Operating
Systems") and applications on a single personal computer.   In
this EULA, the VMware Desktop Software, associated media, printed
materials, online or electronic documentation and the Additional
Modules are collectively referred to as the "Software".  "Open
Source Software" means various open source software components
licensed under the terms of applicable open source license
agreements included in the materials relating to such software.

OPEN SOURCE SOFTWARE
The Open Source Software is composed of individual software
components, each of which has its own copyright and its own
applicable license conditions.  You must review the licenses
within the individual packages to understand your rights under
them.  The licenses can be found in the open_source_licenses.txt
file, other materials accompanying the software package, the
documentation or corresponding source files available at
http://www.vmware.com/download/open_sources.html.   Copyrights to
the Open Source Software are held by the copyright holders
indicated in the copyright notices in the corresponding source
files or in the open_sources_licenses.txt file or other materials
accompanying the software package.

LICENSE
The Software is licensed, not sold.  Subject to the terms and
limitations of this EULA, VMware hereby grants you a nonexclusive,
nontransferable license, without rights to sublicense, to
(i) use the Software (in object code form only) solely for your
own internal information processing services and computing needs;
(ii) modify the Software skins as permitted by VMware for your own
use; and (iii) use the documentation accompanying the Software in
connection with permitted uses of the Software. Subject to the
above, each copy of the Software may not be used by any other
person, whether or not such person is employed by or otherwise
associated with your entity.

LICENSE LIMITATIONS
You may not copy the Software except for a reasonable number of
machine-readable copies of the Software for backup or archival
purposes and except as expressly permitted in the License section
above.  You may not share or use concurrently the Software.  You
may not remove any titles, trademarks or trade names, copyright
notices, legends, or other proprietary markings on the Software.
You are not granted any rights to any trademarks or service marks
of VMware. VMware retains all rights not expressly granted to you.

DISTRIBUTING VMWARE PLAYER
If you are interested in distributing VMware Player electronically
or via internal Web site, CD or other media, or are interested in
placing an "Includes VMware Player" logo on your printed material,
please send a request to player_distribution@vmware.com and we will
provide you with a copy of our Distribution Agreement for your
signature.  The Distribution Agreement must be signed by yourself
and VMware prior to distributing VMware Player or using the
"Includes VMware Player" logo.

LICENSES REQUIRED FOR THIRD-PARTY SOFTWARE
The Software allows multiple operating systems and applications to
run on a single personal computer. You are responsible for
obtaining any licenses necessary to operate any such third-party
software.

PROPRIETARY RIGHTS RESERVED BY VMWARE
VMware retains all right, title, and interest in and to the
Software and in all related copyrights, trade secrets, patents,
trademarks, and any other intellectual and industrial property and
proprietary rights, including registrations, applications,
renewals, and extensions of such rights.

RESTRICTIONS
You may not (i) sell, lease, license, sublicense, distribute or
otherwise transfer in whole or in part the Software to another
party; (ii) provide, disclose, divulge or make available to, or
permit use of the Software in whole or in part by, any third party
without VMware's prior written consent; (iii) modify the Software,
except with respect to the Software skins as expressly permitted
in the License section of this EULA; (iv) create derivative works
based upon the Software; (v) permit another individual or entity
to access or use any software running in a virtual machine using
the Software;  (vi) integrate or use the Software with any other
software, plug-in or enhancement to convert or transform the
VMware virtual machine format into other virtual machine formats;
or (vii) use the Software to provide network, application hosting
or other services to third parties, or otherwise use the Software
on a service bureau or hosting basis for your customers.  Except
to the extent expressly permitted by applicable law, and to the
extent that VMware is not permitted by that applicable law to
exclude or limit the following rights, you may not decompile,
disassemble, reverse engineer, or otherwise attempt to derive
source code from the Software, in whole or in part.   You may not
conduct performance or benchmark studies without VMware's prior
written consent.  VMware will consider written requests to perform
and/or publish performance and benchmark studies. All requests by
you (and not unauthorized third parties) to publish performance
and benchmark results require VMware's review and approval of the
methodology, assumptions, and other parameters of the study.
Please contact VMware at benchmark@vmware.com for more
information.

TERMINATION
VMware may terminate this EULA if you fail to comply with any term
of this EULA.  In the event of termination, you must cease all use
of the Software and destroy all copies of the Software.  In
addition you must remove all copies of the Software from the
personal computer(s) on which it is installed.

GOVERNMENT RESTRICTIONS
You may not export or re-export the Software except in compliance
with the United States Export Administration Act and the related
rules and regulations and similar non-U.S. government
restrictions, if applicable. The Software and accompanying
documentation are deemed to be "commercial computer software" and
"commercial computer software documentation," respectively,
pursuant to DFAR Section 227.7202 and FAR Section 12.212(b), as
applicable.  Any use, modification, reproduction, release,
performing, displaying, or disclosing of the Software by the U.S.
Government shall be governed solely by the terms of this EULA.

NO WARRANTY
No Warranty. The Software is being provided to you on an "AS IS"
basis, without any technical support, and VMware makes no warranty
of any kind regarding its use or performance. VMWARE DOES NOT
AND CANNOT WARRANT THE PERFORMANCE OR RESULTS YOU MAY OBTAIN BY
USING THE SOFTWARE. VMWARE MAKES NO WARRANTIES, EXPRESS OR
IMPLIED, AS TO NONINFRINGEMENT OF THIRD PARTY RIGHTS,
MERCHANTABILITY, OR FITNESS FOR ANY PARTICULAR PURPOSE.

LIMITATION OF LIABILITY
TO THE MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW, IN NO EVENT
WILL VMWARE BE LIABLE FOR ANY LOST PROFITS OR BUSINESS
OPPORTUNITIES, LOSS OF USE, BUSINESS INTERRUPTION, LOSS OF DATA,
OR ANY OTHER DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR
CONSEQUENTIAL DAMAGES UNDER ANY THEORY OF LIABILITY, WHETHER
BASED IN CONTRACT, TORT, NEGLIGENCE, PRODUCT LIABILITY, OR
OTHERWISE.  BECAUSE SOME JURISDICTIONS DO NOT ALLOW THE EXCLUSION
OR LIMITATION OF LIABILITY FOR CONSEQUENTIAL OR INCIDENTAL
DAMAGES, THE PRECEDING LIMITATION MAY NOT APPLY TO YOU.

VMWARE'S LIABILITY UNDER THIS EULA WILL NOT, IN ANY EVENT, EXCEED
THE LICENSE FEES, IF ANY, PAID BY YOU TO VMWARE FOR THE SOFTWARE
LICENSED BY YOU UNDER THIS EULA.

THE FOREGOING LIMITATIONS SHALL APPLY TO THE MAXIMUM EXTENT
PERMITTED BY APPLICABLE LAW, REGARDLESS OF WHETHER VMWARE HAS BEEN
ADVISED OF THE POSSIBILITY OF SUCH DAMAGES AND REGARDLESS OF
WHETHER ANY REMEDY FAILS OF ITS ESSENTIAL PURPOSE.

GENERAL
This EULA is governed by the laws of the State of California and
the United States of America, without regard to conflict of law
principles. The United Nations Convention for the International
Sale of Goods shall not apply.  This EULA is the entire agreement
between us and supersedes the terms of any purchase orders and any
other communications or advertising with respect to the Software.
If any provision of this EULA is held invalid, the remainder of
this EULA shall continue in full force and effect.  This EULA
may be modified only by written agreement signed by authorized
representatives of you and VMware.


CONTACT INFORMATION
If you have any questions about this EULA, or if you want to
contact VMware for any reason, please direct all correspondence
to: VMware, Inc., 3145 Porter Drive, Palo Alto, CA 94304, United
States of America or email info@vmware.com.

VMware is a registered trademark of VMware, Inc. in the United
States and/or various jurisdictions.







Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


```

how do I know where my C header files are?

---

### Post by MartinG on 2005-12-23
For your kernel, try 
/usr/src/linux-headers-2.6.12-9-386/include/

---

### Post by mztriz on 2005-12-23
[QUOTE=MartinG]For your kernel, try 
/usr/src/linux-headers-2.6.12-9-386/include/[/QUOTE]
hmm I think I'm getting closer but that's not correct. ```

The directory of kernel headers (version 2.6.12-9-386) does not match your
running kernel (version 2.6.12-10-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] usr/src/linux-headers-2.6.12-10-386

The path "usr/src/linux-headers-2.6.12-10-386" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

---

### Post by mztriz on 2005-12-23
[QUOTE=mztriz]hmm I think I'm getting closer but that's not correct. ```

The directory of kernel headers (version 2.6.12-9-386) does not match your
running kernel (version 2.6.12-10-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] usr/src/linux-headers-2.6.12-10-386

The path "usr/src/linux-headers-2.6.12-10-386" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```[/QUOTE]

I also tried this 

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] usr/src/linux-headers-2.6.12-10-386/include/
The path "usr/src/linux-headers-2.6.12-10-386/include" is not an existing
directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

thank you for trying to help me :D

---

### Post by mztriz on 2005-12-23
I also tried this 

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] usr/src/linux-headers-2.6.12-10-386/include/
The path "usr/src/linux-headers-2.6.12-10-386/include" is not an existing
directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

thank you for trying to help me :D

---

### Post by MartinG on 2005-12-23
In the code included in your first post, you apparently installed the headers for the 2.6.12-9-386 kernel.  Now the error message suggests your running kernel is 2.6.12-10-386.  Have you not installed the corresponding headers for this yet? Version matching is absolutely *essential*.

If you had installed the right headers, then I think your "I also tried this" would have worked.

---

### Post by mztriz on 2005-12-23
[QUOTE=MartinG]In the code included in your first post, you apparently installed the headers for the 2.6.12-9-386 kernel.  Now the error message suggests your running kernel is 2.6.12-10-386.  Have you not installed the corresponding headers for this yet? Version matching is absolutely *essential*.

If you had installed the right headers, then I think your "I also tried this" would have worked.[/QUOTE]
In my very first post I did this 
```
mztriz@ubuntu2:~$ sudo apt-get install linux-headers-2.6.12-9-386
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.12-9
The following NEW packages will be installed:
  linux-headers-2.6.12-9 linux-headers-2.6.12-9-386
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/6725kB of archives.
```

was that not correct?

---

### Post by mztriz on 2005-12-23
[QUOTE=mztriz]In my very first post I did this 
```
mztriz@ubuntu2:~$ apt-get install linux-headers-2.6.12-9-386
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.12-9
The following NEW packages will be installed:
  linux-headers-2.6.12-9 linux-headers-2.6.12-9-386
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/6725kB of archives.
```

was that not correct?[/QUOTE]
I'm sorry I missunderstood. I *think* i'm doing it right now, I just installed ```
mztriz@ubuntu2:~$ su
Password:
root@ubuntu2:/home/mztriz# sudo apt-get install linux-headers-2.6.12-10-386
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.12-10
The following NEW packages will be installed:
  linux-headers-2.6.12-10 linux-headers-2.6.12-10-386
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 6727kB of archives.
After unpacking 70.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com breezy-security/main linux-headers-2.6.12-10 2.6.12-10.25 [5926kB]
Get:2 http://security.ubuntu.com breezy-security/main linux-headers-2.6.12-10-386 2.6.12-10.25 [801kB]
Fetched 6727kB in 26s (251kB/s)

Preconfiguring packages ...
Selecting previously deselected package linux-headers-2.6.12-10.
(Reading database ... 88214 files and directories currently installed.)
Unpacking linux-headers-2.6.12-10 (from .../linux-headers-2.6.12-10_2.6.12-10.25_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-10-386.
Unpacking linux-headers-2.6.12-10-386 (from .../linux-headers-2.6.12-10-386_2.6.12-10.25_i386.deb) ...
Setting up linux-headers-2.6.12-10 (2.6.12-10.25) ...

Setting up linux-headers-2.6.12-10-386 (2.6.12-10.25) ...

```

so now I should try the other thing again? (i'm going to try it lol)

---

### Post by mztriz on 2005-12-23
```
usr/src/linux-headers-2.6.12-10-386/include/
``` still doesn't work...

---

### Post by sunset on 2005-12-23
What's the error message this time?

---

### Post by mztriz on 2005-12-23
[QUOTE=sunset]What's the error message this time?[/QUOTE]
it's the same thing

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] usr/src/linux-headers-2.6.12-10-386/include/
The path "usr/src/linux-headers-2.6.12-10-386/include" is not an existing
directory.

What is the location of the directory of C header files that match your running

```

---

### Post by rcerreto on 2005-12-23
I think it should be:
/lib/modules/2.6.12-10-i386/build/include

given that i386 is the kernel you're using.
Anyway, in your example an initial slash ("/") could be missing

---

### Post by mztriz on 2005-12-23
[QUOTE=rcerreto]I think it should be:
/lib/modules/2.6.12-10-i386/build/include

given that i386 is the kernel you're using.
Anyway, in your example an initial slash ("/") could be missing[/QUOTE]

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.12-10-i386/build/include

The path "/lib/modules/2.6.12-10-i386/build/include" is not an existing
directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


```

and the first one again
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-9-386/include/

The directory of kernel headers (version 2.6.12-9-386) does not match your
running kernel (version 2.6.12-10-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


```

---

### Post by sunset on 2005-12-23
Like rcerreto says, you need the leading slash.  The "/lib/modules/..." thing should work equally well, but you have a typo there also -- it should be "386" instead of "i386".

---

### Post by MartinG on 2005-12-23
[QUOTE=mztriz]it's the same thing

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] usr/src/linux-headers-2.6.12-10-386/include/
The path "usr/src/linux-headers-2.6.12-10-386/include" is not an existing
directory.

What is the location of the directory of C header files that match your running

```[/QUOTE]As rcerreto says, there's a missing slash:
usr/src/linux-headers-2.6.12-10-386/include/
should be
/usr/src/linux-headers-2.6.12-10-386/include/
How often have I made that mistake :-(

---

### Post by mztriz on 2005-12-23
[QUOTE=MartinG]As rcerreto says, there's a missing slash:
usr/src/linux-headers-2.6.12-10-386/include/
should be
/usr/src/linux-headers-2.6.12-10-386/include/
How often have I made that mistake :-([/QUOTE]

OHH wow, that worked! Thanks everyone!! :)

---

### Post by mztriz on 2005-12-23
wait i have one more question.... =\
Do you want networking for your virtual machines? (yes/no/help) [yes] yes

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes]


should i use nat? what does it do (sorry I'm an idiot...) I don't want to mess up my connection.

---

### Post by p0liX on 2005-12-23
Its best to just keep the defaults and everything will come up as it should.  Works great for me!

---

### Post by mztriz on 2005-12-23
[QUOTE=p0liX]Its best to just keep the defaults and everything will come up as it should.  Works great for me![/QUOTE]
Ok, thanks :)

---

### Post by sunset on 2005-12-23
If you already have a home network or router, don't bother with NAT.  You might need it if there's no router and your computer is wired directly to your DSL modem or whatever.

---

### Post by mztriz on 2005-12-23
[QUOTE=sunset]If you already have a home network or router, don't bother with NAT.  You might need it if there's no router and your computer is wired directly to your DSL modem or whatever.[/QUOTE]
oops... I already did it, is that bad.. (I have a router connected to 3 other computers) this one is directly connected to the router-- the others are wireless

---

### Post by sunset on 2005-12-23
It's not bad, just not necessary.  It will also create headaches for you if you want the virtual machine to be a server of some sort.

NAT is a smoke-and-mirrors way of letting the virtual machine share the same IP address as the host computer.  If you just use bridged networking then the virtual machine will have its own IP address and will be easier to connect to from other machines.

Hope this helps!

---

