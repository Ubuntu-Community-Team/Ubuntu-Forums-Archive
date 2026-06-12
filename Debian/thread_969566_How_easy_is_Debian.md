---
title: "How easy is Debian?"
date: 2008-11-03
forum: Debian
---

### Post by chrispche on 2008-11-03
Compared to a fairly experienced Ubuntu user. If I was to make a switch, how would I find it. There are 3 DVD images to download. Is this the best way to go?

---

### Post by markharding557 on 2008-11-03
the best way to install debian is with a net install cd which is about 150mb it will fetch the rest from the internet.
debian is in many ways the same as ubuntu but is less automated eq multimedia you have to enable a non free repo and individualy install each component,there is no restricted extras or hardware drivers applet.
you may find yourself using the cmdline a little more.
the upside is you learn more and it is very stable and you don't have to install a new version every six months

---

### Post by markharding557 on 2008-11-03
sorry duplicate post

---

### Post by inportb on 2008-11-03
I find Debian extremely stable and lightweight compared to Ubuntu. If you're experienced with Ubuntu, you should have no trouble getting used to Debian. What markharding557 said is absolutely true; Debian is not the same as Ubuntu ;p I also prefer to use the netinst disc.

---

### Post by SunnyRabbiera on 2008-11-03
Debian these days is just as easy as ubuntu, but if you want more current software I will go for debian testing and just download the first image...
You really dont need the other disks unless you have a crappy connection, those disks are more for extra packages if you need them but most of the time you wont.
The only major hurdles you will encounter is yes debian is more terminal oriented though there are ways around that, debian does not have restricted stuff and getting multimedia working is rough around the edges.
But its not that far apart from Ubuntu in the long run, if you can use ubuntu you can use debian

---

### Post by kk0sse54 on 2008-11-03
I agree go with a netinstall of Debian testing(despite it's name I find it very stable) and then add X and a  Desktop Enviroment/wm etc etc afterwards you'll get a great solid stable and fast machine :)

---

### Post by jayson.rowe on 2008-11-03
Installing Debian is no harder than installing Ubuntu w/ the Alt. Install CD.
Just grab the net-install iso, or if you really want, just the first CD - you can also find 1-cd images that install KDE or XFCE by default instead of GNOME if you desire.

As for Stable/Testing/Unstable - I agree w/ the above posts - go for testing - it's the best balance of new and stable.

Most of what you've learned about Ubuntu will apply in Debian, so your learning curve should be pretty flat.

---

### Post by nvteighen on 2008-11-05
Relatively easy, when coming from Ubuntu. Differences are related to those tasks Ubuntu automates for you.

If you prefer a GUI installer that leads you to a standard GNOME desktop instead of a command line, use the CD image #1 or DVD image #1 (the DVD gives you the source code, where the CD not). After that, you can enable the repos (for some reason, in testing a.k.a "Lenny", you only get the updates repository by default, not even the 'main' one).

Something you may miss is sudo. In Debian, the default is su. You can configure sudo if you like, but again, is not the default.

---

### Post by tommcd on 2008-11-06
Here is a good tutorial for getting started with Debian:
[http://forums.debian.net/viewtopic.php?t=13362](http://forums.debian.net/viewtopic.php?t=13362)
To really get the most from Debian you need to learn to use the APT package manager from the terminal.
Aptitude is now the recommended package manager for Debian:
[http://www.debian.org/releases/stable/i386/release-notes/ch-whats-new.en.html#s-pkgmgmt](http://www.debian.org/releases/stable/i386/release-notes/ch-whats-new.en.html#s-pkgmgmt)
To learn how to use aptitude from the terminal. Read the aptitude command line reference:
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/rn01re01.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/rn01re01.html)
You can use apt-get if you want. Just be consistent. Either stick with apt-get or stick with aptitude. Don't arbitrarily swith back and forth between apt-get and aptitde since they handle dependencies a bit differently. Here is the apt how to:
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)
Install Lenny from the Lenny beta 2 CD. The 1st disc is all you need to get started.
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)
 Or do a net install as others have mentioned.

