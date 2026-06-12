---
title: "Ubuntu Boot-up time"
date: 2005-02-08
forum: Desktop Environments
---

### Post by lao_V on 2005-02-08
Recently, I decided to ditch M$ Windows and give Linux a try. After sifting through various distributions for couple of weeks, I came across Ubuntu. I liked what I saw.
 
 I knew using Linux was going to be an interesting challenge and a good learning experience after having used Windows for years. 
 
 However, there is one thing I have been unable to overlook so far and that is the time it takes to boot-up into (any) Linux system is much much longer then WinXP.
 
 Does everyone else have the same experience? Is there anything I can do to make it load faster? (without harware upgrade)

---

### Post by nocturn on 2005-02-08
[QUOTE=lao_V]Recently, I decided to ditch M$ Windows and give Linux a try. After sifting through various distributions for couple of weeks, I came across Ubuntu. I liked what I saw.
 
 I knew using Linux was going to be an interesting challenge and a good learning experience after having used Windows for years. 
 
 However, there is one thing I have been unable to overlook so far and that is the time it takes to boot-up into (any) Linux system is much much longer then WinXP.
 
 Does everyone else have the same experience? Is there anything I can do to make it load faster? (without harware upgrade)[/QUOTE]

Do you have numbers on the times?

Also, do you count the time from bootup to display of the desktop, or from bootup untill the desktop is responsive?  The latter is a big difference between Linux and Windows.

---

