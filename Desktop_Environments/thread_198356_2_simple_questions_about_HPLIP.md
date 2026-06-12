---
title: "2 simple questions about HPLIP"
date: 2006-06-17
forum: Desktop Environments
---

### Post by ThirdWorld on 2006-06-17
I recently got an HP Officejet 4315v. I installed the printer but there was no driver available for it in Ubuntu 6.06. I selected the 4200 series and it printed perfectly, however it wont scan. hp-toolbox utility said that the model is not supported.
My printer is listed and supported in [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)
But it looks like the hplip version in synaptic is HPLIP 0.9.7 released back in November 2005. The new version HPLIP 1.6.6 released this month. 

I have 2 questions:  

1- how can i install the latest version of hplip? my officejet 4315v wont scan because is not supported by the old driver.

2- Why it is taking so long for the Ubuntu team to upgrade something so damn simple as an HP driver?? if the driver released in june is "too new" what about HPLIP 0.9.11 released on may???

I mean, a printer driver is not going to brake a system? you just uninstall it and install the old one and thats it.

any help will be apreciated

Thanks :)

---

### Post by audax321 on 2006-06-17
EDIT: (SORRY FOR THE CAPS, JUST WANT TO MAKE SURE YOU GET THIS EDIT :) ) HPLIP TOOLBOX JUST USES XSANE TO SCAN FROM YOUR PRINTER... SO IF YOU HAVE IT INSTALLED TRY SCANNING USING IT... EVEN IF HPLIP TOOLBOX DOESN'T WANT TO SCAN, XSANE MIGHT STILL SCAN - IF NOT THEN READ ON

Don't know about why they didn't include the latest, but to install the latest you could give this a try:

1. Uninstall the current Ubuntu hplip driver:
[INDENT]sudo dpkg --remove hplip[/INDENT]
[INDENT]sudo dpkg --remove hplip-data[/INDENT]
[INDENT]sudo dpkg --remove hplip-ppds[/INDENT]

also the following package may or may not be installed:

[INDENT]sudo dpkg --remove hplip-base[/INDENT]

WARNING: This will break and force you to remove the ubuntu-desktop metapackage. This is actually fine, just remember to reinstall this package if you ever decide to dist-upgrade your computer to a newer Ubuntu.

2. Install the version at the hplip website:

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

However, I strongly recommend that instead of doing 'sudo make install' as the last step and installing the software you get a program called 'checkinstall' from the repos. All you do is 'sudo checkinstall' rather than the 'make install' command when the step comes up. This will actually create a deb file of the installation and install it so you can easily remove the new HPLIP program at a later time using Synaptic (you should remove the new HPLIP program before reinstalling ubuntu-desktop when you do a dist-upgrade because reinstalling ubuntu-desktop will automatically reinstall the original HPLIP driver and you want to avoid any conflicts).

FINAL NOTE: I haven't done this because the HPLIP that came with Dapper works fine for my printer :p , but it should work for you.

Good Luck :KS

---

### Post by ThirdWorld on 2006-06-17
Thank you for your quick reply. I coulnt install the latest driver (1.6.6) it gave me an error message.  But I installed the 0.9.11 and it works perfectly with my printer. I created a launcher for hp-toolbox, Its so weird the installation didnt create an icon. well now i can scan so i dont need to boot in Windows XP to scan a fax anymore. \\:D/ 

and I got checkinstall, like you suggested i did sudo checkinstall instead of sudo make install.

The last thing that keeps windows alive in a small corner of my Hard drive: Adobe photoshop. 

Lets hope it will be ported some day.

---

### Post by silvagroup on 2006-06-18
ThirdWorld,
I also had the same problem, had two programs that I had to run in windows and was I getting tired of the dual boot thing. Then I found this [http://www.win4lin.com/](http://www.win4lin.com/). Now I no longer even have the option for dual boot since I can run windows under Ubuntu and works great. By the way you can try it for 15 days before you purchase.

---

### Post by odysseus_nz on 2006-06-20
And even better than Win4Lin (as it's free) is QEMU, the default package in the repository is a bit slow and old, but see the How-to post at [http://ubuntuforums.org/showthread.php?t=187413](http://ubuntuforums.org/showthread.php?t=187413) for a script to run to install the accelerated version.

John.

---

### Post by 11hjpphty76lkjj on 2006-06-20
Third World,

I'm curious what problems you had installing HPLIP 1.6.6?

Thanks!

Aaron

---

### Post by davey_mac on 2006-06-23
I followed the instructions from audax321 and hplip installed fine with checkinstall......But should I ever need ti uninstall this can you tell me how to go about this.   This is my 3rd day with Ubuntu and I quite like it...just need to sort out my TV card and scanner then goodbye windows

---

### Post by 11hjpphty76lkjj on 2006-06-23
I could be wrong..but I believe that

```

sudo apt-get remove hplip

```

Should work for the uninstall.  Although it may be hplip-1.6.6

not sure how checkinstall creates the package name.  should be something close though.

A

---

