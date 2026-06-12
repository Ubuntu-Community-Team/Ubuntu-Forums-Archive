---
title: "Can't login to Kubuntu"
date: 2008-02-12
forum: Desktop Environments
---

### Post by Danteleo on 2008-02-12
I am having a problem login into KDE. When I try to login I the screen goes to the load up screen for ~15 seconds and then kicks me back to the login screen.

I am able to login using Failsafe but, not the Default or KDE session.

 I have read the other related posts regarding this problem and they all point to the computers disk being full. I have checked mine (df -h) and have 12% available so I know drive space is not the issue.

The last time I logged off I left to files open (which I have done in the past) and normally when I start my computer back up it just opens those applications or files. Could that be the problem?

I also had an update today prior to shuting down my computer...

Any assistace would be appreciated.

---

### Post by taurus on 2008-02-12
Maybe look in ~/.xsession-errors to see if there is any error message about your session.

```
tail -20 ~/.xsession-errors
```

---

### Post by Danteleo on 2008-02-12
I get this error

kdeinit: Communications error with launcher. Exiting!
kdecore (Kprocess): WARNING: _attachPty() 10


BTW...I can login from the recovery console as root using startx


Thx

---

### Post by Danteleo on 2008-02-12
Okay... I'm looking through the errors again and I see that I have an couple of errors that look like this.

kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po

The reason this caught my eye is because there was an update to the language packs today. Could this be causing the error???

---

### Post by Danteleo on 2008-02-12
Two new errors.

konsole: WARNING: Unable to use  /usr/share/apps/konsole/mc.desktop
konsole: WARNING: Unable to use  /usr/share/apps/konsole/sumc.desktop


I got this as a suggestion from another forum...is it valid?

check the permissions of the user's home dir to make sure that the user is the owner of their home and has read and write permissions.

also check your system log eg /var/adm/messages file to see if any errors.

It might be an NFS mount error if the user's home dir is mount from a NFS server.

---

### Post by Danteleo on 2008-02-12
I have also tried creating a new user and logging in that way but get the same result.

---

### Post by freecouch on 2008-02-12
I am having this same problem.  Any help would be greatly appreciated.  The problem started immediately after today's update.  kicker crashed after (during?) the update.  I couldn't restart it so I logged out, and now can't login again.  I can log in to Gnome, but not KDE.

# tail -20 ~/.xsession-errors

> 
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po
kdeinit: Communication error with launcher. Exiting!
Warning: connect() failed: : Connection refused
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po
startkde: Shutting down...
Warning: connect() failed: : Connection refused
Error: Can't contact kdeinit!
ICE default IO error handler doing an exit(), pid = 7490, errno = 0
startkde: Running shutdown scripts...
startkde: Done.


# tail /var/log/kdm.log

> 
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 3, should be 2; fixing.
(EE) AIGLX: Screen 0 is not DRI capable
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po


---

### Post by yperiard on 2008-02-12
Same problem here. Logs displays the same problem.

There is enough disk space on the machine. Found another post concerning the .ICEAuthority file might be owned by root causing login problem, but this is not the case here.

restarted kdm in console as root from /etc/init.d no change

Also did the update just an hour ago.

All my users login on the system display the same problem.


Hoping someone can find more.


Thanks

---

### Post by Danteleo on 2008-02-12
As sad as this may sound I have to say I feel a bit more relieved that I'm not the only one and that it appears to do to the update that happened today.

I guess my first question is how can the updates be "rolled" back?


This would confirm that it's due to the updates.

---

### Post by rmorris99 on 2008-02-13
This is indeed a language problem. 

dpkg -r language-pack-kde-en
dpkg -r language-pack-kde-en-base

or whatever other kde language packs are installed.

There's a bug report in that also says you can change the language to us-english and that will fix it as well.
[https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/191327](https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/191327)

sudo qt-language-selector --mode select 

I re-installed my system at work this morning because of this. It's pretty stupid that a language pack problem would cause a complete failure of kde.

---

### Post by rflight79 on 2008-02-16
Of all the stupid things. I'm glad I found this before I just decided to start over from scratch.

the 'qt-language-select' failed for me because it said it couldn't connect to a valid X-server, go figure that's because I couldn't get one to start!

Also, 

dpkg -r language-pack-kde-en
dpkg -r language-pack-kde-en-base

failed because the two packages depend on one another.

I used:

sudo apt-get remove language-pack-kde-en

which then allowed it to remove any other dependent packages.

Hope someone else finds this thread before doing a reinstall.

---

### Post by benmoreassynt on 2008-02-25
This is a crazy bug. There have been loads of language issues with Feisty and non English-us languages, including borked menus in KDE. After upgrading the language packs yesterday, I woke up this morning to find Kontact would not check mail (I use it in Gnome), Katapult would not work and KDE would not launch.

The posts above are the solution, and I imagine a lot of people need to know that simple but totally counterintuitive solution.

---

### Post by khuegele on 2008-02-25
Thank you, thank you, thank you!!!:guitar::guitar::guitar:

I am soooo glad I found this thread.  I thought it was something I did.  I removed the package and was able to login.  Now I can get back to work.

Thank you very much for your kind assistance.

---

### Post by mcgrovia on 2008-02-26
Thanks for the help all... here's what worked for me:

1. login under failsafe mode
2. sudo qt-language-selector --mode select
2. Choose English-US

My problem, and only problem, was that it was previously set for non-US English. I didn't need to remove the language packages. granted this is more of a workaround than fixing anything..but for now I have my computer back.

---

### Post by jdramer on 2008-02-26
I ran into this issue this morning too.  Thanks for the fast help!

---

### Post by huck416 on 2008-02-26
sudo apt-get remove language-pack-kde-en worked for me, too. Glad I found this thread; was about to reinstall KDE as well. Thanks.

---

