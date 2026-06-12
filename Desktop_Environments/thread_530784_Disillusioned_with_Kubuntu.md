---
title: "Disillusioned with Kubuntu"
date: 2007-08-20
forum: Desktop Environments
---

### Post by Anlace on 2007-08-20
Greetings,

I am trying to decide whether or not to stay with Ubuntu/Kubuntu and how I might be able make it work.  The thing is I'm unhappy with any number of things that are not working with Kubuntu.  Let me explain.

First Kubuntu strips many of the features that I use in KDE out completely or hides them to the point that I have to rebuild access to them myself.  Is it possible to do a Ubuntu installation without Gnome or KDE and then add in KDE without having to use Kubuntu / kubuntu-desktop?  I cannot find a straight answer for that question and my posts on the Kubuntu forum are largely ignored, people are too busy for such a simple question I guess.

I cannot play multimedia files even though I could in Kubuntu 6.04.  I have tried everything I can lay my hands on, every tutorial I could find, and Amarok still complains that there are no plugins available to play ______.  It won't play anything - not ogg (my personal favorite file format for music), or wav, or cda, or personal playlists previously created in Amarok, or anything.  Again, I have tried everything, all the files and programs it complains are missing are installed.  I gave up.

K3B and K9Copy will not start if a blank CD or DVD is already in the drive.  They just won't do it.  If I forget to start the program first I end up having to kill them because KDE thinks they are running.  If they are they can't be seen by the human eye.  I totally gave up trying to play any DVD on my computer, I don't even want to go there.

My video card apparently isn't liked by Kubuntu either.  I have added the nvidia repository and have made sure that the latest drivers are installed, configured correctly, activated, and sprinkled with holy water.  Even so, I can't simply restart or shut down from KDE, I must get to a console and sudo reboot or halt.  Pain in the butt but if I don't do that Kubuntu pushes a graphic image at too high a refresh rate (at least that's what I think is going on) because at the least I get "out of range" messages on my expensive wide screen monitor or I get horrible scrambled color bars, or and this worries me the most, the screen goes black and my graphic card sounds an on-board alarm while the temperature climbs at an alarming rate and the whole thing locks up so tight that literally pulling the plug is the only way to avoid total ruin.

So, as you can see I am not happy with Ubuntu/Kubuntu Feisty Fawn.  Yet I do wish to support the Open Source and Linux communities.  I chose Kubuntu because I really like KDE, and now I realize that Kubuntu is NOT KDE.  It's KDE for dummies and I don't want that.

I am also concerned over the length of time that the video driver has been broken with no changes in sight.  This has the potential of wrecking hardware which I would think would accelerate the need for a fix.

I am willing to spend some time tweeking my system, I have no problem with configuring a component to work but I don't have time to spend hours and hours researching, posting, and trying to troubleshoot stuff that should just work.  My system is 4 years old, there's nothing edgy or unusual about it.  All the hardware is (supposedly) supported so what gives?

In my opinion there are probably many people that feel the same way that I do that haven't said a word.  Most people won't bother to express what's on their mind, if I've learned anything in my 46 years that would be close to the top of the list.

More food for thought, I am a tech support person for an island in northwest Washington state.  Time and again I wish for a viable answer to the messed up situation that is MS Windows but I cannot in good conscious offer Kubuntu.  Most of my clients are technically challenged and can't afford to pay me for hours of troubleshooting, they are already paying me for hours of troubleshooting Windows as it is so why change to an unfamiliar platform?

I am stepping down from the soapbox now that I've had my say.  I would like more than anything else to hear someone with some intelligence tell me to just hang in there, or to try installing KDE in some manner I haven't been able to find, or that the newer version will be better and less buggy.  Something . . . . anything . . . . before I bail off this sinking ship.

Best Regards,
Gail

Intel 865GBF motherboard with onboard ethernet
Intel Pentium 4 CPU 2.8 GHz
Nvidia GeForce 6800 XT AGP video card
1 GB RAM
Creative Live! Soundcard
120 GB HD and 80 GB HD
Wireless Logitech 3200 keyboard/mouse combo
CD-ROM and DVD-RW

---

### Post by AnRa on 2007-08-20
Instead of kubuntu-desktop, you should install kde-core and some of the suggested packages from kde-extras. ;)