---

### Post by basenvironment on 2008-11-06
> **tommcd said:**
> 
Aptitude is now the recommended package manager for Debian:

> aptitude is the **preferred program** for package management **from console**... **If you are still using dselect**, you should switch to aptitude as the official frontend for package management.

emphasis mine

---

### Post by OutOfReach on 2008-11-06
If you know how to install Ubuntu, you should be good with installing Debian.

---

### Post by notwen on 2008-11-06
> **tommcd said:**
> Here is a good tutorial for getting started with Debian:
[http://forums.debian.net/viewtopic.php?t=13362](http://forums.debian.net/viewtopic.php?t=13362)
To really get the most from Debian you need to learn to use the APT package manager from the terminal.
Aptitude is now the recommended package manager for Debian:
[http://www.debian.org/releases/stable/i386/release-notes/ch-whats-new.en.html#s-pkgmgmt](http://www.debian.org/releases/stable/i386/release-notes/ch-whats-new.en.html#s-pkgmgmt)
To learn how to use aptitude from the terminal. Read the aptitude command line reference:
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/rn01re01.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/rn01re01.html)
You can use apt-get if you want. Just be consistent. Either stick with apt-get or stick with aptitude. Don't arbitrarily swith back and forth between apt-get and aptitde since they handle dependencies a bit differently. Here is the apt how to:
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)
Install Lenny from the Lenny beta 2 CD. The 1st disc is all you need to get started.
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)
 Or do a net install as others have mentioned.

He pretty much summed up everything you need to know to get Debian up & running right there.  I also recommend Lenny if you're still wanting fairly recent app updates,etc.  Best of luck.  =]

---

### Post by markharding557 on 2008-11-06
> To really get the most from Debian you need to learn to use the APT package manager from the terminal.
Aptitude is now the recommended package manager for Debian:
I find synaptic works just as well on debian as it does with ubuntu but it is useful to use apt-get

---

### Post by Sorivenul on 2008-11-07
Debian, from my experience, is a very easy switch for an experienced Ubuntu user, though I was using Debian before I'd used Ubuntu.  I also suggest Lenny, which is already extremely stable and functional.

---

### Post by bartos on 2008-11-09
> **Sorivenul said:**
> Debian, from my experience, is a very easy switch for an experienced Ubuntu user, though I was using Debian before I'd used Ubuntu.  I also suggest Lenny, which is already extremely stable and functional.
 
Debian is easy. I like gui over cli and Lenny works for me. You will have to get programs with newer versions from sid or experimental ( Pidgin 2.5.1)
Easy as ubuntu pie.

---

### Post by Sorivenul on 2008-11-09
> **bartos said:**
> Debian is easy. I like gui over cli and Lenny works for me. 
I agree it is easy.  Though I prefer to use mainly the CLI on my Lenny.  As for the newer versions of programs, many find the tried and tested applications from the stable repository, or what will become stable in the case of Lenny, are fine.  I count myself among this group.

---

### Post by oOarthurOo on 2008-11-11
I use aptitude exclusively, but many are started to regret making it the "preferred method". Aptitude upgrade from etch to lenny is probably a big part of the reason it hasnt' released yet.

---

### Post by Zack McCool on 2008-11-11
> **markharding557 said:**
> 
the upside is you learn more and it is very stable and you don't have to install a new version every six months

There is nothing that says you have to install a new version of Ubuntu every 6 months.  Don't fix what isn't broken.

I have several systems in the house.  This one is running Hardy (actually Mint Elyssa these days, but same difference), the one next to it is running Feisty.  I probably will not install a newer version on either of them.  If I do, it will be way down the line...

---

### Post by tommcd on 2008-11-12
> **oOarthurOo said:**
> I use aptitude exclusively, but many are started to regret making it the "preferred method". Aptitude upgrade from etch to lenny is probably a big part of the reason it hasnt' released yet.

