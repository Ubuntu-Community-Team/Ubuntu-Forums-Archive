---
title: "New User unsure about programs to use"
date: 2009-04-11
forum: General Help
---

### Post by chris.willis on 2009-04-11
Hi there,

I am making the transition to Ubuntu, but am not too sure what the better programs are. I am sorry if something like this has been posted before, but I would like advice as to what to use. I have two laptops and a desktop and want to get away from Windows XP and Vista if possible. Below are programs I either use or would like to use under Windows. Does anybody know what the best equivalents are under this 'Ubuntu'?:

Microsoft Word 2003 (most compatible for long, complex documents?)
Microsoft Excel 2003
Microsoft Outlook 2003
Microsoft Frontpage 2003

Nero Burning ROM
AutoGordian Knot (fantastic prog)
KMPlayer
Windows Media Center
DVD Shrink
DVD Decrypter
ConvertXtoDVD
Womble MPEG Video Wizard DVD
ACDSee
"Eric's Movie Database"

Comodo Firewall Pro
Rising Antivirus
VirtualBox
WinRAR
uTorrent


I think that's everything I'll ever need! I hope you understand how confusing this all is for the average user, but I do look forward to your response.

(While posting this thread, I wasn't sure about all the ubuntu, kubuntu, xubuntus - is there a difference? Should I be using something else or am I in the right place -- sorry if I'm not!)

8o)   thanks in advance,
Chris

---

### Post by lisati on 2009-04-11
Open Office can handle many of the documents produced by Microsoft Office, but you might occasionally find that the formatting is slightly different if you open a file produced by one with the other program. For email, you might want to check out Evolution or Thunderbird.

I think DVD shrink can be made to work via [Wine]("https://help.ubuntu.com/community/Wine") but I'm not completely sure.
Nero has an Ubuntu-friendly version but I think you have to pay for it.

There are a handful of other programs that might be of value, but I hesitate to make suggestions: I keep Windows around for most of the video stuff I do (partly out of laziness searching for suitable equivalents, and partly because none of the Ubuntu-friendly offerings do quite what I want)

---

### Post by JECHO on 2009-04-11
> **chris.willis said:**
> Hi there,

I am making the transition to Ubuntu, but am not too sure what the better programs are. I am sorry if something like this has been posted before, but I would like advice as to what to use. I have two laptops and a desktop and want to get away from Windows XP and Vista if possible. Below are programs I either use or would like to use under Windows. Does anybody know what the best equivalents are under this 'Ubuntu'?:

Microsoft Word 2003 (most compatible for long, complex documents?)
Microsoft Excel 2003
Microsoft Outlook 2003
Microsoft Frontpage 2003

Nero Burning ROM
AutoGordian Knot (fantastic prog)
KMPlayer
Windows Media Center
DVD Shrink
DVD Decrypter
ConvertXtoDVD
Womble MPEG Video Wizard DVD
ACDSee
"Eric's Movie Database"

Comodo Firewall Pro
Rising Antivirus
VirtualBox
WinRAR
uTorrent


I think that's everything I'll ever need! I hope you understand how confusing this all is for the average user, but I do look forward to your response.

(While posting this thread, I wasn't sure about all the ubuntu, kubuntu, xubuntus - is there a difference? Should I be using something else or am I in the right place -- sorry if I'm not!)

8o)   thanks in advance,
Chris


[Click here for the differences between the *buntus]("http://www.google.com")

All of the Ms Office Suite is basically the same as the Open Office Suite. So you can use that...


-Virtualbox = Virtualbox OSE 
-Nero burning software = Brasero Disk burning
-KMPlayer = Mplayer
-Encryption/Decription Software = A lot to choose from. Google it.
-No need for Antivirus
-Not really a need for a firewall.
-Winrar = Standard compression tools that come with the defualt installation of Ubuntu.
-utorrent = Lots of options but i prefer Transmission

---

### Post by ninjapirate89 on 2009-04-11
> Comodo Firewall Pro
Rising Antivirus
VirtualBox
WinRAR
uTorrent

You don't really need a firewall or antivirus in linux.
Virtualbox will work just fine.
I use PeaZip to replace WinRAR.
I use Transmission for torrents.


Edit -> I was beat to it on three out of four! :)

---

### Post by HereInOz on 2009-04-11
Here's a link on how to install DVDShrink using Wine

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by Zulu-Zeffir on 2009-04-11
Nero = Check out K3b
DVD/Burning/Converting etc = Devede
VirtualBox is available for linux
The list could go on forever....

Basically I've found everything I can do with Windows I can do the same if not better with Linux (not just Ubuntu either).  It's all about what you want to do and how much you want to learn. 

In regards to the different Ubuntu distros you mentioned (ubuntu, kubuntu, xubuntus) they are different Desktop Managers.

