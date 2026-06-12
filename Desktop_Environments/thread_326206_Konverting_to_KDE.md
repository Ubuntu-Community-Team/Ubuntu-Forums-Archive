---
title: "Konverting to KDE"
date: 2006-12-27
forum: Desktop Environments
---

### Post by encho on 2006-12-27
I have been Gnome user for years and I liked  Gnome's philosophy of modular approach, where you have separate application for every single thing that you are doing. Being strongly against 'all-in-one' approach, I was reluctant even to try KDE. I had been using it for short period of time few years ago but was annoyed with its look and feel. I hated crystal icons and big ugly clock. And bouncing cursor. So each time I thought about going back to KDE, that picture came to my mind.

Then I moved to KDE and never looked back. (??)

This sudden move happened few weeks ago, when I was doing some website design. I was kinda forced to use KDE (luckily there was Xara installed). Than I had to upload stuff that I made. So knowing Konqueror capabilities, I opened one window and split it in three parts, one big on left for live preview of the website and 2 parts on right representing appropriate ftp and local folders. I was able to finish the website in record time (even faster than in my windows days). I was very impressed by live editing of the content using Kate.

So I have just decided to put my prejudices aside and go with productivity. If I really need job to be done efficiently, KDE is the answer. When I was gnome user I hated seeing anything qt related installed. Even my favorite K3b. KDE environment feels so much more complete; different parts of the environment speak the same language and cooperate oh so well.

There is KDE app for almost anything, including little but nice apps that mean a lot. Like Kget. Like Kwifi. Like Kshutdown. Like Kcolorpicker. Like Kanyothersmalapp. The only reason for using Gnome at the first place was bloated feeling of KDE. But, don't flame me for this, Gnome became more bloated now. Bloated but with only 10% of the KDE's functionality. Go to KDE control center and you can see what I mean. Setup samba? In Gnome you have an option to create share, make it public or not and writable. In KDE same thing, but with VERY huge difference: 'Advanced' button; not just for samba but for almost anything. So you can go one step (or two, or three) ahead and do that advanced conf. Someone will say - if you are power user, than use text editor for smb.conf. I did it. When I was using Gnome. I don't have to do it anymore. I am using KDE. 

There is some work to be done in Kubuntu to make it even better, I am sure. Like making it faster, like Sabayon. Or polished like SuSE. But there is kubuntu.org as very nice website to keep me up to date.

I have heard that new KDE 4 will be something to look at. Faster and smoother. 

Just few questions to other KDE users:
Anyone knows is it true that VLC will be qt based from now on?
How to do action scripts in konqueror (something like Thunar)?
How to do Suse-like menu?

And please note: I am not trying to convince you other people to do the same. I am just telling my story.

---

### Post by Sef on 2006-12-27
Linux is about choice and if you prefer KDE, that's cool.

---

### Post by fuscia on 2006-12-27
kde-core is faster than kubuntu. you can reduce kubuntu using aysiu's guide - [http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)
if you do that, make sure you check through the programs it removes so that you don't remove something you want to keep.

---

### Post by encho on 2006-12-27
Thanks, but I'll stick with defaults for some time, at least till I get comfortable in using it. Also some critical multimedia apps are being removed, which is not acceptable at the moment.

---

### Post by fuscia on 2006-12-27
> **encho said:**
> Thanks, but I'll stick with defaults for some time, at least till I get comfortable in using it. Also some critical multimedia apps are being removed, which is not acceptable at the moment.

you can erase them from the command before you press 'enter'.

---

### Post by Rashid584 on 2006-12-28
good story :D

about the kde-core...the idea is that reducing the number of services being run speeds things up, so which services are the main ones which removing would give the biggest speed boost?

I need things like sound, multimedia, hardware autodetection (HAL), internet (obviously!) kopete, beryl...what else is there?

-Rashid

---

### Post by mastergunner on 2006-12-28
How do you switch to KDE? I am a newb so if someone could be slow in explaing I would appreciate it.

---

