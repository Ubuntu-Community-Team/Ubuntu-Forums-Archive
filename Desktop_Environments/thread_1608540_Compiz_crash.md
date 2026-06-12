---
title: "Compiz crash"
date: 2010-10-29
forum: Desktop Environments
---

### Post by linkingeek on 2010-10-29
I don't know whether it's a bug or not but i'm damn sure there is something serious with KWin or Compiz.I use KUBUNTU amd64,now main question is lucid worked correctly with compiz but something is broken in Maverick,whenever applying window decoration emerald under OpenGL mode everything crashes on desktop and decorations go "off",in case of Kwin decoration KDE prompts for slow graphics(earlier it never had on previous dist.) and desktop effects go off .even Avant window Decoration(properties),Compiz effects do not work.
Now whenever i apply a lower version of compiz 0.8.4 Manually ,then packages break and again i have to update compiz to version 0.8.6.
This problem not only occurring with New installation but also on upgradation:confused:.
Please Help.
___________________________________________________________________________
Configuration:
HP Mini 
Atom N450
2gb DDR2
320 GB HD
I always use microcode.ctl for intel processor.
Never manually applied compiz ppa(on maverick) so not the victim of 0.9 version.

---

### Post by linkingeek on 2010-11-01
> I don't know whether it's a bug or not but i'm damn sure there is  something serious with KWin or Compiz.I use KUBUNTU read once again it's  KUBUNTU amd64,now main point of discussion is lucid worked correctly  with compiz but something is broken in Maverick everytime i apply window  decoration KWin prompt me for "slow desktop effects" on OpenGL mode and  everything suspends on desktop and decorations go "off".no  emerald,Avant window Decoration(properties),Compiz effects work.
Now when i Forcebly apply a lower version of compiz 0.8.4 Manually ,then  packages break and again i have to update compiz to version 0.8.6.
This problem not only occured with New installation but also with Upgradation:confused:.
Please Help.:(Is there no one to help my problem,had nobody experienced it.

To detail my problem here is the output from kwin and compiz

> dolphin@dolphin:~$ kwin --replace
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/dolphin/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

> dolphin@dolphin:~$ sudo compiz --replace
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing move options...done
Initializing resize options...done
Initializing place options...done
compiz (core) - Error: Couldn't load plugin 'decoration'

BUT i've installed each and every package

---

