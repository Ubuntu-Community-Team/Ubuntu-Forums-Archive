---
title: "Why is SUSE faster than Ubuntu on my machine?"
date: 2006-01-12
forum: General Help
---

### Post by Adrian on 2006-01-12
Why is Suse faster than Ubuntu on my machine?

Problem: Everything X-related takes A LOT more cpu in Ubuntu than SUSE. This makes my laptop fan spin, which is pretty annoying to say the least.

For instance, the ksysguard monitor uses approximately 4% of my CPU.
With Kubuntu, it uses 15% (!). The diagram drawing is really slow.

SUSE uses Xorg too, so I find this really strange. I used the SUSE-generated
xorg.conf in Ubuntu, but that didn't change anything.

Any ideas?

System specifications:
Intel Celeron 700 Mhz
384MB RAM
800x600 screen (yay! :) )

This is not really a KDE related problem, I think. The same thing happens when I do this in Gnome.

---

### Post by Rackerz on 2006-01-12
Not really sure what could be causing that. Did you check what proccesses where making it use so much up? 

It could just be that Suse is more suited for your machine. I don't usually see much problems in terms of CPU usage in Ubuntu.

---

### Post by Adrian on 2006-01-12
[QUOTE=Rackerz]Not really sure what could be causing that. Did you check what proccesses where making it use so much up? 

It could just be that Suse is more suited for your machine. I don't usually see much problems in terms of CPU usage in Ubuntu.[/QUOTE]

When I check with the top command, ksysguard uses 15% all by it self, while on SUSE it uses like 4%. On SUSE there are more processes active, but they take very little CPU power each (just like the Ubuntu's non-graphical processes), so it sums up to approx. 6%.

I really want to use Ubuntu, because I like it so much. However, the fan noise from my laptop makes my head hurt.

---

### Post by fannymites on 2006-01-12
I've also noticed this, when running kde in suse and ubuntu suse is much, much quicker for me but when using gnome in both suse and ubuntu, ubuntu is much, much quicker.

---

### Post by Rackerz on 2006-01-12
Hmmmm, I don't really get this problem. Kubuntu is faster than Suse on my machine, how strange. I really don't have an idea what could be causing that sorry guys :).

---

### Post by Adrian on 2006-01-12
[QUOTE=fannymites]I've also noticed this, when running kde in suse and ubuntu suse is much, much quicker for me but when using gnome in both suse and ubuntu, ubuntu is much, much quicker.[/QUOTE]

SUSE's KDE is awsome, indeed. However, in my case, I get the same numbers when I use Ubuntu Gnome (15% for ksysguard). It also feels quite slow, just like Kubuntu, in comparison to SUSE.

---

### Post by Adrian on 2006-01-12
[QUOTE=Rackerz]Hmmmm, I don't really get this problem. Kubuntu is faster than Suse on my machine, how strange. I really don't have an idea what could be causing that sorry guys :).[/QUOTE]

Well, I'm clueless too. I suspect it's my laptop hardware (Compaq Armada 110) that doesn't play well with the X server, but why? It must be possible to solve :)

---

### Post by codejunkie on 2006-01-12
I don't know if this will help in your case, but the kernel you have installed in ubuntu will make a big difference in overall performance with suse you don't have to worry about installing an optimised kernel the installer does it for you. when i do a default ubuntu install the 386 kernel is installed by default and everything seems slower and has kind of a lag to it but if i install the -k7 kernel in ubuntu everything flys. and i get about the same preformance using suse and ubuntu.

---

### Post by Adrian on 2006-01-12
[QUOTE=codejunkie]I don't know if this will help in your case, but the kernel you have installed in ubuntu will make a big difference in overall performance with suse you don't have to worry about installing an optimised kernel the installer does it for you. when i do a default ubuntu install the 386 kernel is installed by default and everything seems slower and has kind of a lag to it but if i install the -k7 kernel in ubuntu everything flys. and i get about the same preformance using suse and ubuntu.[/QUOTE]

Thanks for the suggestion. I'm using the default kernel, and I'll definitely try changing it.

---

