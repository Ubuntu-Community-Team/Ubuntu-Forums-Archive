---
title: "Dell 1535N wireless trouble using WPA"
date: 2008-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by quat on 2008-09-16
Hello, I am new to Ubuntu, just got a Dell Studio 15N with 8.04 installed.  I'm having fun so far, but I've run into a problem.

The wireless works fine as long as I set my router to "no encryption" or to WEP (64 bit, shared key, I haven't tried others).  No problem, perfect connection.

The wireless adpter is a Broadcom BCM4310.

No love if I use WPA (which I know works since I have another laptop talking to it).

I am using the gnome nm applet.  It sees my router, but when I connect and enter my passphrase I get only the lower of the two green dots, then it runs for awhile and gives up.

Thanks for any help!

---

### Post by superm1 on 2008-09-17
> **quat said:**
> Hello, I am new to Ubuntu, just got a Dell Studio 15N with 8.04 installed.  I'm having fun so far, but I've run into a problem.

The wireless works fine as long as I set my router to "no encryption" or to WEP (64 bit, shared key, I haven't tried others).  No problem, perfect connection.

The wireless adpter is a Broadcom BCM4310.

No love if I use WPA (which I know works since I have another laptop talking to it).

I am using the gnome nm applet.  It sees my router, but when I connect and enter my passphrase I get only the lower of the two green dots, then it runs for awhile and gives up.

Thanks for any help!
Have you done all of your apt updates?  There was an issue with the network driver and this sounds fairly familiar.
By chance is it using TKIP?  If so, can you change the network to AES?

---

### Post by quat on 2008-09-17
Thanks for the reply!

I have updated everything.  I still have the same problem: I enter my passphrase, lower green light on the nm applet icon lights, then a long period of thinking during which the "wireless" LED on the router blinks every second or so, then no connection.

I'm really not sure if my router (Actiontec GT701-WG from Qwest) supports AES.  A choice between TKIP and AES never comes up in the WPA setup process.

---

### Post by superm1 on 2008-09-17
> **quat said:**
> Thanks for the reply!

I have updated everything.  I still have the same problem: I enter my passphrase, lower green light on the nm applet icon lights, then a long period of thinking during which the "wireless" LED on the router blinks every second or so, then no connection.

I'm really not sure if my router (Actiontec GT701-WG from Qwest) supports AES.  A choice between TKIP and AES never comes up in the WPA setup process.
Try going to the router setup web url.  Usually there are extra settings that weren't presented in the first run wizard.

---

### Post by jgorr on 2008-09-17
Maybe I should make this a new thread, but my problem is almost the same...

I also have a dell studio 1535n, but with a Boradcom BCM4312. My network manager shows that I am connected and have 100% signal strength, but I am not actually connected (I cant go to any websites or download any packages, etc.)

Any ideas on what is wrong?

I can create a new thread if necessary, but any help here would be greatly appreciated

---

### Post by quat on 2008-09-17
I've become quite a whiz with my router's web setup, not by choice mind you.  I can happily change encryption schemes in the advanced setup, but nowhere do I see any mention of TKIP or AES.  Is there just no hope if I can't switch to AES?

---

### Post by superm1 on 2008-09-17
> **quat said:**
> I've become quite a whiz with my router's web setup, not by choice mind you.  I can happily change encryption schemes in the advanced setup, but nowhere do I see any mention of TKIP or AES.  Is there just no hope if I can't switch to AES?
Well you can try to activate hardy-proposed.  The newer kernel has a newer version of this driver that is supposed to be functional for both AES and TKIP.  If it doesn't work for you, you can just boot into the older kernel.

---

### Post by quat on 2008-09-18
Thanks for all these posts to my question, superm1.

OK, I installed hardy-proposed kernel:
 uname -a: Linux dell-desktop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

Now I can connect to my wireless using WPA-PSK with TKIP.  This is a huge improvement!

I now seem to have a different problem: I can only connect from the nm applet by choosing "connect to other wireless network..." and typing everything (including my lengthy and hard-to-type passcode) in every time.  And, it seems odd.  Sometimes it thinks I'm connected, but I'm not, othertimes it thinks I'm connected and I actually am.

Any additional assistance would be hugely appreciated!

---

### Post by quat on 2008-09-18
Well, the wireless is up and working perfectly now.

Apparently my troubles with network manager are not unknown:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/206568]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/206568")

I have discovered a workaround.  It seems that if you have ever connected to a network, Network Manager will think that it knows the passcode forever for that network and will refuse to update it.  So, I got around this by renaming my network.  When I reconnected to the newly-named network, I entered the passcode and other settings and now nm remembers eveything just fine.  At least that's my convoluted understanding of the situation.

---

