---
title: "What is the differance between Lenny and Gusty?"
date: 2007-11-02
forum: Debian
---

### Post by OldGaf on 2007-11-02
Hi all,

I know there were probably MANY discussion on this over the last few years, and I do NOT want to start a flame war.

Having said that, I have been having a few minor issues with Ubuntu lately so I decided to give Debian a try. I installed Etch (4.0r1) yesterday and was very surprised that the installer was almost identical to Ubuntu (I have always heard it was so much harder to install). I then added 

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

deb [http://security.debian.org](http://security.debian.org) etch/updates non-free

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) etch main non-free contrib

To get java, flash, MP3 support and all that good stuff.

Then I added

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) testing main

to get the latest versions of applications, kernel and headers. 
This gave me the current Lenny.

After installing KDE and removing Gnome, my system is pretty much identical to the Gusty I had. 

One difference is the minor annoyances I had with Kubuntu are gone.

Another odd thing was that the install scrips on a few applications seemed to be more freindly then Kubuntu's. 

During the Samba install, it asked me if I wanted to add a domain or workgroup name. During the Amarok install it asked me if I wanted to setup MySQL.Like I said, not biggie's, but it meant I did not have to edit a file or what ever after these applications were installed. I would have thought it would have been the other way around..... that Kubuntu would have asked the questions and Debian would expect me to manually change things to my liking.

Anyway, my point is that Debian is not at all what I was expecting. It is much, much better. 

Now, on to my question.

What exactly does canonical do to Debian besides branding, to make it Ubuntu?

And don't talk about release dates....

From what I have read, the "Stable" version is Etch, and is stable in the sense that Dapper is stable. Lenny is more like Edgy / Feisty / Gusty, but doesn't have separate releases every 6 month... they just keep adding and fixing / changing things until Lenny is Officially called stable and like Dapper, they don't "mess" with it anymore.

So, that been said, what is the real difference between the current versions Lenny and Gusty ?

---

### Post by arkara on 2007-11-02
i don't think that there is much difernence.

---

### Post by Incense on 2007-11-02
Ii think ubuntu is based on sid, with the packages frozen for six months. I could be mistaken though.

---

### Post by OldGaf on 2007-11-02
> **Incense said:**
> Ii think ubuntu is based on sid, with the packages frozen for six months. I could be mistaken though.

