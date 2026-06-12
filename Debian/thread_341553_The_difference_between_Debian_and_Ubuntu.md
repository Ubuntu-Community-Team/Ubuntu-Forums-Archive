---
title: "The difference between Debian and Ubuntu?"
date: 2007-01-18
forum: Debian
---

### Post by Kernel Sanders on 2007-01-18
Can someone help explain this to me please? Because, from where i'm sitting, they both look remarkably similar :-k (although, I am a total n00b when it comes to such things :oops: )

---

### Post by whistlerspa on 2007-01-18
Ubuntu is based on Debian, as far as I'm aware and hence the similarity

---

### Post by IYY on 2007-01-18
> they both look remarkably similar

What you are seeing is the desktop environment; Gnome, KDE or XFCE. It would look the same on Ubuntu, Debian, Suse, Slackware... Even FreeBSD or Solaris.

---

### Post by Phatfiddler on 2007-01-18
I use(d) both Debian Stable/Testing/Unstable and Ubuntu/Xubuntu/Kubuntu, and there are similarities.  Ubuntu is in fact based off of Debian, but generally uses packages and software specific to *buntu which do not work well with Debian.  General rule of thumb is - *buntu will run Debian, but Debian doesn't run *buntu.  When switching to Debian, it is in your best interest to start with a clean slate, and then build your software from there.  If you try to keep your existing programs, alot of times they will not work, since the Debian repositories are different.

Alot of Debian developers and users do not like Ubuntu since they feel that it leeches off of their hard work, without giving anything back.  This is because alot of Debian packages are modified to work specifically with *buntu, and are updated only for *buntu, therefore forcing Debian users to either use the older version, or modify the original program on their own.

Debian Sarge(stable) is solid as a rock, but only because it uses tried and true software.  Because of this, it uses older versions and an older repository, not to mention older versions of KDE and Gnome.  If you want a rock-solid, up-to date Linux distro, I recommend using Debian Etch(testing).

Also, Debian does not come initially with any non-free packages.  It is easy to get these by simply adjusting your sources, but if you are going to go through the troubles of adding every single codec, driver, and application that is non-free, your best bet is to just use *buntu.  gNewSense is the equivalent of the Debian in the idea that it is completely open-source and free.

Debian also does not offer a Live CD.  You have to install the distro before you can try it out.  Despite this, there are more ways to get Debian and install it than for *buntu.  You can download the entire disk set, which is something like 20 ISO cds, get a Net Install which is 180MB and installs your software of choice via the internet, use the Business Card cd which is around 60MB, and installs a very basic Debian so that you may install the rest via internet, and you may purchase a CD or DVD set through a local vendor.

---

### Post by rabid emu on 2007-01-18
I tried Debian briefly before deleting it and switching for something else.  The way I saw it, it was basically Ubuntu except it didn't come with any drivers or anything pre-installed (yeah I know ubuntu is based on debian).  I don't see any logical reason to choose Debian over Ubuntu, since Ubuntu comes with drivers already installed whereas Debian doesn't (and it's tough in Debian to get things working).  The best part of Ubuntu is that it comes working well out of the box, and it was the only linux distro I've ever used that had support for my wireless card.  After using Ubuntu, Debian seems like a downgrade.  Now of course that's just my opinion after a few minutes of using Debian Etch; X didn't even work out of the fresh install, and after getting a Gui finally up and running I thought "what does this have that Ubuntu doesn't?  And Ubuntu has so much more."  So I got rid of Debian.  In my opinion, the difference is the installation of drivers, and the ease of use of setting Debian up is much harder than Ubuntu.  Some Linux people seem to think harder = better for some reason, I don't know why.

---

### Post by RAV TUX on 2007-01-18
*moving to debian forum*

---

### Post by grte on 2007-01-18
> **rabid emu said:**
>  Some Linux people seem to think harder = better for some reason, I don't know why.

It's not that.  It's that more configurable = better.  But often, there's a causal relationship between configurability and difficulty.

---

### Post by Kindred on 2007-01-19
Well, Debian is built for many more architectures, has multiple release methods (stable, testing, unstable, experimental), much more supported software & has none of the limiting desktop metapackages.  I also find it to be more stable and certainly faster.  Also, much less chance of them incorporating more proprietary junk in future.

---