### Post by Adrian on 2006-01-12
Well, installing the 686 kernel (I have a simple celeron CPU) definitely improved the numbers. Ksysguard now eats 8% of the CPU on average (compared to SUSE's 4%). Any suggestions of what to try next?

What conerns me is that the "rectangular frame" used to select icons on the desktop is not operating smoothly at all. If I use it to "select" 25% of the screen, it gets the hiccups and becomes very slow. On SUSE, I can "frame" the entire screen, and this was also the case in Debian Sarge using XFree86. I recently tried Debian Testing with XOrg and it's just as slow as Ubuntu on my machine.

Any ideas of how I can speed things up a little more?

---

### Post by drizek on 2006-01-13
i think your video card drivers are not installed correctly. what does your xorg.conf look like?

---

### Post by dragonfyre13 on 2006-01-13
I don't know if this is doable in KDE, but if you change the window manager in Gnome, it speeds things up exponentially. Anyone know if SUSE's default is Meatcity as well? If it uses XFCE4, (or something) that would definately explain the difference.

---

### Post by nocturn on 2006-01-13
I don't know, but are you comparing KDE in SuSE to Gnome in Ubuntu?

If so, kwin is beating metacity hands down... so Gnome will run slower (if you have enough memory).

---

### Post by Adrian on 2006-01-13
Thank you everyone for your replies!

[QUOTE=drizek]i think your video card drivers are not installed correctly. what does your xorg.conf look like?[/QUOTE]

That sounds reasonable. However, I tried using SUSE's xorg.conf in (K)Ubuntu (copied everything except the font configuration, which is a little different). They were already quite similar, both identifying my card as "Trident Microsystems CyberBlade i1".

I can post the entire file if you still want to see the details.

[QUOTE=dragonfyre13]
I don't know if this is doable in KDE, but if you change the window manager in Gnome, it speeds things up exponentially. Anyone know if SUSE's default is Meatcity as well? If it uses XFCE4, (or something) that would definately explain the difference.[/QUOTE]

I haven't tried SUSE's GNOME, so all my comparisons have been made using KDE's default window manager Kwin on SUSE. Changing the default window manager in Gnome is an idea, but I'd like to get the KDE desktops equally fast as well.

[QUOTE=nocturn]I don't know, but are you comparing KDE in SuSE to Gnome in Ubuntu?[/QUOTE]
Well, no. I'm comparing SUSE's KDE to Kubuntu. The reason why I've also tried in Gnome is to rule out that the problem is Kubuntu-specific. The Gnome numbers are a little worse - 11% on average for ksysguard when doing nothing else than monitoring the idle system (i.e monitoring itself), in contrast to 8% in KDE (and 4% in SUSE's KDE). Gnome also has the same generally slow behaviour as KDE.

---

### Post by M3lted on 2006-01-13
hey guys slightly of topic , but i saw u talking about choosing the kernel in     (K)ubuntu, where did u choose it , was it during the install or ? 

thx

---

### Post by Adrian on 2006-01-13
[QUOTE=M3lted]hey guys slightly of topic , but i saw u talking about choosing the kernel in     (K)ubuntu, where did u choose it , was it during the install or ?[/QUOTE]

Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by M3lted on 2006-01-13
thank you :)

---

### Post by heftigrat on 2006-01-13
[QUOTE=Adrian]What conerns me is that the "rectangular frame" used to select icons on the desktop is not operating smoothly at all. If I use it to "select" 25% of the screen, it gets the hiccups and becomes very slow.[/QUOTE]
I get the same problem.  From my experience (limited as it is) I get much better performance after I make sure my vid driver is installed correctly.  I know xorg.conf is the same on both machines, but if you don't actually install the drivers it doesn't really matter what's in xorg.conf.  Did you check your particular model card and install the driver in Kubuntu?  And a related question that may make my post invalid, does SUSE come packaged with extra drivers (being 5 discs and all :p )?

---

### Post by daveisadork on 2006-01-13
I wonder if the fact that SUSE uses ReiserFS by default as opposed to Ubuntu's ext2 default would make a difference.

---

