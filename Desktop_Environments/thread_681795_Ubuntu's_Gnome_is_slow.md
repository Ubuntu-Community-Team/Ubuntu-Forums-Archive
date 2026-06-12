---
title: "Ubuntu's Gnome **is** slow"
date: 2008-01-29
forum: Desktop Environments
---

### Post by FFighter on 2008-01-29
And I mean in every aspect. I've been using Ubuntu 7.10 for a few weeks on Dell Optiplex Pentium 4 3Ghz, 2GB RAM and its rendering speed in unacceptable. It just doesn't feel agile like the KDE, XFCE or the Windows GUI. And btw, the Windows GUI is one of the fastest in terms of rendering speed and responsiveness in my opinion.

I don't know if it's GTK, or if the particular Gnome distro. of Ubuntu Gutsy has something wrong. The fact is that Gnome feels slow, period.

XFCE is way better but it is still GTK and sometimes the rendering seems to be a little faulty (such as you seeing a rectange (menu for example) disappearing slowly when it is discarded instead of disappearing instantly (at least in a timeframe in which our eyes can't perceive).

KDE, on the other hand, always felt more responsive.

Would you mind sharing your experiences? Maybe we could arrive into a conclusion on why Gnome/GTK feels so slow.

---

### Post by PurposeOfReason on 2008-01-29
When I use gnome in archlinux I don't have any of the problems you mentioned. I do feel it a lot slower when I used Ubuntu though.

---

### Post by rfruth on 2008-01-29
I turn OFF indexing (System >> Preferences)

---

### Post by depele on 2008-01-29
I have the same problem with a fresh install of ubuntu 7.10.

proc: 2.8
ram: 512

I allready disabled compiz.

But still very slow.

---

### Post by FFighter on 2008-01-29
> **PurposeOfReason said:**
> When I use gnome in archlinux I don't have any of the problems you mentioned. I do feel it a lot slower when I used Ubuntu though.

Hmmm... interesting. I might try installing and give Arch a try. Thanks for the feedback.

EDIT: I was also eager to try Fluxbuntu, it seems it is very lightweight and agile. But still, Gnome should not be that slow. Something is wrong with Gutsy in this aspect.

---

### Post by Crakie on 2008-01-29
Usually the complaint is the other way round: KDE being bloated and sluggish and Gnome being more responsive. Other DE's and WM's are definetely faster than both. 

Perhaps Gnome isn't getting along with some some particular piece of your hardware, which may be solved with some obscure setting. I would not know where to start there, but there has not been a single Linux problem that could not be solved with a little googling or posting in fora.

Arch is most certainly faster than Ubuntu, but requires more knowlegde and willingness to tinker.

---

### Post by samwyse on 2008-01-29
GTK2 is slower than QT. Also the Gnome window manager (Metacity) is slow.

---

### Post by Robstarusa on 2008-01-29
My machine is as follows

Turion TL-50 (which most of the time I run @ 800mhz instead of 1600)
4G ram, ubuntu desktop x86_64

I installed proprietary drivers, turned off all desktop effects & made my theme mist.

That sped everything up considerably.

---

### Post by Phasma on 2008-01-29
Ubuntu just seems to be a considerably slow distro in general. The nice thing though is debian based, and its easy to setup. And for some reason I have become accustomed to using SUDO

---

### Post by frankos44 on 2008-01-29
I loaded Ubuntu on many PC's. 

Mostly they run much faster than windows but I have to agree that with some PC's I find Ubuntu a bit slow. 

I think its purely down to the hardware combination rather than PC's specification. If you are unlucky you could be disappointed with Ubuntu but the majority will be very happy with performance.

I tried Genrtoo 64 bit on my own computer and that does seem to run faster even though Ubuntu works very well anyway. BUT... Gentoo is not easy to set up, not for the faint hearted.

You have top make a choice, ease of use or hours of configuration. Ubuntu is a good all rounder.

---

### Post by RavanH on 2008-01-29
Same here on an AMD64 system. I am sure that the sluggishness I get from Ubuntu is down to the ATI driver... So hardware could indeed be a problem maker for you too. I decided to turn off desktop effects and that improved things a lot. Only Cairo Dock does not render like it should anymore (no transparency), just when I had grown so fond of it...

I installed XFce (with sudo apt-get xubuntu-desktop) and when logged in to a XFce session, the speed is considerably faster. With the limited 'desktop effects' in XFce turned on (shading and transparency) I am quite happy. Cairo Dock now works great too! :)

Speed, usability and slick looks, I find them combined in XFce (with CairoDock giving it an OS X look). So goodbye Ubuntu, hello Xubuntu ;)