Kubuntu (KDE)  -- said to be more window user transition friendly 
Ubuntu (Gnome) -- My preference
Xubuntu (XFCE) -- nice lightweight gui (my second preference on dated hardware)

Don't be lazy, google more.. it's your friend. ;)

---

### Post by lykwydchykyn on 2009-04-11
This site is a useful resource:

[http://www.osalt.com/](http://www.osalt.com/)

---

### Post by Sef on 2009-04-12
> You don't really need a firewall or antivirus in linux.

Not quite correct.   You need a firewall.  Ubuntu has one installed by default because it, like all operating systems, can be hacked.   It is harder to hack than Windows, but it can be done.   There are GNU/Linux botnets.

An anti-virus is needed if you run an email client.   You don't want to send a message that has a Windows virus attached to it.

---

### Post by defaultusername on 2009-04-12
chris.willis,

> 
Microsoft Word 2003 (most compatible for long, complex documents?)
Microsoft Excel 2003
Microsoft Outlook 2003
Microsoft Frontpage 2003


OpenOffice.org is the primary choice for an OSS office suite. KOffice is another option.

> Nero Burning ROM
AutoGordian Knot (fantastic prog)
KMPlayer
Windows Media Center
DVD Shrink
DVD Decrypter
ConvertXtoDVD
Womble MPEG Video Wizard DVD
ACDSee
"Eric's Movie Database"


Unfortunately, there really isn't a whole lot to replace the functionality of Nero in one package. If you're looking into KOffice and already use KDE, take a look at K3b. Recent editions of Ubuntu include "Brasero" which I find adequate for writing ISOs and audio discs.

Linux has several choices for media players: For music, Amarok (kde), Rhythmbox (gnome), and XMMS (low-memory solution). There's also the barebones alsaplayer that will give suitable audio playback without any extras. Codecs are pretty easy to find with Synaptic. 

DVD playback on open platforms has been a subject of much legal debate. VLC/libdvdcss should handle CSS decryption.

> Comodo Firewall Pro
Rising Antivirus
VirtualBox
WinRAR
uTorrent

iptables, the default choice, is included with Ubuntu. There are graphical applications that simply the configuration, too, but I can't name any off the top of my head. Anti-virus software is unnecessary. I find that most malware is either undetected or makes quick work in disabling whatever kind of protective framework is running. Instead, look into projects such as SELinux. Wireshark is a good tool for monitoring activity on an interface. Filters give you a massive amount of control in recognizing suspicious activity. Chkrootkit is great for detecting infected binaries.

There is already RAR support built into Ubuntu.

uTorrent is irreplacable, IMO. I use WINE to run uTorrent because of my general dissatisfaction with available torrent clients (for all platforms!).

Anyway, hope that helps.

---

### Post by DeMus on 2009-04-12
> **chris.willis said:**
> Hi there,

I am making the transition to Ubuntu, but am not too sure what the better programs are. I am sorry if something like this has been posted before, but I would like advice as to what to use. I have two laptops and a desktop and want to get away from Windows XP and Vista if possible. Below are programs I either use or would like to use under Windows. Does anybody know what the best equivalents are under this 'Ubuntu'?:

Microsoft Word 2003 (most compatible for long, complex documents?)
Microsoft Excel 2003
Microsoft Outlook 2003
Microsoft Frontpage 2003

Nero Burning ROM
AutoGordian Knot (fantastic prog)
KMPlayer
Windows Media Center
DVD Shrink
DVD Decrypter
ConvertXtoDVD
Womble MPEG Video Wizard DVD
ACDSee
"Eric's Movie Database"

Comodo Firewall Pro
Rising Antivirus
VirtualBox
WinRAR
uTorrent


I think that's everything I'll ever need! I hope you understand how confusing this all is for the average user, but I do look forward to your response.

(While posting this thread, I wasn't sure about all the ubuntu, kubuntu, xubuntus - is there a difference? Should I be using something else or am I in the right place -- sorry if I'm not!)

8o)   thanks in advance,
Chris

Try this site to find the programs you are looking for:
[http://linuxappfinder.com/alternatives?search_text=]("http://linuxappfinder.com/alternatives?search_text=")

In the search field type in the name of the Windows program and be amazed how many equivalents there are in Linux.
Have fun

---

### Post by chris.willis on 2009-04-12
Many thanks for all this stuff - lots of information to look into. Currently reading the Ubuntu handbook as well. I thought Linux would be complicated but I think it's much easier than I expected, although I'm still unclear about the different distributions, but believe it's about the difference in desktop environments but the same programs can be used. I also read about Mythbuntu which looks good for my main computer, although the site appears to be down.

Anyhow, lots to learn before I report back and let people know what I found - perhaps it will help others. Some useful sites.

Wonderful community - thanks to everybody for the pointers. I look forward to the new release, and getting to know Linux in much more detail!
Chris

---

### Post by defaultusername on 2009-04-12
chris.willis,

GNU/Linux and Ubuntu are both remarkably well-designed and scientific. Luckily, Ubuntu has made Linux accessible by making it easy and intuitive without sacrificing the underlying capabilities.

Bon voyage, happy hacking :-)

