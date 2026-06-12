---
title: "Kanotix RIP"
date: 2006-12-09
forum: Debian
---

### Post by RAV TUX on 2006-12-09
just heard this news on an IRC channel anybody have further details?

---

### Post by manmower on 2006-12-10
Not entirely sure whether it will be Ubuntu based, but they are moving to a more stable foundation it seems.

[Thread about slh leaving Kanotix, related to the switch](http://kanotix.com/PNphpBB2-viewtopic-t-22892.html).

[Announcement of Sidux with a link to their site](http://techpatterns.com/forums/about736.html.).

---

### Post by mips on 2006-12-10
Well there is always [sidux]("http://sidux.com/index.html") or pure [Debian Sid]("http://www.debian.org/releases/unstable/") ;)

Some more info:
[http://kanotix.com/Article210.html](http://kanotix.com/Article210.html)
[http://kanotix.com/PNphpBB2-viewtopic-t-22873.html](http://kanotix.com/PNphpBB2-viewtopic-t-22873.html)
[http://distrowatch.com/weekly.php?issue=20061204#news](http://distrowatch.com/weekly.php?issue=20061204#news)
[http://kanotix.com/PNphpBB2-viewtopic-t-22969.html](http://kanotix.com/PNphpBB2-viewtopic-t-22969.html)
[http://kanotix.com/PNphpBB2-viewtopic-t-22892.html](http://kanotix.com/PNphpBB2-viewtopic-t-22892.html)
[http://kanotix.com/PNphpBB2-viewtopic-t-22902.html](http://kanotix.com/PNphpBB2-viewtopic-t-22902.html)

I was just about to download the Kanotix CD for testing when I came across this. I will rather wait for their future release whatever it is based on. Maybe I will try sidux seeing I already have the debian netinstall cd and it would just require a simple distro upgrade to sidux.

---

### Post by RAV TUX on 2006-12-10
> **manmower said:**
> Not entirely sure whether it will be Ubuntu based, but they are moving to a more stable foundation it seems.

[Thread about slh leaving Kanotix, related to the switch]("http://kanotix.com/PNphpBB2-viewtopic-t-22892.html").

[Announcement of Sidux with a link to their site]("http://techpatterns.com/forums/about736.html.").

Thanks manmower I had heard the news in a IRC channel so I questioned the reliability of the news all together. This is why I posted the thread here for further clarification. Thank you for sharing the link, it appears to be true that Kanotix will no longer be active or supported:

> No further active Kanotix support can be offered due to time and complexity restraints [it's too hard to support kanotix in other words, but the script can, and does, support all kanotix users who want to switch to sidux from kanotix. [http://techpatterns.com/forums/about736.html](http://techpatterns.com/forums/about736.html)

thus I have edited the title of the thread to more accurately present the known facts. I will also move it to the Debian forum.

> **mips said:**
> Well there is always [sidux]("http://sidux.com/index.html") or pure [Debian Sid]("http://www.debian.org/releases/unstable/") ;)

Some more info:
[http://kanotix.com/Article210.html](http://kanotix.com/Article210.html)
[http://kanotix.com/PNphpBB2-viewtopic-t-22873.html](http://kanotix.com/PNphpBB2-viewtopic-t-22873.html)
[http://distrowatch.com/weekly.php?issue=20061204#news](http://distrowatch.com/weekly.php?issue=20061204#news)
[http://kanotix.com/PNphpBB2-viewtopic-t-22969.html](http://kanotix.com/PNphpBB2-viewtopic-t-22969.html)
[http://kanotix.com/PNphpBB2-viewtopic-t-22892.html](http://kanotix.com/PNphpBB2-viewtopic-t-22892.html)
[http://kanotix.com/PNphpBB2-viewtopic-t-22902.html](http://kanotix.com/PNphpBB2-viewtopic-t-22902.html)

I was just about to download the Kanotix CD for testing when I came across this. I will rather wait for their future release whatever it is based on. Maybe I will try sidux seeing I already have the debian netinstall cd and it would just require a simple distro upgrade to sidux.

mips thanks for sharing, I found this very interesting:

> **Stefan Lippers-Hollmann (slh) strives for new Challenges**

For almost 3 years Stefan Lippers-Hollmann (slh) has contributed to Kanotix by being responsible for the Kanotix Repository and by making sure that practically all Debian Packages were compliantly packaged. Furthermore he optimized many things, supplied and tested kernels and also packaged FreeNX, that unfortunately was not accepted by Debian. FreeNX is after his resignment no longer in the Kanotix Repository. Since financing Kanotix through donations has proved a failure and I am planning restructuring to a more stable base (be it Ubuntu or Debian will have to show in tests) and I myself regard Debian/Sid as unfortunately not compliant with a more commercial orientation, he has left the project. 
 Naturaly this is not the only reason, others can be viewed in his  [last statement.]("http://kanotix.com/PNphpBB2-viewtopic-t-22892.html") 
In any case I am very much indebted to him - without him Kanotix would not be what it is today. I wish him lots of success with his new project, that will stay focused on Debian/Sid. 
 Jörg Schirottke (Kano)
[http://kanotix.com/Article210.html](http://kanotix.com/Article210.html)

Please review his last statement here:


>  -----BEGIN PGP SIGNED MESSAGE----- 
Hash: SHA1 
 
ITO: * 
 
$ wget -qO- [http://kanotix.de/debian/dists/sid/main/source/Sources](http://kanotix.de/debian/dists/sid/main/source/Sources) \ 
> [http://kanotix.de/debian/dists/sid/contrib/source/Sources](http://kanotix.de/debian/dists/sid/contrib/source/Sources) | \ 
> [http://kanotix.de/debian/dists/sid/non-free/source/Sources](http://kanotix.de/debian/dists/sid/non-free/source/Sources) \ 
> [http://kanotix.de/debian/dists/sid/vdr/source/Sources](http://kanotix.de/debian/dists/sid/vdr/source/Sources) \ 
> grep -B 8 ^Maintainer\:\ Stefan\ Lippers\-Hollmann | \ 
> grep ^Package\: | \ 
> cut -d\: -f2 | \ 
> sort | \ 
> uniq 
 acx-firmware 
 alevt 
 avm 
 busybox-kanotix 
 checkmem-kanotix 
 configure-xawtv-kanotix 
 cupsconfig-kanotix 
 ddcxinfo-kanotix 
 distro-defaults 
 dvb-firmware 
 dwl520e1-firmware 
 etcskel-kanotix 
 fix-fonts 
 freenx 
 gfxboot 
 gfxboot-theme-kanotix 
 gprsconnect-kanotix 
 grub-gfxboot 
 hwsetup-ng 
 infobash 
 initscripts-kanotix-live 
 ipw2100-firmware 
 ipw2100-firmware-1.3 
 ipw2200-firmware 
 ipw2200-firmware-2.2 
 ipw2200-firmware-2.3 
 ipw2200-firmware-2.4 
 ipw2200-firmware-3.0 
 kadslwatch 
 kanet 
 kanotix-dsl 
 kanotix-graphics 
 kanotix-irc 
 kanotix-isdn 
 kanotix-kernelhacking 
 kanotix-keyring 
 kanotix-menu 
 kanotix-ndiswrapper 
 kanotix-screenres 
 kanotix-scripts 
 kanotix-setpassword 
 kanotix-sounds 
 kanotix-su 
 kanotix-terminalserver 
 kanotix-udev-config 
 kanotix-vdr 
 kbdconfig-kanotix 
 kdeservicemenus-kanotix 
 kde-services-kanotix 
 kisdnwatch 
 knet 
 knxinstaller 
 knx-installer 
 mkdosswapfile-kanotix 
 mkpersistenthome-kanotix 
 modemlink-kanotix 
 mouseconfig-kanotix 
 netcardconfig-kanotix 
 networkconfig-kanotix 
 nx 
 nxclient 
 nxsetup-kanotix 
 playvideodisk-kanotix 
 ppp-scripts-kanotix 
 restartx-kanotix 
 rootshell-kanotix 
 sambastart-kanotix 
 saveconfig-kanotix 
 scanpartitions-kanotix 
 smbconf-kanotix 
 smbconf-pfeifle-nonfree 
 sshstart-kanotix 
 startsyslog-kanotix 
 sudoers-kanotix 
 sysv-freeze 
 teclasat 
 ueagle-firmware 
 w-pvrscan 
 xsession-initscript-kanotix 
 xsession-kanotix 
and all other packages I'm involved in. Code snippets written by me without an 
explicitly specified license can be considered to be licensed under the GPL v2 
(2 only, not 2.1, not 3), because of the sheer number of packages I'm not going 
to upload all packages as orphaned, new maintainers are urged to upload with 
adapted  maintainer entries as soon as possible. 
All NX related packages have been pulled from the archive because I will no 
longer be able to maintain them and to keep care of security issues; likewise 
I've pulled my -slh* labelled kernels from tu-bs.de as I can no longer care for 
them either. 
 
[COLOR=Red][B] I hereby I resign from all positions within in the Kanotix project because of 
technical and personal disagreements about the status quo. Therefore I suggest 
changing all passwords I might have had access to (including the webserver, 
different login passwords, postnuke accounts etc.) and locking my account on 
the forum. I've already withdrawn my key from kanotix-archive-keyring. 

Why do I resign after two years of hard work for Kanotix? 
As expected this isn't easy to answer and has evolved over time, but technical 
and personal disagreements make this step inevitable and non revocable for me. 
In particular I object about[/B]  [B]: 
 - almost one year without any form of suitable release: 
   - this is an eternity for an debian sid based distribution, clean upgrading 
     from the latest release to current -sid is no longer possible 
   - no significant technical progress in those >11 months from upper leading 
     personnel, planned milestones slipped, finished code improvements were 
     neither incorporated nor even tested 
 - seriously deteriorating inter project communications and working athmosphere 
 - unequal distribution of workload and/ or responsibilities 
 - a siginificant shift of agenda in ways I can- and will not endorse 
[/B][/COLOR]  
In particular I would like to thank all developers and team members who have 
contributed a lot to the existing success that made this project possible, 
namely (in alphabetical order): 
acritox 
bfree 
bluewater 
BodhiBaum 
cathbard 
cleary 
corpix 
devil 
etorix 
h2 
kelmo 
locsmif 
makke 
mzilikazi 
peter_weber69 
RoEn 
slam 
webera 
wolfi 
x-un-i 
all others who have contributed their experience, time and code over the last 
three years and of course knopper and Fabianx for providing motivation, a proof 
of concept, and the initial code base, mipooh, N_knx, the university of 
Braunschweig and in particular blutengel and Shoragan, slam, BlueByte and 
Hetzner for hosting and further infrastructure. 
 
Although it might have been better to speak up sooner, it is the way it is. 
 
Good luck with the further development of Kanotix. 
Regards 
   Stefan Lippers-Hollmann 
 
Post scriptum: 
I'm not going to post this in publicly accessible parts of the forum, if any of 
the remaining team members likes to publish this, license to do so is hereby 
granted under the provision that this intent is posted verbatim including its 
(verifiable) gpg signature. 
-----BEGIN PGP SIGNATURE----- 
Version: GnuPG v1.4.5 (GNU/Linux) 
 
iD8DBQFFaFVc+xo5mnFAnN8RAjNgAJ9YS0CZ+aZH1ncW2kxd5qpd3DuanQCfTnvk 
F4UPSLPQSKdSDGwIxysJQ3M= 
=q3jR 
-----END PGP SIGNATURE-----[http://kanotix.com/PNphpBB2-viewtopic-t-22892.html](http://kanotix.com/PNphpBB2-viewtopic-t-22892.html)


and Kelmo's response:
> 
There are major consequence to slh' departure: 
 
 * The Kanotix software repository will most likely never be cared for again . At least, it won't be cared for with the amount of precision and attention that slh was capable of. 
  
 * I no longer have a suitable method of contributing the the Kanotix project. 
 
This means that the usefulness of the Kanotix repository will eventually expire, and that people will have to brave Debian Sid on their own, or join another group that aims to track that exciting and rapidly developing "software wave". 
 
Yes, some other project will exist, and it will aim to follow Debian Sid in the same manner Kanotix has done until this day. The details of that project will be discovered in due time, hopefully by those people who are most passionate about it. 
 
For now, I would only like to say a few things: 
 
 * Thanks to Kano, slh, the team of supporters and users for a great time over the last 18 months or so. During this time, I learnt more than I ever hoped to know about Linux, Debian and FOSS community and development. 
 
 * Thanks specifically to slh for sharing with me the precious knowledge of caring for project software and its user base. He has great development instinct and principles that i was priviledged to learn from during my involvement with Kanotix. 
 
 * All the best to Kano in the future. I hope you find some method of fulfilling the desire to conquer gadgets, devices and methods of "making things work" with a healthy level of personal and financial prosperity. 
 
 * Good luck to the people that decide to track Sid, and aim to help users join that wild ride (via live-cd, bug-fixes packages/scripts/advice etc). One day in the (hopefully not so distant) future, I hope to directly contribute to that effort. 
 
Thanks, Kel.[http://kanotix.com/PNphpBB2-viewtopic-t-22892.html](http://kanotix.com/PNphpBB2-viewtopic-t-22892.html)

Here another independent projects falls unfortunately. As they adopt another base...I am reminded of survival of the fittest, but had wished they had atleast finished one stable release. Even the DeadCD has it uses even if it no longer active. Yet, they will be archived in the pages of Linux history. I do wish Kanotix and all those who departed from the project the very best in their future endeavors.

reference the DeadCD iso "Final Ghost" seems to be no longer available for download, fortunately I have a copy of the distro.

---

### Post by mips on 2006-12-10
> **RAV TUX said:**
> 
Here another independent projects falls unfortunately. As they adopt another base...I am reminded of survival of the fittest, but had wished they had atleast finished one stable release. 


I'm currently trying to install sidux...

---

### Post by RAV TUX on 2006-12-10
> **mips said:**
> I'm currently trying to install sidux...

cool let us know how it goes...

---

### Post by mips on 2006-12-11
> **RAV TUX said:**
> cool let us know how it goes...

Not long after posting that my adsl died, just got it back up now so the install will continue.

Progress so far.
Did a Debian Etch net install (base system only)
Did a distribution upgrade to Sid.
Added sidux sources list from their site.
Ran the H2 script for sidux.

Now I have to add X & KDE...

---

### Post by handy on 2006-12-11
I joined the [**_Sidux forum_**]("http://www.sidux.com/index.html") yesterday.  They have an appealing roadmap:

quote >

[I]On 24th of November 2006 sidux was formed by a group of people who strive to do the impossible: making Debian Sid (aka "Unstable") stable. The goal is becoming the best Debian Sid based live distro with special focus on clean and easy hard disk install. Strategic milestones and 3-4 planned releases timetabled will give stability and accountability to corporate and home users with a demand for bleeding edge software running on modern hardware, and a definable path over time.

The declared and agreed points are:

1) sidux detects and enables you to instantly use more different pieces of hardware than any other operating system today (including other Linuxes), without the need to search for drivers from the hardware vendors' web sites or complicated installation routines. Everything comes ready on a fast live-CD, and can be installed to your hard drive in just a couple of minutes. Only non-free stuff may require additional action.

2) sidux gives you direct and 100% compatible access to the world's biggest repository of software packages (more than 17.000 at the moment in Debian Sid), all of them free and open source, many of them in professional quality. No virus, no trojan - and again no complicate searching hundreds of websites for an application and running dubious installers.

3) sidux is free and open source and comes with free & priceless 24/7 support via this forum and chat (the IRC). Our support staff is friendly, helpful and very highly skilled - some of them are developers of this operating system themselves, others are accessible for complicated escalated support issues.

4) sidux is not corporate driven or owned, but community driven. Actually we are a community of volunteers who share a common goal - building the brilliant operating system.

5) sidux is extremely flexible and offers a bulk load of ready made scripts and meta-packages. You may use them to mutate it into a secure server system, a high class music studio, a professional graphics design workstation, a corporate desktop - or whatever you actually need.

6) sidux is always bleeding edge technology, packed into a tested and stable combination which is ready for use. It is moving very fast, and will always bring to you the hippest and most interesting developments first. sidux is also one of the few operating systems where you can get a 64bit system with real 64bit compiled applications - and again providing the 100% compatible access to Debian Sid.

7) sidux is multilingual - people from all over the world meet here and talk in their native, but also secondary languages. We believe in the power of shared and open communication and therefore don't split the community by countries or languages, but concentrate them. Many people here do speak several languages and are using them when helping you.

There is definitely much more to say - but that's it for the beginning. Please understand that we need to prepare the first release carefully. The project is in its very first days after foundation and will need some weeks until everything works perfectly. Stay tuned, we will keep you updated!

The Initial sidux Team:

Stefan Lippers-Hollmann (slh)
Trevor Walkley (bluewater)
Chris Hildebrandt (slam)
Ferdi Thommes (devil)
Ralph Hokanson Jr. (piper)
Roland Engert (RoEn)
Harald Hope (h2)
Joaquim Boura (x-un-i)
Niall Walsh (bfree)
Andreas Hausmann (Bodhi)
etorix[/I]

/quote

I will install Sidux on my 2nd machine, & will be very interested in its future development too...

---

### Post by RAV TUX on 2006-12-11
> **mips said:**
> Not long after posting that my adsl died, just got it back up now so the install will continue.

Progress so far.
Did a Debian Etch net install (base system only)
Did a distribution upgrade to Sid.
Added sidux sources list from their site.
Ran the H2 script for sidux.

Now I have to add X & KDE...

sounds like a pain in the-arsh....that must be why I use Gentoo based Sabayon now where everything truely just works...

---

### Post by RAV TUX on 2006-12-11
> **handy said:**
> I joined the [**_Sidux forum_**]("http://www.sidux.com/index.html") yesterday.  They have an appealing roadmap:

quote >

[I]On 24th of November 2006 sidux was formed by a group of people who strive to do the impossible: making Debian Sid (aka "Unstable") stable. The goal is becoming the best Debian Sid based live distro with special focus on clean and easy hard disk install. Strategic milestones and 3-4 planned releases timetabled will give stability and accountability to corporate and home users with a demand for bleeding edge software running on modern hardware, and a definable path over time.

The declared and agreed points are:

1) sidux detects and enables you to instantly use more different pieces of hardware than any other operating system today (including other Linuxes), without the need to search for drivers from the hardware vendors' web sites or complicated installation routines. Everything comes ready on a fast live-CD, and can be installed to your hard drive in just a couple of minutes. Only non-free stuff may require additional action.

2) sidux gives you direct and 100% compatible access to the world's biggest repository of software packages (more than 17.000 at the moment in Debian Sid), all of them free and open source, many of them in professional quality. No virus, no trojan - and again no complicate searching hundreds of websites for an application and running dubious installers.

3) sidux is free and open source and comes with free & priceless 24/7 support via this forum and chat (the IRC). Our support staff is friendly, helpful and very highly skilled - some of them are developers of this operating system themselves, others are accessible for complicated escalated support issues.

4) sidux is not corporate driven or owned, but community driven. Actually we are a community of volunteers who share a common goal - building the brilliant operating system.

5) sidux is extremely flexible and offers a bulk load of ready made scripts and meta-packages. You may use them to mutate it into a secure server system, a high class music studio, a professional graphics design workstation, a corporate desktop - or whatever you actually need.

6) sidux is always bleeding edge technology, packed into a tested and stable combination which is ready for use. It is moving very fast, and will always bring to you the hippest and most interesting developments first. sidux is also one of the few operating systems where you can get a 64bit system with real 64bit compiled applications - and again providing the 100% compatible access to Debian Sid.

7) sidux is multilingual - people from all over the world meet here and talk in their native, but also secondary languages. We believe in the power of shared and open communication and therefore don't split the community by countries or languages, but concentrate them. Many people here do speak several languages and are using them when helping you.

There is definitely much more to say - but that's it for the beginning. Please understand that we need to prepare the first release carefully. The project is in its very first days after foundation and will need some weeks until everything works perfectly. Stay tuned, we will keep you updated!

The Initial sidux Team:

Stefan Lippers-Hollmann (slh)
Trevor Walkley (bluewater)
Chris Hildebrandt (slam)
Ferdi Thommes (devil)
Ralph Hokanson Jr. (piper)
Roland Engert (RoEn)
Harald Hope (h2)
Joaquim Boura (x-un-i)
Niall Walsh (bfree)
Andreas Hausmann (Bodhi)
etorix[/I]

/quote

I will install Sidux on my 2nd machine, & will be very interested in its future development too...

EDIT...nevermind.

---

### Post by handy on 2006-12-12
There is no release .iso yet.  

That has to make it a pain in the aarsh. :)

---

### Post by mips on 2006-12-12
> **RAV TUX said:**
> sounds like a pain in the-arsh....that must be why I use Gentoo based Sabayon now where everything truely just works...

Yes, it is a bit of a pain in the arse at the moment. Once the official release is available there will be an .iso available.

Consider it kinda beta at this stage.

---

### Post by mips on 2006-12-12
Ok, done.

Nothing special yet as it just looks like debian to me. Downside is there are constant updates seeing it is Sid. lol,  not long after I finished there were 34MB of updates...

Must say it feels very responsive/fast on my laptop compare to kubuntu but that is subjective i suppose.

I would wait for the official release iso and then try out.

---

### Post by handy on 2006-12-13
I have also installed [_**Sidux**_]("http://sidux.com/index.html") on my 2nd machine.

It is very obviously much faster than the ***Edgy*** install that previously existed on that drive!

It took a long time to install, due to my having to install the [_**Debian Etch RC1 .iso first**_]("http://www.debian.org/devel/debian-installer/").  The time problem will dissapear when the Sidux.iso is released.

For those interested [_**this link is valuable.**_]("http://techpatterns.com/forums/about736.html") too!

---

### Post by mips on 2006-12-13
> **handy said:**
> 
It took a long time to install, due to my having to install the [_**Debian Etch RC1 .iso first**_]("http://www.debian.org/devel/debian-installer/").

handy,

I think it would be much simpler to use the etch netinstall cd, it's also a small <150MB.

With the netinstall cd you do a minimal base install and do not connect to the net. Once the base install is completed you modify your sources list for sid and do a distro upgrade. This is faster than upgrading an full blown installation. 

The h2 script does the rest. Afterwards you just install what you want/need/

---

### Post by handy on 2006-12-13
I tried the netinstall first, but it had trouble with my internet connection, & I don't have the know how to sort it out, so I just downloaded the full EtchRC1.iso & did it that way.

I agree, the net install would be much quicker.

---

### Post by RAV TUX on 2006-12-15
> KANOTIX One of the reasons for the explosion in Linux distribution numbers in recent years is the inability of many developers to agree on common goals and work things out if disagreements arise. The latest project that has succumbed to personal conflicts over its directions is KANOTIX, a Debian and KNOPPIX-based live CD which has become one of the best-loved second-tier Linux distributions on the market. Unfortunately, as announced last week, the distribution's co-developer Stefan Lippers-Hollmann has decided to resign from the project and create a new distribution called [COLOR=red]Sidux[/COLOR]. It has also emerged that Jörg Schirottke, the founder of KANOTIX, is considering to switch the distribution's base from Debian's unstable branch to Ubuntu and possibly attempt a more commercial orientation of the distribution - moves that are likely to displease some KANOTIX users. For a more detailed summary of the current crisis in the project please read The KANOTIX distro implodes by Tuxmachines.> 
[http://www.sidux.com/PNphpBB2-viewtopic-t-111.html](http://www.sidux.com/PNphpBB2-viewtopic-t-111.html)

---

### Post by RAV TUX on 2006-12-15
> **The KANOTIX distro implodes**

                                                 Submitted by eco2geek on Thu, 11/30/2006 - 20:22.     [News]("http://www.tuxmachines.org/taxonomy/term/56")     As of today, the [KANOTIX distribution]("http://kanotix.com/") is...not dead, exactly, but most definitely without a firm direction. Its co-developer has left, its Paypal donation link is down, and it's not clear what's going to happen with it in the future.
 KANOTIX is a Debian unstable-based distribution from Germany, distributed on a live CD. Its kernel comes highly customized to provide support for lots of hardware. It comes with a graphical installer and many customized scripts for ease of configuration. It was originally based on Knoppix, but it was always meant to be installed, while Knoppix is more of a live-CD-only distro.
 KANOTIX's user base is mainly German, although there is an active English-speaking user base.
 The [official message]("http://kanotix.com/Article210.html") from KANOTIX's founder, Jörg Schirottke (a.k.a. "Kano"), reads, in part:

Quote:[INDENT]"Since financing Kanotix through donations has proved a failure and I am planning restructuring to a more stable base (be it Ubuntu or Debian will have to show in tests) and I myself regard Debian/Sid as unfortunately not compliant with a more commercial orientation, he (co-developer Stefan Lippers-Hollmann) has left the project."[/INDENT]

The co-founder's [reasons for leaving]("http://kanotix.com/PNphpBB2-viewtopic-t-22892.html"):
Quote:[INDENT]Why do I resign after two years of hard work for Kanotix? As expected this isn't easy to answer and has evolved over time, but technical
and personal disagreements make this step inevitable and non revocable for me.
In particular I object about:
 - almost one year without any form of suitable release:
- this is an eternity for an debian sid based distribution, clean upgrading from the latest release to current -sid is no longer possible
- no significant technical progress in those >11 months from upper leading personnel, planned milestones slipped, finished code improvements were neither incorporated nor even tested
- seriously deteriorating inter project communications and working athmosphere
- unequal distribution of workload and/ or responsibilities
- a siginificant shift of agenda in ways I can- and will not endorse
[/INDENT]

There is one thing about KANOTIX that will sorely be missed. By way of explanation, when you use Debian Sid and upgrade its packages frequently, things often break. Installation scripts are sometimes buggy. Things get moved around (for example, the shift from X.org 6.9 to 7.0 entailed a shift to new X directories). Packages don't work. Beyond its great user community, KANOTIX included people who would watch out for the "dist-upgrade" bugs, find fixes for them, and communicate that information to the user community in a timely manner. (If you wonder why Ubuntu became so popular so fast, probably the main reason is that it tries to actively make things easier for end-users. Debian, upon which Ubuntu is based, has the opposite reputation.)
 A few of my opinions about this situation:

[LIST]
[*] I don't expect professional developers to be great at communication. Especially when it's bad news. However, it would be nice if the KANOTIX team could be more forthcoming with its users about what's going on.
[*] I hope Kano doesn't decide to base future versions of KANOTIX on Ubuntu. My personal opinion of Ubuntu is that it takes away a lot more from Debian than it gives back.
[*] It's been a wonderful experience using KANOTIX these past 2 1/2 years. It's taught me a lot about Debian and Linux. My deep respect and gratitude goes to all those involved in its development. *(And I think Kano's a genius.)*[/LIST] **Note: The opinions expressed here are mine. I alone am responsible for them.**


[http://www.tuxmachines.org/node/11481](http://www.tuxmachines.org/node/11481)

---

### Post by handy on 2006-12-18
There is plenty of info' about Sidux, (where all the Kanotix developers but *Kano* have moved) on the [Sidux site]("http://sidux.com/").

I post again:

quote>

[I]Press Releases On 24th of November 2006 sidux was formed by a group of people who strive to do the impossible: making Debian Sid (aka "Unstable") stable. The goal is becoming the best Debian Sid based live distro with special focus on clean and easy hard disk install. Strategic milestones and 3-4 planned releases timetabled will give stability and accountability to corporate and home users with a demand for bleeding edge software running on modern hardware, and a definable path over time.

The declared and agreed points are:

1) sidux detects and enables you to instantly use more different pieces of hardware than any other operating system today (including other Linuxes), without the need to search for drivers from the hardware vendors' web sites or complicated installation routines. Everything comes ready on a fast live-CD, and can be installed to your hard drive in just a couple of minutes. Only non-free stuff may require additional action.

2) sidux gives you direct and 100% compatible access to the world's biggest repository of software packages (more than 17.000 at the moment in Debian Sid), all of them free and open source, many of them in professional quality. No virus, no trojan - and again no complicate searching hundreds of websites for an application and running dubious installers.

3) sidux is free and open source and comes with free & priceless 24/7 support via this forum and chat (the IRC). Our support staff is friendly, helpful and very highly skilled - some of them are developers of this operating system themselves, others are accessible for complicated escalated support issues.

4) sidux is not corporate driven or owned, but community driven. Actually we are a community of volunteers who share a common goal - building the brilliant operating system.

5) sidux is extremely flexible and offers a bulk load of ready made scripts and meta-packages. You may use them to mutate it into a secure server system, a high class music studio, a professional graphics design workstation, a corporate desktop - or whatever you actually need.

6) sidux is always bleeding edge technology, packed into a tested and stable combination which is ready for use. It is moving very fast, and will always bring to you the hippest and most interesting developments first. sidux is also one of the few operating systems where you can get a 64bit system with real 64bit compiled applications - and again providing the 100% compatible access to Debian Sid.

7) sidux is multilingual - people from all over the world meet here and talk in their native, but also secondary languages. We believe in the power of shared and open communication and therefore don't split the community by countries or languages, but concentrate them. Many people here do speak several languages and are using them when helping you.

There is definitely much more to say - but that's it for the beginning. Please understand that we need to prepare the first release carefully. The project is in its very first days after foundation and will need some weeks until everything works perfectly. Stay tuned, we will keep you updated!

The Initial sidux Team:

Stefan Lippers-Hollmann (slh)
Trevor Walkley (bluewater)
Chris Hildebrandt (slam)
Ferdi Thommes (devil)
Ralph Hokanson Jr. (piper)
Roland Engert (RoEn)
Harald Hope (h2)
Joaquim Boura (x-un-i)
Niall Walsh (bfree)
Andreas Hausmann (Bodhi)
etorix[/I]

/quote

---

### Post by RAV TUX on 2007-01-05
[B] 	Kanotix RIP
[/B]

---

### Post by Rodneyck on 2007-01-05
Ouch!  I was just downloading Parsix which is based off of Kanotix. Guess I will pass on trying that one.

---

### Post by RAV TUX on 2007-01-06
> **Rodneyck said:**
> Ouch!  I was just downloading Parsix which is based off of Kanotix. Guess I will pass on trying that one.unfortunately there is a few distros that made the mistake of basing their distro on Kanotix RIP....

I would stick with distro that are based on stable OS's...

example: Sabayon based on Gentoo/Slackware (and some advanced and tested functions of KNOPPIX).

Ubuntu based on Debian

KNOPPIX based on Debian

Wolvix based on SLAX

etc.

---

### Post by mips on 2007-01-06
> **Rodneyck said:**
> Ouch!  I was just downloading Parsix which is based off of Kanotix. Guess I will pass on trying that one.

Maybe wait for the Sidux iso to be released, most if not all are ex Kanotix devs.

You can install it but it is not as simple as a normal cd install.

---

