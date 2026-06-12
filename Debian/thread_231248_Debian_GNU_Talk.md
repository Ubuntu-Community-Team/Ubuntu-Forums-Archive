---
title: "Debian GNU Talk"
date: 2005-01-05
forum: Debian
---

### Post by nocturn on 2005-01-05
I've selected Ubuntu for my desktops (home network), but I'm still shopping for a Server OS (Ubuntu is still missing somewhat in that area).

I would like to use Debian stable (when sarge hits the net), and I saw talks that they will introduce a fixed release cycle like Ubuntu (but 12-18 months).

Can anyone confirm if there is already a decision on that?  I dread installing something that is nog going to be updated another 3 years ;-)

---

### Post by crun on 2005-01-05
Debian Sarge has a VERY slow update cicle, but IMO that makes it a perfect server OS. Because the only updates you'll need to download are security fixes, you are left with a tried-and-true thuroughly tested system where bugs and exploits are very rare indeed. Plus, on a server you don;t often have the need for "bleeding edge" version of software - if it works and does what you want it to than that should be enough.

The downside ofcourse is that with Debian Stable, all software is much older than on your regular distro. It is tested thru and thru though, and because of dpkg you can always change your repositories if you want to add a new flavor of a progam.

---

### Post by daniels on 2005-01-05
What do you feel is lacking in Ubuntu?  Apache, PHP, MySQL, PostgreSQL, LVM, et al, are all provided in the supported seed.  And, unlike Debian sarge, this means guaranteed security support.  We see Ubuntu as both a server and a desktop OS, so I'm curious to hear what you believe Ubuntu is lacking in the server department.

(BTW, *.canonical.com and *.ubuntu.com run on Warty.)

---

### Post by nocturn on 2005-01-05
[QUOTE=daniels]What do you feel is lacking in Ubuntu?  Apache, PHP, MySQL, PostgreSQL, LVM, et al, are all provided in the supported seed.  And, unlike Debian sarge, this means guaranteed security support.  We see Ubuntu as both a server and a desktop OS, so I'm curious to hear what you believe Ubuntu is lacking in the server department.

(BTW, *.canonical.com and *.ubuntu.com run on Warty.)[/QUOTE]

You are right.  There are no features missing (that I am aware of) that rules it out for server use (although it is a shame that mit-kerberos is not included in main AFAIK).  

I've read in an FAQ that I can install without X by selecting a custom install (which is good).     

Until today I was still considering Ubuntu or Debian (Sarge when stable) equally.  There are three considerations that made me lean towards sarge:

1° The main issue is the feeling that everything is still new.   Most sysadmins (including myself) tend to be a bit conservative (which is why Sarge is out of the question until it hits stable). 
I'm still a little reluctant to have 2.6 and udev on a server.

2°  From the forums I got the impression that very few people were using Ubuntu as a server.  
The fact that you guys are doint that at canonical is reassuring...

3°  There was a thread on the mailing list today.  Although I do not agree with many of the things the OP said, but in a reply, àne of the Ubuntu developers (Tollef Fog Heen) said:
> 
I think you hit the nail on the head here: conservative. If you're a
server admin, you tend to be (or become) conservative.
...
Heck, I'm not ubuntuizing any of my servers yet, and I'm
one of the developers


Now I am in doubt again.

---

### Post by daniels on 2005-01-05
Yeah, but don't let that indict it. :) I'm perfectly happy with the concept of freedesktop.org running Warty (it is a stable release, after all), and yeah.  Bear in mind that the Firefox maintainer runs Epiphany -- sometimes it's not the best judgement to take (Red Hat's KDE maintainer used the console almost exclusively, also).

---

### Post by HiddenWolf on 2005-01-06
[QUOTE=daniels]Yeah, but don't let that indict it. :) I'm perfectly happy with the concept of freedesktop.org running Warty (it is a stable release, after all), and yeah.  Bear in mind that the Firefox maintainer runs Epiphany -- sometimes it's not the best judgement to take (Red Hat's KDE maintainer used the console almost exclusively, also).[/QUOTE]

People tend to be a bit rusty. Changing ways takes a long time.

On the server OS front, I'm not running one at the moment, but if I will, it'll either be Ubuntu or Debian.
I'd prefer Ubuntu, because I hate the Debian attitude, and I'd like to keep to one distro, if I can.

However, what I miss is a newer version of mysql, and php5.
Mysql has brought out a stable/production version that is newer then the ones in the repro's, and as for php, I'd rather use the newer system, since if I keep coding on 4, it'll be outdated sooner.
Get me a good Apache2/PHP5/mysql4.1 combination, and I'll be happy. :-)

---

### Post by nocturn on 2005-01-07
[QUOTE=HiddenWolf]People tend to be a bit rusty. Changing ways takes a long time.
[/QUOTE]

Well, I didn't used to be ...
But I've done system administration for 4-5 years now, and I learned to be...  specially if you have to stay after hours if something breaks.

Specificly kernel 2.6 is a breaking point, it offers great new features and is certainly the future (running it on my personal worksation since 2.6.4), but it introduced so many changes that there are some problems which I don't like ok a server.
One thing I noticed (on 2 completely seperate machines) is that IO performance before 2.6.7 was much lower then any 2.4 (specially under multiple simultanous loads).  Stability is improving, but not yet on the 2.4 level IMO

I will have to rerun these test on Ubuntu before making my final decision...

---

### Post by Randabis on 2005-01-07
[QUOTE=nocturn]Well, I didn't used to be ...
But I've done system administration for 4-5 years now, and I learned to be...  specially if you have to stay after hours if something breaks.

Specificly kernel 2.6 is a breaking point, it offers great new features and is certainly the future (running it on my personal worksation since 2.6.4), but it introduced so many changes that there are some problems which I don't like ok a server.
One thing I noticed (on 2 completely seperate machines) is that IO performance before 2.6.7 was much lower then any 2.4 (specially under multiple simultanous loads).  Stability is improving, but not yet on the 2.4 level IMO

I will have to rerun these test on Ubuntu before making my final decision...[/QUOTE]
 Can't you run 2.4 kernels in ubuntu?

---

### Post by nocturn on 2005-01-07
[QUOTE=Randabis]Can't you run 2.4 kernels in ubuntu?[/QUOTE]

I don't think they are in the default repositories.
Off course you can always go for custom kernels (from source), but I like the fact that the standard images are security tracked.

Sarge is going to ship with both kernel-trees, but will default to 2.4.  Yet the 2.6 serie is official, so supported.   

If my performance tests go well on Ubuntu, I think Ubuntu will win out (because I fear that Sarge is going to have verrrryyyy llooooonggg release cycles again).  Hell, they're talking about a 12-18 month fixed cycle, yet sarge was due in august (2004).

All my concerns here aside, I think Ubuntu is the best distro I've seen so far (in general).  I'm especially impressed with the quality warty has given that it is a first release.

---

### Post by zeroK on 2005-01-07
[QUOTE=nocturn]I don't think they are in the default repositories.
Off course you can always go for custom kernels (from source), but I like the fact that the standard images are security tracked.

Sarge is going to ship with both kernel-trees, but will default to 2.4.  Yet the 2.6 serie is official, so supported.   

If my performance tests go well on Ubuntu, I think Ubuntu will win out (because I fear that Sarge is going to have verrrryyyy llooooonggg release cycles again).  Hell, they're talking about a 12-18 month fixed cycle, yet sarge was due in august (2004).

All my concerns here aside, I think Ubuntu is the best distro I've seen so far (in general).  I'm especially impressed with the quality warty has given that it is a first release.[/QUOTE]
 Yes, I also first thought about switching my (ok, don't kill me for calling this box a server please ;-) ) server-thing to Debian Sarge but then I thought again that it could take ages again for the next stable release and I'd end up going SID again :-(

---

### Post by Gary Powers on 2005-03-29
Got Hoary installed on two of my boxes and everything is working just fine.  Getting bored though, so I installed Debian on my third box.  Can't figure out how to get the GUI up and running.  Are there forums similar to ours (Ubuntu's) for Debian?

Gary

---

### Post by bored2k on 2005-03-29
[QUOTE=Gary Powers]Got Hoary installed on two of my boxes and everything is working just fine.  Getting bored though, so I installed Debian on my third box.  Can't figure out how to get the GUI up and running.  Are there forums similar to ours (Ubuntu's) for Debian?

Gary[/QUOTE]
 linuxquestions.org
[http://forums.debian.net/](http://forums.debian.net/)

---

### Post by Glanz on 2005-03-29
Yes... [http://www.debianhelp.org/]("http://www.debianhelp.org/") is one. I am a frequent troublemaker there.

Just a few questions: did you install a display manager like GDM for example? What environment or WM are you trying to use?

You can try su > root passwd > startx
to see what happens for openers.

---

### Post by az on 2005-03-29
debianhelp.org

The answer to your question may help ubuntu userse, too, though.  Go ahead.

---

### Post by Gary Powers on 2005-03-29
Thanks for the directions, gents!

Just a few questions: did you install a display manager like GDM for example? What environment or WM are you trying to use?

You can try su > root passwd > startx
to see what happens for openers.[/QUOTE]

I installed GDM and will use Gnome, at least initially.  STARTX gets me a black screen for a few seconds,  restart X, then an error message which comes down to "unable to find screen".

I looked at my XORG.CONF file on this machine and copied the appropriate entries to XF86config, but no joy.

Thanks again to both of you for the quick responses.

Edit:  how do you get those "boxes" around quotes?


Gary

---

### Post by totalshredder on 2005-03-29
Hey, 

 I had the exact same problem as you with debian; nobody could figure it out. But if you can get it working; give me a PM!! I'd love to try debian out :)

Luke

---

### Post by Gary Powers on 2005-03-29
I'll let y'all know what I find out, but after a quick spin through the forums over there, it is almost certainly a driver issue.  I might pick up another video card and see what I can do with that.

Thanks again for the input!

Gary

---

### Post by haquila on 2005-04-15
I know i'm at the wrong place, but i started using ubuntu 4.1 but went for debian because i was used to kde (and window maker).
i did an network install of a laptop sarge(kernel 2.6.8-powerpc)
i installed this because i was using SuSE and Fedora core at work, but there wasn't a free distrid that would work on my new generation ibook{the first white one with a 14inch monitor(old)} but ubuntu and debian.
now i have a lot of bits and peices on my debian but looking in /dev/ there isn't anything that starts with "sd*", so i can take these thing off my machine. 
all i have is "hd*","tty*","vcs*","cdrom","dvd","cdrw"and a bit more.

what i want to do is get my data off my machine.
a cd-rw isn't big enough and i was thinking of a usb-storage or firewire(ieee1394)
but when i put one M-System DiskOnKey in 
i got the below in /var/log/messages 
kernel: ochi_hcd 0001:01:18:0: wakeup
kernel: usb 1-1: new full speed USB device using address 3
kernel: usb-storage: probe of 1-1:1.0 failed with error -1
usb.agent[3147]: usb-storage: already loaded

in /proc/bus/usb/devices one line for the device reads
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
this "Driver=(none)" bothers me.
having nothing starting with "sd*" in /dev i understand that it may be normal that "Driver=(none)" is so.
my question is, how do i install the needed drivers?
i have a feeling that this will add the "/dev/sd*'s"

i know this is the wrong place, and that i don't know much about linux, but,,,,,please.

can someone give me some guiding. reading english, french and japanese is fine:) 

thank you in advance,
sincerely,
akira
ps: usb mouse work fine:)

---

### Post by p!=f on 2005-04-15
Do you run Debian "stock" kernel or your own? Does the kernel have support for that device in?

Btw, KDE based Ubuntu is called Kubuntu which is the official project. You might want to give it a try. ;)

---

### Post by haquila on 2005-04-16
yep:|
the device wasn't supported.
(but i found a device that is supported:))

