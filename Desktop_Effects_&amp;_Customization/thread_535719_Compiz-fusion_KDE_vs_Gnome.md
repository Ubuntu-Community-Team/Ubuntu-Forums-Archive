---
title: "Compiz-fusion: KDE vs Gnome"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by ittiam on 2007-08-26
Is there a difference in performance when compiz-fusion runs on gnome when compared to kde. Apparently I do see a better performance in gnome. I am a kde user but just wanted to  try something out in gnome and when I ran fusion-icon...it just runs so smoothly.Has it been a long known thing or is it just I am seeing wrong or something?

---

### Post by Happy_Man on 2007-08-26
Speaking as one who does, on a regular basis, what you are describing, I can attest that Compiz Fusion is fully DE-neutral. I can see no real speed advantage in GNOME over KDE. But that's just me. Everyone, and their computer, is different.....

---

### Post by ittiam on 2007-08-26
Yea I thought so! I always love kde for its flexibility and utils...I am logging into gnome after a very long time...so i guess ..err..i dont know...it just seems so smooth!

---

### Post by Rupertronco on 2007-08-26
I've got the KDE, XFCE, and Gnome desktops, my compiz benchmark shows that they all run within 10 fps of eachother, which isn't significant at all. I don't think it's something you really need to worry about, there are plenty of other things that make a much more dramatic impact on your compiz performance than your DE.

---

### Post by ittiam on 2007-08-27
One striking difference is the performance of firefox in gnome is far better than in kde when compiz is running. For example in kde when i click on the address bar...it is just stuck and takes some 10-15 seconds for the list of urls to come down with the wobbly effects. I dont see the same in gnome.

---

### Post by tekkenlord on 2007-08-28
I had been using KDE for a long time and recently switched to GNOME. I can confirm that Compiz Fusion is much smoother in Gnome.

---

### Post by Happy_Man on 2007-08-28
> **ittiam said:**
> One striking difference is the performance of firefox in gnome is far better than in kde when compiz is running. For example in kde when i click on the address bar...it is just stuck and takes some 10-15 seconds for the list of urls to come down with the wobbly effects. I dont see the same in gnome.
That's because Firefox is a GNOME-native app. So, in KDE, it first has to load all those GNOME backend libraries before Firefox can start up, whereas in GNOME they are already loaded, so it starts up faster.

---

### Post by cookies on 2007-08-28
> **Happy_Man said:**
> That's because Firefox is a GNOME-native app. So, in KDE, it first has to load all those GNOME backend libraries before Firefox can start up, whereas in GNOME they are already loaded, so it starts up faster.


Actually it's not a "Gnome Application" per se, it's a GTK app. It doesn't require GNOME libs, but it does require GTK libs.

I also see no difference between CF in KDE and GNOME.

---

### Post by ittiam on 2007-08-28
> **Happy_Man said:**
> That's because Firefox is a GNOME-native app. So, in KDE, it first has to load all those GNOME backend libraries before Firefox can start up, whereas in GNOME they are already loaded, so it starts up faster.

I am not talking about how long firefox takes to load. It pretty much takes the same time in both. Sorry If I had not made myself clear. Let me give another shot. When you have firefox open and running, you want to go to a different url, you press Alt+d or click on the address bar to type in ur url. Mostly all the time i try to do this in KDE firefox freezes for some 10-15 seconds. Also then i type the first letter of website, firefox freezes again for 10-15 seconds before it shows me options for auto complete. I have never had this problem in gnome till date. **And by the way all this happen when compiz-fusion is running.** If I kill it...firefox is as smooth in kde as it is in gnome

---

### Post by michael37 on 2007-08-29
I use Gnome with Compiz Fusion and it runs very fast on an ATI video card for my laptop.  However, I know of many people using KDE and having great results.

No preference -- whatever looks better to you.

---

### Post by bigbrovar on 2007-09-04
mehn i most say that i noticed the difference btw KDE and and Gnome in term of compiz fusion performance Gnome is much more smoother especially when it comes to animations effects like Burn and Beam up..i just installed KDE and i was able to notice the difference ..is there any thing i can do to tweak this?

---

### Post by Happy_Man on 2007-09-04
Well, KDE is more resource-intensive, and as Fusion is resource-intensive also, things are bound to slow down, even on good computers. So I would suggest this: log out of KDE, and log into GNOME. Open a terminal and use one of these two commands:

If you used "apt-get" to install Kubuntu:
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools
sudo aptitude install kde-core
```

If you used "aptitude" to install Kubuntu (always the best choice for big giant metapackages like these):
```
sudo aptitude remove kubuntu-desktop
sudo aptitude install kde-core
```

That sequence of commands will remove all the clutter and install just the base KDE apps and libraries. From there, you can build it up as you wish. Much less clutter, and if you do it this way, KDE can run almost as fast and small as GNOME.

---

### Post by robert114 on 2007-12-08
I noticed a slowdown as well on Kubuntu Gutsy with Firefox

Other apps seems to run just fine here

---

### Post by kvonb on 2007-12-15
-

---

### Post by Happy_Man on 2007-12-15
Use one of the many repos available (there are some stickies on the topic in the Desktop Effects forum). Just make sure you have the restricted drivers running. If you just need the Fusion control panel, run ```
sudo apt-get install compizconfig-settings-manager
```

---

