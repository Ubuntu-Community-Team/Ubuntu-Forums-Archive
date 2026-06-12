---
title: "[SOLVED] Dell inspiron 1525 wi-fi and webcam  problem"
date: 2008-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sagarun on 2008-06-11
I have installed ubuntu 8.04 in my dell inspiron 1525....
when i lsmod...

i can see the following modules loaded inside the kernel which are related to wireless

1.iwl3945
2.iwlwifi_mac80211 
3.cfg80211


For some reason my led which is the indicator of wi-fi is not working (not lighting up)

And also i have webcam ubuntu is not recognizing it at all!!!

please help me!

---

### Post by StefAndrew on 2008-06-11
Do you know what your wifi adapter is? Dell branded(usualy broadcom) or Intel?  And have you tried enabling the restricted drivers for the wifi as well?  Make sure you are connected to a LAN cable when you enable the LAN drivers so it can automatically set it up for you.

---

### Post by sagarun on 2008-06-11
> **StefAndrew said:**
> Do you know what your wifi adapter is? Dell branded(usualy broadcom) or Intel?  And have you tried enabling the restricted drivers for the wifi as well?  Make sure you are connected to a LAN cable when you enable the LAN drivers so it can automatically set it up for you.

Its...Intel(R)/pro wireless 3945ABG/BG wireless card....

In system->administration->hardware drivers
it shows the driver is in use.....

I think my LAN is working fine..how does a wi-fi and wired LAN related to?
(Just now i accessed my windows shares using smb)

And i also enabled restricted drivers...my problem is with the LED...and also ettercap is not listing wlan0 as an interface (when i am not connected to  any network)

---

### Post by TCTopCat on 2008-06-12
Hey I've been having some trouble setting up wifi to the point where i'm thinking about calling it a Norwegian blue and taking it to a petshop... (All monty python comments welcome :)) Could someone please tell me how you enabled your drivers/firmware on your inspiron 1525? Anything to stop me from reinstalling everything

---

### Post by treeclimber on 2008-06-12
> **TCTopCat said:**
> Hey I've been having some trouble setting up wifi to the point where i'm thinking about calling it a Norwegian blue and taking it to a petshop... (All monty python comments welcome :)) Could someone please tell me how you enabled your drivers/firmware on your inspiron 1525? Anything to stop me from reinstalling everything
Good luck on that!  I have the same wifi you have and my 1505n finds my wireless connection, but it won't connect under Hardy.  It doesn't show any restricted drivers to enable and when I checked, it showed it was using the correct driver.  It just wouldn't connect.  I hope you get an answer.

---

### Post by sagarun on 2008-06-13
hiii..I accidently fixed the problem....:guitar:

My led is working and i can see wireless networks around me...

When i looked into /var/log/daemon.log...

I found these lines

>  Jun 13 16:57:20 zer0c00l firmware_helper[10545]: main: error loading '/lib/firmware/iwlwifi-3945-1.ucode' for device '/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/firmware/0000:0b:00.0' with driver '(unknown)'


Jun 13 16:57:22 zer0c00l NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 



so i looked into /var/firmware/ but theres no iwlwifi-3945-1.ucode

but there are two directories indicating my kernel version


> 2.6.24-16-generic  2.6.24-17-generic


And i found iwlwifi-3945-1.ucode inside the 2.6.24-16-generic folder....
Just i copied that file to /var/firmware/ folder as root....

Instantly my wi-fi LED was switched on....

:D

and now i can see available networks...



Thanks guys for helping me

Lovingly
Arun SAG

---

### Post by Muflon on 2008-06-17
Hi Sagarun

Your copying of the iwlwifi-3945-1.ucode file is essentially what the linux-backports-modules-2.6.24-nn-generic does in Synaptic Package Manager (there is one for each kernel version).

After intalling a new kernel version, install the related linux-backports-modules package and you will get the same result.

See [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work) for more details.

Muflon

---

### Post by Bob Stine on 2008-07-20
I am trying to get WiFi to work on ubuntu 8.4, freshly installed on a Dell Inspiron E1405.  As for the notes on this page:
on my machine, there is no directory "firmware" under /vars.

When I tried sudo-apt-get install, I got the error
"E: Couldn't find package linux-backports-modules-2.6.24-16-generic".  At boot time, the kernel ID shown is, as typed, 2.6.24-16-generic.

help?

---

### Post by sagarun on 2008-07-20
what's your wireless chip brand and number?
Try installing linux-backport modules

$ sudo apt-get install linux-backports-modules-2.6.24-16-generic

does it recognize your wi-fi card?

---

### Post by richiecomp on 2011-08-23
EASY SOLUTION!!!

Initially, I installed Ubuntu 11.10 on the Dell Inspiron 1525 laptop.  During the installation, it claimed that there was no Internet connection, therefore it would not check for updates.  Upon finishing the installation, I tried to upload the wireless driver from the Additional Drivers option.  After clicking that button, it attempted to read the files from the installation CD.  It said the file could not be found.  I tried to search for it manually, to no avail.  I took the CD out, put it in an XP computer, and was able to fully read its content.  I found the file.  I thought, perhaps, the CD-ROM reader on the laptop was defective, and it wouldn't be able to extract the desired driver file.

I exercised a theory, and put the Ubuntu installation CD back in the laptop.  I rebooted from the CD, and chose the live-CD option (tryout).  After getting to the main menu, I went to Systems Settings, then Additional Drivers, and clicked on it.  Just like before, it would tell me that there was a Broadcom  STA wireless driver.  This time, however, when I pressed the button to install, it actually read from the CD, and installed the driver.  BUT, WAIT!!!  Remember:  this is only a live-CD session.  Therefore, if it were to be turned off, the driver would not appear upon rebooting.  Oh!  What to do?!

Well, now that I had a live-CD session with the wireless driver already installed, all I had to do was to click on the button to install Ubuntu.  While installing the operating system, this time, it actually recognized that there was an Internet connection, and would be able to install any updates.  After Ubuntu was installed, I rebooted, and confirmed that the wireless connection was active.

Note:  There might be a problem with Ubuntu reading its own media.  However, as a tryout, I installed a live USB session of Ubuntu on the same laptop, and was able to read the Ubuntu CD.  Perhaps an investigation is in order.

Here's hoping my simple solution would work for anybody's system.

---

