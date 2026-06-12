---
title: "Installed PKGS wont Run"
date: 2005-06-24
forum: Desktop Environments
---

### Post by 1hutchy on 2005-06-24
I think this is one of those questions alot hate to read , But one of the problems I have had every time I have tried Ubuntu is that alot of Packages installed through Apt dont show up on any list which is not the  problem I'm worried about as it can be easy to addthem  to list  later, but when I try & run some of them like Jabber ,3Dchess etc etc either won't run or I get a error saying  "bash: jabber: command not found" and so forth , so my question is what does everybody else do when this happens as it seems to happen reguraly especially with Debian distros mainly I have found, It happened with Kanotix but not as often as with Mepis which I thought was & is a Great Distro one the best in Fact. Why cant apt install PKGS properly on Ubuntu, I think Ubuntu is good ,but I dont find it happens when using Apt on RPM distros like Fedora etc, I want make it clear I am not complaining so to speak as I am just trying to find out if there is a way to get these PKGS to run etc, Thanks

---

### Post by 1hutchy on 2005-06-24
I hope I dont get so called Hate mail 4, this but I think I will go back to mepis, The only decent Debian Distro on the planet that works properly. I really really really thought that Ubuntu would have improved enough by the time this version of Hoary 5.4 coming out that this big problem of so many PKGS not installing properly would of been fixed, why put them in the apt repositories if they wont RUN on Ubuntu, and I have had Ubuntu installed on 3 different PCs including AMD64 which I am using now , I am just tired of downloading PKGS from apt only 2 find they dont run . not only does mepis have more software 2 choose from but most of them seem to run as well with out rebooting,and I very rarly seemed to have to manually add the name & caption of PKG to add it to the menu etc. the only good thing I found about Ubuntu is the fact they added Gnome 2.10 before any other debian distro had the courage & it works well, & you can also install KDE3.4 if wanted unlike others which is hard to believe as it seems stable enough on all the other Distros I have tried,- ](*,)  AnyWay I feel better Now , I just want to add I am one of those who know & remember the big efforts people put into creating a distro but Ubuntu just needs improving in this area &maybe a couple of others

---

### Post by alastair on 2005-06-24
So, you install a package - e.g. package "package-A". But get a "command not found" when run.

If this happens to me I see what was installed when I installed the package i.e.

dpkg -L package-A

This will list all the files installed with package "A". Perhaps you can spot where the executable is. Or what it is called.

Alternatively ...... switch distributions.

---

### Post by 1hutchy on 2005-06-25
Thanks Alastair for trying to help me on this one, if I can find a easy solution to this problem that occurs every now and then I would be inclined to stick with it, which is why I started this post, but I might need a it of help. here is the status to that command you gave me to hopefully solve this ,as surely there must be a lot of newbies out there that wouldnt have a clue what to do when this happens as it can be just as hard to google 4 a answer, . AnyWay here is my output   
  dpkg -L jabber
/.
/etc
/etc/jabber
/etc/jabber/jabber.d
/etc/jabber/jabber.xml
/etc/jabber/jabber.cfg
/etc/init.d
/etc/init.d/jabber
/etc/logrotate.d
/etc/logrotate.d/jabber
/usr
/usr/sbin
/usr/sbin/jabberd
/usr/lib
/usr/lib/jabber
/usr/lib/jabber/pthsock
/usr/lib/jabber/pthsock/pthsock_client.so
/usr/lib/jabber/jsm
/usr/lib/jabber/jsm/jsm.so
/usr/lib/jabber/xdb_file
/usr/lib/jabber/xdb_file/xdb_file.so
/usr/lib/jabber/dnsrv
/usr/lib/jabber/dnsrv/dnsrv.so
/usr/lib/jabber/dialback
/usr/lib/jabber/dialback/dialback.so
/usr/share
/usr/share/doc
/usr/share/doc/jabber
/usr/share/doc/jabber/README
/usr/share/doc/jabber/UPGRADE
/usr/share/doc/jabber/README.Debian
/usr/share/doc/jabber/copyright
/usr/share/doc/jabber/jabber-xml.diff.gz
/usr/share/doc/jabber/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/jabberd.8.gz
/var
/var/log
/var/log/jabber
/var/lib
/var/lib/jabber
/var/run
/var/run/jabber

I honestly would not know where the problem could be, but I will keep that little command "dpkg -L package-A", is there something missing somewhere Maybe?

---

### Post by Darrena on 2005-06-25
The package you are istalling is not the jabber client package, this is the SERVER package.  Notice the jabberd, that is the jabber daemon.

What you want to install is gnome-jabber, not jabber.  The Gnome-jabber package is the client and jabber is the server portion.  So remove jabber and install Gnome-jabber.

If you enable the universe repositories you can either install it with synaptic or via apt.

The other issue you list with other packages indicates a problem with the packager/package and not ubuntu.  This means that the packager is not putting the launch script in a location in your path.  Generally the package should put the launch script in /usr/bin or /usr/local/bin.  Look at any other apps and see where they place the launch script, they may not be in a location in your path.

Respond here with any other questions.

---

### Post by 1hutchy on 2005-06-25
Thanks I thought it might be something like that,but I have a few games like 3dchess etc, heres one for foobillard that wont run either,
  dpkg -L foobillard
