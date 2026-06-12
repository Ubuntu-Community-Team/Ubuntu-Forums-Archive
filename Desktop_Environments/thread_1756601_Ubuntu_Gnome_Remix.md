---
title: "Ubuntu Gnome Remix"
date: 2011-05-12
forum: Desktop Environments
---

### Post by Kri5 on 2011-05-12
Has anyone tried the following Gnome 3 enviroment for Ubuntu Natty?:
 
[http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)
 
I have recently upgraded to Natty and i'm going to try it for a few weeks, however i'm already missing the amount of customablity i had in Maverick and having googled through the internet for Unity and Gnome 3, on first impressions i'm tending to lean towards Gnome 3.  However there is obvoiusly the drawback that installing Gnome 3 will break Unity, so i'm reluctant to try it on a whim, although i'm not adverse to re-installing, it's just time consuming.
 
If anyone has tried or is using Gnome 3, some feed back would be greatly appreciated.:)

---

### Post by screaminj3sus on 2011-05-12
I haven't tried it but I've heard its missing a few gnome 3 things fedora and opensuse has and can be buggy (opensuse's repo is buggy as hell though too) Some people seem to be running it fine though.

---

### Post by Kri5 on 2011-05-13
Thanks Screaminj3sus,

I went ahead and tried it myself and unfortunately it crashed my system badly, I was unable to boot at all and ended up having to do a complete re-install. At that point I decided to go back to 10.10 as I've always found that to be reliable and stable, plus i love the custom-ability.

I look forward to seeing how 11.10 turns out though.

---

### Post by attackgecko on 2011-05-18
I'm the creator of the UGR project

As of now, the Ubuntu/ Debian GNOME 3 packages are very buggy/incomplete.  We're working with the GNOME 3 team to tame the jungle.  

Personally, it runs pretty good on my test computers, so I'm curious to hear about the issues you had.

---

### Post by VanR on 2011-05-19
Yep it crashed 2 different installs of 11.04 on my machine. I'm back to 10.10 also.

---

### Post by jjcv on 2011-05-19
I have been running it now for several weeks with virtually no problems.  Only problem seems to be GDM when trying to login locks up sometimes.  I have to open a virtual console Ctr-Alt-F1, login and restart GDM to login sometime. (have not tried the restarting for a few days now after lots of updates.

There are also lots of extensions now which allow you to customise Gnome-Shell to make it look like whatever you like.

---

### Post by Dobbie03 on 2011-05-19
Aside from not being able to use Fallback Mode I have zero issues.

---

### Post by attackgecko on 2011-05-20
UGR has included a fallback session option for a few releases now - the gnome-session-fallback package patches the Ubuntu Classic session options to make them run as fallback.  
 
We are working on packaging shell extensions, this will probably come in a month or so.  
 
@VanR I'd like to get some more information on your issues, if possible

---

### Post by karmila on 2011-05-25
> **jjcv said:**
> I have been running it now for several weeks with virtually no problems.  Only problem seems to be GDM when trying to login locks up sometimes.  I have to open a virtual console Ctr-Alt-F1, login and restart GDM to login sometime. (have not tried the restarting for a few days now after lots of updates.

There are also lots of extensions now which allow you to customise Gnome-Shell to make it look like whatever you like.
Yeah, i got this problem too.

But okay though it's still in early development.

---

### Post by cbowman57 on 2011-05-25
> **Kri5 said:**
> Has anyone tried the following Gnome 3 enviroment for Ubuntu Natty?:
 
[http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)
 
I have recently upgraded to Natty and i'm going to try it for a few weeks, however i'm already missing the amount of customablity i had in Maverick and having googled through the internet for Unity and Gnome 3, on first impressions i'm tending to lean towards Gnome 3.  However there is obvoiusly the drawback that installing Gnome 3 will break Unity, so i'm reluctant to try it on a whim, although i'm not adverse to re-installing, it's just time consuming.
 
If anyone has tried or is using Gnome 3, some feed back would be greatly appreciated.:)

Well, I've done my best to remove every last bit of unity from my system, after using it for an extended period, then tried Gnome 3.0 on Natty.  I'm absolutely sold on it even at this early stage.

As far as customization, how much do you want?

---

### Post by cbowman57 on 2011-05-25
> **attackgecko said:**
> I'm the creator of the UGR project

As of now, the Ubuntu/ Debian GNOME 3 packages are very buggy/incomplete.  We're working with the GNOME 3 team to tame the jungle.  

Personally, it runs pretty good on my test computers, so I'm curious to hear about the issues you had.

Good work so far, yours is one of the PPA's that I'm using and I am completely sold on Gnome 3.0.  Thanks a lot for all the time & effort you guys are putting into the project.

---

### Post by cbowman57 on 2011-05-25
> **attackgecko said:**
> UGR has included a fallback session option for a few releases now - the gnome-session-fallback package patches the Ubuntu Classic session options to make them run as fallback.  
 
We are working on packaging shell extensions, this will probably come in a month or so.  
 


I've got a fairly decent collection of extensions, some of which I've modified for maximum compatibility (there were some conflicting extensions).  You're welcome to incorporate them into UGR if you want them.

---

### Post by VanR on 2011-05-25
> **attackgecko said:**
> UGR has included a fallback session option for a few releases now - the gnome-session-fallback package patches the Ubuntu Classic session options to make them run as fallback.  
 
We are working on packaging shell extensions, this will probably come in a month or so.  
 
@VanR I'd like to get some more information on your issues, if possible

Sorry I just saw this. And I also realized it was not UGR I attempted to install so I apologize. I just did a terminal install of Gnome 3 I found on omg ubuntu or somewhere. It wasn't your project.

---

### Post by macozz on 2011-05-25
I just installed UGR in a Natty fresh install, but it fail to start. I get the "Oh no..." error screen. I used to have the gnome-shell working until yesterday, but it stop working.
My system is an Asus 1201n, with Nvidia Ion, 4Gb ram. I have the proprietary driver activated.

Thanks!

---

### Post by macozz on 2011-05-26
I fixed my problem deleting the extension and themes folder in ~home/.local/share/gnome-shell/.
After that you can install the extension again.

---

### Post by attackgecko on 2011-05-27
As far as customization and extensions go, those problems will be solved in a few releases down the road when shell extensions start trickling into our repositories.  We have to create packaging for all of the extensions.  Our priorities will be themeselector (provides easy theme changing) and other customizations.  

For developers, how this will work on the package side is that all shell extensions will go in the same source package.  We'll use launchpad's bzr builder/ source package builder features to automatically include extensions from several different sources, in addition to community contributions.  When the source package is built, it will build a separate installable binary package for each shell extension.  

In a few weeks, we should be ready to start including community contributed extensions.  You can see it start to take shape here:
[https://blueprints.launchpad.net/ugr-meta/+spec/gnome-shell-extensions](https://blueprints.launchpad.net/ugr-meta/+spec/gnome-shell-extensions)
[https://wiki.ubuntu.com/UGR/ShellExtensions](https://wiki.ubuntu.com/UGR/ShellExtensions)

---

### Post by NormanFLinux on 2011-05-28
Make sure developers build a 2D Shell with extensions. Not all of us have accelerated graphics cards.

---

### Post by karmila on 2011-05-28
Hi [attackgecko]("http://ubuntuforums.org/member.php?u=1275368"),

Is there an Ubuntu Forums thread or a site that we are UGR users can monitor the development or current issues?
It would be nice if we have one.

---

### Post by kansasnoob on 2011-05-28
I began testing UGR from it's beginning and most of the shortcomings are actually just gnome3 related.

The past few days I've been testing Oneiric preparing for Alpha1 iso-testing next week and I'm a bit curious how soon we might see UGR begin development on it's OO compatible version :)

As expected the OO default options are only unity and unity-2d (called Ubuntu and Ubuntu 2d at login), and the classic options can be added by installing the package 'gnome-session-fallback', but I've not figured out a way to run a gnome-shell session :confused:

OO will definitely be fun.

---

### Post by bmbaker on 2011-05-28
you can now get the gnome-extensions from the testing ppa :-)

---

### Post by karmila on 2011-05-28
> **bmbaker said:**
> you can now get the gnome-extensions from the testing ppa :-)

Thank for the news :D

---

### Post by attackgecko on 2011-05-30
> **karmila said:**
> Hi [attackgecko]("http://ubuntuforums.org/member.php?u=1275368"),

Is there an Ubuntu Forums thread or a site that we are UGR users can monitor the development or current issues?
It would be nice if we have one.

Everything is on our [launchpad]("https://launchpad.net/ubuntugnome"): bugs, blueprints, releases, etc

> **kansasnoob said:**
> I began testing UGR from it's beginning and most of the shortcomings are actually just gnome3 related.

Yep.  Just about all of our current bugs are GNOME 3 related

> **bmbaker said:**
> you can now get the gnome-extensions from the testing ppa :-)

Awesome.  We'll use this to build UGR's extension pack, which will allow each extension to be installed and enabled separately.

---

