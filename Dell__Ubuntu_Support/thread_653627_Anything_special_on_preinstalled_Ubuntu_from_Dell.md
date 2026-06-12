---
title: "Anything special on preinstalled Ubuntu from Dell?"
date: 2007-12-30
forum: Dell  Ubuntu Support
---

### Post by fbn on 2007-12-30
Hi,

I've just ordered a Dell XPS m1330 with Ubuntu 7.10 preinstalled. Is there anything special on this Ubuntu version installed by Dell or is it a plain out of the box installation?

I mean, System 76 for example have their own hardware driver which they include into the preinstalled Ubuntu. Is there something like that with Dell also or is it save to format and do a manual installation myself?

Frank

---

### Post by XP-FREAK on 2007-12-30
I didn't try it jet, but i think they used the OEM installation feature of ubuntu and fixed prehaps all drivers so that your Dell will run out of the box without problems.

So that's nothin else then a preinstalled windows, added some OEM stuff and installed the drivers.

---

### Post by fbn on 2007-12-30
What do you mean by installed OEM stuff?

---

### Post by LaRoza on 2007-12-30
> **fbn said:**
> What do you mean by installed OEM stuff?

Drivers, files, and other software that computer vendors stick on computers they sell.

I think they have the codecs for playing videos and other media too. So it works easier out of the box.

---

### Post by XP-FREAK on 2007-12-30
> **LaRoza said:**
> Drivers, files, and other software that computer vendors stick on computers they sell.

I think they have the codecs for playing videos and other media too. So it works easier out of the box.

yes, or simply some dell artwork or support tools.. you'll see

---

### Post by fbn on 2007-12-30
Thanks for the info, I'll have a look what they have done :)

---

### Post by natehall on 2007-12-30
*I think they have the codecs for playing videos and other media too. So it works easier out of the box.*

I have a Dell 1420N Inspiron. The "N" signifies that it was preinstalled with Ubuntu. (Fiesty in my case) I had to download the various files needed for videos and sound. The nice thing about preloaded Dells is they have a built in recovery partition. Very usefull when you're just learning about Linux and you've somehow screwed up your machine!

---

### Post by randomlyred on 2007-12-30
Please post back on what's included on the m1330 - I've recently purchased one myself (Vista, no Ubuntu on Dells in Australia) and having spent the better part of a few weeks getting it to go I'm curious as to what works - specifically, do both of the headphone ports at the front of the machine work? Even at the same time?

---

### Post by fragos on 2007-12-30
I have a 1420n that came with 7.04.  I downloaded the Dell 7.10 DVD and upgraded..  I have a strait from Ubuntu 7.10 on my desktop and noticed an interesting but small difference.  The mouse preferences on the Dell have a touchpad tab which isn't on my desktop.  small convienience detail but I wonder what else they did.  Glad I waited for the Dell release of 7.10 -- everything works.

---

### Post by MikeRussell on 2007-12-31
I have a 1420 (wiped vista) and both headphone jacks work at the same time.  If not, the Dell Wiki has a workaround.
Cheers,
Mike

---

### Post by zetetic on 2007-12-31
What's the point of using a pre-installed ubuntu system?

If weren't you who installed the system how can you be sure the system is not compromised??

Don't be naive!

---

### Post by l0stendeavor on 2007-12-31
yeah I quickly reformated and reinstalled ubuntu on my dell 1420n just to be sure it was setup how I wanted it. Don't like strangers messing with my box.

---

### Post by PaJoe on 2007-12-31
My wife's 1420N purchased shorty before Christmas was pretty plain ubuntu, I expected more Dell customization . The newer models with 7.1 have some licensed audio.video programs already setup - I think I read they use Lindvd. The best part of the pre-install is everything works and as previously posted they do have a restore partition. I ended up downloading the Gutsy 7.1  iso from Dell and installed from the live cd so our restore partition has been removed, but I know the ubuntu iso made by Dell works just as good . For the dvd stuff I used:

sudo apt-get install ubuntu-restricted-extras
(Note that there is also xubuntu-restricted-extras and kubuntu-restricted-extras)

I was so impressed with the Dell 1420N that I bought a refurbished Dell 531 desktop, used Dell desktop iso disk to  format and install Ubuntu and  now I have a new Dell desktop running kubuntu for less then I could have purchased the part to upgrade my previous kubuntu system. At his point, I love Dell and the way they try to make every system linux compatible.

---

