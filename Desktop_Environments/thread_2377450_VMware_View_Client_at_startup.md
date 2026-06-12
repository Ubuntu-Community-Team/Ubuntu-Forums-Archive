---
title: "VMware View Client at startup"
date: 2017-11-13
forum: Desktop Environments
---

### Post by blurmcclure18 on 2017-11-13
My work is transitioning towards a virtual environment and we just received windows embedded Dell Thin clients that we will be using in the office, however users will be taking their current laptops home with them to tele-work on their approved days. 

Since we will no longer want to manage these laptops with windows updates and antivirus updates I made the suggestion of running either Ubuntu or Lubuntu on these machines to avoid all of that. I have been testing a way to make the OS invisible to the users as most of them barely know how to use windows let alone even seen a Linux distro. 

I have edited the */etc/default/grub* line to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash 3"
``` for a text only interface and edited the */etc/rc.local* file to ```
xinit /usr/bin/vmware-view --fullscreen
``` so as to launch the view client after drivers have been loaded so the user should only have to login to the vmware client. 

However in testing this after logging into the vmware client and attempting to connect to a virtual machine the connection will be attempted, a black screen will appear for a short duration then disappear back to the pool selection screen. 

I have also noticed that while in the rc.local file i specified --fullscreen for the vmware client, after it launches only takes up a small corner of the screen. I have confirmed that it works under normal boot into the GUI just fine. I have been testing this in virutalbox running Ubuntu 16.04 and on one of the older laptops i have awaiting disposal.

---

