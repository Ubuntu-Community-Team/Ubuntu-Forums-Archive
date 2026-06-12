---
title: "Dell Mini-9 battery charging problem."
date: 2009-03-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CaptPete on 2009-03-12
Umbuntu Ver-8.04+. I have a new mini-9 that was working fine.  After an airplane trip, found that the battery would not charge.  Much time with Dell support to find that "Airplane Mode" under system\Preferences "Must" be disabled or the battery will not charge. The indications of this bug had me concerned that it was a hardware-not software problem.

Did not find the solution in Dell support through forums, email or chat.  Had to talk to India which surprisingly did have good support and a workable solution.  They even called back later to confirm that the battery was charging.

---

### Post by ugm6hr on 2009-03-12
Not sure if this is a request for help or not.

In any case, this is a software feature of Airplane Mode.

I thought it fixed the maximum battery capacity at 40% rather than stopping charging completely, but it is definitely supposed to reduce charging.

---

### Post by bhadams1 on 2009-04-30
Hello,

I just got my 9 (that's what I call my Dell Mini 9--haha) in March.  This is my first week out of the local area and happens to be on business/pleasure trip to Vegas.

I didn't want to (possibly) be charged for Internet usage at the hotel, so I put my 9 on Airplane Mode, and all week I it didn't charge (nor did I put 1-2-1 together).  I thought I burn-out the battery or something.  I couldn't understand why.

So finally, at the airport's "Free" WiFi, I had disabled the Airplane Mode and log onto Ubuntu Forums, and as I found this post and possible answer to my question, I realised that my battery is finally recharging.  Yeah!

So, I don't think 8.04+ fix this probably, or it is just recharging to maintain a charge.  Because all week, I stood at a constant 45% charge.

I'm planning on upgrading to Jaunty.  Does anybody know if this little problem has been fixed?  Also, how would you go about fixing this issue on your own, or can you?

---

### Post by anjilslaire on 2009-05-01
Airplane Mode prohibits charging by design. There is no "fix", per se. Devices like computers charging batteries can cause interruptions with flight control devices on planes, hence the Airplane Mode disabling the ability to recharge.

When you are not on the plane, disable airplane mode and your battery will charge properly again, as you've noticed.

If you're not wanting to accidentally be connecting to hotel wifi, simply disable the wireless on the mini from the network manager applet in the system tray.

---

### Post by bhadams1 on 2009-05-01
Thank you very much Anjilslaire.  I didn't know that about WiFi and flight control.  That definitely explains the "issue", which isn't an issue now.  Thank you again for the why and how.

---

### Post by akc42 on 2009-05-06
It is the same problem on the mini 12

I am on a business trip and had my battery go down on the flight here.  Yesterday I plugged it into a power socket and left it all day, only to get to the bar last night with no power and a battery that had not charged any.

It wasn't until day when after extensive google searching I finally found the answer.  I now have my battery charged for the flight home :)

It would be REALLY USEFUL if there was some indication on the Airplane Mode dialog box if it informed you that it also restricts battery charging.

---

### Post by celem on 2009-06-08
I have the same problem. However, my mini9 is loaded with xubuntu 9.04 (removed ubuntu 8.04). I cannot figure out how to access the airplane mode feature to check it. Xubuntu must place that feature elsewhere but I cannot find it. Any ideas?.

---

### Post by ugm6hr on 2009-06-08
9.04 does not have Airplane Mode; you have to enable it manually.

Look on the ubuntumini website for how.

---

### Post by celem on 2009-06-08
I recall having seen airplane mode while configuring my xubuntu setup, and I may have even set it, but now I cannot find where or how to set/reset it. My battery stopped charging and I would like to verify that airplane mode isn,t set. Is there a command line access for airplane mode?

---

### Post by ugm6hr on 2009-06-08
Try this: [http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html)

---

### Post by anjilslaire on 2009-06-08
As noted, Airplane Mode is a separate .deb that must be installed. It is *not* included in a vanilla (U/X/K)ubuntu installation, as it only appliies to the Dell hardware.
Find it here, install it, and enable/disable as desired:
[http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html)

EDIT: Not fast enough ;)

---

### Post by celem on 2009-06-08
Did that. Took a while to find the executable which, in xubuntu, didn't create a GUI link. It was in /usr/bin/aircraft-manager. No help for my battery problem as it shows airplane mode as disabled. My battery stopped taking a charge and the seemed to be the most common problem. Now I don't know what to do other than ship the mimi9 to Dell.