### Post by tseliot on 2006-01-13
[QUOTE=Adrian]Well, installing the 686 kernel (I have a simple celeron CPU) definitely improved the numbers. Ksysguard now eats 8% of the CPU on average (compared to SUSE's 4%). Any suggestions of what to try next?

What conerns me is that the "rectangular frame" used to select icons on the desktop is not operating smoothly at all. If I use it to "select" 25% of the screen, it gets the hiccups and becomes very slow. On SUSE, I can "frame" the entire screen, and this was also the case in Debian Sarge using XFree86. I recently tried Debian Testing with XOrg and it's just as slow as Ubuntu on my machine.

Any ideas of how I can speed things up a little more?[/QUOTE]
Well that's easy:
If you have an nvidia graphic card you have to install the proprietary drivers.

Then:
```
sudo gedit /etc/X11/xorg.conf
```
OR
```
sudo kate /etc/X11/xorg.conf (if you use KDE)
```

And add the following option at the end of the Section "Device":
```
Option   "RenderAccel"  "True"
```

Then log out, press CTRL+ALT+Backspace (so as to restart the xserver)

Enjoy!

OR if you do not have an nvidia card or the drivers do not work for you, there is a way to disable that effect (which most distros don't use) but I can't remember it since I'm mainly a GNOME user

---

### Post by Adrian on 2006-01-13
[QUOTE=tseliot]
And add the following option at the end of the Section "Device":
Option   "RenderAccel"  "True"
[/QUOTE]
Thanks for the suggestion. However, it didn't seem to make any difference on my hardware. I don't see any error messages, but it feels the same. Maybe the gfx card is too old... The laptop is from 2001, and I suppose that the Trident Microblade i1 chip is older than that.

---

### Post by Adrian on 2006-01-13
[QUOTE=daveisadork]I wonder if the fact that SUSE uses ReiserFS by default as opposed to Ubuntu's ext2 default would make a difference.[/QUOTE]

Some people say it's noticably faster, and other people don't agree. Regardless of what's correct, I think that the file system doesn't affect my particular problem significantly, since I should have RAM enough (384MB) to avoid disk swapping when running one single application.

---

### Post by Adrian on 2006-01-13
[QUOTE=heftigrat]I get the same problem.  From my experience (limited as it is) I get much better performance after I make sure my vid driver is installed correctly.  I know xorg.conf is the same on both machines, but if you don't actually install the drivers it doesn't really matter what's in xorg.conf.  Did you check your particular model card and install the driver in Kubuntu?[/QUOTE]
This sounds very interesting. However, I did some googling and couldn't find any Linux driver (although the manufacturer says that it exists). Furthermore, I found a document of xfree86 compatible cards, and it said that to run the "Trident Cyberblade i1" in particular, all you are supposed to do is to select the "trident" driver (which xorg does for me).

[QUOTE=heftigrat]And a related question that may make my post invalid, does SUSE come packaged with extra drivers (being 5 discs and all :p )?[/QUOTE]
How do I find out? I did an Internet install so it's possible that it just installed the driver for my card.

---

### Post by squizzz on 2006-01-13
I installed Kubuntu (just switched from SUSE) few days ago and have similar problem here. I think main performance difference between SUSE and (K)Ubuntu is because SUSE uses i586 optimized packages, while Kubuntu seems to use "safe" i386. MMX optimizations make wonders when it comes to software drawn graphics, particulary you will suffer huge performance hit with all kind of transparency related stuff just like the one you mention :
[quote="Adrian"]What conerns me is that the "rectangular frame" used to select icons on the desktop is not operating smoothly at all. If I use it to "select" 25% of the screen, it gets the hiccups and becomes very slow.[/quote]
And yes, I was *shocked* by this too - PII 450MHz here! There's no problem with this in SUSE even on as low specs machine as mine, so I guess optimized build is the right way to go.

Now, anyone know of repositories that offer more optimized package builds? (like 586 or 686) :)

---

### Post by Adrian on 2006-01-14
[QUOTE=squizzz]I installed Kubuntu (just switched from SUSE) few days ago and have similar problem here. I think main performance difference between SUSE and (K)Ubuntu is because SUSE uses i586 optimized packages, while Kubuntu seems to use "safe" i386. MMX optimizations make wonders when it comes to software drawn graphics, particulary you will suffer huge performance hit with all kind of transparency related stuff just like the one you mention :

And yes, I was *shocked* by this too - PII 450MHz here! There's no problem with this in SUSE even on as low specs machine as mine, so I guess optimized build is the right way to go.

Now, anyone know of repositories that offer more optimized package builds? (like 586 or 686) :)
[/QUOTE]

