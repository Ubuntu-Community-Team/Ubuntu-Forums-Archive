---
title: "Synaptic Un-installed Itself and Gnome Terminal"
date: 2006-08-17
forum: Desktop Environments
---

### Post by poet_will on 2006-08-17
I did my normal daily updates and I got a message saying I needed to go terminal and do a dist-upgrade.  Well, terminal wouldn't work, so I went into Synaptic and clicked the Mark All As Upgrade or somethign like that.  Well when it got done, I had no Terminal and no Synaptic anymore.  How do I get the terminal back?  This is really annoying.


Thanks in advance,

Will

---

### Post by darrenm on 2006-08-17
Damn strange one. Have you tried rebooting yet? May just be the path messed up or something...

If no good run ```
sudo apt-get install synaptic gnome-terminal2
```

---

### Post by dickwall on 2006-08-17
Same for me - it looks like the dependencies are messed up on some of the python vte files - the update wants to uninstall quite a laundry list of important packages that probably mark the older version of vte as a dependency. I prevented it doing any damage on my systems beyond disabling the terminal (which currently won't start - complaining about a missing vte_terminal_set_opacity symbol. I refuse to let it update the python vte stuff because it wants to remove around dozen packages on my machine. Someone probably needs to know about this and fix it ;-).

Cheers

Dick

---

### Post by givré on 2006-08-17
Those update come from compiz repo.
Related bug in the forum : [http://www.compiz.net/topic-3116-fonts-are-now-complete-crap](http://www.compiz.net/topic-3116-fonts-are-now-complete-crap)
Don't update until it's fix

---

### Post by poet_will on 2006-08-17
I re-installed Synaptic and gnome-terminal and all is well again in the world.  I am using Compiz so I guess that was what my problem is.  I won't update those things anymore.  

Thanks everyone

will

---

### Post by ruffneck on 2006-08-17
same for me as well. I ended up going to a terminal (ctrl+alt+F1) and resintalling the packages that were uninstalled. All seems fine so far.

---

### Post by Uncle Spellbinder on 2006-08-17
I guess I got lucky. I updated last night via Synaptic in *Dapper Drake 6.06.1 LTS*. It included, among other things, the *freetype* update, *cgwd .55*, *cgwd themes .11* *gnome-terminal2* and several others. Other than the many fonts I've added myself now gone (with the exception of *Swiss 721 Cn BT Roman* that was in use at the time of the update) and a markedly slower overall experience using Dapper, all is OK, at least in my case. I does piss me off that nearly 1/3 of my fonts are gone, though.

---

### Post by latebeat on 2006-08-17
> **Uncle Spellbinder said:**
> I guess I got lucky. I updated last night via Synaptic in *Dapper Drake 6.06.1 LTS*. It included, among other things, the *freetype* update, *cgwd .55*, *cgwd themes .11* *gnome-terminal2* and several others. Other than the many fonts I've added myself now gone (with the exception of *Swiss 721 Cn BT Roman* that was in use at the time of the update) and a markedly slower overall experience using Dapper, all is OK, at least in my case. I does piss me off that nearly 1/3 of my fonts are gone, though.
Thanks for the reply, however this is regular gnome session. I have compiz installed but as far as I know libfreetype6 and cairo weren't upgraded as I've locked the in synaptic. I've followed this [howto]("http://www.ubuntuforums.org/showthread.php?t=180647") so I've locked them to prevent them from changing.

---

### Post by givré on 2006-08-17
That probably the reason of the mess, the compiz upgrade goal was to provide a patch version of gnome-terminal with true transparency, but that's needed a lot of package update, for exemple libvte, python-vte... but this gnome-terminal required the new libfreetype6. 
I don't know why it fail like that, but the reason is there, official ubuntu update concerned only few package with only security update (libmagik, binutils) that's definitly couldn't be he cause.

---

### Post by eljaco on 2006-08-18
So, it seems like I fell for the trap. I tried removing and then installing Synaptic, but that didn't work. Sometimes it asks me for the password, sometimes it doesn't, but it never loads up Synaptic. I cleaned up my repos, but how can I solve this synaptic problem? I don't have any problems with the gnome-terminal though, just Synaptic.

[Edit] 
When I run > sudo synaptic I get this error: > synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory


---

### Post by revilot on 2006-08-18
> **eljaco said:**
> So, it seems like I fell for the trap. I tried removing and then installing Synaptic, but that didn't work. Sometimes it asks me for the password, sometimes it doesn't, but it never loads up Synaptic. I cleaned up my repos, but how can I solve this synaptic problem? I don't have any problems with the gnome-terminal though, just Synaptic.

[Edit] 
When I run  I get this error:

[http://www.compiz.net/topic-3191-can-run-synaptic](http://www.compiz.net/topic-3191-can-run-synaptic)

---

### Post by eljaco on 2006-08-18
THANKS!! All better now.

---

### Post by canadianwriterman on 2006-08-18
The fix from the Compiz Forums worked for me too. Funny thing is, I don't even have Compiz installed on my machine.

---

### Post by givré on 2006-08-18
> **canadianwriterman said:**
> The fix from the Compiz Forums worked for me too. Funny thing is, I don't even have Compiz installed on my machine.
No but you probably have the compiz repo in your sources.list.
The update which screw up the system of a lot of people came from the compiz repo.

---

### Post by canadianwriterman on 2006-08-18
You were right. I had this in my repos:
```

deb http://www.beerorkid.com/compiz/ dapper main
```

Took it out... hope it doesn't link to anything other than Compiz that I might have installed through Automatix.

---

