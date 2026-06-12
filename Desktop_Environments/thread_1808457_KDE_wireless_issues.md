---
title: "KDE wireless issues"
date: 2011-07-20
forum: Desktop Environments
---

### Post by HoodedHooligan on 2011-07-20
I've had a growning interest in KDE for a long time and decided to try it out. I downloaded the kde packages from the software center and logged in the KDE session. I tried setting up my wireless internet on my home network but it wouuldn't work. On gnome 2, 3, and unity I usually just type in the security code but KDE won't connect. When at school, I can connect KDE to the free wireless there so I know the problem is something with the password system.

I checked the KDE forums and they say their is some type of issue with how the network manager uses the password and how there might be an update with a fix. If I could get internet access I could check for updates

---

### Post by dyrvere on 2011-07-20
> **HoodedHooligan said:**
> I've had a growning interest in KDE for a long time and decided to try it out. I downloaded the kde packages from the software center and logged in the KDE session. I tried setting up my wireless internet on my home network but it wouuldn't work. On gnome 2, 3, and unity I usually just type in the security code but KDE won't connect. When at school, I can connect KDE to the free wireless there so I know the problem is something with the password system.

I checked the KDE forums and they say their is some type of issue with how the network manager uses the password and how there might be an update with a fix. If I could get internet access I could check for updates
Can you still reach the other desktop environments? Latest version I have here in Arch Linux is the kdeplasma-applet-networkmanager 20110713 (built from git) which depends on the daemon networkmanager 1.8.9997. Is the one you're using as recent?

But can't you manually set up the network through the terminal? Follow this Wiki page to see if there is a solution to your problem, doesn't matter what Ubuntu you run, Linux is still Linux. Although skip all /etc/configurations and module-purge/load/ etc unless you really, really think it's going to help.
[https://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_management](https://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_management)
Lots of luck.

---

### Post by Simian Man on 2011-07-20
Try disabling the KDE wallet.  System Settings->Account Details->KDE Wallet.  The wallet is a system that stores all your passwords together, maybe it's causing trouble.

---

### Post by ubume2 on 2011-07-20
I set up Kubuntu 11.04 wirelessly and had problems too.

I finally had to set up a "script" 

Now for basics of wireless setup and troubleshoot I have used this url:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

This may or may not solve your problem.

G'day

---

### Post by HoodedHooligan on 2011-07-21
> **dyrvere said:**
> Can you still reach the other desktop environments? Latest version I have here in Arch Linux is the kdeplasma-applet-networkmanager 20110713 (built from git) which depends on the daemon networkmanager 1.8.9997. Is the one you're using as recent?

But can't you manually set up the network through the terminal? Follow this Wiki page to see if there is a solution to your problem, doesn't matter what Ubuntu you run, Linux is still Linux. Although skip all /etc/configurations and module-purge/load/ etc unless you really, really think it's going to help.
[https://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_management](https://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_management)
Lots of luck.

Well I tried using the Arch link and here's what I got:

[Step 0:] iwconfig wlan0 mode ad-hoc

Error for wireless request "Set Mode" (8B06):
   SET failed on device wlan0; Operation not permitted

[Step 1:] ifconfig wlan0 up

SIOCSIFFLAGS: Permission denied

[Step 2:] iwlist wlan0 scan

wlan0     No scan results

I figured I might as well stop here for the tutorials since the terminal cannot even see any connections

---

### Post by HoodedHooligan on 2011-07-21
I tried both Simian Man's and ubume2's suggestions and neither worked for me.

---

### Post by ubume2 on 2011-07-23
> **HoodedHooligan said:**
> I tried both Simian Man's and ubume2's suggestions and neither worked for me.

Sorry, I failed to notice you were using Arch KDE. Probably a simple fix, but not for me.

I set up the basic script in /etc/rc.local [Kubuntu]
I set up nearly the same script on the desktop [Kubuntu]

Reboot.

$./wirelessscriptname.sh

Hope you get it fixed! :)

---

### Post by HoodedHooligan on 2012-06-25
I never found a workable solution but newer versions of KDE do not have this issue.

---

