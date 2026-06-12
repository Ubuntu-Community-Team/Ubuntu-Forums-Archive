---
title: "Cinnamon 4.0"
date: 2019-06-16
forum: Desktop Environments
---

### Post by xavierbaez on 2019-06-16
Hello. I know Cubuntu sort of failed at it's not an official flavor.
My question is, after trying embrosyn/cinnamon and finding it VERY unstable, what options do I have if I want to have Ubuntu and also Linux Mint on the same partition?

1) Install Linux Mint 19.1 and then install Ubuntu and Kubuntu desktop
2) Install Ubuntu 18.04 and then install Cinnamon 4.0

It seems like Option 2 is much better as I have no idea how to install Linux Mint 19 and then try to make it look 'like Ubuntu' as I know Ubuntu is a heavily customized gnome 3.

I am also thinking installing Ubuntu in one partition and Linux Mint in another partition, but that makes it really complicated as I want to use this as my main developer machine.

I very much appreciate your thoughts as I want to save days/weeks of wasting time just to found out these are 2 different desktops and will more likely won't be working great in the same partition.

Thanks!

---

### Post by xavierbaez on 2019-06-16
For example, has anybody tried to install Linux Mint Cinnamon to Ubuntu?
Here is the github url where they develop Cinnamon:

[https://github.com/linuxmint/cinnamon](https://github.com/linuxmint/cinnamon)

---

### Post by jeremy31 on 2019-06-16
You might want to see  [https://launchpad.net/~linuxmint-daily-build-team/+archive/ubuntu/daily-builds](https://launchpad.net/~linuxmint-daily-build-team/+archive/ubuntu/daily-builds)

---

### Post by Frogs Hair on 2019-06-16
You could have Mint and Ubuntu on the same drive, but not the same partition. Option 2, 18.04 with cinnamon will work, but you will have the bloat of two desktops. Cinnamon is native to Mint and probably the most stable option.

> I have no idea how to install Linux Mint 19 and then try to make it look 'like Ubuntu

 If the problem is theming there is no reason you can't change the themes and icons on mint to something you like better. It's not that difficult to install themes and icons. Is the Cinnamon desktop a must have ?

---

### Post by xavierbaez on 2019-06-16
> **Frogs Hair said:**
> You could have Mint and Ubuntu on the same drive, but not the same partition. Option 2, 18.04 with cinnamon will work, but you will have the bloat of two desktops. Cinnamon is native to Mint and probably the most stable option.



 If the problem is theming there is no reason you can't change the themes and icons on mint to something you like better. It's not that difficult to install themes and icons. Is the Cinnamon desktop a must have ?

No the problem is not theming
The problem is I want to have multiple Desktop Environments

---

### Post by xavierbaez on 2019-06-16
> **jeremy31 said:**
> You might want to see  [https://launchpad.net/~linuxmint-daily-build-team/+archive/ubuntu/daily-builds](https://launchpad.net/~linuxmint-daily-build-team/+archive/ubuntu/daily-builds)

I tried these two

[LIST=1]
[*]*sudo add-apt-repositoryppa:trebelnik-stefina/cinnamon*&#8232;
[LIST]
[*]DEPENDS ON: ppa:embrosyn and also use nightly builds!!!
[*]PROBABLY UNSTABLE!!!
[/LIST]

[*]sudo add-apt-repository ppa:embrosyn/cinnamon
[LIST]
[*]VERY UNSTABLE
[/LIST]
[/LIST]

The ppa:embrosyn/cinnamon was so bad I couldn't even log into the desktop, Cinnamon binary would crash the second I logged in.
Therefore, the PPA you are suggesting is not based on cinnamon itself but on Linux Mint?

Is there any PPA from Linux Mint 19.1?

Not from the daily builds of Cinnamon or from the daily builds of Linux Mint?

I would just like a stable 3.8 or a 4.0 or Cinnamon.

---

### Post by xavierbaez on 2019-06-16
I guess to rephrase the question
1) If Linux Mint is THE SAME as Ubuntu (share the same base)
Shouldn't it be easy to install the Linux Mint packages into Ubuntu?

After all, they share the same base right?

I am a little surprised we have to chose between two distributions that were supposed to be pretty much the same thing, it's almost as Linux Mint was supposed to be a flavor of Ubuntu.
Like kubuntu or something

---

### Post by Frogs Hair on 2019-06-16
> **xavierbaez said:**
> No the problem is not theming
The problem is I want to have multiple Desktop Environments

You can accomplish that with Ubuntu or Mint, but you will have logout to switch between them. See this sticky for examples of how to install different desktop environments.

[https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676)

---

### Post by Frogs Hair on 2019-06-16
> I am a little surprised we have to chose between two distributions that  were supposed to be pretty much the same thing, it's almost as Linux  Mint was supposed to be a flavor of Ubuntu.
Like kubuntu or something 				

Mint is separate distribution and like many Ubuntu derivatives the packages are not all interchangeable.

---

### Post by jeremy31 on 2019-06-16
> **xavierbaez said:**
> I tried these two

[LIST=1]
[*]*sudo add-apt-repositoryppa:trebelnik-stefina/cinnamon*&#8232;
[LIST]
[*]DEPENDS ON: ppa:embrosyn and also use nightly builds!!!
[*]PROBABLY UNSTABLE!!!
[/LIST]

[*]sudo add-apt-repository ppa:embrosyn/cinnamon
[LIST]
[*]VERY UNSTABLE
[/LIST]
[/LIST]

The ppa:embrosyn/cinnamon was so bad I couldn't even log into the desktop, Cinnamon binary would crash the second I logged in.
Therefore, the PPA you are suggesting is not based on cinnamon itself but on Linux Mint?

Is there any PPA from Linux Mint 19.1?

Not from the daily builds of Cinnamon or from the daily builds of Linux Mint?

I would just like a stable 3.8 or a 4.0 or Cinnamon.

As far as I have seen, the PPA I suggested is made for Ubuntu judging by the version numbers as Cinnamon builds for Mint would show a Mint version, instead of 4.2.0-unstable-201906141145~ubuntu18.04.1 you would see linuxmint19 or tara or tessa, maybe tina

---

### Post by xavierbaez on 2019-06-16
> **jeremy31 said:**
> As far as I have seen, the PPA I suggested is made for Ubuntu judging by the version numbers as Cinnamon builds for Mint would show a Mint version, instead of 4.2.0-unstable-201906141145~ubuntu18.04.1 you would see linuxmint19 or tara or tessa, maybe tina

Yes I understand, but my question was is there a PPA that is built from Linux Mint stable
not from Linux Mint daily.

I can try the PPA, I am afraid of doing it, it took me several hours to uninstall everything and had to create a snapshot.
Throughout many years of experience, you always avoid nightly, unless you're developing.

---

### Post by xavierbaez on 2019-06-16
> **Frogs Hair said:**
> You can accomplish that with Ubuntu or Mint, but you will have logout to switch between them. See this sticky for examples of how to install different desktop environments.

[https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676)

I know I would have to logout and log back in.
I read your post and it says '[COLOR=#000000]Ubuntu with the Cinnamon desktop qualifies as an Ubuntu remix and is not the same as Linux Mint. The former is installed entirely from packages in the repos, whereas Mint is an independent entity with its own developers, policies, maintenance and direction.'

[/COLOR]Therefore, is there any project so Ubuntu users have Cinnamon 3.8 or Cinnamon 4.0 STABLE?

Or should we stick to Cinnamon 3.6.7?

Cinnamon 3.6 was used on Linux Mint 18.3, which was released 1 year 6 months ago (December 2017), so it's not terribly outdated.

***Linux 18.3 Cinnamon 3.6 (December 2017)***
***Linux 19 Cinnamon 3.8 (June 2018)***
[B][I]Linux 19.1 Cinnamon 4.0 (December 2018)

[/I][/B]The problem that I have is PPAs are based on Linux Mint daily, that's way too unstable.
Is there any alternative?

I feel like if I install Linux Mint, I will have the same problem, all the desktops from Ubuntu (ubuntu-desktop, kubuntu-desktop) will be unstable or impossible to install.

---

### Post by Frogs Hair on 2019-06-16
I'm using the 19.10 development release and Cinnamon 3.8 is what is currently included in the Ubuntu repository. Mint does offer a KDE flavor which is very similar Kubuntu. Ubuntu + KDE.

You can install the Gnome and KDE desktops from the Mint repository if needed.

---

### Post by crip720 on 2019-06-16
If you only want different desktops installed in an easy manor, can have a look at [https://linuxaio.net/downloads/linux-aio-ubuntu/](https://linuxaio.net/downloads/linux-aio-ubuntu/).  The only thing is that I don't think they have Ubuntu with cinnamon, but have it with Mint.  AIO combines most of the desktop flavours into one download and they do not seem to make a mess of it, like we can do.  You install and then you have choice of desktop by just logging out and in again.

---

### Post by xavierbaez on 2019-06-17
> **Frogs Hair said:**
> I'm using the 19.10 development release and Cinnamon 3.8 is what is currently included in the Ubuntu repository. Mint does offer a KDE flavor which is very similar Kubuntu. Ubuntu + KDE.

You can install the Gnome and KDE desktops from the Mint repository if needed.

So what would you recommend?

[LIST=1]
[*]Install Linux Mint 19.1 as a base and install
[LIST]
[*]ubuntu-desktop
[*]kubuntu-desktop
[*]budgie-desktop
[*]mate-desktop
[*]xubuntu-desktop
[/LIST]

[*]Install Ubuntu 18.04 as a base and install
[LIST]
[*]cinnamon-desktop
[/LIST]
[/LIST]

It seems that having Ubuntu 18.04 as the base, and then finding a way to get cinnamon-desktop, will be the most stable thing to do.

Have anybody installed Linux Mint 19.1 as a base and then install ubuntu-desktop?
From what I understand, Linux Mint 19.1 is the same as Ubuntu, except for a few packages, correct?

---

### Post by Frogs Hair on 2019-06-17
I would install Ubuntu add the desktops you want and add following[ PPA]("https://launchpad.net/~trebelnik-stefina/+archive/ubuntu/cinnamon"). Ubuntu desktop packages are not intended for Mint. Because Mint and Ubuntu are the same under the hood doesn't mean they support each others desktop environments without  ppa help. They are different distributions with different development teams and goals.

---

### Post by xavierbaez on 2019-07-22
> **xavierbaez said:**
> For example, has anybody tried to install Linux Mint Cinnamon to Ubuntu?
Here is the github url where they develop Cinnamon:

[https://github.com/linuxmint/cinnamon](https://github.com/linuxmint/cinnamon)

Hello. I have successfully installed Cinnamon 4.0 in Ubuntu 18.04 on two machines.

It works perfectly fine and perfectly stable.

If 5 people tell me they want a full tutorial with YouTube video I will spend 2-3 hours creating such tutorial.

My goal is to help anybody interested and also receive feedback so we can make this a sticky post.
If interested please reply.

What I ended up doing is using Linux Mint repositories ONLY for cinnamon.
Spent 2 days on it, and it is working incredibly well.
I can update upgrade it's 99% a Ubuntu distro.
It's almost like a PPA.

---

### Post by catman2 on 2019-07-27
> **xavierbaez said:**
> I tried these two

[LIST=1]
[*]sudo add-apt-repository ppa:embrosyn/cinnamon
[LIST]
[*]VERY UNSTABLE 
[/LIST]
  
[/LIST]

The ppa:embrosyn/cinnamon was so bad I couldn't even log into the desktop, Cinnamon binary would crash the second I logged in.
Therefore, the PPA you are suggesting is not based on cinnamon itself but on Linux Mint?


Not sure if it really helps, but for some quick tests I installed from the embrosyn/cinnamon 

```
 sudo apt install cinnamon
```

from an fully stuffed Xubuntu 18.04 installation. I logged out and into the cinnamon desktop and it seemes to work fine. Only thing it was missing was no images and themes. I did not bother to download any..

Since I did like xfce better I removed the installation again. Maybe its helpful if you could reproduce some specific instabiliites so other people could verify that on their installations?

---