### Post by xabbott on 2007-01-21
> **Kindred said:**
> Well, Debian is built for many more architectures, has multiple release methods (stable, testing, unstable, experimental), much more supported software & has none of the limiting desktop metapackages.

Debian does have meta packages. Just like Debian's meta packages though they don't really limit you. I do believe Debian has more packages but you will generally find new desktop software releasing Ubuntu debs, not debian. :( 

  > I also find it to be more stable and certainly faster.  Also, much less chance of them incorporating more proprietary junk in future.
You could use Debian stable, which I agree is very stable. But you'd be using very old packages. OR use more up to date packages via etch/testing and sid. I consider the latter on par with Dapper and Edgy. As for speed...Edgy boots faster. I generally find the speed comes down to what you install though. You can make them both slim and speedy. 

If you are a general desktop user I feel Ubuntu is probably a better choice at the moment. The community, the faster release cycle, etc. If you have other needs or you're a power user then it really doesn't matter. You can make Ubuntu like Debian or vice versa. 

I'm a former Debian user. I currently use Arch but I do have Ubuntu installed on some of my family's computers.

---

### Post by cunawarit on 2007-01-21
> **xabbott said:**
> You could use Debian stable, which I agree is very stable. But you'd be using very old packages. OR use more up to date packages via etch/testing and sid.

There's another option, you can use Debian stable if you don't require all your software to be the latest. And for those ones that you do require the latest you can use repositories of backported packages, like backports.org and apt-get.org... IF you REALLY require them that is. 

I do agree, it would be nice if Debian moved faster... However, its stability does come from the thoroughness that they apply to the testing process, and that takes time. 

I love Debian!

---

### Post by ushaba on 2007-01-21
i'm kind of curious if there are any differences "under the hood“ as it were. as in, are files kept in dramatically different places in debian? this is something i never seem to be discussed.there's a lot on the leeching process, and the ease of use, but as far as actual differences in system organization, is there much?

---

### Post by AgenT on 2007-01-21
It was best put by the author of Debian System, Martin Krafft:
"Debian may not be the best choice for your first steps in the Linux world. If you are choosing Linux because you have had enough and want to author your documents, compose messages, and browse the Web on a [more] stable, secure, and free operating system from now on, then you may want to consider one of the Debian derivatives... They are frequently optimized for specific applications or target a specific user base, which makes them simpler to learn... These distributions do not handle the broad set of applications that Debian supports and can thus do with less flexibility (and complexity). Once you have learnt to walk with one of these, you can always come back to Debian..."
(page 22, 1st Ed.)
Notice that Martin Krafft is a Debian user and developer. The quote above is from his book about Debian.

File placement is almost identical because 90% or so of the Ubuntu packages are just automatically repackaged Debian (mostly unstable) ones. "Under the hood" is a very blanket term and the answer to that is both yes and no. Then again, the differences in file placement is very minimal even between Debian and Red Hat. They are GNU/Linux afterall. Although Red Hat tends to break standards (or at least they did, not sure about Fedora).

There are differences, even some major ones. Basically, Ubuntu is very narrow in what it does and what it does well. It is also quite unstable when compared to Debian, and has 6 month release cycles. Ubuntu does not have different distrib types. It is either pre-release or released. Debian has stable -> testing -> unstable -> experimental and packages are always moving between the last 3 so you do not have the disadvantage of being stuck with a specific version for 6 months. But Debian stable "releases" are much more infrequent. Ubuntu also has less hardware support, much less in fact. Ubuntu supports 3 architectures, x86, PPC (Apple) and amd64 while Debian supports those 3 plus 8 more. A lot people do not even realize that there are more architectures. Debian and Debian development is more open than Ubuntu and Ubuntu development. This was a reason why one of the major Debian developers switched to Ubuntu. Debian also has a lot more developers than Ubuntu. 

Also, the communities are different. Ubuntu tends to have more Linux novices while Debian has more knowledgeable users. And the communities differ in how they communicate. Debian extensively uses mailing lists which has some major advantages to forums (forums are also available). This is why Ubuntu developers do not visit these forums (they also use mailing lists and other, non-forum types of communication). Documentation on Ubuntu is very low quality. Debian has some of the best. And the quality ones for Ubuntu are just copy/pasted from Debian's website with minor changes to reflect Ubuntu. Debian has whole manuals available online for many aspects of the system (Gentoo also has some very good documentation).

There is also a lot of negative and false sentimentality about Debian from Ubuntu users. Much more so than the other way around. Notice that I said users, not developers. Maybe it is because Ubuntu users are more novice and do not really have a grasp of what they are talking about or because they are ex-Windows users.

Read this post for an example (I also try to explain some of the differences between Ubuntu and Debian in one of the post there):
[http://www.ubuntuforums.org/showthread.php?t=337765](http://www.ubuntuforums.org/showthread.php?t=337765)

There are advantages and disadvantages to both distributions and asking on a Ubuntu forum is probably asking for a slanted answer to the question. Try doing some preliminary research. Read debian.org as they have a LOT of information. Debian users are more open as well. They tend not to care as much if you use Debian or not and are less afraid to tell people that some other distribution is better for a user.

---

### Post by ushaba on 2007-01-22
i've been considering installing debian on my laptop to play around, more as a learning process than anything else. i've got a desktop working perfectly well at the moment, and think that the only way i am going to really learn how everything works is if i am forced to. ie, it's much easier to learn about fdisk because you need to at that moment than because you need it SOMEDAY. the read the manual thing is very dependent on having two computers to work with, and now that i do, i think it may finally be time to play around with debian. i should point out that i'm also considering slackware :) so i'm actually seeking some hassles intentionally. i don't expect a user-friendly experience, but as long as i have ubuntu on my desktop to get work done, that's fine with me. between debian and slackware for finally getting used to vi like a well-worn pair of gloves, any recommendations?

---

### Post by stream303 on 2007-01-22
> **ushaba said:**
> between debian and slackware for finally getting used to vi like a well-worn pair of gloves, any recommendations?

What I'd do in your situation is to try doing a minimal install on your laptop with the text-based alternate-install iso.  You can stay with Ubuntu for that to make it easy to compare config files etc with your pristine desktop machine.

From there, you'll end up at the command line, and will find out how to install/configure X if you want a graphical component, specific laptop feature drivers etc.

Try to install, run, and understand the minimal amount of things you need to get to what you feel is a comfortable level of practicality for you.

For example, I run a minimal install on my G5 iMac using Fluxbox as a window-manager instead of the Gnome desktop environment just because I want to.  I don't have any file managers as I do that via the command line.  My only editors consist of vim and gvim (in X).  I installed powernowd to control my cpu's speed.  Instead of using a graphical app for viewing that, I just cat /proc/cpuinfo from the command line.  I tried to install things that weren't dependent upon Gnome or KDE.  You get the idea.

Bringing your system up from a very minimum like what is on the alternate-install cd could be a very good exercise.

You can easily do the same with debian, slackware, or nearly any other linux distro.  Don't forget to explore the BSD's either.  In fact I prefer debian for this task but it is largely a matter of personal preference, not which is better.

Good times lay ahead with the proper attitude, and it sounds like you have that.  Although I love vi, at first it gave me fits.  Just drop back to nano temporarily if you have to.  If you want to really devote yourself to vi, use 'view' as a text pager instead of 'less' or 'more' when you can.

Have fun!

---

### Post by AgenT on 2007-01-22
Get the book Debian System by Martin F. Krafft (a Debian developer), read parts that interest you, and start an install of Debian. You will learn a lot more with the book because it talks about a lot of Debian concepts and techniques and it is pretty easy to understand. It is one of the best books on computers that I have read. Read reviews by searching Amazon and Google and you shall see. And do not be troubled that it is a little outdated (it was concurrent with Sarge) because everything in it still applies. Here is the [official webpage]("http://debiansystem.info"). And there is no reason to wait for the book before doing install, just install the way mentioned below.

If you refuse to buy the book mentioned above, do a deboostrap Debian install via some random Debian based LiveCD. Do note that Ubuntu does not count because 1) it is really broken in this regard and 2) it is not really compatible with Debian - you should not use Ubuntu repos with Debian ones - especially for low-level stuff. Try Knoppix or maybe get some small Debian LiveCD. The advantage of debootstrap is you do not need to download any iso. All you really need is a few mb worth of packages that you can download while in your LiveCD.