### Post by lao_V on 2005-02-08
It would only seem reasonable to count the time from "switching on" to the display of "login" screen as any time after that is taken by the start-up apps/processes (In this regards KDE is much slower then GNOME - from login screen to desktop availability)
 
 The average time for WinXP is about a minute to the login screen but for Ubuntu (or any other linux) is approximately 2.5-3mins (and if eth0 can't find the network then that seems to take forever before it finally declares 'Failed')
 
 Are there unnecessary services that could be disabled for faster booting without damaging the system?

---

### Post by nocturn on 2005-02-08
[QUOTE=lao_V]It would only seem reasonable to count the time from "switching on" to the display of "login" screen as any time after that is taken by the start-up apps/processes (In this regards KDE is much slower then GNOME - from login screen to desktop availability)
 
 The average time for WinXP is about a minute to the login screen but for Ubuntu (or any other linux) is approximately 2.5-3mins (and if eth0 can't find the network then that seems to take forever before it finally declares 'Failed')
 
 Are there unnecessary services that could be disabled for faster booting without damaging the system?[/QUOTE]

Ok, in this respect, I can agree with you, Linux is slower.

If you count the time from boot to login screen and add the time from clicking OK after entering username/password until a usable desktop, then the difference is much less or even none.

I use WinXP on my portable at work (no Ubuntu on it),  it takes about as long to get from logon to a usable desktop then to boot up.

---

### Post by crun on 2005-02-08
That's one of the things that really bugs me with the Windows box I use at work - booting is lightning fast, but once I've logged in I can easily go off and have a cup of coffee before all those services have finally started. If you're in a hurry it's even worse because you're never sure when everything has finished and you can actually start working.

Ofcouse when you log off and switch users the whole thing begins again. Plus the fact that every app seems to want to install its own running deamon (Adobe Version Cue, NVidia Desktop Manager - wtf?) and you have to clean up after them every time you install something new. Anyway, always a relief to get home and start up Ubuntu, longer booting time yes, but once you've logged in you're set.

---

### Post by rufius on 2005-02-08
[QUOTE=lao_V]Recently, I decided to ditch M$ Windows and give Linux a try. After sifting through various distributions for couple of weeks, I came across Ubuntu. I liked what I saw.
 
 I knew using Linux was going to be an interesting challenge and a good learning experience after having used Windows for years. 
 
 However, there is one thing I have been unable to overlook so far and that is the time it takes to boot-up into (any) Linux system is much much longer then WinXP.
 
 Does everyone else have the same experience? Is there anything I can do to make it load faster? (without harware upgrade)[/QUOTE]
 My system boots to login screen within a minute from turning on the system. This shortened though from the original because I disabled certain daemons that I don't need/see a need for (ie: ppp & pppoe and more). Might try reading up on update-rc.d and decide what services you dont' need.

---

### Post by lao_V on 2005-02-08
If only there was a way for desktop PC's to have a boot up time of only milliseconds like my Pocket PC (although I do realise its not as powerful and has its limitations).

---

### Post by crane on 2005-02-08
What in hte world are you people talking about :?: 
I didn't think people cut there PC's off. :lol: 

I can't really compare, I haven't booted windows in so log I don't know if I would remember how. #-o

---

### Post by eldrich_rebello on 2005-02-08
hey.my ubuntu box used to get from switching on to  a responsive desktop in 45 seconds flat.way faster than windoze.

---

### Post by lao_V on 2005-02-08
Maybe I should have mentioned I have a 2GHz AMD Athlon with 300MB RAM and 120 GB HDD. I would love to know how if anyone can boot up under this spec in 45 seconds.

---

### Post by landotter on 2005-02-08
My 1.1ghz/256 box takes 90secs to get to the login screen fwiw--the same as XP more or less...

You can speed up the boot processes by disabling services. I did this with Fedora and it really helped.

Unfortunately editing service levels is something I'm not comfortable doing with the CLI and I don't see a gui option for Ubuntu.

I do understand the Ubuntu decision to omit such a tool--keep it simple stupid...but I'd like to be able to apt-get one.

---

### Post by k.ODOMA on 2005-02-08
I do have to say that when I was experimenting with Arch linux that I was able to boot about twice as fast as Debian, which was my main distro at the time. It could have been around 45 seconds but I didn't time it.  And this was on a 933mhz Celeron processor.

I think distro implementation is a much bigger factor than Windows vs. Linux.

---

### Post by Jad on 2005-02-08
here is my test result from power up to login screen.

PIII/1G cpu/ 384SD ram.
 74sec
P4 2.6, 256DDRAM
47.70sec

---

### Post by jubuntus on 2005-02-08
I find the same thing (and sometimes embarassing when I try to sell Linux to aunties, mums, etc) but this is being addressed... with ubuntu at least.
[http://www.ubuntulinux.org/wiki/FasterBootProcess](http://www.ubuntulinux.org/wiki/FasterBootProcess)

---

### Post by nocturn on 2005-02-09
[QUOTE=jubuntus]I find the same thing (and sometimes embarassing when I try to sell Linux to aunties, mums, etc) but this is being addressed... with ubuntu at least.
[http://www.ubuntulinux.org/wiki/FasterBootProcess](http://www.ubuntulinux.org/wiki/FasterBootProcess)[/QUOTE]

Do they really worry about it?

I thought my wife and parents the same habit I have.  I bootup my computer when I get home from work or in the morning when I get up (shut it down when I go to sleep).

Bootup is somethings that takes place while getting coffee/taking of coat/...

The same goes for my WinXP machine at work (I hate XP, BTW).

---

### Post by Wim Sturkenboom on 2005-02-09
PIII/500MHz with 384MB
WinXP: 40 seconds
Ubuntu: 90 seconds

PII/400 with 128MB
Slackware 10: 40 seconds

Please do not forget that Microsoft made huge improvements in the bootup time in WinXP. Win2000 and others are a lot slower.

---

### Post by AndersAA on 2005-02-09
are you testing boot time to the linux login screen and the windows login screen?  Windows loads stuff in the background, so it's far from ready when you see the start menu... you CAN do the same in linux.  And hoary has some updates in that area.  Still, I'm glad the developers arn't putting much time into it, and worry about more important stuff ;)

---

### Post by lao_V on 2005-02-09
A 'professional/enthusiast' desktop user may only boot his/her system once a day or in some cases not switch it off at all. In this case boot up time is irrelevant. 
 
 However, I have a feeling that an average desktop user switches on/off the computer once or more in a day. And this is where faster boot up time will be appreciated.

---

### Post by ikletti on 2005-02-10
My bootup time:
1 minute 17 seconds 'til login screen on a
P3 700 MHz, 256 MB RAM, UDMA 2 HDD
with Ext3 file system.

---

### Post by lao_V on 2005-02-10
Now, I'm thinking, is changing the filesystem going to improve the performance? I currently have ext2. But I suppose it greatly depends on what you want to use your system for, doesn't it?

---

### Post by TopDog on 2005-02-10
Haven't timed it, but I have a "feeling" that my Ubuntu-install boots a little bit slower than XP did when I had XP on it. But as someone said, XP takes a lot longer to login than Ubuntu does, so overall I don't really see a difference.

BTW: I like the fact that Ubuntu has a non-GUI boot. It's nice to see what happens. On my Fedora-laptop, I've removed the GUI-boot thingy... result: faster boot.

---

### Post by lao_V on 2005-02-10
Booting in text mode may well be faster but its nice to have an option of both..to see a picture and have a text appear at the bottom displaying what's going on!

---

### Post by AndersAA on 2005-02-10
[QUOTE=lao_V]Now, I'm thinking, is changing the filesystem going to improve the performance? I currently have ext2. But I suppose it greatly depends on what you want to use your system for, doesn't it?[/QUOTE]

ext2 is pretty fast, but it's not journaling, and personally I have to have that.  (Meaning if you shut down without shutting down properly (for example due to power failure) you'll loose files).

---

### Post by ikletti on 2005-02-10
[QUOTE=lao_V]Now, I'm thinking, is changing the filesystem going to improve the performance? I currently have ext2. But I suppose it greatly depends on what you want to use your system for, doesn't it?[/QUOTE]

Justin Piszcz did a benchmark for various file systems, you might want to read (or rather look at the many graphs) here: [http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)
In other locations I've read that ReiserFS should be the fastest one, if you have many small files (as usually happens if you're a developer and do lots of compiling).

If i should have too much spare time, I'll do a fresh install on that machine and see what the results are if I use ReiserFS...

Ingo.

---

### Post by jubuntus on 2005-02-11
[QUOTE=nocturn]Do they really worry about it?[/QUOTE]

Well, not worry about it as in lie awake at night in cold sweats worrying about it!
But commenting on how it seems to boot no faster than their WIndows box did before I upped their hardware and installed Linux? Yes.
For professional/business/developer users, this may not be an issue.
But for the average home desktop user, YES.
There is an old saying, "First impressions count".
And yes I know XP loads the gui first and all that, but does the web browser and email user really care about this? They just want to turn on and play?
And not everybody drinks coffee... :)

---

### Post by alainhenry on 2005-02-11
[QUOTE=landotter]
Unfortunately editing service levels is something I'm not comfortable doing with the CLI and I don't see a gui option for Ubuntu.

I do understand the Ubuntu decision to omit such a tool--keep it simple stupid...but I'd like to be able to apt-get one.[/QUOTE]

To edit boot time services, you can use rcconf from the command line.  
I found that the synchronisation to ubuntu clock was usually very long, and sometimes I abort it by pressing ctrl-c when it tries starting that  service.  

Alain

---

### Post by jubuntus on 2005-02-11
[QUOTE=alainhenry]To edit boot time services, you can use rcconf from the command line.  [/QUOTE]
Hi Alain.
I login sudo -s and rcconf and get a command not found error.
Do I have to login as root? In which case I'll have to enable the account?
Thanks.
Justin.

---

### Post by nocturn on 2005-02-11
[QUOTE=jubuntus]Well, not worry about it as in lie awake at night in cold sweats worrying about it!
But commenting on how it seems to boot no faster than their WIndows box did before I upped their hardware and installed Linux? Yes.
For professional/business/developer users, this may not be an issue.
But for the average home desktop user, YES.
There is an old saying, "First impressions count".
And yes I know XP loads the gui first and all that, but does the web browser and email user really care about this? They just want to turn on and play?
And not everybody drinks coffee... :)[/QUOTE]