/.
/usr
/usr/games
/usr/games/foobillard
/usr/share
/usr/share/games
/usr/share/games/foobillard
/usr/share/games/foobillard/blende.png
/usr/share/games/foobillard/cue_shadow.png
/usr/share/games/foobillard/foobillard.gif
/usr/share/games/foobillard/foobillard.png
/usr/share/games/foobillard/full_symbol.png
/usr/share/games/foobillard/fullhalf_symbol.png
/usr/share/games/foobillard/half_symbol.png
/usr/share/games/foobillard/lightflare.png
/usr/share/games/foobillard/place_cue_ball.png
/usr/share/games/foobillard/queue.png
/usr/share/games/foobillard/queue_shadow.png
/usr/share/games/foobillard/shadow2.png
/usr/share/games/foobillard/shadow3.png
/usr/share/games/foobillard/shadow_alpha.png
/usr/share/games/foobillard/sphere_map_128x128.png
/usr/share/games/foobillard/sphere_map_128x128_light.png
/usr/share/games/foobillard/sphere_map_64x64.png
/usr/share/games/foobillard/table-frame.png
/usr/share/games/foobillard/tabletex_fB_128x128.png
/usr/share/games/foobillard/tabletex_fB_256x256.png
/usr/share/games/foobillard/ball_ball.raw
/usr/share/games/foobillard/posx.png
/usr/share/games/foobillard/posy.png
/usr/share/games/foobillard/posz.png
/usr/share/games/foobillard/negx.png
/usr/share/games/foobillard/negy.png
/usr/share/games/foobillard/negz.png
/usr/share/games/foobillard/bumpref.png
/usr/share/games/foobillard/cloth.png
/usr/share/doc
/usr/share/doc/foobillard
/usr/share/doc/foobillard/changelog.gz
/usr/share/doc/foobillard/README.gz
/usr/share/doc/foobillard/README.Debian
/usr/share/doc/foobillard/TODO
/usr/share/doc/foobillard/copyright
/usr/share/doc/foobillard/changelog.Debian.gz
/usr/share/man
/usr/share/man/man6
/usr/share/man/man6/foobillard.6.gz
/usr/lib
/usr/lib/menu
/usr/lib/menu/foobillard

I will seek & look at some other pkgs that do work & see if I can work something out, but I might need some insightful help ,Thanks

---

### Post by Darrena on 2005-06-25
[QUOTE=1hutchy]Thanks I thought it might be something like that,but I have a few games like 3dchess etc, heres one for foobillard that wont run either,
  dpkg -L foobillard
/.
/usr
/usr/games
/usr/games/foobillard
/usr/share
/usr/share/games
/usr/share/games/foobillard
/usr/share/games/foobillard/blende.png
/usr/share/games/foobillard/cue_shadow.png
/usr/share/games/foobillard/foobillard.gif
/usr/share/games/foobillard/foobillard.png
/usr/share/games/foobillard/full_symbol.png
/usr/share/games/foobillard/fullhalf_symbol.png
/usr/share/games/foobillard/half_symbol.png
/usr/share/games/foobillard/lightflare.png
/usr/share/games/foobillard/place_cue_ball.png
/usr/share/games/foobillard/queue.png
/usr/share/games/foobillard/queue_shadow.png
/usr/share/games/foobillard/shadow2.png
/usr/share/games/foobillard/shadow3.png
/usr/share/games/foobillard/shadow_alpha.png
/usr/share/games/foobillard/sphere_map_128x128.png
/usr/share/games/foobillard/sphere_map_128x128_light.png
/usr/share/games/foobillard/sphere_map_64x64.png
/usr/share/games/foobillard/table-frame.png
/usr/share/games/foobillard/tabletex_fB_128x128.png
/usr/share/games/foobillard/tabletex_fB_256x256.png
/usr/share/games/foobillard/ball_ball.raw
/usr/share/games/foobillard/posx.png
/usr/share/games/foobillard/posy.png
/usr/share/games/foobillard/posz.png
/usr/share/games/foobillard/negx.png
/usr/share/games/foobillard/negy.png
/usr/share/games/foobillard/negz.png
/usr/share/games/foobillard/bumpref.png
/usr/share/games/foobillard/cloth.png
/usr/share/doc
/usr/share/doc/foobillard
/usr/share/doc/foobillard/changelog.gz
/usr/share/doc/foobillard/README.gz
/usr/share/doc/foobillard/README.Debian
/usr/share/doc/foobillard/TODO
/usr/share/doc/foobillard/copyright
/usr/share/doc/foobillard/changelog.Debian.gz
/usr/share/man
/usr/share/man/man6
/usr/share/man/man6/foobillard.6.gz
/usr/lib
/usr/lib/menu
/usr/lib/menu/foobillard

I will seek & look at some other pkgs that do work & see if I can work something out, but I might need some insightful help ,Thanks[/QUOTE]
 That one ran fine for me from a terminal, did you install it from Hoary Universe?

---

### Post by 1hutchy on 2005-06-25
I think so as I always use these repos ,is it a bug repo like unstable, so to speak, where would I find the executable or launch script?

---

