---
title: "Installed Gutsy RC-1 on Dell Inspiron 531s"
date: 2007-10-18
forum: Dell  Ubuntu Support
---

### Post by dondad on 2007-10-18
I got a new Inspiron a couple of days ago with these specs:
```

Inspiron 531s,Athlon 64 X2 4000+ (2.10GHz, 512Kx2) 
2GB DDR2 SDRAM at 667MHz 
NVIDIA GeForce 6150 LE Integrated Graphics GPU  
250GB SATA II Hard Drive (7200RPM) 
No Floppy Drive Requested 
Microsoft Windows Vista Home Premium Edition, English 
Integrated NIC card 
56K PCI Data Fax Modem 
48X CDRW/DVD Combination Drive 
Integrated Audio 
No Preinstalled Software 


```

Since I had not seen Vista running yet, I fired it up to see what it looked like. It looked nice, but I was not impressed with the performance. It seemed very slow, especially when booting. Took forever to get to a totally functional desktop. It might have seemed better over time but.....

After making sure it worked OK, I pulled the hard drive and dropped in a 500 gig that I had around and installed Gutsy RC-1 on it. I partitioned it with 40 gig for the OS, 4 gig for the swap, and the rest for /home.

Installation went well (I got a couple of weird flashes on the monitor during the install, but it still ran fine to completion.) If I had a complaint, it would be that the first logon, it comes up with the volume at max. Whew, that woke me up ;-)

When it came up, it told me about the restricted drivers and provided the box to download and install. That worked fine. I installed the compiz fusion control panel, emerald (with repos) and set it up. Worked great, no problems.

So far, the sound works, It talks to the usb ports (memory stick and camera), display resolution fine, CD/DVD mounts OK (haven't tried burning yet), internet stuff/Firefox works as expected.

I installed the stream codecs and libdvdcss2 and got the music playback and flash to work in Firefox.

Basically, it was a non-event. except for the expected restricted drivers and codecs, everything worked out of the box.

It would appear that this hardware configuration is a good one for ubuntu installation. It installed easily and seems to have nice performance. No complaints.


I like Amarok as a player and so far that is the only problem I have found. It throws and error that it does not have the codecs to play streams (shoutcast). I had a bit of this before (fiesty), but could usually click several times and it would work. Not this time. Not sure if I am missing some codec (xmms works fine), or there is a problem with Amarok.

---

### Post by Sleestack on 2007-10-18
I too have the Dell Inspiron 531 and agree that Vista is dog-slow. Crazy, given it's a dual core machine. I did have some issues getting the nVidia video card to maximize its resolution in both 7.04 and 7.10 but finally got it to resolve at 1680x1050. I had to install the proprietary nVidia drivers, then configure the system to my monitor (Samsung SyncMaster 205bw analog.) Using 7.10 now and the system seems very fast and stable.

I find it a bit odd Ubuntu has 2 sections for video configuration: System->Preferences->Screen Resolution and System->Administration->Screens and Graphics. Seems like it's decoupled and would more easily be proximate in the UI. Once I found the 2 configuration screens I was on my way.

---

### Post by peestandingup on 2007-10-19
Sweet dude. Thanks for the write up.

Just a couple questions before I order me one of these machines.

-How are the integrated graphics? Is all the more intensive eye candy working fully in Compiz, such as the water ripples when moving windows around??

-Im a Linux noob, so why such a big swap partition? Does it get determined by the size drive you're using or what??

-Does that graphics card have DVI out?

-Do you mind burning a CD/DVD to test that part out?

Thanks!

---

### Post by Accelero on 2007-10-30
Hello,
Please pardon my noobieness.

I wanted to give Ubuntu a try and just happened to get a 531s (unfortunately about a week after you because I've got the 3800+), but I tried to install the server version first then put the desktop on that. In addition to finding the bug that states that I need to install the servers edition of restricted drivers (which doesn't exist) I haven't been able to get my graphics card working properly.

Could you please help? I've tried running sudo dpkg-reconfigure xserver-xorg and got an error very similar some other folks in that my hardware wasn't recognized. So I just stumbled through the settings and got things to look a little better, but still can't do things like enable desktop effects.

I would really appreciate any help.

---

### Post by happy-and-lost on 2007-12-16
I know this is an old thread...

Does anyone elses I 531 take a-g-e-s to boot? Not the OS, the BIOS. It hangs on the Dell splash screen for about a minute before loading up Grub :(

---

### Post by noogen on 2007-12-17
> **happy-and-lost said:**
> I know this is an old thread...

Does anyone elses I 531 take a-g-e-s to boot? Not the OS, the BIOS. It hangs on the Dell splash screen for about a minute before loading up Grub :(

You need to add irqpoll to boot parameter.  See response #4 of this thread -> [http://ubuntuforums.org/showthread.php?t=585566]("http://ubuntuforums.org/showthread.php?t=585566")

If you install Ubuntu Desktop using LiveCD and you have an LCD, make sure you remove the splash parameter and following instruction to make the removal of splash parameter permanent.

I just made several success installing 64bit desktop and server on my inspiron 530.  It took several installations becasue I ran into the same issue and also accidentally deleted my windows xp partition hehe...  I have it setup to dual boot correctly now.

---

### Post by happy-and-lost on 2007-12-17
No no, it's not Ubuntu that's taking ages, it's the BIOS. I've e-mailed Dell about it... but I don't hold out much hope there.

---

### Post by EvilMarshmallow on 2008-01-05
Are we talking about the same inspiron 531s?  I have been trying to do exactly what you have done... I want to install Gutsy on it, but the liveCD doesn't work.  I know it's not the CD's fault because i've installed on other machines flawlessly.  But when I boot the liveCD, I never get to a desktop.  After the Ubuntu splash screen with the orange bar fills up, and it's ready to take me to the desktop, it goes black and just sits there.  

I think the only thing that might be different is I'm using the integrated gfx card, but even safe graphics mode won't start up for me, it does the same thing.

Any ideas?

---

### Post by barryh on 2008-01-06
I also have a 531s. i got gutsy and hardy beta installed on it. Graphics work fine.  
I hardly even boot into vista. altho i found that vista ran faster once i upgraded memory to 2 gigs.

---

### Post by boyofford on 2008-01-07
I've just installed 7.10(gutsy gibbon?) on my 530s dual boot with vista premium, no unsolvable problems so far, pretty mush all good straight away, new to linux but already impressed.

Used windows XP for years, and bought this computer with pre-installed vista, it is a very resource hungry, got XP running on various computers at work with at at least half the spec.

However the slow startup problems with vista can be greatly improved by removing programs from startup and getting rid of the dell bloatware.

---

### Post by EvilMarshmallow on 2008-01-08
Does anyone have an idea what might be my problem?  I have tried both the 32 and 64 bit liveCDs, both in regular and safe graphics modes.  Every time, I get to the part of the liveCD boot where I would see the desktop for the first time but it never appears.  I get a black screen.

I looked over the original specs given in the thread and it's exactly what I've got, except I have 1 GB RAM.

I'm connecting this to an old 15-inch monitor... would that make a difference somehow, like it's booting but the monitor can't handle the input?

---

