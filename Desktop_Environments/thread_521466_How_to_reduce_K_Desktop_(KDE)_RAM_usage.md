---
title: "How to reduce K Desktop (KDE) RAM usage ?"
date: 2007-08-09
forum: Desktop Environments
---

### Post by cyneuron on 2007-08-09
Hello there

Everyone knows that kde takes up a little higher RAM than GNOME. and if one sees in Ksysguard no. of processes which start up at boot is really high.

Are all these processes really needed to set up a basic K desktop ?

I think KDE kind of preloads a lot of programs in advance.

Is there any guide or tutorial which explains how to manage the processes and programs to start at boot up and thus to configure KDE to take up less of RAM so as to get high system performance.

---

### Post by ThinkBuntu on 2007-08-09
Hate to say it, but your presumptions are wrong. KDE and GNOME use similar amounts of resources and RAM, and I've even seen studies bearing out that GNOME is more resource-hungry. KDE doesn't load any apps to RAM by default, so unless you've installed some quickstarters, you should be fine.

Also, KSysguard, for some reason, grossly over-estimates RAM usage, probably because it's only running thinly over the shell "top" command.

---

### Post by GeneralZod on 2007-08-09
> **ThinkBuntu said:**
> Hate to say it, but your presumptions are wrong. KDE and GNOME use similar amounts of resources and RAM, and I've even seen studies bearing out that GNOME is more resource-hungry. KDE doesn't load any apps to RAM by default, so unless you've installed some quickstarters, you should be fine.


Yup: [http://ubuntuforums.org/showthread.php?p=2015680#post2015680](http://ubuntuforums.org/showthread.php?p=2015680#post2015680)

> 
Also, KSysguard, for some reason, grossly over-estimates RAM usage, probably because it's only running thinly over the shell "top" command.

More precisely: KSysguard includes the cache and buffers in its memory usage; gnome-system-monitor does not:

[http://ubuntuforums.org/showthread.php?t=490910](http://ubuntuforums.org/showthread.php?t=490910)

---

### Post by cyneuron on 2007-08-09
well, i am not presuming it. i have both ubuntu, kubuntu and pclos 2k7 installed on my system. and i have felt the difference...

as for ksysguard gross over estimates, what about the results this command give in terminal :

free

ubuntu and kubuntu just after install. a difference almost of 100 MB.

---

### Post by cyneuron on 2007-08-09
for the link generalzod provided, well the poll results show gnome is winner over gnome in ubuntu. well reason for that is kubuntu is really full of bug as compared to ubuntu. dont know why as, both use same ubuntu base.

if you compare KDE vs GNOME across all distros, KDE is surely a winner (well, my personal personal perspective, you may surely differ on this)... 

guys, i am not starting the much debated question "Gnome Vs KDE".

i wanted some good tweaks to reduce kde RAM usage.

though i appreciate such wise responses....

---

### Post by Erunno on 2007-08-09
That depends on which services get loaded by default (which could be different from Ubuntu), if Konqueror is preloaded (can be deactivated). For instance, Kubuntu employs a Phyton-based energy management frontend which uses quite a lot more memory than a native C++ solution. Nevertheless KDE loads most of its infrastructure into memory at start but as long as you stay in the KDE world by using only KDE applications you'll have a better cut than using GNOME with aliens like OpenOffice and Firefox.

---

### Post by cyneuron on 2007-08-09
well thats enlightening info.......

then is there any good guide available to manage kde startup processes and programs.

i googled but no good link........

or any tips from you all people........

---

### Post by Crakie on 2007-08-09
> then is there any good guide available to manage kde startup processes and programs.

i googled but no good link........

or any tips from you all people........

I feel it is a bit silly to take a full-featured distro like Kubuntu and start peeling it. It would make more sense to select a lightweight distro and go from there. Debian would be an obvious choice, if you do not want to venture too far from Ubuntu. If you really love speed, then I would recommend Arch Linux or Gentoo. They take a while to setup, but boyohboy are they fast.

---

### Post by miggols99 on 2007-08-09
You could try turning off GUI effects if they are activated

Control Centre >> Appearance and Themes >> Style >> Second tab >> Untick "Enable GUI effects"

You can also disable the bouncy icon:

Control Centre >> Launch feedback >> Change "Bouncing icon" to something else or disable launch feedback (next to cursor) altogether.

If you want really fast, you could try building from ground up:

[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

Or if you want really really fast you could try Arch Linux with KDEmod, the fastest KDE I've ever seen:

[http://kdemod.ath.cx](http://kdemod.ath.cx)
[http://archlinux.org](http://archlinux.org)

But beware that Arch Linux is much harder to set up. A default install will give you CLI only. You will have to install KDE and Xorg etc. after the install (unless you use the full install disk) but I personally use the base one for it to be lighter. The configuration files are very simple. The /etc/rc.conf is a main configuration file for changing just about everything. If you're fine with (K)ubuntu, then stick with it.

---

### Post by ThinkBuntu on 2007-08-09
You could also use Dolphin as your file manager. I wrote a how-to about that in the Tutorials forum, but I'm too lazy to go and find it. A search should be enough.

Dolphin's not the best, and it probably is being radically overhauled for KDE 4, but in many cases it's a fine replacement for Konqueror.

---

### Post by Freddy on 2007-08-10
If you really like (K)ubuntu which I do for the repository's, community and base system and want a faster KDE, just install the base system from the "command line" install, add x-window-system-core, kde-base and kdm, trough aptitude or apt-get. I can agree that Kubuntu feels somewhat slow compared to similar distros providing KDE.

---

### Post by cyneuron on 2007-08-10
thanks for all the responses........

i had already turned up gui and other fancy things.........

about installing only the base system, i consider it only temp solution, bcoz as you go on installing other apps, you have to ultimately install various depndencies.........

i found a page on kde.org about kde performance tips.... really good resource........

you guys do check out that........ just google it.......

and about replacing konquerer, with dolphin......... i also thought about it....... but have been a bit lazy...... will do it sometime.......

---

### Post by Erunno on 2007-08-10
I very much doubt that turning off some GUI effects will have an effect on the RAM usage. It's more likely that you'll safe some CPU cycles by this measure. Same goes for replacing Konqueror with Dolphin as Konqueror is a very light application by itself and, in my opinion, the Dolphin3 is just not worth it as it pales compared to Konqueror (I like Dolphin4 though).

---

