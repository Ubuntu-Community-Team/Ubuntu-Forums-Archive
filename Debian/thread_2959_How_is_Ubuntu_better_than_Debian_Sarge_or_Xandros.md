---
title: "How is Ubuntu better than Debian Sarge or Xandros?"
date: 2004-11-02
forum: Debian
---

### Post by stevho on 2004-11-02
Say for an average home or small business desktop, and ignoring the relatively insignificant difference in costs of the OS themselves, what are the main advantages of Ubuntu over Debian Sarge and Xandros?

---

### Post by diebels on 2004-11-02
It's the best of both worlds. Debians ethics and Xandros ease of use. It's Ubuntu.

---

### Post by kamstrup on 2004-11-02
It would be rather lengthy to rant about all the differences. The best way to go about this is to try all of them and find which one you like best (this would ofcourse be Ubuntu ;P ).

No seriously. It is not that big a deal (if you have a spare computer and some time) to try out the three distros. I think there is a free version of Xandros (without the full capabilities of the non-free version) out there.

Xandros comes with a tailored KDE desktop so if you swear to Gnome, this already settles the choice between Debian Sarge and Ubuntu. Again if you really dig Gnome, Ubuntu would be your choice since the Gnome desktop shipped with Ubuntu is really nice.

---

### Post by az on 2004-11-02
Xandros is proprietary.  This makes it difficult for the user.  It also does nothing to add to debian.

Ubuntu is free software.  If you want to add proprietary or non-free software to your system, you can - easily, but this is your choice.  You do not get that choice withXandros.

Also, I could never get the "personnal" editions of Xandros to install.  I tried two different versions and they both failed.

---

### Post by AndyGates on 2004-11-05
Speaking as a noob who installed Ubuntu last night: the install is really EASY.  For the average user, that's gotta be a plus.  I think all I had to do was say "splat my disk" and pick a username and then all from one CD was an OS, Office, web, mail, and Tetris.  For free.  How cool is that?

