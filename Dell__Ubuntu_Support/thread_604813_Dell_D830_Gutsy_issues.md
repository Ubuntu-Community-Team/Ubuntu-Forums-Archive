---
title: "Dell D830 Gutsy issues"
date: 2007-11-06
forum: Dell  Ubuntu Support
---

### Post by Triptol on 2007-11-06
Used to have a fine Feisty installation with Beryl and all. Pretty happy with it. Now 'upgraded' to Gutsy, running into the following problems:

- Wireless fails when doing intensive NFS work (updating a 20.000 music collection with Amarok fails after +/- 20%). A reboot is needed to restore wireless functionality.
- Keyboard and mouseclick sometimes freeze. After a certain periode of time I am unable to use my keyboard and mouse. The mouse will move, but I can't click. Sometime ctrl-alt-backspace works and restarting kdm fixes it, sometimes all I can do is a power off.
- No compiz. Well hey that seems to be normal, since my card is blacklisted. Unblacklisting gives funny borders when using the compiz-kde windows manager. In the past with beryl and aquamarine I didn't have those problems.

Don't know about hibernation, cause I simply don't care yet. For me the first two need to be fixed before I can bother with those things ;-)

All in all, I'm very much regretting this upgrade. I am wondering if anyone out there has better experiences.

Techsheet: Dell D830, with Intel wireless and graphics. Running AMD64 distribution.

---

### Post by christian.convey on 2007-11-06
I've had a reasonably good experience with the D830.  Suspend/resume seem to work, etc.

My main beef is with sound volume.  Adjusting the sound seems to temporarily make it quiet, and then it crescendos back up to some high level.  I.e., the volume control basically doesn't work, regardless of whether it's via the laptop's up/down volume buttons, or via the Gnome Volume Applet's gui.

---

### Post by kuufi on 2007-11-06
> **christian.convey said:**
> I've had a reasonably good experience with the D830.  Suspend/resume seem to work, etc.

My main beef is with sound volume.  Adjusting the sound seems to temporarily make it quiet, and then it crescendos back up to some high level.  I.e., the volume control basically doesn't work, regardless of whether it's via the laptop's up/down volume buttons, or via the Gnome Volume Applet's gui.

My only problems with D830 seems to be suspend/resume, but what Triptol and you have experenced seems to work seamless in my install. I've got x86 distribution, with Ubuntu Studio setup.

Compiz runs great and no problems with mouse/keyb or wireless device either.

Audio didn't work before I did this:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

---

### Post by dara on 2007-11-06
I'm thinking of purchasing one of these laptops since I want WUXGA (so the 1420n is out) and I need XP in order to connect to my work network (VPN).  But I'd like to make a choice which will give me a reasonable probability of success when installing Ubuntu.  If I have to skip 7.10 and use 7.04 until 8.04 comes out, that isn't the end of the world.

A few questions:

Are the D630 and the D830 identical in terms of Ubuntu issues (not counting the fact that you can't get WUXGA on the D630).  There seem to be more posts on this forum on the 630 than the 830 and I'm wondering if all of them apply too.

I don't really like Nvidia, so I was going to get the Intel video card.  Is it useful to get more RAM in this case?  (It shares RAM right?).  I was thinking of getting 2 Gig instead of 1.  Does anyone have WUXGA who uses this card?

I guess I don't have much need for n wireless speeds, is there any other reason to get the more expensive Intel wireless choice?  Are the drivers the same quality?

I'd probably get the T7300 which seems fast enough, but if anybody cares to comment on their processor too, I'd be interested.

Does anybody have bluetooth working? 

Thanks,

Dara

---

### Post by TrAvELAr on 2007-11-07
> **kuufi said:**
> 
Audio didn't work before I did this:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa


Awesome!  Thanks for posting that.  I was just investigating my audio issues.

---

### Post by Triptol on 2007-11-10
Well here me goes answering my own post:

- My wireless issues mainly have been fixed. Still a little unstable, but stable enough to get me working. What I had to do was install the new network manager package. At the moment it still is in gutsy-proposed, but I guess it will be in one of the more normal repositories soon.

- Keyboard and mouse still freeze once in a while. It seems to be related to my network card issues.

- I got compiz working (not all the features, since xv movies are not suported by the driver). I even have compiz-kde working now, since I downloaded the hardy compiz, compiz-addons and compiz-kde packages. They work for me. Don't know if they will become part of gutsy-backports though, but you can get them and install them with dpkg -i [package-name]

Considering the D630 adn D830: I don't know if they are the same. I think I remember they are both built around the same Intel chipset, so you will run into the same wireless and sound issues. That said: the problems are not the same for all pcs even for the same hardware (spooky isn't it). One of my colleges has the same laptop, ordered at the same date with Dell and only has sound problems.

The sound problems have been discussed on the net a lot. There seem to be around five fixes where some will work for one installation and some for the other (for me option B worked, installing a specific version of alsa). My college doesn't have sound, but his wireless works flawlessly. Guess we need to blame Intel for that ;)

---

### Post by Triptol on 2007-11-10
Found it! Here is a good link for everyone with sound problems on Intel chips:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by lswinkel on 2007-11-11
I must say I haven't tried to rebuild the kernel on my Dell D830 laptop but all the other fixes still fail. 

(just to let others know they are not the only one)

---

### Post by tturrisi on 2007-11-11
> **lswinkel said:**
> I must say I haven't tried to rebuild the kernel on my Dell D830 laptop but all the other fixes still fail. 

(just to let others know they are not the only one)
[http://members.cox.net/tonyt/d830/#audio](http://members.cox.net/tonyt/d830/#audio)

---

### Post by Triptol on 2007-11-13
Also for the record. My wireless still fails when I leave my laptop on for a day. I'm slowly starting to think it has something to do with ACPI or other powersave stuff, since it doesn't really happen when I'm working on the laptop. Not even after hours.

---

### Post by Triptol on 2007-11-13
Found where the error starts in syslog:

```
Nov 14 00:50:07 bilbo kernel: [28980.405531] ipw3945: Error sending cmd #07 to daemon: time out after 500ms.
Nov 14 00:50:09 bilbo kernel: [28981.583709] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Nov 14 00:50:09 bilbo kernel: [28981.660791] ipw3945: Error sending cmd #08 to daemon: time out after 500ms.
Nov 14 00:50:10 bilbo kernel: [28981.803664] ipw3945: Error sending ADD_STA: time out after 500ms.
Nov 14 00:50:10 bilbo kernel: [28981.967356] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Nov 14 00:50:14 bilbo kernel: [28985.194118] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Nov 14 00:50:30 bilbo NetworkManager: <info>  eth1: link timed out.
Nov 14 00:50:30 bilbo NetworkManager: <info>  SWITCH: found better connection 'eth1/draadloos internet' than current connection 'eth1/draadloos internet'.  same_ssid=1, have_link=0
Nov 14 00:50:30 bilbo NetworkManager: <info>  Will activate connection 'eth1/draadloos internet'.
Nov 14 00:50:30 bilbo NetworkManager: <info>  Device eth1 activation scheduled...
Nov 14 00:50:30 bilbo NetworkManager: <info>  Deactivating device eth1.
Nov 14 00:50:30 bilbo dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 14908
Nov 14 00:50:30 bilbo dhclient: killed old client process, removed PID file
```

After this, all I can do is restart

---

### Post by Triptol on 2007-11-13
Seems to be a bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887)

---