LOL, on my company WinXP laptop, they rolled out patches yesterday.
Guess what, everything is about twice as slow as before.
Booting, starting apps, ...

BTW, they are working at boottimes in Hoary, getting GDM to start sooner (but not  before services that are really needed), so hold on.

I still think that WinXP takes equally long to get to the desktop, and actually respond to anything you do (although initial graphics display happes earlier).

---

### Post by nocturn on 2005-02-11
[QUOTE=jubuntus]Hi Alain.
I login sudo -s and rcconf and get a command not found error.
Do I have to login as root? In which case I'll have to enable the account?
Thanks.
Justin.[/QUOTE]

You need to install rcconf first.

---

### Post by brousch on 2005-02-11
I dual boot XP and Ubuntu on a dual p3-450 with 384 Megs RAM.
On this computer, Ubuntu is longer to the login screen, but XP is longer to a useful desktop.

I would say Ubuntu takes 120 seconds to load to the login (Static IP so no network detection needed) and 45 seconds more to the desktop.

XP takes 90 seconds to the login (also static IP) and 120 seconds to the desktop.

---

### Post by jubuntus on 2005-02-12
[QUOTE=nocturn]BTW, they are working at boottimes in Hoary, getting GDM to start sooner (but not  before services that are really needed), so hold on.[/QUOTE]
Yup, they sure are! I posted the link at number 14 in this thread.
[http://www.ubuntulinux.org/wiki/FasterBootProcess](http://www.ubuntulinux.org/wiki/FasterBootProcess)
Also, some possibly, almost very likely, completely irrelevant and unlinked news is that Ubuntu are working with the author of the ettiquette icon set to do the theme for the upcoming hoary, although the author told me that it won't be complete until the release after hoary. The ettiquette icon set is an svg icon set that is the highest ranked at [http://www.gnome-look.org](http://www.gnome-look.org). Although that set posted there will, I suspect, look nothing like the theme they'll end up with (metallic bin doesn't go with Human's organic theme, for example) it does give you an indication of this guy's talent. And he lives in my home town!
Rock on Ubuntu!!!

---

### Post by alainhenry on 2005-02-12
On my AMD K-7 @ 650 MHz, 256 Megs RAM, I need about 2 minutes to be operational with Win98 (including antivirus, not present in Ubuntu).  With Ubuntu, it's a bit more. I need 2 minutes 20 sec. (I stopped the synchronisation with ubuntu clock, which takes ages).  

Alain

---

### Post by rufius on 2005-02-12
[QUOTE=k.ODOMA]I do have to say that when I was experimenting with Arch linux that I was able to boot about twice as fast as Debian, which was my main distro at the time. It could have been around 45 seconds but I didn't time it.  And this was on a 933mhz Celeron processor.

I think distro implementation is a much bigger factor than Windows vs. Linux.[/QUOTE]
 Arch linux also installs a lot less servers by default compared to debian so you have to keep that in mind. Debian/Ubuntu's default server lists are by far a lot longer than Arch's because Arch starts out so minimal as it is.

---

### Post by chryz on 2005-02-12
Possibly a bit unrelated, but seemed most appropriate as far as I can tell. I'm using a laptop that has both wired and wireless networking - obviously I'm only using one of them at a time. Both of the cards use DHCP to get the settings, but at boot it takes a long time for the subsystem to give up on the card that isn't connected - this time can be reduced by editing /etc/dhcp3/dhclient.conf and setting the timeout-value to something around 5-10 seconds (should be plenty and I've never had any problems with it). Just a hint from a fellow newbie.

