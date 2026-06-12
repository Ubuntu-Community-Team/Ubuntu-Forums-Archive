---
title: "Can you upgrade to Dapper from Breezy?"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Swiss on 2006-02-28
Can you upgrade to Dapper from Breezy?

---

### Post by jstueve on 2006-02-28
short answer: yes
long answer: it depends... maybe...

backups are key... especially of any valuable data, and having home on a separated partition is helpful.

the steps:
edit /etc/apt/sources.list 
replace breezy with dapper
save

sudo apt-get update
sudo apt-get dist-upgrade

(go get some coffee/tea)

---

### Post by Ramses de Norre on 2006-02-28
Are settings saved? Like your background, themes, taskpanes, gdesklets, programs and all your files etc.
Are there advantages when you do a fresh install of dapper?

---

### Post by jstueve on 2006-02-28
the dist-upgrade doesn't effect your home directory... 

though some configurations in some applications may require some changes... 

like any other upgrade the caveats are highly individual, and your problems won't be exactly the same as anothers.

---

### Post by Swiss on 2006-02-28
[QUOTE=Ramses de Norre]Are settings saved? Like your background, themes, taskpanes, gdesklets, programs and all your files etc.
Are there advantages when you do a fresh install of dapper?[/QUOTE]


Yes, I need to know this as well!

---

### Post by Grey on 2006-02-28
My desktop has been running the same install of Ubuntu since 4.10.  

I upgraded to 5.04 about a month before it was officially released.  I encountered some problems,  but nothing too terrible.  The biggest problem I faced was that my X Server wouldn't start back up until I made some changes to my configurations.

I upgraded to 5.10 about a month before it was released.  It completely broke my Atheros Wifi card, and rendered the system unusable with it plugged in (crashing, freezing).  I was never able to get it working again.  I switched to my RT2500 card, and built-in ethernet.  There were also some more minor problems with the upgrade... but I can't honestly remember them off the top of my head.  Something to do with drive permissions, and something else.

I upgraded to 6.04 day before yesterday.  The atheros card is long since removed, so I don't know if that's working or not anymore.  However, built-in ethernet is no longer working.  It shows up as eth0_clas, and doesn't work.  Other than that, the upgrade seems to have fixed almost everything that was wrong in breezy.

I upgraded my laptop from 5.10 to 6.04 about 2 weeks ago.  GtkWifi has problems with 6.04, and drops my connection for a split second about every 30 seconds.  (I am told this is to do with probing for new networks and being connected at the same time.  My wireless card (IPW2200) used to support this, but doesn't appear to any longer).  Other than that... it's working fine.  Better than Breezy.  Standby works well, and the bootup and shutdown process is MUCH faster.

I usually replace my custom configurations with defaults when upgrading.  As a result, I lose my changes to things such as my grub screen, login screen, and things like that.  But all my user applications remember me well, and rarely need any additional reconfiguring.

As far as the advantage of a fresh install?  Things tend to work just a tiny bit better.  My laptop is fairly new, and its first install was Ubuntu 5.10 (colony 4).  It was a bit different from my desktop's version of 5.10, but (again), I don't remember any specific details.  I just found that some things worked just fine on my laptop that had been broken for some time on my desktop.

---

### Post by Ramses de Norre on 2006-02-28
This sounds pretty scary to me.. I'm totally dependend of an atheros wifi card for my internet..
Guess I'll stay with breezy for a while and make a fresh install with dapper some time (or maybe I'll try the dist-upgrade first).

---

### Post by Swiss on 2006-02-28
I tried to run apt get update and this is what it spit back out at me:


Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) Dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Dapper-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) Dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Dapper-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) Dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Dapper-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_Dapper_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_Dapper_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) Dapper/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_Dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) Dapper/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_Dapper_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by jstueve on 2006-02-28
try 'dapper'

yes case matters ... you have to be able to see each URL, you can test each URL in Firefox to make sure you can see the dirctory that is being updated.

---

### Post by hashinclude on 2006-04-23
I originally started off with 5.04 (Hoary), and did an apt-get dist-upgrade to 5.10 breezy once that was out (stable).

I decided to move to Dapper (beta), so made the necessary changes in /etc/apt/sources.list, did a update, and dist-upgrade.

Once that was done, however, my X refuses to start.

which X gives my /usr/bin/X, but even just manually starting vanilla X doesn't work (and produces ZERO output on the console)

Any ideas what may have gone wrong, and how (if possible) to downgrade? (I always have the install 5.10 option, but would rather not use it ;)

~hrishikesh

---

### Post by ronmarley1 on 2006-04-23
[QUOTE=jstueve]short answer: yes
long answer: it depends... maybe...

backups are key... especially of any valuable data, and having home on a separated partition is helpful.

the steps:
edit /etc/apt/sources.list 
replace breezy with dapper
save

sudo apt-get update
sudo apt-get dist-upgrade

(go get some coffee/tea)[/QUOTE]

As an alternative, I followed the steps here (you do not need to manually edit your sources list with this process):
[http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)
Type this in a terminal and it will ask you to upgrade:
gksudo "update-manager -d"

---

### Post by joe_bling on 2006-04-23
Ronmarley (or anyone?), does the upgrade process you referenced preserve all of my data, programs, T-bird email and FF settings? (I am running TB and FF 1.5) I understand a backup is preferred, but I want t know what I'm getting into and how much restoration/rebuilding I'm in for.

