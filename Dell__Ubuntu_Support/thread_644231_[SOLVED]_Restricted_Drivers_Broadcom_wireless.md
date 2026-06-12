---
title: "[SOLVED] Restricted Drivers: Broadcom wireless"
date: 2007-12-18
forum: Dell  Ubuntu Support
---

### Post by Dodelijk on 2007-12-18
Hello All, 

I guess this post should go here. 

I'm trying to get my wireless working on my D630. When i go to 'Restricted Drivers' i see an entry for "Firmware for Broadcom 43xx chipset family' which is 'not in use'. 
If i check the Enabled-box i get a message-box saying "Enble Firmware" and some text about the driver relying on proprietary firmware. If i now click 'Enable' i get an error:

"The software source for the package
bmc43xx-fwcutter 
is not enabled"

What do i need to do to get this working ? 

Thanks .....

---

### Post by Dodelijk on 2007-12-18
Ok, inorder to get beyond this message either build-essentials or update needs to be run/installed. 

Connect to the internet with a cable and run these commands:

sudo apt-get update
sudo apt-get install build-essential


I'm still stuck on getting this wireless adapted to work though....

---

### Post by Dodelijk on 2007-12-18
Ok, so i've got it working. 

You need to do what i've said above. and then a dialog will come up asking you to locate the firmware. you need to select the internet option. It has this as the address "http://xeve.de/down/wl_apsta.o"
Then it should be working. You'll need to use a cable of course to do this. I guess you could download the file on another computer and then locate it manually after
enjoy

---

### Post by Monkey_Tales on 2007-12-19
Broadcom wireless program and drivers [U]

[http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-internet.tar.gz](http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-internet.tar.gz)[/U]

---

### Post by pat09 on 2007-12-20
Is there any way you can do this on  another computer and transfer the information via flash drive?

---

### Post by Dodelijk on 2007-12-21
i think you can install the build-essentials without an internet connection and then using the web address i provided go on to another computer and download the file then go through the steps i outlined above and source the required file from your flask disk

---

### Post by ayu on 2007-12-22
Hi, I just made the upgrade to Gutsy on my Vostro, (was using ndiswrapper, installed via a script posted on these forums), and was stuck a while on the restricted drivers firmware (the internet option kept giving me errors).  I went ahead and downloaded [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) from [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43).  Is this the same file?  I have trouble connecting to my router using my broadcom wireless, and it only become stable after connecting/disconnecting for 10 minutes or so (and keeps asking for my router passphrase although I have it saved in my keyring).  Also, is it still using ndiswrapper or does Gutsy use something else?

---

### Post by ayu on 2007-12-27
Hello, should I start a new thread as this one is marked solved?  Giving a quick bump for now, many thanks!

---

### Post by arron on 2007-12-28
Hi.

This horse has been kicked hard in another thread.  Check this thread out:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

The install is in the first threw posts.  If you read threw the other 180+ pages, the just is the restricted drivers are not as fast or good at picking up the signals.  I installed this with the gutsy cd and the downloaded file without any problems.  It works like a champ, and for me the speed it wayyyy better.

---

### Post by ayu on 2007-12-30
Hello,
So ndiswrapper is suppose to be better than the restricted drivers?  I was using ndiswrapper in Feisty and the connection was also always flaky.
Thanks

Edit: Actually, according to network manager, my active connection is using ndiswrapper... although I did install the restricted drivers after the upgrade
Edit2: My issue might be more complex than I thought, so I went ahead and made another thread at [http://ubuntuforums.org/showthread.php?p=4041534](http://ubuntuforums.org/showthread.php?p=4041534)

---

