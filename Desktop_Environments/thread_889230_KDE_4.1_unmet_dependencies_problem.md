---
title: "KDE 4.1 unmet dependencies problem"
date: 2008-08-13
forum: Desktop Environments
---

### Post by semijoyful on 2008-08-13
Hello, I was wondering if I was the only one experiencing this?
I wanted to give the new KDE 4.1 and spin on my Hardy Heron 64bit Ubuntu box, but I was unsuccessful.  I'll show you what I mean:

I add this source to my sources list:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

Then I enter the following in the terminal

```
~$ sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop
```

Here's the output:

```
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main 
Translation-en_US  
                         
....all those repository links...

Fetched 1B in 10s (0B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-kde4-desktop: Depends: ark-kde4 but it is not going to be installed
                        Depends: dolphin-kde4 but it is not going to be installed
                        Depends: juk-kde4 but it is not going to be installed
                        Depends: kde-window-manager but it is not going to be installed
                        Depends: kdebase-bin-kde4 but it is not going to be installed
                        Depends: kdebase-runtime-bin-kde4 but it is not going to be installed
                        Depends: kdebase-workspace-bin but it is not going to be installed
                        Depends: kdemultimedia-kio-plugins-kde4 but it is not going to be installed
                        Depends: kdm-kde4 but it is not going to be installed
                        Depends: khelpcenter-kde4 but it is not going to be installed
                        Depends: kmix-kde4 but it is not going to be installed
                        Depends: knetworkconf-kde4 but it is not going to be installed
                        Depends: konsole-kde4 but it is not going to be installed
                        Depends: kscd-kde4 but it is not going to be installed
                        Depends: ksnapshot-kde4 but it is not going to be installed
                        Depends: okular-kde4 but it is not going to be installed
                        Depends: systemsettings-kde4 but it is not going to be installed
                        Recommends: dragonplayer but it is not going to be installed
                        Recommends: gwenview-kde4 but it is not going to be installed
                        Recommends: kamera-kde4 but it is not going to be installed
                        Recommends: kate-kde4 but it is not going to be installed
                        Recommends: kdesudo-kde4 but it is not going to be installed
                        Recommends: klipper-kde4 but it is not going to be installed
                        Recommends: kmilo-kde4 but it is not going to be installed
                        Recommends: konqueror-kde4 but it is not going to be installed
                        Recommends: konqueror-nsplugins-kde4 but it is not going to be installed
                        Recommends: kopete-kde4 but it is not going to be installed
                        Recommends: kppp-kde4 but it is not going to be installed
                        Recommends: krdc-kde4 but it is not going to be installed
                        Recommends: krfb-kde4 but it is not going to be installed
                        Recommends: ksysguard-kde4 but it is not going to be installed
                        Recommends: kwalletmanager-kde4 but it is not going to be installed
E: Broken packages
```

The conclusion is that I am not able to download KDE 4.1.  Anyone know what's wrong with this picture?

Thanks!

semijoyful

---

### Post by kuja on 2008-08-13
If you go "sudo apt-get install <all of the things it listed>" it should give you the real reason why it doesn't want to do it.

---

### Post by semijoyful on 2008-08-14
I think I understand what you mean, but I am not quite sure.  All of the packages give the same sort of message.  If I try to download the apt file from for instance apt:kubuntu-kde4-desktop in a weblink, it takes me to a prompt to install additional software, but upon clicking yes to confirm it gives me this message 

"Can not install 'kubuntu-kde4-desktop' (E:Unable to correct problems, you have held broken packages.)"

Does this mean that I need to somehow delete these broken packages?  And if that is the case how do I go about doing that?

Thanks for any help!

semijoyful:-k

---

### Post by kuja on 2008-08-14
```
sudo apt-get install kubuntu-kde4-desktop ark-kde4 dolphin-kde4 juk-kde4 kde-window-manager kdebase-bin-kde4 kdebase-runtime-bin-kde4 kdebase-workspace-bin kdemultimedia-kio-plugins-kde4 kdm-kde4 khelpcenter-kde4 kmix-kde4 knetworkconf-kde4 konsole-kde4 kscd-kde4 ksnapshot-kde4 okular-kde4 systemsettings-kde4 dragonplayer gwenview-kde4 kamera-kde4 kate-kde4 kdesudo-kde4 klipper-kde4 kmilo-kde4 konqueror-kde4 konqueror-nsplugins-kde4 kopete-kde4 kppp-kde4 krdc-kde4 krfb-kde4 ksysguard-kde4 kwalletmanager-kde4
```


Is what I meant.

---

### Post by semijoyful on 2008-08-14
Gottcha...I'll try it and post back.  Thank you!
semijoyful

---

