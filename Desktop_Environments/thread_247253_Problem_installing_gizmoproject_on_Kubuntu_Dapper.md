---
title: "Problem installing gizmoproject on Kubuntu Dapper"
date: 2006-08-30
forum: Desktop Environments
---

### Post by chandra on 2006-08-30
I am trying to install the gizmoproject VoIP application on Kubuntu Dapper.

I downloaded from

[http://www.gizmoproject.com/download-linux.html](http://www.gizmoproject.com/download-linux.html)

the following three packages:

bonjour_107.1-0.0.0.50.linspire0.2_i386.deb
libsipphoneapi_alsa_0.78.20060211-1_i386.deb
gizmo-project_1.0.0.18-1_debian_i386.deb

and tried to install them in that order.

With the first package, bonjour, I got the following message:
===========
sudo dpkg -i bonjour_107.1-0.0.0.50.linspire0.2_i386.deb
(Reading database ... 204610 files and directories currently installed.)
Unpacking bonjour (from bonjour_107.1-0.0.0.50.linspire0.2_i386.deb) ...
dpkg: error processing bonjour_107.1-0.0.0.50.linspire0.2_i386.deb (--install):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package libavahi-compat-libdnssd1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 bonjour_107.1-0.0.0.50.linspire0.2_i386.deb
===========

I do not want to touch 

libavahi-compat-libdnssd1 

because that would undermine

kdebase ksysguard ksysguardd kubuntu-desktop

I believe that only a symlink is missing.  Once I set that up manually, I should be able to install all three packages successfully.

Can anyone assist please?

Thanks.

---

### Post by chandra on 2006-08-31
It looks like the solution is as follows:

1. cd /usr/lib

2. sudo ln -s libdns_sd.so.1.0.0 libdns_sd.so

3. sudo dpkg -i libsipphoneapi_alsa_0.78.20060211-1_i386.deb
   sudo dpkg -i gizmo-project_1.0.0.18-1_debian_i386.deb

4. Do not install the bonjour package.

Perhaps the Ubuntu packagers will (if policy allows it) package Gizmo for (K)Ubuntu so that this workaround is not needed.

---

### Post by chandra on 2006-09-02
An update to my reply above.

Upgrade to version 1.1.0.35
==================
1. I had to uninstall libsipphoneapi so:

sudo dpkg -r libsipphoneapi

2. I then installed the new version from
[http://www.gizmoproject.com/jasmine/gizmo-project_1.1.0.35_i386.deb](http://www.gizmoproject.com/jasmine/gizmo-project_1.1.0.35_i386.deb) so:

sudo dpkg -i gizmo-project_1.1.0.35_i386.deb

3. I fired up Gizmo and went to

Gizmo Project -> Preferences -> Audio

ALSA was already pre-selected. My sound card SB Live 5.1 was recognized (bravo!)

4. Yet I still could not hear my own echo test.

5. I found that I had to:

uncheck Automatic Gain Control but keep checked the Echo Cancellation.  Later on, it worked even if Automatic Gain Control was checked.  I am unsure what had changed to allow this.

6. The echo test with 1-747-474-3246 then worked.

---

