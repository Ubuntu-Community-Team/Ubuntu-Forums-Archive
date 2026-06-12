---
title: "Is KDE the black sheep of the Ubuntu family?"
date: 2009-12-28
forum: Desktop Environments
---

### Post by jkounis on 2009-12-28
I have been a happy Ubuntu user since Dapper. When I first installed Ubuntu in 2006, I tried KDE and liked it, but it crashed all the time and proved too unstable for operational use, so I abandoned it. Since, then I've tried a couple of times, and each time have loved the look and feel of KDE, but hated the instability.

Now, I decided to take the plunge again with a new laptop. First, I made the mistake of enabling compiz-fusion on KDE. That broke KDE to such an extent that I had to reinsall my laptop from scratch.

Then I was hit by an X-windows update that had no effect on GNOME, but rendered a computer running KDE completely useless. The screen was totally black... Ctrl-Alt-F1 wouldn't even work to give me a terminal window. Fortunately, I had enabled SSH and was able to get to my computer remotely and fix the problem ([https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483)). A quick check of the forums revealed that _everybody_ who was running KDE had their system broken by this X update... 

Doesn't Ubuntu test both GNOME and KDE environments before they release an update? 

Now, I am typing this from my gnome desktop because my KDE environment is unusable again. As soon as I log in, KDE hangs and I have to force-quit it with Right Alt-PrtScn-K. I tried deleting my .kde file, and it had no effect.

I am at a loss to why the plasma desktop just hangs after login, especially when gnome works fine.

I like KDE a lot, but apparently it doesn't like me back. This brings a couple of questions:

(1) KDE seems to be a respected software project with a large following that has been around for years. Is KDE flaky, is the Ubuntu implementation of KDE flaky, or is it just me? Maybe there is a reason why KDE/Kubuntu is the "second" choice when a new user goes to ubuntu.com and decides to try out ubuntu for the first time?

(2) I'd like to use KDE if it will work for me. Does anyone have any suggestions about how to troubleshoot the KDE hang right after login? The syslog doesn't seem to indicate anything unusual. I am on a Toshiba Satellite L355-S7835 with a Core 2 duo processor/4GB Ram, Intel 5100 integrated wireless.

---

### Post by Ms_Angel_D on 2009-12-28
Some people report having lot's of issues with Kubuntu, and I have heard people say Kubuntu is a bad implementation of KDE. That being said, I personally run Kubuntu and haven't had any hiccups with it. Of course I don't have gnome installed either, but when I have installed it in the past it never gave me a problem. There are many quirks in Kubuntu or so I have heard, that the developers are looking to take care of these with [Project Timelord]("http://www.kubuntu.org/news/timelord") I'm hoping that will help clear up Kubuntu's name some.

---

### Post by 3Miro on 2009-12-28
Ubuntu is very Gnome-centric. I have always had issues running kubuntu. Every now and then some app or another would not run (especially when it comes to the sound). Kubuntu 8.10 with KDE 4.2 was working fine for me, but 9.04 with KDE 4.2 doesn't run. Kubuntu 9.10 run well on my desktop, but when it comes to my laptops, one doesn't even install and the other one doesn't run well. When I tried KDE 4.x with other Linux distros, I had no problems, so it is kubuntu.

I don't think Ubuntu developers test kubuntu as a whole, they probably do a minimal test on KDE as installed after Gnome, but I might be wrong. KDE 4.0 made some revolutionary changes to the projects, however, it was naturally very buggy, this gave somewhat of a bad name to the entire KDE project. Even thought KDE right now is as stable a DE can be, kubuntu doesn't seem to be able to follow, I read somewhere that they didn't have enough people or something.

My solution was to install Ubuntu with Gnome and then install kubuntu-desktop. That gives me both Gnome and KDE and I can switch between them any way that I want.

---

### Post by vnstudy on 2009-12-28
In my favor, I feel KDE is more interesting, but in daily usage, I need a stable enviroment. That is why I choose Ubuntu, instead of Kubuntu.

Windows XP has been living with me in 8 years, but it has gone away since Ubuntu comes to my life. Needless to say, I feel Ubuntu (Gnome) is far different. So that is a reason I do not care about KDE, a Windows XP- like theme.

This is 2nd post on Ubuntuforum :-)

---

### Post by 3Miro on 2009-12-28
Congrats on your second post.

KDE is definitely more advanced then Gnome (something Gnome developers would try to fix for Gnome 3.0), however, I would disagree with you on the XP "look" of KDE. The default setup is windows like (more precisely vista like), however, that it just the first impression. All the Linux DE are infinitely more customizable then any commercial windows/mac, and for me the initial setup last only for a couple of minutes. You can very easily make KDE look almost excatly like Gnome if you want to.

