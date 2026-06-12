---
title: "How to locate and destroy these nasty programs?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by zenlunatic on 2006-06-03
```
jhenn@ubuntu:~$ vrms
               Non-free packages installed on ubuntu

linux-386                 Complete Linux kernel on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
ttf-gentium               Gentium TrueType font

  6 non-free packages, 0.4% of 1381 installed packages.

```

How can I find out what these packages are and totally remove them?  Some of the names are cut off it would appear.  I really don't want these things on my system.  Thank you guys.

---

### Post by Mr. Polite on 2006-06-03
You could remove them. But you'll probably lose most of your media playback capability (MP3, MPEG, etc.). Or limit your system otherwise.

How did they get installed? You must have used Automatix or EasyUbuntu and unknowingly installed those modules. A good reason to manually configure your system so you know whats going on. 

Out of curiosity, why do you want them removed? If its on principle then... well thats very noble of you... but in reality everything, including things in Linux, isn't free.

---

### Post by zenlunatic on 2006-06-03
[QUOTE=Mr. Polite]You could remove them. But you'll probably lose most of your media playback capability (MP3, MPEG, etc.). [/quote]

I don't care.

[QUOTE=Mr. Polite]How did they get installed? You must have used Automatix or EasyUbuntu and unknowingly installed those modules. A good reason to manually configure your system so you know whats going on.[/quote]

Actually no, I didn't use those programs.  I installed ubuntu-desktop kubuntu-desktop and xubuntu-desktop from a server install and a couple additional programs and I never activated multiverse or did any of those things you said.  Its well known ubuntu ships with non-free packages, in case you didn't know.

[QUOTE=Mr. Polite]Out of curiosity, why do you want them removed? If its on principle then... well thats very noble of you... but in reality everything, including things in Linux, isn't free.[/QUOTE]

Um, you care to elaborate on that little theory?

Oh.  And yes it is against my principles to use non-free software, thanks.

---

### Post by zenlunatic on 2006-06-03
Okay just got done installing xubutnu fresh dapper from cd on my desktop.  Haven't installed a single thing except virtual rms.  I even when into synaptic and removed "restricted copyrights" from all my repositories and only have Officially supported and Universe.  Here is what I get:

```
Setting up vrms (1.11) ...

An invocation of vrms has been added to the set of cron jobs run on a
monthly basis, so that you will get a periodic reminder of non-free
packages which are installed on your system.  Here is the current list:

            Non-free packages installed on jhenn-laptop

linux-386                 Complete Linux kernel on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
ttf-gentium               Gentium TrueType font

  5 non-free packages, 0.7% of 736 installed packages.

```

](*,)

---

### Post by aysiu on 2006-06-03
[QUOTE=zenlunatic]Its well known ubuntu ships with non-free packages, in case you didn't know.[/QUOTE] No, it isn't.

Can you please substantiate this statement with some evidence?

---

### Post by zenlunatic on 2006-06-03
[QUOTE=aysiu]No, it isn't.

Can you please substantiate this statement with some evidence?[/QUOTE]

Yeah sure.  sudo apt-get install vrms and see what it says. 90% chance you have none-free packages on your system.

WHEN I SAY FREE I MEAN FREEDOM.

---

### Post by aysiu on 2006-06-03
[QUOTE=zenlunatic]Yeah sure.  sudo apt-get install vrms and see what it says. 90% chance you have none-free packages on your system.

WHEN I SAY FREE I MEAN FREEDOM.[/QUOTE] Actually it's more like 96%, but that's because I installed those non-free packages, not because they came from a default Ubuntu installation.

For example, TTF-Gentium isn't non-free: [http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium_linux](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium_linux)

---

### Post by frying_fish on 2006-06-03
The restricted modules ones look related to your graphics driver, so if you happen to be using ones related to those, then just get rid of them and use the one from xorg itself.

To remove them, why not do apt-cache search restricted-modules, or open up synaptic and search for them in there, then you can see what they are and get rid of them.

---

### Post by Ramses de Norre on 2006-06-03
apt-cache search shows you all that's available in the repos, dpkg -l shows you all that's installed (or has been installed) on your system.

---

### Post by zenlunatic on 2006-06-03
Yeah I could delete those packages, but I could also destroy my system in the process, removing critical packages.

---

### Post by frying_fish on 2006-06-03
well not likely, if they are the ones related to 386 (and I suggest you move to 686, or a more appropriate one anyway).