---

### Post by Davepet on 2005-02-12
On my PII-366 laptop w/128MB, it's a full 3 minutes to login,, and another minute to full desltop.

Starting the hotplug system was almost a minute by itself. 

There is a bit of delay at clock sync, but only if my network modem  isn't dialed up yet, if it is, it just ips through it.

Dave

---

### Post by redneckr1 on 2005-02-23
christ booting is a chore on my imac 233 mhz w/h 64mb ram.

any ideas on talking a n00b through disabling some junk not needed for a standard office, mp3 playing media center?

anyone.

ill get my coat.

---

### Post by zaba on 2005-03-03
[QUOTE=lao_V]However, there is one thing I have been unable to overlook so far and that is the time it takes to boot-up into (any) Linux system is much much longer then WinXP.
 
 Does everyone else have the same experience? Is there anything I can do to make it load faster? (without harware upgrade)[/QUOTE]


I haven't really seen this part of the equation mentioned... For me, a Linux boot could take ten times as long to start and I would still be okay with it. Why? Because I only need to boot Linux once. 

Right now, my Linux machine has been up for 23 days. (It would be more, but I wanted to buy a CD from iTunes). With Windows, the best I could get was three days without having to reboot to make sure everything was working right. (Granted, the last time I really used Windows was with ME). 

