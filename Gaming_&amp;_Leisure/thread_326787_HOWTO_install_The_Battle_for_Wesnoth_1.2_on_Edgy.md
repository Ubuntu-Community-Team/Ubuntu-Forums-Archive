---
title: "HOWTO install The Battle for Wesnoth 1.2 on Edgy"
date: 2006-12-28
forum: Gaming &amp; Leisure
---

### Post by finferflu on 2006-12-28
Hi all, thanks to the [suggestion of mikl]("http://ubuntuforums.org/showthread.php?t=304143"), I'm now posting this short howto.

I've just successfully installed The Battle for Wesnoth 1.2, released a couple of days ago, from the Debian repositories on my Edgy machine (but I bet it would work on other versions as well, correct me if I'm wrong).

First of all you need libsdl-net1.2, and maybe also libsdl-mixer1.2 so:

```
sudo aptitude install libsdl-net1.2
```
and to make sure you have everything, just see if libsdl-mixer1.2 gets installed, otherwise you have no problem:
```
sudo aptitude install libsdl-mixer1.2
```

Now just go to [http://ftp.us.debian.org/debian/pool/main/w/wesnoth/](http://ftp.us.debian.org/debian/pool/main/w/wesnoth/) and download the files for your architecture, in my case:

wesnoth-ei_1.2-1_all.deb
wesnoth-httt_1.2-1_all.deb
wesnoth-music_1.2-1_all.deb
wesnoth-server_1.2-1_i386.deb
wesnoth-trow_1.2-1_all.deb
wesnoth_1.2-1_i386.deb         
wesnoth-tsg_1.2-1_all.deb
wesnoth-data_1.2-1_all.deb     
wesnoth-ttb_1.2-1_all.deb
wesnoth-editor_1.2-1_i386.deb  
wesnoth-utbs_1.2-1_all.deb

I used the [DownThemAll]("http://www.downthemall.net/") extension for Firefox, which makes things a lot easier.

Then open a terminal and cd to the directory where you downloaded the files, and run:
```

sudo dpkg -i wesnoth*.deb
```

And that's it! Brand new version of The Battle for Wesnoth on your machine!

Enjoy! 8)

---

### Post by hikaricore on 2006-12-28
Thanks for pointing this out, mine was just a tad outdated lol.

---

### Post by finferflu on 2006-12-28
> **hikaricore said:**
> Thanks for pointing this out, mine was just a tad outdated lol.

lol! There are [very very interesting new features]("http://www.wesnoth.org/start/1.2/#game") in the current version!! :D

---

### Post by meborc on 2006-12-28
hmm... i never was good at this game, maybe i need to try it again just to make sure ;)

---

### Post by paridoth on 2006-12-28
arg! i just got done spending an hour compiling it! >.< thanks for this though, ill use it on my other machines

---

### Post by meborc on 2006-12-29
played it... got beaten in tutorial... :-#  i really can't play this game :-k

---

### Post by po0f on 2007-01-08
Someone in #ubuntu suggested I play this game.  I didn't use the *.debs provided in this thread, I compiled it from source.

All I can say is I am addicted.  :)  I have played through the first three campaigns and am working on beating the fourth.

---

### Post by finferflu on 2007-01-08
Exactly, I belive this is one of the most beautiful & addicting games I've ever played. And the most fascinating thing is that it's GPL'd, I struggle to believe that :D

---

### Post by defe007 on 2007-01-10
Just for some who might have the same problem, you may also need to install libsdl-mixer1.2.

---

### Post by finferflu on 2007-01-10
> **defe007 said:**
> Just for some who might have the same problem, you may also need to install libsdl-mixer1.2.

Thank you, I've just edited my first post :)

---

### Post by Sammi on 2007-01-26
Is there any game feature difference between downloading these debs and compiling from source?

---

### Post by po0f on 2007-01-26
Sammi,

A real man would compile it from source.  ;)

I honestly don't know, if I come across any program that doesn't have an official Ubuntu deb in the repos, I compile from source.

---

### Post by Sammi on 2007-01-26
> **po0f said:**
> Sammi,

A real man would compile it from source.  ;)

I honestly don't know, if I come across any program that doesn't have an official Ubuntu deb in the repos, I compile from source.
I did compile it and it was a piece of cake. The instructions on the official Wesnoth page are clear and simple. I have even taught myself how to use checkinstall, which I used to install Wesnoth 1.2.1 with sucess. Brilliant :KS

---

### Post by finferflu on 2007-01-27
> **Sammi said:**
> Is there any game feature difference between downloading these debs and compiling from source?

