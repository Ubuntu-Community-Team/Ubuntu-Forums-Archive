---
title: "Something is seriously wrong w/6.06 update-manager. . .Help!!"
date: 2006-06-03
forum: Desktop Environments
---

### Post by RavenOfOdin on 2006-06-03
I am absolutely infuriated, at the moment.

I have recently finished a kernel upgrade to 2.6.16.18 and iptables upgrade to 1.3.5, so I could start cruising the net again on my n*x system.  Once I did it I thought that upgrading to 6.06 wouldn't be a bad idea.

Little did I know. . .

Running the update-manager inside of Kubuntu (which is my main DE), after I checked these forums and saw that users were obtaining good results with it, I got every package downloaded. 1500+ of them. Once the install started, though, s*** hit the fan.

Packages were dropping all over the place with unmet function calls and dependency resolutions.

I ***somehow*** managed to get the overwhelming majority of the packages upgraded and (seemingly) in there correctly, as apt-get would attest, but now three packages which have the entire system on lock down are refusing to configure and I can't get rid of them - via apt-get or my second idea, dselect.  I've tried apt-get -f install and apt-get dist-upgrade. I also tried dpkg -C to find packages which needed configuration. I only was able to get one (perl-modules) configured correctly. 

If anyone wants a copy of my sources.list I'll be happy to post it, but after every try on install, the *get* commands now come back with 

```

Error 2 : Could not stat <xxx> - No such file or directory.

```

I, like other users suggested to do in previous posts, took out every mention of "breezy" from my apt/sources.list and replaced it with "dapper" prior to installation. And as y'all can see, I get that up top.

None of the packages which need to be removed have been, yet.

The current status of my box is that I can get past usplash and all with any kernel, but instead of GDM or KDM I get booted to the terminal login. Reconfiguring drivers through sudo dpkg-reconfigure xserver-xorg hasn't worked. 

GRUB is failing every second reboot(!) and instead of passing me to a kernel list it goes to a blank screen with the blinking underscore and then after 20 seconds to Windows XP. (Whew!)

I don't want to know what may have happened to my system in the install procedure, especially since I've been having iptables problems after the upgrade and now it only loads as a back-end to Firestarter.

The packages which are having install/configuration trouble are as follows:

libc6 - cannot upgrade from 2.3.5<append-version-info here> to 2.3.6
libc6-dev - depends on libc6 2.3.6 yet libc6 2.3.5<append-version-info here> is installed.
belocs-locale-bin- Unable to make backup link, operation not permitted - or install.
/usr/sbin/zic - Unable to make backup link, operation not permitted.

(EDIT: Oh, and when I screw around with apt-get some more it says "Package belocs-locale-bin has no available version, but exists in the database. This may mean that the package has been obsoleted. . .")

I REALLY, REALLY don't want to uninstall and reinstall my system since I have a bunch of work on here for Open Source software projects. A deadline is approaching for them so now I feel like a complete and utter idiot attempting to upgrade at this time!!

Please, if any of y'all can help me you'll have my eternal gratitude. Just get this damned thing working again!

---

### Post by blackjack6.21.91 on 2006-06-03
I'm sorry and I your probably frustrated enough already, but the best advice I can give is to backup your data elsewhere and then reformat (then again, though, I'm a newb and someone probably knows the real solution).  But the main reason I posted is that I freakin love your signature.  This part especially
> ~Linux is not a political platform. It is software. Get a grip.~
I'm sorry for being so irrelevant, but may I quote you?

---

### Post by RavenOfOdin on 2006-06-03
[QUOTE=blackjack6.21.91]I'm sorry and I your probably frustrated enough already, but the best advice I can give is to backup your data elsewhere and then reformat (then again, though, I'm a newb and someone probably knows the real solution).  But the main reason I posted is that I freakin love your signature.  This part especially

I'm sorry for being so irrelevant, but may I quote you?[/QUOTE]

I CAN'T back up my data, I have nothing to back it up with! No partition, no spare CD's to burn.

I will not reformat. I may as well say goodbye to the jobs I'm completing if this happens.

Yes, you may quote my signature.

---

### Post by blackjack6.21.91 on 2006-06-03
If there's a way for you to back everything up on my comp that'd be fine.  Maybe direct connect through limewire or bittorrent of something?  If I can be of any help just let me know.  And thanks

---

### Post by RavenOfOdin on 2006-06-03
[QUOTE=blackjack6.21.91]If there's a way for you to back everything up on my comp that'd be fine.  Maybe direct connect through limewire or bittorrent of something?  If I can be of any help just let me know.  [/QUOTE]

Thank you for the offer, but I believe I'll pass.

[QUOTE=blackjack6.21.91]
And thanks[/QUOTE]

Don't mention it. :)

(Second edit: I don't know how in God's name it was done, maybe through reconfiguring G/KDM one more time, but I am now able to get back into KDE. That takes one heck of a load off my back.)

*breathes relieved sigh*

auth.log and the other utilities I can think of, namely last/b, show nothing out of the ordinary so I don't think iptables really became a problem.  I'll run chkproc and chkwtmp later to make sure.

But now, there are a few more issues - since I can look at this objectively again I'll list them and see if any of y'all that respond know these to be upgrade problems:

1)  My ATI drivers were killed again, and I was running 2.6.12-10-386 to get back in to KDE. That kernel should have had those drivers installed, no exception.
2) libc6/dev and belocs-locale-bin are still broken, I think I'll instead of floppy use wget since some of those packages I need to resolve the breaks are over 4 MB.
3) Adept Updater (System) declines my root password with something along the lines of "You must be root for this to have any effect."
4) GDM and Gnome are not running well, because when I switch to GDM under dpkg-reconfigure and then do a sudo /etc/init.d/gdm start it goes to the themed greeter. I type in my username, password, then it acts like its logging in. It stops splash screen progress on Metacity and then creates two white gnome-panels in front of a black screen, only to kill and create them ad nauseam.  Ctrl-Alt-Backspace stops this. Is there something in the GDM boot manager (I use BUM) that is preventing a clean boot, or is this just the notorious invasiveness of KDE at work?

Other than that, I seem to be running a perfectly functional distro now.

---