---

### Post by XubuRoxMySox on 2009-12-28
Ubuntu is most definitely a "Gnome-centric" distro. KDE is popular, so to keep up with demand, there's a KDE flavored Ubuntu. Lots of people have no trouble with it.

But if you're looking for a rock-stable truly KDE-friendly distro, I recommend [COLOR="Purple"]Mepis[/COLOR]. Based on Debian Stable (Lenny) rather than Unstable (the Ubuntu family, other than LTS releases) and built for the KDE environment, I think you'll find it super-stable and every bit as powerful and versatile as Ubuntu.

I checked out Kubuntu, PCLinuxOS, and Mepis when I was trying out KDE, and Mepis has been far and away the best implementation of KDE of the three I tried.

I prefer Xfce to the other two major desktop environments, but if KDE was my preference, I would most definitely still be using Mepis rather than Kubuntu.

-Robin

---

### Post by 3Miro on 2009-12-28
When I myself was looking for a good KDE distro, many people recomended Mepis, however, currently Mepis comes with KDE 3.5. That one is outdated.

There are very few KDE 4.x oriented distros, Sabayon being probably the best choice. I think the issue comes from the bad popularity that 4.0 got, and even though currently 4.3 is very stable, many people are still wary and staying sway from it.

---

### Post by aftermath58 on 2009-12-28
We are working hard over at Kubuntu under Project Timelord to make one of the best KDE distros for the lucid release, let's see how that comes out to be :popcorn:

---

### Post by 3Miro on 2009-12-28
> **aftermath58 said:**
> We are working hard over at Kubuntu under Project Timelord to make one of the best KDE distros for the lucid release, let's see how that comes out to be :popcorn:

=D> Best of luck and I do hope you guys succeed.

---

### Post by jkounis on 2009-12-28
I really do like prefer KDE 4.3 user interface and would like to use it if at all possible. Does anyone have any troubleshooting suggestions for me to determine why the desktop is hanging immediately after login?

Otherwise, I really don't want to reinstall Kubuntu like I did before to get KDE working again. Are there any other alternatives? would the following be advisable?

```
sudo aptitude reinstall kubuntu-desktop
```

---

### Post by SuperSonic4 on 2009-12-28
**Kubuntu** is ubuntu's poorer brother. Not **KDE**.

If you want a good KDE distro try Chakra, openSUSE, Fedora or Mandriva

---

### Post by judge jankum on 2009-12-28
Is KDE faster than Gnome? Or just a user preference? I've looked at both and end up scratching my head lol!!

---

### Post by Ms_Angel_D on 2009-12-29
> **judge jankum said:**
> Is KDE faster than Gnome? Or just a user preference? I've looked at both and end up scratching my head lol!!

It depends on your system really as to how kde is, I have a dual core duo with 3 gigs of ram of don't notice a difference, but on an older system with less, gnome would be faster.

---

### Post by jkounis on 2009-12-29
In case anyone is interested, I finally discovered the source of the KDE hang that was perplexing me:

I have two NFS-mounted directories. When I logged out of GNOME, network-manager would shutdown making the NFS mounted directories inaccessible. When I then logged into KDE, it would hang. My guess is it was trying to access the NFS mounts before it enabled the wireless connections. 

I don't know why it would be accessing the NFS directories during the login process. My /home is on the local disk, and I only use the NFS mounts to retrieve shared files via Adobe Reader or OpenOffice, _after_ I login. Maybe it was building the "Recent Items" menu or something like that?

In any case, my workaround is to make sure to unmount the NFS directories before logging out of GNOME if I intend to login to KDE.

---

### Post by XubuRoxMySox on 2009-12-29
> **3Miro said:**
> When I myself was looking for a good KDE distro, many people recomended Mepis, however, currently Mepis comes with KDE 3.5. That one is outdated.

Mepis is moving up to KDE 4 in the next version, which is already in Beta3. 

-Robin

---

### Post by 3Miro on 2009-12-29
> **dixiedancer said:**
> Mepis is moving up to KDE 4 in the next version, which is already in Beta3. 

-Robin

Good news.

