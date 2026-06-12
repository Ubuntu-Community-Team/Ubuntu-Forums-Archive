---
title: "amcccle not saving during reboot, can't disable crossfire / use quad monitors"
date: 2010-02-24
forum: Desktop Environments
---

### Post by trinaryouroboros on 2010-02-24
**Hello folk,**

   It's been a little over a year and a half now, I figured I could stop punishing myself on this problem and ask the community for advice.

   The original problem, was getting the "amdcccle" package to make changes permanent on my single Diamond ATI HD 3870 video card, as I have a dual head set up. 

   Every time I make changes using amdcccle, the changes take effect for that session only.  During a reboot, the changes revert, and I have to open amdcccle and do the process all over again.

   I mope about this for a long time, intermittently revisiting the subject, googling my brains out, trying new tactics and approaches, and never getting anywhere with the darn thing.  It would seem like such a simple problem, and I have yet to find decent advice out there on how to resolve it so changes are permanent on a reboot.

**   The current day problem:**

   I have since upgraded my distribution, to Karmic Koala, and have installed a second identical Diamond ATI Radeon HD 3870 card, setting it up with CrossFireX connector and all...now when I go into amdcccle, it shows the two monitors in ATI Catalyst Control Center, and underneath it, there's an "Unknown Adapter" - great, does this thing even work? I don't know! Using lspci shows the device is identical to the other card, and sitting on the 4th bus...so what gives?

   My only conclusion, or hopeful conclusion, is that the same issues that are occurring with amdcccle for the former problem, is causing some mischief with the latter problem...

**   All I would like to do is the following, in short:**

   Disable Crossfire via ATI Catalyst Control Center, so I can hook up Quad monitors (provided I know this 2nd card even works...)

   Save changes in amdcccle (or whatever) so that they're locked and set during a reboot...

**Any, and all contributions here are extremely valued, you have my rapt attention and uber thanks!**

:D

P.S.: I spoke with Diamond, after waiting a miserable week or two for support, they explained (and for all I know they could be wrong) that I should Leave the Crossfire hardware Connector connected...but just disable Crossfire via the ATI Catalyst Control Center.  Granted, I'm sure this is fantastic for Windows, but with that "Unknown Adapter" I get the impression this ATI CCC is just Not understanding that I have a second card here...maybe I would get such options in the ATI software, if it worked? Do you feel, in your experience, that I should remove the crossfire connector so I can get quad monitors?

---

### Post by trinaryouroboros on 2010-03-02
):p

---

### Post by trinaryouroboros on 2010-03-03
Thanks for all the help as usual, I've since installed Catalyst 10.1 from ATI's web site, and followed the guide here in regards to setting things in motion using that .run package instead of the 9.7 package:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

So now amdcccle appropriately loads as Administrative User when I need to make changes, plus it merrily saves the changes finally - so I can reboot and not worry anymore.

Also 'sudo amdcccle' from terminal works as well, FYI

The problem with Quad Monitors, however, persists.  I need to disable CrossFireX using the ATI driver.  If amdcccle is no good...I'm hoping some smart soul out there can inform me of another way to accomplish this.

In amdcccle, the second video card still shows "Unknown Adapter" - so I still need help, should a brave soul feel like rescuing someone.

---

### Post by trinaryouroboros on 2010-03-03
Thanks to this older guide, I think I'm making progress finally:

[http://forumubuntusoftware.info/viewtopic.php?f=7&t=2336](http://forumubuntusoftware.info/viewtopic.php?f=7&t=2336)

I followed their procedures to create the crossfire chain, then enabled it subsequently. Now I can confirm the CrossFire system is enabled for that chain:

aticonfig --lsch

CrossFire chain for adapter 0, status: enabled
  0. 01:00.0 ATI Radeon HD 3870
  1. 04:00.0 ATI Radeon HD 3870

Upon using amdcccle, however, I prematurely tried enabling "Single Desktop" for the "Unknown Adapter" listed, and in doing so, Catalyst actually showed a #3 monitor to the right of #2, so I thought perhaps I was in business - that is until I rebooted.

During boot, Ubuntu jammed/crashed entirely and locked up at the desktop loading screen (during login music), so I had to boot off an Ubuntu CD, and revert to my older xorg.conf file

After repeating the process to get crossfire enabled, I believe my next step, if what Diamond tech support says is true, is to use aticonfig to disable Crossfire (albeit leaving the chain active), reboot, and try amdcccle again.

Caveat to using my current configuration with catalyst 10.1, my Compiz Fusion is fubar.  

Instead of worrying about setting back up amdcccle during a reboot, now I have to click on System > Preferences > Appearance, turn back on Extra for desktop effects - of which, for whatever reason, if I click "Keep these settings" it reverts back to Metacity / stops Compiz from being active, unless I actually open ccsm while the timer is running, turn on some compiz feature, Then I can actually click "Keep these settings" and it stays put...until a reboot of course. So amdcccle is fine during reboot, but now Compiz Fusion is busted. 

I already have fusion-icon loading with force compiz in my startup applications, from before anyway, yet this does nothing to help during boot up.

Any case, I'll update this for history sake when I get around to trying the third monitor with crossfire disabled...

---

### Post by iwtws on 2010-03-16
I also had a problem with amcccle not saving. 

[http://ubuntuforums.org/showthread.php?t=1430198](http://ubuntuforums.org/showthread.php?t=1430198)

---

### Post by trinaryouroboros on 2010-03-30
> **iwtws said:**
> I also had a problem with amcccle not saving. 

[http://ubuntuforums.org/showthread.php?t=1430198](http://ubuntuforums.org/showthread.php?t=1430198)

Thank you, I've been looking for something like this.

---