So, yeah, I think the boot process probably does take longer, but I don't have to deal with it nearly as much. And, I've NEVER had to do the multiple reboots that Windows sometimes made me do. Other than saving some money on the electric bill, is there a reason to turn the computer off?

---

### Post by ixus_123 on 2005-03-03
how many of you have Linux booting off the first p[artition?  What ever os boots from there will have a speed advantage.  I'm not sure how much but it's there.

I usually go & make a cup of tea at first switch on time.  A fast boot is more of an issue for Windows where restarts are needed.  With linux you don't need to restart & as you all probably know, control, alt, backspace will restart gnome in a flash.

I downloaded Windows updates yesterday & those stupid speech bubles drove me mad promting for me to restart for the changes to take effect.  You'd think clicking 'no ' so I could restart later would be enough.  It went on to give me a popup window reminding me to restart every 5 or 10 minutes or something :(

---

### Post by bored2k on 2005-03-03
[QUOTE=ixus_123]how many of you have Linux booting off the first p[artition?  What ever os boots from there will have a speed advantage.  I'm not sure how much but it's there.

I usually go & make a cup of tea at first switch on time.  A fast boot is more of an issue for Windows where restarts are needed.  With linux you don't need to restart & as you all probably know, control, alt, backspace will restart gnome in a flash.

I downloaded Windows updates yesterday & those stupid speech bubles drove me mad promting for me to restart for the changes to take effect.  You'd think clicking 'no ' so I could restart later would be enough.  It went on to give me a popup window reminding me to restart every 5 or 10 minutes or something :([/QUOTE]

YES those bubbles R annoying ... even WORSE are Trend Micro's PC-cillin 2005 restart bubbles ... its not a tray reminder , they DO popup every 5minutes..so if ure typing while it appears... "texas is going bye bye".

---

### Post by kahping on 2005-03-03
haha... i have to agree that those speech bubbles in winxp are annoying; can't say the same about Trend Micro though, as i've never used it.

but Ubuntu's definitely improving on the boot up time. i've upgraded from warty to hoary just a few days ago and i find the boot time is MUCH faster than before. the Ubuntu devs are definitely working on it, so no worries.  ;) 

kahping

---

### Post by psychic on 2005-03-04
The problem with standard linux-bootscripts is that 9 out of ten times they do nothing but wait. (For example, networking... it checks for dhcp and until it gets an IP or a timeout it does nothing)

The same is true for almost every service.

But if you can think of a way to display parallel booting-scripts you can make stuff a lot faster (for example 3 or 4 scripts in the time the network script waits).
I say 'display' because that prolly is the reason the scripts still start after eachother...
ppl want to 'see' what is goin' on. if you throw everything to the background you probably get a faster boot.

---

### Post by landotter on 2005-03-04
[QUOTE=redneckr1]christ booting is a chore on my imac 233 mhz w/h 64mb ram.

any ideas on talking a n00b through disabling some junk not needed for a standard office, mp3 playing media center?

anyone.

ill get my coat.[/QUOTE]
 hey red--You need ram baby. RAM!!

Throw a 256mb stick in that candy coloured box and it'll actually feel spunky. :P

---

### Post by AndersAA on 2005-03-04
[QUOTE=psychic]The problem with standard linux-bootscripts is that 9 out of ten times they do nothing but wait. (For example, networking... it checks for dhcp and until it gets an IP or a timeout it does nothing)

The same is true for almost every service.

But if you can think of a way to display parallel booting-scripts you can make stuff a lot faster (for example 3 or 4 scripts in the time the network script waits).
I say 'display' because that prolly is the reason the scripts still start after eachother...
ppl want to 'see' what is goin' on. if you throw everything to the background you probably get a faster boot.[/QUOTE]

this isn't a problem with "standard linux-bootscripts", this is a problem with ubuntu's bootscripts.  A lot of distro's for example run dhcp requests in the background.  And hoary is a lot better at this than warty was.

---

### Post by kiddo on 2005-03-07
[QUOTE=kahping]but Ubuntu's definitely improving on the boot up time. i've upgraded from warty to hoary just a few days ago and i find the boot time is MUCH faster than before. the Ubuntu devs are definitely working on it, so no worries. ;) [/QUOTE]Heya kahping, that is something that worries me, so I decided I might as well post my boot time. I heard people everywhere saying "WOAH hoary boots much faster!". However, there is absolutely no difference for me. May it be because I have dist-upgraded instead of a fresh-install?

