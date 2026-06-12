---
title: "errors re-installing firefox"
date: 2010-07-11
forum: Desktop Environments
---

### Post by fritzman on 2010-07-11
I began having troubles with firefox, default installation at install of Lucid, a week or so ago.  Plugins did not work, and at the prompt (yellow bar at top of web page) I would elect to install missing plugins.  It would return with the message that xxxplugin was already installed.  
There are multiple threads associated with plugin problems with firefox, and following the suggested fixes, nothing seemed to help.
I have the 64bit version of Lucid;
$ sudo lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
$ uname -a
Linux uglybox 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

So, I uninstalled firefox with synaptic, opting for complete removal.  Then I try to re-install firefox, and get the following;
$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-branding
Suggested packages:
  firefox-gnome-support kmozillahelper
The following NEW packages will be installed:
  firefox firefox-branding
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 12.7MB of archives.
After this operation, 37.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main firefox-branding 3.6.7+build1+nobinonly-0ubuntu0.10.04.1 [207kB]
Get:2 [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main firefox 3.6.7+build1+nobinonly-0ubuntu0.10.04.1 [12.5MB]
Fetched 12.7MB in 1min 17s (164kB/s)                                           
Selecting previously deselected package firefox-branding.
(Reading database ... 265273 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6.7+build1+nobinonly-0ubuntu0.10.04.1_amd64.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.6.7+build1+nobinonly-0ubuntu0.10.04.1_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up firefox-branding (3.6.7+build1+nobinonly-0ubuntu0.10.04.1) ...
Setting up firefox (3.6.7+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thunderbird still works without problems.  I installed Seamonkey, and it has the same problem with plugins that firefox has, although there is no error message, (yellow bar at top of web page) regarding missing plugins.
But, at least it will install.

Can anyone give me a clue as to what might fix this problem with firefox?
I'd really appreciate it.
Thanks,
owa

---

### Post by flick on 2010-07-11
Looks like you have set up your system to get Firefox from a PPA rather than the officially supported repos. PPAs are great if you just have to have some newer version of something, but the only guarantee with PPA stuff is that it built...not necessarily that it will run successfully.

If it were me having this issue : I would remove the PPA for Firefox from my /etc/sources.list, uninstall Firefox, then install it / reinstall it from the official repos only. 

I am using 64 Lucid, and the official repo version of Firefox works splendidly for me with all plugins I need ( Flash and gecko-mediaplayer ).

---

### Post by fritzman on 2010-07-11
Thanks for the quick response, flick.  I removed the PPA from sources, and tried again, with the same results;
$ sudo apt-get remove --purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox* firefox-branding*
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 37.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 265525 files and directories currently installed.)
Removing firefox-branding ...
Removing firefox ...
Purging configuration files for firefox ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for python-support ...
al@uglybox:/etc/apt$ sudo apt-get clean firefox
al@uglybox:/etc/apt$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-branding
Suggested packages:
  firefox-gnome-support kmozillahelper
The following NEW packages will be installed:
  firefox firefox-branding
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 12.7MB of archives.
After this operation, 37.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox-branding 3.6.6+nobinonly-0ubuntu0.10.04.1 [207kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox 3.6.6+nobinonly-0ubuntu0.10.04.1 [12.5MB]
Fetched 12.7MB in 34s (370kB/s)                                                
Selecting previously deselected package firefox-branding.
(Reading database ... 265261 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6.6+nobinonly-0ubuntu0.10.04.1_amd64.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.6.6+nobinonly-0ubuntu0.10.04.1_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up firefox-branding (3.6.6+nobinonly-0ubuntu0.10.04.1) ...
Setting up firefox (3.6.6+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)

The first error mentioned above is "error: alternative path /usr/bin/firefox doesn't exist."

And the results of a search for firefox produces;
$ whereis firefox
firefox: /usr/bin/firefox.ubuntu /etc/firefox /usr/lib/firefox /usr/lib64/firefox
So, I removed all traces of firefox from my system and tried again, with the exact same result.
$ sudo apt-get install firefox -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-branding
Suggested packages:
  firefox-gnome-support kmozillahelper
The following NEW packages will be installed:
  firefox firefox-branding
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 12.7MB of archives.
After this operation, 37.8MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox-branding 3.6.6+nobinonly-0ubuntu0.10.04.1 [207kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox 3.6.6+nobinonly-0ubuntu0.10.04.1 [12.5MB]
Fetched 12.7MB in 34s (370kB/s)                                                
Selecting previously deselected package firefox-branding.
(Reading database ... 265261 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6.6+nobinonly-0ubuntu0.10.04.1_amd64.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.6.6+nobinonly-0ubuntu0.10.04.1_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up firefox-branding (3.6.6+nobinonly-0ubuntu0.10.04.1) ...
Setting up firefox (3.6.6+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)

$ whereis firefox
firefox: /usr/bin/firefox.ubuntu /etc/firefox

$ sudo mv /usr/bin/firefox.ubuntu /usr/bin/firefox

And, now it looks like it's working.... so far, anyway.

Thanks again for being the "other set of eyeballs!"  I don't recall when or why the PPA got added to the sources, but that was probably the culprit all along.
I still don't understand why the installer named /usr/bin/firefox.ubuntu as it did.  Changing it to /usr/bin/firefox seems to have solved that, though.
Thanks again.
owa

---

### Post by flick on 2010-07-11
Happy to have been the other set of eyeballs. Sometimes thankfully that's all it takes. I've done my share of "oh...huh...I guess I did...well crap..." :)

---

### Post by lovinglinux on 2010-07-11
> **fritzman said:**
> 
$ whereis firefox
firefox: /usr/bin/firefox.ubuntu /etc/firefox

$ sudo mv /usr/bin/firefox.ubuntu /usr/bin/firefox

And, now it looks like it's working.... so far, anyway.

Thanks again for being the "other set of eyeballs!"  I don't recall when or why the PPA got added to the sources, but that was probably the culprit all along.
I still don't understand why the installer named /usr/bin/firefox.ubuntu as it did.  Changing it to /usr/bin/firefox seems to have solved that, though.
Thanks again.
owa

That was a divertion issue. I don't think it was created by the PPA, since the developers do not recommend diverting firefox.

It was probably created by a installation script or command you entered.

---

