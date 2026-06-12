---
title: "Are we forced to switch distros?"
date: 2008-12-17
forum: General Help
---

### Post by pikaia on 2008-12-17
Hey everyone.

I have a few old laptops and desktops that I clean up and give away, with a couple I keep (and bug my girlfriend with).  But I have an old Thinkpad 600X that I love, and dual boot Feisty and XP on.  I've distro hopped so many times on this machine to get a decent setup with a reasonable boot time and responsiveness yet without losing too much of the 'modern' look and feel.  I think Feisty is the perfect fit.  It might have some bugs here or there, but nothing that can't be fixed.  I like Dapper, but it goes only so far and is lacking a bit in the area of completeness as far as wireless connectivity and look.  Debian is good, I've tried doing a minimal install and add packages by hand, but for the life of me I can't get it right.  It won't open the eth0 connection on boot and an eth0 up command doesn't do the job.  Plus I can't figure out how to get a boot splash to load... So with all this constant fuss, I tried Feisty.  It has that in-between feel; lightweight enough to run smoothly on the 600Mhz/512MB RAM and no fusses with internet connectivity (network-manager-gnome) or moderness of look.

Ok so some of this is trivial.  But going through all this for an intermediately skilled person to try and build his own debian OS is still extremely frustrating.  I'm sure I'll try it again, but right now Feisty works until I finish my Graduate degree next year.

So Feisty has lost its support, and Dapper will next year.  Adding Debian repositories is not recommended for updates, and I can't get them to work anyway(can't find gpg keys).  So what about those of us that use older versions of ubuntu for our older hardware?  Hardy is WAY TOO BIG, and bulky.  Dapper uses about 65MB, Feisty uses about 80 MB of RAM after boot.  Hardy uses around 130-150.  

Is there other options in the debian/ubuntu world?  I've tried Puppy and Slitaz and DSL and a pile of others, but I like Ubuntu and tend to prefer Gnome over other WMs.  

So what options do we have...

Sorry about the long diatribe, but I really could use some help in figuring out which is the best way to go... retry Debian?  Some of us don't need bigger better and bleeding edge.

Thanks.

---

### Post by aheckler on 2008-12-17
Well, asking for a lightweight distro that uses GNOME is difficult. You might look into Xubuntu, which uses Xfce. It's what I use when I need to go lightweight.

---

### Post by kanikilu on 2008-12-17
I was going to suggest the same thing, and also point out that if you want to use Gnome, you have to sacrifice some system resources - I don't think there's any getting around that. On my box right now, the combination of nautilus, gnome-settings-daemon, and gnome-panel are taking over 100MB of memory. Not to point fingers or anything, but maybe you're barking up the wrong tree...perhaps it's not Ubuntu as such that has become more resource heavy over the past 2 years, but rather Gnome?

If you want to go minimal, start with Xubuntu as it feels very familiar compared to Gnome. If that's still too much overhead, maybe consider something like LXDE, E17 or even fluxbox for the ultimate in minimalism.

You could also try installing the base system with the [minimal cd image]("https://help.ubuntu.com/community/Installation/MinimalCD") and tailoring the system to your needs from there, but I think as soon as you include Gnome, you'll end up back where you started.

---

### Post by scouser73 on 2008-12-17
It sounds as if you've already made your choice with Feisty, I always like to try new O/S's out but I always come back to Ubuntu, at the moment I'm using Intrepid Ibex which is great for me.

I would say that if you're happy with Feisty then stay with it, as there's nothing worse than configuring a new system to find out that you don't like it or could have easily managed with the old system.

As a note though, OpenSuse 11.1 comes out today, and it will be available from 1PM GMT, which is worth a look I suppose.

