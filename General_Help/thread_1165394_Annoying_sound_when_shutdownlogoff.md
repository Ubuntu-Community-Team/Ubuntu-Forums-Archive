---
title: "Annoying sound when shutdown/logoff"
date: 2009-05-20
forum: General Help
---

### Post by uupreti on 2009-05-20
Hi all!
I am getting most ridiculous sound I have ever heard when I shut down or log off my computer from Ubuntu desktop 9.04. When I shutdown from command prompt, it's OK . There is no sound. But when I try to shutdown from GUI, it will give me big beeeeeeeeeeeeeep sound and it seems my speaker is brusting out of this sound.

Anybody got same problem like mine? My comp spec are in my signature.

Thanks.

---

### Post by uupreti on 2009-05-20
And yeah FYI I have already turned off all sounds from System->preferences-> sound, System->preferences->power management.

And I have also blacklisted sound module. But it didn't help either.

Code:
>  echo "blacklist snd_pcsp" >> /etc/modprob.d/blacklist.conf 

---

### Post by gameplay on 2009-05-20
Yes I have this problem - I'm a newbie when it comes to Linux so I have no idea what to do.  I don't get a problem if I log out, only if I shutdown.  I also get a much quieter version of this when booting up, just before you get the 'drums' on the Ubuntu start-up screen.

---

### Post by uupreti on 2009-05-20
yeah this is welcome sound which is much more pleased one. you can turn it off by going to System->preference-> sound and System->preferences->power management->General->extras (uncheck that button)

---

