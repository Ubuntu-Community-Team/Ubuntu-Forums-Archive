---
title: "Why does it have to be SO difficult?"
date: 2006-01-08
forum: General Help
---

### Post by ptmurphy on 2006-01-08
I have been using various flavors of Linux for a while (maybe about two years, Suse and Ubuntu mostly) to setup a web server, MySQL, PHP, Samba, etc.  I like it and enjoy tinkering and figuring things out, but I am a computer nerd.

I would like to share the virus and spyware free experience with my friends and family, but some things are just too difficult for the average home user, in my opinion.  Examples of things that I normally have to do over the course of a Linux install that I don't think my average friend would (or maybe could) do...

1. Get nVidia drivers working properly for 3D graphics
2. Enable DMA for CD/DVD Drives
3. Install MP3 Codecs
4. Install DVD Codecs
5. Get a CSS program working to view DVDs
6. Install and configure Samba for network sharing
7. Re-mapping of keys for shortcuts
8. Get a wireless network card working
9. Any hardware setup problem (keyboard, mouse, CD, etc. not working)

I understand some of the issues (3-5) are a byproduct of having a free operating sytsem, but getting new hardware installed and working properly and getting some programs setup and working seem overly difficult.

I cannot imagine my mom and dad trying to setup and use Linux, or even most of my friends.  It takes a lot of patience and a knack for learning technical things.

As an example, the last time I tried to install nVidia drivers, I totally messed up my xorg.conf.  How many people on here have parents or friends that could have or would have taken the time to figure out how to get X back up and running when confronted with a login: prompt at a black and white screen.

Just curious if anyone else feels the same way and how this can be remedies?

Thanks...

---

### Post by spacetime on 2006-01-08
About the xorg.conf issue... I just installed the latest NVidia drivers and they now come with an automatic xorg.conf editor, presumably based on sed or similar. The rest:

1. Moan at NVidia, not Ubuntu.
2. Most CD/DVD drives I have found have DMA working out-of-the-box on Ubuntu... if my experience is unusual, please let me know.
3-5. Yes, it is a problem. However Automatix provides a relatively easy way to install them (and much more besides). How different is that to having to install SP2 on Windows?
6. I agree, Ubuntu should maybe include Samba by default, and GUI config tools. This is probably my only gripe with Ubuntu... hardly any graphical config tools and no graphical installer, and a not-that-nice looking bootsplash.
7. Again, perhaps something that should be included... although for most things, System->Preferences->Keyboard Shortcuts.
8. NDISWrapper and NDIS-GTK. Use Windows wireless drivers. Problem solved.
9. Most hardware that isn't supported is due to NDAs or similar.

Hope that clears things up a bit... ;) although I do agree Ubuntu, and Linux in general, isn't *quite* as user-friendly as it might be.

---

### Post by skaboss on 2006-01-08
You are definitely not the only one to feel linux, even with it's user friendliest distro (Ubuntu of course ! ;-) ) isn't ready for average users.
But i don't think it's really a problem. Of course, if you want to escape from winjail, you will have to  learn lot of various things about your new OS, some networking, some hardware and so on. I personally find this an exciting experience and i love it. But for sure my hairdresser or my grandpa won't.... So they will stay with you know who. And when they have a problem, they will call their computer's reseller hotline, who will tell them to format and reinstall winblows.
I think the problem doesn't rely on a specific OS, but simply on the computers themselves : even though everybody and their dog have a computer today, computers still aren't ready for average users.
Maybe the solution comes from Apple, and their really user friendly computers...

---

### Post by ptmurphy on 2006-01-08
[QUOTE=spacetime]
2. Most CD/DVD drives I have found have DMA working out-of-the-box on Ubuntu... if my experience is unusual, please let me know.
[/QUOTE]

My latest ubuntu install did not recognize either of my DVD drives as being DMA capable.

One is a Sony DVD+-RW and the other is a Lite-on DVD Rom.

---

### Post by michaelb on 2006-01-08
I actually have had the same thoughts, ptmurphy. As easy as Ubuntu is to install and set up, it must be remembered that a good portion of computer users couldn't even tell you what operating system they are using (Windows), let alone which one is the best. Firefox is easy to install and understand, and thus enjoys widespread popularity. If every computer had both Windows XP and Linux installed on it as duel boot, I wonder which one would become most popular among the non-computer savvy. I know if they gave them both a chance, Linux would grow on them, but just the fact that the word "Terminal" appears on their applications menu may be enough to scare them away ("Terminal? Ai! Does that mean my computer's dieing??"). 90% of people are "mouse people". It's really a tough call if you think about it: WinXP is "good enough" for most people and it does everything automatically, even though it may be doing it the wrong way. While Linux may be more stable and secure etc., the average user worries about two things: writing letters, playing games, and browsing the web looking for cheap laughs. WinXP sings to them and gives them dancing paper-clips when they write letters, thus it must be "easier". There of course is a striking lack of games for Linux, and, as for the last item, Linux doesn't support AOL, so it must be inferior in that respect.

Bah, I'm getting too philosophical. At any rate, I'm still trying to convince my friends to give Ubuntu a try.

I'd love to see a Linux that doesn't try to do it the right way necessarily, it just tries to be better, faster, come with WINE, and *easier*, even easier than Windows. Links isn't as popular as Firefox on Windows for a very simple reason (I don't think I need to explain). I'm not saying I'd like to see Ubuntu *replaced* with a user-friendly Linux. I'd just like to see another fork. Maybe "Duh!buntu: Linux for Human Beans". Or maybe not. ;)

---

### Post by linuxishard on 2006-01-08
[QUOTE=ptmurphy]I have been using various flavors of Linux for a while (maybe about two years, Suse and Ubuntu mostly) to setup a web server, MySQL, PHP, Samba, etc.  I like it and enjoy tinkering and figuring things out, but I am a computer nerd.

I would like to share the virus and spyware free experience with my friends and family, but some things are just too difficult for the average home user, in my opinion.  Examples of things that I normally have to do over the course of a Linux install that I don't think my average friend would (or maybe could) do...

1. Get nVidia drivers working properly for 3D graphics
2. Enable DMA for CD/DVD Drives
3. Install MP3 Codecs
4. Install DVD Codecs
5. Get a CSS program working to view DVDs
6. Install and configure Samba for network sharing
7. Re-mapping of keys for shortcuts
8. Get a wireless network card working
9. Any hardware setup problem (keyboard, mouse, CD, etc. not working)

I understand some of the issues (3-5) are a byproduct of having a free operating sytsem, but getting new hardware installed and working properly and getting some programs setup and working seem overly difficult.

I cannot imagine my mom and dad trying to setup and use Linux, or even most of my friends.  It takes a lot of patience and a knack for learning technical things.

As an example, the last time I tried to install nVidia drivers, I totally messed up my xorg.conf.  How many people on here have parents or friends that could have or would have taken the time to figure out how to get X back up and running when confronted with a login: prompt at a black and white screen.

Just curious if anyone else feels the same way and how this can be remedies?

Thanks...[/QUOTE]




I DO... i dont know anything about linux realy... but i do know that i hate windows... so therefore i chose to ditch it and take UBUNTU but this is like learning how to walk... all over again.. 

i had problems from the start, that basicly, without the help of experianced LINUX users i would still be stuck with now...... And even then im still stuck now and i can get any of the help i need ither...... ALL I WANNA KNOW IS HOW TO SETUP MY INTERNET CONECTION....... but  no...i think EVERY SINGLE install disc i ordered is faulty... cos thats the only thing that seems to explain the problems im having..... PLEASE HELP ME

---

### Post by aysiu on 2006-01-08
[QUOTE=skaboss]You are definitely not the only one to feel linux, even with it's user friendliest distro (Ubuntu of course ! ;-) ) isn't ready for average users.[/QUOTE] Mepis, PCLinuxOS, and Linspire are far more user-friendly, especially for absolute newbies to Linux.

That said, if you have Automatix, Ubuntu's not "so difficult" after all.

---

### Post by audax321 on 2006-01-08
Personally, IF all your hardware is supported I think Linux is very user-friendly. The only thing I see as a usability problem is the lack of GUIs and the need to edit configuration files. It would be nice if users had the option of either using a GUI or editting files manually.

