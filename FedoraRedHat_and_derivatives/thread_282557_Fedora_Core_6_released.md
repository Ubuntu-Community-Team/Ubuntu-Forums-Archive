---
title: "Fedora Core 6 released"
date: 2006-10-22
forum: Fedora/RedHat and derivatives
---

### Post by plb on 2006-10-22
2 days early...

[http://osnews.com/story.php/16256/Fedora-Core-6-Released-to-Mirrors](http://osnews.com/story.php/16256/Fedora-Core-6-Released-to-Mirrors)

---

### Post by teet on 2006-10-22
I might have to give fedora a try again one of these days.  I still have fond memories of my first linux experience with redhat 9...it seems like such a long time ago, although it's only been like 3 years in reality.

I wish they made a 1 CD gnome-only install though.

-teet

---

### Post by LMP900 on 2006-10-22
I'm going to try FC6 as well. When I had FC5 installed, it was probably my most trouble-free Linux experience. I'll admit, it wasn't as pretty as Dapper (yes, I prefered the brown and orange, as well as the icons), but it is my favorite OS to date.

For me, last round (Dapper vs. FC5) went to Fedora. I'll see who wins it for me this round. It might be a closer match this time, since Edgy is looking good, stability and speed-wise.

---

### Post by chaosgeisterchen on 2006-10-23
The match between the two of them seems to be promising and darn close. I will also have a look into Fedora Core just to have it tested. Maybe it does things better than Kubuntu, yesterday I read that Fedora supports some mechanism making it faster than in Kubuntu, although SuSE supports this mechanism too, I do not like the style of SuSE being all too bloated and unstable. I hope Fedora does besser concerning all this.

---

### Post by slimdog360 on 2006-10-23
I couldnt stand FC5 so I couldnt see me trying this one out.

---

### Post by chaosgeisterchen on 2006-10-23
> **slimdog360 said:**
> I couldnt stand FC5 so I couldnt see me trying this one out.

If I may ask: What was your problem concerning FC5? What made it that bad for you? Things I've heard about FC6 so far really makes it good enough to be considered.

---

### Post by coffeecat on 2006-10-23
There's been some chat on [http://fedoraforum.org/forum/](http://fedoraforum.org/forum/) for the last few days. Some people have managed to download ISOs which they thought were the release version but these turned out to be Test3. Others have allegedly obtained the release version and have started torrents.

I've checked the UK mirrors and some European ones. There are quite a few with no /6 directory yet, and those with a /6 directory give you a permission denied error when you try to open it.

I think I'll wait until tomorrow. Or later if the servers buckle. ;)

---

### Post by SpEcIeS on 2006-10-23
Out tomorrow, and I am also considering giving it a try. Being that my first linux distro was Red Hat 6 it tempts me.

Have a spare 20GB Maxtor drive to install on because I really do not want to tamper with my Edgy install.

---

### Post by po0f on 2006-10-23
I am also eagerly awaiting FC6's release (only hours away now!).

---

### Post by chaosgeisterchen on 2006-10-24
Yay... maybe I'll spend the days before Edgy with testing FC6 ^^

---

### Post by ComplexNumber on 2006-10-24
i'm going to be updating soon, i think. i'm still waiting for fedora-release rpm to be available [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/3416249/com/fedora-release-6-4.noarch.rpm.html"). i've already got livna-release rpm. once i've got both, i'll just install them. this will update my repos so that it points to FC6 instead of FC5. then its just a case of 'sudo yum update'.

---

### Post by jdong on 2006-10-24
I really don't feel it being much faster.... DT_GNU_HASH's improvements seem to be marrred by the increased size of binaries and thus the increased IO load.


Fedora is quite great though, the major differences from Ubuntu would be:

(1) No non-free modules in default system. If you have any hardware that needs these, it's a bit more work to set them up and re-set them up after every kernel update.

(2) Multimedia. You'll be consulting 3rd party repositories for those...

(3) Very frequent updates: There will be lots of updates to Fedora, and if you don't have a broadband connection and some level of patience, you'll be whining a lot....

(4) Yum is not as fast as APT. Though it's certainly better than before, YUM ain't the fastest thing around.

---

### Post by SpEcIeS on 2006-10-24
Some good points to take into consideration. Does the **DT_GNU_HASH** change make any improvements at all?

---

### Post by jdong on 2006-10-24
I touched on that in my post. From the benchmarking in the Gentoo world and verified by my  non-scientific experience with FC6, I don't think DT_GNU_HASH is making any significant change in performance.... While it clearly shows improved linker speed in benchmarks, the hash adds about 1-2MB to binaries that really benefit from the enhancement... which will increase HD activity, decrease cache hits, and thus neutralize benefits.... Tasks like opening up Openoffice take roughly the same amount of time in Ubuntu Edgy as in FC6 (even though OOo startup is heavily linker-bound)

FC6 does feel faster than FC5, and even somewhat snappier than Dapper, but this is more due to general improvements in GCC, GNOME, etc that were made since FC5/Dapper release time. Edgy is also snappier than FC5/Dapper for the same reason.

---

### Post by ComplexNumber on 2006-10-24
**jdong**
have you now got FC6 on your system?
also, have you seen the new icons destined for FC7? they look quite nice. i have produced a screenshot of the icons in another thread in the fedora forum here.

>  it's a bit more work to set them up and re-set them up after every kernel update.
i'm not too sure what this "setting up" that you're referring to. i just install by using either sudo yum update or install them via Smart.


>  (2) Multimedia. You'll be consulting 3rd party repositories for those...are you aware that you should only EITHER have livna or rpmforge(eg atrpms, freshrpms, dries, etc) on your system? they are incompatible. hoever, fedora recommends livna. so if you're going to be using livna, update your repos with [this]("http://rpm.pbone.net/index.php3/stat/4/idpl/3377301/com/livna-release-6-1.noarch.rpm.html") (i'm assuming that you are using x86 architecture). if you are going to be using RPMfiorge branch of repos, use [this]("http://rpm.pbone.net/index.php3/stat/4/idpl/3243987/com/freshrpms-release-1.1-1.fc.noarch.rpm.html"). 
> 

(4) Yum is not as fast as APT. Though it's certainly better than before, YUM ain't the fastest thing around.i find it to be quite fast. i updated(download & installed) about 544 packages in about 3/4 hour yesterday. also, are you aware that you can add various modules into yum such as yum-fastestmirror etc?

---

### Post by jdong on 2006-10-24
> **ComplexNumber said:**
> **jdong**
have you now got FC6 on your system?
also, have you seen the new icons destined for FC7? they look quite nice. i have produced a screenshot of the icons in another thread in the fedora forum here.

I've been keeping a FC6 preview install updated for this time... I will do a fresh FC6 final install when I get the chance...

> 
are you aware that you should only EITHER have livna or rpmforge(eg atrpms, freshrpms, dries, etc) on your system? they are incompatible. hoever, fedora recommends livna. so if you're going to be using livna, update your repos with [this]("http://rpm.pbone.net/index.php3/stat/4/idpl/3377301/com/livna-release-6-1.noarch.rpm.html") (i'm assuming that you are using x86 architecture). if you are going to be using RPMfiorge branch of repos, use [this]("http://rpm.pbone.net/index.php3/stat/4/idpl/3243987/com/freshrpms-release-1.1-1.fc.noarch.rpm.html").

Yes, I'm aware of that.... None of the compatible combinations results in as good a coverage of free or non-free software as Ubuntu's universe or Debian sid, though the coverage is good enough for most purposes, and RPMs are probably the most common 3rd party package format you'll find.

>  
i find it to be quite fast. i updated(download & installed) about 544 packages in about 3/4 hour yesterday. also, are you aware that you can add various modules into yum such as yum-fastestmirror etc?
I was going with a default yum install from FC6 preview.... the first update was around 100 packages and took nearly 3 hours to do on a 5000kbit internet connection.... I had not customized yum in any way, so it could've been hanging on a slow mirror, but from me watching it, I could tell that majority of the time it spent downloading hundreds of individual rpm headers, and all those http requests really add up in terms of latency, similar to the reason why bzr is so slow to branch over the network.

---

### Post by chaosgeisterchen on 2006-10-24
@jdong: Does not sound too good. I hoped that the DT_GNU_HASH would improve things significantly, but this technique has to improved quite a lot until it will be really able to let the desktop be racing - firstly they have to decrease the level of growth which the binaries experience while using it. But it is easy to write that here and complex to program it.

FC6 will be probably in my hands tomorrow. I have a 17 GIG spare partition where I will install it onto - I am quite curious about how it will perform. But I do not think that I will be satisfied with it. I neither have fast broadband nor I got any flatrate, so I will stick with Ubuntu which has way less updates I hope. Another point off for FC6 could be the size of the installation image. Whereas Ubuntu needs not more than 700 MB, FC6 has to be downloaded either as 5 CD images or as 3.3 GB DVD-image. 

What on earth do they put on this CD's/ this DVD? Apart from XEN, SELinux and 2 desktop environments.

---

### Post by jdong on 2006-10-24
The Fedora installation media contain all packages in Fedora repositories (i.e. all the non-Extras)... that's roughly equivalent to Ubuntu making a DVD with the entire main and restricted repository contents included... which would be huge, too.

---

### Post by ComplexNumber on 2006-10-24
> the first update was around 100 packages and took nearly 3 hours to do on a 5000kbit internet connection
hmmm i think my internet connection is quite a bit faster than yours.

---

### Post by jdong on 2006-10-24
It might be... the process was largely network bound, downloading hundreds of those 1KB RPM headers are around 1 every 3 seconds. Most of the time was connect() latency rather than actual data transfer... though I blame it more on the servers I was connecting with taking a while to respond.

---

### Post by chaosgeisterchen on 2006-10-24
Thanks for answering. I would never ever need all that will be offered by Fedora Core. So it will be the cleaner solution to continue using Kubuntu, which I am rather satisfied with at the moment.

But one question on decision is still open:

Having no flatrate and a limited traffic volume (5120 MB / month) is it the better solution to use Fedora Core or Ubuntu?

---

### Post by jdong on 2006-10-24
You're gonna get much less update volume with Ubuntu... Fedora is quite prolific with updates.

I'd personally recommend KUbuntu over Fedora's KDE, but that's just me...

---

### Post by ComplexNumber on 2006-10-24
>  I'd personally recommend KUbuntu over Fedora's KDE, but that's just me...
fedora's kde is quite crippled. i installed it the other week. it has lots of packages missing from the repos and the packages aren't split.

---

### Post by SpEcIeS on 2006-10-24
I am not surprised. Is not Fedora, like Red Hat, more geared towards Gnome? Mandriva, or in the past Mandrake, was Red Hat's equal, but with KDE as the prime GUI.

---

### Post by ComplexNumber on 2006-10-24
> **SpEcIeS said:**
> I am not surprised. Is not Fedora, like Red Hat, more geared towards Gnome? Mandriva, or in the past Mandrake, was Red Hat's equal, but with KDE as the prime GUI.
thats true. kde is nothing more than a token gesture for those in the fedora community who like kde.

---

### Post by raublekick on 2006-10-24
downloading the ISOs right now, gonna install it along side edgy, but only to test it out. can't say how good Ubuntu is unless you know how good the competition is :)

---

### Post by chaosgeisterchen on 2006-10-24
Well, I'll stick to Kubuntu then. Thanks for the answers.

---

### Post by SpEcIeS on 2006-10-24
> **raublekick said:**
> ... can't say how good Ubuntu is unless you know how good the competition is :)
This is very true.

---

### Post by jdong on 2006-10-24
> **raublekick said:**
> can't say how good Ubuntu is unless you know how good the competition is :)


+1, well said. That's what I have to say about Ubuntu, too... I didn't realize how much work I had to put into setting up and maintaining my other distro setups (I have fairly permanent SUSE, FreeBSD, Gentoo, Fedora, and Debian testing boxes to some degree, and test other distros here and there too, though those will come and go) until Ubuntu came along and spoiled me.

---

### Post by weapon-x on 2006-10-25
hi friends the new FC6 has been released Its has many latest features the look is gr8.I dont knoe abt the performance bez i have install it yet.Please donmt think that i m campearing it with any other destro.[-( 

Want to Read more click: [here]("http://www.flynix.profusehost.net/viewtopic.php?t=43")

---

### Post by frodon on 2006-10-25
weapon-x, i merged your thread with an existing one on the same topic.

---