### Post by PaJoe on 2007-12-31
> **zetetic said:**
> What's the point of using a pre-installed ubuntu system?

If weren't you who installed the system how can you be sure the system is not compromised??

Don't be naive!

It's unfortunate that you believe Dell would consider losing their reputation trying to hide something in a open source  based system. Once  any company makes a commitment  to open source software they are stuck in a situation where they know people can easily find out what they have in their systems. Yes, the company can hide something but it will be discovered quickly and once discovered their reputation is destroyed and in the business world your reputation is some times all you have to keep you going. Nothing personal, but to suggest Dell is trying or may be trying to sell compromised systems is FUD.

If anyone spends some time on the Dell linux information pages/forums you will quickly see there are a few dedicated linux people working for Dell, just as there are some working at IBM and many other businesses. Linux had made great strides in the last few years and some of that work has been done by people working "on the clock" at IBM and other computer related businesses.

---

### Post by SnowflakeRV7 on 2007-12-31
> **fbn said:**
> I've just ordered a Dell XPS m1330 with Ubuntu 7.10 preinstalled. Is there anything special on this Ubuntu version installed by Dell or is it a plain out of the box installation?
Dell offers the 1330 with Ubuntu preinstalled now?  Cool.

I bought my 1330 without Ubuntu, and installed it myself.  So far, I haven't found anything that didn't work with a default installation.  I have the nVidia 8400 instead of the Intel onboard graphics, so I had to enable the restricted drivers, but I still consider that an out-of-the-box success... It worked fine without them, and still works fine with them.

How is yours being configured?  Will it have a Vista and/or MediaDirect partition (ie. dual/triple boot)?  If not, what will the MediaDirect button (to the left of the power button) do?

If it came with a recovery CD/DVD, i'm sure a lot of non-"ubuntu-preinstalled" owners would love to get a copy of that.  I know I would.

---

### Post by fragos on 2007-12-31
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) has links for the download of Dell 7.01 DVD's.

---