I didn't think that would make such a difference, but apparently it does.
Regarding optimized package builds, wouldn't just an optimized X server speed up things significantly in this particular case?

---

### Post by sunny_nwho on 2006-01-14
but even if suse was faster the performance and environment in ubuntu are awesome....now i can do everything i can in windows in Ubuntu....like presentations, TV-out, irda transfers and receiving,bluetooth transfers and receiving...gr8...i used KDE 3.5 but i was more happy with gnome....bluetooth is gr8 in gnome compared to KDE it works like a charm for me...

---

### Post by SinnerG on 2006-01-17
[QUOTE=tseliot]Well that's easy:
If you have an nvidia graphic card you have to install the proprietary drivers.

Then:
```
sudo gedit /etc/X11/xorg.conf
```
OR
```
sudo kate /etc/X11/xorg.conf (if you use KDE)
```

And add the following option at the end of the Section "Device":
```
Option   "RenderAccel"  "True"
```

Then log out, press CTRL+ALT+Backspace (so as to restart the xserver)

Enjoy!
[/QUOTE]

Got onto this topic by accident but this tip helped me with the slow 'select' draw and also when I move my windows they move right away now (instead of the slow repaint :P)

---

### Post by slinga on 2006-01-17
I'm having the complete opposite experience your having. Having used SuSE 9.2-10.0 for nearly 11 months, (k)Ubuntu's KDE smokes SuSE's. I'm running a 64 bit dual xeon. In all other regards SuSE 10.0 is more polished and stable. I just couldn't take that fact that it was slow on such a powerful machine, that's why I switched. 

I'm going to try the beta version of SuSE 10.1 when it comes out on the 19th. Hopefully that'll be a decent speedup.

---

### Post by drizek on 2006-01-17
slinga, were you using a kde from before version 3.4? there was quite a big speed boost in 3.4.

anyway, im probably going to pass on beta 1 as i have finals next week. ill download beta 2 right before a long weekend.

---

### Post by Brando569 on 2006-01-17
i tried SuSE awhile ago and liked it but couldnt really get used to it, now i use kubuntu and i love it, its a lil slow at times when im running alot of programs (especially amarok, when im playing music) i have a 3.2 ghz and 512mb of ram most of the time i only have around 20mb free

---

### Post by getaceres on 2006-01-21
I tried SUSE 10.0 not long ago, but I found their KDE 3.5 packages extremely unstables. Konqueror was crashing all the time and so some other applications. Also I couldn't get fonts configured properly for my TFT.
When I came back to Kubuntu I didn't notice any difference in performance except for the selection box issue. Also I have a rather fast proccessor (compared to the PII 450MHz), an Athlon XP 2200+. The first thing I make when installing (K)Ubuntu is to install the -k7 kernel packages and the ATI binary drivers.

---

### Post by getaceres on 2006-01-21
I tried SUSE 10.0 not long ago, but I found their KDE 3.5 packages extremely unstables. Konqueror was crashing all the time and so some other applications. Also I couldn't get fonts configured properly for my TFT.
When I came back to Kubuntu I didn't notice any difference in performance except for the selection box issue. Also I have a rather fast proccessor (compared to the PII 450MHz), an Athlon XP 2200+. The first thing I make when installing (K)Ubuntu is to install the -k7 kernel packages and the ATI binary drivers.
I'll give SUSE another try when KDE 3.5.1 comes out to see if it's stable enough.

---

