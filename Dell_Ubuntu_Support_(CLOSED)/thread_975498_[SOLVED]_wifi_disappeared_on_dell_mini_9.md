---
title: "[SOLVED] wifi disappeared on dell mini 9"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by m.musashi on 2008-11-08
I just got a mini 9 yesterday with customized ubuntu (pretty cool, btw). Wifi was working fine out of the box and my daughter spent an hour or so surfing the web last night. Today when if fired it up there was no networking at all. The network manager icon doesn't load and even wired was off. I was able to turn it back on from system-admin-network but there isn't anything listed about wifi.

I did try to uninstall maximus but it returned an error about not being able to write to xorg.conf. I don't know if that would be related or not. I don't see why it should be as maximus has nothing to do with networking.

Any ideas?

Thanks.

---

### Post by sirebral on 2008-11-08
If you don't even have wired that is a problem.

I would ask my daughter to retrace the steps she took.  Maybe something was removed or a new addition is causing conflicts.  Then i would try and find my WiFi driver info.  You might need to reinstall the driver, or something else.

Thankfully the Mini comes with a Flash card port so you can copy any new files to that and run the installs from that also.

I can hardly wait to get my Mini.  I am waiting for a few more months because I am still paying interest free on my Hybrid and I don't want to over extend my self.

---

### Post by m.musashi on 2008-11-09
I doubt she made any changes and Ubuntu is robust enough to not just break with use. I do have wired networking back. I had to re-enable it manually. Odd that it all just died. It could certainly be a driver issue but there doesn't seem to be a good reason for the driver to disappear. Running ifconfig only shows lo and eth0 so it seems wifi has just vanished. Is there an easy way to reinstall the driver for this model?

---

### Post by superm1 on 2008-11-09
Try using the function keys combinations that toggle wifi and BT.  They might actually remove the device from the bus rather than just low power mode.

---

### Post by frankleeee on 2008-11-09
I installed intrepid on my laptop and restarted multiple times and had the Network manager available, but over night it disappeared so I installed wicd works much better. 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
I have seen multiple threads on missing network manager applets.

---