1. Get nVidia drivers working properly for 3D graphics
[INDENT]Never really had a problem here if using the prepackaged Ubuntu drivers... although I agree the official ones can be intimidating for new users... and again... editting xorg.conf is scary for new users.[/INDENT]
2. Enable DMA for CD/DVD Drives
[INDENT]Agreed.. most people don't know what DMA is! Although its not difficult to enable this by editting a file, a GUI would make it much easier for new users.[/INDENT]
3. Install MP3 Codecs
4. Install DVD Codecs
[INDENT]I don't agree with this. Although MP3s and DVDs work for the most part in Windows, have you ever tried installing a Codec pack in Windows? I installed the Kazaa Codec Pack once to play a video and a few of the codecs it installed actually conflicted with others. Luckily my brother was able to help me because he had fixed the problem before... but still, apt-geting a few codecs from universe or PLF is a lot easier in my opinion than finding obscure codec packs. And wait until MS goes all crazy with this DRM garbage...[/INDENT]
5. Get a CSS program working to view DVDs
[INDENT]Not sure about this because libdvdcss2 worked fine for me on all of the computers I've installed Ubuntu on.[/INDENT]
6. Install and configure Samba for network sharing
[INDENT]Actually forget installing and configuring Samba, I hate it. What I did was install  openssh and then access the files either by using 'Connect to server' iin Linux or installing WinSCP3 in Windows. As far as printing I installed my printer using CUPS and I can even print over the internet, so if my sister wants to fax me something she just scans it and prints it to my printer 3,000 miles away![/INDENT]
7. Re-mapping of keys for shortcuts
[INDENT]Difficult for the new user because its hard to edit the xbindkeys config file and use xev... again too much console reliance... it'd be cool if there was a GUI available for this... I used one for xbindkeys a while back but it was really buggy for me. And I think there is much more flexibility in mapping keys in Linux vs. Windows. For one, its not driver dependent and you can do key events on windows, mouse events, as well as just binds to launch apps.[/INDENT]
8. Get a wireless network card working
[INDENT]This is more of a driver issue. People need to start an email campaign to promote Linux with manufacturers like netgear, d-link, etc. Only then will drivers for these devices ever come out. Using ndiswrapper (althouhg it is a nice tool) is not helping Linux... its just using drivers developed for Windows.[/INDENT]
9. Any hardware setup problem (keyboard, mouse, CD, etc. not working)
[INDENT]Again, driver issues and config file problems.[/INDENT]

---

### Post by aysiu on 2006-01-08
[QUOTE=audax321]Personally, IF all your hardware is supported I think Linux is very user-friendly. The only thing I see as a usability problem is the lack of GUIs and the need to edit configuration files. It would be nice if users had the option of either using a GUI or editting files manually.[/QUOTE] They do in *Linux*, just not in *Ubuntu*.

---

### Post by bikeboy on 2006-01-08
The average user isn't the one installing Windows either. They would just as likely have trouble setting it up as they would with Ubuntu.

I don't see the average user configuring a complex network etc on Windows. Things like DMA detection will get better with time. But right now I think Ubuntu is easier to install/setup than Windows because it comes with almost everything the average user would need. What it doesn't have...wiki if you're a geek, automatix if you're not.

---

### Post by qferret on 2006-01-08
[QUOTE=bikeboy]The average user isn't the one installing Windows either. They would just as likely have trouble setting it up as they would with Ubuntu.
[/QUOTE]

Good point!

Synaptic is the best thing since sliced bread IMO.
Searching shareware & freeware sites to find a simple utility or program...bah
keyword search, check a box, click apply....