---

### Post by Phasma on 2008-01-29
> **frankos44 said:**
> I loaded Ubuntu on many PC's. 

Mostly they run much faster than windows but I have to agree that with some PC's I find Ubuntu a bit slow. 

I think its purely down to the hardware combination rather than PC's specification. If you are unlucky you could be disappointed with Ubuntu but the majority will be very happy with performance.

I tried Genrtoo 64 bit on my own computer and that does seem to run faster even though Ubuntu works very well anyway. BUT... Gentoo is not easy to set up, not for the faint hearted.

You have top make a choice, ease of use or hours of configuration. Ubuntu is a good all rounder.

Ubuntu is good for someone not familiar with Linux, too lazy to setup Gentoo, or someone that enjoys the community around it.

On that note I have notticed Fedora, Debian, RHEL, and CentOS are all quicker than ubuntu, and still easy to setup.

---

### Post by forceofnature on 2008-01-29
For the most part I find Ubuntu acceptable for speed with the exception of GIMP.  I find that GIMP performs filter operations slower than Photoshop CS3 on XP.  I am using an AMD XP 3000+ 1 G ram and 160G hdd with an old PCI Nvidia fx5200.

---

### Post by Phasma on 2008-01-29
> **forceofnature said:**
> For the most part I find Ubuntu acceptable for speed with the exception of GIMP.  I find that GIMP performs filter operations slower than Photoshop CS3 on XP.  I am using an AMD XP 3000+ 1 G ram and 160G hdd with an old PCI Nvidia fx5200.

I haven't ever loaded windows on my desktop so it wouldn't be a good comparison, but my laptop is a different story. 1.6 Dual core AMD with 2 gigs of ram and a Geforce 6300

Photoshop seems to be a bit quicker, but really not by much. Also the scripts for rendering in Photoshop are written in a certain language. The gimp stuff is written in python, so it gets passed through a parser first

I think when I get home im going to run Photoshop in Wine and do a comparison for filter operations with the GIMP on the beast. (4 gigs of ram, AMD Dual Core 5000+ Geforce 8600GT)

---

### Post by FFighter on 2008-01-30
Yes, maybe it's time for me  to start playing with more hard-core distros (Gentoo, Slack or even Linux From Scratch), after all, after one year and a half using Ubuntu I might say that I'm very comfortable with the CLI and the bash, and one thing that Ubuntu does well is acting as an entry to the "lower-level" world of GNU/Linux.

However, the point of this post is to find out why Ubuntu's Gnome, or Ubuntu in general is slow compared to other distros (even on high-end hardware). Is that because of poor drivers? Is it because Ubuntu is "bloated" software? Maybe some default obscure configuration?

I will install Fluxbuntu @ home this weekend and share my experiences. It should give some insight regarding this issue.

It could be also useful to install a "bare-bones" Ubuntu and then trying to install Gnome from source... but yes, I'm too lazy... :)

---

### Post by regomodo on 2008-01-30
> **forceofnature said:**
> For the most part I find Ubuntu acceptable for speed with the exception of GIMP.  I find that GIMP performs filter operations slower than Photoshop CS3 on XP.  I am using an AMD XP 3000+ 1 G ram and 160G hdd with an old PCI Nvidia fx5200.

A lot of gimp fans would blindly disagree with you but i feel the same way as i do. This isn't my blog but somebody [benchmarked qt]("http://zrusin.blogspot.com/2006/10/benchmarks.html"). Aparently the gimp's slowness is due to the gtk2 toolkit

---

### Post by frankos44 on 2008-01-30
> **Phasma said:**
> Ubuntu is good for someone not familiar with Linux, too lazy to setup Gentoo, or someone that enjoys the community around it.

On that note I have notticed Fedora, Debian, RHEL, and CentOS are all quicker than ubuntu, and still easy to setup.

My experience says there is little difference between the binary non-optimized distros.  It stands to reason that optimized installations like Gentoo stand a chance of running faster as they will be optimized to a specific PC, however there is a price to pay..... effort, not to be confused with being lazy.  

Is the fractional increase in speed worth the effort? we are not racing formula one cars hunting down 1/10 sec in 2.5 mile lap.

I hope you are not judging performance on boot time alone.

---

### Post by FFighter on 2008-01-30
> **frankos44 said:**
> My experience says there is little difference between the binary non-optimized distros.  It stands to reason that optimized installations like Gentoo stand a chance of running faster as they will be optimized to a specific PC, however there is a price to pay..... effort, not to be confused with being lazy.  

