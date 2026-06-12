---
title: "Running Steam through Wine"
date: 2007-05-08
forum: Gaming &amp; Leisure
---

### Post by DieseL1988 on 2007-05-08
Well I managed to install steam under wine, got through the setup etc. it gets as far as logging in, appears to complete the login stage and then...

[IMG]http://www.marktyrrell.com/other/SteamError.png[/IMG]

Any ideas? I have heard that steam runs under wine, but then I've also heard it doesn't anymore...

---

### Post by dfreer on 2007-05-08
steam runs fine for me. Generally, if there is a problem with steam I:

(1) backup my .gcf files so that I don't have to download 5 GBs of data each time 
(you probably only want to do that after you make sure they work, so get steam working first then back them up)
(2) uninstall wine completely and delete the ~/,wine folder 
(again, you'll want to backup any other programs you have installed with wine. don't restore them until you make sure steam is working)
(3) install wine and run winecfg to create the ~/.wine folder (use a proper wine .deb from winehq, not some script) make sure to autodetect your drives and configure your audio (I find OSS needs to be the only driver running with steam)
(4) grab the tahoma.ttf fonts and put it in your ~/.wine/drive_c/windows/fonts, make sure it is readable by all (maybe executable too, can't remember)
(5) either reboot or check your running processes to make sure any wine or steam processes are killed. reboot is eaiser.
(6) install steaminstall.exe (steam recently came out with steaminstall.msi, which I'm pretty sure can be installed with wine but you'll have to read up on that. For now, either find an older version of steaminstall.exe or you can use the link at the bottom of my post)
(7) tada!
(8) beyond that, you'll have to post more info. I'm probably not much help, but most people completely forget to wipe .wine to clear it of it's settings.

[http://www.steampowered.com/download/SteamInstall.exe](http://www.steampowered.com/download/SteamInstall.exe)

---

### Post by DieseL1988 on 2007-05-08
Well, its a fresh install of wine, installed through apt-get though if that would make a difference?

Slightly Offtopic:

I've been running mIRC quite nicely on wine, anyone know if Paint Shop Pro 9 would run in wine as well?

---

### Post by dfreer on 2007-05-08
best place to check if app works is winehq.

The apt-get version *should* be fine, although I generally download a .deb straight from winehq that way i get the newest version. You can add wine as a repository as well and it will get you the newest version through apt-get.

It may have been an error during the installation, which is why I recommended a fresh install. Generally, after you install you will want to log off steam, shutdown wine, and then log back in. Beyond that I'm not much help.

---

### Post by DieseL1988 on 2007-05-09
Hmmm, well I'll give these things a try later. Just wanted to ask, what's VMware like for running things like steam?

---

### Post by buttons on 2007-05-09
> **DieseL1988 said:**
> Hmmm, well I'll give these things a try later. Just wanted to ask, what's VMware like for running things like steam?

VMware doesn't support 3D acceleration.  *Steam* should run perfectly fine, but none of the games would.

---

### Post by dfreer on 2007-05-09
same with quemu/virtualbox, although I hear there is a way to run applications from windows using rdesktop, I'm wondering if that would work.

---

### Post by DieseL1988 on 2007-05-09
[IMG]http://www.marktyrrell.com/other/NewError.png[/IMG]

Now this is what I get after a fresh install of Wine... steam installer just wont run...

---

### Post by dfreer on 2007-05-09
*I* just got that error as well, wtf!? I was having problems with steam, and so I decided to do a clean reinstall and *poof* steam no longer works. It makes no sense because there is no tmp file in the windows/temp/ folder. Not only that, but installing with sudo (not a good idea, i know) doesn't work either.

---

### Post by DieseL1988 on 2007-05-09
how random! i mean i got the install to work literally 24 hours ago... and now...

---

### Post by aldenhg on 2007-05-09
I got that same error, so I decided to try Cedega. It works, but nowhere near as well as it does under Windows. I'm just going to have to dual boot for a while longer, I guess.

---

### Post by DieseL1988 on 2007-05-10
Just my luck, the day I want to install steam on Linux it decides to create a random error!

Guess this is down to the WINE guys to fix...

---

### Post by buttons on 2007-05-10
It's a regression in 0.9.36.  Downgrade wine and then Steam will install.

Just open synaptic, find wine, highlight it, and press Ctrl+E (or choose Force Version from the menu), and select one earlier than 0.9.36.

EDIT: Once steam is installed CS will play fine with 0.9.36, feel free to upgrade once again afterwards.

---

### Post by DieseL1988 on 2007-05-10
ok so I got it installed again... and im back to sqaure one, im getting the original error message...

---