### Post by qalimas on 2006-12-28
> **mastergunner said:**
> How do you switch to KDE? I am a newb so if someone could be slow in explaing I would appreciate it.


To install KDE and all Kubuntu packages:
```
sudo aptitude install kubuntu-desktop
```
To remove:
```
sudo aptitude remove kubuntu-desktop
```


Just for raw KDE (faster, less bloat, I need to try it soon):
```
sudo aptitude install kde-core
```
To remove:
```
sudo aptitude remove kde-core
```

---

### Post by groggyboy on 2006-12-29
> Just few questions to other KDE users:
Anyone knows is it true that VLC will be qt based from now on?
How to do action scripts in konqueror (something like Thunar)?
How to do Suse-like menu?

I hadn't heard this rumour about VLC going qt - it's not like it has many dependencies anyways! :D 

I'm not sure how to work with action scripts in Konqueror, but I'm sure a little forum searching would turn something up.

the KDE SUSE menu is called kicker.  Look [here]("http://www.kde-look.org/content/show.php?content=50240") for a Kubuntu-ized .deb file.  Not to be confused with SUSE's gnome menu, SLAB!

And by the way, congrats on switching to KDE, the superior DE!

---

### Post by ComplexNumber on 2006-12-29
>  Anyone knows is it true that VLC will be qt based from now on?[http://developers.videolan.org/vlc/NEWS](http://developers.videolan.org/vlc/NEWS)



>  And by the way, congrats on switching to KDE, the superior DE!the buggiest(by far) and most crash-happy DE, more like. when one always has to save their work just in case because of that dreaded feeling that an application can't be trusted not to crash at some random point.....thats KDE. i'm now back on gnome and have left all that behind.

---

### Post by chair on 2006-12-29
> How to do action scripts in konqueror (something like Thunar)? [http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html)

---

### Post by encho on 2006-12-29
> **groggyboy said:**
> 
And by the way, congrats on switching to KDE, the superior DE!

Thanks, I was waiting for someone to say something like: welcome!
> **chair said:**
> 
[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html)

It looks kinda complicated, Thunar was much easier. But there is Krusader, it has builtin customizing of the scripts.

About KDE being unstable... Not for me at least. Some time ago when I was using 3.5.1 or so, it was buggy, but I do not have that feeling anymore. It hasn't crashed since I've started using it.

What I like about kde is kubuntu.org backports. That means even if I use dapper or edgy or feisty, I could still have the latest kde. Not like general ubuntu backports (gnome will stay 2.16 in dapper - forever - unless you use 3rd party repos, which will probably break it beyond repair).

---

### Post by chair on 2006-12-29
> **encho said:**
> It looks kinda complicated, Thunar was much easier. But there is Krusader, it has builtin customizing of the scripts. It's not really, that tutorial is a little long winded, you can figure it out but just looking at the existing files.

Here's an example
```
[Desktop Entry]
ServiceTypes=text/html,text/xml,application/xml,text/rss
Actions=addAsPodcast
[Desktop Action addAsPodcast]
Name=Add as podcast to amaroK
Icon=amarok
Exec=dcop amarok playlistbrowser addPodcast %u
```

---

### Post by lift_test on 2006-12-29
> **qalimas said:**
> To install KDE and all Kubuntu packages:
```
sudo aptitude install kubuntu-desktop
```
To remove:
```
sudo aptitude remove kubuntu-desktop
```


Just for raw KDE (faster, less bloat, I need to try it soon):
```
sudo aptitude install kde-core
```
To remove:
```
sudo aptitude remove kde-core
```

Another newbie, I tried that, got a long list of "not installed" and nothing changed.  Any idea why?

---

### Post by Rashid584 on 2006-12-29
> **lift_test said:**
> Another newbie, I tried that, got a long list of "not installed" and nothing changed.  Any idea why?

copy and paste the output you got an we could tell you why :)

-Rashid

---

### Post by lift_test on 2006-12-29
> **Rashid584 said:**
> copy and paste the output you got an we could tell you why :)

-Rashid

