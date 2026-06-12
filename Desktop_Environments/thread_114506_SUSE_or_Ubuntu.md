---
title: "SUSE or Ubuntu"
date: 2006-01-08
forum: Desktop Environments
---

### Post by Sp@z on 2006-01-08
I totally fell in love with Ubuntu and KDE desktop. However I am having some major issues with the computer shutting down or rebooting in ubuntu. Since I like the KDE desktop so much, a friend of mine suggested I try SUSE. I have downloaded the live cd and played a bit with SUSE but I wanted to throw out an opinion before actually installing it.........I am still very new to Linux and have grown dependant on certain things in ubuntu that I am not sure are availible in SUSE 10.0.........mostly synaptic and automatix! LOL

Any help on the matter would be great! Thanx!~

Oh and here is the link for the shutdown issues and NOTHING has worked for me.........

[http://www.ubuntuforums.org/showthread.php?t=75314](http://www.ubuntuforums.org/showthread.php?t=75314)

---

### Post by L Campbell on 2006-01-08
[QUOTE=Sp@z]I totally fell in love with Ubuntu and KDE desktop. However I am having some major issues with the computer shutting down or rebooting in ubuntu. Since I like the KDE desktop so much, a friend of mine suggested I try SUSE. I have downloaded the live cd and played a bit with SUSE but I wanted to throw out an opinion before actually installing it.........I am still very new to Linux and have grown dependant on certain things in ubuntu that I am not sure are availible in SUSE 10.0.........mostly synaptic and automatix! LOL

Any help on the matter would be great! Thanx!~

Oh and here is the link for the shutdown issues and NOTHING has worked for me.........

[http://www.ubuntuforums.org/showthread.php?t=75314](http://www.ubuntuforums.org/showthread.php?t=75314)[/QUOTE]

I'm not any kind of Ubuntu whiz but I have read that some people's troubles with Ubuntu 'appear' to stem from the fact that they downloaded their own ISO file, instead of using an 'OEM' disk.

Hope this helps.

---

### Post by kairu0 on 2006-01-08
Synaptic is not installed in Suse. I imagine that it is available, but I find the default package management utility much more clumsy than Synaptic.

I had the same issue and I fixed it by adding "reboot=h" to my Grub configuration line.

AKA, do:

```
sudo gedit /boot/grub/menu.lst
```

And add reboot=h to the end of the first Ubuntu option toward the end of the file.

---

### Post by SuperCzar on 2006-01-08
I dont know a thing about automatix, but i do know that synaptic has a good equivalent in YaST, if that is included in OpenSUSE.

I havent gotten a change to try that distro yet, but when i used to use SuSE 8 Professional it was a well refined and easy to use setup.

-- SuperCzar

---

### Post by Sp@z on 2006-01-08
ty for yor comments. I have tried to add reboot-h to the grub, but to no avail. :( I did dowload this distro if ubuntu but have ordered the cd's they just take forever to get here. LOL I dunno if I am going to SUSE yet, 
I want to research it more..............

---

### Post by lotusleaf on 2006-01-08
Why not try both and use what works for you? I use SUSE on some systems but for the most part I use and enjoy Ubuntu. You can install and configure [apt for SUSE](http://linux01.gwdg.de/apt4rpm/) ([howto](http://www.howtoforge.com/apt_for_rpm)).

---

### Post by kingsidy on 2006-01-08
i have used to use Suse (no pun intended) nd i have to say that ubuntu i prefer ubuntu. Plus installing those rpm's gets tricky with those dependancies. also i find that ubuntu is easier to configure. Suse is nice and everything but ubuntu is much more productive for me. don't take my word for it, give it a try and see how you like it.

---

### Post by Sp@z on 2006-01-09
thank you for the comments, I installed SUSE tonight and it is BEAUTIFUL! But a lil too involved for me. I will be continuing with Ubuntu! Thank you all again!

---

### Post by Thirsteh on 2006-01-09
Never liked SuSE much, it's a bit "Microsofty".

---

### Post by ivrobi on 2006-01-09
Hi!

I have an older PC at home and tried both SUSE (9.2) and Ubuntu (5.04 Hoary and 5.10 Breezy). SUSE is too slow, but has more apps. Ubuntu is not so rich in apps, but surely works faster. A vote for Ubuntu.

Greetings!
Robert

---

### Post by cblanquer on 2006-01-09
Hi,

From another perspective, if you have issues with performance due to your old PC, try to install Xubuntu which is supposed to run faster.
It requires to reparameterise Ubuntu in order to use a different, lighter front-end instead of GNOME or KDE (for Kubuntu). Just search the Forum or the Wiki, you'll find the info (I cannot recall it right now).
(I hope this helps)

---

### Post by Azriphale on 2006-01-09
It has been said that SUSE is more friendly to new users. I can't remember who said it, but it has been said.

I disagree with that, personally. I used to run SUSE and after installing Ubuntu, I am never going back. Ubuntu is faster, I think, and since I've started using a .deb based system, I don't know how rpm works. Debian package management makes handling the dependencies a whole lot easier, and to me it just seems to work a whole lot better.

I did enjoy using SUSE when I had it, (otherwise I wouldn't have stuck with it from 9.1 through to 9.3), but I think Ubuntu is far superior.

[quote=ivrobi]Ubuntu is not so rich in apps[/quote]

Ubuntu probably has far more available than SUSE (or so I have read), but to use it you really need broadband. There are 17000 odd packages (or so I have read) in the Ubuntu repos (once universe, multiverse and all the others have been enabled)

---

### Post by rykel on 2006-01-09
[QUOTE=Sp@z]I totally fell in love with Ubuntu and KDE desktop. However I am having some major issues with the computer shutting down or rebooting in ubuntu. Since I like the KDE desktop so much, a friend of mine suggested I try SUSE. I have downloaded the live cd and played a bit with SUSE but I wanted to throw out an opinion before actually installing it.........I am still very new to Linux and have grown dependant on certain things in ubuntu that I am not sure are availible in SUSE 10.0.........mostly synaptic and automatix! LOL

Any help on the matter would be great! Thanx!~

Oh and here is the link for the shutdown issues and NOTHING has worked for me.........

[http://www.ubuntuforums.org/showthread.php?t=75314](http://www.ubuntuforums.org/showthread.php?t=75314)[/QUOTE]


sp@z, i used to be 100% ubuntu (hoary), but ever since i tried out SUSE 10.0 and ubuntu breezy on my new toshiba m40 laptop [with nvidia go 6600], i have been moving back and forth between the two distros ever since.

my preference these days lean towards SUSE, altho' thru' ubuntu synaptic one can install much, much more programs than the former. and download them much, much faster than the SUSE mirrors.

apart from tat, here are instances where SUSE won over my ubuntu breezy:

[INDENT]1. breezy xsane almost tore my little canon LIDE 20 scanner apart!! it just went like a jammed up machine while scanning halfway through a doc... u know, like a car accelerating while the brakes are on...

2. my centrino wifi worked everytime out of the box after installation with SUSE 10.0, but with ubuntu, i need to install the gtkwifi deb.

3. SUSE splashscreens, GRUB, wallpapers, themes etc. all look waaaay more cool than ubuntu's...

4. SUSE is able to mount NTFS and FAT partitions visually through YAST... iirc, ubuntu could mount only FAT partitions during installation.[/INDENT]

in terms of speed/system responsiveness, ubuntu excels over SUSE. the ubuntu menus are also more logically designed than SUSE's, imho.

now, BOTH ubuntu and SUSE have problems shutting off my laptop and with the official nvidia driver. (if i don't use acpi=off before bootup, i would not get any GUI interface)

well, it's almost 1am here in my country, but i hope u can find use for some of my points above!! cheers.   :cool:

---

### Post by veloct on 2006-01-09
[QUOTE=ivrobi] Ubuntu is not so rich in apps[/QUOTE]

Ubuntu has just as many apps as any other distribution, they are just not enabled as default but you can add the multiverse and universe repositories to your sources.list and you'll have just as many as any other distribution.

---

### Post by viscount on 2006-01-09
I dont know, if all you're after is KDE synaptic and automatix
then I would probably suggest sticking with Ubuntu.

I've bought several copys of Suse over the years, before
and after they got bought by Novell and I can tell you they
are a great platform, just about anything you can install
with Synaptic you can also install with yast. Almost, but undoubtedly
synaptic will have more in the base, and way way more if we
start counting optional repositorys.. this is because
debian is so great, not because Ubuntu is so great.

..but Ubuntu is really great, dont get me wrong.

With yast you'll also be able to do all your system configuration, 
and I mean _all_ your system configuration. This is an area
that Ubuntu/Debian are still a long way off from.

However, having said that, and having used both, I am 
going to stick with Ubuntu. Because it is a lot more up to 
date than Debian proper. 

Hope that helps.

---

### Post by bullfrog on 2006-01-09
try the rest , BUT come back to the BEST.  i did   bullfrog

---

### Post by Sp@z on 2006-01-09
Wow so many pionts to consider! This post has been very informative and thoughtful. I am going load SUSE 10 on my laptop and work with it. I have Kbuntu on my desktop now and am quite pleased! I like the KDE desktop more than gnome, but KDE desktop in SUSE is still prettier to the eye.....But SUSE just has more than I am able to grasp at this point so I will take iot slow on my laptop!

---

### Post by rykel on 2006-01-09
just one more point to add to my post above... the "SUSE wifi works everytime out of the box for my laptop"... applies to SUSE with KDE. SUSE with GNOME seems to require a bit of tweaking too...

as a sidenote, these issues with both Ubuntu and SUSE has now caused me to download MEPIS, and i hope tat its wifi and acpi will be more effective than the former two champions.

anybody knows if the most recent version of MEPIS will do better in wifi detection (ie. work like gtkwifi out of the box)?

---

### Post by Cromie on 2006-01-10
For the past few weeks i have given a try to DesktopBsd small but promising good distro, Fedora 4, and the new release OpenSuse 10.0, I think the biggist thing that most people are really forgetting is Support. For the past few weeks i have left message's on certain hardware issue only to find out that some still today never get answered. So it's really not the distro's name , its the support forums that are the backbone of any free distro out there, so to me the best is Ubuntu you never have to wait to long for any good advise.

---

### Post by ivrobi on 2006-01-11
Hi!

@Azriphale, veloct
OK folks, I forgot to write that it is the install CD/CDs I was talking about. Of course, if you enable the extra repositories, you have probably more apps available, than anywhere else. But there are "mortals" like me, with 56k dial-up internet connection... and we appreciate all those usefull apps on the base CD.
Sorry for the misunderstand, my fault...

Greetings!
Robert

---

