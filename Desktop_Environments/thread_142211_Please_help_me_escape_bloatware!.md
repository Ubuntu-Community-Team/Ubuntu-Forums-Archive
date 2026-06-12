---
title: "Please help me escape bloatware!"
date: 2006-03-10
forum: Desktop Environments
---

### Post by Jimage on 2006-03-10
I've been reading up on all these different approaches to getting Ubuntu (in fact, *any* Linux distro) running on "old" computer with a decent interface. The most appropriate I've found was [Installation/LowMemorySystems]("https://wiki.ubuntu.com/Installation/LowMemorySystems"). I followed the instructions there, but apt-get tells me it can't find the icewm package. And if I cut that and menu (which also complains) out of the list, I'm told some Perl package needs to be downloaded that's gonna take another 280Mb of my HDD!

Basically, I just want an OS that boots up quick and isn't going to eat up my HDD, RAM and CPU. In addition, it needs to be a comfortable interface that allows me to use the mouse and keyboard interchangably as Windows does. Win98's simplicity, XP's power combined with Linux's stability.

One of the many reasons I want to leave the Microsoft world is to escape bloatware, which looks to increase yet again with the advent of Vista, but everywhere I seem to look in Linux Land, I'm faced with the same issue! And so often the response to "Old computer?" is "Buy a new one!"

Speedy, small, comfortable and responsive, an operating sytem that boots in no time and flies along no matter the hardware. How can it be done? I refuse to put Linux on my 3200+ and 3700+ until I can be sure it runs comfortably on a PII or less. Then I can start praising Linux and helping others make the shift--and as an added bonus you'll have another Linux game developer to add to the collection.

Thankye muchly for any help y'all can offer.

---

### Post by RAOF on 2006-03-10
You could probably just install Xubuntu - that's Ubuntu, but with an XFCE desktop which is apparently very resource-light.  Run a "server" install, and once you can log in to the command line, you should be able to run **sudo aptitude install xubuntu-desktop**.

---

### Post by Jimage on 2006-03-10
I'll give that a shot, however I'm not too sure about Xfce. I've had Zenwalk installed previously which uses it; it lagged out my (8Mb) graphics card, and I found it incredibly unintuitive. Perhaps there are some settings I can change, such as key configurations, ie. Ctrl+Esc to open the menu for starters.

IceWM sounds more appropriate, and faster, but I haven't been able to get it installed on anything yet.

**Edit:** aptitude tells me it can't find the "xubuntu-desktop" package. apt-get had started downloading something earlier, so I'm fairly certain the network's functioning...

---

### Post by Jimage on 2006-03-10
Oh, God... it's horrible! Aaaagh. Is there something I'm missing, or is IceWM simply a bunch of grey squares!? Ctrl+Esc to open the menu is a good thing, but the menu makes me want to hurl, and none of the themes seem to be making any difference. Maybe I've done something wrong. I hope so...

It uses 50Mb or so less memory, but still the entire 128Mb is almost full. Gah. This OS quest is really starting to get on my nerves.

Obviously, I worked out to uncomment the two lines for the Universe repository, and the past 2.5 hours I've been downloading the necessary packages for IceWM to run. Doesn't seem to be worth it except as a "don't do that again" learning experience.

*sigh* Oh, well... I'll keep mindlessly swimming around the Web in search of a suitable Linux configuration.

---

