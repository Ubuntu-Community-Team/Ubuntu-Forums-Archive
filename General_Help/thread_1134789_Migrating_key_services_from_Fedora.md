---
title: "Migrating key services from Fedora"
date: 2009-04-23
forum: General Help
---

### Post by happyscrappyheropup on 2009-04-23
Well, it finally happened, the primary drive on our company's main services server packed in and while it is limping along on the second drive in the mirror, we've decided that the good old FC5 machine is due for a full upgrade.  Now the thing to remember is that we were an SGI shop back in the day, had Serial HiPPI networking before most people knew there was fiber optics and despite our small size, always had some killer architecture backing us up.

SGI went the way of the dinosaur, we managed to avoid the Windows nonsense of the early 2000's and skipped merrily into Linux, settling on Fedora back 'round '02 and never looked back.  Till now...

As there is a cold spare of this server sitting on the shelf we have decided a clean installation and reconfiguration of the server is in order as the old FC5 distro is a bit long in the teeth. 

We slapped another drive and rebuilt the raid volume on the crippled server that started all this so as not to add to our misery and stared along the merry path to a new (and better?) core services server config on the spare box.

With the cold spare out & dusted off, we downloaded the ISO's for FC10 **and** Ubuntu.

Okay, fist thing's first.  This server is essentially air-traffic-control for our whole office.  It runs DHCP, DNS, LDAP, mail, licenseservers for various flex based vendors as well as puppet, and a few other services we have come to rely on over the years.  It's got 2 drives full mirror and a spare on the self ready to have drives slugged into it on a moment's notice if the hardware goes tits up (mind you we can go down for 1 hour and the world won't end so this is a completely viable redundancy for us).

The rest of the office is running various configurations of FC8 with the exception of one workstation we decided to install Ubuntu on a few months back when a vendor said they had had good luck with the i386 8.10 distro.   Off we went, configured it, added the host to dhcp, put it in dns and all was good.

Well, the long and short of the story is that have come to like Ubuntu on the desktop, quite a lot actually. With the demise of our trusty core services server we figured, 'what the hell.. let's give Ubuntu a shot on this box too!'
[I]
Not to mention we tried giving FC10 a whirl and I have to say, Fedora has really screwed the pooch on this release (not to mention FC9), so we've had it with them... the whole KDE fiasco in FC9 and now all the other FC10 issues... we don't have time for this nonsense while these guys figure out how to keep networking from going haywire... we have windows as an option if we want that kind of admin experience.[/I]

So, first thing we noticed is that there's two variants of the Ubuntu distro, one for servers, and other for workstations.  Hmm.. interesting.  I'm not sure I really understand why the distinction as I have servers I really like having X and Gnome on (like the Oracle server), but whatever... we'll use the desktop version and if I don't want X up on boot, well, that's what the inittab file is for right?

Also noticed that during the install we don't get any of the optional packages or distro options we see in Anaconda.  Kinda liked that, we know we need legacy development libs, etc., but our Ubuntu experience is a little fresh to be complaining about things we may not yet understand, so...

...after that rather long winded introduction, I'm curious if any long time Ubuntu sysadmins (hopefully some who have used Fedora or Cent) have any advice for setting up our core services using Ubuntu. 

It's something any number of us can manage in our sleep with the old FC5 distro we used, but on Ubuntu, everything's just different enough to cause you to curse fits when you are trying to get it done in a hurry...  

The first and most important thing will be setting up the static IP on the main server (ifcfg-eth0 and /etc/sysconfig/network just need a little twiddle right?... *well not in FC10, Network Manager thinks it knows better and the damn interface wants to do all sorts of erratic things on reboot!*) and then configuring DNS.  Next comes dhcpd and eventually ldap (Joy! My favorite torture, configuring ldap, it's been a few years but I hope the experience is not as horrific as my memory would have me believe).

So before we start this little project (or the old server packs it in for good)...

anyone got any advice or want to point us at some links detailing the Ubuntu-centric way of doing all this?

Thanks in advance for all your helpful advice,

HSHP, Esq. IV

---

### Post by kanikilu on 2009-04-23
Sorry I don't have more specific advice (I run only basic web servers), but regarding your comment about the desktop versus server edition, I would recommend going with the server edition. 

While this won't have a GUI installer or a desktop environment (to start), you can always add that later with a simple command, if you want ```
sudo apt-get install ubuntu-desktop
``` That way you'll have the GUI you like, but also take advantage of the server kernel.

*shh* Don't tell anyone I let you know about this <sarcasm>super secret command</sarcasm>! :P

Some people around here seem to be offended by (and take it personally) if you even *think* about putting a desktop environment on a server, and will be very vocal in telling you how to do it the **right** way :rolleyes:

More info:

[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

[http://www.serverwatch.com/tutorials/article.php/3715071](http://www.serverwatch.com/tutorials/article.php/3715071)

And don't forget the Ubuntu Server Guide:

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Oh, also thought it's worth mentioning that you can install some common services with tasksel:

[http://www.go2linux.org/using-tasksel-on-ubuntu-LAMP-switch-to-Kubuntu-Xubuntu](http://www.go2linux.org/using-tasksel-on-ubuntu-LAMP-switch-to-Kubuntu-Xubuntu)

It's kind of an old article, and mentions possibly needing to install tasksel, but it's been included for a while now...

---

### Post by happyscrappyheropup on 2009-04-25
[kanikilu]("http://ubuntuforums.org/member.php?u=87527"),

Thanks much for the pointers.

The Ubuntu Server Guide:

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Was most useful.  There's some good info there for folks coming from other distros.  Many thanks.

I have to say, I _REALLY_ don't like network-manager.  Maybe it's just fine on a laptop but it caused a seemingly endless array of difficulties for us, in the end we removed it altogether.  Eventually all the relevant config files will be managed by puppet or CFEngine.

Another observation; It would be nice if they would extend the DNS guide (in the server guide) to include chrooted dns as well, seems prudent to run dns chrooted these days and I am sure it's just an oversight.  I spent a bit of time googling around and found this on my own.

I did encounter some issues with dhcp3 in that hosts seem to be unable to take (or be given) host names from the dhcp3 server despite configuring to do so.  I found this a bit odd as we've been doing this with RH/CENT/Fedora for years and years and years.  It's one of those things that makes bringing 100's of servers in a farm online really doable as most of our vendors would ship servers with mac addresses for all the ethernet NICs in a file or e-mail if we ask.  This happens every few years as we upgrade the server farm.  We take the file and make a quick change to our dhcpd.conf, restart dhcpd, and when the machines show up with the drives pre-cloned by the vendor we just plug them in and they come up with the corrct addresses and identities.  The CFEngine of Puppetmaster server gives them a once over in case we've made changes in the config since placing the order for the new hardware and we're all done.

In this manner I can bring as many machines online as fast as I can unpack the boxes and rack them.  For 256 machines last time we updated it was about a 4 hour job.  If I had to edit hostname files on all of them it would have been an all night proposition.

So, it seems there's a bug that someone has decided is a low priority and it's simmered since at least ubuntu circa v6... can this really be the case?

I saw somewhere where someone noted that X really doesn't like it if the hostname gets changed under it and that was some sort of justification for not resolving this.  To me that's absurd in the extreme as the consequences of that in a place where we use dhcp precisely to ease management of machines, their names, addresses and thereby config via puppet or CFEngine.  

So if you or anyone has any clue as to how we can get the clients to take their hostname from dhcp3 then I'm all ears.  Either we're missing something or there's some looming hole in dhcp3.  

Thoughts?

:HSHP

---