Have a look at what the "restricted modules" installs, as I know its not installed by default, so if you wanted something say, nvidia graphics support then it would have installed them, or if you had anything else like that that would be included check, if it causes a severe break, well boot to recovery mode and make sure you have a backup kernel (or the live cd to hand so you can boot that, chroot and do what you need there then)

---

### Post by Mr. Polite on 2006-06-03
[QUOTE=zenlunatic]Yeah I could delete those packages, but I could also destroy my system in the process, removing critical packages.[/QUOTE]

See first reply.

---

### Post by az on 2006-06-03
[QUOTE=zenlunatic]Yeah I could delete those packages, but I could also destroy my system in the process, removing critical packages.[/QUOTE]
That depends.

Actually, none of them are crtitical.

Ubuntu ships with some binary-only (therefore not free-libre) drivers.  If you don't play 3d games on your box you don't need them at all.  There are also a few wireless cards and other hardware that ship with some firmware that falls under the same category.

That's it.

They are packaged in a way that makes them easily removed.  You end up with a completely DFSG "free" (gpl compatible - software freedom - the *real* deal.)

No bullshit, without those packages, your system is completely free-libre.  You can even enable the universe repo and still stay "clean".  All of the non-free stuff is in the multiverse repos and the restricted (restricted modules).


In a nutshell, the linux-386 (or 686, k7, smp, whatever) package depends on the linux-image-386 package and the linux-restricted-modules-386 package.

You don't need the linux-restricted-modules packages to boot, just to use those particular devices.  If you do not even own any of that kind of hardware, like I do, you can remove the linux-restricted-modules packages on your system.  That will take with it the linux-386 package, BUT NOT THE linux-image-386 package which is what you need to have to get updates.

Those are all metapackages there to enable you to get the latest real linux kernel package.  For example linux-image-386 will always depend on the latest kernel image, so if there is an update, you get the latset kernel.

Any other questions?

---

### Post by zenlunatic on 2006-06-03
Thanks for a little help instead of some heat.  Okay I got this:

```
jhenn@jhenn-laptop:~$ dpkg -l linux-restricted-modules*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Halfthe-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-restrict 2.6.15.11-1    Non-free Linux 2.6.15 modules on 386
ii  linux-restrict 2.6.15.22      Restricted Linux modules on 386.
ii  linux-restrict 2.6.15.11-1    Non-free Linux 2.6.15 modules helper script

```

Still can't see the entire name of the package.  Any ideas?

---

### Post by az on 2006-06-03
[QUOTE=Mr. Polite]. but in reality everything, including things in Linux, isn't free.[/QUOTE]

Ever heard of the GPL?

---

### Post by zenlunatic on 2006-06-03
[QUOTE=azz]Ever heard of the GPL?[/QUOTE]

Wouldn't be suprised if he said no.

---

### Post by Mr. Polite on 2006-06-03
[QUOTE=azz]Ever heard of the GPL?[/QUOTE]

Yes. Just recently read up on GPLv3... might be the perfect license. The word everything though, as in all inclusive; means that while most of whats included is free (freedom), there are somethings that are not. 

For instance; Sun Java, which is free (Guacamole), is not free (freedom).

My original statment stands unretracted. Everything, including in Linux; is not free.

---

### Post by az on 2006-06-03
[QUOTE=Mr. Polite]means that while most of whats included is free (freedom), there are somethings that are not. 

For instance, Sun Java, which is free (Guacamole) is not free (freedom).[/QUOTE]


Yeah.  And everything that ships with ubuntu and is in the Main and Universe repos are free-libre, with the exception of the linux-restricted-modules packages.


zenlunatic:  Remove any and all linux-restricted-modules packages you have listed as installed in synaptic.  You are good to go.

---

### Post by zenlunatic on 2006-06-03
[QUOTE=azz]zenlunatic:  Remove any and all linux-restricted-modules packages you have listed as installed in synaptic.  You are good to go.[/QUOTE]

I would if I KNEW THE NAME OF THE PACKAGES :confused: Can someone help me figure this out.  See above post.

---

### Post by Mr. Polite on 2006-06-03
[QUOTE=azz]...everything / / except...[/QUOTE]

I understand, but when you follow the word everything with an exception, it means *not* everything.

---

### Post by az on 2006-06-03
[QUOTE=zenlunatic]I would if I KNEW THE NAME OF THE PACKAGES :confused: Can someone help me figure this out.  See above post.[/QUOTE]
"linux-restricted-modules-386" for example.

