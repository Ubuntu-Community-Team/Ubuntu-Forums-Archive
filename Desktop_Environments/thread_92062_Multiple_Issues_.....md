---
title: "Multiple Issues ...."
date: 2005-11-18
forum: Desktop Environments
---

### Post by matc on 2005-11-18
Hi all,

some weeks ago I migrated my computers from hoary to breezy. Most things went 
well and I was happy for a while, but the following issues are starting to 
make me regret my love to this distro.

- KDE "Autostart"
------------------------
Before breezy an inserted CD wouldn't result in any action. Now on breezy it 
constantly tries to start Konqueror (even if disc is empty or Audio CD) and 
then nags that it doesn't work. How do I turn this off?
Setting <storage_automount_enabled_hint>false</..> in /etc/hal/hald.conf 
didn't help at all.
Another attempt: changing file preferences for media/<everything> to /bin/true instead of konqueror - didn't help

- LinCVS
-----------
During the patch lincvs got removed an cannot be reinstalled because of 
missing dependencies.
libqt3c102-mt (>= 3:3.3.3)

- Console language
---------------------------------
Suddenly the console language changed to german which results in 
ununderstandable output. How do I change the console language ?

- Shutdown screen
--------------------------
Now with breezy we got a (more or less colorful and appealing) boot screen.
But why does the shutdown result in a black screen showing a blinking cursor?
Always switching to another terminal just to see whether something's going on 
sucks....

- Developping qt applications
----------------------------------------
Today the first time after weeks I found some spare time for a qt project.
But compiling has become impossible because all qt-libs and headers are 
suddenly missing and installing them is impossible....

  qt3-apps-dev: Hängt ab: libqt3-mt-dev soll aber nicht installiert werden
  qt3-examples: Hängt ab: libqt3-mt-dev (= 3:3.3.4-8ubuntu5) soll aber nicht 
installiert werden
(here i still would like english output....)

- Bluetooth and Kitchensync
--------------------------------------
I am trying to sync addressbook and calendar of Kontact to my Nokia 6630.
Despite the fact that bluetooth itself works well, the kitchensync irmcsync 
module doesn't detect my mobile phone....

- Video application
----------------------
I would need a gui to convert and cut video files. Is there anything usable in the repositories ?

Regards,

Matthias D.

---

### Post by GeneralZod on 2005-11-18
I think I can help with a handful of your problems:


[QUOTE=matc]
- KDE "Autostart"
------------------------
Before breezy an inserted CD wouldn't result in any action. Now on breezy it 
constantly tries to start Konqueror (even if disc is empty or Audio CD) and 
then nags that it doesn't work. How do I turn this off?
Setting <storage_automount_enabled_hint>false</..> in /etc/hal/hald.conf 
didn't help at all.
Another attempt: changing file preferences for media/<everything> to /bin/true instead of konqueror - didn't help
[/QUOTE]

Firstly, make sure everything is up to date - there was a bug in the intial release of Ubuntu which would cause trying to open removable media in Konqueror to fail.

As for stopping it being automatically added - this is handled by "ivman" - search the forums for it if the following thread isn't sufficient:

[http://ubuntuforums.org/showthread.php?t=70092&highlight=ivman](http://ubuntuforums.org/showthread.php?t=70092&highlight=ivman)

> 
- Shutdown screen
--------------------------
Now with breezy we got a (more or less colorful and appealing) boot screen.
But why does the shutdown result in a black screen showing a blinking cursor?
Always switching to another terminal just to see whether something's going on 
sucks....


The bootup is handled by usplash(?), but the snapshot of this app at the time Breezy was released was unable to show a splash screen on shutdown.  This probably won't be fixed until Dapper :/

> 
- Developping qt applications
----------------------------------------
Today the first time after weeks I found some spare time for a qt project.
But compiling has become impossible because all qt-libs and headers are 
suddenly missing and installing them is impossible....

  qt3-apps-dev: Hängt ab: libqt3-mt-dev soll aber nicht installiert werden
  qt3-examples: Hängt ab: libqt3-mt-dev (= 3:3.3.4-8ubuntu5) soll aber nicht 
installiert werden
(here i still would like english output....)


Something very wrong here - I have these installed.  Please post your sources.list.  I have no idea about the language - I'd say it was a system-wide locale setting, but this might not be the case if it only affects CLI apps.

---

### Post by Harleen on 2005-11-18
[QUOTE=matc]
- KDE "Autostart"
------------------------
Before breezy an inserted CD wouldn't result in any action. Now on breezy it 
constantly tries to start Konqueror (even if disc is empty or Audio CD) and 
then nags that it doesn't work. How do I turn this off?
Setting <storage_automount_enabled_hint>false</..> in /etc/hal/hald.conf 
didn't help at all.
Another attempt: changing file preferences for media/<everything> to /bin/true instead of konqueror - didn't help
[/quote]

Try changing this file: /etc/ivman/IvmConfigActions.xml
A very uncomfortable way to turn off this annoying feature. I really hope that will be improved in Dapper.

[QUOTE=matc]
- LinCVS
-----------
During the patch lincvs got removed an cannot be reinstalled because of 
missing dependencies.
libqt3c102-mt (>= 3:3.3.3)
[/quote]

That package seems to be broken.

[QUOTE=matc]- Console language
---------------------------------
Suddenly the console language changed to german which results in 
ununderstandable output. How do I change the console language ?
[/quote]

It's not ununderstandable:cool: 
The language is set by the LANGUAGE environment. Setting it like this should solve your problem: "export LANGUAGE=en_GB.UTF8"
I don't know where this setting should belong to set it system wide, but placing that line in your ~/.bashrc should work until someone clever will give the correct answer.

EDIT: found it! That setting belongs to /etc/environment

[QUOTE=matc]- Developping qt applications
----------------------------------------
Today the first time after weeks I found some spare time for a qt project.
But compiling has become impossible because all qt-libs and headers are 
suddenly missing and installing them is impossible....

  qt3-apps-dev: H&#228;ngt ab: libqt3-mt-dev soll aber nicht installiert werden
  qt3-examples: H&#228;ngt ab: libqt3-mt-dev (= 3:3.3.4-8ubuntu5) soll aber nicht 
installiert werden
(here i still would like english output....)
[/quote]

  qt3-apps-dev: depends on : libqt3-mt-dev that shouldn't be installed
  qt3-examples: depends on: libqt3-mt-dev (= 3:3.3.4-8ubuntu5) that shouldn't be installed

I'd recommend installing libqt3-mt-dev ;)

---

### Post by matc on 2005-11-18
[QUOTE=Harleen]Try changing this file: /etc/ivman/IvmConfigActions.xml[/QUOTE]
That did the job. Thanks.

[QUOTE=Harleen]
(LinCVS)
That package seems to be broken.
[/QUOTE]
:( I started liking this app... Well back to console :)


[QUOTE=Harleen]
It's not ununderstandable:cool: 
The language is set by the LANGUAGE environment. (snip)! That setting belongs to /etc/environment
[/QUOTE]
Thanks another time. The sad thing is that I understand english messages better than German ones even though I'm German myself....


[QUOTE=Harleen]
  qt3-apps-dev: depends on : libqt3-mt-dev that shouldn't be installed
  qt3-examples: depends on: libqt3-mt-dev (= 3:3.3.4-8ubuntu5) that shouldn't be installed

I'd recommend installing libqt3-mt-dev ;)[/QUOTE]

tried that several times. Didn't work.... 

What I did now: 
I switched from (damn slow) [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) to [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) and voilà :D 
After that I installed qt4, removed it and tried to reinstall qt3 it seems to work now.


Thanks GeneralZod and Harleen :)

---

### Post by Harleen on 2005-11-18
[QUOTE=matc]
:( I started liking this app... Well back to console :)
[/quote]

Who wants to return to that archaic command line? You could try cervisia as an alternative. Or compile lincvs for yourself...

[QUOTE=matc]
Thanks another time. The sad thing is that I understand english messages better than German ones even though I'm German myself....
[/quote]

Unfortunally I can really understand...
My favourite translated application is MS Visual Studio, which translates even the C++ commands(!) in some error messages.

[QUOTE=matc]
What I did now: 
I switched from (damn slow) [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) to [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) and voilà :D 
After that I installed qt4, removed it and tried to reinstall qt3 it seems to work now.
[/QUOTE]

The German mirror was down for some hours, which explains, why you couldn't intall the needed package.
No wonder it's so slow, if everyone is updating now. ;)

---

### Post by GeneralZod on 2005-11-19
[QUOTE=Harleen]Try changing this file: /etc/ivman/IvmConfigActions.xml
A very uncomfortable way to turn off this annoying feature. I really hope that will be improved in Dapper.
[/QUOTE]

KDE 3.5 includes a GUI to change the behaviour, and since 3.5 is almost certain to be in Dapper, I think you can consider your wish granted :)

Edit:

Also seconding the recommendation to check out Cervisia.

---

