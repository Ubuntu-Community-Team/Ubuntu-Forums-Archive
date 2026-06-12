---
title: "Fedora Core Talk"
date: 2005-05-24
forum: Fedora/RedHat and derivatives
---

### Post by jdong on 2005-05-24
Hey,

Being my distro-junky self, I leeched a FC4 test3 DVD and am currently playing with this OS off in a chroot. Overall, I'm impressed with what I see.

[list]
[*]New theme. Clearlook, I think it's called. Much more soothing to see than Bluecurve   
[*]**GREAT SPEED IMPROVEMENTS** -- With GCC4's help, Fedora Core 4 feels snappier than Ubuntu. Especially when you try to use heavy Python programs (like YUM), you can seriously feel the difference. In fact, you can feel this during Anaconda, where "checking dependencies" takes less than a second on my system where it used to take at least 10.   
[*]Extensive use of LVM. Anaconda's auto partitioner (like in Core 3) insists on setting up LVM's for every partition it makes. In addition, there's a **GUI LVM configuration tool** after setup, for performing those tasks with LVM's. Great work. Never have to regret a partitioning mistake again (huh? /var holds the RPM database too? oops...)   
[*]Openoffice.org 2 beta is very stable quality (build 104 currently) and Redhat stays on top of updates very well.   
[*]**Virtually all packages in repos up-to-date**. Look at Redhat's history, for example, of how quickly they introduced Firefox 1.0.4 as an update for FC 3 and Rawhide. Can't beat that.   
[*]**Up2date works well now**. Before, up2date was ultra-slow, not to mention half of the times it can't resolve its own dependences. This seems to be virtually resolved now. 
[/list] 

In conclusion, Fedora's come a long way since Core 3 to bolster this new release. This is going to be an excellent distro. I've yet to do any Xen testing, but this may be my distro of choice until Breezy :)

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=jdong]
[*]New theme. Clearlook, I think it's called. Much more soothing to see than Bluecurve   [/QUOTE]

Doesn't Gnome have that? I think thats what I use in ubuntu...

But keep it comming. Love learning about other Linuxs without trying them.

NOTE to others:

This will not turn into a Fedora vs. Ubuntu thread. We have too many of those.  Don't even post if you have something negative to say.

---

### Post by tread on 2005-05-24
How dyu run x in a chroot? I tried, but I couldn't .. even when I allowed other hosts to run in my xsession and setting the DISPLAY variable in the chroot.

Am I making sense?

---

### Post by jdong on 2005-05-24
[QUOTE=tread]How dyu run x in a chroot? I tried, but I couldn't .. even when I allowed other hosts to run in my xsession and setting the DISPLAY variable in the chroot.

Am I making sense?[/QUOTE]

Completely unrelated question, but you can find the answer on Debian's AMD64 32-bit chroot page. The short answer is that you have to bind the two /tmp's together (mount --bind /tmp /chroot/tmp), because X's Unix Socket needs to be shared among the two.


I'm getting ready to test Xen now :)

---

### Post by Lovechild on 2005-05-24
Also new with the lastest glibc and GCC4 is FORTIFY_SOURCE which is enabled by default on all Fedora compiled programs, this protects against buffer overflow attacks even spots them at compiletime.

With SELinux policy improvements, Exec-shield and the default firewall, I think we can proclaim Fedora Core 4 one of the safest out of the box desktop Linux distros. 

Aside that FC4 ships GNOME 2.10 and Fedora Extras is deployed by default, which means Fedora finally has a repo like universe. 

Also in the FC4 cycle Evince as been introduced as the default PDF viewer and might I add, it rocks hard - hopefully this will be proposed for GNOME 2.12,

Overall I think FC4 is look really good, and it's running just fine on my desktop.

---

### Post by Optimal Aurora on 2005-05-24
Hay I was and am downloading Fedora core 4 test 3 and I was wondering has anybody here heard of any problems with compatibility or stability? I know its a test version so it most likely is unstable, but I am just curious.

---

### Post by Quest-Master on 2005-05-24
I've never tried Fedora.. sounds like a good time. So, yeah, could anyone comment on how stable it is at the moment? I'm considering giving it a try.

I can't wait till Breezy comes out though. Speed improvements with GCC4 will be awesome.

---

### Post by Lovechild on 2005-05-24
[QUOTE=Optimal Aurora]Hay I was and am downloading Fedora core 4 test 3 and I was wondering has anybody here heard of any problems with compatibility or stability? I know its a test version so it most likely is unstable, but I am just curious.[/QUOTE]

For my money, being the development branch, FC4 is working quite nicely - I haven't really encountered any crippling bugs except the fact that RedHat consistently breaks the danish translation for redhat-menus in every release cycle and they aren't responsive to bugs on it. I mean they did it for FC3 and now for FC4 (my bug has been hovering for like a month now without even a review).

But day to day work seems fine, I've used it ever since test1 and it's been quite nice. In the sense that it might have had days where booting was a problem (mostly SELinux issues) but it never ate my data or my soul. 

And FE is working very nicely, no complains over the quality of RPMs from me, I currently have AbiWord, GNUmeric and Freeciv installed and running without issue - the Extras team did good work, lots of applauds.

---

### Post by jdong on 2005-05-24
Day-to-day FC4 work is pretty much OK. Packages pulled from 3rd party repos, like DAG, will have to be RPMBUILDed from spec/src due to ABI incompatibility.

