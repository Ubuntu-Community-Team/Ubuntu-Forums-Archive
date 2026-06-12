---
title: "kmenueditor"
date: 2005-08-28
forum: Desktop Environments
---

### Post by CiberAmigo on 2005-08-28
I use kde 4.3.2 and I have had a problem for a long time. It is imposible to add new menuentries width Kmenueditor. also had the same problem before I updated to 4.3.2!
 :???:  :???: 
I have search and search to find any topics on this issue, but can't find any.

Is there someone around here than post how to fix my problem?

Any help would bee apriciated! :-P 

Cencerly 
Ciberamigo

---

### Post by SGC on 2005-08-28
What happens when you click on "New Item" button on kmenueditor?

---

### Post by CiberAmigo on 2005-08-28
If I press new item I can add a new item, but when i press save it does not save the new item(s) I've added.

CiberAmigo

---

### Post by incinerator on 2005-08-28
The recommended approach for adding applications to the menu is putting .desktop files in /usr/share/applications.

Example .desktop files can be found [here](https://wiki.ubuntu.com/UniversePackageWithoutDesktopFileExampleFiles) or in the [unofficial ubuntu guide](http://ubuntuguide.org/).

---

### Post by CiberAmigo on 2005-08-28
Thank you a lot, that was quick answering. :-P 

I attend to do it that way.

Cencerly
CiberAmigo

---

### Post by CiberAmigo on 2005-08-28
Okey, I was a little exited when I answered earlyer (sorry english isn't my native).

I've putted the .desktop file i the /usr/share/application/

and nothing happend, I have restarted KDE and also restarted my pc but no new entry was to discover. [-X 

Any idea whats wrong? :???: 


cencerly
CiberAmigo

---

### Post by incinerator on 2005-08-29
You have put the file into the wrong directory, the correct one is
/usr/share/application**s**

---

### Post by CiberAmigo on 2005-08-29
Nope, I just misspelled it here in the forum. I have putted in the:
   /usr/share/applications/

Also ran 'update-menus'

I can see that the system has written it too:    /home/user/.config/menus/applications-kmenuedit.menu

But the menu still don't chance?? :???: 

Cencerly
CiberAmigo

---

### Post by incinerator on 2005-08-29
what is the name of the .desktop file, are you sure you have not overwritten another one that already existed? Also, there may be something wrong with your .desktop file itself, care to [pastebin](http://pastebin.com/) it here?

---

### Post by CiberAmigo on 2005-08-29
Hey incinerator

I don't think that there is somthing wrong with my .desktop file, byut with my system. 

I have pasted it as you requested. and the name of the of the file is: kphone.

Maybe the problem accent when I followed this adwise: [http://www.ubuntuforums.org/showthread.php?t=32220&highlight=menu-xdg](http://www.ubuntuforums.org/showthread.php?t=32220&highlight=menu-xdg)

I don't think that menu-xdg is a part of the original kubuntu, but since is was there I thougth that it was ok too install it.If I try to remove menu-xdg apt-get will also remove following packages:

akregator amarok amarok-arts amor ark artsbuilder atlantik atlantikdesigner cervisia dbus-qt-1 dcoprss eyesapplet
  fifteenapplet guarddog gwenview juk k3b k3blibs kaddressbook kaddressbook-plugins kaffeine kalarm kalzium kamera kandy
  kappfinder karm kasteroids kate kate-plugins katomic kaudiocreator kbabel kbackgammon kbattleship kbear kblackbox
  kbounce kbruch kbstate kbugbuster kcachegrind kcalc kcharselect kcontrol kcron kde-amusements kde-core kde-i18n-da
  kde-style-lipstik kde-systemsettings kdeaccessibility kdeaddons kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins
  kdeartwork kdeartwork-style kdeartwork-theme-window kdebase kdebase-bin kdebase-kio-plugins kdeedu kdegames kdegraphics
  kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs4 kdelibs4-dev kdemultimedia kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim kdepim-kfile-plugins kdepim-kio-plugins kdepim-wizards kdeprint kdesdk kdesdk-kfile-plugins
  kdesdk-misc kdesktop kdetoys kdeutils kdewebdev kdm keduca kenolaba kfilereplace kfind kfloppy kfouleggs kgamma
  kghostview kgoldrunner kgpg khangman khelpcenter kicker kicker-applets kig kimagemapeditor kitchensync kiten
  kjumpingcube klaptopdaemon klatin klettres klickety klines klinkstatus klipper kmag kmahjongg kmail kmailcvt kmenuedit
  kmessedwords kmilo kmines kmix kmoon kmousetool kmouth kmplot kmrml kmtrace knetworkconf knewsticker knode knotes kodo
  kolf kolourpaint kommander kompare konq-plugins konqueror konqueror-nsplugins konquest konserve konsole konsolekalendar
  kontact konversation kooka kopete korganizer kpager kpat kpdf kpercentage kpersonalizer kpf kpilot kpoker kppp krdc
  kregexpeditor kreversi krfb ksame ksayit kscd kscreensaver kscreensaver-xsavers kshisen ksig ksim ksirtet ksmiletris
  ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash kspy kstars ksvg ksync ksysguard kteatime ktnef ktouch ktron
  kttsd ktuberling kturtle ktux kubuntu-default-settings kubuntu-desktop kuiviewer kuser kverbos kvim kvoctrain
  kwalletmanager kweather kwifimanager kwin kwin4 kwordquiz kworldclock kxsldbg kynaptic libarts1-xine libcvsservice0
  libkcal2a libkcddb1 libkdeedu1 libkdegames1 libkdepim1 libkgantt0 libkipi0 libkleopatra0a libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 libmimelib1a librss1 lskat menu menu-xdg mpeglib networkstatus noatun
  noatun-plugins openoffice.org-kde openoffice.org2-kde quanta secpolicy smb4k umbrello vimpart xmms-kde


wich I don't think is ok.

Cencerly CiberAmigo

---

### Post by incinerator on 2005-08-29
menu-xdg is required by kdelibs-bin, therefore you should not remove it. (k)ubuntu uses it for both gnome and kde menus. I have successfully put entries for custom applications into my kde menu by putting applicationname.desktop files into /usr/share/applications/

Please pastebin that kphone.desktop file of yours.

---

### Post by CiberAmigo on 2005-08-29
ok, but was does pastebin mean?

Cencerly
CiberAmigo

---

### Post by incinerator on 2005-08-30
[http://pastebin.com/](http://pastebin.com/)
I linked to that site in my post yesterday, btw.

---

### Post by CiberAmigo on 2005-09-05
Hei incenrator

I did do a pastebin. 
But for other reason I actauly manage too destroy my system (not on purpose), so I have reinstalled (K)ubuntu.

I can only say; thanks for the help anyway ;-)

Cencerly
CiberAmigo

---

### Post by CiberAmigo on 2005-09-05
Still have the same problem after reinitalling. but now it seemes that I miss the "menu" (or not) I don't now.

In a nother treadth I found that there were repporting of a bug similar to this and a teporary solution is found:
 Alt + F2 --> kmenuedit.

It's actually work's ;-)  I can now save the chances in Kmenuedit. And some work is done to solve the bug.  :razz: 

The bugrepport is here: [https://bugzilla.ubuntu.com/show_bug.cgi?id=8030](https://bugzilla.ubuntu.com/show_bug.cgi?id=8030) 

Cencerly
Ciberamigo

---

