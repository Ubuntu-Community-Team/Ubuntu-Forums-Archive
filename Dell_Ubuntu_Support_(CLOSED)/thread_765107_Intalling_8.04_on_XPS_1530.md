---
title: "Intalling 8.04 on XPS 1530"
date: 2008-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by limkin on 2008-04-24
Hi all,
after installed Ubuntu 8.04, the touchpad don´t work.
PD: I have bios version 08

---

### Post by jbeynon on 2008-04-24
as the laptop is booting, select the boot option and press e to edit the boot options, you need to add i8042.nomux=1 to the boot options then the trackpad works fine,

john.

---

### Post by spacesearcher on 2008-04-24
I'm having the same problem when using the live CD on the same comp with the same bios. I will have to try this when I can. Were there any other problems you found that I should prepare for?

---

### Post by Iwantu_ubuntu on 2008-04-24
Can you guys let me know what wireless card you have on your dell m1530's?  I'm preparing to install 8.04 on it. I have the Dell Wireless 1505 Draft 802.11n card (Broadcom)....when I tried the 7.10 live cd, the wireless card wasn't recognized and am afraid 8.04 might have the same problem.

---

### Post by Vaun on 2008-04-24
You're going to need to install ndiswrapper and make a startup script as shown below.  This has worked since Alpha 5 and is currently working now.

[http://ubuntuforums.org/showthread.php?t=734003]("http://ubuntuforums.org/showthread.php?t=734003")

---

### Post by sgtbug on 2008-04-25
i'd recommend bcm43xx since ndiswrapper did not work for me.. :S

bcm43xx is working perfect.. u just need to unblacklist it..

---

### Post by sgtbug on 2008-04-25
here is my method to do it..

[http://ubuntuforums.org/showpost.php?p=4629707&postcount=16](http://ubuntuforums.org/showpost.php?p=4629707&postcount=16)

cheers! although b44 cards get screwed by it..

---

### Post by jespdj on 2008-04-25
> **limkin said:**
> Hi all,
after installed Ubuntu 8.04, the touchpad don´t work.
PD: I have bios version 08
You need to boot Ubuntu with the following kernel parameter:
```
i8042.nomux=1
```
See [my page](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530).

Thanks to bbroth who posted it [here](http://ubuntuforums.org/showthread.php?t=737060).

---

### Post by limkin on 2008-04-25
Thank you at all!! The problem fixed.
Somebody know why the botton of expulse cd don'k work?
In gutsy gybon don't work to.

---

### Post by Iwantu_ubuntu on 2008-05-03
> **Vaun said:**
> You're going to need to install ndiswrapper and make a startup script as shown below.  This has worked since Alpha 5 and is currently working now.

[http://ubuntuforums.org/showthread.php?t=734003]("http://ubuntuforums.org/showthread.php?t=734003")


Thanks a lot, this ndiswrapper method worked for me.  I tried coolaks suggestions first and unfornately it didn't quiet work, not sure if I did something wrong, but the ndiswrapper method pretty much worked first time.

The only problem I'm encountering is that Network Manager doesn't remember my ssid/wpa key.  I have a hidden ssid and everytime I boot up Ubuntu I have to manually create a new wireless connection and then put in the ssid and wpa key and then hit connect .  Is there any workaround to avoid this and just connect automatically to my wap.  It actually connects to a open linksys automatically (a neighbor).

---

### Post by Vaun on 2008-05-04
I've uninstalled Network Manager and have been using wicd.  It seems to work better with much less connectivity issues.  Just follow the installation instructions listed below and add the repository.

[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

---

### Post by Iwantu_ubuntu on 2008-05-04
> **Vaun said:**
> I've uninstalled Network Manager and have been using wicd.  It seems to work better with much less connectivity issues.  Just follow the installation instructions listed below and add the repository.

[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

Thanks, I'll give it a try. I read that wicd broke someones settings so I was a bit hesitant to try it before exhausting any fixes for Network Manager.  Looks like we have similar specs on the m1530, is your WAP configured with WPA and hidden SSID? TIA

---

### Post by ParvathReddy on 2008-05-07
I am pretty much in the same situation... will try ndiswrapper  when I get home

---

### Post by Iwantu_ubuntu on 2008-05-07
Ok, tried wicd with no success.  I ended up enabling SSID broadcast and although wicd picked up my WAP, it wouldn't connect and get a IP. I ended up reinstalling Network Manager and it connects to my WAP with WPA just fine.  The only annoying thing is that it still connects to a open linksys WAP instead of my WLAN perhaps because it has a stronger signal?... I just manually choose my WAP and connect to it after booting up.

---