There are also some YUM/up2date quirks that need to be worked out (currently, OOo isn't compiled against the right libgcj)

---

### Post by KiwiNZ on 2005-05-24
How was the hardware recognition and support ?
I have used all the Fedora releases to date . Core three gave me a lot of issues .I havent tried Core 4 test 3 yet  , trying to be a reformed distro junkie is hard , but I am trying .

---

### Post by jdong on 2005-05-24
[QUOTE=KiwiNZ]How was the hardware recognition and support ?
I have used all the Fedora releases to date . Core three gave me a lot of issues .I havent tried Core 4 test 3 yet , trying to be a reformed distro junkie is hard , but I am trying .[/QUOTE]

Hmm, Fedora's hardware has been relatively flawless since Core 2, and flawless since Core 3 on my desktop (Athlon64, Asus K8v, Nvidia) and laptop (cheap toshiba Celeron 330, Intel onboard kitchen sink).

So, I guess I'm not qualified to answer this question.

---

### Post by TravisNewman on 2005-05-24
I always wait on a stable release for distributions I don't have much experience in, and I haven't REALLY used Fedora (short of testing and almost immediately uninstalling) but this one sound promising-- like maybe they've finally found their direction. I'll be testing this one when it hits final.

---

### Post by blinksilver on 2005-05-24
FC4 has made such great improvements over FC3 it is not even funny, i am really proud of the fedora team, am downloading it right now actually

---

### Post by Lovechild on 2005-05-25
[QUOTE=KiwiNZ]How was the hardware recognition and support ?
I have used all the Fedora releases to date . Core three gave me a lot of issues .I havent tried Core 4 test 3 yet  , trying to be a reformed distro junkie is hard , but I am trying .[/QUOTE]

Every single item worked out of the box for me, except my monitor which I needed to select by hand (Fujitsu x177) but that's the standard with all distros I guess it's an X thing.

Fedora is excellent in that regard.

---

### Post by 23meg on 2005-05-25
does it boot any faster than FC3, which took 3.5 minutes to boot on my 1.8ghz p4m?

---

### Post by Lovechild on 2005-05-25
[QUOTE=23meg]does it boot any faster than FC3, which took 3.5 minutes to boot on my 1.8ghz p4m?[/QUOTE]

yes, several improvements have gone into boottime, e.g. a lot of services don't start if you don't have the hardware needed. and FC5 will be even better, the bootchart guy rewrote readahead to be more efficient and in the FC5 cycle it will be hooked up to auditd to provide the readahead list. It's noticably faster now already though, I think I boot in about 45 secs on my 1600+XP box, not that I've done serious meassurements.

---

### Post by jdong on 2005-05-25
I also confirm a very noticable improvement in bootup time. Services seem to start up faster (GCC4? Code cleanup?), and there are less services loaded on my system.

---

### Post by Lovechild on 2005-05-25
[QUOTE=jdong]I also confirm a very noticable improvement in bootup time. Services seem to start up faster (GCC4? Code cleanup?), and there are less services loaded on my system.[/QUOTE]

Mostly you can "blame" that on Ziga who wrote bootchart, it really helped the developers examine the boot process and find bugs. Ziga is basically our new god and overlord, all must hail him.

And might I pled you people to not attribute all speed ups to gcc4, it's really not true, it's a better compiler but the biggest gain with gcc4 is java, gcj really works now - so much so that FC4 ships with a natively compiled OpenOffice and Eclipse. This cannot be understated in terms of importance, both breezy and FC5 should ship gcjwebplugin which allows us to have completely free web java applets.. just try imagining that. And tests on planet classpath show that gcj is extremely fast, more so than the sun java JDK - infact everyone's darling wikipedia now runs using gcj.

---

### Post by brickbat on 2005-05-27
I downloaded it and installed it on my hp laptop.  It recognised all the hardware pretty well.  I gave up after 6 hours of trying to install the multimedia capability.  I think this is because it is a test and changing all the time.  Two diferent instruction sites are out of date even though one of them is less 2 weeks old.

I am not a compiler type.  I can't program so it is on my laptop but pretty useless.  I will have to wait until the final fc4 comes out.  Then there should be stable instructions. I am going to check out centos while I wait.

ciao
bb

---

### Post by jdong on 2005-05-27
[QUOTE=Lovechild]And might I pled you people to not attribute all speed ups to gcc4, [/QUOTE]

In FC3, committing 10 1KB binaries to a locally hosted mod_dav_svn Subversion repository took about 20 seconds.

In FC4, the same operation takes about 5 seconds.


What's to attribute this massive speedup to?

---

### Post by tzutolin on 2005-06-02
I've never tried fedora too. 

Is it possible to upgrade to a new version (e.g. from fedora 3 to 4) without reinstalling the whole system?   :smile:

---

### Post by bored2k on 2005-06-02
So far Jdong has given nothing but positive points for FC4.
He is tempting me so hard. If only I wasn't so scared of leaving a .DEBian environment.. Give us more :D!

---

### Post by TravisNewman on 2005-06-03
Debain is quite comfortable compared to RPM, but it's not that bad, just be careful when upgrading things.

---

### Post by bored2k on 2005-06-03
[QUOTE=panickedthumb]Debain is quite comfortable compared to RPM, but it's not that bad, just be careful when upgrading things.[/QUOTE]
 Before Ubuntu , I did try Mandr*iva*:? and AuroX (I also tried RHat on my Linux courses... but we couldn't stand that so ended up using SuSE, AuroX and Ubuntu 4.10RC :-P). I have to say my .rpm experience was not good at all. I want to try FC4 badly because It's supposedly that good (Jdong mentioned speed.. that gets me going), but I hope RPM management is better than what i've seen.

---

### Post by blinksilver on 2005-06-03
yum and yum ex are amazing, plus there is the apt/synaptics system for rpms....

oh and the reason FC4 is fast is not because of GCC4, which actually produces bigger more buggy code (it is a brand new platform and in a short time will be amazing) it is becasue the fedora team made speed a big priorty in FC4 and worked very hard to get it as fast as it is

---

### Post by bored2k on 2005-06-03
[QUOTE=blinksilver]yum and yum ex are amazing, plus there is the apt/synaptics system for rpms....

oh and the reason FC4 is fast is not because of GCC4, which actually produces bigger more buggy code (it is a brand new platform and in a short time will be amazing) it is becasue the fedora team made speed a big priorty in FC4 and worked very hard to get it as fast as it is[/QUOTE]
 So let me get this straight: FC4 is faster than Hoary ? Noticeably faster or just "faster supposedly :?" ?

*gets wget ready for a long journey..*

---

### Post by blinksilver on 2005-06-03
i have no idea if it is faster then hoary, but it is fast compared to FC3

---

### Post by bored2k on 2005-06-03
[QUOTE=blinksilver]i have no idea if it is faster then hoary, but it is fast compared to FC3[/QUOTE]
 I have never tried out Fedora so I wouldn't notice that :-/ . Tomorrow I'll try and get a couple of FC4 reviews/articles so hopefully next week I'll be testing out FC4 :D (Yay ! I had not resumed my distro testing since Xandros3/Ubuntu :D)

---

### Post by tzutolin on 2005-06-03
There is a [thread](http://forums.fedoraforum.org/forum/showthread.php?t=55419&highlight=synaptic) talking about ubuntu and fedora too. Please check it out :)

---

### Post by bored2k on 2005-06-03
[QUOTE=tzutolin]There is a [thread](http://forums.fedoraforum.org/forum/showthread.php?t=55419&highlight=synaptic) talking about ubuntu and fedora too. Please check it out :)[/QUOTE]
 Thanks for the link. I'll read it tomorrow when I'm awake :roll: .

---

### Post by allforcarrie on 2005-06-03
I was not impressed with Fedora, it didnt detect my hardware.

---

### Post by GilGalad on 2005-06-03
[QUOTE=bored2k]So let me get this straight: FC4 is faster than Hoary ? Noticeably faster or just "faster supposedly :?" ?[/QUOTE]

I tried FC4 Test 3 last week on my laptop. I did not really feel it was faster than Hoary, in fact the boot process in FC is still slower (maybe because it starts more services). I am sure the final release will be better on that aspect.

Moreover, my conexant modem did not work (even after applying patches from linuxant - ok. it is a test release); I had to install the NVIDIA drivers by hand (don't tell me about livna repos). When adding repositories to yum I found that they have still not solved this problem:

[http://dag.wieers.com/home-made/apt/FAQ.php#D](http://dag.wieers.com/home-made/apt/FAQ.php#D)

Then I remembered why I switched from FC3 to Hoary in the first place. :smile: 
(but don't misunderstand me, I encourage people to try it and decide by themselves! - FC has some nice features as well)

---

### Post by asimon on 2005-06-03
I tried Rawhide (upgraded from FC4T3) two weeks ago and instantly hit several selinux issues (problems with httpd, ntpd, automatic adsl connection during boot [funny, that doesn't work currently under Breezy too, but there it's no related to selinux], dovecot). Three days after I filed the bug reports all but one were fixed.

Although there are still open bugs wrt their selinux rules I hope that next year selinux is standard on every Linux distro. I like it very much and think we should get every additional security we can get.

Regarding performance: I didn't percived any difference between my Ubuntu, Gentoo, or Fedora desktops.

---

### Post by TravisNewman on 2005-06-03
[QUOTE=blinksilver]yum and yum ex are amazing[/QUOTE]

Well that depends on who you ask ;) I've never tried yum ex, but I've never been anything but incredibly ticked off at yum at any moment that I have to use it. apt for RPM still doesn't compare to apt for debian.

But that's not to say that I'm not going to try it ;)

---

### Post by bored2k on 2005-06-03
[QUOTE=panickedthumb]Well that depends on who you ask ;) I've never tried yum ex, but I've never been anything but incredibly ticked off at yum at any moment that I have to use it. apt for RPM still doesn't compare to apt for debian.

But that's not to say that I'm not going to try it ;)[/QUOTE]
 When will get FC4 have a stable -final- release ?

---

### Post by blinksilver on 2005-06-03
in 5 days

---

### Post by bored2k on 2005-06-03
[QUOTE=blinksilver]in 5 days[/QUOTE]
 Great :D ! I'll wait for it then ! Enough time for me to document myself on Fedora :)

---

### Post by Gtaylor on 2005-06-05
[QUOTE=panickedthumb]Well that depends on who you ask ;) I've never tried yum ex, but I've never been anything but incredibly ticked off at yum at any moment that I have to use it. apt for RPM still doesn't compare to apt for debian.

But that's not to say that I'm not going to try it ;)[/QUOTE]
I agree here, especially the older versions that take 10-15 seconds for almost every operation even with their cache flag. There's no reason to have to go through all of your package data for every single yum command, it just takes so long, whereas apt zips right through a whole lot of changing around. I also found Debian/Ubuntu's selection of packages to be awesome in comparison to other distros out there.

---

### Post by andrewpmk on 2005-06-05
The downside of all these updates was stability. When I ran Fedora Core Test 2, it sort of worked for a while, then it stopped working. At that point, I opened up Windows (which I hardly ever use) and burnt myself a Ubuntu CD.

The good:
- Rapid updates
- GCC4
- Graphical GRUB and boot screen by default
- Very good graphical installer
- More extensive user interface

The bad:
- Poor graphical package manager
- Ugly (IMHO) graphics - although I hardly ever keep the defaults for long, including under Ubuntu

The ugly:
- Stability (will hopefully be fixed by the time FC4 Final comes around)

---

### Post by Curlydave on 2005-06-05
I tried FC3 a few weeks ago as my first linux installation. Install went great, but it would just boot up to a grey screen with a mouse cursor, and there was nothing I could do to fix it. Noone could even begin to help me or tell me why it was doing it. I then went to Ubuntu. Grub wouldn't work with it either, and yes, I set it up properly to the mbr of my Linux HD. That was resolved as well by installing Ubuntu. (I reinstalled FC3 twice before giving up.)

---

### Post by alainhenry on 2005-06-06
I had a similar problem.  I have a  working system with WinXP and Ubuntu Hoary, using GRUB for dual boot.  I recently tried to install FC3: install went fine, but the first reboot stopped immediately at a black screen with "GRUB" on the screen, then froze.  I tried booting from a grub boot floppy, and it did not recognise the partition hda10 I used to install FC3 (the command root (hd0,9) froze the machine.  
By the way, I had the same problem when trying to install Mandriva LE2005 and KUbuntu.  
Any idea ? Any information useful to help solve this ?
Thanks
Alain

---

### Post by bored2k on 2005-06-07
Fedora core delayed until june 13th.. :@

---

### Post by YourSurrogateGod on 2006-02-24
[http://fedoraproject.org/wiki/RenderingProject/aiglx](http://fedoraproject.org/wiki/RenderingProject/aiglx)

Looks like pretty cool stuff. I haven't read all of it, but it should be interesting.

---

### Post by briancurtin on 2006-02-24
yeah it looks cool. theres a thread around from yesterday where we talked about it.

---

### Post by Iandefor on 2006-02-24
Already a thread on it.

[http://www.ubuntuforums.org/showthread.php?t=133555](http://www.ubuntuforums.org/showthread.php?t=133555)

---

### Post by YourSurrogateGod on 2006-02-24
[QUOTE=Iandefor]Already a thread on it.

[http://www.ubuntuforums.org/showthread.php?t=133555](http://www.ubuntuforums.org/showthread.php?t=133555)[/QUOTE]
Didn't see it.

---

### Post by Technoviking on 2006-03-20
Fedora Core 5 has been released ([http://linux.slashdot.org/article.pl?sid=06/03/20/163216)](http://linux.slashdot.org/article.pl?sid=06/03/20/163216)). Congrats to the Fedora team.

---

### Post by taurus on 2006-03-20
And you can see people are running to download it like gangbusters...  The net will be slowing to a crawl now!  :)

[http://distrowatch.com/?newsid=03306#0](http://distrowatch.com/?newsid=03306#0)

---

### Post by WildTangent on 2006-03-20
Link is broken.

-Wild

---

### Post by Zotova on 2006-03-20
I was thinking of trying out Fedora, until I saw the 5 cd thing. Why is there the need for so many cd's! At least the option for a one cd install would be nice where you can install anything extra you need afterwards (e.g. ubuntu).

---

### Post by ComplexNumber on 2006-03-20
[quote=Zotova]I was thinking of trying out Fedora, until I saw the 5 cd thing. Why is there the need for so many cd's! At least the option for a one cd install would be nice where you can install anything extra you need afterwards (e.g. ubuntu).[/quote]
for people who don't have an internet connection.

---

### Post by taurus on 2006-03-20
[QUOTE=Zotova]I was thinking of trying out Fedora, until I saw the 5 cd thing. Why is there the need for so many cd's! At least the option for a one cd install would be nice where you can install anything extra you need afterwards (e.g. ubuntu).[/QUOTE]
You can go for the DVD version and if you don't have a network connection, then you are toasted if you need something extra.  With the DVD (or 5 CDs), it comes with everything including a kitchen sink!!!  ;)

---

### Post by engla on 2006-03-20
[QUOTE=ComplexNumber]for people who don't have an internet connection.[/QUOTE]
The best of the both worlds would be if Fedora installed fine from just one CD, with a basic but adequate setup (like ubuntu), and had this printed clearly in the install/download instructions.

---

### Post by Qrk on 2006-03-20
[QUOTE=Zotova]I was thinking of trying out Fedora, until I saw the 5 cd thing. Why is there the need for so many cd's! At least the option for a one cd install would be nice where you can install anything extra you need afterwards (e.g. ubuntu).[/QUOTE]

Usually you can get by with only the first two CDs and still have a wide variety of packages to choose from.

---

### Post by ComplexNumber on 2006-03-20
[quote=engla]The best of the both worlds would be if Fedora installed fine from just one CD, with a basic but adequate setup (like ubuntu), and had this printed clearly in the install/download instructions.[/quote]
thats what they are doing. if you have a look at their wiki, they are trying to get all the core stuff on 1 CD and all the extras on the remaining 4.

---

### Post by arctic on 2006-03-20
IMHO, why should fedora ship an extra one-cd only thing? In this case, do an ftp-installation. Its faster and easier, plus you get all updates, too. (Okay, they work on a one-cd version, but it ain't necessary imho)

PS: I just downloaded all isos and will commence the installation shortly after I have backed up my system. I must admit, I prefer fedora over ubuntu... don't ask me why.

Now don't shoot me. :P

---

### Post by FLeiXiuS on 2006-03-20
There's also [www.madtux.org](www.madtux.org).  It's about a 2$ fee for a **quick** download mirror.

---

### Post by arctic on 2006-03-20
No need for that. There are so many fedora mirrors that you WILL find a fast, responsive mirror. It has always been that way.

---

### Post by ComplexNumber on 2006-03-20
[quote=arctic]I must admit, I prefer fedora over ubuntu... don't ask me why.

Now don't shoot me. :P[/quote] i do too because the more wide-ranging available applications suits me better. perhaps ubuntu can release a 5/6 cd (or 1 dvd) set.

---

### Post by Brunellus on 2006-03-20
[QUOTE=ComplexNumber]i do too because the more wide-ranging available applications suits me better. perhaps ubuntu can release a 5/6 cd (or 1 dvd) set.[/QUOTE]
can someone clue me in to the difference between a 5 CD set, and an online repository? 

Or:  what apps are fedora-only?

---

### Post by ComplexNumber on 2006-03-20
[quote=Brunellus]can someone clue me in to the difference between a 5 CD set, and an online repository? 

Or:  what apps are fedora-only?[/quote] sorry. what i meant was, i get my linux distros when they are made available on the cover of linux magazines such as linux format and linux developer. some distros such as suse, mandriva,  and fedora are released to include the extras too (so they either come on 4-6 cd's or 1 dvd), whereas distros such as ubuntu are contained on only 1 cd.

---

### Post by psychicdragon on 2006-03-20
Ubuntu also has a DVD ISO available for download. I think it has the entire main repository on it, but I could be wrong.

---

### Post by int on 2006-03-20
**it seems that Fedora Core 5 have some problems. They allready make a patc**h

---

### Post by MetalMusicAddict on 2006-03-20
Anyone seen a torrent for the DVD?

Nevermind. Found [IT]("http://torrent.fedoraproject.org/").

---

### Post by Simian on 2006-03-20
Their Blue Curve theme and yum really bums me out...

---

### Post by psychicdragon on 2006-03-20
[QUOTE=Simian]Their Blue Curve theme and yum really bums me out...[/QUOTE]What's wrong with Bluecurve? I like it a lot better than the current Human theme, the new Human theme I'm not too sure about either.

I haven't used yum since I tried out Fedora Core 2. I did have some problems though and ended up installing apt4rpm. I would imagine things have gotten better in rpm-land since then though.

---

### Post by towsonu2003 on 2006-03-20
those who wanna try FC5 will experience problems with propritary drivers (nvidia and fglrx). Check out [slashdot]("http://linux.slashdot.org/article.pl?sid=06/03/20/163216"), where a couple of informative comments describe how to solve this. You will basically have to get a new kernel. Also, their first update got released minutes before they released FC5. The update is about xorg, and I believe we did not get that update yet on Ubuntu. The developer seemed very unhappy about the [security vulnerability xorg had]("https://www.redhat.com/archives/fedora-announce-list/2006-March/msg00026.html")... And one last thing, you can find out how to install the dreaded codecs and stuff [here]("http://www.fedorafaq.org/"). 

Happy trying :) After all that negative comments for FC on slashdot, and the limited number of blank disks I have, I decided to wait for Suse (5CDs I believe) and Ubuntu (1CD). I'm too cheap... Let me search my magic bag for some spare CDs...

---

### Post by taurus on 2006-03-20
[QUOTE=towsonu2003]those who wanna try FC5 will experience problems with propritary drivers (nvidia and fglrx). Check out [slashdot]("http://linux.slashdot.org/article.pl?sid=06/03/20/163216"), where a couple of informative comments describe how to solve this. You will basically have to get a new kernel. Also, their first update got released minutes before they released FC5. The update is about xorg, and I believe we did not get that update yet on Ubuntu. The developer seemed very unhappy about the [security vulnerability xorg had]("https://www.redhat.com/archives/fedora-announce-list/2006-March/msg00026.html")... And one last thing, you can find out how to install the dreaded codecs and stuff [here]("http://www.fedorafaq.org/"). 

Happy trying :) After all that negative comments for FC on slashdot, and the limited number of blank disks I have, I decided to wait for Suse (5CDs I believe) and Ubuntu (1CD). I'm too cheap... Let me search my magic bag for some spare CDs...[/QUOTE]
Or do what I do, use CD-RW!!!  ;)

---

### Post by towsonu2003 on 2006-03-20
[QUOTE=taurus]Or do what I do, use CD-RW!!!  ;)[/QUOTE]
That's more expensive :PpPp Well, seriously, I 'discovered' that cd-rw's are erasable (I accidentally erased a CD, so I learned that can happen :pP) a couple of weeks ago. 
PS. I couldn't find any spare CDs in my spare bag...

---

### Post by psoleko on 2006-03-20
[QUOTE=towsonu2003] After all that negative comments for FC on slashdot, and the limited number of blank disks I have, I decided to wait for Suse (5CDs I believe) and Ubuntu (1CD). I'm too cheap... Let me search my magic bag for some spare CDs...[/QUOTE]

Negative comments on Slashdot...who would have expected that :rolleyes:

I am installing FC5 on my laptop right now..heard that network manager .6 is in out of the box. Let's see how wireless is working.

---

### Post by towsonu2003 on 2006-03-21
[QUOTE=psoleko]Negative comments on Slashdot...who would have expected that :rolleyes:[/QUOTE]
Especially the ones on the kernel (not accepting proprietary drivers) got me to think that some testing was lacking in that release. I'm not sure if I'm ready for that much bleeding edgeness :)

---

### Post by GarySaved on 2006-03-21
I have been waiting for FC5 for quite some time.
From the way they were talking, it was going to be awsome.
I installed it, and am very disappointed.
It does not come with flash, or Java.
I searched their repositories, and they do not offer either.  You have to go to their sites, and download/install them manually.

Also their multimedia support is not very good.

They still have not gotten close to offering what Ubuntu does.

Gary

---

### Post by Lovechild on 2006-03-21
OMFG!!! it rocks so hard!!!

I'm stunned, I literally cannot describe the polish and hotness that has gone into this release - please download it and try it yourselves.

---

### Post by ComplexNumber on 2006-03-21
[quote=GarySaved]I have been waiting for FC5 for quite some time.
From the way they were talking, it was going to be awsome.
I installed it, and am very disappointed.
It does not come with flash, or Java.
I searched their repositories, and they do not offer either.  You have to go to their sites, and download/install them manually.

Also their multimedia support is not very good.

They still have not gotten close to offering what Ubuntu does.

Gary[/quote]
where are you getting your information from? :confused:
it does have java and flash - the java thats offered in fedora is the gcj and is out of the box. the flash is available as a separate download

---

### Post by taurus on 2006-03-21
[QUOTE=GarySaved]I have been waiting for FC5 for quite some time.
From the way they were talking, it was going to be awsome.
I installed it, and am very disappointed.
It does not come with flash, or Java.
I searched their repositories, and they do not offer either.  You have to go to their sites, and download/install them manually.

Also their multimedia support is not very good.

They still have not gotten close to offering what Ubuntu does.

Gary[/QUOTE]
I assume you meant Sun's java!  Well, does Ubuntu offers Sun's java and flash out of a box?  Don't think so, either.  However, all you need is add a repo to your /etc/yum.d/ and "yum" whatever else you want away...  :rolleyes:

---

### Post by towsonu2003 on 2006-03-21
see [http://www.fedorafaq.org/](http://www.fedorafaq.org/) for that stuff (java, codecs et al)

---

### Post by luna6 on 2006-03-21
I wrote a review for FC 5 which can be read here [http://lunapark6.com/?p=481](http://lunapark6.com/?p=481)  ...once you get it up and running it is sweet. Looking forwards to Dapper.

---

### Post by ComplexNumber on 2006-03-21
[quote=luna6]I wrote a review for FC 5 which can be read here [http://lunapark6.com/?p=481]("http://lunapark6.com/?p=481")  ...once you get it up and running it is sweet. Looking forwards to Dapper.[/quote] nice review. a bit diappointed to read this, though:
> ....while the other one, with an Nvidia video card and Nvidia motherboard chipset, was thoroughly a pain to get working.  
apparently, one should always use the rpm's for updating the video drivers on fedora because using the source drivers from nvidia can make everything  go belly-up

---

### Post by RaptorRaider on 2006-03-21
Can someone tell me how well aiglx is "integrated" in Fedora Core 5?

Similar to Kororaa, which would mean that it is automatically used (unless there is no hardware support)?

---

### Post by arctic on 2006-03-22
Well, I have Fedora 5 now running since some days and it really is a stunning release. The multimedia-crap that somebody complained about (please do the maths, before dissing fedora) was solved in some minutes, same as flash.
Beagle works extremely well, the whole distro is fast, flashy... oh my god... very hard to beat for any distro. I think Ubuntus dapper will come very, very close but it will not beat fedora.

---

### Post by Absolute on 2006-03-22
[QUOTE=ComplexNumber]apparently, one should always use the rpm's for updating the video drivers on fedora because using the source drivers from nvidia can make everything  go belly-up[/QUOTE]

There's also an issue with the graphical installation, for those using XFX nVidia drivers; I still haven't been able to get it to work yet.  

[http://forums.fedoraforum.org/forum/showthread.php?t=99245&page=2&pp=15]("http://forums.fedoraforum.org/forum/showthread.php?t=99245&page=2&pp=15")

---

### Post by towsonu2003 on 2006-03-22
[QUOTE=arctic]Well, I have Fedora 5 now running since some days and it really is a stunning release. The multimedia-crap that somebody complained about (please do the maths, before dissing fedora) was solved in some minutes, same as flash.
Beagle works extremely well, the whole distro is fast, flashy... oh my god... very hard to beat for any distro. I think Ubuntus dapper will come very, very close but it will not beat fedora.[/QUOTE]
Did you try to install any proprietary drivers (read: ATI/NVidia)? Default kernel doesn't accept them. How was your experience, if you installed these drivers? Long / short process? Hard / easy?

This is curiosity... I don't think such a bleeding edge product is appropriate for me for now [no offense]...

---

### Post by towsonu2003 on 2006-03-22
> **Absolute]There's also an issue with the graphical installation, for those using XFX nVidia drivers said:**
> http://forums.fedoraforum.org/forum/showthread.php?t=99245&page=2&pp=15[/URL]
I scanned your forum message in there. Although not good enough in the short run, you might want to submit a bug report to Fedora for that. Don't forget to set the priority to highest bc the bug doesn't let you install Fedora in the first place. The developers may be interested in this as it blocks the installation for anyone using XFX (seems like it in your post at least)... 

Do you think it is possible to install fedora using chroot from inside Ubuntu to other partition? Don't know anything about that, but some part of Gentoo uses chroot for installation :-k

---

### Post by arctic on 2006-03-22
[QUOTE=towsonu2003]Did you try to install any proprietary drivers (read: ATI/NVidia)? Default kernel doesn't accept them. How was your experience, if you installed these drivers? Long / short process? Hard / easy?

This is curiosity... I don't think such a bleeding edge product is appropriate for me for now [no offense]...[/QUOTE]Cannot tell anything on those, as I have SIS graphics, which works perfectly. The forums already have howtos for installing the nvidia stuff and apparently, this works, although you will need to get your hands dirty. I guess the best solution is to wait till end of week. The developers have a new, patched kernel already up and running and do some last tests to it. Thus, a text-based install is a good solution, followed by a yum update from cli. Then, getting the beast to run should be a no brainer. ;)

---

### Post by towsonu2003 on 2006-03-22
[QUOTE=arctic]Thus, a text-based install is a good solution, followed by a yum update from cli. Then, getting the beast to run should be a no brainer. ;)[/QUOTE]
nice info, thanks :)

---

### Post by John.Michael.Kane on 2006-03-23
Testing it Now. seems fast, and text seems to render sharper,programs load quick.Seems to be a pretty good product, However I will stick with ubuntu. not into the whole rpm thing.

---

### Post by towsonu2003 on 2006-03-23
[QUOTE=SD-Plissken]Testing it Now. seems fast, and text seems to render sharper,programs load quick.Seems to be a pretty good product, However I will stick with ubuntu. not into the whole rpm thing.[/QUOTE]
it's weird that every ubuntu user trying fedora is saying "wow this is fast"... any dapper testers see the same difference??

edit: [no offense]

---

### Post by John.Michael.Kane on 2006-03-23
towsonu2003 Dapper not final yet so i can't pass judgement on how it renders text or loads programs just yet. Dapper testing for me is just helping to find any bugs that may not have been found yet. Fedora 5 is their Distribution Release. When Dapper goes gold I'm sure there will be diffrence in many ways, however Fedora has it's users who love it, and Ubuntu has it's users who love it. 

Just my thoughts..

---

### Post by arctic on 2006-03-23
Both distros will be fine releases (okay, fedora already is a fine release, as it hit the mirrors some days ago). If fedora outshines dapper, then this is not a big problem as dapper-developers can take a look at what fedora-developers did in order to make fc5 shine and implement this in e.g. ubuntu 6.10. Same thing will happen if dapper seriously outshines fedora (unlikely imho, but i am biased anyway. lol). After all, every distro tries to learn from the others, right? Fedora and ubuntu are not different in this respect, as both want to make Linux computing easier for everyone. ;)

---

### Post by Simian on 2006-03-23
i always found wifi extremely painfull in fedore. Can anyone tell me if wifi works out of the box now like Ubuntu?

---

### Post by muscaa on 2006-03-23
i tried to install FC5 but my machine got 128Mb RAM and graphical installation is not supported. Very disappointed. :(

---

### Post by towsonu2003 on 2006-03-23
[QUOTE=muscaa]i tried to install FC5 but my machine got 128Mb RAM and graphical installation is not supported. Very disappointed. :([/QUOTE]
did you try the text installer? it's very easy as far as remember. boot from cd and type linux text <enter>

I'm not sure your RAM meets minimum F requirements though... did you check that?

---

### Post by arctic on 2006-03-23
Minimum Memory: 64 MB for text installer, 128 MB for graphical installation.
Minimum Memory for Desktop (Gnome): 192 MB, 256 recommended.

No idea about wifi. Better check their forums. :)

---

### Post by John.Michael.Kane on 2006-03-23
```
#Minimum RAM for text-mode: 128MiB
#Minimum RAM for graphical: 192MiB
#Recommended for graphical: 256MiB 
```
[http://fedora.redhat.com/docs/release-notes/fc5/#id3099264](http://fedora.redhat.com/docs/release-notes/fc5/#id3099264)

---

### Post by towsonu2003 on 2006-03-23
[QUOTE=arctic]
Minimum Memory for Desktop (Gnome): 192 MB, 256 recommended.
[/QUOTE]
hmmm, than muscaa will have to install Fedora with xfce or any other available thingy (that is not gnome and not kde). I'm fairly sure the option is given during text installer.

---

### Post by ssam on 2006-03-23
[QUOTE=Simian]i always found wifi extremely painfull in fedore. Can anyone tell me if wifi works out of the box now like Ubuntu?[/QUOTE]

a lot of the network manager work is being done in fedora so expect wifi to be quite good as long as you have a card with a native driver. not sure about ndiswrapper, maybe they have that good as well, personally i have never used it.

---

### Post by htinn on 2006-03-23
I personally have a DWL-G122, and Fedora Core is nowhere near supporting it out of the box. It doesn't support rt2x00 period. I still had to compile the cvs source by hand to get it working (and yum initially installed the "zen" headers, forcing me to rpm -ivh the headers off the disc manually).

If you like GNOME, I think you'll like Fedora Core 5, because FC5 comes with the latest. If you like KDE, you'd probably be better off waiting for Dapper Kubuntu.

For package handling, I got it working with Smart Package Manager (a bit more of a pain to set up properly, but much much faster than yum).

---

### Post by muscaa on 2006-03-24
[QUOTE=towsonu2003]hmmm, than muscaa will have to install Fedora with xfce or any other available thingy (that is not gnome and not kde). I'm fairly sure the option is given during text installer.[/QUOTE]
hi towsonu2003,

what is xfce? I think i'll have to buy a new pc or notebook by the end of this year. My PC is 5 yr old with just 128Mb RAM, can only install FC4. ](*,)

---

### Post by LinuxKid on 2006-03-24
if the net download falls to a slow, then the bit torrent download must be speeding fast (averaged 50 kbps by kororaa, while the net download was 15 kbps)

btw, I believe debian takes 14/15 cd's :)

---

### Post by towsonu2003 on 2006-03-24
[QUOTE=muscaa]hi towsonu2003,

what is xfce? I think i'll have to buy a new pc or notebook by the end of this year. My PC is 5 yr old with just 128Mb RAM, can only install FC4. ](*,)[/QUOTE]
From wikipedia:
> Xfce is a desktop environment for Unix and other Unix-like platforms, such as Linux and FreeBSD. Its configuration is entirely mouse-driven, the configuration files are hidden from the casual user. "Designed for productivity, it loads and executes applications fast, while conserving system resources." (Olivier Fourdan, creator)
basically, it's a desktop environment for older computers (and hence, "conserving system resources"). you can try it with ubuntu by apt-getting xubuntu-desktop, logging off of gnome and logging in after choosing xfce from "session" in log out menu.

---

### Post by K.Mandla on 2006-04-10
I'm plunking around with FC5 and while it's definitely not Ubuntu, it's not too shabby. I'd like it more if I could get my ancient Linksys wireless card running, and if mp3's weren't a trick to get going, but hey, it's a start. 

And it's blue!

---

### Post by snufkin on 2006-04-10
[QUOTE=K.Mandla]And it's blue![/QUOTE]

But we shouldn't necessarily hold that against it ;)

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=snufkin]But we shouldn't necessarily hold that against it ;)[/QUOTE]
I tried Fedora Core about a month ago but it didn't like my laptop. Fedora 5 doesn't like AMD processors, and is optimized for Intel P4. I also didn't like that I couldn't install the ATi Linux Drivers because I would replace this "important" lib. Everything is also harder to get going in Fedora. Especially if you don't have expericence with RPMS or you are a Linux noob <=== like me :)

---

### Post by taurus on 2006-04-10
What is the model of your Linksys wireless card because I have it, WPC54G, working fine on my laptop running FC5, dualboot with Dapper Flight 6.  And if you need to add extra repo to your /etc/yum.repos.d/ so you can install driver for your nVidia or ATI, mp3, or multimedia, then check out livna's at [http://rpm.livna.org/](http://rpm.livna.org/).

---

### Post by blackant on 2006-04-10
I tried Fedora core 5, but I guess I am too used to Ubuntu...I don't know how to install other stuff and do the updates. :D

---

### Post by taurus on 2006-04-10
[QUOTE=blackant]I tried Fedora core 5, but I guess I am too used to Ubuntu...I don't know how to install other stuff and do the updates. :D[/QUOTE]
With Ubuntu, you use apt-get to install or update your system.  But for Fedora Core, you use yum (text base) or yumex (GUI).  However, you can also use apt-get in FC too if you choose.  
```

yum update <-- to update your system
yum install package_name <-- to install a program

```

---

### Post by AndyCooll on 2006-04-10
Yeah I've looked at FC5 too. The first distro I ever tried was FC4 so I thought I'd do a revisit. 

I quite liked it until I hit a bit of a brick wall trying to get Freenx to work. With Ubuntu it just worked, with FC5 I think I'm going to have to manually set up the keys. In truth I didn't spend too much time trying to work it out.

Everything else about it seems to look good.

---

### Post by Lovechild on 2006-04-10
In my humble opinion Fedora Core 5 is currently the finest distro out there, the security is top notch and the polish that has gone into it is equally awesome.

---

### Post by K.Mandla on 2006-04-10
Yes, it's definitely polished, and it's blue, and I dig the general icon/font appearance, but I don't think I'll keep it long.

It's hard (for me) to ignore the fact that Ubuntu recognizes both my wireless cards (a WPC11 and a Intel Pro 2200BG) before the installation procedure is even started. For some reason I can't tweak the FC5 networking panel to mesh with my router with the Linksys card, and the Intel isn't even recognized as a networking device. I realize I should be more patient with it, but those are kind of dealbreakers for me, particularly since I'm just installing it for kicks. If either one had worked without requiring too much research, it might be sticking around longer.

I certainly can't find any faults with it, and to be honest, the real attraction is the graphical installer (Anaconda?). If Ubuntu could come up with something similar, it would be a real bonus. There's something nice (reassuring?) about an installer that comes up with a mouse pointer and dialog boxes. Ubuntu's certainly works, but could use improvement in that category, after seeing FC5 install.

Maybe I'll look at it again, sometime in the future. It is, after all, blue. ... :mrgreen:

Now please excuse me for about a half an hour, while I wipe out my hard drive. Hmm. ... where did I leave my Flight 6 disc ... ? :-k  ;)

---

### Post by greenpenguin on 2006-04-10
I quite liked FC4.. I may try it :).  The only downside to Fedora i found was that it didn't detect my wireless card (takes rt2500 drivers). The screenshots do look nice :).

Ouch - I just saw the size of the download :(

---

### Post by rabidphage on 2006-04-10
I've wasted a good DVD burning FC5. Installation and polish were all fine. How ever boot sequence froze. I guess FC5 hardware support isn't half as good as ubuntu.
IMHO ubuntu is the best distro for zombies (like me) from the windows world.

---

### Post by K.Mandla on 2006-04-10
[QUOTE=greenpenguin]Ouch - I just saw the size of the download :([/QUOTE]
Yeah, it's definitely no lightweight. I almost gave up on it halfway through the download process, just because I wasn't interested in tying up my bandwidth when I wasn't sure I was going to like it.

[quote=rabidphage]IMHO ubuntu is the best distro for zombies (like me) from the windows world.[/quote]
I think you're right, or at least I would agree with you for myself. I know I should probably give FC5 a fair shake, but I'm just not up for another Holy Grail wireless quest these days. I would've liked to see it click into place ... even if it added another 1.44Mb to the 3.1Gb download. :???:

---

### Post by Bandit on 2006-04-10
Fedora C5 isnt bad at all. Its nice to see that they finally put together something worth recommending.
I have the 32bit verision installed on the wifes computer and my computer.
Its very very fast, faster then the 64bit version of dapper at the momment.
I have everything running perfectly.
I got MP3/DVD stuff all up and running within a few minutes, my ATI radeon 9200 works perfectly out of the box.
Everything runs great just like it should.
Cant wait for Dapper to be released so I can dual boot both of them.

Cheers,
Bandit

---

### Post by mstlyevil on 2006-04-10
[QUOTE=Bandit]Fedora C5 isnt bad at all. Its nice to see that they finally put together something worth recommending.
I have the 32bit verision installed on the wifes computer and my computer.
Its very very fast, faster then the 64bit version of dapper at the momment.
I have everything running perfectly.
I got MP3/DVD stuff all up and running within a few minutes, my ATI radeon 9200 works perfectly out of the box.
Everything runs great just like it should.
Cant wait for Dapper to be released so I can dual boot both of them.

Cheers,
Bandit[/QUOTE]

Dual boot them now. Dapper is very stable and works great.

---

### Post by LightsOut on 2006-04-11
[QUOTE=K.Mandla]Yes, it's definitely polished, and it's blue, and I dig the general icon/font appearance, but I don't think I'll keep it long.

It's hard (for me) to ignore the fact that Ubuntu recognizes both my wireless cards (a WPC11 and a Intel Pro 2200BG) before the installation procedure is even started. For some reason I can't tweak the FC5 networking panel to mesh with my router with the Linksys card, and the Intel isn't even recognized as a networking device. I realize I should be more patient with it, but those are kind of dealbreakers for me, particularly since I'm just installing it for kicks. If either one had worked without requiring too much research, it might be sticking around longer.

I certainly can't find any faults with it, and to be honest, the real attraction is the graphical installer (Anaconda?). If Ubuntu could come up with something similar, it would be a real bonus. There's something nice (reassuring?) about an installer that comes up with a mouse pointer and dialog boxes. Ubuntu's certainly works, but could use improvement in that category, after seeing FC5 install.

Maybe I'll look at it again, sometime in the future. It is, after all, blue. ... :mrgreen:

Now please excuse me for about a half an hour, while I wipe out my hard drive. Hmm. ... where did I leave my Flight 6 disc ... ? :-k  ;)[/QUOTE]

My ipw2200 card worked right out the box for me. Something that DIDN'T work out the box with ubuntu thus the reason I switched. My nvidia card took a whole 2 minutes to get setup also. MP3 took 1 minute, and dvd playback, avi., mpg., .wmv and any other media format took a minute to install as well. The initial installation was also VERY simple. I was up and running in no time. I still havent got a handle on YUM all the way though as I'm still a bit confused about the repo dependency thing that can cause problems, but overall i'm definently happy. I do find the ubuntu forums more active though, but it's ok since it's all linux. I get the best of both worlds. I love my FC5!

---

### Post by jdong on 2006-04-11
Fedora's a pretty sweet distro; if you search me up in this section and fedora, you'll find my opinions about Fedora.

* Note that Fedora tends to lean towards bleeding edge quite often; I've rarely been actually troubled by breakage due to it, but just some of the changelog entries for updates has concerned me ;).
* Fedora has a lot of cool technologies to play with. They spend a lot of time getting Xen and SELinux polished up. If you're more of the linux nerd on the inner side of the OS, you'll enjoy having a Fedora installation around.
* Fedora's combination of bleeding-edge OS components and incorporation of new technologies often leads to 3rd party stuff not working well (i.e. kernel drivers from other sources, 3D graphics drivers, commercial software, etc). Typically it does become fixed in time, but it can be very frustration.
* Expect a lot of updates. They'll taper off in a few months.


Also, when comparing driver compatibility of Fedora and Ubuntu, please compare against Dapper Drake. Breezy is now 6 months old, so any new driver work that happened within the past 6 months (believe me, a lot) does not reflect itself in Breezy. Dapper and FC5 are pretty much on par with each other on hardware support, but more proprietary/non-free drivers work out-of-the-box on Ubuntu than on FC5, in my experience.


FC5 also seems slower than Ubuntu, for one reason or another.

---

### Post by K.Mandla on 2006-04-11
[QUOTE=LightsOut]My ipw2200 card worked right out the box for me.[/quote]
Aw nuts, I wish mine had. I got nothing out of it. I don't know all the ins and outs of FC5, but it didn't show up in the networking tools, and I didn't know how to make that happen.

I'll probably check it out again in the near future. I have this weird quick-look thing I do when I check out new distros or even new OS's. I peek at it, say "that's nice", go away for a month or two, then dig in to it a lot more. That's what happened with Ubuntu.

And next time I'll work harder to get everything to work. :)

---

### Post by Iandefor on 2006-05-18
I installed Fedora Core 5 a while ago, and I documented the experience. Here's a teaser- you'll have to read the full document for all the gory details!

> 
The bespectacled, overweight geek dropped a disk sleeve and a flier for some Red Hat conference or another in front of me. The disc sleeve was blue, and emblazoned with the 'Freedom Forever' Fedora logo- Fedora Core 5. I thanked him, but he just grunted and kept moving. Perhaps my conspicuous lack of a laptop at LinuxFest Northwest left me unworthy of a response. Well, whatever. I'd been hanging out at LinuxFest Northwest on April 29th. It was raining like a sonofabitch, but thankfully, I was inside, attending presentations like "Turing's Cathedral" By George Dyson, and "Incoming! What's of the EFF's Radar." By Danny O'Brien. It was pretty fun, but the presentation entitled "Fedora and Lessons in Community Building" By Greg DeKoenigsberg turned out to be the most interesting.

---

### Post by Iandefor on 2006-05-18
*Bump!*

---

### Post by Sheinar on 2006-05-18
I would read it, but AbiWord doesn't want to import it.

---

### Post by Iandefor on 2006-05-18
[quote=Sheinar]I would read it, but AbiWord doesn't want to import it.[/quote] That could pose a problem.

---

### Post by woedend on 2006-05-18
unfortunately I did the same thing...I didn't have openoffice installed so didn't bother.  Have you by chance considered posting the contents to a webpage?  Just seems easier to read and bookmark.  But please bump again if you get it in another format...i'll give it a read...even though I think FC5 is the devil!! 
take care.

---

### Post by Iandefor on 2006-05-18
[quote=woedend]unfortunately I did the same thing...I didn't have openoffice installed so didn't bother.  Have you by chance considered posting the contents to a webpage?  Just seems easier to read and bookmark.  But please bump again if you get it in another format...i'll give it a read...even though I think FC5 is the devil!! 
take care.[/quote] Fixed it. Now it's in pdf, so even people without OO.o should be able to read it.

Why is FC5 in specific the devil?

---

### Post by woedend on 2006-05-18
hehe...just personal opinion of not having a good experience with it...nothing evil in particular :).  Now keep in mind I only used it when it first came out...yum is terribly terribly slow for me, nvidia wasn't installable, and certain programs(specifically firefox) would hang on first launch for up to 15 seconds!  I even installed twice just to make sure.  Hopefully they've fixed this by now.  But I can't give up apt - do you like fc5 better than ubuntu?

---

### Post by Iandefor on 2006-05-18
[quote=woedend]hehe...just personal opinion of not having a good experience with it...nothing evil in particular :).  Now keep in mind I only used it when it first came out...yum is terribly terribly slow for me, nvidia wasn't installable, and certain programs(specifically firefox) would hang on first launch for up to 15 seconds!  I even installed twice just to make sure.  Hopefully they've fixed this by now.  But I can't give up apt - do you like fc5 better than ubuntu?[/quote] In some ways, I like it better. The desktop experience is pretty slick, at least so far, it's as fast or faster than Ubuntu, and it looks nicer upon first boot than Ubuntu (imho). Then again, rpm is a terrible scourge upon the earth and should be destroyed and buried and never used again. The NVIDIA drivers aren't playing nice with my GPU, but that's fixable by using vesa.

I guess it's right up there with Ubuntu, neck and neck. We'll see with FC 6.

---

### Post by TrailerTrash on 2006-05-18
So Iandefor, are you going to come up with a Fedora BUMPS?

---

### Post by ComplexNumber on 2006-05-18
i think fedora core 5 is the best of the lot. i still have it running as smoothly as ever.

---

### Post by Iandefor on 2006-05-18
[quote=TrailerTrash]So Iandefor, are you going to come up with a Fedora BUMPS?[/quote] BFMPS? No, I don't think so. I briefly considered it, but decided that I hated yum so much I would never be so cruel as to subject a poor shell script to it.

No, the real reason is that I don't feel like researching into making a Fedora Core version, nor am I interested in maintaining one. 

But I actually did consider it :).

---

### Post by ComplexNumber on 2006-05-18
**Iandefor**
why don't you install apt? also install a package manager frontend called Smart. its very good.

---

### Post by Iandefor on 2006-05-18
[quote=ComplexNumber]**Iandefor**
why don't you install apt? also install a package manager frontend called Smart. its very good.[/quote]I could, but I'm having so much fun bashing rpm/yum :)!