Thanks.

---

### Post by ronmarley1 on 2006-04-24
[QUOTE=joe_bling]Ronmarley (or anyone?), does the upgrade process you referenced preserve all of my data, programs, T-bird email and FF settings? (I am running TB and FF 1.5) I understand a backup is preferred, but I want t know what I'm getting into and how much restoration/rebuilding I'm in for.

Thanks.[/QUOTE]
Hi Joe,
You should be OK if you do an upgrade.  For future reference, if you make your /home on a seperate partition, you will be even better off.

---

### Post by m.musashi on 2006-04-24
[QUOTE=ronmarley1]As an alternative, I followed the steps here (you do not need to manually edit your sources list with this process):
[http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)
Type this in a terminal and it will ask you to upgrade:
gksudo "update-manager -d"[/QUOTE]
Can you do this from a server install of Breezy? I tried and got the error```
-bash: gksudo: command not found
```
Thanks.

---

### Post by Ramses de Norre on 2006-04-24
Are you on kde? Try kdesu or kdesudo then instead of gksudo, I think one of them should be installed by default. On gnome gksudo should be installed by default.

---

### Post by m.musashi on 2006-04-24
[QUOTE=Ramses de Norre]Are you on kde? Try kdesu or kdesudo then instead of gksudo, I think one of them should be installed by default. On gnome gksudo should be installed by default.[/QUOTE]
Thanks for the reply.

I did a server install of Breezy so I assume that would gnome-centric but without gnome actually being installed would that mean this isn't possible?

I tried the dist-upgrade after changing all breezy to dapper in sources.list but that also produced a bunch of "failed to fetch" errors.

---

### Post by Ramses de Norre on 2006-04-24
You don't have a GUI installed? Then there is no need for gksudo, it is a program to load graphical programs (eg. synaptic) through sudo. So you'll need to use a command line tool (apt-get will be the best fit I guess).

---

### Post by m.musashi on 2006-04-24
No. No GUI. I'm attempting to recreate a bug and I need to do a server install of breezy and then dist-upgrade. I'm not having any luck on the dist-upgrade so I thought I'd try update-manager but that also isn't working...yet. I'll install it and see what happens. If it's a GUI app then maybe it won't work for me either.

Thanks.

---

### Post by joe_bling on 2006-04-25
[QUOTE=ronmarley1]Hi Joe,
You should be OK if you do an upgrade.  For future reference, if you make your /home on a seperate partition, you will be even better off.[/QUOTE]

Thanks Ronmarley! I went ahead and upgraded w/o any serious issues (wifi is now broken, should be an easy fix).

Hope things are well in Cleveland, I am a former Clevelander. Go Tribe!

---

### Post by phorque on 2006-04-25
How hefty is the downloading doing it the "from Breezy to Dapper" way? I'm tempted to upgrade this way eventually but dunno if I can spare mega-bandwidth on it.

---

### Post by m.musashi on 2006-04-25
[QUOTE=phorque]How hefty is the downloading doing it the "from Breezy to Dapper" way? I'm tempted to upgrade this way eventually but dunno if I can spare mega-bandwidth on it.[/QUOTE]
I tried this way back when I first stated playing with Dapper and it took about 3 hours on my DSL connection (time includes the whole process not just download). I don't remember how large the download was but 300-400MB would be my guess. For what's it's worth, the upgrade didn't work so well and I ended up doing a clean install. Of course that was back on flight 3 and things might work a lot better when it's finally released.

---

### Post by phorque on 2006-04-25
Thanks for the heads up. I also think a clean install will probably be for the best. I'll get a CD off one of my friends or just wait for the official release, methinks.

---

### Post by ronmarley1 on 2006-04-25
[QUOTE=joe_bling]Thanks Ronmarley! I went ahead and upgraded w/o any serious issues (wifi is now broken, should be an easy fix).

Hope things are well in Cleveland, I am a former Clevelander. Go Tribe![/QUOTE]

Did you get the WiFi fixed?  If not, maybe I can help...
Hope you are warm in NC, it's 39 and rain here!

---

### Post by joe_bling on 2006-04-25
[QUOTE=ronmarley1]Did you get the WiFi fixed?  If not, maybe I can help...
Hope you are warm in NC, it's 39 and rain here![/QUOTE]

I haven't fixed wireles yet, I'll work on it this evening and start a new thread if I run into problems. I appreciate your offer of help.

Yeah it's warm! Actually I just moved 2 weeks ago (lived in Cleve Hts), everything is new here and the roads are in nice shape.;)

---

### Post by joe_bling on 2006-04-25
[QUOTE=phorque]How hefty is the downloading doing it the "from Breezy to Dapper" way? I'm tempted to upgrade this way eventually but dunno if I can spare mega-bandwidth on it.[/QUOTE]

My download was 605MB total. Guess it varies based on what packages you have installed. The entire process took around 90 minutes, and that was downloading at 500-600kbps.

---

### Post by phorque on 2006-05-07
[QUOTE=joe_bling]My download was 605MB total. Guess it varies based on what packages you have installed. The entire process took around 90 minutes, and that was downloading at 500-600kbps.[/QUOTE]

I have the Beta install CD now and might use that to upgrade from breezy. I just hope that when I make the plunge I don't end up with everything broken.

---