I have read (but don't know if it is true), that every six months they take a snapshot of the current Debian test (which would be Lenny for Gusty) and then do........... stuff...... ?

---

### Post by meborc on 2007-11-02
i have heard... :D

that ubuntu development version (hardy for now) is made out of daily (or was it weekly) snaps of debian unstable...

it might be right, but then again, i have been hearing a lot lately

---

### Post by p_quarles on 2007-11-02
There's some Ubuntu-specific stuff that gets added, such as the Add/Remove Programs frontend. Apart from that, Ubuntu releases are all "stable" in the sense that libraries and applications won't get any major upgrades until the next release.

Thanks for the heads up on the KDE stuff. I've been having a few minor annoyances in 7.10 (specifically, webkit behaving erratically, and DNS not working for about three minutes shortly after logging in). I might just go with Debian. 

Btw, it's Gu**ts**y Gibbon. As in bold, not flatulent. :)

---

### Post by Bachstelze on 2007-11-02
Moved to the Other OS Talk forum.

---

### Post by Antman on 2007-11-02
> **Incense said:**
> Ii think ubuntu is based on sid, with the packages frozen for six months. I could be mistaken though.

Yes, "I have heard" that too. Basically a Debian Sid (unstable) snapshot is taken, then the Ubuntu devs use that as their basis for the next Ubuntu release and add the Ubuntu tools, tweaks, extra to it.

And I agree with the thread starter that running true Debian has definite advantageous.

---

### Post by tturrisi on 2007-11-02
There's absolutely nothing "stable" about Ubuntu when using the term "stable" in the same context as Debian stable.  Ubunti is built from kernels that are not even available yet in Debian Sid, along with Sid packages.   It is then branded w/ Ubuntu multimedia as well as some other Ubuntu only packages.

Even Ubuntu Dapper is not Debian "stable".

Ubuntu versions become "stable" in a different context of the term "stable" in that new versions are released every 6 months, however the older versions are not really "stable" either.

Ubuntu is NOT safe to use for production servers or for production workstations where stability is necessary, expected and required.  One should always expect issues and glitches in ANY version of Ubuntu, even the versions that are 2 years old.

I'm not "Ubuntu bashing", just pointing out the facts.  I run Debian Sid on my production laptop, I get some glitches, very few, because I don't upgrade the whold system constantly.  I get the system working just how I want it and then keep it that way.  I may intentionally screw it up AFTER I've made the decision to wipe the disk and do a clean new install, that happens about once or twice/year!

My servers are running Debian Woody and Debian Etch.  Rock solid and unbreakable.  The Woody server has not been rebooted in several years except for power brown outs and black outs.

---

### Post by b9anders on 2007-11-03
There are a number of differences

As already pointed out, the difference in base. Testing is based on stable with new packages from sid trickling down after a couple of weeks of being tested there. So glitches trickle in in a much more controlled fashion than in Ubuntu based on sid where nothing is considered stable. Ubuntu is essentially 4-5 months work on 10,000+ unstable packages to be stable enough for release. That it works out is a tribute to how well managed Debian is even in unstable.

Ubuntu loads a different kernel with more modules for more out of the box functionality and also changes the boot process. It reorders and renames packages. The changes are strong enough that it is not a good idea to use Ubuntu packages on a Debian system (I still wish Ubuntu would pay more attention to this area - most of the debian family has no problem running debian packages all across the board - it's all comes from and is compatible with debian. Now more and more packagers for software not in the repos are making packages for Ubuntu over debian, essentially cutting out the rest of the debian family).

Debian is much more vanilla in its setup. You won't recognise nautilus when you first run it in debian compared to ubuntu, no bootsplash and such.

A number of in-house applications developed for Ubuntu like bullet-proof X, the codec install etc.

In summary Ubuntu works out much better in the 'it just works' department. If you're finding yourself tweaking your system with what processes to load on boot, how the DE behaves etc. you might enjoy Debian more as it offers a more stable base that encourages tweaking more and is significantly faster as well. It probably takes more time to set up in a way you like (then again, if you are a tweaker, you'll probably spend more time disabling presets in Ubuntu than setting up things in debian), but once the initial legwork is done, both are a breeze to maintain thanks to apt.

and then of course there is the difference that Debian has a super user distinct from the ordinary user instead of using sudo for everything.

---

### Post by OldGaf on 2007-11-07
The biggest difference I see so far is that it is VERY stable, even tho I added several applications from the testing repo, and The Gimp from the unstable repo. I have everything I want with no issues at all (so far!) I was even able to get my webcam to work, something I could not do with Gutsy, even tho it worked "out of the box" with Feisty. It was little annoyances like that which pushed me to Debian proper...... and I am glad I switched!

---

### Post by ubuntu27 on 2007-11-23
I am using Debian now, and I see some major difference such as not being able to have a working input method for asian lagnagues easely. See the following thread:

[Japanese input in Debian]("http://ubuntuforums.org/showthread.php?t=620762")

PS: I still need help with that.


The GUI apps between Ubuntu and Debian are not the same (Synaptic Source for example.  (I think Ubuntu's Source is intuitive)   *** See my attachment, compare with Ubuntu**

********

Also, unlike my experiences with Kubuntu, Debian with KDE is stable. I don't get any random errors and crushes which I experienced with Kubuntu Feisty.

---

### Post by DjBones on 2007-11-24
not a whole lot of difference between the two really..
aside from the brown theme, ubuntu isn't much different debian testing/unstable haha
aside from my laptop, my other three computers run debian testing

from what i've read on the debian forums though, ubuntu dev's do alot of work on the kernel (hence all the great hardware recognition) but it doesn't easily make its way back up stream very well.

---

### Post by angryfirelord on 2007-11-24
Debian Unstable is the rock from which Ubuntu is built. ;)

Seriously though, Ubuntu is nice because it doesn't change, whereas Debian Testing or Unstable tend to move around a lot. But in terms of quality of packages, Debian certainly does that better because the Ubuntu devs tend to mess around with some things.

---

### Post by mojoman on 2007-11-25
I'm running Debian Lenny now. It's working great. More packages that are more up to date and more stable. That's hard to beat. I had a look at some packages, picked more or less randomly, that was available in both Gutsy and Lenny. Lenny always had a newer version, and though I haven't any experience with Gutsy I can say that Lenny is more stable than Feisty. The two things Ubuntu got going in comparison is ease of installation and configuration (though Debian isn't that hard these days) and a very big user base, which means large support forums (though, in all fairness, I think the members average level of expertise is considerably higher in a Debian forum than in, for example, this forum).

Me, I'm getting a bit sick and tired of the six month release cycle. I mean, upgrade is not always smooth so you'll be better off doing a fresh install. Now, I have a separate /home so that's not the end of the world for me but it gets tedious. I prefer the package-by-package replacement model. Also, I just installed Gutsy but the _[fonts are screwed]("http://ubuntuforums.org/showthread.php?t=623036")_ up so I might just stick with Debian for now (with the non-working Gutsy I'm tri-booting and I got a spare partition on top of that that I'll figure out something nice to install on, just to try it out). But my two cents is that Debian got the upper hand.

/mojoman

---

