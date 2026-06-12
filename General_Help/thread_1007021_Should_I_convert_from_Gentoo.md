---
title: "Should I convert from Gentoo?"
date: 2008-12-10
forum: General Help
---

### Post by MiscDebris on 2008-12-10
I've been a Gentoo user for about 4 years now.  Before that, was Mandrake, then Slackware.  I really love Gentoo, Portage is awesome.  I'm just a little less than thrilled at the compiling and all that.  I'm looking to try other distros.  Is Ubuntu the one I should look at?  If not, where should I look?  I am willing to look at a family of related distros, like Debian and Ubuntu are.

Here's my list of needs/wants:

Needs:
[LIST]
[*]Server version, server capable, or related server dist (Like Debian is related to Ubuntu)
[LIST]
[*]		Virtualization (prefer openvz and Virtualbox)
[*]		Document Management/sharing friendly (iFolder, Alfresco or similar crossplatform and usable offline for windows/linux)
[*]		LAMP
[*]		Routing/Firewall/VPN Friendly (knock and openvpn are used now)
[*]		Web Management
[/LIST]
[*]	Laptop Friendly
[*]	All Multimedia Formats
[*]	Ability to roll my own packages and repository
[*]	Good dependancy resolution
[*]	Good community support
[*]	KDE 3.5.x
[*]	Ext3 and LVM friendly
[*]	Dual/Tri-boot friendly with XP, Vista, and OS X
[*]	To-disk backup (I use dirvish now) that can backup windows (preferably bare-metal backup) and be effecient with diskspace
[*]	CLI friendly
[*]	security tools (nessus, etc)
[/LIST]	

Wants:
[LIST]
[*]Rolling upgrades (like Gentoo)
[*]	If not rolling updates, the ability to upgrade without blowing up
[*]		I tried a Kubuntu 8.04 LTS to 8.10 on two laptops and in Virtualbox, boom on all but one laptop
[*]	Reliable way to sync a phone/pda (can purchase another one if needed) to Kontact (prefered) or Evolution (if I must)
[*]	Reliable way to share information between Kontact (prefered) or Evolution (if I must) and Outlook
[*]	Classroom friendly (notetaking and the like)
[/LIST]	
	

Nice to Have:
[LIST]
[*]Tablet PC friendly
[/LIST]

---

### Post by DGortze380 on 2008-12-10
> **MiscDebris said:**
> 
Wants:
[LIST]
[*]Rolling upgrades (like Gentoo)
[*]	If not rolling updates, the ability to upgrade without blowing up
[*]		I tried a Kubuntu 8.04 LTS to 8.10 on two laptops and in Virtualbox, boom on all but one laptop


This will be a big complaint for you I think... Ubuntu 'Upgrades' tend to fail about 50% of the time, usually best to reinstall... but that means a reinstall every 6 months to maintain current security.

---

### Post by ubuntu27 on 2008-12-10
Hello MiscDebris.  The distro that might meet your needs is [Arch Linux]("http://www.archlinux.org/").

Arch Linux is rolling release, 
uses package management called PacMan,


If you wonder around [this forum]("http://ubuntuforums.org/forumdisplay.php?f=147"), you will see that quite a lot of people are fan of Arch Linux. 
There is even [sub forum dedicated to Arch Linux]("http://ubuntuforums.org/forumdisplay.php?f=321"). 

Read those threads.

Further link:

[Arch Linux]("http://www.archlinux.org/")'s homepage

[Wikipedia article]("http://en.wikipedia.org/wiki/Arch_Linux") on Arch Linux

DistroWatch: [Arch Linux]("http://distrowatch.com/table.php?distribution=arch")

---

### Post by em4r1z on 2008-12-10
Running Gentoo makes you at least an intermediate Linux user, thus I'd recommend **Debian testing/unstable** instead of Ubuntu. It's a solid rolling release system, more stable than most distributions and relatively up do date. Since you prefer KDE 3.5+, I'd also try **sidux** (based on Debian unstable) and **MEPIS** (based on Debian testing.)

I'd play with them till the next stable release of Debian is finished (and its testing/unstable repositories get thousands of updates) and then install a definite system.

---

### Post by MiscDebris on 2008-12-10
Ok, I've all Debian, sidux, MEPIS, and Arch on the wire.  Hope they like it in VirtualBox.

Well, I suppose I wouldn't mind installing every 6 months or so.  I already do that with Windows.  What would change if I dropped the rolling distro want?

Defining my desires a tad more.

Server: Very Stable, need not be as up to date on versions, but very good with security updates.  Virtualization Friendly.  Something I could install at a client.

Laptop: Stable.  Relatively current on software, not necessarily in the package manager, but existing packages somewhere, Multimedia Friendly.  I only use the testing (~x86) on a couple of select packages.

Workstation:  Not Unstable per say, but a bit closer to the bleeding edge than the above Laptop  I only use the testing (~x86) on a couple of select packages.

I'm looking for a distro family that can do all of that.

---

### Post by DGortze380 on 2008-12-10
> **MiscDebris said:**
> Ok, I've all Debian, sidux, MEPIS, and Arch on the wire.  Hope they like it in VirtualBox.

Well, I suppose I wouldn't mind installing every 6 months or so.  I already do that with Windows.  What would change if I dropped the rolling distro want?

Defining my desires a tad more.

Server: Very Stable, need not be as up to date on versions, but very good with security updates.  Virtualization Friendly

Laptop: Stable.  Relatively current on software, not necessarily in the package manager, but existing packages somewhere, Multimedia Friendly.  I only use the testing (~x86) on a couple of select packages.

Workstation:  Not Unstable per say, but a bit closer to the bleeding edge than the above Laptop  I only use the testing (~x86) on a couple of select packages.

I'm looking for a distro family that can do all of that.

Then an LTS Ubuntu like 8.04 Desktop/Server is a little closer to what you want. LTS get security updates throughout their life cycles, you don't have to install every 6 months (LTS is 2 years I believe), and they tend to get increasingly more stable the longer they're around.

---

### Post by Slim Odds on 2008-12-10
> **DGortze380 said:**
> Then an LTS Ubuntu like 8.04 Desktop/Server is a little closer to what you want. LTS get security updates throughout their life cycles, you don't have to install every 6 months (LTS is 2 years I believe), and they tend to get increasingly more stable the longer they're around.

3 years on the desktop, 5 years on the server

---

### Post by binbash on 2008-12-10
I have both ubuntu and gentoo(gentoo since 2000-2001) installed, simple answer is NO dont convert :) , you can try archlinux or debian for rolling release.However, you will miss portage A LOT.If you want a stable system, i  suggest installing debian

---

### Post by em4r1z on 2008-12-12
> **DGortze380 said:**
> LTS get security updates throughout their life cycles, you don't have to install every 6 monthsActually you do if you want newer versions of packages.

**MiscDebris**, while I think you'd manage with almost any distribution, I aslo think that Debian is the only distribution capable of filling all your requirements. In fact, its branches correspond (almost by definition) to the systems you named. Give it a try.

---

### Post by Slim Odds on 2008-12-12
> **em4r1z said:**
> Actually you do if you want newer versions of packages.

Not quite true. Just enable the backports repository.

---

### Post by tdrusk on 2008-12-12
Maybe [Sidux]("http://sidux.com/"), [Arch Linux]("http://www.archlinux.org/"), or [PCLinuxOS]("http://www.pclinuxos.com/").

I have heard a lot of Gentoo users come back to Ubuntu for it's simplicity.

---

