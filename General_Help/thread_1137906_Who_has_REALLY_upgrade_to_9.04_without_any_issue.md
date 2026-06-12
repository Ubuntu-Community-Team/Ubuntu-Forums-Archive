---
title: "Who has REALLY upgrade to 9.04 without any issue?"
date: 2009-04-26
forum: General Help
---

### Post by UranUtan on 2009-04-26
Hi,

EDIT #2 (2009-04-27): after 2 days of stabilization. It seems like most of the issues are graphics driver related. Machine 1 (5 yeas old, using ATI Radeon 9200) Machine 2 (1- year old, NVidia GeForce 9300). After installing Ubuntu-X [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/) all the GUI hang up issues were solved. Avant Windows Navigator still has some applets removed and Samba not working. Sound like the 9.04 was rushed, I guess 9.04.1 will follow soon.

I have read many positive reviews on upgrade to 9.04 alpha, beta, RC. I was confident I would have no issue with the official release. Especially after a successful test on a 8.10 x32 VM. Then I started the upgrade on two computers (8.10 x32 and x64). They have totally different hardware and both have SAME post upgrade (from Alternate CD) issues:

- Compiz gone, Visual Effects defaulted to None
- Gnome Do, Avant Windows Manager, Wine removed
- Online update warned "Partial Upgrade" it never succeeded.

After searching I have found that a manual upgrade by ```
sudo apt-get dist-upgrade
``` complete the upgrade. After that I could update video driver, change the PPA comand to Jaunty for the 3rd party sofwares above and could get them working.

However, the SAMBA server I have set up on these two machines no longer work. **smbclient -L 127.0.0.1 -U%** shows the shares but if I substitute by its static IP **smbclient -L 192.168.1.12 -U%** I got 
[COLOR="Red"]Connection to 192.168.1.12 failed (Error NT_STATUS_CONNECTION_REFUSED)[/COLOR].

May be I could find a solution for this samba issue but this upgrade is rather frustrating. Before I could enjoy any of the new features, I want to get my machines in working order as it was before.

If anyone could upgrade to 9.04 right at the first try, I would suggest you go out to buy a lottery ticket, your lucks are great.

EDIT: gnome-colors icons are replaced by standard icons. Minor issue.

---

### Post by ninjapirate89 on 2009-04-26
I upgraded with no problems at all, however shortly after I did a clean install just to take advantage of ext4.

---

### Post by lisati on 2009-04-26
So far I've had two or three relatively minor annoyances (mentioned elsewhere in the forums), but on the whole, the experience has been good.

---

### Post by gta117 on 2009-04-26
[B]nope I could not.

When I first tied, it said I could not get it because I was not connected to the internet, which was bs.

This was yesterday. Then it took me 10hours do dl it.

Then when I tried typing in make, I got this terrible error with glib, completely preventing me from installing anything.

if you want to know more of that, please see the thread of [/B]**"**[B][B]Ubuntu is terrible for installing... I need help :("

[/B]Anyways, I also have had some lag issues min and max windows. least it now plays .ogg sound files without that hiss sound. 


-gta117
[/B]

---

### Post by mb_webguy on 2009-04-26
I upgraded my old laptop (32-bit) and did a clean install on my newer laptop (64-bit), the latter mostly because I'd previously had to use quite a few workarounds to get some of the (at the time) newer hardware to work correctly, and wanted to make sure none of my changes broke the system on an upgrade.

The upgrade actually went much better than the clean install.  I didn't have to do *anything* on the older, upgraded computer.  On the newer computer with the clean install, it took me a while to get the new Broadcom wireless driver to activate properly.  (Of course, actually having a native driver is much nicer than using ndiswrapper, so I didn't mind much.)

This is actually the first time I've done an upgrade rather than a clean install, and was rather impressed how smoothly it went.

---

### Post by dcstar on 2009-04-26
> **mb_webguy said:**
> 
.........
This is actually the first time I've done an upgrade rather than a clean install, and was rather impressed how smoothly it went.

I never "upgrade", I have a separate /home partition so I always do a fresh install of the O/S and then switch over to my /home when I am satisfied that the new system functions correctly. I save the package Markings in the old system (in Synaptic) and then reload them in the new one to make sure all my packages are installed again.

This seems to avoid any of the "upgrade" issues that people seem to have and has delivered me stable systems (that can be re-installed at any time) for years.

---

### Post by ulfj on 2009-04-26
Not one problem here,well ok just a small one but not Ubuntu;s fault,it was my unstable internet connection,took my laptop to work to install and a couple of hours later up and running flawlessly!:)

---

### Post by telmac on 2009-04-26
CANNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNOT burn disc!!!!!!!!!!!!!!!!!

---

### Post by UranUtan on 2009-04-26
> **dcstar said:**
> I never "upgrade", I have a separate /home partition so I always do a fresh install of the O/S and then switch over to my /home when I am satisfied that the new system functions correctly.

I save the package Markings in the old system (in Synaptic) and then reload them in the new one to make sure all my packages are installed agai

Hi David,

Me too, I also have /home in a separate partition. I would like to experiment your method. Can you describe more on  "save the package Markings and reload them" ?

Also, would the new fresh installed root automatically recognize all the settings and config which already existed in the /home directory?

Thanks in advance

---