---

### Post by Happy_Man on 2007-08-20
Wow. Even though Kubuntu runs like a dream for me, I've heard many more stories like yours than I have heard successes. Have you tried installing regular GNOME Ubuntu? That may work better for you than KDE.

---

### Post by jrusso2 on 2007-08-20
for some reason the KDE in feisty is pretty bad, It seems like it was much better in Edgy Eft.

---

### Post by Anlace on 2007-08-20
Thanks for the replies.

> Instead of kubuntu-desktop, you should install kde-core and some of the suggested packages from kde-extras.

Ok . . . . and at what point would I do that?  Not to be ornery, but this doesn't help much since I haven't seen any option any where that asked me what I would like to install - kubuntu-desktop or kde-core.

> Have you tried installing regular GNOME Ubuntu?

Yes, I installed Ubuntu on my older laptop.  I like it well enough for its utilitarian abilities but I really like the eye candy that KDE offers.  I am also not convinced that switching over to Ubuntu will solve the issues that I am having with the nvidia driver or with multimedia play back.

Opinions?

Thanks for the feedback, this is helping me clear my thoughts about what to do next before my whole system falls apart.

Best Regards,
Gail

---

### Post by Anlace on 2007-08-20
One other thought, can someone say what the future looks like for Kubuntu?

I think I'll do some research about KDE and make very sure that it is Kubuntu and not KDE that's causing this mess.

---

