---
title: "Anyone using gDesklets?"
date: 2005-04-29
forum: Desktop Environments
---

### Post by havesometea on 2005-04-29
I have looked at their website, downloaded the source, and attempted an install.  Their install instructions were woefully inadequate as they left out some packages.  

If you are running it can you please tell me how you got it running?  Or maybe point me to another sort of application similar to gDesklets...

TIA!

---

### Post by Joeb on 2005-04-29
I am using gdesklets.  I installed it from the repository.  But, most of the desklets for sensors are broke because they interface changed between versions of gdesklets.  If there are updated desklets with the sensors, they can be installed manually to get them to work.

What are the problems you are experiencing?

Joeb

---

### Post by havesometea on 2005-04-29
[QUOTE=Joeb]I am using gdesklets.  I installed it from the repository.  But, most of the desklets for sensors are broke because they interface changed between versions of gdesklets.  If there are updated desklets with the sensors, they can be installed manually to get them to work.

What are the problems you are experiencing?

Joeb[/QUOTE]

I don't know why I didn't think of trying to use apt-get.  DOH

bad newbie
bad newbie

Anyway...I tried the "Starter Bar" and it just gave me a blurry icon for my home directory.  Is that normal?

I also tried Corner Xmms and it puked.  Maybe I need an older version of it?

---

### Post by Fab on 2005-04-29
[QUOTE=havesometea]I have looked at their website, downloaded the source, and attempted an install.  Their install instructions were woefully inadequate as they left out some packages.  

If you are running it can you please tell me how you got it running?  Or maybe point me to another sort of application similar to gDesklets...

TIA![/QUOTE]
 i compiled from source, and yes, some packages arent mentioned in the README and INSTALL files, but all of them are available in the ubuntu repos
if you play around with it, it will work out :P

---

### Post by zee on 2005-04-29
tried, not worked with the hw sensors on my laptop, so i deleted them.

i've used the backports repository.

---

### Post by havesometea on 2005-04-29
This is one of the things that frustrates me about Linux.  In the Windows world there is a much easier method for installing applications.  You don't have to worry about this sort of library incompatibility as much.  

For instance...on my XP laptop I downloaded Konfabulator, installed it and had little desktop apps running in about 10 minutes.

I have been tinkering with this on Linux for about 6 hours and still nothing.

---

### Post by Fab on 2005-04-29
[QUOTE=havesometea]This is one of the things that frustrates me about Linux.  In the Windows world there is a much easier method for installing applications.  You don't have to worry about this sort of library incompatibility as much.  

For instance...on my XP laptop I downloaded Konfabulator, installed it and had little desktop apps running in about 10 minutes.

I have been tinkering with this on Linux for about 6 hours and still nothing.[/QUOTE]
 i suggest showing us the error messages from ./configure

---

### Post by Joeb on 2005-04-29
[QUOTE=zee]tried, not worked with the hw sensors on my laptop, so i deleted them.

i've used the backports repository.[/QUOTE]


Isn't the backports repository for Warty?  Why wouldn't you use the current repositories?  By not worked, did the gdesklet fail or did it not register anything?  If the desklet worked, but no data, then are you sure you installed and ran the lm-sensors?

Joeb

---

### Post by Joeb on 2005-04-29
[QUOTE=havesometea]I don't know why I didn't think of trying to use apt-get.  DOH

bad newbie
bad newbie

Anyway...I tried the "Starter Bar" and it just gave me a blurry icon for my home directory.  Is that normal?

I also tried Corner Xmms and it puked.  Maybe I need an older version of it?[/QUOTE]