[Debian Debootstrap Install Manual Section (i386)]("http://www.debian.org/releases/stable/i386/apcs04.html.en")

As pointed out above, Ubuntu is really broken when doing low-level administration. No idea why but let us just say I went through an ordeal because of it (although granted, I did learn from it). My guess would be that it was another special case of "Ubuntu patching". Patched/broken debootstrap or some package that is needed to do a bootstrap.


Also, Ubuntu minimal install will teach you very basic things. You will have a working Ubuntu install automated and the only thing left to do is just aptitude install blah which is not all that interesting. Similar can be said for Debian NetInstall with the only difference is that you have to put some work into getting your network setup sometimes because netinstall iso is 150mb and does not provide a lot of packages.

Slackware would also be a good idea, but I have never done an install and it will more than likely teach you much less than the Debian + book combination above and even the debootstrap since Slackware probably automates things like that. But that is my guess.

[Debian Install Manual]("http://www.debian.org/releases/stable/installmanual")

There is also Gentoo, which will probably teach you a lot of a well if you take the most minimalistic install route. The downside is how long it will take due to compiling everything.

---

### Post by Kateikyoushi on 2007-01-23
> **AgenT said:**
> There is also Gentoo, which will probably teach you a lot of a well if you take the most minimalistic install route. The downside is how long it will take due to compiling everything.