The difference is not in game features, those are present only in different versions, not in different ways to install the same thing. The only thing is that debs save you a lot of time, manage your dependancies, and make it easier to upgrade or uninstall the game. I think that's pretty much it...

> **po0f said:**
> Sammi,

A real man would compile it from source.  ;)


I'm a puppet! :P

---

### Post by finferflu on 2007-02-07
I just want to point out that the Edgy debs for version 1.2.1 are out on [getdeb]("http://www.getdeb.net")!

Have fun!

---

### Post by mikl on 2007-02-17
That's good, since I managed to get throttled by one of the Ubuntu devs for suggesting this :) 

No, seriously, he just pointed out that although Debian and Edgy is binary compatible, Feisty is probably going to break that, since Feisty uses a newer version of some library or other...

So while this trick works for now, beware that it might not do so always. And don't use it for anything critical ;)

---

### Post by Perfect Storm on 2007-02-17
That's why we have howto compile wesnoth on Ubuntu Gaming Arena ;)
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63)
Then no worry about compatiblity or package hacking.

---

### Post by finferflu on 2007-02-17
Thanks for the info guys! I'll keep that in mind. 
So, that means that even though I'm gonna download something for Feisty from getdeb, will that not work?

---

### Post by chinocracy on 2007-02-23
Some other dependencies I discovered, though it's for the 1.1....reverted+something version:

```
xfs
ttf-sazanami-gothic
```

I think this is why my Wesnoth installation keeps crashing upon my just opening it...

EDIT: Nope, it still crashes upon double-clicking the menu icon. I uninstalled it first, and I guess I should get the newest version. Things is, I wonder if it'll work for Dapper.

---

### Post by mikl on 2007-02-23
> **finferflu said:**
> Thanks for the info guys! I'll keep that in mind. 
So, that means that even though I'm gonna download something for Feisty from getdeb, will that not work?

The packages on GetDeb are built for Ubuntu, so no problems there - just make sure you download packages for the right _version_ of Ubuntu ;)

---

### Post by chinocracy on 2007-02-26
By the way, thanks for the info about Getdeb.net. Very helpful resource.

---

### Post by petersjm on 2007-02-26
Hmm. Am I doing something wrong? Installed Wesnoth and it loads fine, I can play through the tutorial, but when I click "campaign", nothing happens... I didn't follow the howto at the top of this thread. I installed it a few weeks ago, but can't remember what I did to install. Maybe I missed a deb or something?

---

### Post by finferflu on 2007-02-26
Just try to reinstall it with the packages provided by getdeb.net, and see what happens... maybe there's a more technical solution, but that's the quickest thing that comes to my mind...

---

### Post by ViGiLnT on 2007-02-26
> **petersjm said:**
> Hmm. Am I doing something wrong? Installed Wesnoth and it loads fine, I can play through the tutorial, but when I click "campaign", nothing happens... I didn't follow the howto at the top of this thread. I installed it a few weeks ago, but can't remember what I did to install. Maybe I missed a deb or something?

You can't load a campaign because you haven't got any installed...

This are all the files available for Battle for Wesnoth on ubuntu repos:

```
vigilnt@i-laptop:~$ apt-search wesnoth
wesnoth - fantasy turn-based strategy game
wesnoth-data - data files for Wesnoth
wesnoth-editor - map editor for Wesnoth
wesnoth-ei - Eastern Invasion official campaign for Wesnoth
wesnoth-httt - Heir to the Throne official campaign for Wesnoth
wesnoth-music - music files for Wesnoth
wesnoth-server - multiplayer network server for Wesnoth
wesnoth-trow - The Rise of Wesnoth official campaign for Wesnoth
wesnoth-tsg - The South Guard official campaign for Wesnoth
wesnoth-ttb - A Tale of Two Brothers official campaign for Wesnoth
wesnoth-utbs - Under the Burning Suns official campaign for Wesnoth

```

You need to get the ones that have "campaign" on the description: go to synaptic or terminal and get them. Then you'll have campaigns available.

---

### Post by chinocracy on 2007-02-27
No wonder mine may not work... I set my monitor resolution on 800x600, since it gets triple images when I go 1024x768, but since Wesnoth by default runs at 1024, then it won't load. Oh well.

---

### Post by petersjm on 2007-02-27
Thanks finferflu and ViGiLnT - I uninstalled what I had and reinstalled using the howto by the OP. Works perfectly now. Now all I need to do is figure out how to win it ;)

---