### Post by aysiu on 2007-08-20
To replace Kubuntu with *kde-core*, paste this command into the terminal: ```
sudo apt-get remove acpi-support adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine anacron apmd app-install-data apport apport-qt ark avahi-autoipd avahi-daemon bc binutils bluez-cups bluez-pin bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty bsh ca-certificates cdparanoia cdrdao cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint dc debtags desktop-file-utils dhcdbd dictionaries-common digikam dvd+rw-tools fftw3 finger foo2zjs foomatic-db foomatic-db-engine foomatic-db-hpijs foomatic-filters fortune-mod fortunes-min fping freeglut3 gcc gcc-4.1 gcj-4.1-base gconf2-common gdb genisoimage gij gij-4.1 gs-common gs-esp gs-esp-x gsfonts gtk-qt-engine gwenview hotkey-setup hpijs hplip hplip-data hwdb-client-common hwdb-client-kde iso-codes k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kbstate kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards kdnssd keep kexi kghostview kio-apt kio-locate kipi-plugins kmag kmail kmailcvt kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksnapshot ksplash-engine-moodin ksvg ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal landscape-client language-selector-common language-selector-qt laptop-mode-tools lftp libakode2 libao2 libapm1 libarts1-akode libatk1.0-0 libavahi-core5 libbluetooth2 libcairo2 libcdparanoia0 libcupsimage2 libcurl3 libcurl3-gnutls libdaemon0 libdatrie0 libdirectfb-0.9-25 libexif12 libexiv2-0.12 libflac++5c2 libflac7 libgadu3 libgcj-bc libgcj-common libgcj7-0 libgconf2-4 libglade2-0 libgmp3c2 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpod1 libgs-esp8 libgsl0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgutenprint2 libhunspell-1.1-0 libicu36 libid3tag0 libidl0 libieee1284-3 libifp4 libimlib2 libjasper-runtime libjaxp1.3-java libjline-java libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmagick9 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmusicbrainz4c2a libmysqlclient15off libneon25 libnjb5 libnl1-pre6 libnm-util0 libnss-mdns libofa0 liboggflac3 libopenobex1 liborbit2 libpango1.0-0 libpango1.0-common libperl5.8 libpoppler1 libpoppler1-qt libportaudio0 libpq5 libpulse0 libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librecode0 librsync1 libruby1.8 libsamplerate0 libsane libscim8c2a libsdl1.2debian libsdl1.2debian-alsa libskim0 libslp1 libsmokeqt1 libsndfile1 libsnmp-base libsnmp9 libspeex1 libsqlite0 libstartup-notification0 libstlport5.1 libtag1c2a libtdb1 libthai-data libthai0 libtheora0 libtunepimp5 libungif4g libuniconf4.2 libusplash0 libvisual-0.4-0 libwpd8c2a libwps-0.1-1 libwrap0 libwvstreams4.2-base libwvstreams4.2-extras libx86-1 libxalan2-java libxerces2-java libxine1 libxp6 libxplc0.3.13 libxvmc1 linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic linux-headers-generic make min12xxw mscompress mysql-common network-manager networkstatus openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-kde openoffice.org-math openoffice.org-style-crystal openoffice.org-style-human openoffice.org-writer openprinting-ppds openssl patch perl-suid pnm2ppa poppler-utils powermanagement-interface powermgmt-base powernowd pykdeextensions python-apport python-dbus python-kde3 python-launchpad-bugs python-problem-report python-qt3 python-qt4 python-sip4 python-software-properties python-uno python-xdg python2.5-dev qca-tls qobex radeontool rdiff-backup readahead ruby ruby1.8 samba-common scim-qtimm screen sgml-base skim slocate smartdimmer smbclient software-properties-kde speedcrunch ssl-cert toshset ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-bitstream-vera ttf-devanagari-fonts ttf-freefont ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-opensymbol ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg unattended-upgrades unzip usplash vbetool vorbis-tools wodim wvdial x-ttcidfont-conf xbitmaps xcursor-themes xml-core xterm zip && sudo apt-get install kde-core
``` This assumes you're using Kubuntu 7.04. If you're using another version, you can find here the proper code to paste in:
[http://psychocats.net/ubuntu/kde-core](http://psychocats.net/ubuntu/kde-core)

---

### Post by Anlace on 2007-08-20
I would love to do a new install of Ubuntu without Gnome and without KDE and then install KDE from scratch.  I don't know how to do that.  The only HowTos I've seen say to first install Ubuntu Server (I do not want server software on this machine) and then install KDE.

I read something that seemed like it might work that used the Alternative CD iso.  Does anyone have any experience with that?  Would it be possible to install the Command Line System, add repositories to apt, and then apt-get what I need?  I could do this, I cut my Linux eyeteeth on Debian.

I still have concerns over the multimedia/video driver issues and whether or not I will simply replicate the problem.

Thanks for the feedback, keep it coming!

Best Regards,
Gail

---

### Post by Happy_Man on 2007-08-20
Oh, sure, yeah. That's how you do it, all right. At the bottom of the download site, there is a checkbox for the alternate install CD. Check it, and burn that. That will use a text GUI to install for you, and from there you can use the full ability of the repos to your whim.

---

### Post by aysiu on 2007-08-20
The *install a server* option on the Alternate CD doesn't actually install server software, which is why they changed the option to *install a command-line system* in the most recent version of Ubuntu.

---

### Post by Anlace on 2007-08-20
Very interesting.  I also have a window open to kde.org, it seems they are up to KDE 3.5.7 and my latest installation of Kubuntu (done in June this year) is KDE 3.5.6.  I wonder of that has resolved any of the issues I'm struggling with and if it would be worth the time and effort to upgrade?

Thoughts?

Best Regards,
Gail

---

### Post by Nythain on 2007-08-20
> **Anlace said:**
> 
First Kubuntu strips many of the features that I use in KDE out completely or hides them to the point that I have to rebuild access to them myself.  Is it possible to do a Ubuntu installation without Gnome or KDE and then add in KDE without having to use Kubuntu / kubuntu-desktop?  I cannot find a straight answer for that question and my posts on the Kubuntu forum are largely ignored, people are too busy for such a simple question I guess.

I would recommend downloading an alternate install disk, installing a command line system then building kde from scratch
> 
I cannot play multimedia files even though I could in Kubuntu 6.04.  I have tried everything I can lay my hands on, every tutorial I could find, and Amarok still complains that there are no plugins available to play ______.  It won't play anything - not ogg (my personal favorite file format for music), or wav, or cda, or personal playlists previously created in Amarok, or anything.  Again, I have tried everything, all the files and programs it complains are missing are installed.  I gave up.
cant help you here... amarok was always good at getting and installing the packages it needed to play files when i added them to the playlist... sorry
> 
K3B and K9Copy will not start if a blank CD or DVD is already in the drive.  They just won't do it.  If I forget to start the program first I end up having to kill them because KDE thinks they are running.  If they are they can't be seen by the human eye.  I totally gave up trying to play any DVD on my computer, I don't even want to go there.
as for k3b and k9copy... once again, k3b performs flawlessly for me, even outside of kde... havent messed with k9copy personally... and as for playing dvd's... i've found that xine-ui and vlc do this rather well
> 
My video card apparently isn't liked by Kubuntu either.  I have added the nvidia repository and have made sure that the latest drivers are installed, configured correctly, activated, and sprinkled with holy water.  Even so, I can't simply restart or shut down from KDE, I must get to a console and sudo reboot or halt.  Pain in the butt but if I don't do that Kubuntu pushes a graphic image at too high a refresh rate (at least that's what I think is going on) because at the least I get "out of range" messages on my expensive wide screen monitor or I get horrible scrambled color bars, or and this worries me the most, the screen goes black and my graphic card sounds an on-board alarm while the temperature climbs at an alarming rate and the whole thing locks up so tight that literally pulling the plug is the only way to avoid total ruin.
you can fix this "out of range" issue by editing your /boot/grub/menu.lst and adding
```

vga=792

```after the
```

quiet splash (or splash quiet)

```options
> 
So, as you can see I am not happy with Ubuntu/Kubuntu Feisty Fawn.  Yet I do wish to support the Open Source and Linux communities.  I chose Kubuntu because I really like KDE, and now I realize that Kubuntu is NOT KDE.  It's KDE for dummies and I don't want that.