Can you explain why this is a problem? I read somewhere that upgrades from one Debian version to another (i.e., Etch to Lenny) are tested by the Debian devs with aptitude, not apt-get, so aptitude is preferred over apt-get for dist-upgrades. I've been using aptitude exclusively also. I have not had any problems with it so far. I installed from the Lenny beta 2 CD though. I did not do a dist-upgrade from Etch.

---

### Post by oOarthurOo on 2008-11-12
I'm subscribed to a couple of the mailing lists, and since this list is public I don't think it would be innapropriate to cut and paste a relevant message from the newsgroup. Bear in mind I have no special relationship to Debian, I just read this and similar posts in the last few weeks. Perhaps it's just a debian developer venting some frustration and nothing should be read into it at all. 

On another note though, I've had similar discussions on this forum with some Ubuntu devels and on Debian forums with knowledgeable users. The only thing that I can say after having read the manuals and talk to the players is that... it's confusing. :)

> On Wed, Nov 05, 2008 at 11:37:56PM +0100, Giovanni Rapagnani wrote:
> > On 05/11/08 15:08, Julien Cristau wrote:
>> >> Does apt-get dist-upgrade instead of aptitude work better?  X drivers
>> >> disappearing on upgrade is really not a viable option, for obvious
>> >> reasons.
> > Yes, same system, same etch installation, I had the system upgraded to 
> > lenny in 3 steps:
> >   aptitude install apt aptitude
> >   aptitude upgrade
> >   apt-get dist-upgrade

> > (there is no typing error above, 2 first with aptitude, 3rd with apt-get)

> > Before running 'apt-get dist-upgrade', I checked if 'aptitude 
> > dist-upgrade' would have removed the Xorg drivers and yes it would.

> > Some bug reports have already reported apt-get works better than 
> > aptitude. But it seems that it won't look serious to recommend the use of 
> > a different package management front-end for each release. And as 
> > aptitude was recommended in the 2 previous release, the ideas would be 
> > (see bug #489132) :
> >  - 1/ to stick at aptitude, find the possible issues and document these 
> > issues in the release notes;
> >  - 2/ improve aptitude.

The reasons for prefering aptitude over apt-get no longer apply, and
aptitude in etch and later is a *worse* tool than it was in earlier
releases, because the maintainer has made the upgrade algorithm overly
clever to the point where it will now propose upgrade solutions that
directly conflict with what has been specified on the command line.

We should cut our losses and recommend apt-get again for upgrades from etch,
as apt is being maintained in a fashion much more appropriate for a core
piece of Debian infrastructure.

-- Steve Langasek Give me a lever long enough and a Free OS Debian Developer to set it on, and I can move the world. Ubuntu Developer [http://www.debian.org/](http://www.debian.org/) [email]slangasek@ubuntu.com[/email] [email]vorlon@debian.org[/email]
-- To UNSUBSCRIBE, email to [email]debian-testing-REQUEST@lists.debian.org[/email] with a subject of "unsubscribe". Trouble? Contact [email]listmaster@lists.debian.org[/email]

---

### Post by tommcd on 2008-11-13
> **oOarthurOo said:**
> 
 The only thing that I can say after having read the manuals and talk to the players is that... it's confusing. :)
That is exactly how I feel after having read many threads on the Debian forums about aptitude vs apt-get.
I just subscribed to a few mailing lists myself so I can stay informed on these issues.

---

### Post by mikjp on 2008-11-13
> **chrispche said:**
> Compared to a fairly experienced Ubuntu user. If I was to make a switch, how would I find it. There are 3 DVD images to download. Is this the best way to go?

If you have a broadband connection, just download the first CD.

---

### Post by factotum218 on 2008-11-16
> **chrispche said:**
> Compared to a fairly experienced Ubuntu user. If I was to make a switch, how would I find it. There are 3 DVD images to download. Is this the best way to go?

Very easy, my eleven year old daughter admins her own sid desktop system.

---

### Post by maybeway36 on 2008-11-16
The best idea is probably to download the netinst CD image, and it will grab additional components from the Debian mirrors for you.

---

