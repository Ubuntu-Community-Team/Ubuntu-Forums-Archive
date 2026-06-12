---
title: "Freaking autostart or how to switch the beagle front-end"
date: 2008-08-04
forum: Desktop Environments
---

### Post by private_lock on 2008-08-04
Hello!

Currently I use [FONT="Courier New"]kerry[/FONT] as front-end for searching with beagle. But on every login there is a second "Beagle Search 0.3.3" coming up. Today I'm going to find out: How to stop it?

I've looked in [FONT="Courier New"]~/.kde/Autostart[/FONT] and in [FONT="Courier New"]~/.config/autostart[/FONT]. Both folders don't have a link to [FONT="Courier New"]beagle-search[/FONT]. The [FONT="Courier New"]systemsettings[/FONT] tell me, that [FONT="Courier New"]~/.kde/Autostart[/FONT] is my default autostart folder so maybe the second is ignored anyway?

Then I installed the [FONT="Courier New"]kcontrol-autostart[/FONT] package and checked [FONT="Courier New"]kcontrol[/FONT] (why isn't this accessible via K-Menu???) This one notified me of another autostart shell script in [FONT="Courier New"]~/.kde/env[/FONT] which just exports an environment-variable.

Furthermore I checked [FONT="Courier New"]/opt/kde3/share[/FONT] ... but there is definitely no [FONT="Courier New"]autostart[/FONT] folder inside, only a folder called [FONT="Courier New"]applnk[/FONT].

Next I wanted to uninstall [FONT="Fixedsys"]beagle-search[/FONT], but there is no such package. And since [FONT="Courier New"]kerry[/FONT] is using [FONT="Courier New"]beagled[/FONT] (the backend demon), I cannot really uninstall that one I thought. But scanning through the details of package [FONT="Courier New"]beagle[/FONT] in the [FONT="Courier New"]adept-manager[/FONT] I found under details, installed files a link to [FONT="Courier New"]/etc/xdg/autostart/beagle-search-autostart.desktop[/FONT].

Next time please hide it a little better. It only took me some hours to find out ](*,) But definitely better, than simply "searching the registry" as some friends advised me ... that would have been to obvious. At least it took root rights to get rid of the file ... so now I feel really important ... god on my system ... you know!?!

Well, as it is already past 11 you've to wait till tomorrow, when I next time boot my machine, to see, if it really did the trick. Actually you'll going to hear the scream, if it didn't work, I'll promise!

Thanks for your valuable time
private_lock

---

### Post by arubislander on 2008-08-04
I will be paying attention to see if I hear you scream :popcorn:

---

### Post by private_lock on 2008-08-06
To my utter surprise, this really was sucessfull, so no need to damage my vocal chords :-)

---

### Post by arubislander on 2008-08-07
Good for you! =D>

---

