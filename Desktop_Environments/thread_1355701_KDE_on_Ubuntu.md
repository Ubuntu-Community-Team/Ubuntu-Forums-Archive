---
title: "KDE on Ubuntu?"
date: 2009-12-15
forum: Desktop Environments
---

### Post by karumudi7 on 2009-12-15
Hi Frnds,
I like Kubuntu Desktop, but all the sfts,support is good 4 Ubuntu.Am I correct?
Thats why I also want to convert into Ubuntu by leaving Kubuntu.
Is it possible to install KDE desktop on Ubuntu(GNOME)??
Or otherwise I continue using Kubuntu.
Plz reply me.

---

### Post by cascade9 on 2009-12-15
Ubuntu = Gnome desktop. 

Kubutnu = KDE desktop. 

By running kubuntu, you already have 'KDE desktop on Ubuntu'.

---

### Post by UbuntuNerd on 2009-12-15
If you want to install kubuntu-desktop in Ubuntu use the following command in a terminal:
```
sudo apt-get install kubuntu-desktop
```
after you install it logout out and back in and look at the login screen under the options select "session" you should see "KDE"

---

### Post by User3k on 2009-12-15
> **cascade9 said:**
> Ubuntu = Gnome desktop. 

Kubutnu = KDE desktop. 

By running kubuntu, you already have 'KDE desktop on Ubuntu'.


Xubuntu=XFCE :)

---

### Post by lovinglinux on 2009-12-15
I recommend installing [kde-minimal](apt:kde-minimal) and [kdeplasma-addons](apt:kdeplasma-addons). You will be able to login into KDE, without installing all Kubuntu applications.

If you don't want to login into KDE, but use the plasma desktop, then see [this](http://ubuntuforums.org/showthread.php?t=1291048).

---

### Post by karumudi7 on 2009-12-16
> **lovinglinux said:**
> 

If you don't want to login into KDE, but use the plasma desktop, then see [this](http://ubuntuforums.org/showthread.php?t=1291048).

Is this for Installing KDE Desktop on Ubuntu?
This changes the Ubuntu Desktop to Kubuntu desktop(jst visulisation) is it correct??

Also is there any differences b/w Ubuntu & Kubuntu otherthan KDE & Gnome?
like stability or anything  else...


I an Newbee to Ubuntu thats Y i am asking!

---

### Post by lovinglinux on 2009-12-16
> **karumudi7 said:**
> Is this for Installing KDE Desktop on Ubuntu? This changes the Ubuntu Desktop to Kubuntu desktop(jst visulisation) is it correct??

Not exactly. That is for running KDE without logging out of Gnome. 

To install Kubuntu desktop, including all default applications like Kmail, Korganizer, Konqueror etc:

```
sudo apt-get install kubuntu-desktop
```

To install only KDE with all fancy desktop widgets:

```
sudo apt-get install kde-minimal kdeplasma-addons
```

> **karumudi7 said:**
> Also is there any differences b/w Ubuntu & Kubuntu otherthan KDE & Gnome?
like stability or anything  else...

Some people will argue that KDE is not stable, but I disagree. It is very stable for me.

---