As fo which one is faster? KDE + Kwin effects is faster than Gnome + Compiz (which is in general since it also makes a difference the effects that have been enabled and the hardware involved). KDE + no effects vs Gnome + Metacity, I would guess Gnome would have a sight edge if any. In genera, the KDE advantage is the more customization + better apps integration. Gnome looks and feels (and in a way is) like a bunch of random stuff hacked to work together, in KDE you know that things belong together (i.e. global shortcuts to control Amarok, Konqueror, Ktorrent and KGet work easily with each other, preview of minimized windows in KWin, no need for a "compatibility and work around" tabs in Kwin and so on)

---

### Post by UKBB on 2009-12-29
> **Ms_Angel_D said:**
> It depends on your system really as to how kde is, I have a dual core duo with 3 gigs of ram of don't notice a difference, but on an older system with less, gnome would be faster.

I installed Kubuntu on my Dell Dimension 4600 P4 pc with 512 meg of ram and it was a real dog compared to just Ubuntu. I dumped it and did a clean install of Ubuntu 9.10. I noticed that 9.10 ran slow at times so I bumped the memory up to 1.5gig (big help). I'm curious how well KDE would do now that the memory is increased.

---

### Post by schnelle on 2009-12-29
Canonical doesn't care about Kubuntu very much. But I must say that Kubuntu 9.10 with KDE 4.3 works very well on 3 different machines with 3 different grafic cards: intel, ati and nvidia. So, thumbs up for Kubuntu team and I hope that Kubuntu 10.04 with KDE 4.4 will rock :)

---

### Post by Zel Rai on 2009-12-29
I liked KDE 3.x. The complete (ie EVERYTHING) KDE 4 suite is almost as resource hungry as an M$ desktop. However its a lot nicer looking and does 100x more neat things. :P If you have the resources to spare and like a good looking GUI then KDE 4 is definately something you may want to try.

On the other hand Gnome 2 is less resource hungry and offers less eye candy. I like its simplicity as eye candy is not terribly important to me.

Ideally I'd like to see KDE 3.5 with some of the more advanced minor features.  For example the  right click menu to sync a folder containing an SVN checkout, or the ability to change the desktop wallpaper from the desktop.

---

### Post by SuperSonic4 on 2009-12-29
> **Zel Rai said:**
> I liked KDE 3.x. The complete (ie EVERYTHING) KDE 4 suite is almost as resource hungry as an M$ desktop. However its a lot nicer looking and does 100x more neat things. :P If you have the resources to spare and like a good looking GUI then KDE 4 is definately something you may want to try.

On the other hand Gnome 2 is less resource hungry and offers less eye candy. I like its simplicity as eye candy is not terribly important to me.

Ideally I'd like to see KDE 3.5 with some of the more advanced minor features.  For example the  right click menu to sync a folder containing an SVN checkout, or the ability to change the desktop wallpaper from the desktop.

KDE 4.4 Running: Amarok, KMess x2, Firefox 3.5, Konsole, Dolphin, KWin + many effects, plasma (among others)

RAM: 642mb 
CPU: ~10% on each core

If I'm careful I can run KDE 4.4 on the laptop which has 512mb with no slowdown unless using intensive tasks.

I like eye-candy and I like stability (but like the bleeding edge more :popcorn:). Plus computers are moving on now and while there are older computers (and an older DE for them) most computers are now capable of running KDE with no problem. If you don't like eye-candy that's no issue but don't use CPU/RAM as a crutch for beating KDE when it applies in relatively few cases

You can drag and drop a picture onto the desktop to set it as wallpaper if that's your whim

---

### Post by Vegan on 2009-12-29
I have tried the various flavors of desktop, Ubuntu us definitely the most stable with the default Gnome.

Using alternatives is fine, but expect problems as you are away from the main line.

---

### Post by premamotion on 2009-12-30
KDE for me was always a problem... instability, bugs and over complicated things... that`s KDE... Gnome is simplicity, is clean and... works...

---

### Post by jcris on 2010-01-04
KDE via kubuntu for me has always felt like it was done half-assed. It always feels clunky, and the font rendering is horrible no matter what I tried. Now KDE via chakra is like someone turned on a light, and found a holy grail. Its faster than xubuntu on my old laptop, hell its even faster than debian & Xfce, and it hardly uses any of my 1.5gig of ram. Fonts look fantastic, and the whole thing is just beautiful. OpenSuse is another great looking distro for KDE, although it dont seem as fast, and does tend to use up alittle more ram. I think xubuntu is one of the best Xfce distros, and ubuntu really makes gnome look great, but kubuntu is prolly the worst KDE distro Ive seen. Maybe next release will see a better KDE.

---

### Post by tmorphius on 2010-01-04
ive never had any problems with kde, but i havent used it as much as gnome

---