I am also concerned over the length of time that the video driver has been broken with no changes in sight.  This has the potential of wrecking hardware which I would think would accelerate the need for a fix.
the video card driver works fine for me... then again the first thing i do is edit the /boot/grub/menu.lst to get console to a font size thats managable
> 
I am willing to spend some time tweeking my system, I have no problem with configuring a component to work but I don't have time to spend hours and hours researching, posting, and trying to troubleshoot stuff that should just work.  My system is 4 years old, there's nothing edgy or unusual about it.  All the hardware is (supposedly) supported so what gives?

In my opinion there are probably many people that feel the same way that I do that haven't said a word.  Most people won't bother to express what's on their mind, if I've learned anything in my 46 years that would be close to the top of the list.

More food for thought, I am a tech support person for an island in northwest Washington state.  Time and again I wish for a viable answer to the messed up situation that is MS Windows but I cannot in good conscious offer Kubuntu.  Most of my clients are technically challenged and can't afford to pay me for hours of troubleshooting, they are already paying me for hours of troubleshooting Windows as it is so why change to an unfamiliar platform?

I am stepping down from the soapbox now that I've had my say.  I would like more than anything else to hear someone with some intelligence tell me to just hang in there, or to try installing KDE in some manner I haven't been able to find, or that the newer version will be better and less buggy.  Something . . . . anything . . . . before I bail off this sinking ship.

Best Regards,
Gail
you mentioned that a lot of stuff worked in previous versions... have you considered installing Dapper (wich is still covered under LTS) for extra stability and support for "older" (and oh i use that term loosely since my machine is older than yours) hardware

Any more questions, concerns or comments and i would love to try to help you out... other than Kubuntu "hiding" or screwing up a lot of kde, it has worked great for me while i ran it (i will give you that Kubuntu does "hide" or alter a lot of kde, and would like to recomend again building from scratch)

---

### Post by trippinnik on 2007-08-21
There's definetly a lot of stuff there.  As to the multimedia do you have xinelibs installed?  It's the backend needed for Amarok.  I've also had to delete .xine directory to get it to work on occassion.  Sometimes Amarok (and other media players) will report that there are no codecs, and I have to delete .xine directory again.
I've just started using KDE full time, what does kubuntu hide that is in a normal install of KDE?

---

### Post by kuja on 2007-08-21
> **trippinnik said:**
> There's definetly a lot of stuff there.  As to the multimedia do you have xinelibs installed?  It's the backend needed for Amarok.  I've also had to delete .xine directory to get it to work on occassion.  Sometimes Amarok (and other media players) will report that there are no codecs, and I have to delete .xine directory again.
I've just started using KDE full time, what does kubuntu hide that is in a normal install of KDE?

I'm pretty sure it has the window menu removed, and the go menu, I forget if anything else is. 

