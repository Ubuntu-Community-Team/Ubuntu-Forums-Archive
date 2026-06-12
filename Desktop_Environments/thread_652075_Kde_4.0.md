---
title: "Kde 4.0"
date: 2007-12-28
forum: Desktop Environments
---

### Post by denali on 2007-12-28
I'm thinking of switching to KDE when they release 4.0 in a few days.  Since I just started using Ubuntu this year, it leads me to wonder if a binary package will be available from the repositories when it's released.  Anyone have any ideas on this?

---

### Post by PPAAUULL on 2007-12-28
I think that you can install the enviroment from the repos. I have done so on my brothers PC with KDE 3.5 so he had GNOME and KDE so he could figure out which he liked better. I forget the commands that could be issued to install a new enviroment but I am sure that it isn't that hard to find around here.

I have been told by people that use KDE that it is more technical in the way that it needs more tweaking. In my opinion though when I used it I didn't have any trouble and that was my first dive into Linux with SuSE running KDE.

Hope this helps.

---

### Post by TheWizzard on 2007-12-28
i don't think they'll put kde 4.0 in the gutsy repos. but i'm not sure. 

i guess 4.0 will be in the next kubuntu release. if you can't wait, you should be able to install kde 4 manually.

---

### Post by markyb86 on 2007-12-28
if it is the kde 4 desktop, you can just install it with

```
sudo apt-get install kubuntu-desktop
```

but if its not you'll get kde 3.5

---

### Post by Half-Left on 2007-12-28
It's in backports, just add this to synaptic.

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)

Gutsy

main

---

### Post by snakeeyes on 2007-12-28
I tried KDE 4.0 on Kubuntu 7.10. It is the release candidate 2 version and its horrible, seriously, it looks good but itsn't as customizable. If u lock the screen, u can't unlock it. If u use kicker then the shading of menus isn't ok, and this is the RC2 version I am talking about. If u try to open a folder with KDE 4.0 RC2 dolphin then it opens one folder called KDE, one called "4" and then a 3rd window with ur folder in it. There r too and I mean too many bugs in it even for a RC2 version. These were the Kubuntu packages though, so who knows maybe openSUSE's r better though I haven't tried them yet.

---

### Post by GeneralZod on 2007-12-28
A few of the bugs snakeeyes mentions are due to improper packaging/ are fixed/ will be fixed for 4.0, but he's essentially correct: KDE4.0 will be *very* rough and buggy, and is probably the worst version to consider switching to :) 

If you seriously want to try to switch to KDE, I'd recommend waiting until at least KDE4.1.

---

### Post by megamania on 2007-12-28
> **GeneralZod said:**
> A few of the bugs snakeeyes mentions are due to improper packaging/ are fixed/ will be fixed for 4.0, but he's essentially correct: KDE4.0 will be *very* rough and buggy, and is probably the worst version to consider switching to :) 

If you seriously want to try to switch to KDE, I'd recommend waiting until at least KDE4.1.
I installed KDE 4 on an Ubuntu system with KDE added.

It works, and it's **beautiful**. There are lots of small things which act strangely (for example, where's the trash icon? Where does Skype go when it is minimized?), but I have the feeling that most of the problems are due to the fact that a RC is added on top of a stable version (without replacing it) which is on top of Ubuntu...

I used to use Gnome for years, but I think KDE 4 will be a killer desktop when it becomes stable. It appears to have all the things I liked of KDE 3 plus the things I love of Gnome.

---

### Post by snakeeyes on 2007-12-28
> **megamania said:**
> I installed KDE 4 on an Ubuntu system with KDE added.

It works, and it's **beautiful**. There are lots of small things which act strangely (for example, where's the trash icon? Where does Skype go when it is minimized?), but I have the feeling that most of the problems are due to the fact that a RC is added on top of a stable version (without replacing it) which is on top of Ubuntu...