I'll look into it, but isn't the apt on RH-based systems just a prettier frontend to rpm?

And I must look into this new package manager more- Shuttleworth had hinted at it being in Edgy.

---

### Post by ComplexNumber on 2006-05-18
well, i personally much prefer rpm. i had a horrible time with dpkg and deb when using ubuntu, and i didn't like them at all. maybe its because i'm more well acquainted with rpm.
> 

I'll look into it, but isn't the apt on RH-based systems just a prettier frontend to rpm? no. its exactly the same as that on debian systems. its also not a frontend.

---

### Post by Iandefor on 2006-05-18
[quote=ComplexNumber]well, i personally much prefer rpm. i had a horrible time with dpkg and deb when using ubuntu, and i didn't like them at all. maybe its because i'm more well acquainted with rpm.
 no. its exactly the same as that on debian systems. its also not a frontend.[/quote] Excellent!

---

### Post by TrailerTrash on 2006-05-18
Like i say Iandefor, I love your work. I thought if you made something for Fedora, then....that would be just swell!:) 

Anyways, have you heard of Fedora Frog? Its for Fedora and it installs all of the goodies for Fedora. My Fedora is working great but i HATE YUM!!!!](*,) :-#

---

### Post by ComplexNumber on 2006-05-18
> My Fedora is working great but i HATE YUM!!!
use apt then. alternatively, use a GUI installer like smart or synaptic  instead of the command line.

