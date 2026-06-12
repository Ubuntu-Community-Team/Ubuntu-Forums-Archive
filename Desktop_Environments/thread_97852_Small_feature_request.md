---
title: "Small feature request"
date: 2005-12-01
forum: Desktop Environments
---

### Post by tomane on 2005-12-01
Greetings,

I've tried Hoary and Breezy with the gnome desktop and currently use breezy, after installing the kubuntu-desktop package.

I prefer kde because of its much greater flexibility and means of customization. Gnome is too much minimalistic and I can't get it to look and act the way I'd like it to.

The issue in installing the kubuntu-desktop package is that I got a whole plaethora of packages that I won't need but clutter my menu and, somehow, my hard disk too.

What I'd like to have is a minimal (meta) package - after searching in synaptic, I couldn't find any - that would depend only on the least packages required to run the kde desktop. Of course, this sounds very abstract as the idea of a basic desktop varies from user to user. What I'd like to see as "minimal" was the core, themes, artwork, basic text editor, base internet apps (browser and email), configuration tools (network, menu editor, control centre), multimedia player, and probably not much beyond that. Then We'd have the ability to choose and install other packages, based on what we needed, therefore reducing the number of installed packages on the system.

I believe a thiner kde desktop might even turn out to be more actractive because of its higher simplicity. For instance, the user wouldn't need more than 2 seconds to find the right item on a menu :-) although he'd probably would have to install aditional packages in order to get his box doing some usefull stuff.

On a final note, the clumsiness I mentioned might also be caused by having gnome and gnome apps installed before installing kde, resulting in gnome and kde apps coexisting and having 2 or 3 apps to do pretty the same thing. If the kubuntu install cd covers this issue and provides a mean of installing the minimal desktop, please accept my apologies fot the long post and time lost reading it. ;-)

Regards.

---

### Post by sanguinemoon on 2005-12-01
A smaller KDE sort of makes sense. The only thing would KDE is not a Ubuntu product, and as such are they even legally allowed to change what KDE contains?

I don't have a problem with having both KDE and Gnome apps. In fact, some Gnomes apps I prefer to the KDE and vice versa. 

I have a question though. I'm not sure if this matters or not, but have you tried just installing KDE and not the whole Kubuntu-desktop? You might be able to get a thinner KDE that way?

---

### Post by aysiu on 2005-12-01
[QUOTE=sanguinemoon]I'm not sure if this matters or not, but have you tried just installing KDE and not the whole Kubuntu-desktop? You might be able to get a thinner KDE that way?[/QUOTE] Kubuntu-desktop installs this on top of Gnome ```
  adept akregator amarok amarok-gstreamer ark arts debtags enscript
  gtk2-engines-gtk-qt gwenview imagemagick ivman kaddressbook kaffeine
  kaffeine-gstreamer kamera kappfinder karm katapult kate kaudiocreator kcron
  kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon
  klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins
  konqueror-nsplugins konserve konsole kontact konversation kooka kopete
  korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver
  ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager
  kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1
  libkipi0 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1
  libksieve0 libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0
  libpythonize0 libsensors3 libtdb1 openoffice.org2-kde poster psutils
  python-kde3 python-opengl python2.4-dev python2.4-kde3 python2.4-opengl
  python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch
  ttf-dejavu xlibs
``` KDE installs this on top of Gnome ```
  akregator ark arts enscript imagemagick kaddressbook kaddressbook-plugins
  kalarm kamera kandy kappfinder karm kate kate-plugins kaudiocreator
  kbugbuster kcron kde kde-amusements kde-core kdeaddons kdeadmin
  kdeadmin-kfile-plugins kdeartwork kdeartwork-theme-window kdebase
  kdegraphics kdegraphics-kfile-plugins kdemultimedia
  kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim kdepim-kfile-plugins
  kdepim-kio-plugins kdepim-wizards kdeprint kdesdk kdetoys kdeutils
  kghostview khelpcenter kicker kitchensync klaptopdaemon kleopatra klipper
  kmail kmailcvt kmenuedit kmilo kmix knewsticker knode knotes konq-plugins
  konqueror-nsplugins konsole konsolekalendar kontact kooka kopete korganizer
  kpdf kpf kpilot kppp krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash
  ksvg ksync ksysguard ksysguardd kteatime ktnef kuser kwalletmanager
  kwifimanager kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1
  libkdepim1 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1
  libksieve0 libktnef1 libmimelib1a libsensors3 poster psutils
```

---

### Post by sanguinemoon on 2005-12-02
I see.

Probably the best thing is just to go through Synpatic and see what packages he wants and remove ones that he doesn't. Just be carefull of and pay attention to the dependencies, though!

---

### Post by tomane on 2005-12-02
This was my first kubuntu/kde install and I just selected the kubuntu-desktop package since it was what was instructed in many places. I'll give a shot at the kde package when I need to install the distro on another machine, which might be soon, anyway.
When I'm on a cleaning spree, I open synaptic and go through the installed packages/descriptions, trying to find surplus stuff. After a few of these sessions I still find stuff to uninstall without loosing any of the functionality I want. Luckily for me, apt handles dependencies really well and everything keeps consistent.

Thanks for all the help.

---

### Post by sanguinemoon on 2005-12-02
Sure. Have fun cleaning out the nonsense. That's what I did myself ;)

---

### Post by mrsva on 2005-12-02
[QUOTE=tomane]
What I'd like to have is a minimal (meta) package
[/QUOTE]

Isn't [FONT="Courier New"]kdebase[/FONT] what you are looking for? From the package description:


> This metapackage includes the nucleus of KDE, namely the minimal package set necessary to run KDE as a desktop environment. This includes the window manager, taskbar, control center, a text editor, file manager, web browser, X terminal emulator, and many other programs and components.

If so,

[FONT="Courier New"]apt-get install kdebase[/FONT]

instead of 

[FONT="Courier New"]apt-get install kubuntu-desktop[/FONT]

Hope this helps! :-)

Marcio

---

### Post by tomane on 2005-12-02
[quote=mrsva]Isn't [FONT=Courier New]kdebase[/FONT] what you are looking for?[/quote] Sounds like it is... Too bad I didn't bump into it before ](*,)

> Hope this helps! :-) It does. Many thanks.
--Antonio

---

### Post by sanguinemoon on 2005-12-02
Can you actually boot into that and have a fully functional desktop though? Also I would want some things like Kaffeine and Xine and too.

---

### Post by tomane on 2005-12-02
Quite probably, no.
We'd probably have to manually browse synaptic and choose multimedia apps, codecs, etc...
The tools needed to do some actually usefull work will probably have to be installed too.
The diference is that instead of having 2 or 3 packages that serve the same purpose, we'd have only one. Even if I wanted to try several alternatives to perform the same function, I can roll back and choose another package and more easilly keep track of what is installed on my system.

---

### Post by tomane on 2006-03-05
I just installed from a kubuntu install CD and found the result quite sleek and clean.

just for the record ;-)

---