I am running a 2.4ghz (overclocked to 2.6) Pentium 4B, with 2x 512mB of 333mhz DDR ram. However, the boot process still takes 50-80 seconds. I will reboot right now to take a more precise benchmark.

The reason why I'd like to boot fast is to impress people :) you can't "purge the infidels" with a 2.5min boot time! :lol: just kidding. however, I'm looking for a way to "prefetch" Gnome when there is no ressource usage (while I'm typing my username and password at the login screen). It would be cool to be able to boot Gnome within 15 seconds (warm start) instead of 30 (cold start).

Oh yeah, for those who want to know, I am using ReiserFS all the way, without any traces of windows (completely wiped it out since 2005, and I'm very happy so). Then I guess Reiser maybe does no difference in the bootup time. It does, however, go BLAZING FAST. I have a complete rsync of my web server by SSH in... one second (yeah, I timed it). That's 30K analyzed files :) (the server is running with ReiserFS too)


**Edit**
I just wrote down my entire boot process. Here goes.
0m03s starting Ubuntu *
0m45s entering runlevel 2
1m00s the nvidia splash screen shows up
1m14s the login screen appears [pause]
1m21s the gnome start sound plays
1m45s the panels and desktop are loaded (visible)
2m01s gnome is fully loaded with Gaim (the only app on startup)

I believe this is painfully long for a Pentium 4 machine with so much RAM

---

### Post by Wusel on 2005-03-18
So that everyone schowing their boottime
Here is mine

42sec to login 
on my Centrino1,5Ghz

---

### Post by 23meg on 2005-03-18
my boot times: 2 minutes on Warty, 30 seconds on XP Pro with SP2 (both to login screen). XP takes an extra 15-20 seconds to "get ready" whereas Warty takes 5 to 10. i'm running a 1.8 ghz p4m laptop with 512 mb ram and a very fast hd.

my newbie observation with simplyMEPIS, Sarge, Warty, Fedora Core 3 and DeMuDi is that there are many unneeded daemons running at startup in all of them. i'll really appreciate help on how to disable these.

m.

---

### Post by garyng on 2005-03-18
hoary seems to be much more faster than sarge. I believe some streamline of the rc?.d thing have been done.

As for cut that down, either update-rc.d or manually remove them. I usually create a disabled directory under rcS.d an rc2.d and move those things not needed to it, easier to me than update-rc.d

