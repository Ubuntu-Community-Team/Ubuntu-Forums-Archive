---
title: "ATI Radeon HD 4770 On Linux???"
date: 2009-05-12
forum: General Help
---

### Post by kenpuu on 2009-05-12
Hi, I need help. 

I've bought this card. It's new, and I don't know how to install it... I have installed Jaunty. I have seen that I have to install the Catalyst driver, but in amd's web I don't see support for this card. Can anyone help me? 

Thanks.

---

### Post by LoloftheRings on 2009-05-12
I'm not familiar with Ati, but you might want to have a look at the restricted drivers dialog.
System->Administration->Hardware drivers

---

### Post by Legace on 2009-05-12
The FGLRX driver [version 9.4] (closed-source ATi driver) does not support 4770 now.

Version 9.5 of FGLRX/ATi Catalyst is expected to be released tommorrow (May 13). Then you can install it..

Here is a guide on how to install: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)
NOTE THAT THAT GUIDE AS OF NOW SHOWS HOW TO INSTALL ATI CATALYST 9.4. Fetch the 9.5 package instead.. :)

---

### Post by kenpuu on 2009-05-12
Thanks. I've reinstalled ubuntu. And I have activated the restricted drivers. Now it seems it works, but I have at bottom-right an icon with an unsopported hardware message. Instead of it, like I say, it works fine.

---

### Post by PorcelainMouse on 2009-05-16
I'm glad it worked for you, but it did not work for me.  I upgraded from 8.10 and you did a fresh install of 9.04, right?  That's one difference, but I still think it's something else.  What about your 4770 card manufacturer?  Mine is a Gigabyte card.  Who made yours?

---

### Post by kenpuu on 2009-05-18
Hello. Mine is manufactured by Powercolor. Anyway, there was some errors, because Catalyst 9.5 wasn't out. But it is now. I have done this and it seems like eveything works fine.

```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run
```

Give execute permission.

```
sudo ./ati-driver-installer-9-5-x86.x86_64.run
```

I hope it's useful to you.(sorry for my english ](*,))

---

### Post by PorcelainMouse on 2009-05-25
kenpuu, your English is great.  Thanks for your help.  I can't be sure, but I think the problem was this missing line in the "Device" section of xorg.conf:

  Option    "UseFSDev" "true"

Before, in 8.10 Intrepid Ibex, I was using an older (nVidia) card and I don't think that option was in my xorg.conf file.  I upgraded and replaced the card at the same time (not wise).  After the upgrade, it worked (without acceleration, of course) and I just assumed XWindows did the right thing and fell back on vesa.  But, I tried to install the proprietary driver manually (since the "Hardware Drivers" application didn't show any available for my new card--it does now, since 9.5 has been packaged).  That resulted in a blank screen and a locked-up keyboard!  The system was still alive, but I couldn't even switch to a virtual console.  The power button caused a safe shutdown, fortunately.

In any case, even the safemode xorg.conf wouldn't work.  I booted to "recovery mode" (from the GRUB menu, basically linux single).  I discovered a nice little menu when the system finished booting.  In that menu, I found an option that tries to fix X.  This added "UseFSDev" "true" to the safemode version of xorg.conf.  After that, X started okay.

All of this may have been handled by the upgrade if I had installed the new card properly, first.  Or, vice versa.  Either way would have been a better choice.  Then again, maybe the safe mode xorg.conf file is bad.  Shouldn't it include that option now?  In Jaunty, I think all drivers are using the kernel frame buffer now, right?  That would have saved me some headaches, too.

---

### Post by pandasonic on 2009-05-29
I'm having problems with the ATI Radeon HD 4770 (Vendor: Sapphire) and Jaunty.  

Problems:
1.  Suspend and Hibernate will only work with CompizFusion disabled.
2.  PC crashes whenever I try to log out, regardless of Compiz.

I tried following the steps listed here: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Hang_at_logout]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Hang_at_logout"), but that did not work.

Any ideas?

---