See this link for more info: 
[http://jucato.org/kde/konq-profiles.html](http://jucato.org/kde/konq-profiles.html)

---

### Post by Anlace on 2007-08-21
Thanks for the replies, I wish I would have asked for help sooner than this!

Nythain - I have never heard of the "out of range" fix you suggested, I will do that and see if it helps.  Since I had to hand edit xorg.conf to display the desktop correctly on my 1680 X 1050 wide screen it makes sense that I'd need to edit /boot/grub/menu.lst too.

I intend to rebuild from scratch with a command-line install followed by a KDE install.  Does anyone know if xorg is installed with command-line?  I am assuming the answer is no.

I have installed all of the multimedia codecs that are mentioned in all of the HowTos, wikis, and walk-throughs I could find.  It's just weird that nothing works and it's very frustrating as well.  I gave up after hours of fussing, tweeking, reinstalling, etc etc etc.

trippinnik - The KDE functionality I miss the most that is removed in Kubuntu:

At the top of that list is how I could go to the Logout Manager and from a pull-down list choose which operating system I would like to boot into.  The program is called "NextBoot" and KDE incorporated it with version 3.4.  I tried to install it to use from Kubuntu but it ended up breaking Grub and hosing the MBR, I ended up having to reinstall Kubuntu.  See [http://www.marktaff.com/software/GRUB_NextBoot/](http://www.marktaff.com/software/GRUB_NextBoot/) for specific info about NextBoot.

Another item that I was able to find and create menu items for is the KDE Control Center.  The Kubuntu dummied down version of it is System Settings.

I have not been able to get KNetworkManager to work correctly and have filed a bug report with Kubuntu, it's still broken after 3 months but I'm not sure that it isn't another issue outside of Kubuntu's responsibility.

I could go on, but I think you get the idea.

Thanks again for the feedback, maybe this weekend I'll do the command-line install and write my own HowTo to help out others also wanting KDE without Kubuntu.

Best Regards,
Gail

---

### Post by kuja on 2007-08-21
> **Anlace said:**
> I intend to rebuild from scratch with a command-line install followed by a KDE install.  Does anyone know if xorg is installed with command-line?  I am assuming the answer is no
No, you'll need to "sudo apt-get install xorg xserver-xorg" to get that..

> **Anlace said:**
> Another item that I was able to find and create menu items for is the KDE Control Center.  The Kubuntu dummied down version of it is System Settings
To get this back in your menu: right click on the panel, go to configure. Go to the menus tab, in the scrolling box on the right check settings. It'll give you an entry for kcontrol in the menu.[/quote]

> **Anlace said:**
> I could go on, but I think you get the idea.
It's probably in your best interest to do so. The community has answers for almost anything :)

---

### Post by Nythain on 2007-08-21
yeah, my biggest complaint was kcontrol... i always have to call it from command line, because the (i forgot what the menu entry is called exactly) in the kmenu SUCKS.

as for xorg, no its not installed with a command line system... you could
```

sudo apt-get build-dep kde
or
sudo apt-get build-dep kde-core

```
to get and install all the dependencies for kde... not sure if it will work very effectively with such a large metapackage though

wish i could help you more... good luck on the kde build... ubuntu at its base is still my favorite and preferred linux distro

---

### Post by kuja on 2007-08-21
> **Nythain said:**
> yeah, my biggest complaint was kcontrol... i always have to call it from command line, because the (i forgot what the menu entry is called exactly) in the kmenu SUCKS.

as for xorg, no its not installed with a command line system... you could
```

sudo apt-get build-dep kde
or
sudo apt-get build-dep kde-core

```
to get and install all the dependencies for kde... not sure if it will work very effectively with such a large metapackage though

wish i could help you more... good luck on the kde build... ubuntu at its base is still my favorite and preferred linux distro
it's called system settings, and though it has come a long way since its beginnings I still prefer kcontrol too.

Doing the build-dep for kde will work though some things may not be up-to-date enough and might have to be installed manually, if one is to build kde from teh vanilla sources. 

I don't know that I'd recommend building it from source though. It takes hours and hours and hours, and I really couldn't see the "benefits" of doing so.

Bottom Line, so long as kubuntu-default-settings is NOT installed, you should have a fairly vanilla kde without having to go through all the headaches of starting with kde-core, or building from source.

---

