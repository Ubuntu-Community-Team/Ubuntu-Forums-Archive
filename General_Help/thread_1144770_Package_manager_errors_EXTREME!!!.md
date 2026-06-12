---
title: "Package manager errors EXTREME!!!"
date: 2009-05-01
forum: General Help
---

### Post by xaegis on 2009-05-01
Problem with Uninstalling screem.
in synaptic screem appears to be installed but when I  try to remove it I get errors.
Can anyone tell me what I should be doing?

Thanks in advance!



:)

Here is a copy of the terminal

$user-laptop:~/Desktop$ sudo dpkg -s screem
Package: screem
Status: purge ok half-configured
Priority: optional
Section: web
Installed-Size: 7744
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.16.1-4.2ubuntu1
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libcroco3 (>= 0.6.1), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.71), libenchant1c2a, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.16.0), libgnome-menu2 (>= 2.15.4), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeprint2.2-0 (>= 2.17.0), libgnomeprintui2.2-0 (>= 2.17.0), libgnomeui-0 (>= 2.22.0), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.14.1), libgtkhtml2-0 (>= 2.11.1), libgtksourceview1.0-0 (>= 1.7.2), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.21.6), libpopt0 (>= 1.14), libsm6, libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4), gconf2 (>= 2.10.1-2), dbus-1-utils
Suggests: tidy, exuberant-ctags
Description: A GNOME website development environment
 SCREEM is a tag-based Web page editor which aims not only to aid in creating
 Web pages, but also to provide useful site maintenance facilities,
 including automatic link updating and site upload facilities. SCREEM has
 more than just the usual HTML tags, with features for including Javascript,
 PHP, cascading style sheets, etc within your site.
 .
 It is written for use with the GNOME ([http://www.gnome.org](http://www.gnome.org)) desktop
 environment
Original-Maintainer: Rob Bradford <robster@debian.org>

$user-laptop:~/Desktop$ sudo dpkg -l screem
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pF  screem         0.16.1-4.2ubun A GNOME website development environment

$user-laptop:~/Desktop$ sudo dpkg --purge screem
(Reading database ... 114741 files and directories currently installed.)
Removing screem ...
Warning: /usr/share/gconf/schemas/screem.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing screem (--purge):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 screem
$user-laptop:~/Desktop$

---

### Post by dcstar on 2009-05-01
> **xaegis said:**
> Problem with Uninstalling screem.
in synaptic screem appears to be installed but when I  try to remove it I get errors.
Can anyone tell me what I should be doing?


Use Synaptic to reinstall it and then remove it.

---

### Post by xaegis on 2009-05-01
> **dcstar said:**
> Use Synaptic to reinstall it and then remove it.

When I do that I get an error box that says:

E: screem: subprocess post-installation script returned error exit status 2

also anotherterminal that says:

Warning: /usr/share/gconf/schemas/screem.schemas could bot be found.
Usage:gconf-schemas --[un]register file1.schemas [file2schemas[..]]

gconf-schemas error: You need at least a file to (un)register.
dpkg:error processing screem (--configure):
 subprocess post-instillation script returned error exit status 2
Errors were encountered while processing:
 screem
E:  Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:



Seems like I have Schrödinger's package its neither installed nor un-installed!!!

=(

---

### Post by xaegis on 2009-05-01
Did I win the "stump the community" prize?


Yay for Meeeeeee!!!!!


*sob*

:cry:

---

### Post by The Cog on 2009-05-01
I had that problem a couple of days ago. I didn't know how to fix it, so I backed /home to a USB hard drive and reinstalled and restored.

I know there is a way to override the error and allow the removal to complete thoug. I remember now that it was a problem with an early .deb from VirtualBox that caused the same problem. There was a command to force the uninstall, but I don't remember what it was. Maybe search the VirtualBox site to find it?

---

### Post by xaegis on 2009-05-01
SOLVED!!!


ok I went to the:
 /var/lib/dpkg/info
folder and removed all the screem files referenced there using: 
sudo rm screem.* -i

then I reinstalled the package using the force command and finally used

sudo dpkg --purge screem

that seems to have tasken care of the problem.


Thanks for all the input!

-e

---