### Post by kenpuu on 2009-05-31
> **PorcelainMouse said:**
> kenpuu, your English is great.  Thanks for your help.  I can't be sure, but I think the problem was this missing line in the "Device" section of xorg.conf:

  Option    "UseFSDev" "true"

Before, in 8.10 Intrepid Ibex, I was using an older (nVidia) card and I don't think that option was in my xorg.conf file.  I upgraded and replaced the card at the same time (not wise).  After the upgrade, it worked (without acceleration, of course) and I just assumed XWindows did the right thing and fell back on vesa.  But, I tried to install the proprietary driver manually (since the "Hardware Drivers" application didn't show any available for my new card--it does now, since 9.5 has been packaged).  That resulted in a blank screen and a locked-up keyboard!  The system was still alive, but I couldn't even switch to a virtual console.  The power button caused a safe shutdown, fortunately.

In any case, even the safemode xorg.conf wouldn't work.  I booted to "recovery mode" (from the GRUB menu, basically linux single).  I discovered a nice little menu when the system finished booting.  In that menu, I found an option that tries to fix X.  This added "UseFSDev" "true" to the safemode version of xorg.conf.  After that, X started okay.

All of this may have been handled by the upgrade if I had installed the new card properly, first.  Or, vice versa.  Either way would have been a better choice.  Then again, maybe the safe mode xorg.conf file is bad.  Shouldn't it include that option now?  In Jaunty, I think all drivers are using the kernel frame buffer now, right?  That would have saved me some headaches, too.

Then, is everything working fine now? It's impossible to me fix the lags and the rest of problems.

> I'm having problems with the ATI Radeon HD 4770 (Vendor: Sapphire) and Jaunty. 

Problems:
1. Suspend and Hibernate will only work with CompizFusion disabled.
2. PC crashes whenever I try to log out, regardless of Compiz.

I tried following the steps listed here: [http://wiki.cchtml.com/index.php/Ubu...Hang_at_logout](http://wiki.cchtml.com/index.php/Ubu...Hang_at_logout), but that did not work.

Any ideas?

It seems ATI drivers don't support xorg-server 1.6, which is included in Jaunty. I've read Canonical says it's ATI's responsibility.
I wrote an email to AMD, asking them if they will make the changes to the drivers. I have to say they answered very soon. But, after two messages, this is what they told me:

> Dear Customer,

Your service request : SR #{ticketno:[8200206032]} has been reviewed and updated.

Response and Service Request History:

There is no information on the drivers available before a driver is released, no one in Customer Care can confirm what will be supported or fixed in a driver that has not been released.

 

In order to update this service request, please respond, leaving the service request reference intact.

Best regards,

AMD Global Customer Care

I wish we'll have good luck...

---

### Post by pandasonic on 2009-06-03
> **kenpuu said:**
> Then, is everything working fine now? It's impossible to me fix the lags and the rest of problems.



It seems ATI drivers don't support xorg-server 1.6, which is included in Jaunty. I've read Canonical says it's ATI's responsibility.
I wrote an email to AMD, asking them if they will make the changes to the drivers. I have to say they answered very soon. But, after two messages, this is what they told me:



I wish we'll have good luck...

Thanks for that!  I hope they release an update soon.

---

### Post by randyklein99 on 2009-06-08
> **kenpuu said:**
> 
It seems ATI drivers don't support xorg-server 1.6, which is included in Jaunty. 

So is it a hard thing to downgrade xorg-server while in Jaunty?  Or will Catalyst 9.6 support that?

---

### Post by PorcelainMouse on 2009-06-10
kenpuu, yes, it is fixed now.  I'm using the Catalyst 9.5 drivers, but via manual install (download from AMD's ATi web-site); I haven't switched to the 9.5 drivers in Ubunbtu's repositories, which showed up just a couple of days afterward.  I've been playing Quake4 and it's pretty fast.

