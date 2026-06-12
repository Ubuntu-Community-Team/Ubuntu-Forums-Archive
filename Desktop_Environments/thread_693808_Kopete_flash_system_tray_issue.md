---
title: "Kopete: flash system tray issue"
date: 2008-02-11
forum: Desktop Environments
---

### Post by Helios89 on 2008-02-11
Hi folks,
i'm using gnome 2.20.1 on ubuntu 7.10

it's been a few days that kopete does not flash anymore on the system tray at the bottom of the screen when somebody messages me.

I installed kde4-core and then removed and then reinstalled again. I hope this is a useless information for my problem.

Any ideas?

Thanks in advance, you guys :guitar:

---

### Post by linuxwizard on 2008-02-11
Have you checked your notification settings to make sure something didn't change ? Open Kopete > settings > configure notifications

---

### Post by harold4 on 2008-02-11
Is it kopete or kopete-kde4 that you're using?

---

### Post by Helios89 on 2008-02-11
i currently use kopete, i never used the kde4 version.

I checked in settings > configure notification

but everything seems to be fine.

"an incoming message" is set to "mark taskbar" (that's the bar at the bottom of the screen in the default gnome configuration, i guess, and the one i would like to flash)

:S i still have no ideas.

---

### Post by harold4 on 2008-02-11
[Maybe]("http://kopete.kde.org/faq.php#TheflashingtaskbarnotificationsarentworkingformebutIstillseepassivepopupswhenpeoplecomeonlineorgoawayWhydoesntthetaskbarflash")

---

### Post by Helios89 on 2008-02-11
Uhm since i haven't compiled nothing it's very strange

```
davide@hati:~$ dpkg -l | grep kdelibs
ii  kdelibs-data                               4:3.5.8-0ubuntu3.2                        core shared data for all KDE applications
ii  kdelibs4c2a                                4:3.5.8-0ubuntu3.2                        core libraries and binaries for all KDE appl
ii  kdelibs5                                   4:4.0.1-0ubuntu1~gutsy1~ppa2.1            core libraries for all KDE 4 applications
ii  kdelibs5-data                              4:4.0.1-0ubuntu1~gutsy1~ppa2.1            core shared data for all KDE 4 applications

```

i am kinda noob :D 

what should i do next?

---

### Post by harold4 on 2008-02-11
Do you get a flash when using kopete in KDE?

Either try purging the kde4-core to see if there is a conflict of some sort, or install kopete-kde4 and see if that'll flash.

---

### Post by Helios89 on 2008-02-12
Now i have completely remove any kde4 binary/config file

and kopete-kde4 didn't work. :S

it said me "command not found" but it was installed, as i removed it "sudo apt-get remove kopete-kde4"

:S sooo strange

---

### Post by harold4 on 2008-02-18
if you uninstalled kopete-kde4 before executing the command, it was uninstalled, so it would not find the command.

I just tested kopete that comes bundled with kde 3.5.8 and I get a flash and also get feedback when using AWN.  

Since you have kde4-ppa packages installed, it's possible these broke kopetes flashing feedback, since those are not official packages.

You can try uninstalling kde4 packages and restarting X to see if that does the trick.

---

### Post by Helios89 on 2008-02-18
> **harold4 said:**
> if you uninstalled kopete-kde4 before executing the command, it was uninstalled, so it would not find the command.

I just tested kopete that comes bundled with kde 3.5.8 and I get a flash and also get feedback when using AWN.  

Since you have kde4-ppa packages installed, it's possible these broke kopetes flashing feedback, since those are not official packages.

You can try uninstalling kde4 packages and restarting X to see if that does the trick.

I tried to execute the command right after instaling kopete-kde4 but that it's not an issue relevant ( i guess was a problem with symbolic links or sth else similar)

i know that kopete from kde 3.5.8 works fine, i have been using it for a lot of time and only recently it has this (annoying) issue.

I uninstalled all the kde4 packages and restarted x (and rebooted pc, also) several times but nothing worked.

---

### Post by harold4 on 2008-02-18
Give tihs a try.  This should undo what was bonked by the kde4 libs.

```
sudo apt-get install --reinstall kdelibs-data kdelibs4c2a kopete
```

---

### Post by Helios89 on 2008-02-19
Nope :((((

Maybe it's a taskbar issue from gnome?

---

### Post by harold4 on 2008-02-21
Did some testing and found i only get flashes when the window is open and out of view.

---

### Post by Helios89 on 2008-02-21
Well it is normal that it flashes when minimized and you are working onto some other window but in my case it never flashes. 

:( really dunno what to think..and it's kinda annoying...the delay until my reply makes my contact angry :P

---

### Post by harold4 on 2008-02-21
Toss up a screenshot of your settings in "behavior > events"

---

### Post by Helios89 on 2008-02-21
[IMG]http://www.andvari.it/docs/events.png[/IMG]

here you are :)

---

### Post by harold4 on 2008-02-21
Our only difference is that you have "button ignore closes chat" selected.  

Out of curiosity, see if changing your window theme allows flashing.  I've seen some themes that will disallow kopete to flash.

---

### Post by Helios89 on 2008-02-21
I have always used this windows theme, but i will give this a try, not having better ideas..

---

### Post by harold4 on 2008-02-21
Also, do a package search for "arts" to see which packages/versions you have installed.

---

### Post by Helios89 on 2008-03-01
```
$ dpkg -l | grep arts
ii  libarts1c2a                                1.5.8-0ubuntu1                           aRts sound system core components
ii  libartsc0                                  1.5.8-0ubuntu1                           aRts sound system C support library

```

here it is

(sorry for the delay, i've been in paris these days :) )

---

### Post by harold4 on 2008-03-01
Here's my output of dpkg -l | grep arts
```

arts                                       1.5.8-0ubuntu1
libarts1-akode                             4:3.5.8-0ubuntu1                
libarts1-dev                               1.5.8-0ubuntu1                     
libarts1c2a                                1.5.8-0ubuntu1                     
libartsc0                                  1.5.8-0ubuntu1                       
libartsc0-dev                              1.5.8-0ubuntu1                      

```

---

### Post by Helios89 on 2008-03-02
now i've been able to install some other arts packages (not all because a couple of them gave me error in matter of dep)

```
davide@hati:~$ dpkg -l | grep arts
ii  arts                                       1.5.8-0ubuntu1                           sound system from the official KDE release
ii  libarts1-akode                             4:3.5.8-0ubuntu1                         akode plugin for aRts
ii  libarts1c2a                                1.5.8-0ubuntu1                           aRts sound system core components
ii  libartsc0                                  1.5.8-0ubuntu1                           aRts sound system C support library

```

but now i think i figured out what is the problem:

```
ii  metacity                                   1:2.21.8-0ubuntu2~pollycoke1             A lightweight GTK2 based Window Manager
ii  metacity-common                            1:2.21.8-0ubuntu2~pollycoke1             Shared files of lightweight GTK2 based Windo

```

i have this version of metacity which is unofficial (from a popular linux "evangelist" here in italy who releases packages upgraded)

i think that going back to the previous version could be solve the problem, but how to do that? And what is your version of metacity?

---

### Post by harold4 on 2008-03-02
I have since dumped gnome, so no version of metacity :-P

Comment out the offending repo, then

```
 sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update
sudo apt-get install --reinstall <package-name>
```

---

### Post by Helios89 on 2008-03-03
```
$ sudo apt-get install --reinstall metacity
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
La reinstallazione di metacity non è possibile, non può essere scaricato.

```

It is in italian, but it says that reinstallation of metacity is not possibile, it cant be downloaded.

---

### Post by harold4 on 2008-03-03
Funky.  What does "apt-cache search metacity" return?

---

### Post by Helios89 on 2008-03-03
```
davide@hati:~$ apt-cache search metacity
amor - a KDE creature for your desktop
human-theme - Human theme
libmetacity-dev - Development files of lightweight GTK2 based Window Manager
backstep - Draws icons for minimized windows on your desktop
blubuntu-theme - Blubuntu look - GTK and Metacity theme
gnome-themes-extras - various themes for the GNOME 2 desktop
gray-theme - Gray GTK theme
gtk2-engines-spherecrystal - A blue vector theme for GTK+ 2.x
industrialtango-theme - Industrial Tango GTK theme
kwin-style-alphacube - Alphacube window decoration for KDE
legacyhuman-theme - Legacy Human GTK theme
metacity-themes - Themes for the Gtk2 metacity window manager
outdoors-theme - Outdoors GTK theme
peace-theme - Peace look - GTK and Metacity theme
resilience-theme - Resilience GTK theme
silicon-theme - Silicon GTK theme
tropic-theme - Tropic look - GTK and Metacity theme
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
wmctrl - control an EWMH/NetWM compatible X Window Manager
compiz-gnome - OpenGL window and compositing manager - GNOME window decorator
metacity - A lightweight GTK2 based Window Manager
metacity-common - Shared files of lightweight GTK2 based Window Manager
libmetacity0 - library of lightweight GTK2 based Window Manager
```

---

### Post by harold4 on 2008-03-03
```
metacity - A lightweight GTK2 based Window Manager
metacity-common - Shared files of lightweight GTK2 based Window Manager
libmetacity0 - library of lightweight GTK2 based Window Manager
```

You can't reinstall any/all of those?

---

### Post by Helios89 on 2008-03-04
Nope. All the same message, they can't be downloaded :confused:

---

### Post by harold4 on 2008-03-04
What displays for
```
ls /var/cache/apt/archives | grep meta*

```

---

### Post by Helios89 on 2008-03-04
nothing :(

---

### Post by harold4 on 2008-03-05
apt-get can't install what it doesn't have access to :-P

What's your /etc/apt/sources.list look like?

---

### Post by Helios89 on 2008-03-05
here:

[URL="http://www.andvari.it/docs/sources.list"]
/etc/apt/sources.list[/URL]

[/etc/apt/sources.list.d/extra.list]("http://www.andvari.it/docs/extra.list")

still confused :confused:

---

### Post by harold4 on 2008-03-07
Looks fine.  I bet there is still some lingering packages from a non-official repo that has things breaking.

---

### Post by Helios89 on 2008-03-07
then, what do you suggest me to do?

thanks in advance, however ;)

---

### Post by harold4 on 2008-03-08
In synaptic, search "name and description" for "ppa" and see what is installed.

---

### Post by Helios89 on 2008-03-09
i thought that dpkg -l | grep ppa was better :P

```
rc  kdebase-kio-plugins                        4:3.5.8-2ubuntu3~gutsy1~ppa1             core I/O slaves for KDE
rc  kdebase-runtime-data                       4:4.0.1-0ubuntu1~gutsy1~ppa1             shared data files for the KDE base runtime m
rc  kdebase-workspace-bin                      4:4.0.1-0ubuntu2~gutsy1~ppa1             core binaries for the KDE 4 base module
rc  kdebase-workspace-data                     4:4.0.1-0ubuntu2~gutsy1~ppa1             shared data files for the KDE 4 base module
rc  kdelibs5                                   4:4.0.1-0ubuntu1~gutsy1~ppa2.1           core libraries for all KDE 4 applications
rc  kdepimlibs5                                4:4.0.1-0ubuntu1~gutsy1~ppa1             core libraries for KDE PIM 4 applications
rc  kdesktop                                   4:3.5.8-2ubuntu3~gutsy1~ppa1             miscellaneous binaries and files for the KDE
rc  libkonq4                                   4:3.5.8-2ubuntu3~gutsy1~ppa1             core libraries for Konqueror
rc  libkonq5                                   4:4.0.1-0ubuntu2~gutsy1~ppa1             core libraries for KDE 4's Konqueror
rc  libphonon4                                 4:4.0.1-0ubuntu1~gutsy1~ppa2.1           cross-platform multimedia framework (runtime
rc  libplasma1                                 4:4.0.1-0ubuntu2~gutsy1~ppa1             library for the plasma KDE 4 desktop
rc  libstreamanalyzer0                         0.5.7-1~gutsy2~ppa1                      streamanalyzer library for Strigi Desktop Se
rc  libstreams0                                0.5.7-1~gutsy2~ppa1                      streams library for for Strigi Desktop Searc
rc  libstrigiqtdbusclient0                     0.5.7-1~gutsy2~ppa1                      library for writing D-Bus clients for Strigi
ii  python-sip4                                4.7.1-1ubuntu1~gutsy0~ppa1               Python/C++ bindings generator runtime libraries

```

:S i thought i had removed all those (AUTOCENSORED) packages from kde4. They are everywhere, they are alive! :P

---

### Post by Helios89 on 2008-03-16
any other idea?

---

### Post by harold4 on 2008-03-16
Are you able to uninstall the ppa pkgs for the official repo alternatives?

---

### Post by Helios89 on 2008-03-17
Well, as you can see most of them are only rc, or configuration file remaining from previous installations. I can remove them but I doubt it would be useful. The only thing currently installed is python, but I dont know how much could affect kopete..

(and i still cannot reinstall metacity)

---

### Post by Helios89 on 2008-05-26
When I had some issue that made me format and reinstall Ubuntu 7.10, this problem was solved (my home directory was not touched, however).

Now, this problem returned. And i no longer have ppa packages installed.

So annoying :evil:

---