### Post by yesint on 2008-01-01
Dear All,
What about the "hard drive killer" bug, which is present in ubuntu? ([http://ubuntuforums.org/showthread.php?t=591503&highlight=kill+hard+drive](http://ubuntuforums.org/showthread.php?t=591503&highlight=kill+hard+drive))
Is it fixed in the pre-installed system or not? If Dell sells xps1330 with ubuntu preinstalled they should deal with this issue somehow. 
Could somebody who have this pre-installed system check if they have this bug?

---

### Post by fragos on 2008-01-01
I haven't noticed any extraneous disk activity on my 1420n when on 7.04 or now with running Dell 7.10.

---

### Post by yesint on 2008-01-02
The hard drive of Dell xps 1330 (and probably all other in xps series) is affected by this bug.
[http://ubuntuforums.org/showpost.php?p=4056757&postcount=631]("http://ubuntuforums.org/showpost.php?p=4056757&postcount=631")
Can anybody who has an xps with pre-installed ubuntu confirm this?

---

### Post by Fascination on 2008-01-03
> **SnowflakeRV7 said:**
> Dell offers the 1330 with Ubuntu preinstalled now?  Cool.

I bought my 1330 without Ubuntu, and installed it myself.  So far, I haven't found anything that didn't work with a default installation.  I have the nVidia 8400 instead of the Intel onboard graphics, so I had to enable the restricted drivers, but I still consider that an out-of-the-box success... It worked fine without them, and still works fine with them.


I just recieved my XPS1330 from dell, though I never saw an option to select Ubuntu as the OS (maybe its not being offered immediately to the UK site yet?). Does the biometric reader work fine under Ubuntu?

---

### Post by SnowflakeRV7 on 2008-01-03
> **fragos said:**
> [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) has links for the download of Dell 7.01 DVD's.
Darn, they don't list one for the 1330 yet.  If they did, i'd be all over it.

I suspect the 1420 version is close enough, I think the 1330 and 1420 share the same hardware anyway, but i'd still prefer to have a properly targeted restore disk.

---

### Post by fragos on 2008-01-03
> **SnowflakeRV7 said:**
> Darn, they don't list one for the 1330 yet.  If they did, i'd be all over it.

I suspect the 1420 version is close enough, I think the 1330 and 1420 share the same hardware anyway, but i'd still prefer to have a properly targeted restore disk.

After restoring a system the real work begins.  Backing up /home, including hidden files, helps but there's still configuration and start files that need to be restored.  IMHO -- the best route is using gpated to make a copy of your working partition or group of them.  This could be a partition on the system or an external disk.  As to the Dell install disk, I'll bet the 1420 install will get you closer than a vanilla LiveCD.

---

### Post by zetetic on 2008-01-21
> **PaJoe said:**
> It's unfortunate that you believe Dell would consider losing their reputation trying to hide something in a open source  based system. Once  any company makes a commitment  to open source software they are stuck in a situation where they know people can easily find out what they have in their systems. Yes, the company can hide something but it will be discovered quickly and once discovered their reputation is destroyed and in the business world your reputation is some times all you have to keep you going. Nothing personal, but to suggest Dell is trying or may be trying to sell compromised systems is FUD.

If anyone spends some time on the Dell linux information pages/forums you will quickly see there are a few dedicated linux people working for Dell, just as there are some working at IBM and many other businesses. Linux had made great strides in the last few years and some of that work has been done by people working "on the clock" at IBM and other computer related businesses.

Dell could use some proprietary package(s). In fact I think Dell ships systems with some proprietary stuff, like drivers...

So the point remains... Don't be naive. Install yourself your system!

---

### Post by zetetic on 2008-01-21
And the kind of people who don't know something so simple as installing linux, it's not the kind of people who easily would discover pre-installed malware...

---

### Post by tptbz on 2008-01-22
Hello,

Dell doesn't use any proprietary drivers on the 1420N with Ubuntu.

If they did they would be available on their driver download site.

Therefore there are no proprietary drivers in the 1420N.

---

### Post by tptbz on 2008-01-22
> **fbn said:**
> Hi,

I've just ordered a Dell XPS m1330 with Ubuntu 7.10 preinstalled. Is there anything special on this Ubuntu version installed by Dell or is it a plain out of the box installation?

I mean, System 76 for example have their own hardware driver which they include into the preinstalled Ubuntu. Is there something like that with Dell also or is it save to format and do a manual installation myself?

Frank

Dell doesn't sell the XPS m1330 with Ubuntu installed.

---

### Post by drsaamah on 2008-01-23
not in the MOST countries that is.  in germany and a few others they do.  its unfortunate, i just bought a 1330 today and no matter how much i fought with them they wouldnt send me an OS-free laptop, much less a ubuntu one.  200 dollars wasted.

---

### Post by rosegarden78 on 2008-01-23
I don't want to burst your bubble but you can probably get a Dell Inspiron 1200 like mine and still do some graphics, music and video conversions.  I just hope the hardware and speed is significantly better.  But with 512 memory I figure I'll use the 1200 with Ubuntu until it falls apart on me.

---

### Post by kenshin_i on 2008-01-24
They do sell xps m1330 in germany.

EDIT: they do now in europe, US will come in a week

---

### Post by samir85 on 2008-01-24
Hi, I'm considering to buy the Dell XPS M1330 Linux laptop. Anyway Dell ships it by default with an Intel GMA X3100 graphic card, can somebody comment how good this graphic card does perform?

---

### Post by RedRat on 2008-01-24
OK  got my Dell Inspiron with Ubuntu pre-installed. Here is what I found. Out of the box, it does allow you to see DVDs. There is a recovery partition, but there is apparently a catch which I will describe. Everything works out of the box extremely well. However, I made the mistake of trying to download Ubuntu Studio. For whatever reason the installation did not go well. After I got all of the parts of Studio downloaded, and went to reboot the x-server would not load. The only way I could get back in the system was to hit the ESC button when Grub was loading and then load the generic ubuntu. No problem there, lost nothing. 

Now the partition. I thought that this was the original partition that came with the machine, it is an iso-file. So I thought I would just go back to the original OS. No Joy. Basically, that iso file is continually added to, when I went to use this in recover mode, I was back to x-server not loading, and the ubuntu-studio components there. So each time I started my machine, I had to hit ESC and load the generic OS--which now included Studio and its components. So somewhere during the download of Studio, the x-server config was fouled up. I tried several options on the grub menu and still was right back to a non-loading x-server.

Finally, I just gave up and reinstalled Ubuntu from the disk that Dell provided. No problem there, that went very smoothly. It recognized my nVidia card and loaded the restricted drivers and the machine now works just as when I got it. I don't think that there is anything really special that Dell does, maybe some restricted drivers for DVDs but you can get libdvdcss2 etc anyway.

The machine works great, I now am doing all of my stuff on it. I have no problems so far. I think the machine is great.

---

### Post by x0as on 2008-01-24
> **kenshin_i said:**
> They do sell xps m1330 in germany.

EDIT: they do now in europe, US will come in a week

Its just a shame that in the UK,  the m1330 with vista installed is better value than the ubuntu version.

---

### Post by fragos on 2008-01-24
> **samir85 said:**
> Hi, I'm considering to buy the Dell XPS M1330 Linux laptop. Anyway Dell ships it by default with an Intel GMA X3100 graphic card, can somebody comment how good this graphic card does perform?

It supports 3D rendering and on my 1420n gave me about 1,100 pfs running glxgears.  Compiz blacklists this card so despite excellent performance you'll be giving up the extreme eyecandy.  IMHO with the smaller laptop screen I don't find that eyecandy as compelling.  The extra processing wil also take more battery.  I got the 9 cell battery option with my 1420n and get over 5 hours battery run time.

---

### Post by RedRat on 2008-01-25
Thanks for the info. Extremely helpful.

---

### Post by zetetic on 2008-01-27
> **tptbz said:**
> Hello,

Dell doesn't use any proprietary drivers on the 1420N with Ubuntu.

If they did they would be available on their driver download site.

Therefore there are no proprietary drivers in the 1420N.

That's what they say... lol

Would a hacker tell the victim a trojan or a rootkit was installed on the system?

Did Sony told the consumers about their rootkit, for instance?

---

### Post by Raggnarok on 2008-01-27
I think UBUNTU is a good idea, but DELL? Yuck.

---

### Post by fragos on 2008-01-27
> **zetetic said:**
> That's what they say... lol

Would a hacker tell the victim a trojan or a rootkit was installed on the system?

Did Sony told the consumers about their rootkit, for instance?

Would you please share with us the details of the evil Dell has done.  We'd all be interested in how you discovered this.

---

### Post by CancelloCornorosso on 2008-01-27
going back to the original topic, I'd have two questions for people who tried Dell's iso:

1. Is the version in the dvd 32bit or 64bit?
2. How does the media direct button work when a clean install from the dvd is done?

I have a dual booting m1330, but I'd like to give Dell's new dvd a try depending on these two questions.

Thanks in advance

---

### Post by fragos on 2008-01-27
I upgraded my 1420n to Dell 7.10.  It's 32 bit and all the special buttons and functions work.

---

### Post by CancelloCornorosso on 2008-01-29
> **fragos said:**
> I upgraded my 1420n to Dell 7.10.  It's 32 bit and all the special buttons and functions work.

thanks fragos, but I didn't explain myself in question 2: I meant what happens to the media direct partition and what happens when you press the media direct power up button instead of the regular power button. Dell has has specific set up that you mess up if you simply erase the MBR and install Ubuntu.

To clarify, does anyone know what happens to the Media Direct/Regular OS set up installing the dell's ubuntu dvd iso on a m1330.

thanks

---

### Post by fragos on 2008-01-29
On the 1420n after the Dell 7.10 DVD install the Media Direct button will cause a system start similar to the power button.  While running the Media Direct button brings up Rythmbox.

---

### Post by kbless7 on 2008-01-29
Dell had problems 5 years ago with bad hardware, but now they are better than any other computer company. Maybe not apple but thats different.

---

### Post by CancelloCornorosso on 2008-01-30
> **fragos said:**
> On the 1420n after the Dell 7.10 DVD install the Media Direct button will cause a system start similar to the power button.  While running the Media Direct button brings up Rythmbox.

that's good news IMO, I want to use 64bit, but I guess I can restore from DVD so to fix Dell's MBR and then install hardy 64bit. Again, thanks

---

### Post by valke on 2008-02-09
i'm expected to get my 1420n in a few days. i'm seriously stoked. i read the rythmbox pops up with meda direct. anyway to change that and have lindvd or vlc pop up instead? also i wish they had a rust colored version for us ubuntu users lol.

---

### Post by thelip on 2008-02-09
I just got my m1330 last night from Dell, and pressing the media direct button fires up Rhythmbox.

---

### Post by fragos on 2008-02-09
> **valke said:**
> i'm expected to get my 1420n in a few days. i'm seriously stoked. i read the rythmbox pops up with meda direct. anyway to change that and have lindvd or vlc pop up instead? also i wish they had a rust colored version for us ubuntu users lol.

Try System-> Preferences-> Removable Drives and Media-> Multimedia tab and change the default "Portable Music Players".  I looked at where the hot key bindings are configured ans they only define the function which implies that the default application will be used.

---

### Post by kbless7 on 2008-02-09
> **valke said:**
> i'm expected to get my 1420n in a few days. i'm seriously stoked. i read the rythmbox pops up with meda direct. anyway to change that and have lindvd or vlc pop up instead? also i wish they had a rust colored version for us ubuntu users lol.

I have a media center dell from a year and a half ago. Pressing my media direct starts rhythmbox. nothing too special

---

### Post by dondad on 2008-02-12
> **natehall said:**
> *I think they have the codecs for playing videos and other media too. So it works easier out of the box.*

I have a Dell 1420N Inspiron. The "N" signifies that it was preinstalled with Ubuntu. (Fiesty in my case) I had to download the various files needed for videos and sound. The nice thing about preloaded Dells is they have a built in recovery partition. Very usefull when you're just learning about Linux and you've somehow screwed up your machine!

I have an xps410n and there is one thing to watch for about the Dell reinstall partition:

The initial install had the setup all on one partition, which means that if you reinstall, you will lose all of your data unless you back all of it up (not that I ever broke anything but... ;-)). I would recommend that you not use that, but instead, before you get a lot of data, download the standard Ubuntu CD, repartition your hard drive and put your /home on a separate partition, then reload. That way, you can reload without losing everything and most of the extra programs will still be there after a reload because a lot of them instal to your home directory and do not get wiped in a reinstall. For any reloads, use the CD, and not the built in partition.

---

### Post by valke on 2008-02-12
i just got my 1420n series. i had a b120 that was running 7.10 albeit poorly, and multiple hardware failures, so getting this puppy was a dream come true. and i was able to shift to lindvd thanks to fragos. you totally rock.

---

### Post by Sayuuk on 2008-02-12
> **fragos said:**
> I have a 1420n that came with 7.04.  I downloaded the Dell 7.10 DVD and upgraded..  I have a strait from Ubuntu 7.10 on my desktop and noticed an interesting but small difference.  The mouse preferences on the Dell have a touchpad tab which isn't on my desktop.  small convienience detail but I wonder what else they did.  Glad I waited for the Dell release of 7.10 -- everything works.

the touchpad tab appears when you have a touchpad.

since your desktop probably doesn't have a touchpad, that's normal ;-)

---

### Post by Sayuuk on 2008-02-12
> **valke said:**
> i'm expected to get my 1420n in a few days. i'm seriously stoked. i read the rythmbox pops up with meda direct. anyway to change that and have lindvd or vlc pop up instead? also i wish they had a rust colored version for us ubuntu users lol.

have a look at the keyboard shortcuts

when I try to use the media button to start a terminal it sometimes works and sometimes not.

---

### Post by natehall on 2008-02-12
[QUOTE=dondad;4317475]I* have an xps410n and there is one thing to watch for about the Dell reinstall partition*:

I've since done the Dell Gutsy DVD with a fresh install. I don't have a whole lot of data to backup myself so I just put what little I really want to save on USB sticks. As I was totally new to Linux at the time I bought my 1420N it has been a great way to discover just how neat Linux really is. ( I had tried and failed to load Linux on a dead Windows Pavillion HP in the past. It now runs Ubuntu! )

---

### Post by valke on 2008-02-12
i'm wondering if the media buttons works on amarok.

---

### Post by fragos on 2008-02-12
> **Sayuuk said:**
> the touchpad tab appears when you have a touchpad.

since your desktop probably doesn't have a touchpad, that's normal ;-)

My Desktop has a USB cabled touchpad.  With 7.04, I enabled Synaptics in xorg.conf.  With 7.10 it works without adding Synaptics to xorg.  By work I mean taps and vertical scroll as well as cursor positioning. What you say seems logical. For whatever reason my touchpad is recognized and supported without adding the device to xorg.

---

### Post by Pastor_JW on 2008-04-20
I got my 1525 with LinDVD and Ubuntu 7.10 preinstalled and working nicely (after I got the system reinstalled cause I never got an initial startup screen!) but I am wondering if I upgrade to 8.04 later this week will LinDVD still work?  Kinda hate to lose that as the laptop is used in the car to watch movies on trips!  I added BibleTime to the original install but the current version needs to be fixed.  Other than that I think it special that Dell is putting a real operating system on their machines!!  Thanks Dell!

---