Others: I don't think there is any call for downgrading X.  It's true, there was a problem.  Sounds like the Ubunutu folks whipped passed ATi by switching to the new Xorg server and, thereby, dropped compatibility with older drivers, which happened to include all but the bleeding edge of the Catalyst driver series.  But, I think it's all fixed, now.

---

### Post by kenpuu on 2009-06-10
> **PorcelainMouse said:**
> kenpuu, yes, it is fixed now.  I'm using the Catalyst 9.5 drivers, but via manual install (download from AMD's ATi web-site); I haven't switched to the 9.5 drivers in Ubunbtu's repositories, which showed up just a couple of days afterward.  I've been playing Quake4 and it's pretty fast.

Others: I don't think there is any call for downgrading X.  It's true, there was a problem.  Sounds like the Ubunutu folks whipped passed ATi by switching to the new Xorg server and, thereby, dropped compatibility with older drivers, which happened to include all but the bleeding edge of the Catalyst driver series.  But, I think it's all fixed, now.

Is it fixed? How? I only have to reinstall the drivers from ATI website?(sorry, I haven't understand well your post)

---

### Post by pandasonic on 2009-06-10
PorcelainMouse,

Are you able to log out of your system?  Are you having problems with suspend/hibernate and/or restarting and shutting down?

I installed the Catalyst 9.5 drivers directly from ATI's website and I'm still having the problems I described above.

---

### Post by KanineN on 2009-06-15
Sorry for the bump, but is the 4770 working for you now? I may consider to buy one so I want to make sure that it will work with ubuntu.

---

### Post by fdmille on 2009-06-17
The 9.6 driver is now available and seems to fix the shutdown and other problems.  Follow the Jaunty [installation guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide").

---

### Post by randyklein99 on 2009-06-19
It's working much better with 9.6 than with 9.5.  I have no problems logging out or switching users.  There's some other issues, but they all seem bearable.

Edit: Suspend only seems to work with Compiz disabled.

---

### Post by PorcelainMouse on 2009-06-25
kenpuu, sorry my post wasn't clear.  When I wrote, "It's fixed," I meant that the new Catalyst Drivers (Linux driver version 8.216) are available via the official APT repository.  When I installed this card, I couldn't get the drivers from the repository.  Now you can.  So, you no longer have to download them from AMD/ATi.  But, I'm sure everybody has figured this out for themselves at this point.

---

### Post by PorcelainMouse on 2009-06-25
All,

After I got the proprietary drivers installed and fixed the xorg.conf file, it worked very well.  I'm anxious to try 9.6, I'm still using the 9.5 version I manually installed, earlier.

Regarding Compiz, I don't use it.   Also, I haven't actually logged out of my computer since the upgrade.  So, I'm afraid I'm no help to you.

However, I do have this problem: keyboard freezes/locks up when returning to X from virtual console.  Do you have that problem???

When I use CTRL-ALT-F1 (or -F2, or -F3, etc.), the system switches to a virtual console.  That works fine.  But, when I use F7 to switch back to XWindows, the screen goes blank/black and XWindows never returns.  AND, most disturbingly, the keyboard freezes/hangs; it is completely locked up / frozen / hung.  I have to hardware reset the whole system, even thought it appears to be running.  When I hit Caps Lock or Scroll Lock, the keyboard LEDs DO NOT light.  I even tried it with a PS/2 keyboard, but that exhibits the same behavior.  Sounds like a bug in the new Xorg, to me, but I didn't find any bug reports about it.

I wonder if this is related to the logout problem or the hibernation problem.  I'll try to logout soon and report back.  Let me know if you have the same problem with virtual consoles.

---

### Post by PorcelainMouse on 2009-06-28
Yes, my system also locks up/freezes/hangs when logging out.  I guess this is all moot, though, since it has been confirmed by others that 9.6 resolves this issue.  But, the release notes don't mention this symptom in the resolve issues section, so it's hard to be confident.

I hope these issues are related.  I will try 9.6 later.  Hopefully, it will be released to Ubuntu repositories, soon.

---