I used to use Gnome for years, but I think KDE 4 will be a killer desktop when it becomes stable. It appears to have all the things I liked of KDE 3 plus the things I love of Gnome.
I installed KDE 4 as a seperate session with my kde 3.5.8 install as instructed on Kubuntu's website and its full of bugs. I can even configure my panel, right clicking on it does nothing. Its the last release candidate before the final release I think and there r still a thousand bugs in it. The new kick off menu they use sucks compared to suse menu. They really have to fix a lot of bugs I think.

---

### Post by denali on 2007-12-28
Thank you for all the responses!  I'm getting the impression that my "Mileage May Vary", so I think I may sit back and monitor (lurk) on the forums on 1/11 and see what happens.

Thanks again!

---

### Post by megamania on 2007-12-29
> **snakeeyes said:**
> I installed KDE 4 as a seperate session with my kde 3.5.8 install as instructed on Kubuntu's website and its full of bugs. I can even configure my panel, right clicking on it does nothing. Its the last release candidate before the final release I think and there r still a thousand bugs in it. The new kick off menu they use sucks compared to suse menu. They really have to fix a lot of bugs I think.
I agree. It's full of bugs, but it looks very promising. As I said, I think it will be a killer desktop environment *when it gets stable*.

And I don't like the kick off menu either, but I *hope* in the stable version it will be customizable.

---

### Post by megamania on 2007-12-29
> **denali said:**
> Thank you for all the responses!  I'm getting the impression that my "Mileage May Vary", so I think I may sit back and monitor (lurk) on the forums on 1/11 and see what happens.

Thanks again!
Yeah, I don't think a miracle will happen in two weeks. Stay with Gnome or KDE 3.5 for a while.

As I said, I like kde 4 but I have it as a separate session. If it was my only DE, I would go crazy all the time.

At the moment I'm using KDE 3 and it looks so old - but it's fully functional. It think for a while it's going to be a bit like XP/Vista: Vista is the future, but for the moment most people stick to XP.

---

### Post by snakeeyes on 2007-12-29
You can make kde 3.5.8 look very nice if u want, here is how mine looks:

---

### Post by miggols99 on 2007-12-29
The RC2 is quite unstable. I running Arch Linux with the latest KDE4 svn. Here is my current desktop with compositing:

[[img]http://xs322.xs.to/xs322/07526/Snapshot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs322&d=07526&f=Snapshot.png)

It's running very stable for me, the only problem I have is getting KNetworkManager to startup when I login. I think that the KDE4 final release will be much better. I say that you should wait until the final release. After all, it's only 12 days.

---

### Post by snakeeyes on 2007-12-29
> **miggols99 said:**
> The RC2 is quite unstable. I running Arch Linux with the latest KDE4 svn. Here is my current desktop with compositing:

[[img]http://xs322.xs.to/xs322/07526/Snapshot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs322&d=07526&f=Snapshot.png)

It's running very stable for me, the only problem I have is getting KNetworkManager to startup when I login. I think that the KDE4 final release will be much better. I say that you should wait until the final release. After all, it's only 12 days.
I think ur packages may be stable, I can't even modify the panel on mine, if I lock the screen it won't unlock no matter how many times u enter the password, its slow. Trust me I had high hopes of KDE 4.0, but maybe its just the Kubuntu packages with the problems.

---

### Post by atomkarinca on 2007-12-29
> **miggols99 said:**
> The RC2 is quite unstable. I running Arch Linux with the latest KDE4 svn. Here is my current desktop with compositing:



It's running very stable for me, the only problem I have is getting KNetworkManager to startup when I login. I think that the KDE4 final release will be much better. I say that you should wait until the final release. After all, it's only 12 days.

What's up with that panel? I mean, it's huge!

---

### Post by miggols99 on 2007-12-29
> **atomkarinca said:**
> What's up with that panel? I mean, it's huge!
Yes it is quite big isn't it :) I hope they can make it a bit smaller for the final release. At the moment I can't do a thing about it..

@snakeeyes: I can lock and unlock my session fine. But I still can't resize the panel...

---

### Post by snakeeyes on 2007-12-29
> **miggols99 said:**
> Yes it is quite big isn't it :) I hope they can make it a bit smaller for the final release. At the moment I can't do a thing about it..

@snakeeyes: I can lock and unlock my session fine. But I still can't resize the panel...
Do u have the bug in which u open a file with Dolphin KDE 4 and multiple windows open. I think Arch packages r better cause Kubuntu's r horrible. Seriously whatever u do don't install Kubuntu's KDE packages. One thing I don't get about Ubuntu and Kubuntu is that they donj't pay as much attention to bugs as other distros do.

---

### Post by PmDematagoda on 2007-12-29
> **snakeeyes said:**
> Do u have the bug in which u open a file with Dolphin KDE 4 and multiple windows open.

I reported the bug on the KDE bug database, but it turns out that it was fixed in the later snapshots of KDE4.0, so it seems that the people with those problems are those who installed KDE4.0 RC2 on Ubuntu through the repositories.

---

### Post by snakeeyes on 2007-12-29
> **PmDematagoda said:**
> I reported the bug on the KDE bug database, but it turns out that it was fixed in the later snapshots of KDE4.0, so it seems that the people with those problems are those who installed KDE4.0 RC2 on Ubuntu through the repositories.
oh great

---

### Post by miggols99 on 2007-12-29
I've made a little mockup of how I would like the panel to be. Personally I hate the giant task manager..

[[img]http://xs122.xs.to/xs122/07526/Panel.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs122&d=07526&f=Panel.png)

---

### Post by tofagerl on 2007-12-29
But why would they release a release candidate that is not release-worthy? Release.

That's what Alphas are for. I don't even like people using RCs, Betas should be enough.

---

### Post by snakeeyes on 2007-12-29
> **tofagerl said:**
> But why would they release a release candidate that is not release-worthy? Release.

That's what Alphas are for. I don't even like people using RCs, Betas should be enough.
That is exactly what I thought. I was thinking ok great RC2 should be stable enough why not try it and then after installing it, I got slapped in the face. I am a KDE fan so no flames please, but thats really not what I expected from KDE developers ecspecially so close to the release date.

---

### Post by miggols99 on 2007-12-29
I have improved the mockup to show the whole panel.

[See it here](http://img184.imageshack.us/my.php?image=panelaz7.png)

Compare it to the original screenshot I posted. This one IMO is much better. Slimmer, less space consuming and no ugly stretched icons :P

---

### Post by lexxonnet on 2007-12-30
From what I've heard, they want to push an early 4.0 release, and the tags, i.e., release candidate/beta etc are more indicative of the state of the libraries than the desktop itself.

Frankly, I'm a bit disappointed, but I'll just treat 4.0 as another beta, and 4.1 as the final when it comes out. To be honest, KDE4 has achieved a lot, and its great for some people to play around with, but just isn't releasable quality yet.

---

### Post by snakeeyes on 2007-12-30
I hope Kubuntu 8.04 will have KDE 3.5.8 and not KDE 4.

---

### Post by TheWizzard on 2007-12-30
there won't be a kubuntu 8.04

---

### Post by snakeeyes on 2007-12-30
> **snakeeyes said:**
> I hope Kubuntu 8.04 will have KDE 3.5.8 and not KDE 4.
there is a kubuntu 8.04, visit [http://www.kubuntu.com](http://www.kubuntu.com)

---

### Post by lexxonnet on 2007-12-30
well, it'll have both. They'll both be officially supported for 18 months I believe

---

### Post by TheWizzard on 2007-12-31
> **snakeeyes said:**
> there is a kubuntu 8.04, visit [http://www.kubuntu.com](http://www.kubuntu.com)

you're right. so this story is a hoax: 
[http://linux.slashdot.org/article.pl?sid=07/12/29/2216249&from=rss](http://linux.slashdot.org/article.pl?sid=07/12/29/2216249&from=rss)

---

### Post by Terracotta on 2007-12-31
> **TheWizzard said:**
> you're right. so this story is a hoax: 
[http://linux.slashdot.org/article.pl?sid=07/12/29/2216249&from=rss](http://linux.slashdot.org/article.pl?sid=07/12/29/2216249&from=rss)


No, it's not, K ubuntu 8.04 just won't be an LTS release because of the big change that KDE 4.0 is, that's all that's been said in the article.

---

