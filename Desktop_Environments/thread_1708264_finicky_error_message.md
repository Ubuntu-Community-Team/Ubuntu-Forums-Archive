---
title: "finicky error message"
date: 2011-03-16
forum: Desktop Environments
---

### Post by HappyLinux on 2011-03-16
OK, I keep getting this error message pop-up on rare occasions when I boot into Ubuntu 10.10. I don't know what it means or what it's for. I tend to hit "Don't delete" and then restart the computer.

It only really crops up once every 30 or so boots of Ubuntu, or if I've done a lot of updates through the update manager.

Oh yes, whenever this message appears, the Rubbish Bin vanishes from the bottom right. Everything tends to be fine after the restart.

Does anyone have any guesses on what's happening?

---

### Post by Krytarik on 2011-03-16
Your observation you made corresponds with the error message you are getting, obviously. ;-)

After that happened the next time check "~/.xsession-errors" for error messages.

To avoid a complete restart/relogin when getting this error, you could simply restart gnome-panel instead:
- press Alt+F2
- enter```

killall gnome-panel
```

---

### Post by HappyLinux on 2011-03-17
> **Krytarik said:**
> Your observation you made corresponds with the error message you are getting, obviously. ;-)

After that happened the next time check "~/.xsession-errors" for error messages.

To avoid a complete restart/relogin when getting this error, you could simply restart gnome-panel instead:
- press Alt+F2
- enter```

killall gnome-panel
```

Where would I find this "~/.xsession-errors" thingy?

---

### Post by Krytarik on 2011-03-17
> **HappyLinux said:**
> Where would I find this "~/.xsession-errors" thingy?
The "~" stands for the home directory of the (current) user. So "~/.xsession-errors" is actually "/home/USERNAME/.xsession-errors".

---

### Post by HappyLinux on 2011-03-17
The recent log you mentioned didn't have much in it, but the .old copy next to hit has plenty in it. Is there anything in this that might be of use, or should I wait for the rare message to pop-up again?

---

### Post by Krytarik on 2011-03-17
There are some more error messages about other applets/apps, right at the bottom of the log. But no mention of the trash applet. And the trash applet issue is the only one which regularily re-occurs, right? Just wait for the issue to re-occur then, like I said. Each of those log files imo covers only one session.

---

### Post by HappyLinux on 2011-03-19
Yes, I noticed all those error messages, but they're mainly for applications/features that I don't actually use.

1) I haven't tried using my Bluetooth device in some time now that I can simply remove the memory card from my phone and plug into my card reader.
2) I've never used a PC alarm other than to pull pranks back in school.
3) I have the screensaver turned off. Since power management features became standard on monitors where they can be powered down to standby, I find screensavers a redundant feature that should be removed from future OS releases (MS, Linux, Mac, etc)
4) The update notifier one is somewhat of an annoyance. Since an update a couple weeks ago, despite the settings, the update manager rarely checks for updates and lets me know. I have to manually check.

---

### Post by Krytarik on 2011-03-19
> **HappyLinux said:**
> 
3) I have the screensaver turned off. Since power management features became standard on monitors where they can be powered down to standby, I find screensavers a redundant feature that should be removed from future OS releases (MS, Linux, Mac, etc)
LOL:D  I somehow concur, some "screensavers" are such resource-hungry that they barely deserve to be named as such! But initially they were made made for a real purpose: To prevent the burning effect of CRTs. And those are also the ones which have most likely no built-in power managment. I use such an "ancient" thing, and I use indeed Ubuntu's power management features. Ok, also with a nice screensaver, "GLMatrix". :)
> **HappyLinux said:**
> 
4) The update notifier one is somewhat of an annoyance. Since an update a couple weeks ago, despite the settings, the update manager rarely checks for updates and lets me know. I have to manually check.
Check if it is enabled in "Startup Applications".

---

### Post by HappyLinux on 2011-03-19
> **Krytarik said:**
> LOL:D  I somehow concur, some "screensavers" are such resource-hungry that they barely deserve to be named as such! But initially they were made made for a real purpose: To prevent the burning effect of CRTs. And those are also the ones which have most likely no built-in power managment. I use such an "ancient" thing, and I use indeed Ubuntu's power management features. Ok, also with a nice screensaver, "GLMatrix". :)

Check if it is enabled in "Startup Applications".

You can't buy CRTs now, so what's the point in screensavers now-a-days?? A few makes of CRTs did come with power management, but they were the ones that were released before the flat panel ones truly came into effect to replace the CRTs. Me, I just set the power management to turn the monitor off/standby after 20 minutes.

I just checked the startup list. Yep, the update program is ticked.

---

### Post by Krytarik on 2011-03-19
> **HappyLinux said:**
> You can't buy CRTs now, so what's the point in screensavers now-a-days??

Because some of those are really long-lasting, mine is some 12 years old, and still fit enough, it's simply not to get to die! ;)
> **HappyLinux said:**
> 
I just checked the startup list. Yep, the update program is ticked.
Your settings in "Software Sources -> Updates" are similar to mine in the attached screenshot?

---

### Post by HappyLinux on 2011-03-20
Here's an image of my settings. They're similar.

---

### Post by Krytarik on 2011-03-20
Forget about the error messages in "~/.xsession-errors.old", there seem to be always errors when a xsession ends, I got also some. I didn't mind that.

Regarding the update notifier, I found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)

I'm quite sure that I also had those issue a while ago, but now it's fine.
You may try to disable its auto-launch feature, meaning that you get a notification in the notification area instead of launching the update manager altogether, if you don't have it already that way:
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/update-notifier/auto_launch"
- untick it

---

### Post by HappyLinux on 2011-03-21
Do I have to re-tick the box after a restart of the system?

---

### Post by Krytarik on 2011-03-21
> **HappyLinux said:**
> Do I have to re-tick the box after a restart of the system?
No, that is a permanent change of its behaviour. Just wait and see if it notifies you about updates during the next days.

---

### Post by HappyLinux on 2011-04-03
OK folks, an error message popped up. You'll find attached to this post the screen capture of the error message which is similar to the one previously, and also a copy of the entire xsession errors file.

---

### Post by Krytarik on 2011-04-03
It seems that from time to time the startup of your panels doesn't work as it should, but since it apparently doesn't happen to often, I don't suspect a major issue here. 

For example, I just started experiencing a periodic issue with the startup of Emerald, but as long as it doesn't happen too often, I'm fine with it.

When such issues occur, you can just restart your panels like I described in post #2.

---

### Post by HappyLinux on 2011-04-04
Fair enough

---