That heavily depends on what system is he running, I installed on a 1Ghz pntium M in a weekend with X.
I think it is a great learning tool but you could do that with debian and ubuntu as well or side by side.

---

### Post by yigal.weinstein on 2007-01-27
I used Debian as my first Linux distribution 4 years ago and used it for 2 years.  It is a good project.  The main difficulty I have with investing in it for my needs are that I want a desktop that I can manipulate text, graphics in, in an enjoyoyable gui experience.  I can buy a digital camera and it will be supported.  I can get a new printer and not have to wonder what piece of software is buggy.  Debian is not a distribution for me.  Ubuntu makes a nice usable, distribution that may not be in every respect the cutting edge but then neither is Debian Unstable.  Ubuntu far surpasses Debian in these regards,
1.  A usable out of the box gui experience
   Gnome 2.16 Edgy vs. Gnome 2.14 Unstable.  The gui work in Ubuntu is very nice and it is a real treat sometimes to work in a GUI rather than Bash.
2.  A forum of active members willing to help the other human out.
3.  Installed and working drivers, programs for some of the more common hardware setups: HPLIP etc.

These are important to me.  Important enough to run Ubuntu and not Debian.

---

### Post by jingo811 on 2007-10-10
Will Adamant1988's
** Enabling Multimedia in Feisty (HOW-TO)**
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
Work on Debian and other Linux distros?

Having experienced 2 major kernel problems within 2 years on different PC's related to a simple Synaptic kernel upgrade I'm starting to see less advantages with Ubuntu compared to Debian (which I started to use). 
Also my HP printer and Canon scanner worked right away on Dapper and Feisty until Feisty did a kernel upgrade then neither worked.  Well the printer would work if you searched like crazy for months.

I see no difference in ease of use with external hardwares such as Wireless USB, scanners, printers, cameras etc. etc.  Ubuntu requires you to fix things in terminal anyways 80% of the time then it seems using a stable Debian would be just as well.  Less headaches whe the **** hits the fan.

---

### Post by wdo_will on 2007-10-13
Debian is a great OS.  I used it for a decent period of time and liked the configurability.  Ultimately, I switched back to Ubuntu after being really annoyed that my upgrade from Etch to Lenny didn't work out very well (though I blame myself for this in hindsight).

There is nothing you can do in Ubuntu that you cannot do in Debian.  It will take a bit of work, but that isn't a bad thing per se.

I'd say that Debian and Ubuntu are equally good, it just depends on your wants and needs.

---

### Post by rsambuca on 2007-10-14
> **wdo_will said:**
> Debian is a great OS.  I used it for a decent period of time and liked the configurability.  Ultimately, I switched back to Ubuntu after being really annoyed that my upgrade from Etch to Lenny didn't work out very well (though I blame myself for this in hindsight).

There is nothing you can do in Ubuntu that you cannot do in Debian.  It will take a bit of work, but that isn't a bad thing per se.

I'd say that Debian and Ubuntu are equally good, it just depends on your wants and needs.