Somewhat prolix.
vic@Time:~$ sudo aptitude install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  adept amarok avahi-daemon k3b kde-guidance kdebase-kio-plugins
  kdenetwork-filesharing kdeprint kicker kopete ksysguardd
  kubuntu-default-settings kubuntu-desktop kwin language-selector-qt
  libk3b2 libxine-main1
The following NEW packages will be automatically installed:
  amarok-xine kate kcontrol kdebase-bin kdebase-data
  kdenetwork-kfile-plugins kdepasswd kdesktop kdm kdnssd kfind khelpcenter
  klipper kmenuedit konqueror konqueror-nsplugins konversation
  kpersonalizer kpf kppp krdc krfb ksmserver ksplash ksysguard ktorrent
  kubuntu-artwork-usplash kubuntu-docs libavahi-core4 libkonq4 libruby1.8
  libtunepimp3 libvisual-0.4-0 libvisual-0.4-plugins openoffice.org-kde
The following NEW packages will be installed:
  amarok-xine kate kcontrol kdebase-bin kdebase-data
  kdenetwork-kfile-plugins kdepasswd kdesktop kdm kdnssd kfind khelpcenter
  klipper kmenuedit konqueror konqueror-nsplugins konversation
  kpersonalizer kpf kppp krdc krfb ksmserver ksplash ksysguard ktorrent
  kubuntu-artwork-usplash kubuntu-docs libavahi-core4 libkonq4 libruby1.8
  libtunepimp3 libvisual-0.4-0 libvisual-0.4-plugins openoffice.org-kde