### Post by sirebral on 2008-11-09
I was going to point you to wicd also.  As of this post: [http://ubuntuforums.org/showthread.php?t=975612](http://ubuntuforums.org/showthread.php?t=975612)

---

### Post by m.musashi on 2008-11-09
Thanks for the tip on wicd. I may check that out but I would like to figure out what is up with the default install. This is a test unit for a possible lab so knowing the issues and solutions would be good.

> **superm1 said:**
> Try using the function keys combinations that toggle wifi and BT.  They might actually remove the device from the bus rather than just low power mode.

I did try that. It opens up a password window saying an app wants to run. However, after entering my password nothing happens. Wifi doesn't act any different and no app "appears" to run.

---

### Post by ArKay on 2008-11-09
> **superm1 said:**
> Try using the function keys combinations that toggle wifi and BT.  They might actually remove the device from the bus rather than just low power mode.Sadly if you use the Fn/2 combination to turn off wireless it comes back with a reboot automatically (on mine). And (at least on mine) the combination keystroke still requires the password to activate.

Is it grayed out or simply not showing on the menus ?

I'm thinking you either need to restore it and see if you get the wireless back or restore it. Or (of course) see how useful Dell tech support is... :(

---

### Post by m.musashi on 2008-11-09
> **ArKay said:**
> Sadly if you use the Fn/2 combination to turn off wireless it comes back with a reboot automatically (on mine). And (at least on mine) the combination keystroke still requires the password to activate.
I get the password request too but nothing happens and a reboot doesn't change anything.

> Is it grayed out or simply not showing on the menus ?

I'm not sure what you are referring to here.

> I'm thinking you either need to restore it and see if you get the wireless back or restore it. Or (of course) see how useful Dell tech support is... :(

Are you referring to restoring the driver? I did try Dell tech support and got passed around through about 8 different people before someone realized that the department everyone was trying to transfer me to was closed. Their stupid answering system kept forwarding me to the wrong department and then they would send me back. I will try them again tomorrow if I don't find a solution.

---

### Post by m.musashi on 2008-11-10
A couple updates and a hope that someone recognizes this problem.

I called Dell today and was told to just reinstall Ubuntu. Given that I don't have an external DVD for this and that it's pretty pointless to reinstall to fix a minor issue (this isn't windows) I decided to blow them off and do a bit more exploring.

The general concensus seems to be that the wifi is just turned off. The fn-2 key has no effect. It asks for permission to run /usr/bin/aircraft-manager-util 'RADIO' but after entering a password nothing appears to happen.

I decided to run it in a terminal and see what happens.
```
sudo /usr/bin/aircraft-manager-util 'RADIO'
```
simply returns "Too few arguments. Stopping."

If I run a different app
```
sudo /usr/bin/aircraft-manager
```
a nice little gui app for turning on and off wifi and bluetooth pops up and it reports their state in the terminal. After doing this it did indeed report that wifi was off. I turned it on via the gui and then ran it again to confirm that it was on. However, there was still no change to wifi, the output of ifconfig or iwconfig (no wireless extensions). Clearly something is wrong and given how the fn+2 key works I'd say there may also be a bug (unless a missing driver is the issue).

Can anyone add any insight into why wifi continues to not work or show up even it appears to be "on"? Thanks.

Oh, and one more piece to the puzzle - though maybe not related - the computer has also stopped resuming from sleep which it did perfectly the first day.

---

### Post by m.musashi on 2008-11-11
Well, I fixed this by running all updates, rebooting, removing the wl driver from the hardware driver tool and rebooting. I don't, know why but after rebooting again it came back with the wl driver enabled and wifi working. Doesn't make a whole lot of sense to me but it worked. Gotta love the resilancy of Ubuntu.

---

### Post by James L. Dean on 2008-11-16
The problem is definitely caused by the failure of maximus to deinstall.  It happened to me too.  I restored from the DVD that came with the Mini 9, losing a day's work.  Then, I disabled maximus by moving maximus-autostart.desktop from /etc/xdg/autostart to my home directory.

---

### Post by carleton on 2009-03-01
Please help I'm having the same trouble. My new mini was working great for several weeks but I booted up today and the wifi won't show up. I've tried everything suggested here.

Help!

---

### Post by sirebral on 2009-03-01
> **carleton said:**
> Please help I'm having the same trouble. My new mini was working great for several weeks but I booted up today and the wifi won't show up. I've tried everything suggested here.

Help!

Try connecting through a wired connection and installing updates.

---

### Post by carleton on 2009-03-01
I tried, but it doesn't seem to recognize the wired connection either...

---

### Post by davidpwhelan on 2009-03-07
[Dell Mini 9, Ubuntu 8.04 ]
I had the same result as @James L Dean.  If you attempt to remove Maximus, it seems to disable your wireless settings.  When you click on System > Administrator > Networks, there is no evidence of wireless.  

I say attempt because the ume-launcher fails to uninstall and reinstalling Maximus through the Synaptics package manager does not fix the problem.

To fix the broken wifi, I found this post:
[http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html)

which fixed my problem without a full re-install or resorting to the DVD. After adding the repositories (I did it through the Synaptics Package Manager, which spat a certificate warning error after I asked it to refresh package information, but which I ignored), I used a terminal and installed the packages.  I got a mixture of updated and new packages.  When I was finished and rebooted, my wireless was back in place (including all of my security, preferred network settings, etc.).  The new launcher is pretty amazing (I will probably still disable it, but I like it better than the Dell Launcher that I disabled).

---

### Post by tortugamarina on 2009-05-10
Ok: same problem, after some big package update. So far, I've been able to find out the following:
[LIST]
[*]Wicd, or whatever such program is called, might work. Since it needs to uninstall Network Manager, I did not dare to try, since that would totally unplug me from the Internet (wired is bad, but better than totally off the net)
[*]Turning on and off the Broadcom card from system-hardware has no perceivable effect
[*]typing wlist scan from a terminal will tell you that no device is running the wireless connection or something like that. iwconfig will report no wireless extension on lo,eth0 or sms.
[*]Interestingly, though, wlist scan as root does list the neighboring routers. This is likely to mean that the wl card is there, recognizable by the os, and that the problem has something to do with some permission system.
[*]For what it's worth, the first reboot after the nightmarish update, the wifi worked just fine, the Spanish keyword didn't, though. This led me to reboot again, which somehow triggered the wifi-out scenario. Have my keyboard reconfigured, but the exact layout for my Dell 9 just not there.
[*]Difficult to express how insanely angry I am.
[/LIST]
Now, I am quoting in bold what James L. Dean suggested in the middle of this thread. Since it is a very short post, I missed it the first five times I read the forum:

**[COLOR="Red"]The problem is definitely caused by the failure of maximus to deinstall. It happened to me too. I restored from the DVD that came with the Mini 9, losing a day's work. Then, I disabled maximus by moving maximus-autostart.desktop from /etc/xdg/autostart to my home directory.[/COLOR]**

Thanks a lot. Gonna watch some movie.

---

### Post by nelio2k on 2009-05-15
Actually, from this thread:

[http://ubuntuforums.org/showthread.php?t=1070978](http://ubuntuforums.org/showthread.php?t=1070978)

by adding the word "wl" to the end of /etc/modules solved the problem for me.

I'm running Dell Ubuntu 8.04 on my Dell astro a90, or dell mini 9.

---

### Post by Schamess on 2009-12-16
Here's what worked for me.  I followed the instructions here: [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Then I had to _UNPLUG the ethernet cable_ and reboot.

It found my wifi connection right away without any problem.

---

### Post by jwaclawsky on 2009-12-16
I had the same problem with the Dell 8.04 Ubuntu installed on my Mini9. The maximus CRAP never worked correctly (you can see my past forum questions on it back approx 6 months ago). Maximus wouldn't follow configuration settings, did strange things like maximizing all my windows when I close something and when I finally got sick of it, I de-installed it and I lost my WIFI and some other things.

Basically from some hard lessons, I gave up on the Dell or netbook remix to stay away from maximus. It is Crap! I am happy on my mini9 at 9.10 right now using ubuntu-9.10-desktop-i386.iso So far this is the best performance I have had. The only problem I had was an already known and simple fix at 

[http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html](http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html) 

Please beware Maximus it IS unnecessary and total crap!

---

### Post by keelyizzy on 2009-12-29
the same message is coming up on mine but ive just got it so i dont no the password can any 1 jelp plz

---