Is the fractional increase in speed worth the effort? we are not racing formula one cars hunting down 1/10 sec in 2.5 mile lap.

I hope you are not judging performance on boot time alone.

Yes, Gentoo has the advantage of allowing you to fine-tune the binary output. However, other binary distros. that are fast and agile exist, or not?

I wonder why you would have to compile everything from source to have a fast OS. I agree that it is fun and a very rewarding experience (if you've got the time and willingness) to build a system from source, and that you can do whatever you want and make things the way you want, but arguing that a binary (pre-compiled) linux system is inexorably slower than source distros is not a very clear argument IMHO. 

Btw, why not trying Linux From Scratch instead of Gentoo? :)

---

### Post by frankos44 on 2008-01-30
> **FFighter said:**
> Yes, Gentoo has the advantage of allowing you to fine-tune the binary output. However, other binary distros. that are fast and agile exist, or not?

I wonder why you would have to compile everything from source to have a fast OS. I agree that it is fun and a very rewarding experience (if you've got the time and willingness) to build a system from source, and that you can do whatever you want and make things the way you want, but arguing that a binary (pre-compiled) linux system is inexorably slower than source distros is not a very clear argument IMHO. 

Btw, why not trying Linux From Scratch instead of Gentoo? :)

You cant compile and optimize for my computer and expect it to run on yours. Even if we have the same Intel P4 and memory, your graphics card will differ from mine and your network adapter, sound and support chipsets will be different.  

Like I said in an earlier post, I dont think the difference is worth the effort.  I think many get confused because for them, changing distros made a huge difference and in their case it may have been due to hardware support and drivers.  

Microsoft have been at this game for years, these days they expect every piece of hardware component thats sold on the market to be shipped with a CD and be supported by the manufacturer. In turn the software will most likely be optimized by the manufacturer as they want their product to out perform the competition.

When you think about it Miicrosoft have been very clever, they dont even have to get their hands dirty for their extortionate fees. With this in mind they have done a terrible job over the last decade, we should be looking at something far more advanced than vista or XP?

---

### Post by Lean 946 on 2008-01-30
i use GNOME and its faster than another DE's, in fact, in my pc (Pentium 3, 192MB RAM) its faster GNOME than Xfce or KDE

---

### Post by Phasma on 2008-01-30
> **frankos44 said:**
> My experience says there is little difference between the binary non-optimized distros.  It stands to reason that optimized installations like Gentoo stand a chance of running faster as they will be optimized to a specific PC, however there is a price to pay..... effort, not to be confused with being lazy.  

Is the fractional increase in speed worth the effort? we are not racing formula one cars hunting down 1/10 sec in 2.5 mile lap.

I hope you are not judging performance on boot time alone.

Boot up time is a horrible judge of speed. I dont even concern myself with boot up time on my laptop. 

I do notice a difference in application response and memory usage on other distros that I have mentioned.

About 5 years ago I built a LFS box. Now that was a very very fast box. I would say Gentoo is comparable to LFS.

I think part of the sluggishness that ubuntu has is from the kernel. There is so much in that kernel. On top of that the kernel isn't optimized (which I think is one of the few binaries that plays a roll on speed). Dapper included optimized kernels that you could install. They improved the system overall. I wish that was something that they would still do because I don't have as much time on my hands as I used to I cant be compiling and testing kernels to make speed improvements.

What I found odd is on my machine with an ATI onboard setup the kernel was still loading some kind of nvidia module on boot. Seems like more bloat than is needed.


With all of that said I put Photoshop CS2 running in Wine up against the GIMP.

Starting CS2 takes a good bit of time but once it is running it is almost at native speeds. The gimp starts up much quicker. (and I run KDE with no GNOME extentions loaded at startup.)

Filter operations on the same image took about the same amount of time. I agree the GIMP is slower.

---

### Post by regomodo on 2008-01-30
> **Lean 946 said:**
> i use GNOME and its faster than another DE's, in fact, in my pc (Pentium 3, 192MB RAM) its faster GNOME than Xfce or KDE

I find that very, very hard to believe. In my experience  gnome is the slowest "even more so in Gutsy due to tracker), followed by KDE, XFCE, openbox, fluxbox, LXDE, icewm and JWM. In that order.

---

### Post by FFighter on 2008-01-30
> **regomodo said:**
> I find that very, very hard to believe. In my experience  gnome is the slowest "even more so in Gutsy due to tracker), followed by KDE, XFCE, openbox, fluxbox, LXDE, icewm and JWM. In that order.