0 packages upgraded, 52 newly installed, 0 to remove and 0 not upgraded.
Need to get 86.1MB of archives. After unpacking 229MB will be used.
The following packages have unmet dependencies:
  kubuntu-default-settings: Depends: kde-style-lipstik which is a virtual package.
                            Depends: ksplash-engine-moodin which is a virtual package.
                            Depends: kwin-style-crystal which is a virtual package.
  kdeprint: Depends: enscript which is a virtual package.
            Depends: poster which is a virtual package.
            Depends: psutils which is a virtual package.
  kwin: Depends: libxcomposite1 which is a virtual package.
  libk3b2: Depends: libdbus-qt-1-1c2 (>= 0.60) which is a virtual package.
           Depends: libflac++5c2 which is a virtual package.
           Depends: libmpcdec3 which is a virtual package.
  avahi-daemon: Depends: libdaemon0 which is a virtual package.
  kicker: Depends: libxcomposite1 which is a virtual package.
  kubuntu-desktop: Depends: akregator which is a virtual package.
                   Depends: ark which is a virtual package.
                   Depends: arts which is a virtual package.
                   Depends: bogofilter which is a virtual package.
                   Depends: gtk2-engines-gtk-qt which is a virtual package.
                   Depends: gwenview which is a virtual package.
                   Depends: kaddressbook which is a virtual package.
                   Depends: kaffeine-xine which is a virtual package.
                   Depends: kamera which is a virtual package.
                   Depends: karm which is a virtual package.
                   Depends: katapult which is a virtual package.
                   Depends: kaudiocreator which is a virtual package.
                   Depends: kcron which is a virtual package.
                   Depends: kde-systemsettings which is a virtual package.
                   Depends: kdeadmin-kfile-plugins which is a virtual package.
                   Depends: kdebluetooth which is a virtual package.
                   Depends: kdegraphics-kfile-plugins which is a virtual package.
                   Depends: kdemultimedia-kfile-plugins which is a virtual package.
                   Depends: kdemultimedia-kio-plugins which is a virtual package.
                   Depends: kdepim-kio-plugins which is a virtual package.
                   Depends: kdepim-wizards which is a virtual package.
                   Depends: keep which is a virtual package.
                   Depends: kghostview which is a virtual package.
                   Depends: kio-apt which is a virtual package.
                   Depends: kio-locate which is a virtual package.
                   Depends: klaptopdaemon which is a virtual package.
                   Depends: kmail which is a virtual package.
                   Depends: kmailcvt which is a virtual package.
                   Depends: kmilo which is a virtual package.
                   Depends: kmix which is a virtual package.
                   Depends: kmplayer-konq-plugins which is a virtual package.
                   Depends: knetworkconf which is a virtual package.
                   Depends: knotes which is a virtual package.
                   Depends: konq-plugins which is a virtual package.
                   Depends: kontact which is a virtual package.
                   Depends: kooka which is a virtual package.
                   Depends: korganizer which is a virtual package.
                   Depends: kpdf which is a virtual package.
                   Depends: krita which is a virtual package.
                   Depends: kscd which is a virtual package.
                   Depends: kscreensaver which is a virtual package.
                   Depends: ksnapshot which is a virtual package.
                   Depends: ksplash-engine-moodin which is a virtual package.
                   Depends: ksvg which is a virtual package.
                   Depends: ksystemlog which is a virtual package.
                   Depends: kubuntu-konqueror-shortcuts which is a virtual package.
                   Depends: kwalletmanager which is a virtual package.
                   Depends: libarts1-akode which is a virtual package.
                   Depends: libnss-mdns which is a virtual package.
                   Depends: qca-tls which is a virtual package.
                   Depends: scim-qtimm which is a virtual package.
                   Depends: skim which is a virtual package.
                   Depends: speedcrunch which is a virtual package.
                   Depends: vorbis-tools which is a virtual package.
                   Depends: wlassistant which is a virtual package.
  adept: Depends: debtags which is a virtual package.
         Depends: libtdb1 which is a virtual package.
  k3b: Depends: libdbus-qt-1-1c2 (>= 0.60) which is a virtual package.
  kdebase-kio-plugins: Depends: libdbus-qt-1-1c2 (>= 0.60) which is a virtual package.
  libxine-main1: Depends: libmodplug0c2 (>= 1:0.7-4.1) which is a virtual package.
                 Depends: libxvmc1 which is a virtual package.
  amarok: Depends: ruby which is a virtual package.
          Depends: python-qt3 which is a virtual package.
          Depends: libifp4 which is a virtual package.
  kdenetwork-filesharing: Depends: perl-suid which is a virtual package.
  kde-guidance: Depends: libpythonize0 which is a virtual package.
                Depends: pykdeextensions which is a virtual package.
                Depends: python-kde3 which is a virtual package.
  ksysguardd: Depends: libsensors3 (>= 1:2.9.2) which is a virtual package.
  language-selector-qt: Depends: python2.4-qt3 which is a virtual package.
  kopete: Depends: libjasper-runtime which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
adept [Not Installed]
amarok [Not Installed]
amarok-xine [Not Installed]
avahi-daemon [Not Installed]
k3b [Not Installed]
kate [Not Installed]
kcontrol [Not Installed]
kde-guidance [Not Installed]
kdebase-kio-plugins [Not Installed]
kdenetwork-filesharing [Not Installed]
kdeprint [Not Installed]
kdnssd [Not Installed]
kicker [Not Installed]
konqueror [Not Installed]
konversation [Not Installed]
kopete [Not Installed]
ksysguard [Not Installed]
ksysguardd [Not Installed]
kubuntu-default-settings [Not Installed]
kubuntu-desktop [Not Installed]
kwin [Not Installed]
language-selector-qt [Not Installed]
libk3b2 [Not Installed]
libxine-main1 [Not Installed]

Score is 206

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
vic@Time:~$

Good luck, means nothing to me, except it doesn't like something!](*,)

---

### Post by Rashid584 on 2006-12-29
lol next time put that in [ code ][ /code ] tags ;) :p

Paste your sources.list (/etc/apt/sources.list) i don't know what repository the kde stuff is in but it might be universe and you might not have universe enabled. Have you got it enabled?

-Rashid

---

### Post by lift_test on 2006-12-29
> **Rashid584 said:**
> lol next time put that in [ code ][ /code ] tags ;) :p