BTW, X takes quite sometime to init which unfortunately is not avoidable for most.

---

### Post by mirtux on 2005-03-21
[QUOTE=chryz]Possibly a bit unrelated, but seemed most appropriate as far as I can tell. I'm using a laptop that has both wired and wireless networking - obviously I'm only using one of them at a time. Both of the cards use DHCP to get the settings, but at boot it takes a long time for the subsystem to give up on the card that isn't connected - this time can be reduced by editing /etc/dhcp3/dhclient.conf and setting the timeout-value to something around 5-10 seconds (should be plenty and I've never had any problems with it). Just a hint from a fellow newbie.[/QUOTE]
Hi,
   thanks for the hint about the DHCP timeout....

Regards,
MC

---

### Post by lorap on 2005-03-21
hi guys!
56 seconds :-)

40gb hard
2.6g intel
256 ram
+slow hard dish 4200 rpm cause it's a laptop :-)
i've dropped out my win xp that far so if i would want to find it i'll need to search with the dog :-)
pavel

---

### Post by dolson on 2005-03-27
Who cares about boot time? It's all about the uptime, baby!

Sadly, my record uptime so far on Ubuntu is 9 days, whereas with Debian Sid, my uptime was measured in weeks, and almost months in a couple cases.

My server uptime is definitely measured in months, and would've been years if my stupid cheapo UPS wouldn't have started beeping like crazy. Current uptime on my server is 48 days. Max since switching the OS from Mandrake a long time ago was 212 days (I was too lazy to ditch Mandrake off of my server until sometime in early 2003.. I needed it to be up, couldn't afford the downtime, until I moved cities, then that kinda killed my uptime, which was over 200 days on Mandrake 8.2 I think it was).

Anyhow, I've seen, with my own eyes, Slackware boot up in 7 seconds. And on nothing special hardware too. This was in 2002. Also, I had Debian booting up from power on to user interface in 13 seconds. Mind you, these were college projects (mine was a gaming console, I developed the UI and a game for it), so they didn't need everything that people use on a standard desktop (the Slackware thing was an older PC turned into a GPS mapping system for a car... Pretty cool stuff at that college, I tell you what).

Yes, the boot time on Ubuntu is slow. Even when I ran Debian before this, it was much faster. I haven't tackled speeding it up yet though, because I just don't care that much. Windows might boot faster, but it's just as fast to crap out on you too.

---

### Post by kiddo on 2005-03-30
Looks like some activity has been going on since I last visited that post ;) okay, just my recent experience: I've installed a fresh Hoary on my laptop, which is a P3 Speedstep 600mHz with 256mB of ram. Guess what? It boots a whole lot faster than my 2.4gHz desktop (which I previously said took 2minutes+ to boot). 

The laptop takes 1 min 40 seconds, and 43 seconds flat when using hibernation. Wow! Kudos! Even if that's only ~15-30 seconds less, that's achieved on a machine with a quarter of the RAM and CPU (and a 4200rpm laptop HDD?). I expect Grumpy (or any next fresh install on my desktop when I mess things up a little bit too much someday ;)) to be quite fast!
What still eats up boot time is the "starting hotplug subsystem"...

Now, the reason why I don't keep every computer always on is for obvious noise reasons (and remove some strain on my power supply fans XD). Having a minimum of 3 PCs around, including a laptop with a very noisy HDD, it's a lot better to boot'em up when needed. Boot time is not really crucial, but it's always a nice thing to ...not have ;)

---

### Post by arctic on 2005-03-30
the update to hoary increased my bootup time on an ext3 partition hdd with 7200 rpm from roughly 2 minutes to 54 seconds until i get to gdm on an old 750 mhz duron with 330 mb ram. not bad at all.