or

" linux-restricted-modules-2.6.15-23-386"

---

### Post by zenlunatic on 2006-06-03
WTF!

```
jhenn@jhenn-laptop:~$ sudo apt-get remove ttf-gentium
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ttf-gentium xubuntu-desktop

```

So you can't remove those fonts without totally removing xubuntu-desktop?  STUPID! Ubuntu doesn't even let you reclaim your freedom.

---

### Post by zenlunatic on 2006-06-03
```
root@jhenn-laptop:~# vrms
            Non-free packages installed on jhenn-laptop

linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
ttf-gentium               Gentium TrueType font

  4 non-free packages, 0.5% of 735 installed packages.
root@jhenn-laptop:~# dpkg -l linux-restricted-modules-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-restrict 2.6.15.11-1    Non-free Linux 2.6.15 modules on 386
ii  linux-restrict 2.6.15.22      Restricted Linux modules on 386.
ii  linux-restrict 2.6.15.11-1    Non-free Linux 2.6.15 modules helper script

```

Can someone please tell what are/ how to find out what the actual names of these packages are so I can apt-get remove them?  Thanks. ](*,)

---

### Post by Corvillus on 2006-06-03
Just maximize your terminal window before doing the dpkg -l and you should be able to see the full names of the packages, at least that works for me anyway.

---

### Post by meng on 2006-06-03
[QUOTE=zenlunatic]So you can't remove those fonts without totally removing xubuntu-desktop?  STUPID! Ubuntu doesn't even let you reclaim your freedom.[/QUOTE]

Hey don't lose your cool. That package is just a convenient way of installing everything that most folks want for xubuntu - it's kind of a dummy package. If you have installed everything and want to remove just a few components, then you can safely remove xubuntu-desktop and xfce will still be there. As quoted in the package description (copy/paste from synaptic):

> ]Xubuntu desktop system
This package depends on all of the packages in the Xubuntu desktop system

It is safe to remove this package if some of the desktop system packages are
not desired.

---

### Post by zenlunatic on 2006-06-03
[QUOTE=Corvillus]Just maximize your terminal window before doing the dpkg -l and you should be able to see the full names of the packages, at least that works for me anyway.[/QUOTE]

ert wrong! nice try though. [-(

---

### Post by meng on 2006-06-03
Synaptic package manager is one way to get the answer, anyway here it is:

linux-restricted-modules-2.6.15-23-386
linux-restricted-modules-386
linux-restricted-modules-common

---

### Post by zenlunatic on 2006-06-03
[QUOTE=meng]Synaptic package manager is one way to get the answer, anyway here it is:

linux-restricted-modules-2.6.15-23-386
linux-restricted-modules-386
linux-restricted-modules-common[/QUOTE]

Thank you. :KS  Hope my system boots now :twisted:

---

### Post by zenlunatic on 2006-06-04
Anyone know how to do this without synaptic?  I want to do a server install on my old laptop and I don't plan on installing synaptic.

---

### Post by meng on 2006-06-04
(sudo) apt-get remove (whatever packages you want to remove)

---

### Post by zenlunatic on 2006-06-04
no rly?

anyway i need to know how to find the exact names of the packages that i want to remove since dpkg -l and vrms don't tell me the true names of the packages.  so far I was only able to do this with synaptic. ](*,)

---

### Post by meng on 2006-06-04
The packages are the ones I listed, three of them.

---

### Post by shamrock_uk on 2006-06-04
I'm sure you're managing to make this harder than it is! :p

dpkg -l *does* give the complete package name for me. Are you using a tiny terminal or something?

```
sudo dpkg -l | grep restricted
```

Run that in a gnome terminal.



If you don't know the exact names of the packages, you can operate on wildcards. 

The following:

```
sudo apt-get remove linux-restricted-*
```

will do the job for you. 

You may also want to get rid of *linux-386* or *linux-686* as I believe someone mentioned that these metapackages will pull in the latest restricted modules next time there's an upgrade (although of course, it will ask for confirmation). Removing them will stop that, although you'll have to upgrade your kernel manually then (not that there should be a new one anytime soon now Dapper is stable).

---

### Post by jBilbo on 2006-06-13
Do not remove ttf-gentium!

It's Free (as Freedom). It was relicensed months ago with OFL (Open Font License), an official FSF valid free license. More info:

[http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium)
[http://www.fsf.org/licensing/licenses](http://www.fsf.org/licensing/licenses)

---

