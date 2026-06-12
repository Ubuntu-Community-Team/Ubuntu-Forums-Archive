---
title: "no updates"
date: 2008-08-20
forum: Desktop Environments
---

### Post by tombo465 on 2008-08-20
Hello , its been about a :guitar:week or so since i have seen any updates for hardy heron . it seems kind of unusual . has  there been any updates ? if so what should i check after having already checked automatic updates box is checked

---

### Post by picpak on 2008-08-20
Go to System > Administration > Update Manager and see what's there.

---

### Post by pparks1 on 2008-08-20
You could verify with
sudo apt-get update
sudo apt-get upgrade


As the major releases get a bit older, the # of updates usually does slow down.  I don't think this is something to worry about.

---

### Post by tombo465 on 2008-08-20
it's up to date .sorry ! i think i updated it when i was getting help with another problem through the command line . <sudo apt-get update> would that line do it

---

### Post by jmate24 on 2008-08-20
yes it would. also try...```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by tombo465 on 2008-08-20
hey pparks1 how doyou get your system info on there

---

### Post by cool_penguin on 2008-08-21
I too have been seeing this. I now am trying to manually check for updates each day, but no updates to be seen. 

Ubuntu team has probably working too hard and are now taking a break, :popcorn:

---

### Post by ammikulka on 2008-08-21
I noticed last week that the update manager was updated. And i think it is automatically installing my updates now. Not positive tho

---

### Post by Bakon Jarser on 2008-08-23
> **ammikulka said:**
> I noticed last week that the update manager was updated. And i think it is automatically installing my updates now. Not positive tho

Probably not.  If you open synaptic package manager and go to file > history you can see all updates.  It's really odd that we had updates every other day since installation, the last update was to the update manager, and now no updates for almost two weeks.  It makes me think that the update may have broken the update manager.  I did get one update today but not from an ubuntu repository, it was a wine update.

---

### Post by mcduck on 2008-08-24
If there's no security issues then there's no need for updates. That's just normal.

The generic rule n Ubuntu is that after release the program versions are frozen and updates are only provided for security reasons and to fix serious bugs.

If you enable the backports repository you might get some new program versions, but backports only provides updates for packages that are in the next Ubuntu release, have little or no dpependencies and that no other packages depend on. So all updates coming from backports are just a nice extra, and you shouldn't even expect always getting the latest & greates versiosn of every program.

---

### Post by Xfcn on 2008-08-24
Thanks for this thread. I was wondering why my almost daily update experience had petered out to nothingness.

How does one enable the Wine and Backports updates?

---

### Post by Bakon Jarser on 2008-08-24
> **Xfcn said:**
> Thanks for this thread. I was wondering why my almost daily update experience had petered out to nothingness.

How does one enable the Wine and Backports updates?

For backports go to System > Administration > Software Sources.  Click on the updates tab and check the box next to unsupported updates.  You might want to read up a little more on unsupported updates first but I'm to lazy to find links right now.  Fore wine go here to enable the repository for the latest version.  [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)  After the last version made one of my programs stop working I've decided to stick with the stable version of wine wich is the one in the ubuntu repositories.

[QUOTE=mcduck]If there's no security issues then there's no need for updates. That's just normal.[/QUOTE]

I don't disagree, I just think that it is suspicious that we had security updates just about every other day since hardy came out and now nothing since the update manager was updated.  It's just hard to believe that there haven't been any security updates in two weeks.

---

