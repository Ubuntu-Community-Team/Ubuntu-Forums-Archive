---
title: "VirtualBox: Windows XP USB issue"
date: 2010-10-03
forum: Desktop Environments
---

### Post by Merthod on 2010-10-03
Hi, I just installed Windows XP in VirtualBox (3.2.8) in Ubuntu 10.04.1 LTS. I have an USB issue, so I looked for more info in both the documentation and forums and found some answers. However, they haven't worked for me.

THE PROBLEM: Windows XP can't recognize my connected USB devices (my external hard drive and ipod)

SOLUTIONS TRIED: I added myself in the *vboxusers* group so my **etc/group** file reads like this: [FONT="Courier New"]vboxusers:x:128:myuser[/FONT]

This is what VirtualBox documentation says about doing this:
[FONT="System"]On newer Linux hosts, VirtualBox accesses USB devices through special files in the file system. When VirtualBox is installed, these are made available to all users in the vboxusers system group. In order to be able to access USB from guest systems, make sure that you are a member of this group.[/FONT]

Then, in the VirtualBox main window, I clicked "Settings" on my virtual XP installation. In the "USB" option group I have both "Enable USB Controlled" and "Enable USB 2.0 (EHCI) Controller" checked, then added both my external hard drive and ipod through the "Add Filter from Device (Alt+Ins)", and have both checked. 

Still, Windows XP won't recognize any of my USB devices. Any help will be appreciated.

If it is helpful, in XP, System->Properties->Hardware->Devices my USB ports are recognized.

---

### Post by wilee-nilee on 2010-10-03
I might have missed it but are you running the Vbox from synaptic or the software center, rather then the download from Oracle.

---

### Post by PhilGil on 2010-10-03
I assume you're using the right version of VBox, the PUEL version from the website? In the past I've had to reboot my computer before the USB devices were recognized in VirtualBox. I'd give that a try.

---

### Post by Merthod on 2010-10-03
Thanks for your promptly answers. 

wilee-nilee: I installed VirtualBox from Ubuntu's Software Center (virtualbox-3.2).

PhilGil: I rebooted then and I have rebooted again now. It still doesn't work. I ran this command:

[FONT="Courier New"]dpkg -l virtualbox*[/FONT]

And it returned this:

[FONT="Courier New"]Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  virtualbox     <none>         (no description available)
ii  virtualbox-3.2 3.2.8-64453~Ub Oracle VM VirtualBox
un  virtualbox-ose <none>         (no description available)[/FONT]

So I assume I have PUEL version installed.

---

### Post by PhilGil on 2010-10-03
> **Merthod said:**
> I installed VirtualBox from Ubuntu's Software Center (virtualbox-3.2).
So I assume I have PUEL version installed.
There's your problem right there. The version of VirtualBox in the repository is the Open Source Edition, not the PUEL version. You need to get the PUEL version from the web: [http://www.virtualbox.org/wiki/VirtualBox_PUEL .]("http://www.virtualbox.org/wiki/VirtualBox_PUEL")

Uninstall the version from the repo, install the version from the web (you can download the deb file or there might be a repo -- it's been a while since I've installed VBox in Ubuntu). You should still be able to use the virtual hard disk you've already created.

---

### Post by wilee-nilee on 2010-10-03
> **PhilGil said:**
> There's your problem right there. The version of VirtualBox in the repository is the Open Source Edition, not the PUEL version. You need to get the PUEL version from the web: [http://www.virtualbox.org/wiki/VirtualBox_PUEL](http://www.virtualbox.org/wiki/VirtualBox_PUEL)

Argh Matey you be correct.;)

---

### Post by Merthod on 2010-10-03
Alright then, I'll install this package. I found that there's an Ubuntu specific .deb package for 10.04 and others, just for you to know.

I'll try it and report to you. Thank you.

---

### Post by Merthod on 2010-10-04
Well... before I tried to install this version I tried a last time and amazingly they worked. Now I'm happy and I think that's it. Now I'll focus to my next problem...

Tanks for your help.

---

### Post by mister_p_1998 on 2010-10-04
Had this problem for ages on Lucid, the only way I got it to work was running VirtualBox as root, not a great idea but it works.
Steve

---

### Post by TNT1 on 2010-10-04
A related question, I have a samsung mobile, I have installed the pc suite on my virtualbox, xp, set up the usb filter, and in devices it shows the samsung, but it's greyed out, and I can't select it. On the Lucid host, lsusb shows the samsung, but it's not mounted. What can I do?

---

### Post by Merthod on 2010-10-04
> A related question, I have a samsung mobile, I have installed the pc suite on my virtualbox, xp, set up the usb filter, and in devices it shows the samsung, but it's greyed out, and I can't select it. On the Lucid host, lsusb shows the samsung, but it's not mounted. What can I do?

First check whether you are or are not in the *vboxusers* user group. Avoiding the terminal you can do this in two ways: 
[LIST=1]
[*]Go to System->Administration->Users and Groups. In that window, click on "Groups", then find *vboxusers* in the list, double click it and check your user so you are included.
[*]Navigate to /etc and open the "group" file. In there it should be a line for this group like this: [FONT="Courier New"]vboxusers:x:128[/FONT]. You edit it so it reads like this: [FONT="Courier New"]vboxusers:x:128:your-ubuntu-username[/FONT] and save.
[/LIST]

Reboot your VirtualBox instance. In my case I also rebooted Ubuntu, although I'm not sure whether it is necessary but it doesn't do any harm. I loaded up Windows and finally saw my drive in black in USB Devices. I had to wait a little though since the disk didn't mount right away in Windows. It is also recommended that you boot up without the drive mounted in VirtualBox since the load up can be VERY slow.

Also be sure to add the filter **from device** since if you did it manually you may have made a mistake. The option is right there.

---

### Post by LuthienT on 2011-08-07
related problem - I have added my to the vboxusers group , except that in the 'settings' box in Virtual Box, it doesn't have a 'USB' menu. There simply isn't anything there. I know [http://techtooltip.wordpress.com/2008/09/22/how-to-use-host-usb-device-from-guest-in-virtual-box/](http://techtooltip.wordpress.com/2008/09/22/how-to-use-host-usb-device-from-guest-in-virtual-box/) has an image that shows my settings window is supposed to look like this:
[IMG]http://techtooltip.files.wordpress.com/2008/09/vbusb_virtualboxconfiguration1.jpg[/IMG]but all my settings shows me are the following options:

[IMG]http://i1099.photobucket.com/albums/g385/LuthienT/Screenshot.png?t=1312738401[/IMG]any help on rectifying this problem? I know I have the OSE version, but I've checked for extension packs and the VBoxManage list tells me that I have "usbhost" which is supposed to provide info and options regarding USB devices.

---

### Post by PhilGil on 2011-08-07
> **LuthienT said:**
> I know I have the OSE version, but I've checked for extension packs and the VBoxManage list tells me that I have "usbhost" which is supposed to provide info and options regarding USB devices.
The OSE version does not support USB, regardless of what the documentation may say. You have to use the PUEL version from the VirtualBox website [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) .

---

### Post by wildmanne39 on 2011-08-07
Hi, also you need to add an empty filter to make usb work.

---

### Post by LuthienT on 2011-08-10
got PUEL, added filter, thanks.

---