I'd say one thing that Ubuntu has that Debian doesn't is quick default integration of the newest gnome desktop.  It seems ubuntu works with the gnome developers to get the latest version right after it is released.  The same version doesn't hit the Debian repos for quite some time.

---

### Post by jingo811 on 2007-10-15
So if you're not married to the Gnome Desktop then using Debian is better?

---

### Post by rsambuca on 2007-10-15
> **jingo811 said:**
> So if you're not married to the Gnome Desktop then using Debian is better?

I wouldn't say better, just different.  Each of these distros has different goals.  Ubuntu comes with more set up for you than Debian, but Debian is a little more customizable without losing upgradability.

---

### Post by jingo811 on 2007-10-15
> **rsambuca said:**
> .... Each of these distros has different goals.  Ubuntu comes with more set up for you than Debian, ...

Yeah I've heard or read that somewhere can you point me to some site that list and compare what have or have not been setup between Ubuntu, Debian or any other Distros?
I had trouble finding such information on DistroWatch.com they only listed programs that came with each distro not how the setups differed like what you mentioned.

---

### Post by rsambuca on 2007-10-15
To be honest, I don't think I have ever seen a decent comparative site like you want.  It certainly would be nice, though.

---

### Post by SunnyRabbiera on 2007-10-15
well certainly there are philosophical differences between the two

---

### Post by jingo811 on 2007-10-15
I have had nothing but bad experience with Ubuntu.
[LIST]
[*]taskcel
[*]aptitude
[/LIST]
Delete things you haven't selected.  A certain kernel upgrade makes your NOAPIC computers go brown screen indefinetely.  Scanners and printers stop working with certain kernel upgrade.
I don't know how much longer I can take this unstable abuse Ubuntu forces on me the user :(  

Something opposite of Ubuntu is what I need something stable that doesn't upgrade until everything is 120% for certain.  Debian for life!

---

### Post by jingo811 on 2007-10-17
> **rsambuca said:**
> .... Each of these distros has different goals.  Ubuntu comes with more set up for you than Debian, ...

So what you said earlier reminds me of something that some Linux veteran said to me once that Ubuntu has more setup that you don't have to activate stuff by yourself in order to protect ports and stuff.

Does that mean Debian has less security by default than Ubuntu.  And if you don't know how to secure things by yourself then you're pretty much sitting on a vulnerable Windows like machine even if it's something as reputable as Debian:confused:

---

### Post by ZipoTe on 2007-10-17
> **jingo811 said:**
> [...] Does that mean Debian has less security by default than Ubuntu[...]:

what??
you say ubuntu comes with more stuff to protect your system... can you explain what are you referring at?:-s

---

### Post by rsambuca on 2007-10-17
> **jingo811 said:**
> So what you said earlier reminds me of something that some Linux veteran said to me once that Ubuntu has more setup that you don't have to activate stuff by yourself in order to protect ports and stuff.

Does that mean Debian has less security by default than Ubuntu.  And if you don't know how to secure things by yourself then you're pretty much sitting on a vulnerable Windows like machine even if it's something as reputable as Debian:confused:

I never said anything about security.  The extras I was referring to that are included by default in Ubuntu are things like plug-and-play tv-tuner support, printers, scanners, bluetooth, etc.

---

### Post by jingo811 on 2007-10-17
> **ZipoTe said:**
> what??
you say ubuntu comes with more stuff to protect your system... can you explain what are you referring at?:-s

I'm just saying I once met this Linux veteran in real life and he said something about Ubuntu thinks about their users security wise compared to other distros.
Where he said other distros require the user to protect ports and stuff themselves.

I'm no security expert so I don't know the extent of the protection that needs protecting but that's what he said.  But he didn't say Debian he said other Distros and he was a Gentoo user.

---

### Post by kellemes on 2007-10-18
If you need to have a "it **just** works" system with a default bloated setup "protecting" you from all kinds of horrible dangers from the outside world you *may* need to go Ubuntu. You actually don't have to think at all to get it to **just** work. Sounds like Windows to me.

If you're actually able to think about what you need from your system, and able to setup a plan to get your system running... Debian most often is the better choice, it's gives you the foundation to base your system on. If you want the ultimate in stability you can have it.. If you want the bleeding-edge you can have it. Debian can be anything **you** want it to be. And it does it well.

---

