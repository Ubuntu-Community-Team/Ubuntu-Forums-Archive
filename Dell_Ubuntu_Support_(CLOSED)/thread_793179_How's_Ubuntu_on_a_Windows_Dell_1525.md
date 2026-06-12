---
title: "How's Ubuntu on a Windows Dell 1525?"
date: 2008-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mjpatey on 2008-05-13
Hi, Group-

I just received a Dell offer via email, and I can get a 1525 laptop with Windows, configured to my specs for $693. With the exact same specs on their 1525 with Ubuntu, it would cost $873.

I'm wondering... can I buy the Windows laptop, wipe it and install Ubuntu, and have all the hardware work flawlessly right away? In their configurator, I selected the exact same hardware for the Windows laptop as was listed for the Ubuntu one, so my guess is that it would be pretty close to perfect. What do you think?

Does anybody have any experience getting Ubuntu running on a Dell 1525 that was originally purchased with Windows on it?

Thanks for any insight you may have!

Also... would wiping Windows and installing Ubuntu void my 1-year Dell warranty?

-Mark

---

### Post by crjackson on 2008-05-13
Buy the cheaper model, install Ubuntu as either a dual boot or in wubi to test fully.  If it does everything you want, wipe windows and run Ubuntu.

You won't know how well everything is supported until you try.  Chances are good that you won't have many issues, but if there are any, that's what Dell is supposed to work out with the pre-install.  Also with the pre-install you get little things like propriotary codec, commercial DVD software, and model specific patches for your hardware (SO I'M TOLD).

---

### Post by mjpatey on 2008-05-13
crjackson, thanks for the info!  I'd rather not buy one and just hope for the best, though... I'd like a clearer picture of what I'm in for.

Tell me if my thinking sounds right:  a "Windows" 1525 laptop should be able to run a standard Ubuntu install pretty well given hardware identical to the "Ubuntu" 1525 model, minus a few device drivers.  I would also assume that if I buy a Windows 1525 laptop and choose to install the special Dell-optimized Ubuntu from their wiki, I should be even better off.  In my mind, it should be identical to one of the Dell 1525 laptops that are sold with Ubuntu pre-installed.

Does that sound right?  Or, even better, can anyone relate personal experience with this?

---

### Post by primski on 2008-05-14
I just bought an Inspiron 1525.

Most of it works flawlessly out of the box. Except wireless, you need ndiswrapper for that. Broadcom doen't not supply linux driver. Dunno when that's gonna change.

Other than that, everything works, bluetooth, graphics, webcam, you name it.

About warranty... no, wipping windows off does not effect warranty.

---

### Post by mjpatey on 2008-05-14
That's great!  Thanks.

primski, did you get these results using a generic Ubuntu install, or Dell's custom installation?

-Mark

---

### Post by primski on 2008-05-14
> **mjpatey said:**
> primski, did you get these results using a generic Ubuntu install, or Dell's custom installation?

-Mark

Generic, Hardy i386, mine came with Vista preloaded.

---

### Post by mjpatey on 2008-05-14
primsky, I may be getting this wrong, but I think anyone can download the specialized Dell version of Ubuntu from the Dell Ubuntu wiki page.  There's one for the Inspiron 1525 specifically, and if I understand correctly, it should include all the things you need to get everything working properly.

Someone correct me if I'm wrong, but I'm hoping this is the case.

-Mark

---

### Post by primski on 2008-05-15
Yes, you're right. I've found it, although Gutsy version and after I already installed Hardy.

I'm not sure thought, what wifi drivers Dell version of ubuntu uses....ndiswrapper?

---

### Post by vadikgo on 2008-05-15
> **primski said:**
> Yes, you're right. I've found it, although Gutsy version and after I already installed Hardy.

I'm not sure thought, what wifi drivers Dell version of ubuntu uses....ndiswrapper?
Dell version of ubuntu support only the Intel Wireless drivers, not ndiswrapper.

[QUOTE=mjpatey]I would also assume that if I buy a Windows 1525 laptop and choose to install the special Dell-optimized Ubuntu from their wiki, I should be even better off. In my mind, it should be identical to one of the Dell 1525 laptops that are sold with Ubuntu pre-installed.

