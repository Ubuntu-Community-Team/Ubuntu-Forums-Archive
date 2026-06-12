---
title: "did something stupid with apt-get please help!"
date: 2011-02-11
forum: Desktop Environments
---

### Post by gobbledigook on 2011-02-11
Hello!

yes i am officially a retard :popcorn:

I was installing zabbix and had to make some mysql stuff work... couln't remember my mysql password, so figured i'd uninstall mysql and reinstall.

so i did:

```
sudo apt-get remove mysql-*
```

i was admittedly stoned when doing this, but it has uninstall a LOT of other stuff... including xbmc. 

no problem, i'm an idiot but i'll just reinstall xbmc and the other stuff...

```
sudo apt-get install xbmc
package not found
```

did update as well and still no joy!

any ideas how i can get this running again or would it just be easier to reinstall... (a route of lst resort as i have lot of configured stuff to back up and restore :( )

---

### Post by 3Miro on 2011-02-11
xbmc is not part of the official Ubuntu repository, you will have to reinstall it the same way you installed it in the first place.

[http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux](http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux)

Use Synaptic Package Manager (System -> Admin -> SPM) for better control in finding individual packages (if they are in the repository).

I don't know what depends on MySQL and what got removed, I don't have MySQL installed, which means it doesn't come by default. You can use SPM when you uninstall things to see exactly what would be installed/removed.

---

### Post by gobbledigook on 2011-02-11
thanx! 

sorry forgot to mention using 10.10.

i installed xbmc through the SPM originally, after added the PPA and now it doesn't even show up in the list there! gonna go full reinstall... don't like this mix of desktop/server, seems neither suits my needs perfectly and if you mess about in CLI then it cocks something else up in the desktop!

my mess so i can only really blame myself...

---

### Post by Krytarik on 2011-02-11
Then just re-add the PPA. If you want to avoid a re-install of the complete system, I recommend looking into "/var/log/apt/history.log" to see which packages has been removed. Synaptic's history only shows its own log.

---