(Of course, I haven't got into setting up my various devices yet ;) )

---

### Post by georgeg on 2004-11-05
I'm currently playing with Xandros OCE and last night I booted up the Ubuntu Live version.  While I like the look of the Xandros KDE desktop, I was more impressed that Ubuntu recognized my sound card which Xandros didn't.  I'll play with Ubuntu Live more over the weekend and if I like what I experience, I just may change.  Xandros is nice and may be better when 3.0 comes out but it will probably be close to a year before 3.0 filters down to the OCE (free) level.  Ubuntu has most all of the features of Xandros 3.0 right now.  I just wish they offered a choice between KDE and Gnome.

---

### Post by ubuntu-geek on 2004-11-05
[QUOTE=georgeg]I'm currently playing with Xandros OCE and last night I booted up the Ubuntu Live version.  While I like the look of the Xandros KDE desktop, I was more impressed that Ubuntu recognized my sound card which Xandros didn't.  I'll play with Ubuntu Live more over the weekend and if I like what I experience, I just may change.  Xandros is nice and may be better when 3.0 comes out but it will probably be close to a year before 3.0 filters down to the OCE (free) level.  Ubuntu has most all of the features of Xandros 3.0 right now.  I just wish they offered a choice between KDE and Gnome.[/QUOTE]
 You might find this thread to value on the subject of KDE for ubuntu..

[http://ubuntuforums.org/showthread.php?t=2811&highlight=kde](http://ubuntuforums.org/showthread.php?t=2811&highlight=kde)

---

### Post by cseg on 2004-11-05
Both Ubuntu and Xandros are Debian-based distributions.  Ubuntu is now and forever free.  Xandros is a commercial distribution but a free-beer Open Circulation Edition is available as a bittorrent download.  Parts of the Xandros distribution are proprietary, like its Xandros File Manager.

Install: The Ubuntu install is pretty easy.  The Xandros install is even easier and prettier. :)  The Ubuntu install has a longer net-install component and seems to do the equivalent of an apt-get upgrade at installation time.  The Xandros installer installs only from CD and you will have to do your own upgrade after installation is complete.

Hardware detection:  depends on your hardware.  For many, both "just work".  For some, one or the other or both may have problems.  One feature of Xandros is that if you /change/ you hardware, it will re-detect it.  I don't think Ubuntu does this. 

Boot loader:  Xandros uses lilo and has a graphical boot menu.  Ubuntu uses grub and has a text-based boot menu.  Both will identify other operating systems that are on your system at the time of installation to allow multi-booting.

Releases:  Xandros seems to release new versions about every December -- v 3.0 is coming up.  Ubuntu is scheduled to release every 6 months -- Hoary Hedgehog is coming up.  In general, I think that Ubuntu will have fresher versions of software than Xandros.  Xandros has no clever names for its releases. :(  Ubuntu has open betas:  it you want to live near the edge you can help out with the development of the next release by simply updating your apt/sources.list.  Xandros has private betas:  you may apply to participate on their web site but you may not be accepted.

Repository support:  They both provide a "minimal" installation from CD which can then be enhanced by their own .deb repositories.  Both do not recommend going outside of their repositories.  Xandros is based on a Testing snapshot, Ubuntu is based on an Unstable snapshot.  Both have a "supported" repository and an "unsupported" repository.  (Who wants to do a comparison between them?)

APT GUI support:  Ubuntu uses Synaptic as a GUI front end to apt.  Xandros comes with an application named XandrosNetworks which performs the same function, but is also something of a Xandros "portal".  Of course you could use Synaptic on Xandros if you wanted since it uses apt for package management.  I simply use apt-get on both.  XandrosNetworks is reminisent of iTunes in that it is not a browser-based application but it behaves much like a browser with most content being delivered from the remote site.  Xandros also has a "Premium" membership which gives you discounts on non-free software, such as Star Office and CrossOver Office (I think).

root: Xandros has a active root account with a separate password.  Ubuntu has a "passive" root account which is accessed via sudo.  This is similar to the way that Mac OS X is set up (that my wife uses) and so is not really a surprise for me.  You can enable the root user on Ubuntu if you care to.

User Interface: Since Ubuntu was released, the GNOME vs KDE "war" has become a non-issue for me.  Ubuntu is the first GNOME-based distribution that I have encountered which is really clean.  Xandros has a KDE-based user interface which is also very clean.  I'm not aware of any features of either environment which makes it stand out over the other.  (If there are some, please enlighten me.)

Nautilus vs Xandros File Manager:  They have similar functionality, but XFM has the edge.  Both allow you to navigate through a Windows network.  For some reason, Ubuntu asks me for a username and password while Xandros does not.  Go figure.  Once I have navigated to a directory on the network, XFM allows me to locally mount that location so that it appears on the local file system (by default in your home directory) by clicking on a link.  Likewise, for me to share a local directory so that others can see it is just a right-click on the directory and selecting the Sharing option.  XFM also has data- and music-CD buring built in.  I've not gotten this to work on my version of Ubuntu, but I have not tried that hard, either.  In Xandros, if you have a Windows partition on your system, this shows up as "C:" in their file manager.

Services:  Ubuntu has no services turned on by default.  Xandros has samba active and possibly one or two more.  

kernel:  Ubuntu:  2.6.8.1; Xandros: 2.4.24.

X:  Ubuntu XFree86 4.3.?, Xandros XFree86 4.3.? (I think).

Software:  Ubuntu has Firefox and Evolution for browsing and email.  The Xandros OCE (Open Circulation Edition) uses Opera for both.  The commercial Xandros versions use Mozilla for both.

Screenshots:  [list]Ubuntu: [http://osdir.com/shots/slideshows/slideshow.php?release=156&slide=1](http://osdir.com/shots/slideshows/slideshow.php?release=156&slide=1)

Xandros: [http://osdir.com/shots/slideshows/slideshow.php?release=137&slide=1](http://osdir.com/shots/slideshows/slideshow.php?release=137&slide=1)[/list]

I like Ubuntu because it gives me a clean environment with the latest software.  Having a slightly off-the-beaten-path system (VIA M10000 (plug: [http://www.mini-itx.com/reviews/nehemiah/](http://www.mini-itx.com/reviews/nehemiah/))) it is important to me to be able to get the latest drivers and patches to the kernel and X to get the most out of my system.  Xandros is a well-integrated system which has excellent support for Windows interoperability.  Its a great transition OS for Windows users.  The commercial version comes with CrossOver Office pre-installed and provides and evaluation copy of Win4Lin (I think) in their repostory.  Their Business Edition can log you into a Windows Doman Controller.

---

### Post by jdodson on 2004-11-05
good description of features.  

it might just be me :grin: but to me, free/open source is a good thing.  it seems nuts when a gnu/linux vendor such as xandros proprietorizes something when 99% of the OS is free/open source.  they lock down thier package manager and file manager yet the rest of the OS is completley open?  i didnt understand this when suse did it(they dont anymore), and i dont understand it now.  

what happens when xandros folds?  it seems to me, eventually they will fold as the world cannot handle 2,000 pay to play gnu/linux distros.  lycoris suffers from this as well, or so it seems to me that it does. 

anyways, rock on ubuntu

 :grin:

---

### Post by kastorff on 2004-11-05
cseg, that is an outstanding summary of Xandros and Ubuntu. Ubuntu just replaced Xandros on one of my desktops and my laptop. (I have another machine with SuSE 9.1 Pro). Xandros has always been my favorite recommended distro for Windows users just coming to Linux, but Ubuntu is making me think twice. I agree with those who bring up the open source vs. proprietary aspects of the two, and I feel like over the long haul the more "open" the better. I am amazed at how polished Warty is for a first release...as soon as there is a supported KDE option, this distro will be very hard to beat.

---

### Post by dmeister on 2004-11-08
While it's obviously good that ubuntu is signficantly more free than Xandros, one of the aspects that attracted me to ubuntu over Debian proper is that the community seems more friendly to the use of non-free software with the system.

Personally, I rather like the fact that ubuntu works well somewhere inbetween the two extremes as they were.

---

### Post by idrinkwhisky on 2006-12-06
i have ubuntu on my system. but i just read somewhere that Xandros ships with  Crossover Office. This might be really useful for some people that want to use MS Office.

There are a few advantages of MS office over Open Office (mainly in Excel).
1) most people know VBA and don't know how to code in OO (the newest version of OO supports VBA though)

2) I believe the Excel "solver" / "goal seek" is better than the OO version of solver/goalseek.

3) familiarity of most people with MS Office.

---

### Post by RAV TUX on 2006-12-06
moving to other OS forum

---

### Post by mushroom on 2006-12-06
Fundamentally, they're all very similar. It's all about atmosphere. Debian has kind of a geeky, hackerish atmosphere that not everyone can get in to. Xandros has a cold, corporational atmosphere that doesn't do a whole lot in the way of promoting the fact that you're using FOSS, so one comforting factor to a new user that just switched from Windows is lost. Ubuntu has a very warm, community-oriented atmosphere that makes you feel good about using FOSS. It's that atmosphere along with a competent (though not perfect) default interface that made it the most popular Linux distro.

---

### Post by kazuya on 2006-12-08
I agree with Mushroom here. I like them all, but Ubuntu has the clear edge for me. Debian through knoppix may be more capable or fast, but Ubuntu's support and use is easiest for a noob or beginner up to an expert level.

---

