---
title: "Inspiron 1525 11.04 Broadcom 43XX Wireless Install"
date: 2011-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Lucky8Media on 2011-04-28
Tested On Dell Inspiron 1525, vanilla install of Natty Narwhal 11.04, using LiveCD, Broadcom BCM 43XX

[Note] No need to be connected to the Internet!

_Step 1: _

Double Click Following File From Ubuntu 11.04 LiveCD or equivalent:

Ubuntu 11.04 i386 -> pool -> main -> d -> dkms -> dkms_2.1.1.2-5ubuntu1_all.deb (double click)

Ubuntu Software Center will open up and press install on your right to, you know, install.

[Warning] DKMS is requirement to install the BCM43XX Wireless Driver

_Step 2:_

Double Click Following File From Ubuntu 11.04 LiveCD or equivalent:

Ubuntu 11.04 i386 -> pool -> restricted -> b -> bcmwl -> bc,wl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb

Ubuntu Software Center will open up and press install on your right to, you know, install.

_Step 3:_

Restart!

_Step 4: _

Connect to Internet!

_Step 5:_

Enjoy!

---

### Post by jasonmanchu on 2011-04-28
oh that's a great solution. I feel so humiliated because mine is too verbose. 
[http://ubuntuforums.org/showthread.php?p=10717295](http://ubuntuforums.org/showthread.php?p=10717295)
Note: I think this works only for STA drivers
BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, and **BCM43228

---

### Post by Lucky8Media on 2011-04-28
> **jasonmanchu said:**
> oh that's a great solution. I feel so humiliated because mine is too verbose. 
[http://ubuntuforums.org/showthread.php?p=10717295](http://ubuntuforums.org/showthread.php?p=10717295)
Note: I think this works only for STA drivers
BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, and **BCM43228

No my friend just different... there are different needs for different people and  I am sure you have helped alot of people out!

---

### Post by drauger on 2011-04-29
A nutty bug of the Natty Narwhal- they just forgot to include some packets :)

---

### Post by Ratzian on 2011-04-29
I have a dell inspiron with broadcom BCM4313 and after a fresh install, networking worked perfectly on 11.04.

After a while the additional divers appeared and I installed the STA wireless (I said why not if I also install ati catalyst). Networking worked after that, but after I once disabled networking using the function key, networking completely stoped working.

The sollution was to remove the STA driver and after that networking returned to normal (both wired and wireless).

The conclusion: Never try to fix anything that isn't broken.

---

### Post by irv on 2011-04-29
I also have the Broadcom STA  (BCM4311), and followed the instructions and nothing works. Did a reinstall, and uninstall, and reinstall. Rebooting and still now wifi. I can plug in the cable and it works but now wireless.

---

### Post by renbulao on 2011-04-30
My HP Presario V3000 on BCM-4311 also does not work following the instructions above. It worked in Ubuntu 10.10 though.

---

### Post by irv on 2011-04-30
> **renbulao said:**
> My HP Presario V3000 on BCM-4311 also does not work following the instructions above. It worked in Ubuntu 10.10 though.
Yes, I got it to work in 10.04, 10.10 but it will not work with 11.04. Something is different in 11.04 and needs to be fix for other with this same card. If you have a live CD try it, and if you have a 4311, good chances it will not work.
I have had problems with this card since I got this Dell, and I just order a different card, one with Intel chips. When I install the card when I get it, I will keep you posted.

---

### Post by omnitech_human on 2011-04-30
I can confirm that I cannot power-on the BCM4311 (Inspiron e1505) card on 11.04. 

Perhaps it has something to do with the Fn shortcuts? The rest of the Fn+ shorcuts work except bluetooth, disc drive tray and wireless card and I believe this suggests that NN is unable to communicate with hardware using Fn shortcuts at all.

---

### Post by irv on 2011-04-30
> **omnitech_human said:**
> I can confirm that I cannot power-on the BCM4311 (Inspiron e1505) card on 11.04. 

Perhaps it has something to do with the Fn shortcuts? The rest of the Fn+ shorcuts work except bluetooth, disc drive tray and wireless card and I believe this suggests that NN is unable to communicate with hardware using Fn shortcuts at all.

This might have something to do with it also: I read this on the Additional Drivers dialog box:
> Proprietary drivers do not have public source code that Ubuntu developers are free to modify.  Security updates and corrections depend solely on the responsiveness of the manufacturer.  Ubuntu cannot fix or improve these drivers.

---

### Post by omnitech_human on 2011-04-30
> **irv said:**
> This might have something to do with it also: I read this on the Additional Drivers dialog box:
No, that warning's been there since... forever. I recall seeing it in LL.

---

### Post by Traktion on 2011-05-01
I had issues with my Inspiron 6400 with the broadcom 4311, after I upgraded from 10.10. It worked before the upgrade, but failed after the upgrade, giving me many hours of head scratching. The STA driver was present in 'additional drivers', but it didn't seem to work.

I added the following to the end of /etc/modprobe.d/blacklist-bcm43.conf:

'; modprobe --ignore-install b43'

I had also installed some other stuff, when trying to get it working and I'm not sure it is using the STA driver at all now:

'sudo apt-get install bcmwl-kernel-source b43-fwcutter'

TBH, I was just glad to get it working and I'm hoping that those who know the system better will find the above useful. If nothing else, it may help someone else to get their b43xx device working again!

---

### Post by irv on 2011-05-01
> **Traktion said:**
> I had issues with my Inspiron 6400 with the broadcom 4311, after I upgraded from 10.10. It worked before the upgrade, but failed after the upgrade, giving me many hours of head scratching. The STA driver was present in 'additional drivers', but it didn't seem to work.

I added the following to the end of /etc/modprobe.d/blacklist-bcm43.conf:

'; modprobe --ignore-install b43'

I had also installed some other stuff, when trying to get it working and I'm not sure it is using the STA driver at all now:

'sudo apt-get install bcmwl-kernel-source b43-fwcutter'

TBH, I was just glad to get it working and I'm hoping that those who know the system better will find the above useful. If nothing else, it may help someone else to get their b43xx device working again!

I gave this a try. This is what I came up with. First I added the line to the blacklist-bcm43.conf and this is what happen in the terminal: 

```
sudo gedit /etc/modprobe.d/blacklist-bcm43.conf
[sudo] password for irv: 

(gedit:15134): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.HC6GUV': No such file or directory

(gedit:15134): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```
It allow me to add the line, but it looks like it wanted to create something in the /root/.local/share/recently-used.xbel.HC6GUV but failed.
After playing around with removing the STA driver, it would delete the blacklist-bcm43.conf file. If I reinstall the STA driver it comes back and I have to all the line again.
[COLOR="Red"]The bottom line is no matter what I do the wireless card does not work.[/COLOR]
Oh yes, I did do the install:
```
sudo apt-get install bcmwl-kernel-source b43-fwcutter
```

---

### Post by Traktion on 2011-05-01
Have you tried just running the following in the console:

sudo modprobe --ignore-install b43

I tried the above and my wireless sprung into life moments later.

Also, have you tried using the text based editor 'nano' instead? I'm not sure what those permissions issues are, but they look to be due to 'gedit'.

---

### Post by irv on 2011-05-01
> **Traktion said:**
> Have you tried just running the following in the console:

sudo modprobe --ignore-install b43

I tried the above and my wireless sprung into life moments later.

Also, have you tried using the text based editor 'nano' instead? I'm not sure what those permissions issues are, but they look to be due to 'gedit'.

OK, I did the edit with nano the text based editor, and no errors. I then did the command 
> sudo modprobe --ignore-install b43
Tried it a couple of times and nothing happens.
This one really has me puzzled.  I guess the only thing I didn't try yet is to install the windows driver with ndiswrapper. I don't want to do this if I can help it.

---

### Post by Traktion on 2011-05-02
> **irv said:**
> OK, I did the edit with nano the text based editor, and no errors. I then did the command 

Tried it a couple of times and nothing happens.
This one really has me puzzled.  I guess the only thing I didn't try yet is to install the windows driver with ndiswrapper. I don't want to do this if I can help it.

Ah, sorry to hear that. I thought it was worth posting, just in case it was of any use. Good luck with finding the problem!

---

### Post by patslap on 2011-05-02
```
sudo modprobe --ignore-install b43
```
This worked and resolved my wireless/wifi problems; I too have a Broadcom 4311, in an Acer Extensa 5220 laptop

I reinstalled restricted STA drivers in the 'additional drivers' section in applications.

Then I entered ```
sudo modprobe --ignore-install b43
```

Then I clicked on the wifi radar in the top panel and enabled wireless networks. A few seconds later nothing had happened, so i used the wireless slider (switches wireless card on/off) on the laptop and wireless networks became available and I was autoconnected to my default wireless network.

Thanks for the help - I had tried about 5 previous solutions before but this is the only one that worked for me.

---

### Post by irv on 2011-05-02
I am glad that others have gotten there wireless going, but here is where I am sitting with mine.
[ATTACH]190818[/ATTACH]
As you can see from my screen shot, I have the firmware installed, but it says it is not. This one really has me scratching my head.

---

### Post by Traktion on 2011-05-02
> **irv said:**
> I am glad that others have gotten there wireless going, but here is where I am sitting with mine.
[ATTACH]190818[/ATTACH]
As you can see from my screen shot, I have the firmware installed, but it says it is not. This one really has me scratching my head.

I remember getting something like that before I rebooted and did the modprobe. There is definitely some sort of limbo state going on with the 43xx wireless configuration.

You could try doing 'modprobe -l | grep b4' and seeing if the module is loading ok too? You may have a different problem to what I experienced, but it does look/sound familiar!

---

### Post by Traktion on 2011-05-02
> **patslap said:**
> 
Thanks for the help - I had tried about 5 previous solutions before but this is the only one that worked for me.

Good stuff! I'm glad I posted it up now then! :)

---

### Post by irv on 2011-05-02
> **Traktion said:**
> I remember getting something like that before I rebooted and did the modprobe. There is definitely some sort of limbo state going on with the 43xx wireless configuration.

You could try doing 'modprobe -l | grep b4' and seeing if the module is loading ok too? You may have a different problem to what I experienced, but it does look/sound familiar!

I tried this and here is my out put:
```
kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/cxgb4/cxgb4.ko
kernel/drivers/net/cxgb4vf/cxgb4vf.ko
kernel/drivers/net/b44.ko
kernel/drivers/infiniband/hw/cxgb4/iw_cxgb4.ko

```

---

### Post by Traktion on 2011-05-02
> **irv said:**
> I tried this and here is my out put:
```
kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/cxgb4/cxgb4.ko
kernel/drivers/net/cxgb4vf/cxgb4vf.ko
kernel/drivers/net/b44.ko
kernel/drivers/infiniband/hw/cxgb4/iw_cxgb4.ko

```

Hmm, it looks like the module is definitely loaded then. I think you must have a different problem to the one I had after all!

---

### Post by irv on 2011-05-02
Well, I got a different wifi card today and installed it, but I believe I got a bad card. It was used and I got it off ebay. Win7 and Ubuntu did not even recognize it. So I am back to the Broadcom card.

It looks like I have no other choice but to go back to 10.10 if I can't get this one to work. I will play around a little longer that I will just install 10.10. I can't believe I am going to do this, because I was just starting to like Unity.
Thanks for all you help on this one.

---

### Post by irv on 2011-05-02
Well, like I said earlier, I didn't want to try ndiswrapper but I was going to give it a shot. wouldn't you know there is a bug report on ndiswrapper in 11.04. 
> ErrorMessage: ndiswrapper kernel module failed to build
Back to square one. I guess I am not going to try that.

I am going to give one more card a try before going back to 10.10. The card is going to be shipped today, hopefully I will have it by next week.

One good thing is I have another hard drive setup with 10.10 already setup on it. When I go on the road (next Thursday) I will just pop that one in and I will be good to go.

---

### Post by irv on 2011-05-02
[COLOR="Red"]Praise the LORD!!! I got it to work.[/COLOR]

I fixed my problem with the Broadcom BCM4311 driver in 11.04.
Here is what I did. 
1. I uninstalled &#8220;bcmwl-kernel-source&#8221; package,
```
sudo apt-get remove bcmwl-kernel-source
```
2. I installed &#8220;firmware-b43-installer&#8221; package
```
sudo apt-get install firmware-b43-installer
```
3. I installed &#8220;b43-fwcutter&#8221; packager
```
sudo apt-get install b43-fwcutter
```
4. I typed into the terminal:
```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

This was the out put:
> # which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt


Now I am going to reboot and hopefully it will keep working.

Edit: After rebooting everything still works.

---

### Post by irv on 2011-05-02
The last thing I notice was I am not using the Broadcom STA driver.
[ATTACH]190886[/ATTACH]

---

### Post by Traktion on 2011-05-02
> **irv said:**
> The last thing I notice was I am not using the Broadcom STA driver.
[ATTACH]190886[/ATTACH]

This is the same for me too, but mine said it was activated but not in use.

I just removed the STA driver, then rebooted and it broke the wireless networking again. However, I did a 'modprobe b43' and it came back to life again, but I noticed '/etc/modprobe.d/blacklist-bcm43.conf' had gone too.

So, I added 'b43' to /etc/modules, rebooted again and it worked again. It looks like the STA driver doesn't work for the b4311 any longer (or at least not on my Dell Inspiron 6400), but the b43 module, with b43-fwcutter, does. However, for some reason the b43 module wasn't being loaded by default on my machine, but adding it to /etc/modules fixed that.

---

### Post by irv on 2011-05-02
> **Traktion said:**
> This is the same for me too, but mine said it was activated but not in use.

I just removed the STA driver, then rebooted and it broke the wireless networking again. However, I did a 'modprobe b43' and it came back to life again, but I noticed '/etc/modprobe.d/blacklist-bcm43.conf' had gone too.

So, I added 'b43' to /etc/modules, rebooted again and it worked again. It looks like the STA driver doesn't work for the b4311 any longer (or at least not on my Dell Inspiron 6400), but the b43 module, with b43-fwcutter, does. However, for some reason the b43 module wasn't being loaded by default on my machine, but adding it to /etc/modules fixed that.

Yes, something changed so that the STA driver does not work, So we are both using the b43. I read on facebook that the STA driver is better that the b43. It was said that it runs slower and gets a weaker signal. Well, time will tell. I did a speed check on the wire and on the wifi, and here is what I saw. The first is on the wire:
[ATTACH]190905[/ATTACH]

[ATTACH]190906[/ATTACH]

I don't see much of a difference. Not enough to worry about.

---

### Post by MurphysLaww on 2011-05-03
Just adding some of my experience.

Unfortunately, I tried enough different things that I'm not sure what worked. 

I tried the sudo modprobe --ignore-install b43 at the beginning of this thread with no luck, then went to another thread, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

and downloaded and extracted the firmware again, then someone had replied to my beginner question here: 

[http://ubuntuforums.org/showthread.php?p=10761161#post10761161](http://ubuntuforums.org/showthread.php?p=10761161#post10761161)

mentioning that I should SHUT THE MACHINE DOWN instead of restarting it. I did this, and re-ran 

sudo modprobe --ignore-install b43 

and it worked! If I had to guess, it was the shutting the machine down that did it, but it is just a guess. 

hope that helps someone in a similar situation.

***edit***

Ahh, if it were only that simple. I now have to run that command everytime I startup to get my wireless now.

---

### Post by Traktion on 2011-05-03
> **MurphysLaww said:**
> Just adding some of my experience.

Unfortunately, I tried enough different things that I'm not sure what worked. 

I tried the sudo modprobe --ignore-install b43 at the beginning of this thread with no luck, then went to another thread, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

and downloaded and extracted the firmware again, then someone had replied to my beginner question here: 

[http://ubuntuforums.org/showthread.php?p=10761161#post10761161](http://ubuntuforums.org/showthread.php?p=10761161#post10761161)

mentioning that I should SHUT THE MACHINE DOWN instead of restarting it. I did this, and re-ran 

sudo modprobe --ignore-install b43 

and it worked! If I had to guess, it was the shutting the machine down that did it, but it is just a guess. 

hope that helps someone in a similar situation.

***edit***

Ahh, if it were only that simple. I now have to run that command everytime I startup to get my wireless now.

There are a couple of things which may help when restarting in this thread. Removing the STA driver and then adding 'b43' to '/etc/modules' seemed to work well for me.

---

### Post by irv on 2011-05-03
> Ahh, if it were only that simple. I now have to run that command everytime I startup to get my wireless now.

Or you could add the command in the "Startup Applications" and it would run every time you startup. At least that way you would not have to type it every time.
One more thing, Seeing I do not have STA installed, I do not have the blacklist-bcm43.conf in the /etc/modprobe.d/ so I don't have the line ; modprobe --ignore=install b43'. Can't add the line if I don't have the file. Now my wifi work, so I don't have to type anything.
Like you said you did so many thing it is hard to say what made it start working, I fell the same about my setup.

---

### Post by kolwon on 2011-05-03
I generally have lots of problems with my wireless (coompletely broke it in 10.10) I upgraded hoping to fix the problem and had some doubts when I found this thread but I persevered anyway. I installed while connected to the net with all updates checked and the broadcom STA wireless driver was activated by default and wireless was working out of the box. (I too have the bcm 4311 on an older hp pavillion dv2000 (dv2415nr to be specific))

---

### Post by Bucic on 2011-05-03
It did NOT work for Broadcom BCM4318, HP Compaq nx6125.

[http://ubuntuforums.org/showthread.php?p=10758273](http://ubuntuforums.org/showthread.php?p=10758273)

---

### Post by toasterboy1 on 2011-05-04
> **irv said:**
> [COLOR="Red"]Praise the LORD!!! I got it to work.[/COLOR]

I fixed my problem with the Broadcom BCM4311 driver in 11.04.
Here is what I did. 
1. I uninstalled “bcm-kernel-source” package,
```
sudo apt-get remove bcm-kernel-source
```
2. I installed “firmware-b43-installer” package
```
sudo apt-get install firmware-b43-installer
```
3. I installed “b43-fwcutter” packager
```
sudo apt-get install b43-fwcutter
```
4. I typed into the terminal:
```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```



> **Traktion said:**
> 
So, I added 'b43' to /etc/modules, rebooted again and it worked again. It looks like the STA driver doesn't work for the b4311 any longer (or at least not on my Dell Inspiron 6400), but the b43 module, with b43-fwcutter, does. However, for some reason the b43 module wasn't being loaded by default on my machine, but adding it to /etc/modules fixed that.

Thank you guys. These steps got mine working. Compaq Presario V6133cl. Broadcom BCM4311.

---

### Post by afspear on 2011-05-08
> **irv said:**
> [COLOR="Red"]Praise the LORD!!! I got it to work.[/COLOR]

I fixed my problem with the Broadcom BCM4311 driver in 11.04.
Here is what I did. 
1. I uninstalled “bcm-kernel-source” package,
```
sudo apt-get remove bcm-kernel-source
```
2. I installed “firmware-b43-installer” package
```
sudo apt-get install firmware-b43-installer
```
3. I installed “b43-fwcutter” packager
```
sudo apt-get install b43-fwcutter
```
4. I typed into the terminal:
```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

This was the out put:


Now I am going to reboot and hopefully it will keep working.

Edit: After rebooting everything still works.

Zing!  worked for me too!  thanks

---

### Post by DareBear666 on 2011-05-15
Hello all,

I am very happy that I found this solution. I have had problems with my BCM4311 on all versions of Ubuntu except for 10.10.  When I upgraded to 11.04 I thought my problems were gone, as I did not have any with 10.10, but alas, no wireless connection (after installing additional drivers, of course). The solution I found is in the following link:

[http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working](http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working)

Props to that guy for finding the solution. Basically, you remove the STA BCM drivers in "Additional Drivers" and search B43 in the Software Manager and PRESTO! For me it was a matter of seconds.

Good luck to all!

---

### Post by HarryG321 on 2011-05-16
Thanks a lot :D

This solution worked perfectly for me.

Dell Inspiron 1501
B4311 Chipset
11.04

---

### Post by Gorban on 2011-05-19
I made it work with Broadcom 4318. 
The firmware-b43-installer and b43-fwcutter packages are installed. All other bcm packages are removed, including broadcom-sta-common and bcm-kernel-source (i searched "bcm" in Synaptic). 
I don't have any /etc/modprobe.d/blacklist-bcm43.conf file.
The command
  
sudo modprobe --ignore-install b43

made the wireless work. But after reboot, the wireless was again not working.  
Then i discovered the /etc/modprobe.d/broadcom-sta-common.conf file. I removed it, then the wireless worked after reboot.

---

### Post by nm_geo on 2011-05-19
We worked on these problems back before Natty was released or still in development.. click on this>  _**[Thread]("http://ubuntuforums.org/showthread.php?t=1700897")**_ messages 5 & 6 are some I contributed.

---

### Post by snaga on 2011-05-25
I've been thru all the various threads trying to get my 1525 to get a wireless connection on Natty. My problem is that while I can see my router, I cannot seem to connect to it. I am using the b43 driver. The wireless light comes on, and I can see the available routers, but cannot connect.

---

### Post by irv on 2011-05-25
> **snaga said:**
> I've been thru all the various threads trying to get my 1525 to get a wireless connection on Natty. My problem is that while I can see my router, I cannot seem to connect to it. I am using the b43 driver. The wireless light comes on, and I can see the available routers, but cannot connect.

Make sure you don't have the STA driver activated under Additional Drivers. If it is un-activated it and reboot. Then follow the instruction above and try rebooting again. Hope this works, I know I had to play around with this for awhile to get it to work.

---

### Post by bak&#305;r on 2011-06-12
I have the same problem. I tried many suggestions, none but the command 
sudo modprobe --ignore-install b43  works, but it should be repeated every time I reboot. Anyone has a solution?

---

### Post by PDG1 on 2011-07-03
> **irv said:**
> [COLOR="Red"]Praise the LORD!!! I got it to work.[/COLOR]

I fixed my problem with the Broadcom BCM4311 driver in 11.04.
Here is what I did. 
1. I uninstalled “bcm-kernel-source” package,
```
sudo apt-get remove bcm-kernel-source
```
2. I installed “firmware-b43-installer” package
```
sudo apt-get install firmware-b43-installer
```
3. I installed “b43-fwcutter” packager
```
sudo apt-get install b43-fwcutter
```
4. I typed into the terminal:
```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

This was the out put:


Now I am going to reboot and hopefully it will keep working.

Edit: After rebooting everything still works.

this worked perfectly for me.
no problems thus far :D

I'm a bit of a newb, and i have no idea what the difference is between the b43 driver and the sta driver but i do know that when i 'lspci | grep Network' it shows me with the b43 and internet is working.

Great job :D

---

### Post by irv on 2011-07-04
> **PDG1 said:**
> this worked perfectly for me.
no problems thus far :D

I'm a bit of a newb, and i have no idea what the difference is between the b43 driver and the sta driver but i do know that when i 'lspci | grep Network' it shows me with the b43 and internet is working.

Great job :D
Glad it worked for you. It worked for me also because we have the same wifi card. The STA driver worked in 10.10 but not in 11.04. I don't know why, but all I know it the b43 works with 11.04.

---

### Post by bak&#305;r on 2011-07-04
worked for me too, thanks a lot.

---

### Post by simplemethod on 2011-07-22
Thank you!! I have finally gotten my wireless working thanks to this thread (3 days of trial and error with other tutorials leading to failed attempts).

The only thing I am running into now is that when I reboot I have to type 
sudo modprobe --ignore-install b43 
to get my wireless turned on again. It is not turning on automatically when I start up the computer for some reason...Does anyone have a solution to this?

It is not the worst thing in the world because at least the wireless works but I would love to fix this if I can...

---

### Post by DonSlice on 2011-07-30
This worked for me on Linux Mint 11! Thank you!!

> **irv said:**
> [COLOR="Red"]Praise the LORD!!! I got it to work.[/COLOR]

I fixed my problem with the Broadcom BCM4311 driver in 11.04.
Here is what I did. 
1. I uninstalled “bcm-kernel-source” package,
```
sudo apt-get remove bcm-kernel-source
```
2. I installed “firmware-b43-installer” package
```
sudo apt-get install firmware-b43-installer
```
3. I installed “b43-fwcutter” packager
```
sudo apt-get install b43-fwcutter
```
4. I typed into the terminal:
```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

This was the out put:


Now I am going to reboot and hopefully it will keep working.

Edit: After rebooting everything still works.

---

### Post by irv on 2011-10-19
> **irv said:**
> [COLOR="Red"]Praise the LORD!!! I got it to work.[/COLOR]

I fixed my problem with the Broadcom BCM4311 driver in 11.04.
Here is what I did. 
1. I uninstalled &#8220;bcm-kernel-source&#8221; package,
```
sudo apt-get remove bcmwl-kernel-source
```
2. I installed &#8220;firmware-b43-installer&#8221; package
```
sudo apt-get install firmware-b43-installer
```
3. I installed &#8220;b43-fwcutter&#8221; packager
```
sudo apt-get install b43-fwcutter
```
4. I typed into the terminal:
```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

This was the out put:


Now I am going to reboot and hopefully it will keep working.

Edit: After rebooting everything still works.

This fix works in 11.10 also.

---

### Post by irv on 2011-12-15
I believe this last post, #48 will fill most broadcom cards. Also I am testing 12.04 Alpha 1 and this fix works on this release also. I am using kernel 3.2.0-4.10 and the problem with the broadcom card are still not address as of yet. I really have my doubts that this will be fixed in the final release.
The new 3.3 kernel will not be released with 12.04. This is because of the release date. I am hoping that when 3.3 is out it will fix this problem. Until they fix this problem this is the only work-around I found to work.

Hopefully this thread will help other out here.
I am marking this thread solved.

---

### Post by irv on 2012-07-16
I know this is a old thread, but I just wanted to up date it by saying that this fix works on 12.04 also. I had a mistake in the Title, it should have been an Inspiron 1521 not 1525, but if the 1525 uses a 4311 Broadcom card this should work also.
One more thing, make sure you have dkms installed before following the steps to get the wireless working.

---

### Post by herteljt on 2013-06-03
Following irv's instructions, I was able to get this working for a Gateway MT6840 with Broadcom 4318 using Ubuntu 13.04. Thanks!

---