Yes, Gnome is the slowest of them all.

What do you think about the Mac OSX GUI? I've never used Mac OSX so I can't comment, but it seems to be slick and fast.

The Windows XP GUI (Can't tell about Vista) is also very responsive.

---

### Post by frankos44 on 2008-01-31
> **FFighter said:**
> Hmmm... interesting. I might try installing and give Arch a try. Thanks for the feedback.

EDIT: I was also eager to try Fluxbuntu, it seems it is very lightweight and agile. But still, Gnome should not be that slow. Something is wrong with Gutsy in this aspect.

Let me know how you get on with Arch..

---

### Post by samwyse on 2008-01-31
> **samwyse said:**
> GTK2 is slower than QT. Also the Gnome window manager (Metacity) is slow.

Well, I tried Gnome again and didn't find it slow.

---

### Post by Phasma on 2008-01-31
One of the things I have never understood is why debian based distros still compile for a 386 archetecture. Ubuntu especially, It isn't like there is a 386 around that can handle running so much as just a CLI install. At least optimize for 586 or 686 instruction sets. I think that would have a larger benefit for speed in the OS than people believe.

When I was playing with LFS it was a super fast system. Everything was very responsive and thing's compiled significantly faster. Those arch flags make the difference in the core libraries and kernel. That is why there is a gain.

Arch linux, Gentoo, LFS are all a testament to that.

---

### Post by schmolch on 2008-01-31
I have 8 different Distros* installed on my Laptop** and Gnome under Ubuntu doesn't feel any slower/faster than on the others.

*Ubuntu-7.10, Ubuntu-Hardy, opensuse-10.3, opensuse factory, fedora8, fedora rawhide, gentoo-linux x86, gentoo-linux ~x86
** thinkpad x60t (cd 1.8, 2GB, 80GB 5400rpm hdd, sxga+ tablet-pc)

---

### Post by schmolch on 2008-01-31
Do you use a nvidia card?
On my Desktop with nvidia-cards gnome/gtk is slow too.

---

### Post by imtheguru on 2008-01-31
> **FFighter said:**
> Yes, Gentoo has the advantage of allowing you to fine-tune the binary output. However, other binary distros. that are fast and agile exist, or not?

I wonder why you would have to compile everything from source to have a fast OS. I agree that it is fun and a very rewarding experience (if you've got the time and willingness) to build a system from source, and that you can do whatever you want and make things the way you want, but arguing that a binary (pre-compiled) linux system is inexorably slower than source distros is not a very clear argument IMHO. 

Btw, why not trying Linux From Scratch instead of Gentoo? :)Because, they've been benchmarked and, in the average case, the performance gains are no more than 3-4% than a pre-compiled system.

LFS is only really worth it for render farms or GCC nodes... computers which are expected to run at 100% capacity for most of their operational lives.

Cheers.

---

### Post by frankos44 on 2008-02-01
> **Lean 946 said:**
> i use GNOME and its faster than another DE's, in fact, in my pc (Pentium 3, 192MB RAM) its faster GNOME than Xfce or KDE

This just supports what I have been saying. I feel that It hass nothing to do with computer specification or GNOME being slow, its purely that your hardware combination is perfect for Ubuntu, it might just be it will be sluggish on another distro.

One thing I have noticed is all computers using Intel Pentium with Intel support chips and Intel Graphics controllers I have played with work very well indeed with Ubuntu and would probable work well with other distros also.

Its not going to be easy to make any generalized comment on one distro being better than another because each person adding to this thread will base it on their own PC and their own experience. Once they change their PC, they may just change their mind.

---

### Post by FFighter on 2008-02-01
It seems this Ubuntu's 7.10 Gnome/metacity/GTK2 slowdown is a real issue. See other recent, similar posts.

[http://ubuntuforums.org/showthread.php?t=682988](http://ubuntuforums.org/showthread.php?t=682988)
[http://ubuntuforums.org/showthread.php?t=670950](http://ubuntuforums.org/showthread.php?t=670950)

I specially disagree with an answer in the second post, comparing the XP GUI with Fluxbox. The XP guy/DE can be 8 years old, but is significantly more complex than Fluxbox.

I don't think you could also judge the speed of the Windows XP GUI based on its age.

Windows XP DE **is** more responsive than Ubuntu's Gnome and is more complex (more features).

I'm not saying Gnome is bad, I really liked it, I just wish it was faster!

---

### Post by Asham on 2008-02-02
I hear ya! I share the same opinions. 

I come from having used MS Windows for like 10+ years to Ubuntu and Gnome, and I too noticed the responsiveness and the general speed of Gnome (GTK) is not quite top notch. It's not even close to being bad or un-usable, but it could be a tad faster. :)

---

### Post by Phasma on 2008-02-02
> **FFighter said:**
> It seems this Ubuntu's 7.10 Gnome/metacity/GTK2 slowdown is a real issue. See other recent, similar posts.

[http://ubuntuforums.org/showthread.php?t=682988](http://ubuntuforums.org/showthread.php?t=682988)
[http://ubuntuforums.org/showthread.php?t=670950](http://ubuntuforums.org/showthread.php?t=670950)

I specially disagree with an answer in the second post, comparing the XP GUI with Fluxbox. The XP guy/DE can be 8 years old, but is significantly more complex than Fluxbox.

I don't think you could also judge the speed of the Windows XP GUI based on its age.

Windows XP DE **is** more responsive than Ubuntu's Gnome and is more complex (more features).

I'm not saying Gnome is bad, I really liked it, I just wish it was faster!

Seriously try installing another GNOME based distro and do just a speed comparison with GNOME. Redhat. Gentoo, SuSE will all be quicker. Then go look at what arch those are compiled for.

Setting the arch flag for compiling packages DOES make a difference. A rather large difference. I just wish Debian and the derivatives would also see that. 

I haven't owned a computer that didn't support i686 or better arch in over 13 years. Now why deal with antiquated instruction sets, when processors for the last 15 years have support optimized instruction sets. It isn't like the machines that are only a i386 arch have the balls to run an Ubuntu install, or hell I would be surprised if they could even load a 2.6.x kernel without running into issues.

So again, why support antiquated arch? There is NO point to it.](*,)](*,)](*,)

---

### Post by Menzonius on 2008-02-03
Does anybody else experience *terrible* lag by the way, when selecting a large list of files/directories in Nautilus by using the shift and arrow keys? What's up with that?
I think Gnome is definitely faster on other systems.

---

### Post by frankos44 on 2008-02-03
> **FFighter said:**
> And I mean in every aspect. I've been using Ubuntu 7.10 for a few weeks on Dell Optiplex Pentium 4 3Ghz, 2GB RAM and its rendering speed in unacceptable. It just doesn't feel agile like the KDE, XFCE or the Windows GUI. And btw, the Windows GUI is one of the fastest in terms of rendering speed and responsiveness in my opinion.

I don't know if it's GTK, or if the particular Gnome distro. of Ubuntu Gutsy has something wrong. The fact is that Gnome feels slow, period.

XFCE is way better but it is still GTK and sometimes the rendering seems to be a little faulty (such as you seeing a rectange (menu for example) disappearing slowly when it is discarded instead of disappearing instantly (at least in a timeframe in which our eyes can't perceive).

KDE, on the other hand, always felt more responsive.

Would you mind sharing your experiences? Maybe we could arrive into a conclusion on why Gnome/GTK feels so slow.

You gotta have something wrong. Ubuntu / GNOME is instantaneous on my PC, no delays with video performance and apps run up very quickly. It has to be a hardware / driver issue.

---

### Post by jbaerbock on 2008-02-03
Personaly I use KDE because Gnome seems sluggish to me. Such as boxes disapearing after I hit ok etc...very slow. XFCE is awesome but Gnome things are slipping in there already so it is only a matter of time before it goes slower and slower as well. KDE is slower than WindowsXP but it is fast enough to be acceptable. Fluxbox is fast but not very user friendly like KDE.

---

### Post by markharding557 on 2008-02-03
i use debian testing/sid with gnome these days and i have noticed it is considerably quicker than ubuntu.
this may be due to using a k7 optimized kernel for my processor though

---

### Post by regomodo on 2008-02-05
> **markharding557 said:**
> i use debian testing/sid with gnome these days and i have noticed it is considerably quicker than ubuntu.
this may be due to using a k7 optimized kernel for my processor though

it could be due to your k7 kernel but i found exactly the same thing. Ubuntu/gnome ran like a dog on my laptop but Debian Lenny/gnome was almost as fast as xfce. All comes down to convenience vs speed

---

### Post by linux phreak on 2008-02-05
I would advise any one  frustrated with ubuntu to try Xubuntu.It is way faster and almost as featurefilled as ubuntu.The system sounds are the things i miss in xubuntu or is it there hidden somewhere?

---

### Post by thepocketdrummer on 2008-02-06
I'm not sure why everyone is experiencing issues. I have an athlon 64 X2 4200+ (@2.7Ghz), 2GB of ram, and a 7800GT and it's very zippy for me. Even with Compiz maxed.

I WILL say that I've bricked the OS 4 times in two days. Where's this stability everyone keeps preaching?:confused:

---

### Post by geokker on 2008-02-06
Yes, Ubuntu Gutsy 64bit is slow for me too. Windows XP on the same hardware is much, much faster. In fact, XP running on VirtualBox is faster! I'm tempted to install Windows 2000 - it would surely fly on my modern kit.

In addition to general sluggishness with Gnome, the amazing instability of Firefox, the bloat of open office, the dumbness of gnome-panel, closing apps down during shutdown, the myriad runaway processes - all of these issues conspire to erode my enjoyment of open source.

I'm willing to give any other WM or distro a try but I've tried many and they're much the same in the performance stakes.

---

### Post by FFighter on 2008-02-06
> In addition to general sluggishness with Gnome, the amazing instability of Firefox, the bloat of open office, the dumbness of gnome-panel, closing apps down during shutdown, the myriad runaway processes - all of these issues conspire to erode my enjoyment of open source.

I feel your pain. That's exactly what I've been experiencing with Ubuntu, since I started using it with Feisty Fawn. 

Don't get me wrong. Ubuntu is great, in overall. But things (as I've heard) started to get bloated, slow and unstable with 7.04. I give Ubuntu all the credits for being the way in which I entered the Linux world, though, and that's one of the great things it is doing for Linux.

I already decided to "take some days off" and install Gentoo, I think it is about time I migrate to a "more pure" linux distro.

---

### Post by frankos44 on 2008-02-06
> **FFighter said:**
> I feel your pain. That's exactly what I've been experiencing with Ubuntu, since I started using it with Feisty Fawn. 

Don't get me wrong. Ubuntu is great, in overall. But things (as I've heard) started to get bloated, slow and unstable with 7.04. I give Ubuntu all the credits for being the way in which I entered the Linux world, though, and that's one of the great things it is doing for Linux.

I already decided to "take some days off" and install Gentoo, I think it is about time I migrate to a "more pure" linux distro.

Done that and the speed difference was hardly measurable... get a decent pc cus the problem dont  exist here. My PC is very quick with both systems. The spec is: P4 3G 533/800Mhz bus, 1G RAM, Intel 915 Chipset with SATA 300G hard drive. Perhaps your hardware is not using correct drivers.. look into that first, or maybe you dont have enough RAM.

After playing around with LFS for a few days and not getting all the apps I needed to work, then doing the same exercise with Gentoo,   I was pleased to get back to Ubuntu, at least it verfied to me that it made little difference.

I will be interested in your experiences though, keep me posted.. Thanks

---

### Post by noogen on 2008-02-06
Gnome use to be slow for me too.  It was because I was not using the right graphic driver.  I think having good graphic will make gnome faster.  

Because I have had problem in gnome, I have try out Kubuntu (KDE) and it seem to be much faster even with the slower graphic driver.  One thing I notice about GNome is that if one app crash/freeze with hour glass, it stop you from starting any other app.  On the other hand, KDE seem to use separate thread/process for each app so crashing app doesn't effect performance of other app.

All experience are from installations of Gutsy 64 bit (Kubuntu and ubuntu).  I am now running in stable Gutsy 64 bit server installlation with gnome (ubuntu-desktop).  I understand the limited software availability and stability in 64 bit so I have 8 gb to run virtual machines.  Speed benefits of running virtual machine in 64 bit allow me to seamlessly run other applications in my xp virtual machines.  

My 0.02c.

---

### Post by geokker on 2008-02-06
+1 for xubuntu. XFCE (albeit with nautilus) is quicker and less stodgy for me. Compositing in xfce4 seems 'lighter' and just as effective.

On the graphics driver issue, I have a couple of powerpc Macs running Tiger. These are not powerful machines and the graphics cards are 'slight' yet, the serious GUI effects are smooth. I've got the hardware muscle, I *know* the software isn't tapping it in any flavour of Linux WM.

---

### Post by NJC on 2008-02-06
Gnome feels slow to me too - on all 3 PC's I've had it installed. I currently have a dualboot XP/Gutsy 1.3Ghz Duron 640 MB ATI 64MB. XP must be 75-100% faster than Ubuntu ... but it's an apples to oranges comparision since Win is 7yrs old, and Ubuntu <1yr. 
 
Maybe Win has a faster GUI period. Maybe something to give them credit for?? And given time, Gnome will probably get there too.

---

### Post by kevinatkins on 2008-02-06
Interesting thread. From my experience so far, Gnome currently feels somewhat slower than KDE (it used to be the other way around...)..

And I think Ubuntu is one of the slower distros - I recently tried Mandriva 2008 on a Dell Inspiron 2500 laptop (P3 1GHz, 384MB RAM) and it felt just as snappy as Ubuntu 7.10 on my AMD XP2 4400 64 bit rig with 1GB RAM!!

Only problem was that Mandriva felt very rough around the edges to me - nice distro, just not my cup of tea... So I've just loaded Fedora 8 onto the laptop and it's about par with Ubuntu on that same machine - not as quick as Mandriva.. 

Still, I find Ubuntu good enough all round - I keep coming back to it because, on the whole it does a good job, although some very annoying bugs have been creeping in over the last couple of releases.. And to back up what one of you has already written, Firefox is pretty dismal - far too many crashes and lock-ups (the same seems to afflict Windows builds, too)

---

### Post by Raptor Ramjet on 2008-02-06
Well sadly I have to agree as I too find Gnome to be very slow.

One of the worst things is selecting multiple files in Nautilus using the keyboard.  i.e. select a single file then hold down shift and press page down a few times to select multiple files.  In a directory with a large number of files using this method can be "dog slow".

Using the same technique in Windows Explorer seems lightning fast in comparison.

In fact all in all I'd agree that Gnome just simply feels sluggish.

Oh well, just though I'd add my tu'ppence worth :)

---

### Post by Menzonius on 2008-02-06
> **Raptor Ramjet said:**
> 
One of the worst things is selecting multiple files in Nautilus using the keyboard.  i.e. select a single file then hold down shift and press page down a few times to select multiple files.  In a directory with a large number of files using this method can be "dog slow".


I experience *exactly* the same problem and I agree completely that this is extremely annoying, so it's nice to hear I'm not the only one. I particularly hate it when long after I've let go of the shift key, it just keeps on going and selecting files/dirs I never wanted to select. If you do that in rapid succession, de-selecting and selecting many files, you could go out for coffee for like five minutes, and it will still be going up and down by the time you get back :shock:

I have a reasonably fast system, with a sata drive, an Athlon XP 2600+ CPU, 512DDR ram, and 128MB nVidia FX5700. It's  certainly not the fastest hardware anymore, but certainly meets the hardware requirements for running Ubuntu, and even runs full Compiz desktop effects with no problems whatsoever. AFAICT, here is just no reason for Nautilus to behave like this.

---

### Post by frankos44 on 2008-02-06
Its beginning to look s if every one who is complaining about Gnome being slow is running nVidia graphics card.  Just so happens that all my computers here have Intel graphics and mine are all OK. Maybe this is the key to the problem?

---

### Post by cprofitt on 2008-02-06
> **FFighter said:**
> Yes, Gnome is the slowest of them all.

What do you think about the Mac OSX GUI? I've never used Mac OSX so I can't comment, but it seems to be slick and fast.

The Windows XP GUI (Can't tell about Vista) is also very responsive.

Vista's GUI with all the extras is much more responsive than Gnome or KDE on my work laptop.

---

### Post by frankos44 on 2008-02-07
Im not sure if this helps but the slowness of gnome on ubuntu using nVidia might be something to do with not having hardware acceleration, try this:

[http://packages.ubuntu.com/feisty/misc/nvidia-glx-new](http://packages.ubuntu.com/feisty/misc/nvidia-glx-new)

Please let em know if it helps.

---

### Post by Menzonius on 2008-02-07
> **frankos44 said:**
> Im not sure if this helps but the slowness of gnome on ubuntu using nVidia might be something to do with not having hardware acceleration, try this:

[http://packages.ubuntu.com/feisty/misc/nvidia-glx-new](http://packages.ubuntu.com/feisty/misc/nvidia-glx-new)

Please let em know if it helps.

I'm afraid not in my case, hardware acceleration is definitely active; I've edited xorg.conf manually and tested it with glxinfo and glxgears. Games run just fine and the compiz desktop effects work very well too. As these things surely require accelerated graphics to work, I don't see how in this aspect it could be related to my graphics card. 

Maybe if I have some free time to test this, I'll try it with the Xorg "nv" driver, without compiz effects, and see if that changes anything. 

One thing I do notice in any event is that CPU usage goes through the roof when I try selecting a load of stuff in Nautilus, does that happen for you as well?

---

### Post by frankos44 on 2008-02-07
> **Menzonius said:**
> I'm afraid not in my case, hardware acceleration is definitely active; I've edited xorg.conf manually and tested it with glxinfo and glxgears. Games run just fine and the compiz desktop effects work very well too. As these things surely require accelerated graphics to work, I don't see how in this aspect it could be related to my graphics card. 

Maybe if I have some free time to test this, I'll try it with the Xorg "nv" driver, without compiz effects, and see if that changes anything. 

One thing I do notice in any event is that CPU usage goes through the roof when I try selecting a load of stuff in Nautilus, does that happen for you as well?

I must admit im puzzled by this thread because at the end of the day my machine is very quick. My laptop is quick and my daughters computer is quick and I mean impressive. 

I do recall one of my customers Dell machine being very sluggish some time ago but I dont have it here to investigate why and I cant remember the spec of that machine either.

The only common denominator here is all PC's have intel support chip-sets and Intel graphic controllers. That was my reason for my speculation. 

If you have anything like that to test with I would be interested to find out if you still think Ununtu is sluggish.

---

### Post by julius malchovitch on 2008-02-07
Don't want to start a flame war with this post but I am deeply concerned we have to blame GTK for the Gnome poor responsiveness.

I really don't know GTK internals but I have a little development experience with GTK, QT and MFC and I have to say that both QT and MFC seem to be much better engineered APIs.

This is a real pity 'cause actually Gnome, in my opinion, looks much more 'professional' than KDE, and it's adoption in the enterprise world could suffer a lot from its poor performance.

MS XP and Vista (with full Aero enabled) feel _much_ more responsive on my systems.

Luca

---

### Post by NJC on 2008-02-07
> **frankos44 said:**
> Its beginning to look s if every one who is complaining about Gnome being slow is running nVidia graphics card. Just so happens that all my computers here have Intel graphics and mine are all OK.
 
I've used Gnome on a Matrox G200 8MB, on-board Intel i810e chipset and now ATI Radeon 7000 64MB - ALL molasses. I'd fully expect the former 2 to be slow, but not the ATI. Having said that, I understand ATI does not have Linux driver support as good as NVidia.

---

### Post by Charcoal1981 on 2008-02-07
I'm running an athlon 2800+, 1GB RAM and an Nvidia FX5900XT (_old_ hardware!) with compiz activated and gnome runs as fast as a very fast thing. I am stunned by the number of people who have said they think the windows GUI is faster, I can make a cup of coffee in the time it takes firefox to open in windows.

I suspect that this is either a hardware issue or those who are suffering slow down have done horrible things to their installation.

---

### Post by Tichondrius on 2008-02-07
> **julius malchovitch said:**
> Don't want to start a flame war with this post but I am deeply concerned we have to blame GTK for the Gnome poor responsiveness.

I really don't know GTK internals but I have a little development experience with GTK, QT and MFC and I have to say that both QT and MFC seem to be much better engineered APIs.

This is a real pity 'cause actually Gnome, in my opinion, looks much more 'professional' than KDE, and it's adoption in the enterprise world could suffer a lot from its poor performance.

MS XP and Vista (with full Aero enabled) feel _much_ more responsive on my systems.

Luca

In general I prefer to do web/email in windows, partly due to faster GUI, and partly due to better compatibility and choice of apps. Also content creation is better in Windows, as well as gaming.

That's why I run Ubuntu in a virtual machine on my Vista host, and only use ssh/vnc to communicate with it. In fact I don't use Ubuntu as a workstation or desktop OS, I use it only as a development platform and web/app/mail/file server, and manage it using remote access protocols. So, I'm insulated for Linux GUIs.

---

### Post by andrewjoy on 2008-02-07
2.4 4800+ 2x1Mb L2 @ 210 FSB
1gb DDR400 @ 420
256 7950GT
WD Raptor

Gnome runs just fine for me its slower than xfce but i pref gnome.

My Window Manager of choice is ICEwm but i just cannot get it to work in ubuntu.

---

### Post by ** Andy ** on 2008-02-07
I've had this problem throughout various versions of Ubuntu. I changed my ATI card to a Nvidia one in the hope that it would solve the problem. It hasn't. :( Performance is slightly better, but window drawing is slow and tabs in Opera and Firefox can take seconds to open. I don't know what's causing the problems, but it's annoying as hell. I don't recall having this problem with Kubuntu.

---