---

### Post by TrailerTrash on 2006-05-18
[QUOTE=ComplexNumber]use apt then. alternatively, use a GUI installer like smart or synaptic  instead of the command line.[/QUOTE]


Hmmm..I never thought of that...DUH ](*,) ](*,) :oops:

Dose Synaptic and/or Smart work ok on Fedora?

---

### Post by ComplexNumber on 2006-05-18
>  Dose Synaptic and/or Smart work ok on Fedora?
yes. i have used synaptic before (although its not presently installed), but i'm using Smart at the moment on FC5.

---

### Post by jbmalone on 2006-05-19
I still plan installing FC5 on my desktop before the end of the summer...

Good review, I enjoyed reading it.

---

### Post by ubuntu_demon on 2006-05-19
nice review.

I don't agree with this part :

> 
Take this with Mark Shuttleworth's announcement of plans to impose no major goals for Edgy,
and instead to let it be the wild-child release after Dapper, it looks like Ubuntu will have some
major catching-up to do in Edgy+1.


Dapper has to be super stable and robust. IMHO Edgy gives is the perfect moment to try new things. People that want stability have Dapper. For Edgy new things can be tried but it won't be as stable as Dapper. Edgy+1 will be more stable again.

from fridge.ubuntu.com :

[quote=Mark Shuttleworth]
So dream a little about Xen for virtualisation, Xgl/AIGLX and other wonderful wobbly window bits, the goodness of Network Manager, a first flirt with multiarch support for true mixed 32-bit and 64-bit computing on AMD64, the interesting possibilities of the SMART package manager&#8230; and other pieces of infrastructure which have appeared tantalisingly on the horizon.
......
We can afford to take some risks with Dapper+1, because Dapper has turned out so well. We have a great answer for people who need super-solid and super-predictable results: Dapper is still fresh, will continue to work on modern hardware for some time, and has plenty of legs in its support cycle left to run.
[/quote]