---

### Post by Jpardue on 2009-04-12
> **defaultusername said:**
> chris.willis,

GNU/Linux and Ubuntu are both remarkably well-designed and scientific. Luckily, Ubuntu has made Linux accessible by making it easy and intuitive without sacrificing the underlying capabilities.

Bon voyage, happy hacking :-)
The awesome part about Ubuntu is it's user friendly imo. All you need to do is just follow all of the links these helpful people have listed and read, read, read, read. I think the more you know about linux the easier it becomes and can become even easier to use and more intuitive than Windows.

---

### Post by DeMus on 2009-04-12
> **Jpardue said:**
> The awesome part about Ubuntu is it's user friendly imo. All you need to do is just follow all of the links these helpful people have listed and read, read, read, read. I think the more you know about linux the easier it becomes and can become even easier to use and more intuitive than Windows.

If you are a "simple" computer user then I still think Windows is your program. Buy a pre-installed computer, hook it on and use it.

When you are more, when you want to change things, when you want to choose things, when you want to learn things, then Linux is the one you are looking for. When computing is supposed to be fun, use Linux.

As you can see here on this forum there ae many people willing to lend a helping hand to those just starting, still learning, still investigating.

And to be honest, well I am Dutch so maybe that explains it, I also like the fact it is for free. Remember the days when you used Windows? Did you use free software, did you use software you paid for, or did you use "free" software you had to pay for, in other words illegal stuff. Now all I use is for free and it is still legal to use. Fantastic.

---

### Post by chris.willis on 2009-04-12
I think there's a lot of good quality freeware stuff for Windows - many of the programs I listed in my first post are freeware and just as good, if not better, than is commercial counterpart. I think that holds a big attraction to everybody. Like many people, I thought Linux was just terminal commands until I Googled screenshots, then I started to get serious. I briefly used Ubuntu 8.10 under a virtual machine (Virtualbox) and will experiment for the next week til I install Jackalope on my laptop. Looking forward to this 'Mythbuntu' distribution. I'm still going through the sites for alternative freewares - surprising how much are both Linux and Windows!

There's so many programs. Still not sure which ones to use. Maybe all of them, I suppose, since they're easily available.

---

### Post by chris.willis on 2009-04-13
So - does Linux need a firewall? Some posters are split on the subject. I read Linux works on iptables; predefined rules, but to configure in and outgoings you need a gui-enabled firewall like Firestarter. I understand the part about viruses and malware - what a big PLUS for Linux not having so many viruses!

What a huge collection of software. Thank heaven for big hard drives.

Thanks very much for everybody's suggestions on specific software. it's always easier to start with recommendations than to go through sites and pick some at random, although the latter will be interesting to do when I'm up to speed with everything.

The Ubuntu Pocket Guide is a very good guide for us gnubies ;) lol.

---

### Post by hyper_ch on 2009-04-13
are you behind a router? then you probably don't need to mess around with iptables. Even if you are not, you probably still odn't need to mess around with iptables.

---

### Post by chris.willis on 2009-04-13
I use a [DSL502-T DLink]("http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=1&Sub2=2&PID=48") router connected to a wireless Belkin router firewall enabled (always use a firewall in Windows).

I think I'll install Firestarter til I learn more. Worst thing it can do is add a few seconds to boot time. I hear boot speed is vastly improved with Jackalope to compensate.

Many thanks for all your responses. Never expected so many people to help me and I'm glad I'm wrong.

---

### Post by hyper_ch on 2009-04-13
before you install firestarter have a look at the sticky threads in the security section. And just installing stuff without knowing what it does and how it affects your system is probably one of the worst things you can do from a security point of view - this is also true for firestarter et al.

---

### Post by futz on 2009-04-13
> **defaultusername said:**
> uTorrent is irreplacable, IMO. I use WINE to run uTorrent because of my general dissatisfaction with available torrent clients (for all platforms!).
Try [KTorrent]("http://ktorrent.org/"). It's really good. I think it's as good as uTorrent, which I use on my Windoze boxes.

---

### Post by lisati on 2009-04-13
> **chris.willis said:**
> I use a [DSL502-T DLink]("http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=1&Sub2=2&PID=48") router connected to a wireless Belkin router firewall enabled (always use a firewall in Windows).