I think by default the Starter Bar just gives you the icon for your home directory (although I don't recall it being blurry) and you must add other icons to it, to launch apps.  So, that might be normal.

I'm assuming that you have Xmms installed.  I wasn't aware of a problem with it, just the various sensors.  What version of gdesklets are you running?

Joeb

---

### Post by shakin on 2005-04-29
[QUOTE=havesometea]This is one of the things that frustrates me about Linux.  In the Windows world there is a much easier method for installing applications.  You don't have to worry about this sort of library incompatibility as much.  

For instance...on my XP laptop I downloaded Konfabulator, installed it and had little desktop apps running in about 10 minutes.

I have been tinkering with this on Linux for about 6 hours and still nothing.[/QUOTE]


Well, I ran 'apt-get install gdesklets' and it works fine, although some gdesklets are broken due to a problem with gdesklets itself. Starterbar, clock and many others work really well. Konfabulator is harder to install on Windows because you have to find the download and go through the installation wizard.

---

### Post by ssam on 2005-04-29
gdesklets is in the hoary universe

---

### Post by zee on 2005-04-29
[QUOTE=Joeb]I think by default the Starter Bar just gives you the icon for your home directory (although I don't recall it being blurry) and you must add other icons to it, to launch apps.  So, that might be normal.

I'm assuming that you have Xmms installed.  I wasn't aware of a problem with it, just the various sensors.  What version of gdesklets are you running?

Joeb[/QUOTE]
 to Joeb: the install went fine (as usual :-) ) but the desklet didn't find any hardware sensors. I've installed lm-sensors too.

it's probably just my laptop (Toshiba Satellite M30) and not something software related.

zee

---

### Post by pjack76 on 2005-04-29
[QUOTE=zee]to Joeb: the install went fine (as usual :-) ) but the desklet didn't find any hardware sensors. I've installed lm-sensors too.

it's probably just my laptop (Toshiba Satellite M30) and not something software related.

zee[/QUOTE]

The trick is, you should NOT install gdesklets3.4-data from the Hoary universe. The package description says you should, but this is not what you want to do. Almost none of the desklets contained in gdesklets-data work correctly. Frankly I think it should be removed from universe.

So if you've installed gdesklets-data, use Synaptic to remove it. You'll want to do a "Complete Removal".

To install individual gdesklets, you have to go to the website and download them individually. Save them to your desktop, run the gDesklet accessory, and drag the desklets you downloaded into the gDesklet accessory.

Then you can install them with ease.

I went through all of this last night, I'm composing a HOWTO that also lists which gDesklets from the website actually work. I should have that up tonight...

Hope that helps,

-Paul

---

### Post by Gary Powers on 2005-04-29
havesometea, did you get your gDesklets working yet?  If not, please holler and I will tell you a simple process (learned after struggling with them for six weeks).  Some of them in gDesklets-data do not work, but I think you will able to get pretty much what you want.  I am running on them on three machines, two ubuntu and one vidalinux.

Gary

---

### Post by 23meg on 2005-04-29
what would you all say about the overall cpu power hogging of gdesklets? i've been meaning to try them, but am skeptical about wasting cpu cycles for things i don't absolutely need.

---

### Post by Joeb on 2005-04-30
[QUOTE=zee]to Joeb: the install went fine (as usual :-) ) but the desklet didn't find any hardware sensors. I've installed lm-sensors too.

it's probably just my laptop (Toshiba Satellite M30) and not something software related.

zee[/QUOTE]

I like pjack76's advice.  Uninstall gdesklets-data and go to the website to download the desklets you actually want.  Most of the desklets in gdesklets-data are for the older version of gdesklets and are broken in the new version (this isn't just an Ubuntu problem).

As for the sensors, if you open a terminal window and run "sensors,"  do any readings show up?  If no, then the desklet won't find them either.  If yes, then it's most likely a broken desklet.

Joeb

---

### Post by Joeb on 2005-04-30
[QUOTE=23meg]what would you all say about the overall cpu power hogging of gdesklets? i've been meaning to try them, but am skeptical about wasting cpu cycles for things i don't absolutely need.[/QUOTE]


I think the cpu hogging is dependent on what gdesklets you are running.  I mainly run goodweather and a number of sensors and my cpu usage (as displayed by a desklet) is around 4%-5% (gnome running (obivously), but nothing else but gdesklets).  That's fine for me.  I'm running an AMD 1900+ cpu, though, so a slower processor might have more problems.  I've heard that some desklets are real memory hogs, but the "sidebar" sensor displays I'm using don't seem to be.

I'd suggest trying gdesklets, adding a cpu monitor and then start adding various other desklets to see how they react on your machine.

Joeb

---

### Post by seven on 2005-04-30
for XMMS you will need the python xmms package.
it is found in the universe repositpoy

oh and I use gdesklets, but alot of the stuff their doesn't work because it is for old versions

---

### Post by Psquared on 2005-05-02
[QUOTE=havesometea]This is one of the things that frustrates me about Linux.  In the Windows world there is a much easier method for installing applications.  You don't have to worry about this sort of library incompatibility as much.  