the bootup speed depends on several things: first of all: the rpm of your hdd, clean scripting, then the filesystem (ex3 and reiserfs are faster than ext2 and reiser4 afaik) and the layout of your system. if you have the swap as first partition, then the root filesystem and after this the home partition, the access to the bootup scripts is considerably faster than putting the swap at second or third place on your hdd.

just my two cents

---

### Post by soul_rebel on 2005-04-05
on a p3 1000 256 mb ram and a junky hd:
from grub to gnome (logged in and gnome completely loaded):
90 seconds

Some services had to be disabled for this.

---

### Post by chryz on 2005-05-09
Personally I think Ubuntu seems highly unoptimized when it comes to boot-up - too much time is spent simply waiting for things... wasted time without any disk activity or much cpu usage to talk about. Don't listen to the pessimists - the quick boot-ups are out there - my way slower slackware box boots so fast that it makes this one look like a slow-mo.

Haven't tested it myself, but LibRenix recently featured an article on replacing initrd with initng and shaving off an enormous amount of time. Ubuntu, being a frontline distribution should consider looking into it.

---

### Post by freeflight on 2005-05-11
I personnaly disagree with a lot of guys there and i think boot up process should (must?) be improved for several reasons :

1. dudes who say that they dont  mind because they never stop their computer are freaks ;) Everyone must stop their computer if they dont use it by ecological conscience... well thats another topics but my opinion.

2. Our goal should not be winXP but beOS which start in about 15 sec on older computers. That's a challenge.

And yes, with a newly installed hoary, startup process is faster than on an updated wharty. It took me about 2 mins on my laptop whereas now, it takes about 1min. 

But thats only a beginning. Ubuntu *is* a desktop oriented distribution aimed for users who dont even care what is a startup service. So the only way to be above others OS is to improve dramaticaly the boot process and responsiveness of the UI. 

If we dont care or if ubuntu still wait too long, development process and migrate things like sysinit to initng will become more and more difficult... 

My goal is to decrease the 1min to 30 sec boot process. Lets give a try  :?

---

### Post by henriquemaia on 2005-05-12
[QUOTE=freeflight]I personnaly disagree with a lot of guys there and i think boot up process should (must?) be improved for several reasons :

1. dudes who say that they dont  mind because they never stop their computer are freaks ;) Everyone must stop their computer if they dont use it by ecological conscience... well thats another topics but my opinion.

2. Our goal should not be winXP but beOS which start in about 15 sec on older computers. That's a challenge.

And yes, with a newly installed hoary, startup process is faster than on an updated wharty. It took me about 2 mins on my laptop whereas now, it takes about 1min. 

But thats only a beginning. Ubuntu *is* a desktop oriented distribution aimed for users who dont even care what is a startup service. So the only way to be above others OS is to improve dramaticaly the boot process and responsiveness of the UI. 

If we dont care or if ubuntu still wait too long, development process and migrate things like sysinit to initng will become more and more difficult... 

My goal is to decrease the 1min to 30 sec boot process. Lets give a try  :?[/QUOTE]

Very much agree with your point 1. Being ecological. A computer just running out of laziness is terrible for the environment. We should have this in consideration even when we're p2p.

Last night went late to bed just reading about **initng**. This should be a must on every distro once it gets stable.

---

### Post by nocturn on 2005-05-12
[QUOTE=henriquemaia]
Last night went late to bed just reading about **initng**. This should be a must on every distro once it gets stable.[/QUOTE]

It depens, there is also some trouble with the Apple license, maybe that'll be an issue too.

---

### Post by AndersAA on 2005-05-12
[QUOTE=nocturn]It depens, there is also some trouble with the Apple license, maybe that'll be an issue too.[/QUOTE]

initng and launchd are not the same project, initng is GPL licensed if I remember correctly.

---

### Post by nocturn on 2005-05-12
[QUOTE=AndersAA]initng and launchd are not the same project, initng is GPL licensed if I remember correctly.[/QUOTE]

There must have been some short-circuit in my brain to get these confused ;-)

I read about launchd a couple of days ago and mixed them up today.  Thanks.

---

