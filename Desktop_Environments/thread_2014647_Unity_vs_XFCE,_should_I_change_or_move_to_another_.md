---
title: "Unity vs XFCE, should I change or move to another OS? How?"
date: 2012-07-02
forum: Desktop Environments
---

### Post by jjww on 2012-07-02
Lots of questions and info, so please take the time to read.

**I love Ubuntu**, I would love to stick with it, It's way better than windows especially since Vista and windows 7 which are truly dreadful so I'm not even thinking about moving back to that and I can't afford a Mac. But, (Of course there has to be a but) I have been using Ubuntu as my only OS for quite a while now (since 10.04) which got updated to 11.04 when that version was released but I used the classic desktop exclusively. With the recent hype about the improvements made to the unity desktop I finally took the plunge and updated to 12.04 over the weekend.

I'm now regretting that decision as I just don't get on with unity. It's a personal thing but I find my productivity is down hugely because it's just not designed for multi tasking.

**Feel free to skip this explanation** of why I don't get on with Unity but if you understand my issues it might help for a more appropriate answers/opinions.

I'm not restricted to a laptop sized monitor, I'm not using touch screen, I'm on a full blown desktop system with a 28" monitor and lots of windows open.
Because of the way that I work with typically 8 apps running and often as many as 20 apps open at any one time. Usually, eclipse, netbeans, terminal windows, browser, email, emulators and the odd game of kpatience sitting in the background for when my head is getting too stuffed full of coding issues.

I need a better interface for launching apps, hiding and showing apps (I miss the single click hide and show apps button) the fact that apps launch in full screen making it difficult to switch between apps, hiding the launcher, making it difficult to launch new apps, no option to add launchers to the task bar (That I could find anyway) for custom launchers. I use that option frequently as my custom launchers are now on the desktop and I need to minimise all windows to get to the launcher instead of just clicking the minimise button.
Quite often I will just click on a menu item for an non active window to do something like re-launch an emulator from eclipse, I just cant do this in Unity.
It takes a lot longer to navigate the launcher to launch apps. Havr to type into to the launcher search bar or browse all apps (Where have the categories gone?) making it twice as long to launch a new app than the classic desktop experience.

I guess it works well for most but it sucks for me. This is not about not wanting to move with the times. It's about change has to work better for me not worse.
[B]
So back to my question

[/B]I had a look at xfce from recent issue (May 2012 I think) linux format magazine remix of a number of Ubuntu distro configurations and it looks like it has all the features that I need/miss since updating to 12.04 and it seems on the surface to be very very good. 

1) What I don't understand is what I would loose if I switched to xfce. Why is xfce not the desktop of choice? What makes Unity better than xfce?

2) How to switch?
If I choose to use xfce is it possible to replace Unity and keep my apps and data) I have sda1 as a seperate partition to my home folder. In fact I have a number of partitions for swap folder and somerthing else (Can't remember what right now).

3) Would Linux Mint suit better?
I have had a play with a mint live distro (again from lxf magazine) a while back and that looked awesome but I just went to have another look and got totally confused with the different desktop solutions (cinnamon vs MATE) and again I found myself with too much choice and not knowing enough to make an informed decision.

4) Am I just missing something?
I'm confused about the popularity of Unity? Are there features that address my issues that I just haven't discovered yet? I know I can stick stuff to the launcher bit what's the point of that if I have to minimise my apps just to see the launcher?

The just try it and see principle works but not for me right now! I need to make as informed decision as is possible to make without too much more trial and error as my productivity is suffering I need to make the right chpice as quickly as possible.

I would be grateful for any qualified opinions and answers.

Thanks for your time.

---

### Post by kansasnoob on 2012-07-02
I maintain over 40 PC's, mostly for elderly users, and I've confronted the same issue. Currently about 2 dozen of those users just can't adapt to Unity so I started this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

It's currently difficult for me to edit that thread but if you have a question you should be able to add a comment to that thread.

Or you can even send me a PM if absolutely needed :)