[http://www.opensuse.org/en/]("http://www.opensuse.org/en/")

Anyway, good luck with whatever you choose to use.

---

### Post by kerry_s on 2008-12-17
you should try debian again, i don't understand why you would lose internet if it worked during the install.
i'll talk you through it: :p

grab the net installer:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

at package selection uncheck the desktop.
log in as root
apt-get install xorg lxde
reboot (press ctrl+alt+delete)

that's it very simple. lxde is a window manager(openbox) but it's setup in such a way it's lighter than any other desktop.
you can check it out here:
[http://lxde.org/](http://lxde.org/)

once you have lenny installed, you should never have to install again, everything is just a "apt-get upgrade" away.

---

### Post by pikaia on 2008-12-18
First of all thanks for all the input.  

Now let me say that I've tried tons and tons of distros, probably in the 30-40 range.  I like PCLinuxOS (PCFluxbox is great), and Mandriva, but started with Ubuntu and keep coming back to it.  I like Debian, but have had a heck of a time configuring it properly, with network manager and various nonfree codecs.  And I gotta say, as cheesy as it sounds, I prefer a boot splash.

I've tried several Window Managers, Fluxbox, KDE, Gnome, Xfce and LXDE.  I like fluxbox (especially the PCLinux version, its very well done) and LXDE.  But LXDE is still a bit buggy for me to use regularly.  So I prefer Gnome.  I'm not looking to get down to 40MB of RAM using GNOME.  But sub-100MB at idle isn't asking much.  I've exchanged Thunar for Nautilus which saves and use Opera nearly exclusively.

So I've been doing the low resource distro thing for a while.  But what bugs me is that these early Ubuntu versions (Dapper and Feisty mostly, Edgy's got a 'middle child syndrome' thing going on.) are really key, in that they hit the niche of modern needs, with modest (relatively) resources.  But we're losing these because their being fazed out.  

So, I prefer Gnome, Debian and light resources.  I've actually tried Debris Linux, which is based on Gutsy and BeaFanatix, and is a great little distro.  And as I said, I'll probably end up building my own Debian again, but I couldn't get the net install disc to work, and using installed Etch and a half twice, once as a full install, which was nearly as bloated as Ubuntu, installing OpenOffice and various useless tools to me (Gaim, pidgin, burner tools, etc)  The second as a minimal install without a desktop and couldn't get the network up, (well I could, but had to "eth0 up eth0 down eth0 up" after every boot.

I'm just wondering where those of us who like the older versions of Ubuntu for their out of box usefulness will do when its all been fazed out?  I'm still trying to figure out how to update my Feisty install I made on Thanksgiving...

Thanks again.

EDIT: I also run Hardy on my Desktop, but again, for the old hardware I have sitting around, I like the older versions of Ubuntu over others that are less intuitive to me.  I'm sure I'll get around to using Arch and BSD sooner or later, but right now I just want things to be manageable.  I'll get more invested as soon as I have time.  I've already spent WAY too much time installing/configuring/uninstalling-repeat... I just want one that works right now.

---

### Post by AmyRose on 2008-12-18
> **pikaia said:**
> Hardy is WAY TOO BIG, and bulky.  Dapper uses about 65MB, Feisty uses about 80 MB of RAM after boot.  Hardy uses around 130-150.I run Hardy on less powerful hardware than you have here, GNOME included. You just can't expect everything to be perfectly snappy like it is on newer hardware without making sacrifices--it's a tradeoff.

---

### Post by pikaia on 2008-12-18
I understand its not going to be super snappy, but I can expect some responsiveness.  I get it with the earlier versions... thats all I expect.  I turn off the services I don't need.  I don't think I have outlandish expectations, afterall I do prefer a 10 year old laptop over my 2 year old one...

---

### Post by zvacet on 2008-12-18
@** pikaia**

> I'm still trying to figure out how to update my Feisty install I made on Thanksgiving...

You can upgrade via net or with alternate CD to Gutsy.Read [this]("https://help.ubuntu.com/community/GutsyUpgrades") to do it right.You don´t leave much of choice,because you want Gnome and lightweight desktop in same time.Install xubuntu-desktop as it is explained [here.]("http://psychocats.s465.sureserver.com/ubuntu/purexfce")If this doesn´t satisfied your needs try PCLOS again.

---

### Post by kerry_s on 2008-12-18
> **pikaia said:**
> I understand its not going to be super snappy, but I can expect some responsiveness.  I get it with the earlier versions... thats all I expect.  I turn off the services I don't need.  I don't think I have outlandish expectations, afterall I do prefer a 10 year old laptop over my 2 year old one...

actually you are, the newer the software the more resources it needs. i understand you liking the old stuff, but what you want to do with it and the limitations of the hardware have to work together.

given your specs "600Mhz/512MB RAM" you should be able to run what ever you want comfortably.

my laptop is 10 years old 450mhz 256mb ram, it's the only working computer i have right now. like you i want speed, so i built mine from a base install up, i use some light programs, but the rest is standard, firefox, openoffice...

anyways the thing you got to ask yourself is "do you really need it?" or "i just want it!".

cause all you really need is just enough to get the job done and any window manager can give you a workspace to launch a program, the difference is balance, how much resources the work area uses, compared to the program you want to use "do you really care whats sitting behind what your working with?".

here's what i see:

---

### Post by eye208 on 2008-12-18
Install the latest Ubuntu release as a command line system and then apt-get install the applications you need. The package manager will automatically add the components required by these applications (and nothing else). It doesn't get any more lightweight than this.

This is much better than using an obsolete version of the system.

---

### Post by mikjp on 2008-12-18
I would stick with Debian. Or try Slackware, Vector or Zenwalk instead.

---

### Post by pikaia on 2008-12-18
Wow, I hope I haven't upset too many people.  

I don't think I've expressed myself very clearly... There seems to be this divide in the community.  What I see as the consumer minded faster processor/more RAM, better video card (Kubuntu, Linux Mint), or extremely low resource, limited Window Manager for very old systems (Sawfish/FVWM/Fluxbox).  But I feel that most people need/want a system where the interface looks decent (no desktop effects, but not win95 either), feels comfortable and can do the standard tasks of internet, document work and listen to music... And I feel its that lower-middle range thats being left behind.  The group that fits somewhere above the DSL/DeLi camp and beneath where Ubuntu/Sabayon/Linux Mint is.  Even Xfce is a bit bulkier now and running Xubuntu draws more resources than Dapper (w/GNOME).  So my question was what alternatives are there?  Especially for newer users with less time and desire to learn (break/fix/rebreak) on their hands (which is where I feel the CLi Debian is).  

I think getting a base Gnome desktop with firefox and a useful network connection isn't too much to ask and bringing the RAM use down somewhere between 70-100 @ idle.  I've done the base Hardy install and apt-get all the packages I need, but it never seems to run as smoothly as a full install that I remove packages from.  Its odd, but there are always hiccups... like it'll take 2 minutes to boot, or won't reset properly, or uses more RAM or is constantly ramping the CPU to 100%...  

I know I can upgrade my feisty through the repos, but I just want stability out of the system at this point.  I don't want bigger and better.  So taking a functional system and constantly upgrading isn't what I'm looking for, its more about getting upgrades (fixes) for the things that need it. 

Hopefully this gets my point across better... but maybe Zenwalk/Slack is where that niche will be filled.  I know its faster, but I was hoping to find it in a Debian based distro.  Most people don't need a Dual core processor and 2 GB of RAM to do what they need/want.  But they have to, to keep up with the OS requirements/demands (Vista).  I'm worried the same thing is happening with Ubuntu.  (that is not an insult, I love the OS, but an observation of what I see happening)

---

