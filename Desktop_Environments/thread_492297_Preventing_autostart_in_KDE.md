---
title: "Preventing autostart in KDE"
date: 2007-07-04
forum: Desktop Environments
---

### Post by Cygnus on 2007-07-04
Hi, I have found some posts here about how you can create .desktop files and add to .kde/Autostart to have an application autostart with KDE. However I have the opposite problem, kwifimanager is autostarting with KDE and I do not want it to. My Autostart directory is empty so where is it specified that this and all the other applications in the tray should start ?

I could not find a setting in kwifimanager to prevent it from starting up either. I am a bit tired of closing it manually on every startup.

---

### Post by moore.bryan on 2007-07-04
[I]i'd check the [documentation]("http://docs.kde.org/stable/en/kdenetwork/kwifimanager/control-center.html#auto-configuration") on it and see if there's a setting in there.
i don't use kde, but it seems like many don't like kwifimanager ([http://ubuntuforums.org/showthread.php?t=38942](http://ubuntuforums.org/showthread.php?t=38942)); perhaps one of their other suggestions would suit you better?
[/I]

---

### Post by Cygnus on 2007-07-04
The setting in the documentation only seem to prevent a certain configuration from loading, not preventing the entire program to load which is what I am looking for.

I am already using another application (KNetworkManager) for the network which is why I do not need this to autostart. They both autostart now. KNetworkManager actually has a setting for configuring autostart.

So of course I could just uninstall kwifimanager, but I am interested in how this work. Certainly there must be a way to configure an app to not start without uninstalling the entire app ? Somewhere KDE is told to start the application, but where is this ?

---

### Post by moore.bryan on 2007-07-04
[I]okay, i think i may have found something.  according to [this thread]("http://www.linuxforums.org/forum/linux-applications/7028-kde-autostart-programs.html"), the last two choices seem your best bets.  either do what dutch kind suggests
> in the file ~/.kde/share/config/ksmserverrc are some specifics
or go with ducu13's suggestion:
> [/I]Try to look in System Settings > [Server]("http://www.linuxforums.org/forum/#")    Settings > Services .You`ll find your application here with a checkmark.Those with a checkmark nearby means that start when the system starts.

---

### Post by Cygnus on 2007-07-04
Thanks a lot :)

Ducu13's suggestion worked fine. Although the program was not listed as kwifimanager in the list but "Networkstatusdaemon". I did not know if that meant kwifimanager or knetworkmanager, but I tried it and it turned out to be the one I wanted. 

Would help of course if that list also mentioned the actual name of the applications to autostart instead of just pseudonames supposes to describe what the application does. Even more so when I am not using english and the english name I mentioned above is just my translation from swedish.

---

### Post by moore.bryan on 2007-07-04
*your explanation was fine... i'm glad you finally got it working how you wanted.  happy ubuntu-ing.*

---