Ubuntu still rocks!

---

### Post by Kronalias on 2012-07-02
I dislike Unity intensely and jumped ship pdq from Ubuntu to Xubuntu - and I haven't looked back.

Xfce does everything I need of it, and I have it installed on a MythTV front/backend, desktop, solid state PC and laptop.

There were two glitches:

1. My laptop wifi wouldn't work out of the box. The wifi is Broadcom, and this thread sorted it:
[http://ubuntuforums.org/showthread.php?t=1966012](http://ubuntuforums.org/showthread.php?t=1966012)

2. Xubuntu 12.04 doesn't support PAE kernels, as in it won't see more than 3GB of RAM.
If you want to use larger memory then you need to change the kernel:

Just check that your machine supports PAE:
grep --color=always -i PAE /proc/cpuinfo
If you see pae in red then you're ok.

Install the pae enabled kernel
sudo apt-get install linux-headers-generic-pae
sudo apt-get install linux-image-generic-pae
sudo apt-get install linux-generic-pae

Reboot and run free in a terminal - you should be able to see all the memory available in your system.

Tidy things up by removing non-pae kernels:
sudo apt-get remove linux-headers-generic
sudo apt-get remove linux-image-generic

As I understand it, Xubuntu 12.04 is the last issue to be released without PAE support, so this problem will go away in the not too distant future.

HTH, Kronalias

---

### Post by rai4shu2 on 2012-07-02
If you do use Xubuntu 12.04, there are a few caveats:

[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117)
[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)
[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

And if you want the latest Xfce:

[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

---

### Post by 3Miro on 2012-07-02
I use XFCE on one machine and Unity on another. Both on 25 - 26 inch monitors with i7 CPUs. I would say that XFCE is better, but Unity is sufficient. Unity on 11.04 is the first draft, if you want to get a better feel for it, try 12.04 that is a lot more polished. Many of the nuisances that you describe are gone now, I didn't use 11.04 Unity, I used 11.10 a little and now I am happy with 12.04.

Ultimately there is no interface that will make everyone happy, the good news is that you have choice.

> **jjww said:**
> 
1) What I don't understand is what I would loose if I switched to xfce. Why is xfce not the desktop of choice? What makes Unity better than xfce?

XFCE takes longer to set the way you want, but the modern XFCE is pretty close to Gnome 2 (just have to set it to behave the way you want). Gnome 3 is the default DE of Ubuntu, with settings, apps, daemons, they just replace the WM/interface Gnome-shell with Unity (Ubuntu has always used Gnome). Compared to XFCE (and Gnome-shell) Unity is more flashy. I find Unity a lot more functional then Gnome-shell and Gnome 3 apps have more integrated features than XFCE.

> 
2) How to switch?
If I choose to use xfce is it possible to replace Unity and keep my apps and data) I have sda1 as a seperate partition to my home folder. In fact I have a number of partitions for swap folder and somerthing else (Can't remember what right now).

Install xfce4 form the Software Center or Synaptic. Then log into XFCE. All of your apps and data will be there. You may have to spend some time setting up xfce, but in the end you should have Ubuntu working with XFCE. Note that installing xubuntu-desktop is also an option, but it will pull in other things that you may or may not need.

> 
3) Would Linux Mint suit better?
I have had a play with a mint live distro (again from lxf magazine) a while back and that looked awesome but I just went to have another look and got totally confused with the different desktop solutions (cinnamon vs MATE) and again I found myself with too much choice and not knowing enough to make an informed decision.

Mint comes by default with Gnome 3 and Gnome-shell. They provide an alternative of Mate or Cinnamon. You can also install Mate and Cinnamon (and Gnome-shell) under Ubuntu without the need to use Mint. You may have to do some of the settings manually, but it shouldn't be an issue.

> 
4) Am I just missing something?
I'm confused about the popularity of Unity? Are there features that address my issues that I just haven't discovered yet? I know I can stick stuff to the launcher bit what's the point of that if I have to minimise my apps just to see the launcher?

