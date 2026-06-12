---
title: "Kubuntu = Ubuntu + KDE only?"
date: 2005-06-21
forum: Desktop Environments
---

### Post by Raccroc on 2005-06-21
I haven't given Ubuntu much more than a passing glance since I am not a fan of Gnome (at least since they butchered it when going to 2.x).  I recently discovered Kubuntu and thought I'd give it a go since Ubuntu has been getting such rave reviews.

After installing it and playing around for awhile, I can honestly say it looks good and deserves further inspection (as a side note, I thought having awk as the shell during the install was a bit odd).  That is untill I setup agt-get and when l went to install Gaim and Firefox.  

From the looks of it, Kubuntu is nothing more than Ubuntu with KDE setup instead of it's own seperate distrobution.  This means it's using the standard Ubuntu repositories and software like Firefox, Bluez, and Gaim are complied against gtk instead of qt.

Can this be confirmed, or am I missing someing?
Considering that I am correct, is there any movement to actually spin Kubuntu off as it's own with all packages (wm specific anyway) being recompiled?

[edit] Ok, so I am a dumbass who should have RTFM.  Just read the Kubuntu FAQ ([http://www.kubuntu.org](http://www.kubuntu.org)) and apparently I am correct.  That is a disappointment because I can see I will be running into the same issue I run into with the Redhat based distros.  Well, my search continues for a likable KDE centric Linux (which is not source based).

---

### Post by clb137 on 2005-06-21
[QUOTE=Raccroc]I haven't given Ubuntu much more than a passing glance since I am not a fan of Gnome (at least since they butchered it when going to 2.x).  I recently discovered Kubuntu and thought I'd give it a go since Ubuntu has been getting such rave reviews.

After installing it and playing around for awhile, I can honestly say it looks good and deserves further inspection (as a side note, I thought having awk as the shell during the install was a bit odd).  That is untill I setup agt-get and when l went to install Gaim and Firefox.  

From the looks of it, Kubuntu is nothing more than Ubuntu with KDE setup instead of it's own seperate distrobution.  This means it's using the standard Ubuntu repositories and software like Firefox, Bluez, and Gaim are complied against gtk instead of qt.

Can this be confirmed, or am I missing someing?
Considering that I am correct, is there any movement to actually spin Kubuntu off as it's own with all packages (wm specific anyway) being recompiled?

[edit] Ok, so I am a dumbass who should have RTFM.  Just read the Kubuntu FAQ ([http://www.kubuntu.org](http://www.kubuntu.org)) and apparently I am correct.  That is a disappointment because I can see I will be running into the same issue I run into with the Redhat based distros.  Well, my search continues for a likable KDE centric Linux (which is not source based).[/QUOTE]


Why should it spin off????  Have you installed Ubuntu on its own????  that way you can make comments on if it is just KDE added.

---

### Post by Raccroc on 2005-06-21
I don't really understand your question/comment.  Why would I install Ubuntu?  I know it's a Gnome centric distro.  This is about Kubuntu and wether or not it is Ubuntu + Kde but still Gnome centric (from a compiled package standpoint) or an actual KDE centric distro.

Turns out it is Ubuntu + KDE.  Here is what I found in the FAQ:
> What is Kubuntu?
Kubuntu is the first Ubuntu derived distribution. Our Kubuntu CDs are made up of Ubuntu's base plus KDE. You can get exactly the same effect by installing Ubuntu and adding the KDE packages (and removing the Gnome packages) from the Ubuntu archives.
Is this a fork of Ubuntu?
No, it is an official part of Ubuntu. All our packages are in the same archives.
As far as WHY it should spin off?  I didn't say it should.  I simply wanted to know IF it DID spin off because that is what I am looking for.  I would prefer a KDE centric distro because I don't what a bunch of gtk and gnome libs that I don't really need for things like Firefox or Bluez-utils.

---

### Post by Pcghost on 2005-06-21
I am running Kubuntu and honestly I don't get canonicals decision here.  A LOT of Linux users prefer KDE, so on that Ubuntu is alienating over half the market.  Not to mention that they decided to support Gnome, A Novell product. Where is the sense in that? I'm not saying they shouldn't include Gnome, only that they should include both and Kubuntu should simply be Ubuntu, with the display manager decision left to the users.  

But (K)ubuntu is working fairly well for me so I guess it doesn't matter too much really. \\:D/

---

### Post by SGC on 2005-06-21
[QUOTE=Pcghost]Not to mention that they decided to support Gnome, A Novell product[/QUOTE]
Since when Gnome becomes a novell product ?!

I don't like gnome , but it seems that many linux users prefering it.

---

### Post by manicka on 2005-06-21
[QUOTE=Pcghost]I am running Kubuntu and honestly I don't get canonicals decision here.  A LOT of Linux users prefer KDE, so on that Ubuntu is alienating over half the market.  Not to mention that they decided to support Gnome, A Novell product. Where is the sense in that? I'm not saying they shouldn't include Gnome, only that they should include both and Kubuntu should simply be Ubuntu, with the display manager decision left to the users.  

But (K)ubuntu is working fairly well for me so I guess it doesn't matter too much really. \\:D/[/QUOTE]
 This post needs clarification. 

Gnome is not a Novell Product

---

### Post by Eddy DaKillaBee on 2005-06-21
Just like everyone else has said, Gnome is **not** a Novell product. ^_^ While I can understand the Raccroc's view, I don't think he's quite getting something right here.

First of all, think about this: if Ubuntu had both Gnome and KDE packages all rolled up into one distro (on CD/DVD now), you'd have to download more CDs to get the installation going. This means that if I want KDE as my window manager I'm stuck getting lots of packages for GTK and Gnome on CD even though I may never need them. Same thing goes for the other way around (and so far I still like Gnome over KDE, but it's all a matter of personal preference!).

By making Ubuntu and Kubuntu (therefore kinda splitting up the distros but not, seeing that they share the same repositories and such), I can choose to get Kubuntu if I want KDE, and I don't need to download all this other GTK and Gnome stuff.

Second, there shouldn't be an issue with both distros using the same repository. I have Ubuntu installed on my laptop and Kubuntu installed on my desktop machine, and as far as I can tell, this comment:> From the looks of it, Kubuntu is nothing more than Ubuntu with KDE setup instead of it's own seperate distrobution. This means it's using the standard Ubuntu repositories and software like Firefox, Bluez, and Gaim are complied against gtk instead of qt.is dead wrong.

There is no QT version of Gaim or Firefox: they use GTK2!! If you want something compiled against QT, you may want to consider Kopete or Konqueror, which are both great programs in their own right.

Third, since both distros use the same repository, this means that my version of K3B in Ubuntu is the same as Kubuntu, and that there shouldn't be any problems. And yes, while I said earlier that I do like Gnome over KDE, K3B beats anything else that's out there hands-down. :grin: 

But yeah, Raccroc, just give it a try and stick with it. I've been happy since the switch, and I really don't think you'd have Redhat/Fedora-type issues here. :D

---

### Post by Raccroc on 2005-06-21
Good things :)

> While I can understand the Raccroc's view, I don't think he's quite getting something right here. 
I've run into three methods of of handling an alternate wm where the distro is based around a different one.:
1.  Redhat Style:  Redhat is a Gnome based distro, but during the install (custom?), you can de-select Gnome and add KDE.
2.  [Don't rememeber which distro did this] Style:  I ran accross a distro that by default installed Gnome (and was Gnome based); however, during the initial boot screen (where you enter 'linux', 'expert', 'live', etc) you could enter 'linux kde' and it would install KDE instead of Gnome. 
3.  Kubuntu Style:  Spin a different CD and install from there.

Prior to Kubuntu, I've never run across this method.  So when I saw Ubuntu has a spin-off called Kubuntu, I assumed (insert ass-u-me joke here) the reason they spun a whole new CD was because they were going to make it KDE based.  Otherwise, I'm not sure why you woundn't just use one of the first two methods (by adding a "KDE Support" CD which would be required only if choosing KDE during the install).
> Second, there shouldn't be an issue with both distros using the same repository.
But that doesn't really make it a different distro (which is what I originally THOUGHT Kubuntu is), rather it's the same distro with an alternate install.
> is dead wrong
You are right.  Both GAIM and Firefox do require GTK2.  My bad, I did misspeak about that.  What they DO NOT both require (in the wild) is all the Gnome Libraries that a Gnome based distro requires them to have.  For example, there is no reason in the world to need gconf2 on my KDE system, but that is a package apt-get wants to pull for Firefox.  From my experience, using packages compiled based on Gnome for KDE tends to create annoyances.  Usually they are small things like missing/incorrect menu entires (getting MUCH better since KDE and Gnome have started unifiying standards) or bad default fonts (search the forum for Firefox Fonts and you will see what I mean...easy fix, just something you shouldn't need to do).
> Ubuntu is alienating over half the market
I don't know that "alienating" is the right word.  Granted, if I found a distro that offered me all the same things as this one, but was KDE based, I would probably walk away from this one.  But that doesn't mean I'm alienated.  Just not quite as good as I had originally hoped is closer to it.  An example would be I hate the way Firefox handles bookmarks (single file), but I still use it over IE in Windows.  Pro's WAY WAY out weight the cons.  So it's a small annoyance I live with.

Which brings me to the fact that I am not saying this is a "take my ball and go home" type issue.  With every distro I ever tried, there are things I like and things I don't.  When the likes begain to outweight the dislikes, it's time to start looking around.  This is a single, small dislike.  Otherwise, it's got a lot going for it and is getting rave reviews from a lot of sources.  I will give it an honest try for awhile before I decide if I want to walk away.

As an aside:  Ditto on the Gnome not being Novell's.  If I were to even suggest something along those lines, it would be that Gnome is becoming Redhat's bitch :grin:  [NOTE: This is really just a joke from around the office  which comes from the fact that they both tend to have the "corporate desktop" mentality where they want to hide/remove/obscure much of the configuration options and create a Blue Curve type "one look, one feel" "That Just Works(tm)".  This is absolutely great in the corp. environment when you have to support everyone's systems, it's just not what I want as a home and power user.]

---

### Post by dresnu on 2005-06-21
You can check out Xandros for a Kde-based distro. And I also think mepis and knoppix use kde by default as well, at least it was that way in the live cds I tried.

---

### Post by shakin on 2005-06-21
If there were a backports-style repository for apps that are compiled for qt instead of gtk (where that is an option), that would be brilliant and it would probably solve 90% of the problems brought up in this thread. It could even have an experimental build of firefox with qt support :)

The issue of whether or not the base distro is gnome-centric or not is a moot point for a debian-based distro. The system is what the repositories are. Yes, the main repositories are all gnome-centric, but a single superhero for the kubuntu community could run a repository and fix all that.

What apps would be included in a kubuntu repository? I don't really know which gtk apps I run now have a qt compile option. The repository could also have a lot of stuff from kde-apps.org in universe.

---

### Post by cowlip on 2005-06-22
I think a good way to use gtk apps in KDE is to install gtk-qt theme engine.  Gnome apps are identical looking, then.

---

### Post by Pcghost on 2005-06-22
Sorry. Was I wrong in saying that Gnome is actually Ximian Gnome?? Ximian was bought by Novell last year, hense the reason I say Gnome is a Novell product. I very well could be wrong.

Edit: Here is the Register story about the purchase

[http://www.theregister.co.uk/2003/08/04/novell_buys_ximian/](http://www.theregister.co.uk/2003/08/04/novell_buys_ximian/)

But as it appears from the Gnome project homepage, Ximian is simply a Contributor and has a seat on the advisory board. A foundation seems to actually control it.  I stand corrected. Sorry to any Gnome zealots I may have offended. :-#

---

### Post by tristian on 2005-06-22
Gnome is mainly developed by Redhat. Redhat even host the Gnome website.

Gnome runs on the GTK+ engain which has been used by a few Window Managers.

---

### Post by elsewhere on 2005-06-22
There are plans at the moment to develop a "kfirefox" port of firefox once QT 4.0 is out, though it won't be officially Mozilla sanctioned.

The decision to go GTK vs. QT is pretty much up the the developers and they generally have their reasons for going one way or another.  I won't go any further because such things generally end in KDE vs Gnome flamewars, but the beautiful thing about it is the choice the developers have.  I don't think it's a small thing to port from one environment to the other and frankly, there really isn't much gain in doing so since the applications tend to work transparently well in the desktop of choice (UI issues aside). Ports like that are usually done just for the sake of doing so (such as the kfirefox port will be if it actually happens), rather than an actual gain.

As for having to install Gnome along with Firefox, well Firefox is part of Ubuntu, not Kubuntu, and that's the way the depencies were originally set.  Kubuntu intentionally excluded GTK apps in most cases, opting for pure KDE/QT ones instead, Konqueror instead of Firefox, KMail instead of Evolution or Thunderbird, etc.  (even when they lack functionality compared to GTK equivalents, such as Kynaptic vs. Synaptic).  The control file in the .deb files could probably be tweaked to remove the gnome dependencies that may not be true dependencies, but that would be time consuming to do across the repositories and would become far more cumbersome to support.  The alternative would be for Kubuntu to create their own repositories, but I think there's only so far you can reasonbly expect corporate sponsorship of a truly free distribution to have to go, particularly considering how much has been invested in K/Ubuntu already.

Also, apps like Mozilla can also be installed directly from the vendor for a "cleaner" install without the need for gnome addons, but then you lose package management and some of the distro-specific integrations.  So it's a trade-off.

I do think that even though it has it's roots in a gnome-based distro, Kubuntu is probably one of the better implemented KDE distros.  It was the first one to use KDE 3.4, 3.4.1 was made available as a port immediately at release, and even KOffice 1.4 was made available as of release yesterday.  Some KDE distros are still using 3.2.x or 3.3.x (although probably with a degree more stability).

Just throwing in my $0.02...!

Cheers,
KV

---

### Post by Segovia on 2005-06-23
If you are not happy with Kubuntu, perhaps try Kanotix.  In my opinion, it's the best KDE/Debian distro.  Hopefully, the next version of Kubuntu (Breezy Badger), will change my mind on that.

For now I prefer to stick with Ubuntu (GNOME).  With all things considered for *my* needs, it's the best distro available, even though I generally prefer KDE.

---

### Post by Zeddicus on 2005-06-23
[QUOTE=shakin]I don't really know which gtk apps I run now have a qt compile option.[/QUOTE]

Honestly?  *VERY* few.  Few enough that it really isn't worth the effort.  In ~2 years (and a *lot* of apps) with Gentoo, I can only recall one significant app that had exclusive "qt" and "gtk" compile options -- Celestia.  And, well... a quick apt-cache search reveals:

celestia - A real-time visual space simulation (KDE frontend)
celestia-glut - A real-time visual space simulation (GLUT frontend)
celestia-gnome - A real-time visual space simulation (Gnome  frontend)

In other words -- if both versions are useful, chances are they'll both be in the repos anyway. :)

As for firefox, well... if the Gnome deps are that big a deal (personally, I don't care -- there's always the occasional Gnome app I'll want to try, but I know others might), the binary installer from mozilla.org is very usable, last I checked.  (I know, not ideal, but not *that* big an issue, imho)

(and hey -- isn't Konq getting an optional Gecko renderer soon anyway?! :))

---

### Post by fdoving on 2005-06-24
The whole idea (as I see it) about kubuntu (and ubuntu) is to provide both desktop environments but let the user choose before downloading the cd image.

Everything you need to get a working desktop with an office suite is included on that one cd. If KDE and Gnome were both included the distribution would be 2 cds anyway. I think separating them into two iso images is a good idea. This way both KDE users and Gnome users get a one-cd-installation.
Lots of users download cd images and burn them at home. Some places bandwith costs alot. 
I doubt users would like to be forced to download first cd1 with the base system and Gnome, and them cd2 with KDE and addons, just to get my system installed with KDE. 


- Frode

---

### Post by manicka on 2005-06-24
[QUOTE=fdoving]The whole idea (as I see it) about kubuntu (and ubuntu) is to provide both desktop environments but let the user choose before downloading the cd image.

Everything you need to get a working desktop with an office suite is included on that one cd. If KDE and Gnome were both included the distribution would be 2 cds anyway. I think separating them into two iso images is a good idea. This way both KDE users and Gnome users get a one-cd-installation.
Lots of users download cd images and burn them at home. Some places bandwith costs alot. 
I doubt users would like to be forced to download first cd1 with the base system and Gnome, and them cd2 with KDE and addons, just to get my system installed with KDE. 


- Frode[/QUOTE]
 Nicely summed up and this is why ubuntu is so popular

---