Paste your sources.list (/etc/apt/sources.list) i don't know what repository the kde stuff is in but it might be universe and you might not have universe enabled. Have you got it enabled?

-Rashid

Yes

---

### Post by qalimas on 2006-12-29
> **lift_test said:**
> Yes

Please run this command and paste to us the output:
```
cat /etc/apt/sources.list
```

---

### Post by lift_test on 2006-12-30
> **qalimas said:**
> Please run this command and paste to us the output:
```
cat /etc/apt/sources.list
```

Commented out the 2 lines that were causing the problem but it hung at Postfix config

---

### Post by Rashid584 on 2006-12-30
so it mostly worked?

what do you mean hung...? how long did you leave it for?

anyway, whys it need to install postfix :s postfix isnt part of kde nor a dependency... :S

-Rashid

---

### Post by Lord Illidan on 2006-12-30
Good for you...or should I say, Kood for you? :-k

I kinda like them both. I love Ubuntu Gnome's theme, it is much more welcoming than Kubuntu's default theme. Although, in Edgy, it looks nicer than in the olden days...and after coming back from FC 6...where the damn bluecurve theme literally gets on my nerves in seconds, that's saying a lot.

What I dislike about Gnome? Sometimes it is hard to konfigure things the way you want them. Screensavers are one thing, Samba is another. For that, sometimes KDE is better. But then, Gnome is pretty good at looking pretty.

---

### Post by Rashid584 on 2006-12-30
KDE can look very good too...with some customisation. I hate the default KDE and Kubuntu look personally...but what I have atm, I think looks pretty damn nice :D

I have kde-style-polyster, my own green colour scheme, beryl + dreams tiger emerald theme, a green-colourised OS X Panther wallpaper, Kiba-Dock (with a translucent white background and white border) a transparent kicker, and a white shadowed MacOS style menu bar at the top :D

Here's some shots :D

-Rashid

---

### Post by Lord Illidan on 2006-12-30
I can't say that's ugly....v. nice..i might try it.

---

### Post by Rashid584 on 2006-12-30
great :D

just ask if you want the colour scheme, wallpaper or kde-style :)

-Rashid

---

### Post by LadFromWales85 on 2007-01-03
Can't say I'm fond with the separate toolbar at the top, though I can see how that can save on screen real estate, as I assume the bar refreshes to reflect the currently selected window?

I give Beryl a go on my system, but ended up removing it as I just couldn't be bothered to tone down its rediculously over the top default settings...and I'm a minimalist

---

### Post by rctxtreme on 2007-01-03
I am a long-term KDE fan (but short-term Linux user, does that even work? :P) and after using Gnome for a while I find it better, however I experienced KDE in Mandrake (yes, before they changed to Mandriva) Move around in '04, so I think maybe KDE will be much better. But I do hate bloat. Although I do like the wide range of KDE-native apps such as Kopete, so I might as well install KDE and give it a spin. I'm not planning on core since I'm a Linux noob and I want everything I want preinstalled. Then I kill what I don't want with Add/Remove and Synaptic :)

What I don't like about Gnome: Radically different from Windows, hard to learn
What I don't like about KDE: Size of "start" is same as other icons, GIGANTIC bar.

---

### Post by Rashid584 on 2007-01-04
> **LadFromWales85 said:**
> Can't say I'm fond with the separate toolbar at the top, though I can see how that can save on screen real estate, as I assume the bar refreshes to reflect the currently selected window?

I give Beryl a go on my system, but ended up removing it as I just couldn't be bothered to tone down its rediculously over the top default settings...and I'm a minimalist

I like the menu bar at the top because of [Fitt's law](http://en.wikipedia.org/wiki/Fitts'_law). It feels more natural and easier to acquire the menu options when its at the top of the screen than if it were at the top of each window.

And yes, it changes depending on which program you have focused. 

Being a KDE user, you might assume I like lots of bloat and icons etc but I'm actually very minimalist. KDE gives me the power to get everything as minimal as I want them, thats why I like kde. (and its integration, speed, and beauty)