Does that sound right? Or, even better, can anyone relate personal experience with this?[/QUOTE] 
[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525")

---

### Post by dphurst on 2008-05-15
I found that the Ubuntu Dell 1420 was sweet with everything working as I would expect.  The 1420 and the 1520 that were originally Win XP or Vista machines did not work quite as seamlessly due to Broadcom wifi instead of Intel wifi.  The installs were not bad at all though and would be completely adequate since I found the quirks and either fixed them or found workarounds.  Ndiswrapper fixed the problem on the 1520 and just hoping the RF switch never got turned off on the 1420 with the A/G/N wifi was the other!  The wifi switch on the 1420 just didn't seem to work under Ubuntu but the wifi was always on.  I'd recommend the Ubuntu Dell version of the 1420 with all the bells and whistles.  It all works the way you expect with no quirks and is supported from Dell that way.  What a pain to send your laptop back the factory for a hardware fix and get it back with Vista instead of Ubuntu!  That is worth a couple hundred bucks to me as a support person!
Dow

---

### Post by Judge P on 2008-05-17
I bought a Dell 1525 pre-installed with 7.10 Gusty Gibbon from Dell, current Dell UK price £298.99, with intel Pro Wirless 3945 802.11a/b/g mini pc card eur,supplied with Dell drivers, all worked fine. Upgraded to 8.04 Hardy Heron, but then no sound, this link fix problem [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound). Now all works well and not using dell drivers anymore. A good laptop for the price, main weak point: speakers are not very good

---

### Post by satbunny on 2008-06-08
I think you can buy the cheaper version, download the DVD iso from here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)
and then upgrade to 8.04 using Update Manager and check any issues that need fixing here: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

I just did this with a 530n and it worked fine.

---

### Post by Dr. Tingles on 2009-01-09
Satbunny,

One thing that the iso you recommended will not do is handle DVD playback legally or without user intervention.  This is from the link you provided.

> The DVD playback software and media playback codecs are *NOT* included in this public image.

I purchased a 1525 with Vista and installed Ubuntu from the iso you recommended or maybe it's predecessor, I'm not on that computer right now so I can't verify the version.  You need to manually add the Dell php info into your software sources to get the backports for the wireless led etc but for the most part it works.  The media, volume and mute buttons are all assigned and work and all the Fn keys (that I have tried) like Fn+F2 etc work without issue.

[[COLOR="Indigo"]Here[/COLOR]]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry") is the link for the PHP settings if they are still required.

Does anyone have access to an **original** rescue/restore DVD from Dell for the 1525 that they are willing to share?

---

### Post by llamakc on 2009-01-09
> **Dr. Tingles said:**
> Satbunny,

One thing that the iso you recommended will not do is handle DVD playback legally or without user intervention.  This is from the link you provided.



I purchased a 1525 with Vista and installed Ubuntu from the iso you recommended or maybe it's predecessor, I'm not on that computer right now so I can't verify the version.  You need to manually add the Dell php info into your software sources to get the backports for the wireless led etc but for the most part it works.  The media, volume and mute buttons are all assigned and work and all the Fn keys (that I have tried) like Fn+F2 etc work without issue.[B]

[[COLOR=Indigo]Here[/COLOR]]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry") is the link for the PHP settings if they are still required.[/B]  

Does anyone have access to an **original** rescue/restore DVD from Dell for the 1525 that they are willing to share?

Those are not PHP settings, but what is added to the /etc/apt/sources.list file so that the package management system may acquire packages from the source that is added.

---

### Post by Dr. Tingles on 2009-01-09
Beware the noob!

Sorry for the misinformation.#-o

---

### Post by athertek on 2010-03-16
Check out [UbuntuHCL's reviews]("http://http://www.ubuntuhcl.org/browse/product+dell-inspiron-1525?id=629"), it got a 4.3/5 over 8 reviews.

---

### Post by llamabr on 2010-03-17
This thread is more than a year old.  Why would you resurrect it?

---