---

### Post by anjilslaire on 2009-06-08
Double check the connection. Remove the battery and plug it back ito the Mini, then plug the AC in again. I've seen some laptop batteries have connection issues like that once or twice.

---

### Post by celem on 2009-06-08
I believe that I solved the problem as the battery is now charging (32% as I type this). Earlier, I disabled BLUETOOTH in the BIOS, since my mimi9 doesn't have bluetooth hardware. THIS IS WHAT STOPPED THE BATTERY FROM CHARGING! Re-enabling bluetooth, even though it doesn't exist reactivated battery charging. My experience should serve as a warning and help to others.

Personally, I consider this to be a very obtuse design.

Thanks for your help.

---

### Post by anjilslaire on 2009-06-08
Strange. I have Bluetooth disable in bios as well (although I do have bluetooth, but don't use it), and my battery charges fine...

In any event, glad you're fixed.

---

### Post by tyroeternal on 2009-06-11
Even though it shows Airplane mode as disabled it was actually enabled as far as your system was concerned.  If you would have enabled it and disabled it again, it would have started working properly.

---

### Post by celem on 2009-06-11
I had to install it as it isn't included in 9.04 xububtu. I activated it and deactivated it without success. Airplane mode had no effect. Only re-enabling the non-existent bluetooth in BIOS resolved the problem. Charging now works correctly.

---

### Post by ronewolf on 2009-08-07
> **tyroeternal said:**
> Even though it shows Airplane mode as disabled it was actually enabled as far as your system was concerned.  If you would have enabled it and disabled it again, it would have started working properly.

Well, I'll be! Indeed, disabling Airplane Mode (after getting off plane) so that I could use networking wasn't enough to get the battery going. I followed your advice and enabled Airplane Mode and now the battery is happily charging. 

So thank you for the helpful suggestion.

And, if it is actually true that battery charging needs to be disabled during plane flights along with networking then I'll suggest that there are at least two bugs here. One is documentation - this no or low charge only "side effect" of Airplane Mode should be made obvious. Its not documented anywhere now as far as I can tell. The 2nd bug, duh, is that it shouldn't be necessary to toggle Airplane Mode twice for the power management to get it.

This URL [https://bugs.launchpad.net/dell-mini/+bug/302924](https://bugs.launchpad.net/dell-mini/+bug/302924) asks for people to comment if they are having this problem. I didn't only because I am not sure what launchpad is and how they are connected with the dev community etc.

---

### Post by mika6617 on 2009-08-09
Hi, I too have this same problem, however the aformentioned remedy doe not help me. whether I enable or disable airplane mode my battery still does not charge. any assistance would be excellent.

---

### Post by celem on 2009-08-09
mika6617, did you read my cure above? Worked for me.

---

### Post by anjilslaire on 2009-12-20
OK,
Ironically, I now experience the battery failing to charge behavior. I'm running Karmic UNR, installed the latest Aircraft-manager 12.1 deb from the PPA
[https://launchpad.net/~opensource-subakutty/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~opensource-subakutty/+archive/ppa?field.series_filter=karmic)

Flipped it on, flipped it off, now the battery refuses to charge, and has drained to 0%, so I'm stuck on AC power now. I've tried the following:
[http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/420-battery-not-charging-2.html#post12070](http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/420-battery-not-charging-2.html#post12070)
[http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/1955-fix-no-battery-charging-ubuntu.html#post15644](http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/1955-fix-no-battery-charging-ubuntu.html#post15644)
Also, repeatedly disabling Airplane mode, even booting into a live Jaunty environment, installing aircraft-manager into Jaunty & disabling it, suspecting it having been a compatibility issue with Karmic.

My warranty has just expired, so sending off for a new battery is not a trivial matter. Also, this just happened after adding aircraft-manager to Karmic, so I'm pretty sure its not a bad battery.

Thoughts? Thanks!

---

### Post by celem on 2009-12-20
Read back in this post "aircraft-manager" created charging problems for me. I suspect that if you follow the advice in this thread you'll be charging again.

---

### Post by anjilslaire on 2009-12-20
Yes, 1st thing I did was enable Bluetooth in th BIOS. No luck. Still not charging :(

---