---

### Post by Iandefor on 2006-05-19
ubuntu_demon:

I guess we'll just live with opposing views, then, eh? We're taking different conclusions from essentially the same information.

---

### Post by ubuntu_demon on 2006-05-20
[QUOTE=Iandefor]ubuntu_demon:

I guess we'll just live with opposing views, then, eh? We're taking different conclusions from essentially the same information.[/QUOTE]

evidently :)

But there will be specs. Take a look at them after the Paris dev summit. Maybe you'll like them ... maybe not.

All Ubuntu specs are here :
[https://launchpad.net/distros/ubuntu/+specs](https://launchpad.net/distros/ubuntu/+specs)

Dapper's specs are here :
[https://launchpad.net/distros/ubuntu/dapper/+specs](https://launchpad.net/distros/ubuntu/dapper/+specs)

Edgy's specs will probably here :
[https://launchpad.net/distros/ubuntu/edgy/+specs](https://launchpad.net/distros/ubuntu/edgy/+specs)

---

### Post by Iandefor on 2006-05-27
[quote=ubuntu_demon]evidently :)

But there will be specs. Take a look at them after the Paris dev summit. Maybe you'll like them ... maybe not.

All Ubuntu specs are here :
[https://launchpad.net/distros/ubuntu/+specs]("https://launchpad.net/distros/ubuntu/+specs")

Dapper's specs are here :
[https://launchpad.net/distros/ubuntu/dapper/+specs]("https://launchpad.net/distros/ubuntu/dapper/+specs")

Edgy's specs will probably here :
[https://launchpad.net/distros/ubuntu/edgy/+specs]("https://launchpad.net/distros/ubuntu/edgy/+specs")[/quote] Ah, good to know.

When will this summit be?

---

### Post by Omnios on 2006-06-10
I spend most of today resising and remaking my drive partitions so I have a 39 Gig drive to load different distros to try out. Anyways I already tryed Debian and now want to give Fedora a try. Anyways looking on the download page it has 5 cds to download and am wondering how many I actualy need to download to do a install. Any suggestions welcome

---

### Post by ComplexNumber on 2006-06-10
i think its 2(possibly 1) for a basic install

---

### Post by user1397 on 2006-06-10
you can download the install dvd if that's less of a hassle for you, and if you have dvd capabilities on your pc

---

### Post by Omnios on 2006-06-12
Tryed doing the Fedora install with 2 iso images but it did not complete the install and also tryed updating the install to set it up for a 2 cd install which resulted in the start up hanging in checks. Anyways im downloading the third cd iso image now and it should work as there was only 6 minuts left in the install after the two iso images. Ill update probably tomoro after I finish downloading the third disk and burn it. Also tryed doing the grub reinstall which whiped out my Ubuntu and unfortunatly I also have a new Ubuntu install today to but managed to get Fedora into the grub.

---

### Post by ComplexNumber on 2006-06-12
**Omnios**
after you've successfully downloaded it, get [this]("http://easylinux.info/wiki/Fedora_frog"). its the equivelent of ubuntu's automatix.

---

### Post by RAV TUX on 2006-06-12
I found fedora a complete waste of blank CD's and DVD's.

---

### Post by ComplexNumber on 2006-06-12
[quote=yozef]I found fedora a complete waste of blank CD's and DVD's.[/quote] why do you say that? 

translated, that can only mean that it doesn't work with your hardware

---

### Post by Omnios on 2006-06-13
After spending a day downloadingh the third disk iso I tryed to install Fedora again only for it to take a few seconds to get the files off the image and ask for disk 4. As it stands now I think Ill give up on fedora as it will take two days to download the last two disks. Also there dows not seem to be a net install for fedora core 5 so as things stand I will wait till I can get a better internet connection.

---

### Post by RAV TUX on 2006-06-13
[quote=ComplexNumber]why do you say that? 

translated, that can only mean that it doesn't work with your hardware[/quote]

Your translation is correct.

Gentoo, Yoper, Dreamlinux and dyne:bolic worked at detecting my hardware without event. They "Just Work".

Gentoo
[http://www.gentoo.org/](http://www.gentoo.org/)

Yoper
[http://www.yoper.com/](http://www.yoper.com/)

dyne:bolic
[http://www.dynebolic.org/](http://www.dynebolic.org/)

Dreamlinux
[http://www.dreamlinux.com.br/](http://www.dreamlinux.com.br/)

---

### Post by asimon on 2006-06-13
I needed all 5 CDs for an installation, but I installed both Gnome and KDE, and a lot of development stuff too, including the eclipse package group.

---

### Post by basketcase on 2006-06-13
I played with FC3 back in the day and it had it on my server up until I decided to move it over to Ubuntu 5.10.  I've been considering FC5 to see how the distro has come along.  My only complaint is I hated RPM dependencies, but it seems 'yum' has taken care of that for the most part.

---

### Post by Omnios on 2006-07-23
Hi hi well It was realy wierd I took my time and downloaded the other CD's so I ended up with 5 in totoal, now the wierd part the failed installs all asked to 5 cd's and my successful install only required 3 cd's, Anyways without installing Fedora Grub be prepared to manualy edit the Ubuntu grub file basicly just think linux and hack at it lol. Anyways its figuring out grub is very simple and there are a few posts on what to do. Well now I officially have had three Linux distros installed and look forward to play with it a bit though I dought any distro I install will ever replace Ubuntu as my main os.

 Ubuntu
 Debian
 Fedora
 
 Is there still a Red Hat Desktop????

---

### Post by Iandefor on 2006-07-23
> **Omnios said:**
> Hi hi well It was realy wierd I took my time and downloaded the other CD's so I ended up with 5 in totoal, now the wierd part the failed installs all asked to 5 cd's and my successful install only required 3 cd's, Anyways without installing Fedora Grub be prepared to manualy edit the Ubuntu grub file basicly just think linux and hack at it lol. Anyways its figuring out grub is very simple and there are a few posts on what to do. Well now I officially have had two Linux distros installed and look forward to play with it a bit though I dought any distro I install will ever replace Ubuntu as my main os. Yeah, the "I need all 5 discs to install even though I'm only using 3 of them" is a little annoying. [I've hit that problem before]("http://www.ubuntuforums.org/showthread.php?t=178607").> Is there still a Red Hat Desktop???? It's officially called Red Hat Enterprise Linux now.

---

### Post by Omnios on 2006-07-23
Well checked out Fedora today and it seems pretty standard but I realy do not see any advantages over Ubuntu at all. Things are a bit different the package manager takes for ever to update and start and from what I have seen Ubuntu is still a better choice for begginers after trying to research some stuff on the forum. I will probably play with it for a bit but  prefear Ubuntu.

---

### Post by w_r_cromwell on 2006-07-29
> **Iandefor said:**
> Yeah, the "I need all 5 discs to install even though I'm only using 3 of them" is a little annoying. [I've hit that problem before]("http://www.ubuntuforums.org/showthread.php?t=178607"). It's officially called Red Hat Enterprise Linux now.

I turned my back on RedHat when they started that Enterprise stuff because it started making noises like Microsoft's obnoxious marketing and license model. I still use RedHat 9 and I am preparing to update that with a new kernel, libraries, and apps. I don't have much experience doing that so I will get to learn some new skills.

Ubuntu has failed to deliver in my opinion <heresy I know>. I am not going to give up on Ubuntu yet. I have talked a couple of people who wanted to get away from MS into trying Ubuntu and it keeps breaking and tripping them. They are both back on Windows XP. If they have to learn the inner workings to make it do what they want then I think RedHat is much more robust (just my own experience). I started with RH at version 4 and I was able to completely get rid of MS (on my personal machines) by version 5. So I am biased but accustomed to a system that runs as configured each and every time I issue the command...not just sometimes or on certain fridays or only during waning moon phases. Okay... enough of the exaggeration.

Bill

---

### Post by Peter Mount on 2006-07-29
If you do wind up liking Fedora check out:

[http://www.stanton-finley.net/](http://www.stanton-finley.net/)

It's the "Fedora equivalent" of the [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) help page for K/X/Ubuntu.

Fedora Core 5 is a perfectly good distro for most people. I just found I "hit the wall" with it when I tried to set up the version of LAMP that I needed. Plus I found Ubuntu has a program available for finding orphan dependencies that I didn't find with Fedora. I think Ubuntu's program is "deborphan" (correct me if I'm wrong).

Have fun

---

### Post by RAV TUX on 2006-07-30
These 4 threads have been merged:

[http://www.ubuntuforums.org/showthread.php?t=147516](http://www.ubuntuforums.org/showthread.php?t=147516)
[http://www.ubuntuforums.org/showthread.php?t=157870](http://www.ubuntuforums.org/showthread.php?t=157870)
[http://www.ubuntuforums.org/showthread.php?t=178607](http://www.ubuntuforums.org/showthread.php?t=178607)
[http://www.ubuntuforums.org/showthread.php?t=193975](http://www.ubuntuforums.org/showthread.php?t=193975)

one Fedora Core 5 is enough.

---

### Post by Iandefor on 2006-08-02
> **yozef said:**
> These 4 threads have been merged:

[http://www.ubuntuforums.org/showthread.php?t=147516](http://www.ubuntuforums.org/showthread.php?t=147516)
[http://www.ubuntuforums.org/showthread.php?t=157870](http://www.ubuntuforums.org/showthread.php?t=157870)
[http://www.ubuntuforums.org/showthread.php?t=178607](http://www.ubuntuforums.org/showthread.php?t=178607)
[http://www.ubuntuforums.org/showthread.php?t=193975](http://www.ubuntuforums.org/showthread.php?t=193975)

one Fedora Core 5 is enough. Merge acknowledged, but why is only 1 thread enough?

---

### Post by RAV TUX on 2006-08-02
> **Iandefor said:**
> Merge acknowledged, but why is only 1 thread enough?

Edit that:  9 fedora threads should be enough;) (some are Fedora Core  5, some other versions)

[http://www.ubuntuforums.org/showthread.php?p=1331704](http://www.ubuntuforums.org/showthread.php?p=1331704)
[http://www.ubuntuforums.org/showthread.php?t=6553](http://www.ubuntuforums.org/showthread.php?t=6553)
[http://www.ubuntuforums.org/showthread.php?t=20218](http://www.ubuntuforums.org/showthread.php?t=20218)
[http://www.ubuntuforums.org/showthread.php?t=39265](http://www.ubuntuforums.org/showthread.php?t=39265)
[http://www.ubuntuforums.org/showthread.php?t=36756](http://www.ubuntuforums.org/showthread.php?t=36756)
[http://www.ubuntuforums.org/showthread.php?t=41316](http://www.ubuntuforums.org/showthread.php?t=41316)
[http://www.ubuntuforums.org/showthread.php?t=135944](http://www.ubuntuforums.org/showthread.php?t=135944)
[http://www.ubuntuforums.org/showthread.php?t=133802](http://www.ubuntuforums.org/showthread.php?t=133802)
[http://www.ubuntuforums.org/showthread.php?t=43480](http://www.ubuntuforums.org/showthread.php?t=43480)

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***Fedora Tech Talk***

organizing a bit I have merged these threads:

[http://www.ubuntuforums.org/showthread.php?t=36756](http://www.ubuntuforums.org/showthread.php?t=36756)
[http://www.ubuntuforums.org/showthread.php?t=231262](http://www.ubuntuforums.org/showthread.php?t=231262)
[http://www.ubuntuforums.org/showthread.php?t=135944](http://www.ubuntuforums.org/showthread.php?t=135944)
[http://www.ubuntuforums.org/showthread.php?t=147516](http://www.ubuntuforums.org/showthread.php?t=147516)

---

### Post by cantormath on 2006-08-07
> **yozef said:**
> I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***Fedora Tech Talk***

Should be gentoo talk, or slackware talk....or BSD-from-Floppy talk, lol FC is cool...::grin::

---

### Post by RAV TUX on 2006-08-07
> **cantormath said:**
> Should be gentoo talk, or slackware talk....or BSD-from-Floppy talk, lol FC is cool...::grin::

actaully Gentoo was the first one of the series and PC-BSD has been started too....keep in mind we can add to the list as needed....just PM me with ideas.

---

### Post by cantormath on 2006-08-07
ah man, sorry, I clicked on new post and saw the rest of them, duh to me.

---

### Post by RAV TUX on 2006-08-07
> **cantormath said:**
> ah man, sorry, I clicked on new post and saw the rest of them, duh to me.

Thats cool just glad to see that this is getting responses so early....remember try to utilize these threads for Tech Talk about the perspective Distro...

---

### Post by Iandefor on 2006-08-08
Well, dammit all... I installed FC5 on my laptop. I did NOT have half so good a time as when I installed it on my desktop. It installed fine, yes, but it appears to have played hob with my partition tables. Ubuntu stopped booting, and Fedora, well, Fedora wouldn't even boot. So, first try, I screwed something up. Nothing new :). I went ahead and hosed all my other operating systems and put FC5 on a single partition. And that's when I began the process of learning that (to put a spin on the old "Ubuntu ain't Windows" thing:D)... FC5 ain't Ubuntu! For some reason unbeknownst to me, after I opened gconf-editor and checked off "always use browser view" in the nautilus settings, because I hate spatial view, and "always use location bar", because I prefer it... gconf-editor locked up. Hard. A manual killall did the trick... but it was not confidence-inspiring. After that, nautilus began to act rather strangely. Icons in Icon View obeyed their *own* rules when it came to organising themselves. I was baffled... and then gnome-settings-demon sort of disappeared. Things did not get better, but suffice it to say that when I went to repartition the disc on my laptop so I could reinstall Ubuntu, the partitioner freaked out. It eventually began to work, but, *damn*, it even screwed up my hard disc for a time. I wonder what it was I did wrong... ah, well. I'm re-downloading the discs (I tossed out the others by accident yesterday) and I'm going to give it another go! I just hope that, this time around, it works out better :). I'm going to be more careful on the install this time around, and if it still throws a wobbler, I'll just wait for FC6, because that will have been the third install of FC5 (out of 4!) that has failed on me. I'm willing to blame my failure on the computer gnomes. They must have possessed my computer or something :).

More to come!

---

### Post by ComplexNumber on 2006-08-08
> after I opened gconf-editor and checked off "always use browser view" in the nautilus settings, because I hate spatial view, and "always use location bar", because I prefer it
not necessary. just fire up nautilus, select Edit in the menu, then select the 2nd tab. see screnshot below

---

### Post by Iandefor on 2006-08-08
> **ComplexNumber said:**
> not necessary. just fire up nautilus, select Edit in the menu, then select the 2nd tab. see screnshot below *sighs*

Someone smack me in the head, please. Seriously. 

Somehow that configurator option escaped my notice. Well, it's a little late to see if that would have prevented a hard lockup on my previous setup, but I'll keep it in mind.

Oh, and thanks :-D.

---

### Post by ComplexNumber on 2006-08-08
> **Iandefor said:**
> *sighs*

Someone smack me in the head, please. Seriously. 

Somehow that configurator option escaped my notice. Well, it's a little late to see if that would have prevented a hard lockup on my previous setup, but I'll keep it in mind.

Oh, and thanks :-D.
i can't see any reason why using nautilus rather than gconf-editor would have made much difference in causing the lockup. but just in case it does, let me know how you get on :)

---

### Post by Iandefor on 2006-08-08
> **ComplexNumber said:**
> i can't see any reason why using nautilus rather than gconf-editor would have made much difference in causing the lockup. but just in case it does, let me know how you get on :) The lockup was in gconf, so if it ain't running, odds are low it'll lock up :). But, you never know.

---