here's the data of the device, (just want to contribute a little, so could some one fowardit on to whoever wants it)
/proc/bus/usb/devices
T: Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=12 MxCh= 0
D: Ver 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P: Vendor=08ec ProdID=0010 Rev= 2.00
S: Manufacturer=M-Systems
S: Product=DiskOnKey
S: SerialNumber=021A62161701E995
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 94mA 
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
E: Ad=81(I) Atr=02(Bulk) MxPS= 64 Ivl=0ms
E: Ad=01(0) Atr=02(Bulk) MXPS= 64 Ivl=0ms
hope this will mean something for someone.

just remembered that this device didn't work on SuSE neither.
one last question.
why don't these devices(the devices that i can mount) not show up after
# fdisk -l
i remember on SuSE and Fedora Core that this comnand would give me the list of every device connected to my machine, but now i only get what is on hda.
this is how i changed the mounting points in /etc/fstab after a reboot for my scsi devices(external HDDs).
sorry, i know this must be a debian question again in the wrong place,,,,.
Sincerely
akira

---

### Post by MetalMusicAddict on 2006-08-01
Im getting a 64-bit system soon. I wanted to try Debian 64 but was wondering if anyone here has used it? Is it any different than Ubuntu-64?

---

### Post by siimo on 2006-08-01
I was exited about running 64bit linux as well when i got my 64bit system in december for christmas! but after 3-4 weeks of running it i gave up and went back to 32bit.  

why?

64 bit is a waste of time currently - you will not get any noticible speed improvements over 32bit and it will use slightly more memory as well.  whats more theres the need of having 32bit stuff like firefox so you can use plugins like flash.  Same thing with mplayer as win32codes are only 32bit.  I think openoffice still doesnt compile for 64bit.  So you end up with both 32 and 64 bit version libraries of some things as well.


Besides my rambling above, yes i have used debian 64bit and it is a good system but it doesn't have openoffice etc as they don't install 32bit packages by default so you manually have to create a 32bit chroot and apt-get stuff like OOo in that.  This was 2-3 months ago maybe the situation has changed? anyone know?

---

### Post by RAV TUX on 2006-08-01
this thread has been moved to "other" linux talk.

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***Debian Tech Talk***

cleaning up a bit I have merged these threads:

[http://www.ubuntuforums.org/showthread.php?t=10138](http://www.ubuntuforums.org/showthread.php?t=10138)
[http://www.ubuntuforums.org/showthread.php?t=231248](http://www.ubuntuforums.org/showthread.php?t=231248)
[http://www.ubuntuforums.org/showthread.php?t=27243](http://www.ubuntuforums.org/showthread.php?t=27243)

---

### Post by RavenOfOdin on 2006-08-15
How can I do this? 
I recently remade my backup comp for Etch and made the swap partition as large as the amount of RAM.  Unfortunately, I have only 32MB of RAM in said comp.  Now, GNOME takes an awful lot of time to load small things such as the theme manager, or to change themes, or to install from apt-get.

I can do all these things from Fluxbox without difficulty but I'm wondering if I can speed GNOME up in order to use it.  I've already thought of disabling unneeded services and/or boot scripts.  Any time I open more than one application, GNOME goes nuts.  I used to have SELinux enabled but that proved to be a MAJOR CPU hog and gave me a zillion terminal messages.

Any ideas, people?

---

### Post by xXx 0wn3d xXx on 2006-08-15
1. Enable prelink

2. Make sure DMA (if you hardware supports it) is activated.

3. Use hdparm to optimize your hd.

4. Custom compile a new kernel (2.4.xx series) since your hardware is most likely old, and remove all the excess stuff.

5. If you use firefox, use swiftfox for intel/amd processors.

6. Use [ XML Optimization ](http://gnomefiles.org/app.php?soft_id=1397)

7. [ Tweak you ext3/reiserfs filesystem for a performance boost. ](http://ubuntuforums.org/showthread.php?t=107856)

8. [ Clean up unnessary files. ](http://ubuntuforums.org/showthread.php?t=140920)

9. Make boot faster with InitNG 

Note: All of these links are for Ubuntu but they will work on Debian.

Edit:

[http://www.debian-administration.org/articles/199](http://www.debian-administration.org/articles/199) - Simple change in Init scripts
[http://www.debian-administration.org/articles/211](http://www.debian-administration.org/articles/211) - Use bootchart to identify propblems when booting
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388) - Filesystem comparsion on Debian Etch

---

### Post by croak77 on 2006-08-16
32MB Ram might be pushing it. I'd say just go with a window manager.

---

### Post by Iandefor on 2006-08-16
My suggestion? Chuck GNOME. It was intolerably slow with 64 MB for me, I can't imagine it would be *better* on half that. Go with the *real* man's choice- bash!

:-D

---

### Post by RavenOfOdin on 2006-08-16
@Owned: Thanks, I'll check those out soon enough.

@croak: That may be the issue. I wasn't even able to run KDE on Sarge 
without having a monster swap file (256 MB), and even then it 
routinely stayed at 100% usage.  If I can find the exact type of RAM 
that these iMacs take I might buy two 192MB sticks and put those in at 
some point.

@Iandefor: Lol@bash.  I imagine that would be good for a dedicated 
server. ;)

---

### Post by tseliot on 2006-08-16
32MB of RAM ??? I didn't know that GNOME could run on it.

Anyhow try Openbox or Icewm

---

### Post by croak77 on 2006-08-16
13 years and still going strong. Who's partying tonight?

---

### Post by BWF89 on 2006-08-16
And people say "Do we still need Debian" pfft, way to go Debian. They've showed us that you can create a safe, massive, and stable OS that stands the test of time on an entirely volunteer basis.

[IMG]http://giftedsouls.com/gs/images/smilies/party-smiley-041.gif[/IMG]

---

### Post by plb on 2006-08-17
"Linux.com reports that the third beta of Debian Etch installer (released August 11, 2006) has some major new features, which might make this version of Debian the easiest to install. According to the original announcement, we will now be able to install using a graphical user interface on i386 and amd64 platforms. We will also be able to set up encrypted partitions during installation. Debian Etch is scheduled to be released on December 2006"

[http://linux.slashdot.org/linux/06/08/17/137219.shtml](http://linux.slashdot.org/linux/06/08/17/137219.shtml)

---

### Post by RavenOfOdin on 2006-08-18
Only time will tell if its requirements are less or more than the graphical installer on Dapper.

Etch seems like a pretty good system at the moment so I can hope.

---

### Post by Klaidas on 2006-08-18
yay, my story got here :)

---

### Post by zxee on 2006-08-26
Is anyone here actually using etch? I'd like to know how it compares to woody and sarge. Exactly how improved is the installer and admin over those releases? Thanks. BTW I've previously installed 3.01 r1 and used dselect so install is no big deal but I'm wondering how up to date the install is once it's complete.

---

### Post by tturrisi on 2006-08-26
I'm using a recent etch install.  Smooth as silk to install (net install).  What I always do is when at the point of selecting what software to install (desktop, web server, laptop, etc) I space key empty everything and that's that.  Next step is reboot & log in.  I login as root and edit my sources.list, add a pgp key for debian-multimedia.org and then install exactly what I want for my system.

At first I install upgrades, xorg, gnome-desktop-environment & all my desired apps (nmap, wireshark, synaptic etc).  Then I startx & remove the undesirable bloat in such as evolution, epiphany, gonme-desktop-environment, etc.  Then I install any other desired apps fitting for the comp I am using including kernel-headers, 686 kernel & dev packages needed to make & install needed drivers such as madwifi or others.  This gives a leaner faster more efficient gnome exactly how I want it.  It's way better than Ubuntu this way.

Etch packages are more recent than Sarge packages.  FYI, Ubuntu IS USING the etch installer!  Installs are way easier now compared to Woody (unless one was familiar & used to the woody cfdisk & text mode.)

---

### Post by zxee on 2006-08-27
Thank you tturrisi, I appreciate your sharing and experiance with etch.
Unfortunately I can only download isos from wifi spots-my home computer is connected by dial up so doing a net install is not really feasible.
I may get the etch iso though and try it-thanks again.

---

### Post by tturrisi on 2006-08-29
next time on broadband download all the cds or dvd isos...

---

### Post by baldy1324 on 2006-09-01
WOW i heard gnome could run at a minimum of 128 MB-definetly use fluxbox-the greatest window manager of all time.

---

### Post by baldy1324 on 2006-09-01
if ind that ubuntu is too unstable and that is why i use debian

---

### Post by baldy1324 on 2006-09-01
right now 64-bit is not worth it. i havent noticed any speed improvments and lots of plugins and software isnt supported for it. if you did want to go 64, debian traditionally has better non-x86 support.

---

### Post by Rumor on 2006-09-05
On Friday the first I did a network install of Debian Etch - beta 3 on a PC at the office. We're considering migrating our desktops to a Linux distribution in an effort both to prolong their usefulness and save on future costs.

I downloaded the netinst.iso from here: [http://cdimage.debian.org/cdimage/etch_di_beta3/i386/iso-cd/](http://cdimage.debian.org/cdimage/etch_di_beta3/i386/iso-cd/)

During the install routine, I was prompted for a network mirror from which the installer would grab the latest files for a default desktop environment / default system installation. The installer scanned the mirror and then proceeded to download 642 files which took quite a while. 
Once that was done, it asked about mail routing and finished the install before ejecting the CD and rebooting.

The default desktop environment / default system install gave me the gnome desktop, both firefox and epiphany web browsers, openoffice.org and evolution, synaptic, lifrea, gaim and the gimp along with a whole slew of other programs. Everything was the latest version so far as I have seen. Build-essential was also installed by default (if I remember correctly) so installing a jabber client from source was a snap.

Installing the cups-pdf printer (following this thread: [http://www.ubuntuforums.org/showthread.php?t=188860](http://www.ubuntuforums.org/showthread.php?t=188860)) was also painless. We do a lot of printing to PDF in our office.

I added
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
deb-src [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main 
to the sources.list file and added the gpg key (see the FAQ here: [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)) to install mplayer and related multimedia codecs. 

I've installed gdesklets and tweaked the xorg.conf file to allow a better desktop resolution.

What impressed me most was that the installer automatically installed the 686 linux kernel.

So far all I have done is some testing on the system to see how it works with our in-house database, printers and network fax server. I am very impressed with the installation (though it was time consuming) and the speed at which this old, slow PC is now running.

I'm looking forward to the final release. The beta has me quite impressed. It may well be the OS we adopt here.

---

### Post by meng on 2006-09-05
During my recent flirtations with other Linux distros, I was very impressed by the Debian Etch netinstall. I am very tempted to make the switch if the final release is well received.

---

### Post by tturrisi on 2006-09-06
I run etch on my laptop now instead of Ubuntu.  I used the current net-install, but a bit different than how you did it.

When at the point of choosing software, I remove all X's and choose to download and install nothing at all.  This results in just the base system install.  At reboot I login as root and edit my sources.list to:
```
deb http://ftp.debian.org/debian/ etch main 
deb-src http://ftp.debian.org/debian/ etch main 
deb http://ftp.us.debian.org/debian/ testing main contrib non-free 
deb http://security.debian.org/ etch/updates main 
deb-src http://security.debian.org/ etch/updates main 
deb http://debian-multimedia.org/ etch main 
# below is for madwifi debs
# deb http://ftp.au.debian.org/debian/ testing main contrib non-free  
# deb-src http://ftp.au.debian.org/debian/ testing main contrib non-free
```

Next I install the pgp key for debian-multimedia.org followed updating apt.

Then I install the rest of my system (I prefer gnome, just the minimum). I usually use apt at this point to install much more, but rest can be done via synaptic if you don't know actual package names.
```
apt-get install xorg gnome-core synaptic gdm
```

This way, you can build the exact system you want w/out the bloat of gnome-desktop-environemnt package and the bloat of a full gnome install used in the etch installer.  I prefer abiword & gnumeric over openoffice & I do not want evolution or games.

---

### Post by greggh on 2006-09-09
> **tturrisi said:**
> I run etch on my laptop now instead of Ubuntu.  I used the current net-install, but a bit different than how you did it.

When at the point of choosing software, I remove all X's and choose to download and install nothing at all.  This results in just the base system install.  At reboot I login as root and edit my sources.list to:
```
deb http://ftp.debian.org/debian/ etch main 
deb-src http://ftp.debian.org/debian/ etch main 
deb http://ftp.us.debian.org/debian/ testing main contrib non-free 
deb http://security.debian.org/ etch/updates main 
deb-src http://security.debian.org/ etch/updates main 
deb http://debian-multimedia.org/ etch main 
# below is for madwifi debs
# deb http://ftp.au.debian.org/debian/ testing main contrib non-free  
# deb-src http://ftp.au.debian.org/debian/ testing main contrib non-free
```

Next I install the pgp key for debian-multimedia.org followed updating apt.

Then I install the rest of my system (I prefer gnome, just the minimum). I usually use apt at this point to install much more, but rest can be done via synaptic if you don't know actual package names.
```
apt-get install xorg gnome-core synaptic gdm
```

This way, you can build the exact system you want w/out the bloat of gnome-desktop-environemnt package and the bloat of a full gnome install used in the etch installer.  I prefer abiword & gnumeric over openoffice & I do not want evolution or games.

That's a good method for a clean install. I think I'm going to try your method with an Ubuntu Server install. Do you know if you can do just a server install with Edgy?

---

### Post by tturrisi on 2006-09-11
> **greggh said:**
> That's a good method for a clean install. I think I'm going to try your method with an Ubuntu Server install. Do you know if you can do just a server install with Edgy?
Not sure about Edgy, but yes, you can do what you want w/ the Etch net-install.

After loading just the base system do:

apt-get upgrade

apt-get install apache2 php4 mysql-server mysql-client openssh-server

optional:
apt-get install phpmyadmin some-ftp-server

---

### Post by MethodOne on 2006-09-15
Right now, I am downloading the 19 CDs for Etch (my portable hard drive has a FAT32 partition) and make DVDs from them with jigdo (on my NTFS or ext3 partitions).  Could anyone list some third-party repositories that they use for Debian (other than wine, vlc, debian-multimedia, and backports)?

I really liked the graphical installer, but it should boot into it by default.  It should be on the alternate CDs for Edgy+1.  The [screenshots of the desktop on shots.osdir.com](http://shots.osdir.com/slideshows/original.php?release=724&slide=41) remind me of Ubuntu, but without the brown.  It even includes the update utility!

---

### Post by Minyaliel on 2006-09-28
I've installed Etch on my main computer, it works like a dream. After this, I don't know if I'm coming back to Ubuntu again... that is, until the release of Edgy, anyway ;)

---

### Post by era86 on 2006-09-28
Is there any way to use the nm-applet in Ubuntu on Debian? And if so, is there a way to use it in PyPanel instead of Gnome?

Thanks!

---

### Post by Rumor on 2006-09-30
I am confident you can use the nm-applet. It's in the repositories. I don't know about using it with pypanel, though. I don't use pypanel.

---

### Post by JcZndeR on 2006-09-30
I am trying out different things right now and I was wondering how to get a graphic environment up and running on a debian install.
I downloaded "debian-31r3-i386-binary-1.iso" and it doesnt seem to have any graphical interface.  Its just a shell.
I can't quite figure out how to get connected to the internet working either so i can't just directly download X sever or w/e.
So does anyone know which binary(s) I'm suppose to download?
Thanks a bunch.

---

### Post by kerry_s on 2006-09-30
Maybe it just didn't detect your monitor or card. Try> startx <and see what error you get.

If it's like ubuntu-server-install you can try

apt-get update
apt-get install x-window-system-core gdm xterm (Your WM)

x-window-system-core = the xenviroment for gui

gdm = login manager, it can also be> kdm, xdm, wdm

xterm = terminal,there are lot's of terminals out there but this is what is used if your dropped to a shell or for fail safe mode.

(Your WM) = fluxbox, openbox, wmaker, gnome, kde

You might also want to add synaptic for a gui package handler.
Remeber in debian you have to su to root befor you can do this.

---

### Post by JcZndeR on 2006-09-30
I have tried startx.
its not even there
and as i said i don't know how to get internet connected
at least not without a gui

---

### Post by croak77 on 2006-09-30
How do you usually connect to the net? What type of connection do you have?

---

### Post by JcZndeR on 2006-09-30
I use a Wireless Linksys network adapter thingy, but I don't even know which program to use to set it up.

---

### Post by kerry_s on 2006-10-01
Okay, i see what the problem is you didn't get all the debian cd's, you just grabbed the first one. Since your not connected directly to the internet to do a net install, you'll need all the debian cd's from here-> 
> [ftp://mirrors.kernel.org/debian-cd/3.1_r1/i386/iso-cd](ftp://mirrors.kernel.org/debian-cd/3.1_r1/i386/iso-cd)
or for weekly
> [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/)

Debian is a big distro and if you do the net install then it's only one cd, but if you want the whole thing...

---

### Post by JcZndeR on 2006-10-01
Ahh... I see
thanks
I must have misunderstood their FAQs
I didn't realize I needed all of them.
Wow
This is gonna take a while
Thanks again

---

### Post by kerry_s on 2006-10-02
Yeah, there are much easier way's to get debian. I would just grab kanotix it's just 1 live/install cd and is built on debian sid(unstable).-> [http://distrowatch.com/?newsid=03717#0](http://distrowatch.com/?newsid=03717#0)

---

### Post by era86 on 2006-10-02
Thank you.. Actually.. I was having trouble before using nm-applet, but now I know what I was doing wrong. Instead of using the "test" in my sources.list, I was using "unstable".

---

### Post by gg234 on 2006-10-06
looking for some nice [web installer in action ]("http://www.debianadmin.com/debian-etch-beta3-graphical-mode-installation-with-screenshots.html")for debian etch beta3

---

### Post by cunawarit on 2006-10-12
I was happy as Jack the Biscuit with Debian Sarge and decided to upgrade to Etch. 

It all went wrong! See: [http://ubuntuforums.org/showthread.php?t=275586](http://ubuntuforums.org/showthread.php?t=275586)

I changed my sources.list from sarge to etch and from stable to testing.

Then did:
apt-get update

Then did:
apt-get dist-upgrade

Felt smug thinking how easy it all was and then got brought back to reality…It all went wrong...

It imported my Xfree86 settings into Xorg but it doesn’t work. I ran thru: 
sudo dpkg-reconfigure xserver-xorg 

…to no avail.

It complains about my mouse, about my graphics chipset and X doesn’t start. I think I choose the right chipset, then again I might not have, it was past 1am… so I don’t rightly know…

Also… My machine refuses to shutdown… I tried:

shutdown –a now

Numerous times and it kept on showing me the X server error logs and then logging me
Out and not shutting down. 

Also… 

apt-get install anything kept on complaining about untrusted sources and it never did before with Sarge. 

I haven’t got the error logs with me right now as I am at work, but has anyone else had a rocky transition from Sarge to Etch? When Etch is finally released, is the Xorg problem I am experiencing likely to be fixed? There is no Etch install CD right now, but this is likely to come with a nice hardware detection thing that will take care of that, right????

---

### Post by swamytk on 2006-10-13
My current Home PC (PIII/192MB) is installed with Debian sid. I have this setup for last one month and found stable. Actually I installed Debian Sarge through DVD. It was just base install. After first phase of installation, the installation wizard prompted for which tree of debian I wish to install. It offered Stable (Sarge), Testing (Etch) and Unstable (Sid). I selected Testing. I have heard that it is good enough stable for a Home PC. I did base installation only. After that X windows, XFCE 4.4 (beta) and all other applications were installed through apt-get and synaptic. Here is the list of applications I use:

1. Thunar file manager
2. Firefox browser
3. Thunderbird for GMail
4. Scribus for brochures and artwork
5. GIMP for image editing
6. Anjuta/Glade for learning development
7. xfce4-terminal for console
8. xmms and mplayer for audio/video
9. Bluefish for web development (Home site)
10. Gnumeric for home finance maintenance
11. OpenOffice.org (mostly for documents received through email)
12. gThumb for photos
13. Audacity for small voice recording (fun to record my child Udhaya’s voice)
14. gnome-volume-manager to auto run gThumb once camera plugged in, vcd/dvd auto play, cd-recording application auto play
15. Mousepad for simple text edit
16. xfce4 plugins - screenshot, volume manager, notes, screen lock. Though I don’t like tray running plugins much, I found these useful and light weight.
17. Orage - Calendar application which is simple and light weight with Event reminder and clock applet.
18. gTodo - Simple to-do manager

Pl. look at the attached screenshots.

I found this setup more than enough for any one’s day to day work. A week back I upgraded this setup to Unstable tree of Debian. It is rock stable. AFAIK Debian-Unstable is more stable than many other distributions. Apart from stability, the choice of application is important. I had that freedom to choose the above application list.

Summary:
If you have atleast 2 years of experience in Linux and legacy PC, Debian is the best distro to manage your PC with less resource utilization and flexible configuration of system and application. When you have brand a new PC, go for the great Ubuntu, which is nicely integrated and stable.

---

### Post by Anonii on 2006-10-13
I'm glad you liked Debian, since its my distro of choise and I'd be using it right now, if there wasnt this forum.

But well, the applications you listed are easily available in Ubuntu, too.
The APT packaging system too. But, unfortunately, the student some times surpass the teacher in some things, and Ubuntu has a freaking great community, when I cant say the same for Debian.


By the way, in 4months~ Debian 4.0 is coming out!

---

### Post by cunawarit on 2006-10-13
After having a bit of a nightmare time trying to upgrade to Etch with APT I went for a clean install... I didn't know an Etch Beta 3 install CD existed.

Anyway, it went OK the second time round. 

The Etch installer detected my graphics chip, Sarge had failed to do so. I did have to tweak the Xorg config file because it was set to only use 60Hz refresh.

The other issue I had was the Flash plugin (which I got from the Flash site) not playing sounds. After installing all the ALSA stuff, going thru the config and not working... It worked today after I rebooted.

I am happy now!!!! :D

Etch does seem slower than Sarge was though. I am using a Celeron 700 with 128 of RAM. And I'm using fluxbox.

---

### Post by hey_ian on 2006-10-15
Ubuntu is better for Linux beginners and users who migrate form windows. Debian sarge is better for server, not for home PCs, but Debian testing is.

---

### Post by Greevous on 2006-11-01
So you're saying that to go that way of installing Debian you have to download and burn 21 cds and run all of them? Isn't the sarge installation just a one-disk process? I believe I tried the same thing JcZnder did and got only the command prompt as well.

---

### Post by deanlinkous on 2006-11-02
nope
cd1 is enough to get you a basic gnome or a basic kde
I would go for debian etch instead of sarge.

---

### Post by JcZndeR on 2006-11-05
I stopped working with this for a while, but decided to work on this today
im lost
so i dont need all of them??
i dunno
because cd1 didnt seem to have much on it
and i am having trouble running cd2
am i suppose to boot with cd2 or run it after i boot up
if the latter how do i do that?
sry, i really havent learned to use a computer really well without a gui
one of the bad things about using windows for so long..

---

### Post by Lucho on 2006-11-08
So, I've been using 32-bit Debian on my machine for a while -since Sarge came out
in fact; I just upgraded to Etch now some 5 months ago- but this weekend I got the 
urge to try 64-bit Etch. Well, that and I was intrigued by the idea of a "how low can you
go" minimalist install of debian. So, I DLed the netinstall and went to work. The results:
               This is the first time I've used a graphic interface to install Debian OR Ubuntu.   It
worked just fine, but is anybody else left underwhelmed by it? 
            Out of the box, Etch doesn't do Static IPs, at least not that I saw. Easily corrected
by booting into the other SO on the HD and tweaking a few files, but oops :oops:  
           I pulled just enough of KDE to get the two apps that I really like- Konqueror 3.5.5
and amarok 1.4.1. Everything else is XFCE 4.3.99.
           The first thing I did after getting an xserver in place was to compile a brand-new
2.6.18.2 kernel and install the 9625 beta nvidia driver. So far, so good \\:D/     
       I only installed what I needed. Unfortunately I need quite a bit: CUPS, an office suite
(I went with Koffice 1.6 and kooka. It seems lighter.), Kaffeine-xine and Mplayer for 
multimedia, mencoder and acidrip, and finishing with Kopete.
          So I'm stuck with an install that's 1.7 GB acc. to GParted :shock:  But I've got a 
system that flies, it's so fast. And the boot is fast - I haven't timed it yet, but it's visibly
faster than my 64-bit Dapper- entering the session at only 106MB (remember, I need
CUPS, hplip, and kdelibs at startup, all of them 64-bits). 
         I'm still quite the noob at this, but I really like what I'm seeing. Just wanted to share 
my experiences.

---

### Post by deanlinkous on 2006-11-08
>  Out of the box, Etch doesn't do Static IPs, at least not that I saw
You must not of saw it then. :)

You load Konqueror and amarok and THEN you install xfce? Kind of defeats the purpose but whatever floats your boat. :)

1.7GB is a lot IMO. Did you download all this and if so then have you cleaned the apt cache? That should free up some room.

One thing I love about linux is picking and choosing my favorite apps instead of being given a certain set. That is why I am rarely pleased with the one CD approach of a lot of distros.

Etch is awesome!

---

### Post by tturrisi on 2006-11-08
Etch DOES DO static ip setup right in the graphical installer!  When the screen comes up for networking and it says something like "configuring network w/ dhcp" then select & use the cancel button.  You will then be give choices how you want to config the network.  DHCP, manually, etc.  Choose manually & set your network info.

You can also use select & use the Back buttons to get back to a main installer menu where you can manually select the install steps.  Use this method to skip creating a user account other than root during the install.  You can addusers later after the system is setup and desired software has been installed.

---

### Post by Lucho on 2006-11-09
So, the static IP thing is about what I thought. I thought I had missed something;
oh well, live and learn ;)  I'm not used to graphic installers yet- IMO ncurses installers are better than most people give them credit for.
> You load Konqueror and amarok and THEN you install xfce? Kind of defeats the purpose but whatever floats your boat. 
 
 1.7GB is a lot IMO. Did you download all this and if so then have you cleaned the apt cache? That should free up some room.
 
    Actually, I should have expressed myself better. I did what some here have done:
I didn't install anything from the installer; a reboot later, I used the absolute minimal
base install to apt-get xorg, kde-core, synaptic, and kdm. That got me konqueror-
I didn't install it separately. From there I compiled the kernel, which is where I got 
most of the installed libs and why I'm thinking of reinstalling- I've got the compiled 
2.6.18.2 kernel, so I don't need all the other cruft. 
  Anyway, only after that did I install everything else (amarok, XFCE,etc). I'm still a
bit of a noob; this was my first netinstall and I'm naturally disorganized anyway.
I'm satisfied though- it taught me a little (about organization lol :rolleyes: ) and
Etch really is awesome! :mrgreen: :mrgreen:

---

### Post by Lucho on 2006-11-09
Ok, one quick thing, and I promise to shut up ;) 
 I decided that, instead of reinstalling to avoid the mistakes I made in the
netinstall, I'm going on a apt-cleaning frenzy. Anything not absolutely necessary
is gone. Unfortunately I need:
an office suite for work (abiword & Gnumeric aren't enough; for now Koffice w/Kooka)
apps for audio + video encoding (for now acidrip/mencoder)
multimedia (amarok, kaffeine-xine, mplayer)
messenger (kopete for now) 
   So far, I've only been able to slim the system to about 1.2 GB. The problem is that
I tried to build a debian box I can work on. I probably shouldn't complain too much;
it's not like the system is deficient. I'm just spoiled by a couple of KDE apps.

---

### Post by deanlinkous on 2006-11-09
:D I was just saying IMO you might as well use KDE instead of XFCE. But as I said, whatever floats your boat. If I want a really light system then I try to stay away from anything that pulls in too much stuff. I have my favorite software list but occasionally I go looking at all the alternatives to see if something catches my eye and meets my requirements of being reasonably light. If it was me and I wanted a light system but a good file manager I would check out some of the others since Konq pulls in so much other stuff. But having some fun and plenty of choice is what it is all about.

---

### Post by tturrisi on 2006-11-09
Myself, I prefer Gnome, so I do a net install and deselect software using the spacebar.  This reboots to a minimal system.  Then do apt-get upgrade to get the latest security & upgrade packages.  Then edit my sources.list and do:
~$apt-get install xorg gnome-core w32codecs mplayer
Absolutely NO gdm.  This way I can boot the system and don't have to login and still be able to have my servers running. (w/out bloated gdm stuff)

---

### Post by Lucho on 2006-11-09
I actually don't like KDE so much as I like Konqueror and amarok. I'm trying
to like XFCE, but it's a slow process (it's just kind of wierd :-k).
I totally agree- just the absolute minimum. Now that I know how a netinstall
works I can avoid repeating the mistakes of this time.

---

### Post by deanlinkous on 2006-11-09
Just gotta have those two huh? ;)
I think XFCe is cool, but I never have gotten use to it and as such cannot say I (personally) like it either. I actually like icewm or if I really want something of my own making then I grab sawfish window manager and a panel like py-panel.

Of course KDE can be customized like crazy and changed around.

Anyway, have fun with it...

---

### Post by gctaylor1 on 2006-11-11
Hi,

Can I install xfce4 in etch when I already have gnome installed?

I'm trying to do this with aptitude and I get dependency problems that I can't figure out.
I select the xfce metapackage, and as I hit e to examine the suggested solutions, aptitude suggests these 8 keeps.
gamin
libgamin0
libthunar-vfs-1-2
thunar
xfce4
xfce4-session
xfce4-utils
xfdesktop4

So I scroll down to xfce4 and in the bottom pane it displays:
xfce4 depends upon xfdesktop4 (>= 4.3.99.1-1)
--\ The following actions will resolve this dependency:
  -> Cancel the installation of xfce4
  -> Install xfdesktop4 [4.3.99.1-1 (testing, testing)]

So I scroll down to xfdesktop4 and in the bottom pane it displays:
xfdesktop4 depends upon libthunar-vfs-1-2 (>= 0.4.0rc1-1)
--\ The following actions will resolve this dependency:
  -> Cancel the installation of xfdesktop4
  -> Install libthunar-vfs-1-2 [0.4.0rc1-2 (testing, testing)

None of these packages are installed yet, plus the solutions seem circular to me?

What am I doing wrong here?

---

### Post by gctaylor1 on 2006-11-11
Okay.  I figured this out.  I just needed to look at each "keep" and follow the dependency trail.  In this case it was gamin that was conflicting with fam, and fam didn't want me to uninstall because of something else that I can't remember.  The main thing is that they were recommends, not what I'd call real dependencies.  Once I worked my way back and uninstalled the beginning recommend I could keep uninstalling until the issue was resolved.

xfce4 is installed, working, and looking awesome!

---

### Post by Ptero-4 on 2006-11-11
gctaylor1, as a note for future cases. To avoid installing "recommends" automatically go to "Options">"Dependency handling" and uncheck "Install recommended packages automatically".

---

### Post by deanlinkous on 2006-11-11
Are you up to date? That is strange. Did you try apt? Do you only have testing listed in your sources?

---

### Post by gctaylor1 on 2006-11-12
Ptero-4: thanks for the tip, I'm still finding my way around Debian (and Xubuntu).  Sometimes I find it useful to pull in the recommends automatically and sometimes it's a pain.  Haven't figured out the best way yet.

deanlinkous: 
```
Are you up to date? That is strange. Did you try apt? Do you only have testing listed in your sources?

```
Pretty sure I'm up to date.  I first installed Sarge last week to get a feel for the system and see how old the packages were.  They're old.  I also wanted to know that a dist-upgrade would would work in the future if I decided to stay with debian and/or xubuntu.   I had used debian around the slink/potato era and because of a pptp package I needed I ended up using a mix of stable and testing and eventually my system got pretty messed up.  Anyway I'm trying to do it right this time.  

I haven't used apt because I'd read that aptitude automagically handles the dependencies better and I need all the help I can get.  

I changed all of my sources to testing right before I upgraded.

I'm really impressed with both etch and dapper(and even sarge, really). Things have come a long way since I've been away from debian and I think I'll be staying this time.  

Gary

---

### Post by patrickfromspain on 2006-11-14
I've just installed Debian Etch RC1... an so far, I'm very impressed with it. The new graphical installer is very nice, and once it is installed it seems to be faster than ubuntu.

The only thing I'm missing is the ubuntu kernel.. my battery monitor doesn't work with vanilla kernel until 2.6.18, and etch has 2.6.17 and hasn't patched Smart Battery Support into it. Not a big deal... 2.6.18-2 compiling ;)

Overall.. I like it!

---

### Post by Lucho on 2006-11-14
Well, I've been running 64-bit Etch for some days now, using it as my main workbox.
Wow... Etch really *is* faster than Ubuntu, and I'm comparing it with the two using
the same hand-rolled kernel (2.6.18.2), same graphic driver (Nvidia 9629), and
the same tweaks. I ended up yanking XFCE from the system and running a pure
KDE (although decidedly minimalistic, as previously posted).
     I can't wait to see how the final release of Etch turns out next month :cool:

---

### Post by midwinter on 2006-11-15
I've been running Etch for a day now and it seems quite nice.  I am slightly surprised I had to turn off installing all recommended dependencies by default, in order to prevent a lot of uneeded bloat.  Also some of it is not particularly transparent in the way that I would like.. I guess i'm too used to Arch.  I'll stick with it for now though.

---

### Post by medeski on 2006-11-19
Since it's been a week this post might not be relevant anymore, but in case it is:

It's been a while since I installed Etch, but disk 1 should be enough.  The graphical install version should make things easier -- is it possible you grabbed the wrong iso?

The extra disks are basically snapshots of the repositories, and are probably most useful on a machine with no internet connection at all.  In other words, on such a machine you'd be able to apt-get from the cds themselves without using the network.

Anyway, [this]("http://www.debianadmin.com/debian-etch-beta3-graphical-mode-installation-with-screenshots.html") seems like a decent walkthrough for the installation process -- hope it helps.

---

### Post by scrooge_74 on 2006-11-19
When I was starting I went with Debian Sarge, I only had to download 2 CDs and after some configuring I was on my way. So he probably got the wrong ISO files.

After installing I had to make some changes in sources.list to get the rest of the repositories.

---

### Post by Lucho on 2006-11-19
Well, nothing lasts forever. After such a good time with Etch,
I suppose it was inevitable that something would go wrong. My
Nvidia driver decided to stop working. Actually, it somehow got
corrupted, and I can't for the life of me get it reinstalled.
Here's the log from my attempts to reinstall the driver. Keep 
in mind that:
     - the file that it says is missing does indeed exist, and 
always has. Nothing has changed.
     - the driver has already been installed on this system, so 
there is no doubt that it works (hmm... worked).
 > nvidia-installer log file '/var/log/nvidia-installer.log' 
creation time: Sun Nov 19 18:10:27 2006 

option status: 
  license pre-accepted    : false 
  update                  : false 
  force update            : false 
  expert                  : false 
  uninstall               : false 
  driver info             : false 
  precompiled interfaces  : true 
  no ncurses color        : false 
  query latest version    : false 
  OpenGL header files     : true 
  no questions            : false 
  silent                  : false 
  no recursion            : false 
  no backup               : false 
  kernel module only      : false 
  sanity                  : false 
  add this kernel         : false 
  no runlevel check       : false 
  no network              : false 
  no ABI note             : false 
  no RPMs                 : false 
  no kernel module        : false 
  force SELinux           : default 
  no X server check       : false 
  force tls               : (not specified) 
  force compat32 tls      : (not specified) 
  X install prefix        : (not specified) 
  X library install path  : (not specified) 
  X module install path   : (not specified) 
  OpenGL install prefix   : (not specified) 
  OpenGL install libdir   : (not specified) 
  compat32 install chroot : (not specified) 
  compat32 install prefix : (not specified) 
  compat32 install libdir : (not specified) 
  utility install prefix  : (not specified) 
  utility install libdir  : (not specified) 
  doc install prefix      : (not specified) 
  kernel name             : (not specified) 
  kernel include path     : (not specified) 
  kernel source path      : (not specified) 
  kernel output path      : (not specified) 
  kernel install path     : (not specified) 
  proc mount point        : /proc 
  ui                      : (not specified) 
  tmpdir                  : /tmp 
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com) 
  RPM file list           : (not specified) 

Using: nvidia-installer ncurses user interface 
-> License accepted. 
-> There appears to already be a driver installed on your system (version: 1.0- 
   9629).  As part of installing this driver (version: 1.0-9629), the existing 
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a 
   bort installation) (Answer: Yes) 
-> No precompiled kernel interface was found to match your kernel; would you li 
   ke the installer to attempt to download a kernel interface for your kernel f 
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No) 
-> No precompiled kernel interface was found to match your kernel; this means 
   that the installer will need to compile a new kernel interface. 
-> Performing CC sanity check with CC="cc". 
-> Performing CC version check with CC="cc". 
ERROR: The kernel header file 
       '/lib/modules/2.6.18.2.rob64/build/include/linux/version.h' does not 
       exist.  The most likely reason for this is that the kernel source files 
       in '/lib/modules/2.6.18.2.rob64/build' have not been configured. 
ERROR: Installation has failed.  Please see the file 
       '/var/log/nvidia-installer.log' for details.  You may find suggestions 
       on fixing installation problems in the README available on the Linux 
       driver download page at [www.nvidia.com](www.nvidia.com).
can anybody give this poor noob a hand?

---

### Post by deanlinkous on 2006-11-19
Did you update something? change anything?

---

### Post by Lucho on 2006-11-19
Well you see, that's the problem. The corruption was caused (I think,
I'm noob enough to not say for certain) by an update to xorg- it was
7.1.something. I have a 32-bit Etch on my HD. It went through the same
process (with the same custom kernel and Nvidia driver: 2.6.18.2 and
9629 respectively). However, when I reinstalled, everything went by the
numbers. Not a single error in 32-bit Etch, only in 64-bit Etch.

---

### Post by JcZndeR on 2006-11-23
Thanks..
i will try
aiya..
installing ubuntu was much easier
im hoping debian is worth it
by what i've heard, it prbly is

---

### Post by scrooge_74 on 2006-11-23
At the end I had a Debian stable version which worked very well and some of the programs like Open Office, Gaim, Firefox i got them from debian backports so I had the same programs as the unstable version.

In the end I learned a lot of things, know I find Ubuntu very easy, but I had a good school working with Debian itself

Have fun

---

### Post by greggh on 2006-12-09
I just did the net install for etch. The iso is only 127 MB to download. I chose to do the base + desktop install. It detected everything automatically,connected to the mirror, and installed a full Gnome desktop very similar to Ubuntu. Everything just worked. Etch is faster than Dapper. It boots in just 25 seconds. Dapper takes 40. System monitor shows Etch takes 90 Mb memory after boot. Dapper takes 110. I'm moving to Etch. :D

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by IYY on 2006-12-09
Sounds cool. I do hear Etch is less stable and buggier than any Ubuntu release.

---

### Post by xabbott on 2006-12-10
I used Etch for a bit. It's actually (from strictly desktop perspective) not very different from Ubuntu. I found Edgy better in terms performance and just general polish. Note that Etch isn't a release yet so it isn't a fair comparison.

To the OP. As far as the boot times and memory. I would assume its a difference in the services being loaded. I've never used Dapper, used debian most of the time. But I found Edgy to boot much much faster.

---

### Post by Kindred on 2006-12-10
I've been running Testing/Etch for about a month, i'm definitely sticking with it for the forseeable future.  It's been extremely stable for me and really quite fast, though not 'Arch' fast (but what is?).  

Upgrading has been problem free & with no desktop metapackage required (what's that all about anyway?..).

---

### Post by mips on 2006-12-10
Anyone here try [sidux]("http://www.sidux.com/") ? Based on debian sid.

---

### Post by tturrisi on 2006-12-10
I've been using Etch for some time now w/ no issues.  The last 2 installs I did by using the business card net install.  The neat thing w/ that is you can boot using the command "expertgui" and during the install you can choose the exact kernel you want.  That way you don't end up w/ the stock 486 kernel that you then have to upgrade to 686 or 686-smp.

The other advantage is it makes it so much easier to then install kernel-headers & build-essential & module-assistant & build packages from source while not running into any conflicts in headers (486 vs. 686).

To reduce the memory used and increase efficiency, I DESELECT software during the installation by using spacebar to remove the x's next to Desktop & Base System. Selecting "Desktop" installs the complete gnome-desktop-environment when all you need is: (at first boot do)
apt-get install gnome-core xorg synaptic (if want gui for software installs)

After installing ALL the packages I need & want it uses 97 mb of ram at boot.

---

### Post by r4ik on 2006-12-10
I gave it a try the new 'installgui" is dead easy.
When you know your way in the terminal a bit it is not hard to install
the extra's you want to.
Lets see what the future brings. :)

---

### Post by deanlinkous on 2006-12-10
Of course using a preseed file has always been dead easy, one command easy in some cases.

The new installer is nice for thsoe that want/need it and I am glad to see it.

---

### Post by xabbott on 2006-12-10
You know you can do the Etch style install with Ubuntu as well. I think it's the same exact installer. You can then apt-get gnome-core, etc. That is why I said from a desktop perspective they are nearly identical.  o_O

---

### Post by tturrisi on 2006-12-10
> **xabbott said:**
> You know you can do the Etch style install with Ubuntu as well. I think it's the same exact installer. You can then apt-get gnome-core, etc. That is why I said from a desktop perspective they are nearly identical.  o_O
Agreed, except w/ etch you get a lot less unneeded stuff.  For example, if I want an im client I'll install the one I choose.  But I don't use im so I don't get it w/ etch.  Same for office apps.  I don't dig openoffice, I prefer abiword & gnumeric.  And for multimedia, I just use mplayer for all but occasional mp3 listening & then I use xmms. I like having the choice of what apps I want rather than acchieving what I want by uninstalling what comes w/ ubuntu.

---

### Post by xabbott on 2006-12-10
You can literally install them both almost the same exact way. If you took the kernel/img you can install Ubuntu from it. I was about to say that maybe if you use the Live CD that you have to get all the default apps. But I don't know that for sure. I installed Ubuntu like I did Debian.

---

### Post by deanlinkous on 2006-12-10
huh?

---

### Post by xabbott on 2006-12-10
I meant, all you need to install Ubuntu is its kernel and initrd.img. Meaning, you don't have to install apps you don't want to.

---

### Post by Ben Sprinkle on 2006-12-11
Hello, I am going to try Debian, I burned the stable of Sarge last night.
I am using net install because it looks perfect for what I need. (I don't want all the extra bull)

I heard that Etch is coming out soon but has been delayed to January or Febuary or something.
Should as of now, use Etch, Sid, or Sarge??
Please tell me reasons for each including performance, stability, crashing and etc. I will probably be using Xfce as well.

Thanks.

---

### Post by Rumor on 2006-12-11
I've been using Etch on one box for some time with no problems. Most everyone who has chimed in here seems to have had good success with Etch. I've found it very stable.

---

### Post by Ben Sprinkle on 2006-12-11
[http://www.linuxforums.org/forum/debian-linux-help/62596-etch-vs-sarge.html](http://www.linuxforums.org/forum/debian-linux-help/62596-etch-vs-sarge.html)
I am reading that thread now, I am starting to lean more towards Etch now. Hmm.

---

### Post by jdhore on 2006-12-11
i say go for Etch, it has very up-to-date stuff, Xorg and it's very fast and stable...Sarge is getting long in the tooth and it's still running XFree and IMO, Sid is just too new and too likely to have issues for me to want to even try it

---

### Post by xabbott on 2006-12-11
For general desktop use, Etch. You'll be able to mix Sid packages in most of the time too.

---

### Post by Ben Sprinkle on 2006-12-12
Alrighty, Etch it is. ;)

---

### Post by mips on 2006-12-12
> **Goat Spirit said:**
> Alrighty, Etch it is. ;)

Did you have a  look at [sidux]("http://sidux.com/")

It's 'stable' sid :mrgreen:[]("http://sidux.com/")

---

### Post by mystdragon on 2006-12-13
If you're up to it, I recommend testing.  If you like stability, without the worry of your options getting long-in-the-tooth, or you want the newer toys without worrying about them breaking, testing is great.

At the moment etch and testing are one and the same.  Once etch is frozen, however, testing will begin to pull in new stuff, while etch will basically remain frozen, save for security updates.

I've run this way for years, starting when woody was in testing.  I've been fairly happy with testing and haven't had any problems with it.

---

### Post by handy on 2006-12-13
[_**I 2nd Sidux!**_]("http://sidux.com/index.html")

---

### Post by mips on 2006-12-13
> **handy said:**
> [_**I 2nd Sidux!**_]("http://sidux.com/index.html")


how did it work out for you ?

---

### Post by Ben Sprinkle on 2006-12-13
I hate sidux.

---

### Post by handy on 2006-12-13
> **mips said:**
> how did it work out for you ?

I've answered this in another post, but I just had to say it here too Mips!

Sidux, is fast!  It installed without a hitch, & I did it the long way around, installing Etch RC1 first & then running the h2 script. It will be so much easier when they release their first .iso.

I'm very impressed with it.

P.S. I'm really glad that I don't know what hate is!

---

### Post by Ben Sprinkle on 2006-12-13
Well mabey not hate, I just don't like it that much.

---

### Post by zugu on 2006-12-14
Hello everyone.

I'm thinking more and more of switching my desktop from Ubuntu 6.06 to Debian. Here are the reasons I want to leave Ubuntu:

- important applications, such as VLC, Firefox, GAIM etc. do not receive backports for the 6.06 release
- I want to try something new
- I don't like the Ubuntu "habit" of including beta software in the official releases
- I need a stable desktop

What I don't know if Debian can offer me, nevertheless I want from it:

- a more stable desktop;
- backports and updates for the important applications;
- no beta software in the official releases;
- easy installation of the nVidia legacy drivers and other proprietary packages (if it's just as easy as in Ubuntu, then it's OK with me)
- more control over what packages to install in the installer;

So, is Debian for me? I've been using Ubuntu for almost a year, and I'm already familiar with the apt system and the GNOME desktop environment. Will I survive in a Debian world?

---

### Post by matthew on 2006-12-14
Debian is quite good. You might need to do some work to make it look/feel exactly like you are used to in Ubuntu, but it's not impossible by any means. I recommend you try the testing branch, currently called "Etch." If you have a free partition on your hard drive or an extra computer to do a test install first and see if you like it that would be a good idea. In any case, back up all your data before you do anything.

---

### Post by zugu on 2006-12-14
Should I wait until Etch is out?

---

### Post by matthew on 2006-12-14
> **zugu said:**
> Should I wait until Etch is out?
No. It's quite stable now and it is still receiving updates. 

If you use Sarge you will run into the same thing you are with Dapper...just security updates as the software gets older. Stable releases are more stable because they stick with tried and true stuff at the expense of having the latest and greatest.

Anyway, Etch is very stable for an everyday desktop user. Stay away from Sid unless you know what you're doing.

---

### Post by zugu on 2006-12-14
So, Etch will eventually receive security updates only, just as Sarge?

Thank you for the replies.

---

### Post by xabbott on 2006-12-14
You do know that, like Ubuntu you won't get new versions of software only security updates...

In fact I believe once Etch is released it wont even have any version of Firefox. Right now Etch gives you Firefox 1.5. I got 2.0 (Iceweasel) by adding Sid repos. I personally think you don't gain or lose much going from Ubuntu to Debian.

---

### Post by patrickfromspain on 2006-12-14
I installed Debian Etch to try... but I've just decided to stay.. I really like it. It's already very stable (RC1 stage passed, waiting for RC2). Edgy had some nasty bugs, and both Edgy and Dapper, comparing to etch, feel slower and less responsive, plus edgy is not as stable.

Etch is a bit a mix of dapper and edgy. Libc6 (2.3.6 I think) and gnome (2.14) are the same version as Dapper, while Xorg is the same version as Edgy (7.1). 

Drivers and so on... No problems. I've installed codecs without a problem using through Synaptic, the same as installing the NVIDIA drivers (I install the NVIDIA drivers from [www.nvidia.com](www.nvidia.com), running the installer)

Try it!

---

### Post by rplantz on 2006-12-14
> **xabbott said:**
> I personally think you don't gain or lose much going from Ubuntu to Debian.
After working with both distros, I concur with xabbott's statement.

A couple of weeks ago I installed Debian Etch so that I can dual boot into it or Ubuntu 6.10. Both of my installs are 64-bit.

My reasons were very similar to zugu's, except that I wanted to be more on the bleeding edge than more stability.

Perhaps Debian gives me a little more flexibility, but that also means that I need to do more to configure it. For example, I wanted to create a public_html directory in my home directory so I could run php scripts. It took me a while to get it working in Debian. It was fun, and I learned a lot. But in Ubuntu I just did mkdir public_html and it all worked.

On the other hand, Keyboard Indicator 2.16 is broken in 64-bit Ubuntu. Debian still uses 2.14, which works just fine.

So far, I have not found any advantages of Debian over Ubuntu for my uses.

---

### Post by robbie75 on 2006-12-14
Hi,
I come from the debian world: several years with
my trusty debby...started with the unforgettable 
woody :) then sarge and last, etch... till the last
summer when I decided to give a try to ubuntu and 
I really appreciated its world and its phiplosphy,
so I am currently using Dapper :) and I'm pretty happy with it
but, at least for the moment I have Debby on all
of my servers.

BTW I totally agree with rplantz

---

### Post by Kindred on 2006-12-14
I'd certainly recommend Debian Etch also, it's working great for me so far.

---

### Post by zugu on 2006-12-15
This is unfortunate, the thing I hate most is being stuck with old versions of the software. Why is that? Isn't there a solution for people to have a stable system AND update important software as-you-go?

Maybe the approach is wrong. Right now, distro makers have to customize pieces of software, in order to be sure that software won't create problems. I think it should be the developer's job to make sure his program works well, not the distribution maintainer. This would also encourage "natural selection".

It looks as if the OSS world is more of an unfinished business: the developers write their code, and some other people finish the job in whatever way they see fit.

This is WRONG.

Also, I have always thought that "bleeding edge" is when one installs every experimental/alpha/beta software one can think about, not when trying to update VLC player to the latest stable version.

---

### Post by mips on 2006-12-15
> **zugu said:**
> This is unfortunate, the thing I hate most is being stuck with old versions of the software. Why is that? Isn't there a solution for people to have a stable system AND update important software as-you-go?


[Sidux]("http://sidux.com/")  ?

---

### Post by Kindred on 2006-12-15
> **zugu said:**
> This is unfortunate, the thing I hate most is being stuck with old versions of the software. Why is that? Isn't there a solution for people to have a stable system AND update important software as-you-go?

Maybe the approach is wrong. Right now, distro makers have to customize pieces of software, in order to be sure that software won't create problems. I think it should be the developer's job to make sure his program works well, not the distribution maintainer. This would also encourage "natural selection".

It looks as if the OSS world is more of an unfinished business: the developers write their code, and some other people finish the job in whatever way they see fit.

This is WRONG.

Also, I have always thought that "bleeding edge" is when one installs every experimental/alpha/beta software one can think about, not when trying to update VLC player to the latest stable version.

Maybe try Arch then, or possible even Debian Unstable.  

I have not used Debian unstable but Arch is really quite stable.  You will run into occasional bugs in packages though because they haven't been tested for long enough before going into the distro. 
 
One of the Unix philosophies is release early and often, this is the way it is and you generally have to compromise on stability or have slightly older packages (which is not all that bad really.... ever had a Windows system all up to date?  Me neither, I never cared all that much then at all).  

Arch is pretty good though.

---

### Post by patrickfromspain on 2006-12-15
if you install debian sid you will always be on the bleeding (maybe broken, too) edge. If you install etch and change etch with testing in sources.list, you will always have an updated system and quite stable too, always getting newer versions.. not bad, you decide.

---

### Post by yabbadabbadont on 2006-12-15
> **patrickfromspain said:**
> if you install debian sid you will always be on the bleeding (maybe broken, too) edge. If you install etch and change etch with testing in sources.list, you will always have an updated system and quite stable too, always getting newer versions.. not bad, you decide.

Thanks for that information.  I was wondering if it would be as simple as that.

---

### Post by fluffnik on 2006-12-17
> **zugu said:**
> This is unfortunate, the thing I hate most is being stuck with old versions of the software. Why is that? Isn't there a solution for people to have a stable system AND update important software as-you-go?

The key word in Debian System is System.

Everything has to interoperate, nothing must break anything else non-conflicting.

Stable and unstable in Debian terms refer to the ABI and configuration and packaging namespace and syntax rather than the robustness of individual apps.

If you want to play get the Debian Installer (DI) buisness card snapshot ISO which lets you choose and gets the latest *everything* for your chosen release from the net...

---

### Post by SnTholiday on 2006-12-20
I am a noob to both Ubuntu and Debian. Last night I tried to install Debian/Sarge using the netinstall and everything went fine, but when I chose the desktop environment for the packages, it downloaded both apps for gnome and kde. How do I add only a gnome desktop? Is installing Etch easier?

Thanks.

---

### Post by deanlinkous on 2006-12-20
> **xabbott said:**
> I meant, all you need to install Ubuntu is its kernel and initrd.img. Meaning, you don't have to install apps you don't want to.

That would be one HECK of a minimal install and I have no idea what function you would gain from it. :)

---

### Post by deanlinkous on 2006-12-20
> **SnTholiday said:**
> I am a noob to both Ubuntu and Debian. Last night I tried to install Debian/Sarge using the netinstall and everything went fine, but when I chose the desktop environment for the packages, it downloaded both apps for gnome and kde. How do I add only a gnome desktop? Is installing Etch easier?

Thanks.

Etch is a breeze, especially the GUI installer....

By default etch will install only the GNOME desktop now AFAIK...

---

### Post by BigDave708 on 2006-12-20
Welcome to Debian. I migrated to Etch from Ubuntu myself.

> **IYY said:**
> Sounds cool. I do hear Etch is less stable and buggier than any Ubuntu release.
All Ubuntu releases are based off Debian Sid (the 'unstable' release), whereas Etch is currently the 'testing' release. Generally speaking, Etch and Sarge (the current 'stable' release) are both considered to be more stable than Ubuntu because they have been in development longer, although that means they can sometimes have slightly out-of-date programs in them. But, no, Etch is by no means 'buggier than Ubuntu'.

---

### Post by tkjacobsen on 2006-12-20
Last time i checked etch had a lot of  applications in newer versions than edgy.. Also when not preparing for release, debian testing is updated more often than ubuntu, and therefore has newer versions.. That is my experience.

---

### Post by greggh on 2006-12-20
> **tkjacobsen said:**
> Last time i checked etch had a lot of  applications in newer versions than edgy.. Also when not preparing for release, debian testing is updated more often than ubuntu, and therefore has newer versions.. That is my experience.

Two of the main apps, gnome and firefox are older with etch though. Etch gives you gnome 2.14, Edgy gives you gnome 2.16. Etch gives you FF 1.5, Edgy gives you FF 2.0. You can change your sources.list to Sid though and get the newest of everything.

---

### Post by jobezone on 2006-12-20
> **greggh said:**
> Two of the main apps, gnome and firefox are older with etch though. Etch gives you gnome 2.14, Edgy gives you gnome 2.16. Etch gives you FF 1.5, Edgy gives you FF 2.0. You can change your sources.list to Sid though and get the newest of everything.
Or you can wait until Debian devels backport gnome 2.16 for etch ([http://www.backports.org](http://www.backports.org) (which they promise they will after etch is released).

---

### Post by xabbott on 2006-12-21
> **SnTholiday said:**
> I am a noob to both Ubuntu and Debian. Last night I tried to install Debian/Sarge using the netinstall and everything went fine, but when I chose the desktop environment for the packages, it downloaded both apps for gnome and kde. How do I add only a gnome desktop? Is installing Etch easier?

Thanks.

Yes, Etch is easier and is soon to be the new stable. Don't bother with Sarge. Also if you want KDE over Gnome do **not** select Desktop Environment during the install. Once you land at command line do:
```
apt-get install x-window-system-core kde
```

I also recommend the [Debian wiki]("http://wiki.debian.org/") for more help.

---

### Post by elijahclarity on 2006-12-21
Hi all
I think this was cool stuff so I decided to share it with ya all:

In a mail on d-d-a ([http://lists.debian.org/debian-devel-announce/2006/12/msg00006.html](http://lists.debian.org/debian-devel-announce/2006/12/msg00006.html)) 

"The KDE and XFCE variants of CD#1 are now being produced to give more
choice to people for initial installation. By default, CD#1 has always
meant to be enough to install a fully-functioning system, including a
desktop. On sarge, we (just about) managed to make all that fit,
including a choice of KDE or Gnome. However, since the sarge release
the size of the set of packages needed to cover each desktop *and* the
rest of the base system has grown substantially. We're now at the
point where that's just not possible any more. The default CD#1 will
now install a Gnome desktop, and there are replacement CDs that will
install KDE or XFCE instead. Download your own choice. Thanks to Joey
Hess for the work to make these happen. "

I think this will be announced in the release notes when Etch goes final.

You can try the Xfce & KDE versions here:
[http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-xfce-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-xfce-CD-1.iso)
[http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-kde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-kde-CD-1.iso)

Plz let us know how good they are compared to Xubuntu/Kubuntu.

I got all this info from a thread at a Debian forum here [http://forums.debian.net/viewtopic.php?t=10832&start=0&postdays=0&postorder=asc&highlight=](http://forums.debian.net/viewtopic.php?t=10832&start=0&postdays=0&postorder=asc&highlight=)

Aint it great news? :p

---

### Post by BarfBag on 2006-12-21
Very good news!  I flip-flop between desktop environments way too much.  I prefer KDE over GNOME, but prefer the way GNOME makes fonts look over KDE.  Just something else that makes me want to try Etch.  It's looking really good.

---

### Post by elijahclarity on 2006-12-21
> **BarfBag said:**
> Very good news!  I flip-flop between desktop environments way too much.  I prefer KDE over GNOME, but prefer the way GNOME makes fonts look over KDE.  Just something else that makes me want to try Etch.  It's looking really good.
Ur pretty right....I just cant wait to download the Etch CDs! :D

---

### Post by shining on 2006-12-21
I like the names much more, that's what Ubuntu should have done since the beginning.
ie Ubuntu-kde instead of Kubuntu, and Ubuntu-xfce instead of Xubuntu

I'm not sure which one is better for a new user though.

---

### Post by lyceum on 2006-12-21
I read a blog that said the Etch would knock Ubuntu off number one. Not trying to flame, just wanting to know, what is the big deal about it?

---

### Post by jobezone on 2006-12-21
When etch is released, they'll be giving 3 different sets of the first install cd, one which contains GNOME, one KDE, and one XFCE.

---

### Post by plb on 2006-12-21
[http://wiki.debian.org/NewInEtch](http://wiki.debian.org/NewInEtch)

---

### Post by RAV TUX on 2006-12-21
moving to the Debian Forum.

---

### Post by lyceum on 2006-12-22
> **plb said:**
> [http://wiki.debian.org/NewInEtch](http://wiki.debian.org/NewInEtch)

Cool, thanks fot the link!

---

### Post by greggh on 2006-12-22
This is good. But it would really be GREAT if they offered seperate cd isos to just install KDE-core and Gnome-core.

---

### Post by maxamillion on 2006-12-22
Very interesting ... Makes me wonder if they are trying to gain back some desktop real estate lost to (x|k|ed)ubuntu or just deciding to go with it because it has shown as a success in the community by adding the choices.

---

### Post by MetalMusicAddict on 2006-12-22
> **lyceum said:**
> I read a blog that said the Etch would knock Ubuntu off number one. Not trying to flame, just wanting to know, what is the big deal about it?

Etch is like Dapper.

Ive been doing alot of testing with Debian (Sid) vs. Ubuntu (Feisty). [HERES]("http://ubuntuforums.org/showpost.php?p=1910785&postcount=107") my opinion.

---

### Post by maxamillion on 2006-12-22
Allow us to investigate how pointless it is to compare debian and Ubuntu (especially ubuntu alpha and debian sid):

What is Ubuntu?
A six month incremental snapshot of debian sid repositories with custom kernel, packages, and configurations targeting the ease of use for desktops.

.... ermm, I actually don't need to continue, That will suffice.

---

### Post by xabbott on 2006-12-23
Honestly it's pretty pointless to compare them at all. I went from Debian to Ubuntu (on my desktop) but there is very little difference.

I just like when I see people who start with Ubuntu and go to Debian (Etch) state how much faster Debian is. ](*,)

---

### Post by patrick295767 on 2006-12-23
I am having troubles wiht 
Xwrapper.config
from user, as console config, no way to make : 
X :2   or xinit -- :2
There is apparently no solution in Ubuntu. The bug was introduced from Breezy to Dapper, and that will stay. 
It s like the bug too with metacity that was never corrected. 

Certainly Debian, since it has better image, could have that done. 

Concerning Edgy, quite few debs were not well made, and libs are missing. For me, that is important. I use linux, when upgrade to newer distro, I dont want to build my packages myself with checkinstall;.... i have other things to do, .... Sun shining ... soo, why loosing time with remaking work that hasnt been well verified ... At every new distro release, if everbd has to remake its debs by its own .... anyhow ... 
 
I will try today the Famous Debian

Patrick
Ubuntu Lover

---

### Post by patrick295767 on 2006-12-23
> **zugu said:**
> Hello everyone.

I'm thinking more and more of switching my desktop from Ubuntu 6.06 to Debian. Here are the reasons I want to leave Ubuntu:

- important applications, such as VLC, Firefox, GAIM etc. do not receive backports for the 6.06 release
- I want to try something new
- I don't like the Ubuntu "habit" of including beta software in the official releases
- I need a stable desktop

What I don't know if Debian can offer me, nevertheless I want from it:

- a more stable desktop;
- backports and updates for the important applications;
- no beta software in the official releases;
- easy installation of the nVidia legacy drivers and other proprietary packages (if it's just as easy as in Ubuntu, then it's OK with me)
- more control over what packages to install in the installer;

So, is Debian for me? I've been using Ubuntu for almost a year, and I'm already familiar with the apt system and the GNOME desktop environment. Will I survive in a Debian world?

Me too, lack of stability & uncorrected bugs, ... I am trying Debian ! 

it is said : nothg better for stability    for debian-based
Finally, the wise jump I guess. Stability of OS is sthg important

---

### Post by 23meg on 2006-12-23
> 
I am having troubles wiht
Xwrapper.config
from user, as console config, no way to make :
X :2 or xinit -- :2
There is apparently no solution in Ubuntu. The bug was introduced from Breezy to Dapper, and that will stay.
It s like the bug too with metacity that was never corrected.Is this bug reported elsewhere, or can you go into more detail of what exactly it prevents you from doing?> Certainly Debian, since it has better image, could have that done. In almost all cases, if something is fixed in Debian, it will also be fixed in Ubuntu in the next release, since Ubuntu takes from Debian.> 
Concerning Edgy, quite few debs were not well made, and libs are missing. Which ones?

---

### Post by mips on 2006-12-23
> **23meg said:**
> Is this bug reported elsewhere, or can you go into more detail of what exactly it prevents you from doing?In almost all cases, if something is fixed in Debian, it will also be fixed in Ubuntu in the next release, since Ubuntu takes from Debian.Which ones?

I always thought Ubuntu takes from Sid to get the latest stuff, so if sid has bugs ubuntu will have bugs.

---

### Post by patrick295767 on 2006-12-23
Fresh News from the Installation !!!  I just installed debian, mozilla and gnome.

Finally, I can have a working LINUX !! 
I already Love this Debian box, for that.
 
 
try from user from dapper or edgy :
startx -- :2.0
and let me know if it works ... 
  Me yes !! 
  
  
The idea is that I am having on :6  a Ekiga phone running
 
  
The only thing is that the basic repositories are bit smaller... not so much are in it as for Ubuntu
  XFREE86 is replacing XORG
I like to xfree86, but I am still dont know if COMPOSITE is possible with it;
anyhow I can make deb for Xorg later
 
Stable & Finalized OS was really a necessity for me.
  
To be continued with Debian EXPERIENCE ...

---

### Post by RAV TUX on 2006-12-23
moving to Debian forum

---

### Post by xabbott on 2006-12-24
> **mips said:**
> I always thought Ubuntu takes from Sid to get the latest stuff, so if sid has bugs ubuntu will have bugs.

They don't just take them from Sid and punch out a new release. They do patch them and do security updates, etc. These patches also get sent back to Debian.

---

### Post by xabbott on 2006-12-24
If you plan on using Debian right now I recommend going with Etch. It will become the new stable soon.

---

### Post by mips on 2006-12-24
> **xabbott said:**
> They don't just take them from Sid and punch out a new release. They do patch them and do security updates, etc. These patches also get sent back to Debian.

Fair enough but a few still slip by.

---

### Post by patrick295767 on 2006-12-24
> **RAV TUX said:**
> moving to Debian forum

Thanks, 
I saw afterwards...

---

### Post by xabbott on 2006-12-24
> **mips said:**
> Fair enough but a few still slip by.

Just like a few slip by from unstable, to testing, to "stable." Does it happen often? No. Just that the whole point is moot. I don't feel Etch is more or less stable than Ubuntu. And Sid def isn't as stable as a release.

---

### Post by patrick295767 on 2006-12-24
Hi, 

With time, I needed a linux very stable & I tried (again after some time ) : 
  
_Debian Sarge:_
            This is very very impressive. This release is even more stable than my previous Mac Os X.
             The firefox, quite old 1.0.4, is not buggy at all !  You can surf in total security of crashes.
             Some packages are still not present, but if you need just minimum non brand new apps.
             No problems with debs, no bugs around ... aterm fonts even are fixed with mc 
             I did not have anythg crashing.
  
[U]
Debian Etch:[/U]
             They call it testing, and there is not everythg fully working

_Debian Sid:_
             Didnt try.
 
(kind of less repos than Ubuntu)
  
[B]
Debian & Stability = ROCKS ![/B]
  
  
--
I did not choose Dapper just for its bug of Xwrapper.config still remaining
And I like the stability concept of Debian 
[http://debian.org](http://debian.org)
[http://www.debian.org/releases/](http://www.debian.org/releases/)
& I have folks around still loving this distro
...

---

### Post by jdhore on 2006-12-24
> **patrick295767 said:**
> Hi, 

With time, I needed a linux very stable & I tried (again after some time ) : 
  
_Debian Sarge:_
            This is very very impressive. This release is even more stable than my previous Mac Os X.
             The firefox, quite old 1.0.4, is not buggy at all !  You can surf in total security of crashes.
             Some packages are still not present, but if you need just minimum non brand new apps.
             No problems with debs, no bugs around ... aterm fonts even are fixed with mc 
             I did not have anythg crashing.
  
[U]
Debian Etch:[/U]
             They call it testing, and there is not everythg fully working

_Debian Sid:_
             Didnt try.
 
(kind of less repos than Ubuntu)
  
[B]
Debian & Stability = ROCKS ![/B]
  
  
--
I did not choose Dapper just for its bug of Xwrapper.config still remaining
And I like the stability concept of Debian 
[http://debian.org](http://debian.org)
[http://www.debian.org/releases/](http://www.debian.org/releases/)
& I have folks around still loving this distro
...

heh...you want to see a REALLY stable distro?

check out FreeBSD...i run it on my home everything server (file server, media server, SSH "shell", HTTP server, AND FTP server) and my current uptime is almost 6 months...about 167 days

---

### Post by burek on 2006-12-24
bsd stories: [http://www.oreillynet.com/sysadmin/blog/2004/05/bsd_success_stories_1.html](http://www.oreillynet.com/sysadmin/blog/2004/05/bsd_success_stories_1.html)
they say that it is the best

---

### Post by tbroderick on 2006-12-24
> **zugu said:**
> This is unfortunate, the thing I hate most is being stuck with old versions of the software. Why is that? Isn't there a solution for people to have a stable system AND update important software as-you-go?


Have you tried Zenwalk or Slackware?

---

### Post by patrick295767 on 2006-12-25
> **xabbott said:**
> If you plan on using Debian right now I recommend going with Etch. It will become the new stable soon.

Would you have wise sources.list for a apt-get dist-upgrade ? (sarge to etch)
I am not quite pleased with mine etch sources.list ... 

thanks !!

besides: [http://www.debian.org/releases/testing/](http://www.debian.org/releases/testing/)
there is still some bugs ... ar e they gonna correct them ? [http://bugs.qa.debian.org/cgi-bin/standard.cgi](http://bugs.qa.debian.org/cgi-bin/standard.cgi)

have you etch ? If yes, can you from /dev/tty1    do from user :    xinit -- :3
is this corrected in Etch ?
try in ubuntu, bug still there ...

---

### Post by dbbolton on 2006-12-26
i'm thinking about giving it a try myself.

---

### Post by dbbolton on 2006-12-26
hmm. i hope these downloads finish soon.

---

### Post by patrick295767 on 2006-12-26
> **dbbolton said:**
> i'm thinking about giving it a try myself.

The sarge has 2.4 kernel 
which means that you cannot do everythg with tvtime & alsa ...

---

### Post by patrick295767 on 2006-12-26
I am still very very impressed by Debian

I love it since all bugs of Edgy & Dapper are not there

This Debian distro is highly stable, reliable, and you can be confident that your OS will work !

It isnt more difficult than Ubuntu, ... Debian is the mother of Ubuntu. They are rather identical but one is less buggy.

---

### Post by plb on 2006-12-28
I just tried the daily build and the gui installer is awesome. The desktop is great too.

---

### Post by neowolf on 2006-12-28
> **plb said:**
> I just tried the daily build and the gui installer is awesome. The desktop is great too.

Etch does rock, shame about the whole Mozilla argument though.

---

### Post by mips on 2006-12-28
> **neowolf said:**
> Etch does rock, shame about the whole Mozilla argument though.

Who actually gives a toss about the name ? Makes no difference in my life.

---

### Post by BarfBag on 2006-12-28
I'm beginning to think that the direction Ubuntu is going in isn't for me.  I can't believe I'm saying this, but it's getting too easy to use!  That's good for some users, but for geeks with too much time on their hands (like me), it creates pure boredom.  I'm probably going to switch to Debian when Etch becomes stable (unless the question after this one turns out to be true), but don't want to be stuck where I am now in the near future.  What direction is Debian going in?  Is it trying to balance itself out for both the geek and the newbie, or is it trying to compete with Ubuntu?

Now I have a question about the stable and testing versions.  With Etch soon going stable, I'm not going to install the current version (I believe it's 3.1).  I'd like to get this show on the road as soon as possible, though.  If I install the testing version of Etch, will I be able to upgrade (with software update) the packages to the ones in stable Etch when it comes out?  I don't feel like going through installing and configuring it twice.

Last question.  What repositories do you guys recommend I add?  The only one I'm interested in at the moment is the Debian Multimedia one (which I used in Simply Mepis).  Could you guys give me the link and keys for that one?  I completely forgot where it is.

That's all for now.  I'll probably have more questions after I go through with this.  Thanks!

Edit - a few more popped up in my mind.  First off, is there any difference in code between Debian and Ubuntu?  What in particular makes Debian so stable, besides the more bug-free packages?

Can I have it install a KDE desktop during installation, or do I have to do it manually afterwards?

Thanks again.  This post might receive a few more edits.  :-P

---

### Post by xabbott on 2006-12-28
> **BarfBag said:**
> I'm beginning to think that the direction Ubuntu is going in isn't for me.  I can't believe I'm saying this, but it's getting too easy to use!  That's good for some users, but for geeks with too much time on their hands (like me), it creates pure boredom.  
If you feel this way Etch will probably bore you too. Ubuntu and Etch are very similar.

> **BarfBag said:**
> 
I'm probably going to switch to Debian when Etch becomes stable (unless the question after this one turns out to be true), but don't want to be stuck where I am now in the near future.  What direction is Debian going in?  Is it trying to balance itself out for both the geek and the newbie, or is it trying to compete with Ubuntu?
As far as I know Debian's main goal is stability and quality. This doesn't say much about geek vs newbie. But like I said, right now it's a very newbie friendly distro imo. If you want to "geek out" on a distro I recommend ArchLinux, Slackware, or Gentoo.

> **BarfBag said:**
> 
Now I have a question about the stable and testing versions.  With Etch soon going stable, I'm not going to install the current version (I believe it's 3.1).  I'd like to get this show on the road as soon as possible, though.  If I install the testing version of Etch, will I be able to upgrade (with software update) the packages to the ones in stable Etch when it comes out?  I don't feel like going through installing and configuring it twice.

If you install Etch right now all you have to do is leave "etch" in your sources. Then it will always remain Etch. From test to stable you will be using Etch. I've been using Etch for awhile (mixed with unstable) and it's solid.
 
> **BarfBag said:**
> 
Last question.  What repositories do you guys recommend I add?  The only one I'm interested in at the moment is the Debian Multimedia one (which I used in Simply Mepis).  Could you guys give me the link and keys for that one?  I completely forgot where it is.


```
deb http://www.debian-multimedia.org etch main
```

> **BarfBag said:**
> 
That's all for now.  I'll probably have more questions after I go through with this.  Thanks!

Edit - a few more popped up in my mind.  First off, is there any difference in code between Debian and Ubuntu?  What in particular makes Debian so stable, besides the more bug-free packages?

Can I have it install a KDE desktop during installation, or do I have to do it manually afterwards?

Thanks again.  This post might receive a few more edits.  :-P

There are a lot of little things different between Debian and Ubuntu. From a desktop's user pov I would say it'd be hard to notice. As for stability Debian typically doesn't use bleeding edge stuff, does a lot of testing, etc. 

If you want KDE instead of Gnome use the following image
[http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-kde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-kde-CD-1.iso)

If you've downloaded a weekly net install then you can use
```
install tasks=kde-desktop
```

---

### Post by xabbott on 2006-12-28
> **mips said:**
> Who actually gives a toss about the name ? Makes no difference in my life.
Well I care because all this fuss was made and what browser is included in Etch?! **FIREFOX 1.5**,

---

### Post by plb on 2006-12-28
just download firefox from mozilla and use it...that is what I always do anyway...just be sure to apt-get install libstdc++5

---

### Post by patrickfromspain on 2006-12-28
Hi there!!

As in debian we don't get free shipped cds, I've done (some friends helped me, too) some work in the artwork.. hope you like it and/or find them usefull.

---

### Post by xabbott on 2006-12-28
> **plb said:**
> just download firefox from mozilla and use it...that is what I always do anyway...just be sure to apt-get install libstdc++5

I just got it from unstable.

---

### Post by patrickfromspain on 2006-12-28
I jumped into etch to try it.. and have stayed.. I love it :D

---

### Post by pay on 2006-12-28
Thats really nice. Thanks.

---

### Post by dakini on 2006-12-28
Nice, Patrick.  Thank you.

---

### Post by mykalreborn on 2006-12-29
i was jsut wandering, since debian is one of the oldest deistributions around, and from what i have seen one of the biggest, why have they only reached version 3?

ps:please don't bother telling me how silly this question is. just answer

---

### Post by jdhore on 2006-12-29
It's because Debian tests the hell out of everything, all their software, all their packages...everything...like Dell, so they test it and the packages may be semi-old, but they're stable as hell...so it takes a while to get out...if you're comparing it to Ubuntu being on 6.10 or 7.04, remember, Ubuntu STARTED at 4.10, also i think Ubuntu is based on the Unstable version of Debian...ALSO, on most of the Debian versions, they've gone to 3.1, 3.2, 3.2r2, etc. and sometimes with Ubuntu there's only 1 version under a full number or only 2 versions under a full number (4.10 and 6.06/6.10 respectively)

---

### Post by tturrisi on 2006-12-29
It's not a stupid question!  (there are only stupid answers)
All you ever wanted to know about Debian is here:
[http://www.debian.org/doc/FAQ/](http://www.debian.org/doc/FAQ/)

---

### Post by plb on 2006-12-29
Etch will be 4.0 :-D And yes Debian takes a while to get out because of all the testing that is done. That is the reason Debian is so stable, they release when it's ready...there is no deadline.

---

### Post by neowolf on 2006-12-29
Debian take their time and do thing **very** thoroughly, plus they exhaustively test all their packages to an almost bug-free state. While distro's like SUSE/Mandriva go up to version 9 and beyond often a point jump from say 9.1 to 9.2 is just updated packages and a few minor features while from Debian 3.1 to the upcoming 4.0 they've added tons of new stuff like SecureAPT, Multi-Arch support, Offical AMD64 port and LSB 3.1 compliance.

---

### Post by matthew on 2006-12-29
> **jdhore said:**
> if you're comparing it to Ubuntu being on 6.10 or 7.04, remember, Ubuntu STARTED at 4.10
...
and sometimes with Ubuntu there's only 1 version under a full number or only 2 versions under a full number (4.10 and 6.06/6.10 respectively)I'm off topic here, but FYI...especially since the original question has been answered quite well.

The Ubuntu version numbers work differently. The first number is from the year and the second the month of the release.

4.10 released October 2004
5.04 released April 2005
5.10 released October 2005
6.06 was delayed and released June 2006
6.10 got back on the April/October schedule and came out October 2006
7.04 is scheduled for release April 2007

and so on

---

### Post by mykalreborn on 2006-12-29
i allways felt i was in good hands when i downloaded ubuntu and 64studio - debian based. :D

---

### Post by unisol on 2006-12-30
ihave  ap3 384 mb mem 80 gb hd nvidia geforce fx 5500 video card. my question is can you install 3d acceleration in etch? i have done it with ubuntu no problem.

---

### Post by patrickfromspain on 2006-12-30
I have installed the latest nvidia drivers from [www.nvidia.com](www.nvidia.com) with little problems.. You can.

---

### Post by maxamillion on 2006-12-30
etch offers the nvidia-glx binary package just like ubuntu does ... [http://packages.debian.org/testing/x11/nvidia-glx](http://packages.debian.org/testing/x11/nvidia-glx)

```
su
aptitude install nvidia-glx
```

then edit your xorg.conf ... same system, same task :)

---

### Post by ahaslam on 2006-12-30
I had a few problems using this weeks build. I had no processor scalling, got warnings when using opengl & the gnome panels were supprisingly buggy. I have not experienced any crashes, but pleanty of glitches. 

Tony.

---

### Post by Lucho on 2007-01-08
I'm probably reviving an old thread, but every time somebody talks about
bugginess in an Etch build, the bugs that are mentioned are gnome-related.
A connection, perhaps?

---

### Post by gholen on 2007-02-09
Well, there are some bugs, that I am aware abaout, I just swithed BACK to Debian on my laptop, because I wanted a more stable thing then Edgy och even dapper could give me.

The main problem with Etch is that Etch is still usin an old GNOME release, but thats good too, because then its tested for quite some time.
The best thing is that GNOME in etch is, to the differense från ubuntu 5.10, stable, in tha way that it does not crash.

---

### Post by ahaslam on 2007-02-11
According to Distrowatch, Etch now has Gnome 2.16. I thought the plan was for it to be available in backports, maybe 2.14 just had too many problems? I'm looking forward to the final release ;)

Tony.

PS. What do you guys go for: netinstall, 1cd, 2-3cd's, dvd, etc?
I'm torn between the 1st cd & the netinstall disc, wanting to keep bloat to a minimum.

---

### Post by Kateikyoushi on 2007-02-12
I got the DVD not that I really want to make a heavy system but at least can se the disc for other installs.

---

### Post by AgenT on 2007-02-12
> **Anthony Haslam said:**
> According to Distrowatch, Etch now has Gnome 2.16. I thought the plan was for it to be available in backports, maybe 2.14 just had too many problems? I'm looking forward to the final release ;)
Distrowatch is not a reliable source for anything, including news and distribution popularity. Debian Etch will have GNOME 2.14 because 2.16 is very buggy. Check out the official GNOME bugzilla and you will see the critical bugs that it still has after all these months. KDE is only 0.0.1 version behind because the newest version was released a little over 1 week ago and Etch is frozen.

> PS. What do you guys go for: netinstall, 1cd, 2-3cd's, dvd, etc?
I'm torn between the 1st cd & the netinstall disc, wanting to keep bloat to a minimum.Just do a netinstall as it will save you time in the long run unless you expect to do a reinstall after you have your new system up. Remember, all you will need to download is a 150MB iso and then only the packages that you need. With a full 1 CD disk you will 1) download a 650MB iso 1) re-download most packages that the CD has anyway just because newer updated versions will be available. If you choose to install KDE desktop instead of GNOME, you will need to use the daily build netinstall image as this is a new task option. Of course, you can always install KDE yourself but the task option has many benefits such as installing other, non-KDE packages (such as sound and printer support) that are very useful for desktop systems. Press F8 in the CD boot menu for more information on how to start a KDE desktop install.

For Debian questions and answers it is best to use a Debian forum like [forums.debian.net]("http://forums.debian.net")

Linux.com has an interesting article on [Debian and the upcomming release]("http://www.linux.com/article.pl?sid=06/11/21/1552223").

---

### Post by Kateikyoushi on 2007-02-12
The last paragraph was interesting in light that Etch won't be out at least till March.

---