I think I'll install Firestarter til I learn more. Worst thing it can do is add a few seconds to boot time. I hear boot speed is vastly improved with Jackalope to compensate.

Many thanks for all your responses. Never expected so many people to help me and I'm glad I'm wrong.

I have a DSL-502T modem/router that I no longer use: if memory serves correctly it has some firewall capabilities.

---

### Post by chris.willis on 2009-04-13
Thanks hyper_ch. That's probably my Windows mindset. Sounds like it's a common concern with people making the switch. Thanks for pointing it out.

---

### Post by futz on 2009-04-13
> **chris.willis said:**
> Nero Burning ROM
K3b

-----------------------

> KMPlayer
Windows Media Center
Totem Xine

-----------------------

> ConvertXtoDVD
Devede (excellent - vastly improved over earlier versions)

-----------------------

> ACDSee
gThumb

-----------------------

> VirtualBox
VirtualBox

-----------------------

> uTorrent
KTorrent

---

### Post by chris.willis on 2009-04-13
This is great: I think my primary concern is Microsoft Office and getting it installed. I have to share lots of MS Word documents at work etc, many quite complex - until I can retire I'm stuck with it, but the forums are a great help! So many solutions rather than problems. Thanks to all!

---

### Post by futz on 2009-04-13
> **chris.willis said:**
> This is great: I think my primary concern is Microsoft Office and getting it installed. I have to share lots of MS Word documents at work etc, many quite complex - until I can retire I'm stuck with it, but the forums are a great help! So many solutions rather than problems. Thanks to all!
Open Office will read and write MS Office files. You may possibly run into some small differences on the outputs though. Depends on what you're doing. Test and see how it works.

I recently rebuilt my business/accounting box (running Windoze, for the accounting software). I dumped MS Office and went with Open Office and Thunderbird for email. After a couple weeks using it I don't miss MS Office at all!

I would have switched to Ubuntu, but moving my accounting to another program is a huge job, so I stick with crappy Simply Accounting.

---

### Post by Topsiho on 2009-04-13
Seems to be off topic, but a firewall was mentioned, and ip tables, firestarter, and a modem/router with a firewall.

If you want to ***know*** that you are protected you can just visit

grc.com

and use ShieldsUp  (need to click on ShieldUp in two places).
All my ports are green :)


Read what Gibson writes on this page, is OK for Windows and also for any other Operating System ...

And it was already mentioned above, but possibly not loud and clear enough: using wine (and there are other programs, some not free) you can use many Windows programs, probably with a speed penalty.

Greets,

Topsiho

---

### Post by chris.willis on 2009-04-14
Definitely not off topic. This is all great stuff and I'm enjoying fiddling around with stuff - and looking forward to fiddling more when I install Jaunty.

I think you have all answered the basic questions for me. There are a number of forum posts about what software is the best, some confusing, but I think I have more enough to set me up, and I've read enough to understand more about the Linux mentality. I've even poked at the command lines with some success, surprised that it's not that hard to grab the basics.

Thank you all for sharing your time and experiences. I'm looking forward to testing lots of programs to see what best works for me. I think the next week is experiment, experiment, experiment with MS Word v OpenOffice which is the most critical part, and worst case scenario, for work docs, I just use Wine or a virtual machine. What a great system this Ubuntu is.

On another note, off topic, it's amazing how many friends and colleagues I have talked to who are dead-set against Linux even though they know nothing about it - wouldn't even try a live CD. Their general opinion seems to be that only Windows exists. Everything else is esoteric and mysterious.

So, I'll close this thread. Thanks again, and I'll probably see you around sometime!

Best regards
Chris

---

### Post by chris.willis on 2009-04-25
Aah, my initial post seems so long ago ...

Microsoft Word 2003 - installed under Wine. Brilliant!
Microsoft Excel 2003 - installed under Wine, but OpenOffice used instead
Microsoft Outlook 2003 - Evolution. Great program!
Microsoft Frontpage 2003 - installed under Wine, but Komposer is good too

Nero Burning ROM - already installed with Jaunty Jackalope.
AutoGordian Knot (fantastic prog) - Don't know yet.
KMPlayer - Totem but install 'codecs' as required.
Windows Media Center - not sure yet. Myth sounds good.
DVD Shrink - installed under Wine
DVD Decrypter - installed under Wine
ConvertXtoDVD - not sure yet.
Womble MPEG Video Wizard DVD - not sure yet.
ACDSee - already installed with Jaunty
"Eric's Movie Database" - installed under Wine

Comodo Firewall Pro - not required
Rising Antivirus - not required
VirtualBox - same
WinRAR - installed under Wine
uTorrent - ktorrent, or utorrent installed under Wine

Sorry if half the above are all installed under Wine, but it's a fantastic program.

---