### Post by pelle.k on 2006-01-23
[QUOTE=tseliot]Well that's easy: If you have an nvidia graphic card you have to install the proprietary drivers. Then: ```
sudo gedit /etc/X11/xorg.conf
``` OR ```
sudo kate /etc/X11/xorg.conf (if you use KDE)
``` And add the following option at the end of the Section "Device": ```
Option "RenderAccel" "True"
``` Then log out, press CTRL+ALT+Backspace (so as to restart the xserver) Enjoy! [/QUOTE] I have to ask you why this isn't included in your howto? I just happened to try this (didn't think it would do anything as i have followed all your "method 2" notes) But it worked! cool :)

[edit] the "Got onto this topic by accident but this tip helped me with the slow 'select' draw and also when I move my windows they move right away now (instead of the slow repaint)" part that is....[/edit]

---

### Post by drizek on 2006-01-23
wow, i just installed suse 10.1 and it kicks ass. i cant figure out how to get my wifi working though, so it kinda ruins it.

---

### Post by Adrian on 2006-01-24
[QUOTE=drizek]wow, i just installed suse 10.1 and it kicks ass. i cant figure out how to get my wifi working though, so it kinda ruins it.[/QUOTE]

I've been looking at that beta as well, but I haven't tried it yet. Did you notice any speed differences (compared to 10.0)?

---

### Post by drizek on 2006-01-24
i dunno, the lack of internet kinda kills it for me. i dont use it anymore, and im going to replace it with my first Gentoo install this thursday.

---

### Post by Adrian on 2006-01-24
[QUOTE=drizek]i dunno, the lack of internet kinda kills it for me. i dont use it anymore, and im going to replace it with my first Gentoo install this thursday.[/QUOTE]

Funny. I'm just doing my first Gentoo install also (instead of installing the SUSE beta as I originally planned). Some advice: don't install the entire kde-meta package unless you have a fast machine. My computer has been buidling it non-stop for the last 48 hours, and there's plenty of stuff left to compile :)
Next time I'll only install the necessary stuff.

---

### Post by moopere on 2006-01-24
[QUOTE=Adrian]Funny. I'm just doing my first Gentoo install also (instead of installing the SUSE beta as I originally planned). Some advice: don't install the entire kde-meta package unless you have a fast machine. My computer has been buidling it non-stop for the last 48 hours, and there's plenty of stuff left to compile :)
Next time I'll only install the necessary stuff.[/QUOTE]

Get back to us here on this thread if you can actually benchmark or otherwise quantify any speed differences beteen ubuntu and gentoo - I'm really interested as it seems to me that Linux (not just ubuntu) systems are getting slower and slower as time goes by.  

I'm just starting to get into a serious set of kernel and other compiles with benches to try and see if I can't work out whats going on....for sure something is up these days as I have a rack full of 200->1GHz machines here all of which used to run things like Debian Woody and SuSE 6.4 and so on really really fast, but now can't even run a basic ubuntu/suse/redhat installation.

As a beginning I have recently compiled a stock breezy kernel for i586 and did some benching on a P200 (classic) versus the ubuntu i386 stock breezy kernel...I gotta tell you, theres not a lot in it.  In fact, given enough runs I think the averages would collapse to around a delta of zero.

This was pretty dissapointing I have to say, I was expecting at least some measurable change, which is why I'm pretty interested in the results you get with Gentoo - if you compile not just the kernel but _everything_ will you get measurable speed increases and will those increases be large enough to justify the huge amount of time and effort expended?

Cheers,
Craig

---

### Post by drizek on 2006-01-25
try something like vector linux for those old boxes.mainstream distros have performance that keeps up with maintsream hardware, but there are always highly optimized distros available for the older stuff.

---

### Post by moopere on 2006-01-25
[QUOTE=drizek]try something like vector linux for those old boxes.mainstream distros have performance that keeps up with maintsream hardware, but there are always highly optimized distros available for the older stuff.[/QUOTE]

I guess I expected an answer like this (thanks for the pointer to vector by the way, I'm looking now), and I'm really in no position to disagree - much like Windows, the Linux systems get more features and so on thereby taking up the extra horsepower that modern machines provide.

I wonder though, what exactly is going on with the code that turns your brand spanky new 3GHz P4 into a 486DX2/66 from 10 years ago?  Is it the convenience of plugging in your USB device and having it automount?  Is it a whole bunch of 'little' things like that that end up bogging down your machine?

You know what else I wonder?  How on earth did we ever get any work done back in the 80's and 90's?  I mean, with such slow computers?

* smile *

I've had this conversation before but have yet to see a convincing argument.  For instance, look at Windows NT4, came out around 1994 right?  You could run it pretty darn well on a 486DX4/100 with 8 or 16MB RAM (I was running OS/2 on 4MB then).  

Now, I'm not trying to turn this into a Windows versus Linux war, but think about what you got with NT4 and what you could do on such a tiny powered machine.  

I'm running some tests now, just for grins, on an Intel P5, 200MHZ (non mmx), 96MB RAM - this would have run NT4, Win95 and any Linux available at the time really really quickly, I mean, people would be blown away by the outright speed of this powerbox in its day - but now, today, I cannot comfortably run Ubuntu with either Xfce, Gnome or KDE without any actual applications at all?  I can't even run the desktop....

Anyway, I don't want to hijack this thread completely, but its food for thought.  Why _is_ SuSE so much quicker than Ubuntu?  Why are the current crop of machines running fabulous desktops about as quick as our simple desktops back in 1994?  Is it a compiler issue?  Is the requirement to support such a huge number of historical processors and machines starting to add up?

Cheers,
Craig

---

### Post by drizek on 2006-01-25
ubuntu simply is just not optimized for speed. there is quite a bit of bloat in it to make it easier to use. the suse team really put some work into 10.0 to make it faster. the same applies to vector, and vector can still do things like automount your usb stick(IIRC). there are a ton of performance optimizations for linux, ubuntu just doesnt use any of them. The link in my sig for prelinking does help application load times quite a bit, but ubuntu is not prelinked by default.

---

### Post by fannymites on 2006-01-25
But I still say ubuntu gnome is quicker than than suse gnome.  It's only when running in kde that suse shows it's speed.
As for prelinking, I've turned it off on boot on suse and haven't noticed any difference in the speed of apps launching but it seems to boot quicker without it.

---

### Post by drizek on 2006-01-25
thats preloading, not prelinking.

---

### Post by fannymites on 2006-01-25
Yeah, I realised after I posted but I felt too stupid to edit it so I left it and hoped no-one noticed.

---

### Post by ace2005 on 2006-01-25
I'm stuck in windows at the moment, no middle click :(, tried to upgrade to dapper, didn't go so well, kde screwed up, something to do with KDE, anyway, so i tried debian stable, wanted KDE 3.5, went to sid, wanted kernel 2.6.15, installed it, kernel panic, lilo related, damn!, reinstalled, chose grub, manually edited the sources list to sid, installed ok, KDE wasn't installed, used second PC as a gateway, installed KDE, found kernel 2.6.15, installed it, udev was upgraded hotplug was removed, the kernel couldn't compile the eagle-usb driver bla bla bla, found new kernel with eagle-usb already compiled as well as nvidia, installed this one, all seemed ok, mouse problem, xorg wouldn't work, thought i could install kubuntu's kernel, the modem and nvidia worked fine on that, installed them, downgraded udev, reinstalled hotplug, started x, without a mouse by setting the device to /dev/tts0 or something similar, but the mouse wouldn't work, but xorg worked and had a gui, logged in, kde won't login, gets stuck at loading initialising services, disconnected from the net, killed x, logged in, and it worked, got to the desktop, initialised the modem, it crased, something to do with the modem, i gave up, thought i'll reinstall Kubuntu, kubuntu DVD is scratched, so i'm downloading Kanotix now and i hope this works [-o< [-o< [-o< 

If it doesn't i'll just wait for the new version of Kubuntu, good timing to screw up i guess

---

### Post by pelle.k on 2006-01-25
I installed suse 10.0 a couple days, and i don't know how large the difference in speed is between 10.0 and 10.1, but i can assure you - suse wasn't running any quicker (at all) than my present kubuntu setup. Kubuntu is among "the snappier" distros i've tried for sure. So i can't really relate to what you are saying, but i've tried PCLinuxOS out, which is a great, relly great, distro too, but it bogged down my computer bad, compared to kubuntu really. Xfce is what i'd like to call REALLY snappy though, but i love KDE, and it has become a trend lately, that KDE gets faster for every release. There are also some well known modifications you can make to speed up kubuntu, which ships with a default 386 kernel, and most often not the "correct" driver to get full hardware acceleration. Do you for instance know what "preemption model" your default kernel is compiled with? This has huge impact on GUI/WM reaction/latency... Just recently i found that if you add *Option "RenderAccel" "True"* to "Device" section in your xorg.conf, using an nvidia card and the newer nvidia driver, some things become "snappier" than ever before, like marking large areas with the mouse pointer in KDE. And... i'd like to add - if i remember correctly, KDE 3.4.3 was "rushed" into breezy because of the lack of time. Can it be that this has negative consequenses on some desktop setups?

[edit]And what's the deal with KDE 3.5 people :) People go crazy over it! Sure there are some improvements, but it's not like it's gonna change your life or anything. It's like 3 months until dapper is released. You'll survive. I would personally advice you not too upgrade breezy to KDE 3.5, because it's not as stable as 3.4.3 in kubuntu, and it never will be until dapper. well... enough of my useless rants :) [/edit]

---

### Post by drizek on 2006-01-25
in a few weeks(days?) well get 3.5.1 in dapper, which should be more stable than 3.4.3. Also, with the version freeze, dapper will start becoming more and more stable from here till the release.

However, i just finished installing gentoo. still dont have any apps loaded or anything. i booted back into ubuntu cause i, like an idiot, forgot to emerge dhcpd during the install, so i dont have internet, lol. now i have to chroot into gentoo to emerge it from ubuntu. Anyway, other than that the install went well, and it feels cool to have compiled my first custom kernel, after TWO years of using linux. i should have done this sooner...

---

### Post by nianhbg on 2006-01-29
[QUOTE=moopere]Get back to us here on this thread if you can actually benchmark or otherwise quantify any speed differences beteen ubuntu and gentoo - I'm really interested as it seems to me that Linux (not just ubuntu) systems are getting slower and slower as time goes by.  

I'm just starting to get into a serious set of kernel and other compiles with benches to try and see if I can't work out whats going on....for sure something is up these days as I have a rack full of 200->1GHz machines here all of which used to run things like Debian Woody and SuSE 6.4 and so on really really fast, but now can't even run a basic ubuntu/suse/redhat installation.

As a beginning I have recently compiled a stock breezy kernel for i586 and did some benching on a P200 (classic) versus the ubuntu i386 stock breezy kernel...I gotta tell you, theres not a lot in it.  In fact, given enough runs I think the averages would collapse to around a delta of zero.

This was pretty dissapointing I have to say, I was expecting at least some measurable change, which is why I'm pretty interested in the results you get with Gentoo - if you compile not just the kernel but _everything_ will you get measurable speed increases and will those increases be large enough to justify the huge amount of time and effort expended?

Cheers,
Craig[/QUOTE]

I'm new to linux. And my first installation i made was a gentoo installaiton. Gento was running quite fast on my machine. Then I installed Ubuntu with Gnome and i love it, but it a lot slower. In my gentoo installation i compiled everything.

---

### Post by tdell on 2006-01-29
Not sure. It is one of the resaons I switched to SUSE from Ubuntu, Networking was painfully slow on Ubuntu, in SUSE it was iinstantaneous

Tom

---

### Post by Adrian on 2006-01-29
OK, I installed Gentoo (and learned a lot on the way!), but couldn't make KDevelop work as it should. That seems to be a bug that troubles more people than me, so I decided to return back to openSUSE again (yes, I really need KDevelop).

While Gentoo was quick, I was surprised to see that it wasn't noticably faster than openSUSE (yes, I used the "optimal" CFlags for my Coppermine Celeron processor).

My only problem with SUSE is really the fonts. They look somewhat blurry on my 800x600 screen when anti-aliasing is enabled. I've changed the DPI to 75, which is the same as I used in other distributions. It's not a big difference, but it's still annoying enough. The best solution so far has been to disable anti-aliasing.

---

### Post by kakashi on 2006-01-29
[QUOTE=Adrian]Why is Suse faster than Ubuntu on my machine?

Problem: Everything X-related takes A LOT more cpu in Ubuntu than SUSE. This makes my laptop fan spin, which is pretty annoying to say the least.
[/QUOTE]
perhaps ubuntu is not properly configuring your video hardware. look into it.

---

### Post by Adrian on 2006-01-29
[QUOTE=kakashi]perhaps ubuntu is not properly configuring your video hardware. look into it.[/QUOTE]

As stated aboive, it's a basic Trident Cyberblade i1, using the **trident** driver. Even when using SUSE's xorg.conf in Ubuntu, I get the same problems.

So, what more can I do? Are there any other configuration files that I've missed?

---