For instance...on my XP laptop I downloaded Konfabulator, installed it and had little desktop apps running in about 10 minutes.

I have been tinkering with this on Linux for about 6 hours and still nothing.[/QUOTE]

It all has to do with expectations. If you expect something to work 100% out of the box with no tweaking you will likely be disappointed with Linux. OTOH, you can't tweak Windows as much (if at all really because the kernel code is proprietary) and everything is a licensing issue.

So, yes, if you want something that just works XP is the way to go. If you want something cutting edge, customizable to your liking and evolving everyday Linux is for you. Plus, you have to like to tinker.  :wink:

---

### Post by Leigh on 2005-05-02
[QUOTE=Psquared]If you expect something to work 100% out of the box with no tweaking you will likely be disappointed with Linux. ....

So, yes, if you want something that just works XP is the way to go. If you want something cutting edge, customizable to your liking and evolving everyday Linux is for you. Plus, you have to like to tinker. [/QUOTE]

And because of this, I don't think that Linux is ready for the **end-user at home**.  For all their faults, Microsoft has made home computing a lot easier. I don't think your average user wants to download and compile source code or struggle for 6-weeks (see post #14) to get something working.  When you download and install software, you want it to work immediately, not have to tweak and fiddle.  Please note, I did say *end-user*, I'm not talking about techies or people with a greater-than-normal interest in computing, but your average person in the street, who buys a computer, gets it home, plugs it in and it just starts working.

I don't want to start a Holy War and I apologise for temporarily hijacking this thread. I'm sure this has been debated to death elsewhere, so I shall desist now.

---

### Post by Psquared on 2005-05-02
Funny thing is, I thought Ubuntu Warty worked pretty well out of the box. If all i was doing was email, internet and a little light typing - with some multimedia - then it is perfect. At least as usable as XP. Plus, Ooo is light years ahead of what comes standard on an XP machine without going out and buying M$ Office.

RhythmBox is as good as ITunes and Xine and MPlayer are great multimedia programs.

Games, printer support, and video support (ATI and nVidia) are issues with Linux, but its getting there.

I wonder if kernel development will slow down in the future?

---

### Post by Psquared on 2005-05-03
gDesklets works perfectly for me. I installed just the desktop-shell from Synaptic (Hoary) and then dowloaded the desklets I wanted from [www.gnomedesktop.org](www.gnomedesktop.org) and dropped them in.

Only problem I am having is they won't save between sessions. They are also not transparent. I wish I could figure out how to get rid of the borders and make them transparent -- really transparent -- not that fake stuff. ;)

---

### Post by Gary Powers on 2005-05-03
[QUOTE=Psquared]gDesklets works perfectly for me. I installed just the desktop-shell from Synaptic (Hoary) and then dowloaded the desklets I wanted from [www.gnomedesktop.org](www.gnomedesktop.org) and dropped them in.

Only problem I am having is they won't save between sessions. They are also not transparent. I wish I could figure out how to get rid of the borders and make them transparent -- really transparent -- not that fake stuff. ;)[/QUOTE]

Under System > Preferences > Sessions > Startup Programs, just stick gDesklets in there and they will come up everytime.

Gary

---

### Post by bubb on 2005-05-03
Hope you guys can help  :???: 

Here is my terminal session from running apt-get:
[I]mark@ubuntu:~$ sudo apt-get install gDesklets
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gDesklets
mark@ubuntu:~$[/I]

I looked in Synaptic & couldn't find any mention of gdesklets...

What do you think? (using x386 Hoary 5.04)

---

### Post by tread on 2005-05-03
Thats 'gdesklets', not 'gDesklets'. Probably case-sensitive ..

---

### Post by bubb on 2005-05-03
Well I figured it out...though thanks for replying (wasn't case sensitive)

I edited my sources.list file to go out and get things from other repositories.

Then I updated apt-get..then ran the apt-get install gDesklets..

BING!

I am becoming a regular pro with this Linux!

---

### Post by Psquared on 2005-05-03
[QUOTE=Gary Powers]Under System > Preferences > Sessions > Startup Programs, just stick gDesklets in there and they will come up everytime.

Gary[/QUOTE]

Been there, done that, got the T-shirt. ;)  (but it didn't save)

Actually, I am now trying it by putting in /usr/bin/gdesklets in "Startup Programs."

---