The just try it and see principle works but not for me right now! I need to make as informed decision as is possible to make without too much more trial and error as my productivity is suffering I need to make the right chpice as quickly as possible.

I would be grateful for any qualified opinions and answers.

Thanks for your time.

Try Unity on 12.04. (btw, moving your mouse over the left edge should bring up the launcher, also hitting the "meta" or "windows" key, you can also use Compiz Config Settings Manager to force the launcher to not auto-hide as well as adjust the size of the icons)

Spend some time with XFCE as it is different and you need to massage it to get it to do what you want.

---

### Post by DMGrier on 2012-07-02
I think Unity is pretty awesome, I think of it like this,Windows and Apple are slowly moving to a desktop that will function well on a desktop and a tablet and I have used both Windows 8 CP and OSX lion and honestly neither one really can be good at both. I heard OSX is going to start becoming more like iOS but I had a Iphone and I hated it do to lack of features. Unity does a decent job at both as far as the desktop is concerned, it is new but for all the major desktop changes I think they did a hell of a job and with each release I watch Ubuntu Unity become more mature. Yeah Unity is not for everyone but I am proud of my wife cause she is by no means a Linux person like myself but she just made the switch to 12.04 with Unity due to it's app center, reliability and multi-tasking that windows could not provide.

---

### Post by jjww on 2012-07-02
Thanks for all the replies.

DMGrier - Ubuntu is great, Linux is great but for the reasons I outlined in my post I can not afford to use Unity as it just reduces my productivity too much. Congrats on converting your other (Better?) half :)

Thanks to Kronalias and 3Miro for such comprehensive responses. You have helped make things a lot clearer for me. I think I'll try installing xfce.

rai4shu2 - Those issues are not really show stoppers for me thanks for pointing them out.

---

### Post by dangmc on 2012-07-03
@jjww: I feel your pain! I have a desktop pc similar to what you described, And finally out of sheer desperation I tried this:[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu). I was very pleasantly suprised how painless this was; No errors. I simply added lost programs as needed. Now I seem to have left all the program crashes I've experienced since installing 12.04-x86_64. I really hate unity and I've tried several different os's and environments before settling on this. Everything runs a lot faster, too. Right now I'm also trying to learn Slackware. Not for the faint hearted or for those who don't have time to experiment, but I've learned more about how Linux works in the past month than I learned in 6 years of Ubuntu.

---

### Post by unsinkable on 2012-07-03
sorry can't answer any of your questions, but, have you tried out Elementary OS? Unity does suck, but we hate to switch away from ubuntu, so maybe you can try out elementary os, it's based on ubuntu core, so you can use all the softwares and programs and its interface is not unity and it looks very good (quite like OS X). You don't have to switch to another distro. Give it a try!

---

### Post by DMGrier on 2012-07-03
> **jjww said:**
> Thanks for all the replies.

DMGrier - Ubuntu is great, Linux is great but for the reasons I outlined in my post I can not afford to use Unity as it just reduces my productivity too much. Congrats on converting your other (Better?) half :)

Thanks to Kronalias and 3Miro for such comprehensive responses. You have helped make things a lot clearer for me. I think I'll try installing xfce.

rai4shu2 - Those issues are not really show stoppers for me thanks for pointing them out.

I get the productivity thing and I was not going to try to argue that I was just trying to point out before the hate for Unity started getting posted all crazy when honestly when you look at it from what is trying to be don,e they have IMO done better then M$ and Apple.

I would not give Elementary a try only because I have read that they are very buggy and a few releases ago a certain  update cause a full on Ubuntu desktop install or something. 

In my experience I really enjoyed using Linux Mint Debian Edition xfce desktop just due to how light and fast it was.

---

### Post by andrew.46 on 2012-07-03
> **dangmc said:**
>  Right now I'm also trying to learn Slackware. 

It is a good time to look at Slackware as version 14.0 will be out soon enough.

---

### Post by vasa1 on 2012-07-03
Nice recurring discussion :)

---