### Post by semijoyful on 2008-08-15
I tried your suggestion, and this is the result:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ark-kde4: Depends: kdebase-runtime but it is not going to be installed
            Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
  dolphin-kde4: Depends: kdebase-runtime but it is not going to be installed
                Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
                Depends: libkonq5 but it is not going to be installed
                Depends: libsoprano4 (>= 2.0.98) but it is not going to be installed
  dragonplayer: Depends: kdebase-runtime but it is not going to be installed
                Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
  gwenview-kde4: Depends: kdebase-runtime but it is not going to be installed
                 Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
                 Depends: libkipi5 but it is not going to be installed
  juk-kde4: Depends: kdebase-runtime but it is not going to be installed
            Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
  kamera-kde4: Depends: kdebase-runtime but it is not going to be installed
               Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
  kate-kde4: Depends: kdebase-runtime but it is not going to be installed
             Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
             Depends: libplasma2 but it is not going to be installed
  kde-window-manager: Depends: kdebase-runtime but it is not going to be installed
                      Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
                      Depends: libkdecorations4 but it is not going to be installed
                      Depends: libkwineffects1 (>= 4:4.1.0) but it is not going to be installed
  kdebase-bin-kde4: Depends: kdebase-runtime but it is not going to be installed
                    Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
  kdebase-runtime-bin-kde4: Depends: kdebase-runtime but it is not going to be installed
                            Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
  kdebase-workspace-bin: Depends: kdebase-plasma-kde4 but it is not going to be installed
                         Depends: kdebase-runtime but it is not going to be installed
                         Depends: kdebase-workspace-libs4+5 but it is not going to be installed
                         Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
                         Depends: libplasma2 but it is not going to be installed
                         Depends: libsoprano4 (>= 2.0.98) but it is not going to be installed
  kdemultimedia-kio-plugins-kde4: Depends: kdebase-runtime but it is not going to be installed
                                  Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
                                  Depends: libkcddb4-kde4 (= 4:4.1.0-0ubuntu1~hardy1~ppa1) but it is not going to be installed
  kdesudo-kde4: Depends: kdebase-runtime but it is not going to be installed
                Depends: kdelibs5 (>= 4:4.0.1-0ubuntu1) but it is not going to be installed
  kdm-kde4: Depends: kdebase-runtime but it is not going to be installed
            Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
  khelpcenter-kde4: Depends: kdebase-runtime but it is not going to be installed
                    Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
  klipper-kde4: Depends: kdebase-runtime but it is not going to be installed
                Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
  kmilo-kde4: Depends: kdebase-runtime but it is not going to be installed
              Depends: kdelibs5 (>= 4:4.0.3-0ubuntu3) but it is not going to be installed
  kmix-kde4: Depends: kdebase-runtime but it is not going to be installed
             Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
  knetworkconf-kde4: Depends: kdebase-runtime but it is not going to be installed
                     Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
  konqueror-kde4: Depends: kdebase-runtime but it is not going to be installed
                  Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
                  Depends: libkonq5 but it is not going to be installed
  konqueror-nsplugins-kde4: Depends: kdebase-runtime but it is not going to be installed
                            Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
  konsole-kde4: Depends: kdebase-runtime but it is not going to be installed
                Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
  kopete-kde4: Depends: kdebase-runtime but it is not going to be installed
               Depends: kdelibs5 (>= 4:4.1.0-0ubuntu11~hardy1~ppa1) but it is not going to be installed
               Depends: kdepimlibs5 (>= 4:4.0.83) but it is not going to be installed
  kppp-kde4: Depends: kdebase-runtime but it is not going to be installed
             Depends: kdelibs5 (>= 4:4.1.0-0ubuntu11~hardy1~ppa1) but it is not going to be installed
  krdc-kde4: Depends: kdebase-runtime but it is not going to be installed
             Depends: kdelibs5 (>= 4:4.1.0-0ubuntu11~hardy1~ppa1) but it is not going to be installed
  krfb-kde4: Depends: kdebase-runtime but it is not going to be installed
             Depends: kdelibs5 (>= 4:4.1.0-0ubuntu11~hardy1~ppa1) but it is not going to be installed
  kscd-kde4: Depends: kdebase-runtime but it is not going to be installed
             Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
             Depends: libkcddb4-kde4 but it is not going to be installed
  ksnapshot-kde4: Depends: kdebase-runtime but it is not going to be installed
                  Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
  ksysguard-kde4: Depends: kdebase-runtime but it is not going to be installed
                  Depends: kdebase-workspace-libs4+5 but it is not going to be installed
                  Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
                  Depends: libplasma2 but it is not going to be installed
  kwalletmanager-kde4: Depends: kdebase-runtime but it is not going to be installed
                       Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
  okular-kde4: Depends: kdebase-runtime but it is not going to be installed
               Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1~ppa3) but it is not going to be installed
               Depends: libokularcore1-kde4 but it is not going to be installed
  systemsettings-kde4: Depends: kdebase-runtime but it is not going to be installed
                       Depends: kdelibs5 (>= 4:4.1.0-0ubuntu1~hardy1) but it is not going to be installed
E: Broken packages
```


Any idea where to go from here?

Thank you for your help!

semijoyful

---

### Post by moise7864 on 2008-08-28
You just need to enable the backports repository in System > Administration > Software sources > updates. (In ubuntu)

Or add these lines to your source.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe

---

### Post by domino1241 on 2009-05-20
> **moise7864 said:**
> You just need to enable the backports repository in System > Administration > Software sources > updates. (In ubuntu)

Or add these lines to your source.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe

That fixed it for me.  Thanks.

---