Having the menu bar at the top makes windows looks so much more simpler...I'll attach some examples ;) (i also remove icons I don't use etc)

As for Beryl...cant say I agree. I love all the whacky effects :D (although for a default installation I think it should be, by default, very toned down. The import function allows me to import my whacky-settings easily so Im happy :))

> **rctxtreme said:**
> I am a long-term KDE fan (but short-term Linux user, does that even work? :P) and after using Gnome for a while I find it better, however I experienced KDE in Mandrake (yes, before they changed to Mandriva) Move around in '04, so I think maybe KDE will be much better. But I do hate bloat. Although I do like the wide range of KDE-native apps such as Kopete, so I might as well install KDE and give it a spin. I'm not planning on core since I'm a Linux noob and I want everything I want preinstalled. Then I kill what I don't want with Add/Remove and Synaptic :)

What I don't like about Gnome: Radically different from Windows, hard to learn
What I don't like about KDE: Size of "start" is same as other icons, GIGANTIC bar.

You can change the KDE panel (kicker) size by right clicking, Configure Panel, Arrangment, Size "Small" or custom and change it to whatever you like. Mine is 45px.

-Rashid

---

### Post by rctxtreme on 2007-01-04
So far KDE is quite good with some colour changes and some theming. I like kde-look.org :)

And the control center link in Novell's kicker is quite good, it has much more options.

I think in a Linux mag I read before they said Gnome is good, but removes too many options so that it's not too good for a power user. But it appears they remove many other features as well, so even with the Slab it gets confusing.

One up for KDE and Novell's kicker, meanwhile I'll continue testing KDE and GNOME.

Though I may need to still install normal Ubuntu on a computer because many EasyUbuntu apps and Automatix apps when installing use Gnome for their interface, though is it possible to solve this without installing Gnome? Maybe, install GTK+2?

(btw where'd you get that vista theme, rashid?)

---

### Post by adzik on 2007-01-05
I used to use kde only, but found that I ran into a lot of apps bombing and inconsistent behavior in kde. 
I've always like kde, but I kinda' "had it" with certain things I did and used, even after correcting things manually. So gnome it is for now, and to be honest, I find it more sound overall, even if I had to sacrifice some things, which were really just details.
But this was a year and a half ago I used kde last so who knows. I am looking forward to see what KDE4 will become.
I guess in the end, that's the beauty of what we have. Freedom to choose from a vast array of choices. :)   (instead of windows xp, or windows vista which is a trick, not a choice)

---

### Post by rctxtreme on 2007-01-06
I bet you'd only save a few bucks if a free Linux distro was avaliable as OEM on the same model as a computer with Vista preinstalled.

---

### Post by LadFromWales85 on 2007-01-12
Rashid:  That does look very good, well except the fact that your using an aero theme...I tend to get wound up when I ever use Windows these days (lack of selecting copying text, no Klipper, no split pane file management, etc).

I didn't think for a second that because you used KDE you like bloat etc...I use KDE, and I definately do not like bloat, though I do not make Konqueror as minimalist as you, but I may steal some of your ideas :)

I have my Kicker at the top of the screen, always have, same with the task bar in Windows, so moving the window bar to the top of the screen perhaps wouldn't have the same effect as it does with your setup.

---

### Post by userundefine on 2007-01-12
> **Rashid584 said:**
> KDE can look very good too...with some customisation. I hate the default KDE and Kubuntu look personally...but what I have atm, I think looks pretty damn nice :D

I have kde-style-polyster, my own green colour scheme, beryl + dreams tiger emerald theme, a green-colourised OS X Panther wallpaper, Kiba-Dock (with a translucent white background and white border) a transparent kicker, and a white shadowed MacOS style menu bar at the top :D

Here's some shots :D

-Rashid
I agree that's really sweet.  I've always wanted to stick with KDE just because it gives you SO many options, but I dislike it's child's-toy default look and I never feel I'm getting anywhere in customizing so I stop.  But I likes what you gots, so I think I'll try this again. :)

---