### Post by hw-tph on 2006-03-10
IceWM can be configured to look really well. So can fvwm, which is most likely the most configurable and powerful window manager out there (and most [beautiful](http://www.theskyiscrape.com/scott/fvwm_green.png)?) - but it requires some tinkering.

Your RAM is there to be used. Linux will cache everything aggressively in memory to increase performance. You might want to read [this](http://gentoo-wiki.com/FAQ_Linux_Memory_Management).

Trying - and failing - is a learning experience. Learn how to use Linux and you won't be sorry, but it will take some time.


Håkan

---

### Post by Djartklom on 2006-03-10
<i>Basically, I just want an OS that boots up quick and isn't going to eat up my HDD, RAM and CPU. In addition, it needs to be a comfortable interface that allows me to use the mouse and keyboard interchangably as Windows does. Win98's simplicity, XP's power combined with Linux's stability.</i>

Try Vector Linux.  It is a very well-implemented desktop-oriented distro that runs well on older hardware.  Also, check out the new Elive 4.2 cd, which is an installable Debian variant with the amazing Enlightenment desktop environment.

---

### Post by Jimage on 2006-03-10
Thankyou! That is by far the most useful reply I've received on a Linux forum. I was unaware of Linux's RAM dynamics, and that FVWM screenshot looks extremely tasty.

So, if it's not overloaded RAM that makes things unresponsive, what are the issues I should be addressing? And where would I start looking for info about customising IceWM? Is FVWM faster as well as potentially better looking?

Btw, where do these packages get saved to from the repository before being installed? I'd like to store them somewhere so I don't need to keep downloading them for every computer I install on.

***Djartklom** Try Vector Linux*
I have a copy of that, but it crashes out on me for some reason whenever I attempt to install it. I don't remember the error, though. I may give it a whirl on another machine if you think it's really worth checking out.

ELive looks interesting... I'll keep that in mind if it works well installed to the HDD. I installed Enlightenment when I was running Zenwalk last week or so, and it was nice except for its mouse orientation and all the stuff floating around arbitrarily. However, I presume like Ice and FVWM it is customisable but takes some effort.

---

### Post by hw-tph on 2006-03-10
Getting fvwm to look *that* good actually requires an incredible amount of work. So it's good to know that some kind souls post their configs at the [fvwm forum](http://fvwm.lair.be/). In default configuration it looks absolutely horrible but is extremely quick. Another option I would like to suggest is [Openbox](http://www.openbox.org). I have used Openbox (along with a panel of some sort - usually fbpanel or pypanel) for years on both slow and fast machines. Openbox is very easy to configure and provides much better performance for slow machines than full-blown desktops like Gnome or KDE. There are some neat window decorations you can download if you wanto, and making your own isn't very hard either.

As for performance - disable the init scripts for services you don't use often. If you don't use Samba all the time, disable it. If you only use Apache and MySQL for occasional testing, disable them. If you don't use RAID or LVM, disable those scripts too. Ubuntu comes with a whole lot of scripts enabled that often are redundant to the user (I would appreciate if the Ubuntu debs for services such as Apache and MySQL would ask if they should be loaded on boot like most stock Debian packages do).

When you have disabled the services you don't need start looking at if you have DMA enabled for your hard drive, and perhaps try a different IO scheduler. I prefer the cfq scheduler ("completely fair queuing"), which suits both my laptops and my desktop pretty well. The system feels a bit more responsive when using cfq. To enable the cfq scheduler, pass "elevator=cfq" to the kernel at boot. You can edit /boot/grub/menu.lst and add it to the kernel line and the kopt line (do NOT uncomment the kopt= line, just append "elevator=cfq" to the options already there - without the quotes of course).


Håkan

---

### Post by az on 2006-03-10
[QUOTE=Jimage]Oh, God... it's horrible! Aaaagh. Is there something I'm missing, or is IceWM simply a bunch of grey squares!? Ctrl+Esc to open the menu is a good thing, but the menu makes me want to hurl, and none of the themes seem to be making any difference. Maybe I've done something wrong. I hope so....[/QUOTE]

Exactly what packages did you install?  Did you change the session to icewm in GDM?  Are you using GDM (the login greeter thing)?  Did you install the menu package?

I wonder if the grey squares are becuase you don't have the fonts properly configured.  Did you install x-window-system-core?

[QUOTE=Jimage]It uses 50Mb or so less memory, but still the entire 128Mb is almost full. Gah. This OS quest is really starting to get on my nerves..[/QUOTE]

128 megs is a lot for icewm.  Don't worry.

[QUOTE=Jimage]Obviously, I worked out to uncomment the two lines for the Universe repository, and the past 2.5 hours I've been downloading the necessary packages for IceWM to run. Doesn't seem to be worth it except as a "don't do that again" learning experience..[/QUOTE]

No.  Icewm is something like a 2.2 meg download.  You are also downloading all the security updates and bugfixed packages from the past five months.

[QUOTE=Jimage]*sigh* Oh, well... I'll keep mindlessly swimming around the Web in search of a suitable Linux configuration.[/QUOTE]

Just shoot any and all questions you have here....

---

### Post by Jimage on 2006-03-10
[QUOTE="hw-tph"]Another option I would like to suggest is Openbox.[/QUOTE]
I've read a bit about this, and it sounds like an interesting possibility. I'll certainly try it out.

[QUOTE="hw-tph"]As for performance - disable the init scripts for services you don't use often.[/QUOTE]
I'll look into that. I'm not sure where these are kept, but it shouldn't be too hard to find a tutorial or something about it.

[QUOTE="azz"]Exactly what packages did you install?[/QUOTE]
Basically the same as it told me [here]("https://wiki.ubuntu.com/Installation/LowMemorySystems"), minus Firefox and Abiword, the former of which I installed from the CD afterwards.
```
sudo apt-get install gdm x-window-system-core xterm icewm menu synaptic
```

However, I did try to modify the fonts and most of the options were greyed out, so I might have done something stupid along the way.

What I mean by 'grey squares' is that the taskbar and menu look like a bunch of 16-colour palette command buttons trying to look 3D... and failing miserably. Of course, the cramped, narrow font doesn't do much to alleviate this either.

Btw, is there anything I need to modify to setup my graphics card properly? It's only an onboard 8Mb SIS 620, but such hardware used to fly on Win98, and even XP, when I had it installed on a 350/128Mb/8MbGFX five years ago, even on resolutions up to 1600x1280!

When I drag windows around the place there's a delay and a lot of tearing before the screen is redrawn. I suspect a driver issue because XP does a similar thing for many cards when running its generic graphics driver--once the proper driver is installed the display runs flawlessly.

Two other minor things:
How do I get XFM running after apt-getting it? And why does the Ubuntu loading banner remain even after the window manager has loaded? It gets to the third icon and just sits there.

Thanks immensely so far. This place rocks.

---

### Post by az on 2006-03-10
[QUOTE=Jimage]
When I drag windows around the place there's a delay and a lot of tearing before the screen is redrawn. I suspect a driver issue because XP does a similar thing for many cards when running its generic graphics driver--once the proper driver is installed the display runs flawlessly.[/QUOTE]

I get that when I run things on a box with less than 128 megs of ram.  Using anything better than a pentium II (333MHz) with 128 megs of ram, it seems to go away.

[QUOTE=Jimage]
Two other minor things:
How do I get XFM running after apt-getting it? And why does the Ubuntu loading banner remain even after the window manager has loaded? It gets to the third icon and just sits there.[/QUOTE]

Log out and before logging back in, pick the icewm session (Click OPTIONS) of any other session you want to run.  You are trying to load the default gnome session (which you do not have installed) and that's why you get the banner.

If you have not already done that, it may solve you other problem, actually.

---

### Post by Jimage on 2006-03-10
[quote="azz"]Log out and before logging back in, pick the icewm session (Click OPTIONS)[/quote]I assume you meant 'Session'? Seems to have worked--the banner no longer comes up. I found XFM in the menu structure, but it doesn't do anything. Same goes for several other apps, though Firefox and xterm work.

---

### Post by az on 2006-03-10
[QUOTE=Jimage]I assume you meant 'Session'? Seems to have worked--the banner no longer comes up. I found XFM in the menu structure, but it doesn't do anything. Same goes for several other apps, though Firefox and xterm work.[/QUOTE]
Fire up xterm and type
xfm
to see what error you get.

---

### Post by Jimage on 2006-03-10
Tells me, 'command not found'.

---

### Post by az on 2006-03-11
dpkg -L xfm

It's found in:
/usr/X11R6/bin/xfm

I dunno why the menu item is wrong...  Maybe it assumes it is in your path.  Maybe a bug report is in order.


I would suggest you try xfe or rox-filer, though...  Much nicer...

---

### Post by hw-tph on 2006-03-11
> I'll look into that. I'm not sure where these are kept, but it shouldn't be too hard to find a tutorial or something about it.
They are located in /etc/init.d. Read the Debian Policy Manual (**sudo apt-get install debian-policy**), chapter 9.3 - [System run levels and init.d scripts](http://www.us.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit). The debian-policy is a very good reference and lets you understand Debian (and in extension - Ubuntu, since it is Debian) as opposed to Linux in general.

You can easily manipulate what services run at what runlevels using **update-rc.d**. There are also more or less graphical applications that can help - like [bum](http://www.marzocca.net/linux/bum.html) - but knowing how to do it from the command line can be a real life saver.


Håkan

---

### Post by Jimage on 2006-03-11
Right, I've found xfm. I'll find a way to edit the menu entry. Hopefully it's possible to eventually set one of these window managers to allow editing and dragging of the menu items as per Explorer.

[quote="Håkan"]The debian-policy is a very good reference and lets you understand Debian (and in extension - Ubuntu, since it is Debian) as opposed to Linux in general.[/quote]
Thanks, I'll be sure to grab that.

I think I've got a good idea of how to go ahead with tweaking this thing now. Thankye once again.

---

### Post by OfficeLinebacker on 2006-03-12
I just wanted to mention that I am trying to install Ubuntu on a machine with a spare HD I have laying around...a 1.6GB WD Caviar.  Obviously too small for Gnome or KDE, but probably big enough for one of the smaller window managers.
 
It's got a Celeron 850MHz and ~380MB of RAM, but regular GNOME is certainly far from "snappy."
 
I'm having trouble figuring out which window manager to use.  I'm fairly new to Linux and am comfortable in Gnome, but HATE KDE.  I think just cos I tried Ubuntu before I tried Kubuntu so Gnome just "feels" better.
 
I'm thinking of just going with Xubuntu cos it seems like the easiest optin.  I always seem to find a way to bugger things up.
 
I may try to use this machine as a netowrk bridge (pick up a wireless signal on a WS card and then "share" it through the ethernet port, a la Windows connection sharing.  Maybe if I find a bigger HD eventually run a squid proxy or something on it.  Also the machine will be folding 24x7, hopefully :)
 
ANyways as I wait for the "server" install to complete any suggestions welcome.

---

### Post by OfficeLinebacker on 2006-03-12
Well, I decided to go with Xubuntu-desktop cos it seems like there are less opportunities for messing up:
 
[https://wiki.ubuntu.com/InstallingXubuntu]("https://wiki.ubuntu.com/InstallingXubuntu")
 
I'll probably eschew GDM but we'll see.

---

### Post by Teroedni on 2006-03-12
> It's got a Celeron 850MHz and ~380MB of RAM, but regular GNOME is certainly far from "snappy."

:O

A Celeron 850 mhz should do fine.



Im running Dapper Drake (devel) on a Pentium 350mhz computer with 320mb ram and a Ati rage 8mb graphics card:P

This machine is quite snappy using latest  gnome, and the memory use after been started lies on 83mb:)

I would recommend that you try a Dapper Drake Flight 5.
But just keep in mind that Dapper is development version, and therefore s not recomende for production use.

Flight cd 5 info here
[http://www.ubuntu.com/testing/flight5](http://www.ubuntu.com/testing/flight5)

Downloads
[http://cdimage.ubuntu.com/releases/dapper/flight-5/](http://cdimage.ubuntu.com/releases/dapper/flight-5/)

---

### Post by OfficeLinebacker on 2006-03-12
Damn, flight 5 already?  I just burned a couple of Flight 4 CDs
 
Anyway already done installing Xubuntu, rebooting now
 
also, I totally grok the "bloatware" sentiment.  It automatically installed stuff like cups, which is a printing thing, right?  I don't plan on ever hooking up this machine to a printer.

---

### Post by OfficeLinebacker on 2006-03-12
aaaaaaaaaaaaaaaaaand it didn't work
 
This crap is really starting to frustrate me.  I mean this shouldn't be rocket science.  Basically after logging in I type startxfce4 and the screen flashes a couple of times and then light grey.  In other words, a complete waste of the past couple of hours.

---

### Post by OfficeLinebacker on 2006-03-12
[quote=Teroedni]:O
 
A Celeron 850 mhz should do fine.
 
 
 
Im running Dapper Drake (devel) on a Pentium 350mhz computer with 320mb ram and a Ati rage 8mb graphics card:P
 
This machine is quite snappy using latest gnome, and the memory use after been started lies on 83mb:)
 
I would recommend that you try a Dapper Drake Flight 5.
But just keep in mind that Dapper is development version, and therefore s not recomende for production use.
 
Flight cd 5 info here
[http://www.ubuntu.com/testing/flight5]("http://www.ubuntu.com/testing/flight5")
 
Downloads
[http://cdimage.ubuntu.com/releases/dapper/flight-5/]("http://cdimage.ubuntu.com/releases/dapper/flight-5/")[/quote]
 
What kind of hard drive are you running?

---

### Post by az on 2006-03-12
[QUOTE=OfficeLinebacker]aaaaaaaaaaaaaaaaaand it didn't work
 
This crap is really starting to frustrate me.  I mean this shouldn't be rocket science.  Basically after logging in I type startxfce4 and the screen flashes a couple of times and then light grey.  In other words, a complete waste of the past couple of hours.[/QUOTE]

What happens when you type

sudo apt-get install x-window-system-core?

---

### Post by OfficeLinebacker on 2006-03-12
[quote=azz]What happens when you type

sudo apt-get install x-window-system-core?[/quote]

azz,

It's already over.  I am back on regular Ubuntu.  It is soooooooo sloooooooow, though.  top shows Xorg taking up about 10-10% of CPU just sitting there.  When I minimize windows, they have this weird strobing black frame effect.  

The machine is some kind of retread HP, I believe with the Celeron as noted and onboard videao...Intel 810 Chipset I believe but I am not certain.  

Oh wait the Mobo is a CUW-AM.  The font looks like Asus.  Small form factor looking thing. 

384MB RAM.

Any thoughts?

P.S.  Feel free to tell me to start my own thread.

---

### Post by az on 2006-03-12
[QUOTE=OfficeLinebacker]azz,

It's already over.  I am back on regular Ubuntu.  

Any thoughts?

P.S.  Feel free to tell me to start my own thread.[/QUOTE]


Use synaptic to enable universe, than update and install icewm and menu.

Log out and then back in using the icewm session.  This should be really fast.  You will have all the ubuntu tools needed via the menus.

You can even tell icewm to run things like gnome-volume-manager when you startup by editing the .startup script in your ./.icewm folder in your home drive.  That way, you get automatically mounted pendrives and cdroms...

---

### Post by OfficeLinebacker on 2006-03-12
OK, I'm gam e:)

sudo apt-get install icewm menu

just got done cranking...time to restart~!

---

### Post by OfficeLinebacker on 2006-03-12
Hey, I am in icewm now.  It's a litte snappier, but still oddly slow.

I think it may have to do with the onboard video getting assigned a certain amount of the system RAM for video, and I think I remember something about being able to tweak that value.

--Ok tried reconfig'ing xorg, but to no avail.  I did leave the default value for video RAM however.  Since I have 386 MB I may try giving the video 32 meg or so and see how that goes.

---

### Post by stabface on 2006-03-12
Vector is quite good for older systems if you know what you are doing. I tried vector for me first distro and got really frustrated with linux as a whole. But it did get to run and play music browse the net on some beasts of old systems.

---

### Post by OfficeLinebacker on 2006-03-12
I'm thinking it's the intel810e chipset.  There's a driver for in in X but it cannibalizes memory from regular RAM, and it's basically a shitty achitecture.  
 
I should do a search.

---

### Post by az on 2006-03-14
[QUOTE=OfficeLinebacker]I'm thinking it's the intel810e chipset.  There's a driver for in in X but it cannibalizes memory from regular RAM, and it's basically a shitty achitecture.  
 
I should do a search.[/QUOTE]
Your video card should not be making your system slow.  The only thing that would be slow on the desktop because of your video card is 3d-accelerated games and screensavers and stuff - opening and moving windows is not slowed down by this.  All the 2d stuff is as fast as it can be, whether you are using a mega-powerful gamer card or a small pci 4meg video card.  

You should be able to run icem with less than 128 megs of ram.

On a side note, you can change the amount of memory your onboard video takes up in the bios, not by reconfiguring X.

So, what do you mean by slow?  When you boot Windows, Internet explorer is loaded into memory.  Firefox is not loaded into memory in Ubuntu until you click on it - is this what you mean?
Despite that, I find my pIII 700 desktop more useable (fewer pauses) running Ubuntu than my fater-in-law's 2.4Gig Celeron running XP.

---

### Post by Teroedni on 2006-03-14
[QUOTE=OfficeLinebacker]What kind of hard drive are you running?[/QUOTE]
Scsi with maximum 80mb .I think its on 5gb. Bought it Cheap....Really cheap;)

---

### Post by OfficeLinebacker on 2006-03-14
azz,
 
First of all thanks for taking a personal interest in my case.
 
What I mean by slow, is the artifacts from moving a window where the background doesn't get immediately repainted when you move the window.  It's like you're smearing it (sorry there is probably a word for this).  Also, in FF, when I hit the New Reply button, the area where the text box would appear on the next page kind of freezes and shows that area of the previous page for a bit before the page loads entirely.
 
Finally, whenever minimizing windows, you see these black frames that get progressively smaller and then disppear into the task bar area into which it's minimized.  That's probably the most notable "slowness" to it.  It looks kind of jerky and inconsistent.
 
I hope this makes sense.

---

### Post by Dragineez on 2006-03-14
I have ubuntu running on a P-I 200Mhz, 128MB RAM, Real3D i740 8MB PCI Video card, and 4GB HD. I put xfce on it last night and it runs like a charm. Is it as fast as my P4? Of course not, but it is acceptable. I installed dillo to use as a lightweight browser. If there's anything I really want to look at I just paste the URL into Firefox - but I don't surf on that machine with FF.

Unless you're trying to run it on a 486, there shouldn't be any problem. Installation from apt or synaptic couldn't be easier. I haven't used icewm or flux, so it wouldn't be fair to comment on them - but I'm quite happy with xfce.

---

### Post by OfficeLinebacker on 2006-03-14
I'm afraid your video card trumps mine, thus making our situations uncomparable, dragineez.

---

### Post by gwilson on 2006-03-14
This is a rather odd discussion.

If you want to get Linux running on a system with low resources (which you don't actually specify) for the fun of it or to utilize old hardware, that's fine. Maybe try Damn Small Linux which is only a 50 MB download. You can add programs to it if you want to, and it's pretty slick.

If, as you say, you mainly want to install it on this other computer in order to test Linux out before putting it onto your newer computer, it begs a few questions.

First, you're not going to learn much about how Linux runs on a 3 GHz system by putting a barebones Linux distribution on this poor old hardware. What's the point?

Second, why is this such an either/or proposition? Your modern 3 GHz computer can easily run several operating systems with no problems. Why not just clear out some space on your hard drive to set up a partition you can install Ubuntu into and use GRUB to boot all operating systems? 

Third, Ubuntu, compared to other Linux distributions is a no-brainer to install and maintain. You can make it as bloated or as light as you want to simply by clicking a few boxes in Synaptic Package Manager. I just did a full install of Dapper Drake Gnome with a bunch of KDE add-on packages, and it used all of 4 gigs on my hard drive. Surely a 3 GHz system can spare 5 gigs for a full-blown Ubuntu installation, and then you would be able to see what it can do.

Finally, regarding download times, if you don't have at least a DSL connection to the internet, you won't be very happy with Linux if you are into trying new software and keeping packages up to date. Your dial-up modem would be running 24 hours a day. 

I probably missed the point here, somehow.  Right?  :-k 

GW

---

### Post by Taino on 2006-03-14
I like DamnSmallLinux [http://damnsmalllinux.org]("http://damnsmalllinux.org") for older machines that may have too much trouble running a Ubuntu distro.

Its a good Linux replacement for Win95 and Win98 on older machines and DamnSmallLinux is only a 50mb distro.
You should try and run Ubuntu if you can since it has so many more capabilities, But if your severely hardware limited, damnsmalllinux is a pretty good alternative.

---

### Post by OfficeLinebacker on 2006-03-14
dwilson, you talking to me or the OP?

Also, please see a related thread (where MY hardware is specified):

[http://www.ubuntuforums.org/showthread.php?t=143676](http://www.ubuntuforums.org/showthread.php?t=143676)

---

### Post by az on 2006-03-14
[QUOTE=OfficeLinebacker]
What I mean by slow, is the artifacts from moving a window where the background doesn't get immediately repainted when you move the window.  It's like you're smearing it (sorry there is probably a word for this).  Also, in FF, when I hit the New Reply button, the area where the text box would appear on the next page kind of freezes and shows that area of the previous page for a bit before the page loads entirely.[/QUOTE]

How slow?  How long do the artifacts stay there?  Less than a second or more than a few seconds?  In icewm, you got the cpu monitor on the bottom right.  Does it go up to 100 per cent and stay there until the artifacts go away?

Because this is something that I get on my P1 166 Mhz laptop with 96 megs of ram.  On a similar system to your's, Via C3, 733 mHz with 192 megs of ram, icewm was super-fast and did not show these symptoms.


 [QUOTE=OfficeLinebacker]
Finally, whenever minimizing windows, you see these black frames that get progressively smaller and then disppear into the task bar area into which it's minimized.  [/QUOTE]

That is an effect to let you know where the wondow got minimised to.  It is supposed to be onscreen for a second or two (enough for you to see it).  In seconds, how long can the lines stay there?

How much of your disk space is occupied?  If you disk is really really full (greater than 90 percent) you can take a big performance hit.  I really can't think of anything that is slowing down your system so much.

---

### Post by gwilson on 2006-03-15
[QUOTE=OfficeLinebacker]dwilson, you talking to me or the OP?

Also, please see a related thread (where MY hardware is specified):

[http://www.ubuntuforums.org/showthread.php?t=143676](http://www.ubuntuforums.org/showthread.php?t=143676)[/QUOTE]

To the original poster.

---

### Post by OfficeLinebacker on 2006-03-15
[quote=azz]How slow? How long do the artifacts stay there? Less than a second or more than a few seconds? In icewm, you got the cpu monitor on the bottom right. Does it go up to 100 per cent and stay there until the artifacts go away?
[/quote]
 
Hmm, I'd say maybe 2-3 seconds.  As for the CPU monitor, I have folding running and pegging the CPU all the time anyway, so I can't really tell what effects moving the window have.
 
[quote=azz]
Because this is something that I get on my P1 166 Mhz laptop with 96 megs of ram. On a similar system to your's, Via C3, 733 mHz with 192 megs of ram, icewm was super-fast and did not show these symptoms.
 
 
That is an effect to let you know where the wondow got minimised to. It is supposed to be onscreen for a second or two (enough for you to see it). In seconds, how long can the lines stay there?
[/quote]
 
glad I'm not the only one who misspells "window" like that on fora!  :mrgreen: 
 
As far as the time it takes, again 2-3 seconds is my best guess.  on my work computer (Athlon 64 running XP Pro), it takes almost as long, only with the blue top bar shrinking effect, but it's deliberate and you can tell it's SUPPOSED to be that way.  The irregularity of the effect in GNOME, plus my subjective perception, just *feels* like it's running up against some bottleneck.
 
[quote=some dude]
 
How much of your disk space is occupied? If you disk is really really full (greater than 90 percent) you can take a big performance hit. I really can't think of anything that is slowing down your system so much.[/quote]
 
I'll have to check on the disk, but pretty sure it's not 90% full.
 
Thanks again.

---

### Post by spetey on 2006-03-16
I'm really looking forward to an easy install of [Ubuntu Lite]("http://www.ubuntulite.org/").  I think it's an especially good alternative to the $100 computer projects for the less priveleged.  Given that it's hard just to *give away* old computer equipment, it seems to me a much better use of time and natural resources to make easy lightweight user-friendly OS's for old hardware than it is to try to make cheap new hardware.

Besides, I'd love to be able to keep using otherwise outdated computers in other rooms, or give them to relatives, or ...

---

### Post by OfficeLinebacker on 2006-03-17
Just wanted to say that MY problem was helped immensely by the suggestion to back down from 24 color mode to 16.  Apparently this allowed DRI to operate.  see:  [http://www.ubuntuforums.org/showthread.php?p=835664#post835664](http://www.ubuntuforums.org/showthread.php?p=835664#post835664)

---

### Post by Jimage on 2006-03-29
In response to gwilson:

I already consider XP much too bloated. I would prefer something the size of Windows 98 with Linux's security and stability. I would use 98se on this machine (I already use it on several other machines), except I prefer XP's taskbar and appearance, as well as NTFS capability. That's pretty much all there is that has me forking out this extra gig of HDD space to run XP over 98.

In fact, I'd use DOS for all my computers if it had a supported API and modern drivers. Linux is the next best thing in this regard.

Perhaps a slightly hungrier Linux OS would be more suitable for my 3GHz machines. However, I have a pile of equipment from the early- to mid-90s on which I'd like to be able to run something as comfortable as XP and as speedy as 98. I suppose that's what I'm really trying to do at the moment.

If I can manage to achieve such a thing, then I will have, by extension, an operating system that can run on my newer machines with practically no resource consumption. Then I can start putting some slightly hungrier software into action, building from the ground up rather than from some arbitrary collection offered to me by a given distro.

I don't use chunky office or imaging programs, or much of the other random junk that everyone seems to consider necessities these days. I will find or create software that suits my purposes once I have the basic OS functioning.

Oh, and there is no multiboot option as far as I'm concerned. I can do everything I need to in Windows. My aim is to find a way to do everything I need to in Linux. If I must still use Windows, even sparingly, there's no point to the exercise. Plus I really dislike waiting for computers to load, especially rebooting.

You have a point about the download times. It's certainly a chore on dial-up. I'll be getting DSL connected soon, though, so it won't be quite as much of an issue. Even so, if I'm upgrading several machines at once it would be preferable to not have to waste bandwidth and simply be able to copy across the downloaded packages from one machine to another.

Unfortunately, real-life stuff interfered with my Linuxing and I've stashed my machines away for a while. I have somewhere to start from when I get back into it again though, so thanky'all. hopefully I'll be able to accomplish my goal sometime this year.

---

### Post by OfficeLinebacker on 2006-03-29
If your'e willing to write your own software, it's not such a big step to just customize Linux into your own distribution.

---

### Post by LostBear on 2006-03-30
i too are trying to get some kind of useable system out of the too very old laptops i have. 

I have to say the best i have used is Damn Small linux on a low end machine. (i have a 350mhz amd k6-2 laptop with the standard 32mb of RAM. is a HiGrade Notino Mi3000)  and damnsmalllinux runs like a ferrari on it. uses only 11mb when idle. try pulling that off m$, i abandoned it coz i got fed up with trying to get my speedtouch working on it.

Speedtouch runs on ubuntu so im about to screw everything up by installing a lighter desktop like fwm. going to use other laptop wich isnt much better (pentium II 333mhz with 192 mb RAM)

Why am replying?? to point out an alternative to Damn Small (wich, lets face it, isnt pretty) .......slax. very small (~150mb ish) comes in several flavours (KillBill which is autoconfiged for using Wine...PopCorn which is already setup for watching dvds....Frodo wich is just a terminal, no graphical desktop....Slax Server which has everyhtin set up for running a web/mail/print server.)

ignore that it is a live cd and can be booted from a pen drive. it is possible to install to hd.

[http://slax.linux-live.org/download.php]("http://slax.linux-live.org/download.php")

theres my 2 pence worth.

---

### Post by localzuk on 2006-03-30
> I have folding running

Do you mean 'Folding At Home'? If so, I would advise turning it off until you have your problems sorted - that could be the issue...

---

### Post by bodhi.zazen on 2006-07-29
Small, fast distro you ask.

Try Arch Linux. Small, fast, and up to date.

Zenwalk is also an option.

Good luck

---