### Post by Struki on 2009-12-18
I'm interested in trying out kde desktop, but since I'm relatively fresh user there are some things that I don't understand. 
**1**. Is it possible to use kde and gnome and to chose wich one to use at each startup(similar to dual boot)?
**2**. Is it possible to use the above if you are not using the login screen at startup(I'm logged in at start up)?
**3**. What ARE mayor differences between Kde and gnome outside the obvious visual design?
**4**. What IS the difference between kde, kubuntu desktop, and plasma desktop?
**5**. If i choose to switch to some of these variations what would be my benefits and my downsizes?
**6**. Wich choice would you suggest?

---

### Post by lovinglinux on 2009-12-18
> **Struki said:**
> **1**. Is it possible to use kde and gnome and to chose wich one to use at each startup(similar to dual boot)?

Yes.

> **Struki said:**
> **2**. Is it possible to use the above if you are not using the login screen at startup(I'm logged in at start up)?

The login manager will remember your option, so if you are using Gnome you can logoff instead of reboot, then select the Desktop Enviroment you want to use. Next time you boot, it will automatically log into the last used Desktop Environment.

> **Struki said:**
> **3**. What ARE mayor differences between Kde and gnome outside the obvious visual design?

Basically the default applications and some stuff under the hood. For instance, KDE uses Kwallet for storing passwords, which is tightly integrated with the KDE browser and other KDE applications. If you want to use Gnome apllications inside KDE, they will probably not store passwords in Kwallet. For example, I was experiencing problems with esvn, in terms of retrieving passwords from the keyring. Once I switched to kdesvn, the problem was solved, since it stores the passwords in Kwalllet.

> **Struki said:**
> **4**. What IS the difference between kde, kubuntu desktop, and plasma desktop?

KDE is the [Desktop Environment](http://en.wikipedia.org/wiki/Desktop_Environment), which includes the [plasma desktop](http://en.wikipedia.org/wiki/Plasma_%28KDE%29) (fancy widgets, panels and so on), the default applications like Konquereor, Kmail, Kontact and also includes [Kwin](http://en.wikipedia.org/wiki/Kwin), which is a window manager like Compiz.

Kubuntu desktop is a meta-package. Basically it is not an application, but a list of all the default applications installed by the Kubuntu CD. So when you install kubuntu-desktop package, you automatically install all default Kubuntu applications. But uninstalling kubuntu-desktop does not remove them.

> **Struki said:**
> **4****5**. If i choose to switch to some of these variations what would be my benefits and my downsizes? Wich choice would you suggest?

You have to try it and see for yourself. I switched to KDE because I don't like where Gnome 3 is going with the new [Gnome Shell](http://ubuntuforums.org/showthread.php?t=1114918), so I decided to give KDE a try. At first it feels strange, because you need to learn how to configure it, specially if you use Gnome for some time. Nevertheless, I really enjoyed the switch in the long term. I couldn't be happier with my new desktop.

Anyway, there are tons of threads comparing Gnome with KDE.

---

### Post by Struki on 2009-12-18
Nice reply, you really got me reading. So somehow I think the most logical thing for me to do would be trying out the tutorial on using the plasma desktop you wrote, and then gradually switch to kde if I feel like it.
You agree?

O and is it possible to use desktop apps like AWN bar, and such in kde desktops?

---

### Post by RazzyDaz on 2009-12-18
Lovinglinux---
I am looking for use KDE inside Ubuntu.  I saw the page where you listed how to follow the step to setting up KDE.  I have a question, when I go to activate the hardware, there isn't anything in the box. What should I do? Does it matter? My graphics seem to working fine, but wanted to make sure, before starting.

---

### Post by lovinglinux on 2009-12-18
> **Struki said:**
> Nice reply, you really got me reading. So somehow I think the most logical thing for me to do would be trying out the tutorial on using the plasma desktop you wrote, and then gradually switch to kde if I feel like it.
You agree?

Nope. You won't be able to grasp KDE with that. Is just a hack to run the fancy tuff from KDE over Gnome. I think would be easy for you to switch completely. BTW, I don't know the answers to your questions posted in that thread.

> **Struki said:**
> O and is it possible to use desktop apps like AWN bar, and such in kde desktops?

Yes, but AWN depends on lots of Gnome packages.

---

### Post by Struki on 2009-12-18
> **lovinglinux said:**
> Nope. You won't be able to grasp KDE with that. Is just a hack to run the fancy tuff from KDE over Gnome. I think would be easy for you to switch completely. BTW, I don't know the answers to your questions posted in that thread.

Ok then, could you pls then tell me how to undone all the changes i did with your tutorial, and I'll try the real deal



> **lovinglinux said:**
> Yes, but AWN depends on lots of Gnome packages.
So i will have some problems running it in kde? Is there an alternative for kde?

---

### Post by lovinglinux on 2009-12-18
> **Struki said:**
> Ok then, could you pls then tell me how to undone all the changes i did with your tutorial, and I'll try the real deal


1) Open gconf-editor from the terminal:

```
gconf-editor
```

Open "desktop >> gnome >> session >> required_components", then double-click the "panel" option and add "gnome-panel" value.

2) Delete the two scripts saved on your desktop.

3) Restore metacity if you don't want to use Emerald anymore

```
metacity --replace
```

4) you can remove the installed packages if you want, but most of them will be installed with the full kde.

This is the command (please notice that this also removes compiz and emerald):