It doesn't get any easier, as long as you don't run into conflicting dependencies.
(I haven't had much of that lately...was pretty common around the GTK/GTK2 gcc3/gcc4 switches though)

---

### Post by aysiu on 2006-01-08
[QUOTE=qferret]
Synaptic is the best thing since sliced bread IMO.
Searching shareware & freeware sites to find a simple utility or program...bah
keyword search, check a box, click apply....[/QUOTE] As long as the package is in the repositories, it's a much simpler process. I *hated* digging around the internet, searching download.com and other sites, trying to avoid sketchy spyware and adware. Synaptic makes it simple--a centralized location for applications.

---

### Post by jomurmiranda on 2006-01-09
[QUOTE=audax321]Personally, IF all your hardware is supported I think Linux is very user-friendly. The only thing I see as a usability problem is the lack of GUIs and the need to edit configuration files. It would be nice if users had the option of either using a GUI or editting files manually.

1. Get nVidia drivers working properly for 3D graphics
[INDENT]Never really had a problem here if using the prepackaged Ubuntu drivers... although I agree the official ones can be intimidating for new users... and again... editting xorg.conf is scary for new users.[/INDENT]
2. Enable DMA for CD/DVD Drives
[INDENT]Agreed.. most people don't know what DMA is! Although its not difficult to enable this by editting a file, a GUI would make it much easier for new users.[/INDENT]
3. Install MP3 Codecs
4. Install DVD Codecs
[INDENT]I don't agree with this. Although MP3s and DVDs work for the most part in Windows, have you ever tried installing a Codec pack in Windows? I installed the Kazaa Codec Pack once to play a video and a few of the codecs it installed actually conflicted with others. Luckily my brother was able to help me because he had fixed the problem before... but still, apt-geting a few codecs from universe or PLF is a lot easier in my opinion than finding obscure codec packs. And wait until MS goes all crazy with this DRM garbage...[/INDENT]
5. Get a CSS program working to view DVDs
[INDENT]Not sure about this because libdvdcss2 worked fine for me on all of the computers I've installed Ubuntu on.[/INDENT]
6. Install and configure Samba for network sharing
[INDENT]Actually forget installing and configuring Samba, I hate it. What I did was install  openssh and then access the files either by using 'Connect to server' iin Linux or installing WinSCP3 in Windows. As far as printing I installed my printer using CUPS and I can even print over the internet, so if my sister wants to fax me something she just scans it and prints it to my printer 3,000 miles away![/INDENT]
7. Re-mapping of keys for shortcuts
[INDENT]Difficult for the new user because its hard to edit the xbindkeys config file and use xev... again too much console reliance... it'd be cool if there was a GUI available for this... I used one for xbindkeys a while back but it was really buggy for me. And I think there is much more flexibility in mapping keys in Linux vs. Windows. For one, its not driver dependent and you can do key events on windows, mouse events, as well as just binds to launch apps.[/INDENT]
8. Get a wireless network card working
[INDENT]This is more of a driver issue. People need to start an email campaign to promote Linux with manufacturers like netgear, d-link, etc. Only then will drivers for these devices ever come out. Using ndiswrapper (althouhg it is a nice tool) is not helping Linux... its just using drivers developed for Windows.[/INDENT]
9. Any hardware setup problem (keyboard, mouse, CD, etc. not working)
[INDENT]Again, driver issues and config file problems.[/INDENT][/QUOTE]

I would agree, except that many times there are solutions for many driver problems that just entail downloading, typing and compiling. I believe that many of these problems respond to: 1. The people that know the stuff just don't think it's hard, and 2. the people that know would rather work on "real" problems, not just making Ubuntu easier to use. I guess I'm more concerned about this now because I feel Ubuntu could sooo easily be better than Windows. It's *this* close...

Oscar

---

### Post by enderv on 2006-01-09
[QUOTE=bikeboy]The average user isn't the one installing Windows either. They would just as likely have trouble setting it up as they would with Ubuntu.
[/QUOTE]
I beg to differ. I can install XP on my PC within two hours running, with the Wifi and most of things I wanted (Firefox, OpenOffice etc..), but I spent last three days to get Ubuntu running properly (and it's still not - I still can't figure out why ndiswrapper looks ok, but I get no wireless interface, and yes, it has been installed as a kernel module - but your average joe user would hgave no clue what kernel is!). 
None of the readmes/wikis provided a solution to my graphic card problems (and I don't think ATI 800XL is such a strange card...).

So we're not talking about things like setting a corporate network, or even home network, but stuff like getting the desktop run! 

So, from ease-of-installation I think Linux has still some way to go - although admitedly it is already much, much better than about 5 years ago when I looked at Linux at desktop last time. (I was rather pleased when my printer worked out of box in Ubuntu)

Closing one's eyes to it won't help it though. Nor will the "so fix it yourself" attitude - if you want more people to pick it up and start using it.

V.

---

### Post by johna11en on 2006-01-09
[QUOTE=ptmurphy]
Examples of things that I normally have to do over the course of a Linux install that I don't think my average friend would (or maybe could) do...

1. Get nVidia drivers working properly for 3D graphics
2. Enable DMA for CD/DVD Drives
3. Install MP3 Codecs
4. Install DVD Codecs
5. Get a CSS program working to view DVDs
6. Install and configure Samba for network sharing
7. Re-mapping of keys for shortcuts
8. Get a wireless network card working
9. Any hardware setup problem (keyboard, mouse, CD, etc. not working)

I understand some of the issues (3-5) are a byproduct of having a free operating sytsem, but getting new hardware installed and working properly and getting some programs setup and working seem overly difficult.
[/Quote]

1/2/3/4/5 can be fixed/installed easily using Automatix.  6 would never really be done from a average computer user.  Samba could be easier to use.  8/9. Depends on the hardware you have.  I'm sure you know this already.  Just think that in Windows not everything works either.  You are required to have drivers from the OEM.

> 
I cannot imagine my mom and dad trying to setup and use Linux, or even most of my friends.  It takes a lot of patience and a knack for learning technical things.


I think everyone needs to be patient with Linux.  It has improved so much in the last 10 years.  In the next 10 years any computer savvy person (knowing the basics) should be able to install it and use it.  

There is an entire breed of computer user out there who refuses to learn anything about computers or how to properly use them.  Those people will never adapt no matter how easy you make it.

---

### Post by handy on 2006-01-09
Some hardware config's are more compatible than others.  You see people on this forum with tons of troubles, that others know nothing about because they are on a different machine.

Windoze has an obvious advantage there, having been in the market place for years, having developed relationships with all it's partners, one way or another...  It has drivers & hardware support comming out of it's ears!

That's a tough problem for the Linux community to solve!  

But it is being solved, many of us have NO prob's at all with our installations.  :KS  

Synaptic, Automatix & the right hardware to start with, then you find that only the following items:

6. Samba 

7. Re-mapping of keys for shortcuts

8. Get a wireless network card working

Are a problem, & then, only for those that they are a problem for. :rolleyes: 




**There are major dark political moves that M$ is VERY much involved in, see here:**

[http://www.cl.cam.ac.uk/~rja14/tcpa-faq.html](http://www.cl.cam.ac.uk/~rja14/tcpa-faq.html)
 
handy

---

### Post by ptmurphy on 2006-01-09
Everyone has made a lot of good comments and suggestions.

The problem I have is that my friends and family tend to be fairly adventurous due to the fact that they have me as a backup.  If something goes wrong, well my phone starts a-ringing!

---

### Post by nocturn on 2006-01-09
I agree with the former post, most end-users are not capable of installing their own OS and required programs.  At least at the end of an Ubuntu install, you have a working computer with applications.  Windows XP will offer you notepad and a calculator. 

Most end users are not installing their own systems, and are incapable of installing maintaining the anti-virus and firewall software so desperately needed in that commercial OS.

For a fair comparison between OS's, you should compare a preinstalled Ubuntu system with a preinstalled Windows system.

---

### Post by Snooz on 2006-01-09
[QUOTE=enderv]...None of the readmes/wikis provided a solution to my graphic card problems (and I don't think ATI 800XL is such a strange card)...

[/QUOTE]

Download the fglrx driver. And run EasyUbuntu (google for it).

It's damn easy to get the ati cards working with EasyUbuntu. Be sure to check the right maximum resolution !!!!! (if you cant see the spalsh anymore, go into recovery mode and edit the resolutions of all the screens in the xorg.conf file with vi or vim)

grtz

---

### Post by enderv on 2006-01-10
[QUOTE=Snooz]Download the fglrx driver. And run EasyUbuntu (google for it).

It's damn easy to get the ati cards working with EasyUbuntu. Be sure to check the right maximum resolution !!!!! (if you cant see the spalsh anymore, go into recovery mode and edit the resolutions of all the screens in the xorg.conf file with vi or vim)
[/QUOTE]

I did, in the end (download fglrx from ATI), but the way I ended up installing them differed from the WIKI instructions. 

But I'd have liked it to work out of the box (as other things do). As I say, ATI card's aren't exactly rare out there, so having anywhere up to half of the populace experiencing problems isn't making the installation problem helpful... 

If you look at the forums, a lot of the major questions seems to be about ATI cards + wireless (and indeed, these two are what I have/had problem with, with the wireless not being sorted out yet), so I hope that dealing with these is a high priority on someone's usability list.  

V.

---

### Post by nkhansen on 2006-01-10
[QUOTE=enderv]I beg to differ. I can install XP on my PC within two hours running, with the Wifi and most of things I wanted (Firefox, OpenOffice etc..), but I spent last three days to get Ubuntu running properly.[/QUOTE]

Well. You are probably right. However, my situation is the other way around. I can get ubuntu running in 2 hours with all the stuff I wanted (Firefox, Ogg/Vorbis support, Support for my media-library disk (ext3), Wireless (Linksys WUSB11) and more). 

When I tried to install WinXP (I got Civilization IV for Christmas), it didn't recognise the wireless interface (I have been using Linux for years, so I don't keep the driver CDs delivered with any of my products), or the built-in Nvidia Ethernet adapter. I had to get an old 3com 10mbps card, which WinXP supports out-of-the-box and use that to get the drivers I needed.

Then I had to install ext2fs, oggcodecs, firefox and openoffice. It took me 2 hours of looking/downloading!

Now, two days after it runs rather decent, but I still can't add my ogg/vorbis file to WMP's media library.

I realise, that my problems with WinXP concerns hardware support and the fact that I am accustomed to simple things like a fairly standard ethernet-adapter working out of the box. What makes WinXP's hardware support rather good is the hardware-manufacturers support of WinXP, not WinXP itself.

The point is, that on Ubuntu, ease depends on what you are used to, and what hardware you have.

---

### Post by Gowator on 2006-01-10
[QUOTE=spacetime]
6. I agree, Ubuntu should maybe include Samba by default[/QUOTE]

Really have you ever tried getting NFS to work in Windows ?  

Does anyone moan to Microsoft that you can't browse NFS natively in Windows.  

Samba is not a tool everyone should use it is just to allow the odd person/organisation to use Windows and real OS's on the same network.  It should **NOT** be used for 2 realOS computers like OS-X, linux/unix, BSD but only getting a real computer to be able to provide shares for Windows machines.  Samba though an excellent program for what it is is a horrible kludge to allow Windows to communicate witrh the rest of the world.

---

### Post by handy on 2006-01-10
[QUOTE=nocturn]I agree with the former post, most end-users are not capable of installing their own OS and required programs.  At least at the end of an Ubuntu install, you have a working computer with applications.  Windows XP will offer you notepad and a calculator. 

Most end users are not installing their own systems, and are incapable of installing maintaining the anti-virus and firewall software so desperately needed in that commercial OS.

For a fair comparison between OS's, you should compare a preinstalled Ubuntu system with a preinstalled Windows system.[/QUOTE]

There is wordpad.

handy

---

### Post by Gowator on 2006-01-10
[QUOTE=nkhansen]Well. You are probably right. However, my situation is the other way around. I can get ubuntu running in 2 hours with all the stuff I wanted (Firefox, Ogg/Vorbis support, Support for my media-library disk (ext3), Wireless (Linksys WUSB11) and more). 

When I tried to install WinXP (I got Civilization IV for Christmas), it didn't recognise the wireless interface (I have been using Linux for years, so I don't keep the driver CDs delivered with any of my products), or the built-in Nvidia Ethernet adapter. I had to get an old 3com 10mbps card, which WinXP supports out-of-the-box and use that to get the drivers I needed.

Then I had to install ext2fs, oggcodecs, firefox and openoffice. It took me 2 hours of looking/downloading!

Now, two days after it runs rather decent, but I still can't add my ogg/vorbis file to WMP's media library.

I realise, that my problems with WinXP concerns hardware support and the fact that I am accustomed to simple things like a fairly standard ethernet-adapter working out of the box. What makes WinXP's hardware support rather good is the hardware-manufacturers support of WinXP, not WinXP itself.

The point is, that on Ubuntu, ease depends on what you are used to, and what hardware you have.[/QUOTE]

I can't agree more!  
Linux supports way more hardware out of the box than XP but people have bought hardware specifically for XP and then are surprised if it doesn't work first time with Linux.  

ndiswrapper ?  Samba ... these are just compatibility programs and though the programmers deserve praise they are not meant to be easy ... setting up samba for linux is 10x easier than NFs unix servies for NT or XP! Has anyone managed to get a linux driver working in XP?  nope ... yet they expect it to  be simple to get a windows driver working in linux because they can't be bothered to find a natively supported card ?????

Linux works with Winmodems, Winprinter and now WinWifi cards and still people complain. Linux doesn't need people who are actively trying to stiff linux by supporting companies that make specifically Linux unfriendly hardware.  I don't even mean compnaies that don't open source the drivers but companies like netgear who deliberately make the driver files non extractable in Wine .. and yet are quote happy ripping of IPCHAINS and LINUX GPL's without even acknowledging them!  

Even OS-X doesn't make it simple to use linux programs though at least they can usually be compiled and do work yet I don't see list of people saying OS-X doesn't make it simple to run windows programs/drivers and protocols ?

With friends like this who needs enemies?

---

### Post by enderv on 2006-01-10
[QUOTE=nkhansen]Well. You are probably right. However, my situation is the other way around. I can get ubuntu running in 2 hours with all the stuff I wanted (Firefox, Ogg/Vorbis support, Support for my media-library disk (ext3), Wireless (Linksys WUSB11) and more). 
....
The point is, that on Ubuntu, ease depends on what you are used to, and what hardware you have.[/QUOTE]

I agree that these things are fairly subjective - the only (HW) problem I ever had with XP was with my hard disk, where it on install took only 140MB, not whole 200.

I used to have HW hell with 95s and linux long ago, customarily spending days to get my hw configured properly (my video used to conflict with my soundcard which in turn conflicted with modem and that with network card... or something like that). So when I installed XP, and what used to take a weekend took an hour I was impressed enough to go and buy XP! :)

Don't take me wrong - I'm impressed with Ubuntu in a lot ways. I'd even be ok with the graphic card hassle I had, but now I'm going through the wireless troubles that I just can't figure out at all (see my ndiswrapper problems thread), and I can't go w/o wireless - it's just not an option on that computer. Which most likely means I will revert back to XP , regardless of how much I dislike it for anything else than games, and have another go in a year or two.


> 
people have bought hardware specifically for XP and then are surprised if it doesn't work first time with Linux

You mean like that Canadian company, can't remember, ah ATI... 
Strange, I thought I could download linux drivers from them (and they were the ones that worked in the end...).

> 
Has anyone managed to get a linux driver working in XP? 

Why should they? I'm not aware of any users that would need to use a device that can be used under linux only (if there even is such), and wouldn't switch to linux instead.

> 
nope ... yet they expect it to be simple to get a windows driver working in linux because they can't be bothered to find a natively supported card ?????


You mean like I should go out, and throw my HW investment to get a differnt OS running? That sounds so much like MS with Win 3.5/95.... 

Yes, it will be hard on Linux initially (and still is), until a critical mass is accumulated and vendors start producing linux drivers as well.  
But if your cause is to further linux on desktop, as a viable alternative to MS, it _has_ to do this hard bit first. And ndiswrapper (when it works) is a perfect for the (hopefully not too long) transitional period.

Hell, at the moment if I could buy (for say up to 20 quid) a out-of-the-box-working something that would install a driver for my wifi and allow me to set up a WPA in three easy steps (which is what it takes in Windows), I'd be more than happy to pay.


V.

---

### Post by Gowator on 2006-01-10
[QUOTE=enderv]

You mean like that Canadian company, can't remember, ah ATI... 
Strange, I thought I could download linux drivers from them (and they were the ones that worked in the end...).
[/quote]
That is the whole point... but if you want pain in linux go ATI ... I know lots of people got it to work eventually but they choser to buy the worst supported card out of the big 2.  

> 
Why should they? I'm not aware of any users that would need to use a device that can be used under linux only (if there even is such), and wouldn't switch to linux instead.

This is because Linux is open...
... however *for instance* you can use a Sun keyboard or SGI mouse in linux so long as you have the physical interface... 
So far as I know the xbox controllers and remote etc. ONLY work under linux and the XBOX os...  NOT windows.  I can use stuff for macs or lots of old hardware which was supported under DOS and Win3.1 which isn't supported under XP!  However what people usually complain about is not this but the latest product with designed for XP clearly on the box!  

> 
You mean like I should go out, and throw my HW investment to get a differnt OS running? That sounds so much like MS with Win 3.5/95.... 
Yes ... though eBay is more cost effective.  
I stopped using ALL Windows about 5 yrs ago after spending 5 years dual booting or having both.  (I used to have 10 PC's in my basement) however now every single bit of hardware i have works in Linux first time.   
(It also sounds like XP unless you think you can get XP running on my server which is a P90 with 128MB RAM!)  

> 
Yes, it will be hard on Linux initially (and still is), until a critical mass is accumulated and vendors start producing linux drivers as well.  
But if your cause is to further linux on desktop, as a viable alternative to MS, it _has_ to do this hard bit first. And ndiswrapper (when it works) is a perfect for the (hopefully not too long) transitional period.

Unfortunately it also sends the wrong signals and wrong sales figures to the manufacturers thus making this transitional period longer.  

I totally boycott Netgear because of their linux policy and if everyone else did then they might start playing by the rules.  
If you look at another Canadian company ... (Matrox) they always supported linux...  they had dedicated (FREE) support and helped with HW acceleration etc.  
Meanwhile .... people bought NVIDIA and ATI to run Windows games and we now end up with only 2 major vendors for graphics cards one who 1/2 support linux and one who 1/4 support it!  

> 
Hell, at the moment if I could buy (for say up to 20 quid) a out-of-the-box-working something that would install a driver for my wifi and allow me to set up a WPA in three easy steps (which is what it takes in Windows), I'd be more than happy to pay.


Sorry it will be more than 3 steps but this might help you anyway if you reserve £20 for the card :D  
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

Hope that helps!

---

### Post by enderv on 2006-01-10
[QUOTE=Gowator]That is the whole point... but if you want pain in linux go ATI ... I know lots of people got it to work eventually but they choser to buy the worst supported card out of the big 2.  
> 
[quote]
So far as I know the xbox controllers and remote etc. ONLY work under linux and the XBOX os...  NOT windows.  I can use stuff for macs or lots of old hardware which was supported under DOS and Win3.1 which isn't supported under XP!    


I chose the card before I decided to give linux another try.  But don't  you find it strange that weird old HW gets supported when one of two mainline cards doesn't?

> 
I totally boycott Netgear because of their linux policy and if everyone else did then they might start playing by the rules.  


This won't work unless netgear considers linux market an interesting one, which in turn won't happen if it's not easy enough to use for Joe Random. Having an out-of-the-box functionality helps a lot with this. 

That's what I meant that unfortunately initially the hard yards will have to be put in by someone in the linux world.

I'm not saying that this should be necessarily free - as I said I'd happily pay a reasonable price (say up to 100 quid) for a distro that worked out of the box in 95% cases and in the rest I could get a good support (better than MS though :) ).

> 
people bought NVIDIA and ATI to run Windows games and we now end up with only 2 major vendors for graphics cards one who 1/2 support linux and one who 1/4 support it!  


If you want to lobby for linux, game makers should be the ones... I applaud Bioware (for example) and blizzard (for WoW) - I'd switch to linux entirely, and MS likely wouldn't see a cent from me if I had the same selection of games for linux as I have for XP. I think a lot of people who have now dual boot wouldn't anymore, and a few of Win only would move to Linux too.. 

> 
Sorry it will be more than 3 steps but this might help you anyway if you reserve £20 for the card :D  


I've considered getting a new card, but I don't really want to go an shovel money for yet another wireless card (I have three USB ones I think, but only one g) (if nothing else, it's not being environment friendly :) ). That's why I'm happier to pay for services than goods :).

Just one thing to make sure: I'm not bashing linux. I like it more than XP. I just don't think it's ready for Joe Random yet - although it's pretty close I'd think, and covered an incredible distance from the last time I looked.

V.

---

### Post by Gowator on 2006-01-10
[QUOTE=enderv][QUOTE=Gowator]That is the whole point... but if you want pain in linux go ATI ... I know lots of people got it to work eventually but they choser to buy the worst supported card out of the big 2.  
> 


I chose the card before I decided to give linux another try.  But don't  you find it strange that weird old HW gets supported when one of two mainline cards doesn't?

Not really because this old HW provided the spec needed to write drivers against wheras ATI protects it.  You can view this at different levels.  A manufacturer can provide specs .. it can provide partial specs, it can do nothng or it can activaly try and prevent people finding out the specs.  ATI chooses the latter.  
> 
This won't work unless netgear considers linux market an interesting one, which in turn won't happen if it's not easy enough to use for Joe Random. Having an out-of-the-box functionality helps a lot with this. 

Yes but equally this won't happen while Netgear don't kinow who is buying their products and using ndiswrapper.  

> 
That's what I meant that unfortunately initially the hard yards will have to be put in by someone in the linux world.

Probably but that can be by flocking to the manufactuerers who do provide.  
Graphics cards are now a lost cause, we missed the boat because its now almost a duality and Intel might provide some competition but in  most areas say NIC's more players mean that having say 80% of the 5% linux users is better than 3% of the total market.  

> 
I'm not saying that this should be necessarily free - as I said I'd happily pay a reasonable price (say up to 100 quid) for a distro that worked out of the box in 95% cases and in the rest I could get a good support (better than MS though :) ).

 Hmm Linspire is clos-ish... i paid my $100 for life membership though I don't actually use it :D  because for me I'd rather have a *real* distro and a bit of work...

> 
If you want to lobby for linux, game makers should be the ones... I applaud Bioware (for example) and blizzard (for WoW) - I'd switch to linux entirely, and MS likely wouldn't see a cent from me if I had the same selection of games for linux as I have for XP. I think a lot of people who have now dual boot wouldn't anymore, and a few of Win only would move to Linux too.. 

I agree and I just play consoles .. but at least Im not clouding the market by using cedega/wine on windows products

> 
I've considered getting a new card, but I don't really want to go an shovel money for yet another wireless card (I have three USB ones I think, but only one g) (if nothing else, it's not being environment friendly :) ). That's why I'm happier to pay for services than goods :).


Like i said eBay :D  but the thing I did was slowly just swap out the non-linux compatible stuff.  

> 
Just one thing to make sure: I'm not bashing linux. I like it more than XP. I just don't think it's ready for Joe Random yet - although it's pretty close I'd think, and covered an incredible distance from the last time I looked.

V.
I honestly think it depends what Joe wants.  
word processor, email, browser ... no problem except for realmedia etc. but the problem is realmedia shouldn't exist ... flash should not exist etc. because the internet should not contain closed formats.  The problem is companies use these on websites and then people need to download the plug-ins and these come with restrictive licenses.  The only pirated SW I ever use is realplayer because I refuse to give my card details to a company who's plan is to make it difficult for you not to keep paying once the 1 month grace period is finished.  

Games .. yep I agree but again companies are not interested in your opinion they are interested in your £ and $ ... and if you buy and use it in cedega/wine then they really don't care .. if you buy it and it works poorly they don't care .. all they care is you buy it.

---

### Post by Puptentacle on 2006-01-11
I'm becoming a Linux disciple after a very VERY short period of time. 

I was a variation on  the "Joe Random" user until pretty recently. I've wanted to get away from Winders for a LONG time. I've been playing with Live CDs for around two years before I finally found Ubuntu and decided to make the plunge. Right now I'm dual booting until I'm comfortable with Bash and the various programs and then...Windoze is GONE. 

What took me so long? "Linux is HARD". I heard so many people say that. I have to say that, even for a pretty advanced user, the word "Terminal" IS pretty scary. But at least the terminal (which I'm now teaching myself) is logical, unlike the underlying command structure of Windoze. I'm starting to rant...

I DO think that I could take a machine, install Breezy as it comes, sit it in front of Granny or Grandpa Average and it will do everything they want it to do. Anyone who is familiar with the basics of computing should be able to install Ubuntu, open the repositories and fly. Problem is, people are used to the way Billy's Gates of Hell operates and that is what they are going to stick with. Changes are occuring, however. 

Firefox is opening up MANY users to the concept that there is life outside MS and that life can be better. I personally think as more people see and work with Firefox they will be more susceptible to the suggestion that "If you like Firefox, you ought to try Ubuntu". The more hands those live CD distros end up in, the more users you are going to see. 

As far as installs and compatibility go...I had ZERO problems getting Ubuntu up and running on my machine. Nvidia GeForce 5500, Creative Audigy ZS Platinum, no problems whatsover. Hell, even my DSL worked out of the box. That NEVER happened with a Windoze install. Something always gave me troubles. 

To bring this tired, sleepy run-on post to a close... It depends on what you are looking for. Some people will NEVER switch from Windoze, more out of fright than any real, solid reasons. But with DRM and the inevitable problems that will be associated with Longhorn, you are going to see more and more people switch. Lets hope Linux is ready.

---

### Post by hscottyh on 2006-01-11
[QUOTE=nocturn]For a fair comparison between OS's, you should compare a preinstalled Ubuntu system with a preinstalled Windows system.[/QUOTE]

I agree! All the friends/family I've converted have always called me to install software for windows much less windows! If it's this kind of user, then ubuntu is just as easy for them to use.

Thank goodness for VNC! When they have a question or problem, I don't have to leave the house, no matter what OS they are on. :KS

---

### Post by pieboy314 on 2006-01-11
I had this discussion with another techie this afternoon. I am new to linux and learning alot in a hurry. But there is no way in this world I would advise a novice computer user to run a linux box.

I think most people that are posting in here and saying otherwise are just overly optimistic and/or out of touch with where your average novice computer user is coming from. I do a bit of work in tech support and trust me... your novice to average computer user is not ready for Ubuntu, regardless of how userfriendly it is.

---

### Post by Puptentacle on 2006-01-11
I don't think I quite explained myself in my post from last night. 

I think a person COULD sit down and get right into Ubunutu...but only if that person has NO experience with Windows. 

Windows has a set of protocols that just plainly do NOT apply in Linux. The problem isn't learning Ubuntu, the problem is UNLEARNING WINDOWS! People are so used to the awkward way that Windows functions they have a hard time doing something different. How else do you explain people who continue to use IE after being shown Firefox? 

A basic install of Ubuntu contains the tools that MOST average users actually USE on a computer. Word Processing, Email, Internet, Music Player, basic set of games. Gaming, programming, movie editing, etc. are not done by most users. Windows requires you to get your own word processor (unless you count Wordpad!), your own media player (unless you count the bloated, slow, feature free Windows Media Player), your own mail app (unless you count the buggy Outlook). All of this is available in a basic install of Ubuntu. None of these apps for Ubuntu is any easier to learn than the Windows version. 

Downloading apps in Ubuntu is actually EASIER than with Windows. With Windows, you are forced to go out and either purchase programs, sometimes costing a large sum, or search endlessly for freeware which might be infected with adware, spyware or worse. The other option is cracked or hacked progs, and we all know what problems can come from that. Ubuntu nearly makes it effortless with the use of repositories containing applications proven to work. 

I think most people could easily be taught Linux (or learn it themselves) if they are motivated to do so.

---

### Post by aysiu on 2006-01-12
[QUOTE=Puptentacle]
I think a person COULD sit down and get right into Ubunutu...but only if that person has NO experience with Windows. 

Windows has a set of protocols that just plainly do NOT apply in Linux. The problem isn't learning Ubuntu, the problem is UNLEARNING WINDOWS! People are so used to the awkward way that Windows functions they have a hard time doing something different. How else do you explain people who continue to use IE after being shown Firefox?[/QUOTE] Most of my co-workers are these "average" Windows user we keep talking about, and I agree with your statement about "unlearning" Windows--they'd be fine in Ubuntu if they'd started with it, but change isn't their strongsuit when it comes to computers.

Hell, even just changing databases (still Windows), upgrading from 2000 to XP, and switching up Microsoft Office versions threw all my co-workers off, and they all came complaining to me that they no longer could do what they used to be able to do until I showed them "the new way." Still Windows, but even *then* they needed "re-training."

---

### Post by aysiu on 2006-01-12
[QUOTE=pieboy314]
I think most people that are posting in here and saying otherwise are just overly optimistic and/or out of touch with where your average novice computer user is coming from. I do a bit of work in tech support and trust me... your novice to average computer user is not ready for Ubuntu, regardless of how userfriendly it is.[/QUOTE] I'm sorry, but I don't trust you. New users need to be trained even to use Windows. Daily... *daily* I have my co-workers bugging me because they don't know how to do something in Windows or something "wrong" happened in Windows, and they want me to look into it (I'm not the tech department by the way). The truth is that novice-to-average users are constantly reliant on more advanced users, regardless of operating system.

Please cite specific aspects of the Ubuntu user interface or specific daily tasks that would be more difficult for novice users than in Windows.

---

### Post by nocturn on 2006-01-12
[QUOTE=pieboy314]I had this discussion with another techie this afternoon. I am new to linux and learning alot in a hurry. But there is no way in this world I would advise a novice computer user to run a linux box.

I think most people that are posting in here and saying otherwise are just overly optimistic and/or out of touch with where your average novice computer user is coming from. I do a bit of work in tech support and trust me... your novice to average computer user is not ready for Ubuntu, regardless of how userfriendly it is.[/QUOTE]

Again, I really disagree.  But for a novice, they should get a preisntalled Ubuntu box as they do for Windows.

I maintain that in that situation, Ubuntu is easier to maintain for them then to deal with Anti-Virus, Anti-spyware and the likes on that OS from redmond.

I help out quite a number of people with their computers (I'm actually a programmer/sysadmin) and I have yet to meet a novice user that is capable of installing windows and anti-virus correctly.  Most of them buy a box with windows+norton and you find out that their AV hasn't been updated for 3 years when a virus hits them badly.

---

### Post by Gowator on 2006-01-12
[QUOTE=pieboy314]I had this discussion with another techie this afternoon. I am new to linux and learning alot in a hurry. But there is no way in this world I would advise a novice computer user to run a linux box.

I think most people that are posting in here and saying otherwise are just overly optimistic and/or out of touch with where your average novice computer user is coming from. I do a bit of work in tech support and trust me... your novice to average computer user is not ready for Ubuntu, regardless of how userfriendly it is.[/QUOTE]


Absolutely not... but then I can't say it any better than 

[quote=Puptentacle]
I don't think I quite explained myself in my post from last night.

I think a person COULD sit down and get right into Ubunutu...but only if that person has NO experience with Windows.

Windows has a set of protocols that just plainly do NOT apply in Linux. The problem isn't learning Ubuntu, the problem is UNLEARNING WINDOWS! People are so used to the awkward way that Windows functions they have a hard time doing something different. How else do you explain people who continue to use IE after being shown Firefox?

A basic install of Ubuntu contains the tools that MOST average users actually USE on a computer. Word Processing, Email, Internet, Music Player, basic set of games. Gaming, programming, movie editing, etc. are not done by most users. Windows requires you to get your own word processor (unless you count Wordpad!), your own media player (unless you count the bloated, slow, feature free Windows Media Player), your own mail app (unless you count the buggy Outlook). All of this is available in a basic install of Ubuntu. None of these apps for Ubuntu is any easier to learn than the Windows version.

Downloading apps in Ubuntu is actually EASIER than with Windows. With Windows, you are forced to go out and either purchase programs, sometimes costing a large sum, or search endlessly for freeware which might be infected with adware, spyware or worse. The other option is cracked or hacked progs, and we all know what problems can come from that. Ubuntu nearly makes it effortless with the use of repositories containing applications proven to work.

I think most people could easily be taught Linux (or learn it themselves) if they are motivated to do so.[/quote]

My mum hadn't used a 'computer' since the early IBM standalone WP's.  
Giving her a Gnome desktop with everything she needs (browser, email and WP) is far simpler for her than installing XP.  

When we installed Lotus Notes at work we had to retrain users because it uses non standard MS icons and menu's ... when you take someone from a Mac or someone who has been using Solaris for years then Ubuntu is not only more simple than XP it is in a different league.  

If you live in the paradigm of download illegal software and cracks and click on a self installing .exe with unknown payload world then the task of opening up synaptic and choosing the program might seem strange but its a damned site easier.

---

### Post by Gowator on 2006-01-12
[QUOTE=aysiu]

Please cite specific aspects of the Ubuntu user interface or specific daily tasks that would be more difficult for novice users than in Windows.[/QUOTE]
Easy ...
In Windows i can install a virus simply by having it in outlook.  In linux I have to extract it, make it executable and then run it ... and even then I can't get the  damned viri to work properly under Wine!

---

### Post by porschemad911 on 2006-01-12
My housemates could barely set up Windows by themselves, and they definitely couldn't set up any sort of linux. But I've thought of a cunning plan to wean them off Windows (on my housemate's laptop).

I've moved my desktop complete with fully set up Breezy install into the family room, so they can use it for the internet, office, IM, gaming, multimedia etc and see how much better it is that Windows!

Reel 'em in ... :p

---

### Post by pieboy314 on 2006-01-12
I guess there is some need to defend my comments, although the point of unlearning Windows first is a very good point.

But as user friendly as Synaptic is,  looks at my post and the two responses I got for what I thought was installing a simple chess game.

[QUOTE=pieboy314]ok...

I used System > Administration > Synaptic Package Manager

installed gnuchess, no erros but it does not appear under my Games menu, where might I find it and how do I run it?

sorry for the very newbish question[/QUOTE]

[QUOTE=benplaut](i don't use GNUchess, so this may not be correct)

Press Alt+F2, then in the box that pops up, type 'gnuchess' (without the ' '), and click 'Run'.

Good Luck!

**<EDIT>**

Read what Qrk says, below.[/QUOTE]

[QUOTE=Qrk]gnuchess does not incude a GUI. It is only the chess program underneath.

To run it usably, use synaptic to get either "gnome-chess" or "knights"

Knights is a KDE program but it is very nice. You'll have to configure them to use gnuchess as the chess engine.[/QUOTE]

I am sorry, but that is not novice level stuff. That is not a big fat icon on my desktop ready to go.
However, I can download a simple executible from download.com and double click it in another environment. The odd windows newbie might screw that up too, but someone must admit that it would be a slightly simpler process.

I am learning to love linux and Ubuntu, but I am a novice when it comes to linux and I still say it is not all about my Windows hang-ups, linux is still slightly more technical.

If you look at my example and say, "piece of cake", "entry level stuff" you are confirming my point, you forget how confusing it can be to newbies.

Hope that my comments does not tick off anyone too much, I am trying linux for a reason.** I do not want it to just be Windows, I understand it is different and should be** ( I am also already tired of the people simply looking for linux windows) and please also remember that I did not start the post I am just chipping in my opinion.

just my two cents worth...

---

### Post by nocturn on 2006-01-12
[QUOTE=pieboy314]
I am sorry, but that is not novice level stuff. That is not a big fat icon on my desktop ready to go.
However, I can download a simple executible from download.com and double click it in another environment. The odd windows newbie might screw that up too, but someone must admit that it would be a slightly simpler process.
[/quote]

Yes, it is simpler, but how many times will this kind of action download something infected with spyware?  How many times will the downloaded app overwrite newer libraries in system?

We have to strike a balance between simplicity and safety, windows is completely on the simplicity end of that equation and that hurts users too in the long term. 

> 
If you look at my example and say, "piece of cake", "entry level stuff" you are confirming my point, you forget how confusing it can be to newbies.


Yes, it is a piece of cake for me now, but I switched to Linux in 1997 and ditched windows completely in 1999.  Almost everything done on  Linux was more difficult then in windows back then.  But it got rid of me having to reinstall win98 every six months and got me numerous other benefits.

Things got easier with time (and I'm a very technical user).  But I did not understand how difficult windows can be to someone that is not used to it until I spent nearly two years away from it (I worked for a company with Gnome/Solaris desktops for a while and use Linux at home).

When I got my winXP notebook at work, I found it very confusing and I really missed a package manager and many other features.  The download.com dogma did not suit me any more.

There are some things that can improve such as the chess situation you describe, but it will improve by implementing a solution on top of the Linux-dogma and not by mimicking windows.

---

### Post by Gowator on 2006-01-12
[QUOTE=pieboy314]I guess there is some need to defend my comments, although the point of unlearning Windows first is a very good point.

But as user friendly as Synaptic is,  looks at my post and the two responses I got for what I thought was installing a simple chess game.

I am sorry, but that is not novice level stuff. That is not a big fat icon on my desktop ready to go. [/quote]
Well the problem is in answering questions at the right level.  

If you sound like you know a reasonable amount people will answer a bit more tersely than if you say HELP - COMPLETE NOOBIE - HELP  ....

However what you have described is a bit of  poor luck!  
A good thing with Debian is that the packages are split into components which means you don't get horrid deps on some small package (like say cdrecord) being bundled with one CD writing app.  
However Cdrecord is ajust a CLI prog which is used by Gnome burner, k3b et al...  so if you choose to install it you won't get an icon ... etc. because it has no GUI interface unless a 3rd party app is added. 

What would be nice is an extra flag in apt tools which indicates if the package is a front-end package or not ...


Imagine downloading a driver in Windows... it might double click top open or it might be a zip file with a readme that says copy this to the xxx directory by chance you found the latter..  



> 
I am learning to love linux and Ubuntu, but I am a novice when it comes to linux and I still say it is not all about my Windows hang-ups, linux is still slightly more technical.

If you look at my example and say, "piece of cake", "entry level stuff" you are confirming my point, you forget how confusing it can be to newbies.
yes and no ... if you kep with it you will be thinking piece of cake real soon!  
> 
Hope that my comments does not tick off anyone too much, I am trying linux for a reason.** I do not want it to just be Windows, I understand it is different and should be** ( I am also already tired of the people simply looking for linux windows) and please also remember that I did not start the post I am just chipping in my opinion.

just my two cents worth...
Well certainly not me nor nocturn by his answer....

Linux-Windows users do piss me off though :D  
Like nocturn says this has to be solved from a linux paradigm NOT a windows one because the latter is throwing out the baby with the bathwater.  

One way is
[http://klik.atekon.de/](http://klik.atekon.de/)

another is arnieboy's automatix ...  

both of these work though by limiting the choice of what they show ... 
if they included lots of libs and helper apps etc then they would cease to be simple.

---

### Post by pieboy314 on 2006-01-12
yes, Gowator & Nocturn I have read and agree.

I jumped into this thread at the point where they were discussing if Ubuntu was suitable for new computer users. Right or wrong.. I posted an opinion on that. Then when asked, I provided an example to back my statement. Thats all.

I did not mean to debate the pros and cons of the various OS'es.

This is a great community and as I said I am learning & loving Ubuntu. I will be an expert soon. ;)  I guess I should reserve my comments until I am an expert on both systems.

..but for now, I do offer an the unique perspective of the "newb"

---

### Post by Ubuntu_User on 2006-01-12
[QUOTE=ptmurphy]I have been using various flavors of Linux for a while (maybe about two years, Suse and Ubuntu mostly) to setup a web server, MySQL, PHP, Samba, etc.  I like it and enjoy tinkering and figuring things out, but I am a computer nerd.

I would like to share the virus and spyware free experience with my friends and family, but some things are just too difficult for the average home user, in my opinion.  Examples of things that I normally have to do over the course of a Linux install that I don't think my average friend would (or maybe could) do...

1. Get nVidia drivers working properly for 3D graphics
2. Enable DMA for CD/DVD Drives
3. Install MP3 Codecs
4. Install DVD Codecs
5. Get a CSS program working to view DVDs
6. Install and configure Samba for network sharing
7. Re-mapping of keys for shortcuts
8. Get a wireless network card working
9. Any hardware setup problem (keyboard, mouse, CD, etc. not working)

I understand some of the issues (3-5) are a byproduct of having a free operating sytsem, but getting new hardware installed and working properly and getting some programs setup and working seem overly difficult.

I cannot imagine my mom and dad trying to setup and use Linux, or even most of my friends.  It takes a lot of patience and a knack for learning technical things.

As an example, the last time I tried to install nVidia drivers, I totally messed up my xorg.conf.  How many people on here have parents or friends that could have or would have taken the time to figure out how to get X back up and running when confronted with a login: prompt at a black and white screen.

Just curious if anyone else feels the same way and how this can be remedies?

Thanks...[/QUOTE]
The answer is quite easy. Most Linux distributions cannot provide these solutions by default because the US laws and patents don't let them do it legally.

---

### Post by ritger on 2006-01-12
In response to the TS of this thread, i think you'll have the same problem with people getting Windows to install. Most people i know rather go buy a new pc once the old one is so slow due to spyware it's barely usable. So i don't think installing is a big problem, since you're gonna be stuck with that job anyway. Or do you like getting calls from your uncle to see if you can restore his D: drive with 6 years worth of photography and no backups after he mistakenly hit `use entire drive' in the installer? This is just as simple to mess up in any other OS.

I used to be the go-to guy in my family (being a CS student). So i just switched to GNU/Linux myself so i could say i didn't understand one thing about Windows. Now i just put either OS X or GNU/Linux as the dealbreaker. You want my support? Use either one, otherwise don't call me. So when mum wanted a new pc i made her buy a Mac. Locked it down, and haven't had one single call with `My printer won't work', `the scanner is broken' or any other stuff relating to software problems. You can do practically the same with any modern GNU/Linux distribution, it'll take you some more time but it's doable. Just make sure up front they know what to expect. I always make it abundantly clear that you don't get to change anything on the pc. You get to use it. You want to mess up the install? Fine, don't come crying to me when it's broken, you get to fix it yourself as well.

But that's just my geeky perspective.

---

### Post by tim.n9puz on 2006-01-12
[QUOTE=spacetime]...The rest:

1. Moan at NVidia, not Ubuntu.
[/QUOTE]

I'm not picking on spacetime here but this sort of advice is something that I feel we all need to avoid if we intend to promote and evangelize Ubuntu/Linux. 

Whether <insert distro name here> is available without purchase or not the user is in the role of a customer. If he or she is installing their new system they primarily just want it to work. When it doesn't they mostly feel that "Linux didn't work", at least for them. Telling them that Linux/Ubuntu is okay and that they should complain to nVidia or another supplier does not help them with their problem which is how to make their computer do email, word processing, etc. effectively and cheaply.

---

### Post by Jave27 on 2006-01-12
[QUOTE=tim.n9puz]I'm not picking on spacetime here but this sort of advice is something that I feel we all need to avoid if we intend to promote and evangelize Ubuntu/Linux. 
[/QUOTE]

But, at the same time, he's absolutely right.  Perhaps "moan" was too tough of a word, but contact with manufacturers must be made before they realize that there is a market out there for Linux users.  nVidia does a pretty good job of supporting Linux, but they could always do better, and they've gotten consistently better with time and help from users.

Evangelizing only goes so far.  If you come into a forum and say "Ubuntu is the greatest thing on the planet!" and then have to explain that "well, except products x, y, z, .... don't work at all, or at least without major tweaking", then you'll just get laughed at.  Evangelize the philosophy if you're going to do it, but don't evangelize a particular project that happens to follow that philosophy unless it is exactly what the other person is looking for.  Zealots annoy me sometimes (not saying you are one, just saying).  :)

---

### Post by jobezone on 2006-01-12
[QUOTE=tim.n9puz]Telling them that Linux/Ubuntu is okay and that they should complain to nVidia or another supplier does not help them with their problem which is how to make their computer do email, word processing, etc. effectively and cheaply.[/QUOTE]

True, but complaining to the hardware suppliers that they give the necessary specifications for linux developers to make drivers for it, is a good way to try to reach the long-term goal of not having these kind of problems. That, and start using non-pantented codecs like ogg vorbis.

---

### Post by Gowator on 2006-01-12
[QUOTE=pieboy314]yes, Gowator & Nocturn I have read and agree.

I jumped into this thread at the point where they were discussing if Ubuntu was suitable for new computer users. Right or wrong.. I posted an opinion on that. Then when asked, I provided an example to back my statement. Thats all.

I did not mean to debate the pros and cons of the various OS'es.

This is a great community and as I said I am learning & loving Ubuntu. I will be an expert soon. ;)  I guess I should reserve my comments until I am an expert on both systems.

..but for now, I do offer an the unique perspective of the "newb"[/QUOTE]
Please don't do that because you have a very valuable commodity that cannot be bought or learned .. noobyness :D  

Your identification of the problem is correct and the software you chose illustrates something that needs doing that it is hard for people who have 10yrs of linux to experience realise.  For instance the package lists have grown a lot .. when I started with linux the first time there were almost no apps that ran in X... and installing a program meant downloading and compiling source code.  

However (no offense) you are unlikely to come up with the best way to address it until you understand more about linux or *nix overall and .. by that time you will have lost your noobyness and be helping others .. (every single one of us started off a noobie!)  but you won't have the same insite into what a first time linux user thinks anymopre because those little things will have become second nature

---

### Post by JimS on 2006-01-12
...
So  ---  What are U going to do?

First question should be what do you need to do?
Can Linux assist you?
Or is this task a Windows thingy?
Then -- Can you afford it?  Time?  Money?
Do you have the knowledge to put it together
or are you going to have to have someone else
help you?
These are just a few questions you should ask yourself
before venturing into the Linux (Mac or Windows also) world.
Asking yourself the necessary questions may be hard work
for some of you.  I can tell by your comments.

Linux is different, but not much.
Putting Linux on a Windows box may be stupid in some cases.
You may need to built your own box.
Retro fitting may or may not work.

But using Linux (once it is properly installed on the right equipment)
is no more difficult than using Windows or Mac.  Switching from
Windows to Linux is as easy as switching from driving a car to
driving a small pickup truck.  My wife is a computer putz, but she
can do her thing on both our boxes, the Windows one on the
right side of the desk, and the Linux one of the left.

The only SO difficult thing is to put your desires, OS. HW, and SW
together into a viable package.  Once that is done the rest
is a piece of cake.

JimS
Prostate Cancer Aware
...

---

### Post by linuxa on 2006-01-12
Whilest I do agree that issues to do with codecs or closed source software (e.g. Nvidia drivers) do make life hard for the general acceptance of linux.

Things like getting DMA set up by default in a Linux distro should IMHO be done prior to shipping a distro.

That being said I do think that we are in the infancy stage of Open Source development, and if I could compare it to the life of the automotive industry, the Linux world right now is very much like the days of old when if you wanted to drive a car, you had to be an (amateur) mechanic. 

The cons of Free Software is that you must be willing to give the time, energy and for some of us - hair :P needed to get things working.

Just yesterday, my install of the newest Nvidia driver ran amok when unbeknown to me, my last "apt-get upgrade" brought in a compiled version of an earlier driver with the latest kernel update -  say hello to a day without X :rolleyes: 

But at the same time, as someone who is interested in looking under the hood of an OS, and perhaps isn't too afraid to spare a few hair folicals or two. I'm fully willing to look past the difficulties of using Linux over Windows, and still give high praises to the Open Source Community :D

But my friends/family? I look forward to the day when Linux distros are fully dummy-proofed (mean that in the nicest possible way)...

Regards all

---

### Post by Puptentacle on 2006-01-13
[QUOTE=linuxa]
But my friends/family? I look forward to the day when Linux distros are fully dummy-proofed (mean that in the nicest possible way)...[/QUOTE]


I don't think that is ever going to happen. Even after all these years, courses in schools, TV shows, books and "the geeky neighbor" there are still Windows users who can't install a printer (much less drop in a video or sound card).  I'm sure Dell and other manufacturers still get calls from users who can't power on the machine ("I've tried EVERYTHING and it doesn't work") only to find out the problem is a lack of power interface cable connection (not plugged in). 

ritger has a good point with the "you get to use it", not break it mentality.  That will definitely be the way I set up machines for others in the future.

---

### Post by Gowator on 2006-01-13
[QUOTE=Puptentacle]I don't think that is ever going to happen. Even after all these years, courses in schools, TV shows, books and "the geeky neighbor" there are still Windows users who can't install a printer (much less drop in a video or sound card).  I'm sure Dell and other manufacturers still get calls from users who can't power on the machine ("I've tried EVERYTHING and it doesn't work") only to find out the problem is a lack of power interface cable connection (not plugged in). 

ritger has a good point with the "you get to use it", not break it mentality.  That will definitely be the way I set up machines for others in the future.[/QUOTE]

Well it has happened already we just don't notice it.  
Almost everyone can use a Tivo .. linux.. or numerous routers based on linux (a bit more techy) or probably 101 other places you come across linux everyday and don't realise it.  

Most people I know can use google... (linux) and webmail apps running linux .. just so long as they don't know it's linux running behind it.  

If you want a simple PC i can give you a mythTV box or a cut down box with Mail client, browser and OO and it will just work and work... but what we (the people on this thread want) is something more flexible than that.  

The cost comes with flexibility and liinuxa made a good analogy.  
Do  you want an OS you can fix yourself OR an OS you need an expert with expert diagnostic tools that only work for your distro-release to work.  

 My father is 70 and everyone in his generation with a car had to tinker but this meant they could always get it going.  I can tinker a fair bit myself... but not so much as my father's generation .. my father is an engineer so i expect that but even his accountant friends could tinker at least as well as me with a carb!  

Now my car needs specialist equipment just to do the timing ... something used to be done with a little screwdriver... or wrench ... if it goes wrong I need an expert to fix it.... 

Wheras there may be a linux for people who don't want to understand how-it-works it will never be as flexible as one where you must!

---

### Post by ade234uk on 2006-01-13
You know I have gone past the point of saying that Linux should do this and Linux shoud do that because eventually these things will be ironed out and secondly Linux is a different animal.

Ubuntu is running better than my Windows ever did and this is not because I am now a M$ hater its FACT. 

Microsoft can try to dazzle me with their new Vista simplistic bullshite advertising look, but it simply dont rub with me anymore. Under that gloss finish is a complete pile of shit OS which unfortunately average Joe cannot see or understand and will go for looks.

What keeps me interested is how far Linux has matured in the last 2 years and how it pushes the boundaries. 

I like to think about all the exciting projects around like Mono, Crossover Office 6 with game support. This is enough and warrants never running Windows. 

The more people install Linux as you know who install Linux the more companies will respond. 

NVDIA are the good guys becuase of the drivers I know I can safely part with my money for a new NVIDIA card. Forget ATI they dont give a shit and becuase of this they lose money, and when they start losing more money we will start to see more co-operation from them.

---

### Post by kosmic on 2006-01-13
[quote=Gowator]Easy ...
In Windows i can install a virus simply by having it in outlook. In linux I have to extract it, make it executable and then run it ... and even then I can't get the damned viri to work properly under Wine![/quote]
 
How amazing post :) heheh my favority

---

### Post by Bealer on 2006-01-13
Being quite new to Linux myself, I've found it to be close but not quite there as a solution for a novice user to switch from Windows.

1) The hardware support is still a bit of a pain. I'm not arguing where the blame lies, it's still an issue though.

2) Lack of inbuilt WPA. More common these days, I found it quite tricky to setup, some nice gui diagnostics or feedback would be helpful.

3) More gui configuration. I've found this lacking in Ubuntu. Fedora seemed much better, but still not great. Command lines are ok, but take time, are open to typo's etc... a gui would be much more practical for all the settings I may need to change.

4) Lack of inbuilt mp3, codec support etc... Can't really be helped, but still annoying.

Apart from those four points I really like it. Just feels more solid, reliable. Also, Automatix helps solve some of the above issues, a great package to have. Just love the fact that I shouldn't really have to go to a website to download an app, as it'll most likely be in one of the repositories.

With regards to Ubuntu I'd like to see better wireless support inbuilt, and easier to configure/check. A graphical installer like Anaconda, maybe a nicer looking loader (during boot). And a more simplified or organised version of the synaptic installer. From what I've read Fedora Core 5 will address this issue as the number of often strangely (or messily) named packages in apt can be quite overwhelming.

Next step is to learn up a little more, and put it on my parents machine and slowly switch them across.

---

### Post by Gowator on 2006-01-13
[QUOTE=Bealer]Being quite new to Linux myself, I've found it to be close but not quite there as a solution for a novice user to switch from Windows.

1) The hardware support is still a bit of a pain. I'm not arguing where the blame lies, it's still an issue though.

2) Lack of inbuilt WPA. More common these days, I found it quite tricky to setup, some nice gui diagnostics or feedback would be helpful.
[/quote]
Yep ... its comoing though 
> 
3) More gui configuration. I've found this lacking in Ubuntu. Fedora seemed much better, but still not great. Command lines are ok, but take time, are open to typo's etc... a gui would be much more practical for all the settings I may need to change.

Try webmin ...  for instance which is a web interface.  
Its not as hand-holding as say YaST but it is portable and works the same on every *nix AND *bsd and ....  
I'm not a fan of distro specific linux GUI tools because they rarely work well and usually think they know what you want better than you do!  
In the end I find them more limiting because usually they are incompatible with editing and tweaking by hand and hence better not to have them.  
Suse for instance does everytihng with YaST but if its not in YaST then you can't do it without ignoring countless "Do not edit this file" warnings... and when you do it ends up being reset next time...

I just did a Suse install  and  for some reason YaST would not work with the NIC and DHCP... (bear in mind its an install next to BSD, Ubuntu and gentoo which all work) .. whenever I tried to bypass it with a static IP it works until I reboot and YaST decides to undo my manual edits!  

.. so be careful what you wish for ..it might come true ....

> 
4) Lack of inbuilt mp3, codec support etc... Can't really be helped, but still annoying.

I know ... linspire did a $5 life license for DVD playback .. I'd happily pay  $5 or $20 even for all the codecs as a maintained .deb 

>  Automatix helps solve some of the above issues, a great package to have. Just love the fact that I shouldn't really have to go to a website to download an app, as it'll most likely be in one of the repositories.
 :D  yep... I'd rather have a repo with libdvdcss, mp3 codecs etc. legally than see them included into distro's though.  This way its simple to have even just an icon on the desktop like automatix does which goes off and fixes stuff but someone has to negotiate this with the relevant people!

---

### Post by brunog on 2006-01-13
I have to agree.
For me, I would like to get away from Win.98 but refuse to pay for XP and like the idea of a comunitee of people supporting each other in developing "free" software.
I have been trying Ubuntu for the past 6 to 8 months.  I am by no means a computer geek,  but like working with these fantastic machines and figuring things out.  I am an Engineer by training,  so should be able to understand some of the technical issues.
But sometimes I have no idea what people are talking about.
I have been trying for 4 months to get my winmodem working with no success.  Things as essential as connecting to the internet should at least be a bit easier.
If you battle to get your foot in the door - it is sometimes more difficult to continue.

I will not give up.
I believe there is a future in OSS.
And when the time comes - I will know something usefull (just as I am fortunate enough to be able to help myself in DOS when others just want to click and drag...).

Long live OSS!!

---

### Post by adam.tropics on 2006-01-13
Difficult....perhaps, but as time goes by even in the windows world, users are being asked to learn and understand more and more. Hell, the average household these days needs a network administrator! Computer for the kids, one for the wife, one for the husband, routers etc etc.Things have changed a tad since the days of just plugging into the phoneline and dialing up! So I fail to really understand why, with all the help available, (not forgetting these forums, which are a fantastic resource), it's so difficult. 

From what i can see, and this includes me, most people here seem to eventually manage to gat a working box with the software they need running. Along the way they learn something, also good. The problems come when we then get cocky and learn about tweaking and customization, and break it ourselves!! I read once in one of these things someone describing themselves as 'confident enough in ubuntu to be a danger to himself'!! Many of us suffer this  me thinks!

---

### Post by linuxa on 2006-01-14
[QUOTE=Puptentacle]I don't think that is ever going to happen. Even after all these years, courses in schools, TV shows, books and "the geeky neighbor" there are still Windows users who can't install a printer (much less drop in a video or sound card).  I'm sure Dell and other manufacturers still get calls from users who can't power on the machine ("I've tried EVERYTHING and it doesn't work") only to find out the problem is a lack of power interface cable connection (not plugged in). 

ritger has a good point with the "you get to use it", not break it mentality.  That will definitely be the way I set up machines for others in the future.[/QUOTE]

I get what you are saying.

IMHO, it comes down to the fact that computers used to be government/research equipment - the "don't touch unless you know what you are doing!" kind of thing. Hopefully as time goes on, the acceptance of the pc will give the Joe/Jane user more courage than to think of a computer as some type of mystical artifact. 

Just like the gradual acceptance of cars, TVs and other new jee-whiz electronic gadgets. The same kind of acceptance would probably make the same everyday user seek out Window alternatives :D

---

