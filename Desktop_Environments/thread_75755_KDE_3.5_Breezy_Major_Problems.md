---
title: "KDE 3.5 Breezy Major Problems"
date: 2005-10-14
forum: Desktop Environments
---

### Post by spiritz on 2005-10-14
Hello,

I've been using Breezy & KDE 3.5 beta 1 since a few weeks, everthing worked properly since two day ago when breezy was released.

I noticed when breezy got released that lots of packages were updated, including kde ones.

Now KDE media-autodection doesn't work anymore, I also noticed that kwallet doesn't work properly, ie I'm unable to log on my account on kopete because it seems that it can't trigger kdewallet to get my accounts L/P.  I also miss some traysys apps such as the battery monitor, and khotkeys won't start neither, :
> 
$ khotkeys
KInit could not launch ''.
KCrash: Application 'khotkeys' crashing...
ERROR: Communication problem with khotkeys, it probably crashed.
zsh: exit 255   khotkeys


Is there anyone else experencing these problems?

---

### Post by spiritz on 2005-10-14
I fogort to add that "media:/" doesn't work neither and I seem to experience cookies problems on konqueror.

---

### Post by GeneralZod on 2005-10-14
Ouch - sounds nasty :(

I've heard about the auto-detection several times now, and word is that this will be fixed in a later release which can be used with Kubuntu.

Not sure about kwallet, though - as a stop-gap solution, your passwords can probably be reclaimed by running

```

kwalletmanager

``` 

from the command line.

As for the others, I'm not sure; it will very helpful to the devs and the other members of this community if you could file bug reports on each issue.

I'm going to do a fresh install of Kubuntu at the weekend, after which I'll hopefully be of more use :)

[QUOTE=spiritz]I fogort to add that "media:/" doesn't work neither and I seem to experience cookies problems on konqueror.[/QUOTE]

This is very probably related to the bugs in auto-=detection.

---

### Post by Knome_fan on 2005-10-14
At least the media problem seems to be a bug they introduced very shortly before the release.
> Breezy is also the first place to get KDE 3.4.3 which umm, should have been released yesterday. The last minute addition has caused some problems like KMail not working with GPG and media:/ not using HAL, I'll get fixes for those in -updates as soon as possible. We didn't get KOffice 1.4.2 or Amarok 1.3.3 in unfortunately, those were too close (I'm really beginning to see the advantages of gnome's 6 predictable month releases).
[http://www.kdedevelopers.org/node/1537](http://www.kdedevelopers.org/node/1537)

So it should be fixed shortly, I hope.

---

### Post by spiritz on 2005-10-14
thanks for you inputs. I'm looking foward to seeing upgrades soon.

---

### Post by manubreizh on 2005-10-14
hi spiritz,
i've experienced the same bug with /media : it shows an error message, like "sda1 folder doesn't exist" when i plug an usb key ; by the way, in konqueror, you can have access to this media in the root file (not in sudo mode, but in user mode) : if you open the /media folder, do you see your usb key ? in my case, it works, i can move folders form and to the key ; the only thing i cannot do is to unmount before pluging it off ; but it seems not to destroy the key (for the moment !).
hope it helped

---

### Post by Navyblue on 2005-10-14
I have the same automount preoblem too.

What I did was add the appropriate line in /etc/fstab and mount it from the console line.

---

### Post by manubreizh on 2005-10-14
hi once again,
i've upgrated to 3.5beta1 a few minutes ago, and media works ! i don't know if it's this upgrade that fix the problem, or another in the last 30 minutes (from repos) but it works !

---

### Post by raoult on 2005-10-18
spiritz,
were you able to come to any resolution regarding the wallet/kopete situation. I experienced the same problems after upgrading to (beta)3.5 in addition to KHotKeys, media, etc. . .

-raoult

---

### Post by spiritz on 2005-10-19
All my problems got relsoved by upgrading to kde 3.5 beta 2.
HOWEVER now I have a new problem, making kde almost unusable :
[http://bugzilla.ubuntu.com/show_bug.cgi?id=18066](http://bugzilla.ubuntu.com/show_bug.cgi?id=18066)

---

### Post by hekata on 2005-10-19
I had the same problems after upgrading, so I've reinstalled everything. I'm back to Kubuntu 5.04 and I think I'll wait till I upgrade again.
Adding the devices in etc/fstab works, that's all I can say.
The problem with the mouse sounds nasty.
Hope they'll fix it soon.

---