```
sudo apt-get remove compiz compizconfig-backend-gconf compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper libdecoration0 compizconfig-settings-manager python-compizconfig emerald libemeraldengine0 kde-minimal akonadi-server dolphin exiv2 kappfinder kde-icons-oxygen kde-minimal kde-window-manager kdebase kdebase-bin kdebase-data kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdelibs-bin kdelibs5 kdelibs5-data kdepasswd kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepimlibs-data kdepimlibs5 kdm kfind khelpcenter4 klipper konqueror konqueror-nsplugins konsole ksysguard ksysguardd kwrite libakonadiprivate1 libboost-program-options1.38.0 libclucene0ldbl libexiv2-5 libkdecorations4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkwineffects1 liblzma0 libmodplug0c2 libmpcdec3 libplasma3 libpolkit-qt0 libqimageblitz4 libqt4-designer libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-webkit libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x mysql-server-core-5.1 phonon-backend-xine plasma-dataengines-workspace plasma-widget-folderview plasma-widgets-workspace soprano-daemon systemsettings ttf-dejavu ttf-dejavu-extra compiz-kde compizconfig-backend-kconfig exiv2 kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-libs4+5 kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data khelpcenter4 libavahi-qt3-1 libclucene0ldbl libexiv2-5 libkdecorations4 libknotificationitem1 liblua50 liblualib50 liblzma0 libmodplug0c2 libmpcdec3 libplasma3 libqt3-mt libqt4-designer libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-webkit libsoprano4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x phonon-backend-xine soprano-daemon ttf-dejavu ttf-dejavu-extra kdebase-workspace-wallpapers kdeplasma-addons kdewallpapers libkexiv2-7 liblancelot0 libmarble4 marble-data plasma-dataengines-addons plasma-runners-addons plasma-wallpapers-addons plasma-widget-lancelot plasma-widgets-addons libqt4-assistant libqt4-help libqt4-scripttools libqt4-test libqt4-xmlpatterns plasma-scriptengine-python python-kde4 python-qt4 python-sip4 gtk2-engines-qtcurve kde-style-qtcurve kwin-style-qtcurve
```

> **Struki said:**
> So i will have some problems running it in kde? Is there an alternative for kde?

Nope, it's just that I don't like to install all those packages just to run a single application.

---

### Post by 3Miro on 2009-12-18
My two cents:

KDE is stable, Kubuntu is not. Ubuntu is Gnome oriented and many apps are not well tested/set up for KDE. There seem to be other issues with Kubuntu, I know for two instances when Kubuntu will not install and Ubuntu will (same version 9.10).

What I did was:

1. Install Ubuntu 9.10 with Gnome and all.
2. Install kubuntu-desktop and all the addons. This is now stable for me and I can switch between the Ubuntu optimized Gnome and the newer and flashier KDE.
3. Then I installed XFCE and haven't used Gnome or KDE in 2 weeks. XFCE is ... fast. It has fewer features, but it is so much faster that it is worth the trade-off in my view. Also, XFCE uses the dame GTK libraries as Gnome, so apps generally do not suffer from compatibility issues.

Anyway, installing KDE takes about 1GB extra and XFCE about 100MB. You can easily have them all and decide which one you want/need.

PS KDE has the Fancy Panel widget that is the KDE equivalent of AWN. I found it, however, to be somewhat unstable.

---

### Post by Extract_Here on 2009-12-19
if you like kde just stick with kubuntu because its ubuntu in kde. if you want gnome use ubuntu

---

### Post by Struki on 2009-12-22
Ok so it took me some time but I did it, i got my kde desktop installed. So now I'm wondering:
1. How can I customize my desktop, are there any tutorials, cause i can't find any good ones. 
2. My emerald isn't working, how do I start it in kde
3. I'm running AWN and Screenlets in gnome, they pop out in kde when I switch and cause confusion so can i keep them in gnome, and not use them in kde?

---

### Post by Struki on 2009-12-22
Ok so it took me some time but I did it, i got my kde desktop installed. So now I'm wondering:
1. How can I customize my desktop, are there any tutorials, cause i can't find any good ones. 
2. My emerald isn't working, how do I start it in kde
3. I'm running AWN and Screenlets in gnome, they pop out in kde when I switch and cause confusion so can i keep them in gnome, and not use them in kde?

Ups sry for the double post!

---

### Post by lovinglinux on 2009-12-22
> **Struki said:**
> Ok so it took me some time but I did it, i got my kde desktop installed. So now I'm wondering:
1. How can I customize my desktop, are there any tutorials, cause i can't find any good ones. 
2. My emerald isn't working, how do I start it in kde
3. I'm running AWN and Screenlets in gnome, they pop out in kde when I switch and cause confusion so can i keep them in gnome, and not use them in kde?

2 - Use [fusion-icon](apt:fusion-icon)

Sometimes emerald doesn't load and loading it with fusion-icon doesn't fix the problem. Then I have to log-out and login again. I'm not sure why this happens.

3 - I guess you need to login into Gnome, then go to "System >> Preferences >> Startup applications" and disable both. The KDE equivalent is under "System Settings >> Advanced User Settings >> Autostart".

---

### Post by Struki on 2009-12-22
ok so im playing around with plasma desktops and i can't figure out why can't i install more plasma themes after some time, and i can't remove the ones i installed.
Anyone?

---

### Post by DjAT on 2009-12-24
I installed KDE on ubuntu. nw i like to restore all setting of original ubuntu(not KDE)
how to remove or restore this ?

---

### Post by UltraZone on 2009-12-24
I would like to cross-link a solution to a potential problem.

What I did was to install: kde-minimal and kdeplasma-addons as described in the first page of this thread.

However, this does not have kdenetworkmanager, so I couldn't connect to my wireless.  From what I read the native kdenetworkmanager is pretty awful, so you can just run the Gnome network manager, but you must enable it to run under KDE.

So do this in a terminal:

sudo gedit /etc/xdg/autostart/nm-applet.desktop

enter your sudo password then edit the line that says OnlyShowIn= and add KDE at the end.  In my case it had GNOME;XFCE; already enabled but no KDE.  This is useful if your networking is working perfectly in Gnome already and don't want to mess with having to set up networking all over again under KDE.  

Oh yes, save and close gedit and you're done.  Maybe need to re-login.

---

### Post by ElSlunko on 2009-12-24
I did the minimal install & noticed that the GTK Styles setting was missing from System Settings > Appearance. So I installed kcm-gtk & I got the dialogue, but the GTK themes just won't stick to GTK apps. Any clue why this might be happening? Should I start a new thread?

---

### Post by lovinglinux on 2009-12-24
> **ElSlunko said:**
> I did the minimal install & noticed that the GTK Styles setting was missing from System Settings > Appearance. So I installed kcm-gtk & I got the dialogue, but the GTK themes just won't stick to GTK apps. Any clue why this might be happening? Should I start a new thread?


See [http://ubuntuforums.org/showpost.php?p=8107813&postcount=17](http://ubuntuforums.org/showpost.php?p=8107813&postcount=17)

---

### Post by ElSlunko on 2009-12-24
Thank you Lovinglinux. That did the trick.

---

### Post by ElSlunko on 2009-12-24
I noticed that the GTK theme renders as .gtkrc-2.0-kde4 which has to be renamed each time I change something. Not sure if there's a way to fix that yet.

---

### Post by drumkitcat on 2010-02-16
This has been a very interesting thread to read through!

I myself am running a dual boot Kubuntu 9.10/ Ubuntu Studio 9.10 on my Toshiba Satellite A40 laptop.

I started off installing only Kubuntu 9.10 as a fresh install leaving the Windows XP world forever.. It installed perfectly fine and I was running wireless in no time at all.  My favorite feature of Kubuntu is the Kontact organizer/mail suite - it's awesome.... but I'm a drummer and wanted various software for music editing etc, and got turned onto Ubuntu Studio - it's great!  I installed it, and somehow in the process turned my computer into a dual boot system.

It's been a few months now that I have both systems, Kubuntu does lock up sometimes, while Gnome has been rock steady.

Overall I think I like Ubuntu Studio more, but I wish I could port all the Kontact stuff I've entered into it and just do a fresh install of only Ubuntu Studio - it loads up rocket fast and works amazingly well. 

Still, it's been great having the option to run either - Kubuntu or Ubuntu - but I think for me the better fit is Ubuntu.  I am a musician and a certified project manager, so there's little time for tweaking a computer or playing games on it.  

Can someone tell me if Kontact files can be exported (contacts, emails, calendar entries) or would I have to start fresh with whatever the organizer software is in Ubuntu?

Thanks
Paul

---

### Post by rokixz on 2010-02-16
I'm interested in such a thing like auto-toggling off effects in kubuntu when full-screened app is running. I feel very uncomfortable with this when playing GL based game, fps took very low. I got such a feature in OpenSuse and Arch, it ran very smoothly and I needn't to switch off effects manually. Btw, KDE 4.4SC.

---

