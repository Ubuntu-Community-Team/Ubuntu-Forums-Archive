---
title: "Problem installing Pennmush"
date: 2009-06-09
forum: Gaming &amp; Leisure
---

### Post by GrahamP on 2009-06-09
I'm new to Ubuntu/Linux so this is probably me missing something obvious but I'm having an issue with installing and running Pennmush and could use some advice. 

Began by looking in Synaptic. Yep, there it was. Pennmush 1.8.2p8, the latest stable release in the Universe repository. A good start. Installed. No reported problems. 

Found the files in /usr/share/pennmush. Well, some of the files. No sign of the executable, nor of netmush, which the restart script insists is also essential. Searching the file system failed to find any trace of either of the apparently missing files. 

So I have a set of questions. First, am I overlooking something that is obvious to a more experienced user? Second, has anyone else installed Pennmush from Synaptic, and can thus confirm the apparently missing files are actually installed in that process? Third, for future reference, can I assume that packages in a repository /have/ been checked at least once and that any problems are likely at my end? I've installed a fair number of packages from the repositories in the last couple of weeks and the entire process has been straightforward and flawless up to now. So maybe I've been lulled into a false level of trust in the Synaptic Package Manager. :D

---

### Post by Grishka on 2009-06-09
hey, you can easiliy check out what files were installed with a given package from synaptic. just check out the 'installed files' tab in package properties. there's no need to hunt around the system for files, you've got it all on a plate. netmush, for example, can be found in /usr/lib/pennmush/game.

check out the documentation in /usr/share/doc. have you installed it for yourself by running penn-install from your home directory? necessary files will be put there.

---

### Post by GrahamP on 2009-06-09
> **Grishka said:**
> hey, you can easiliy check out what files were installed with a given package from synaptic. just check out the 'installed files' tab in package properties. there's no need to hunt around the system for files, you've got it all on a plate. netmush, for example, can be found in /usr/lib/pennmush/game.

Thank you, Grishka. This sorted out my Pennmush problem and taught me where to look for installed files in the future.

---

### Post by hartonj on 2009-06-30
Got a couple of questions regarding this matter. One has anyone managed to successfully run pennmush after installing with synaptic? If so, how did you set up the restart script, mush.cnf, netmush so it all works? If not, can anyone give me advice on how to do that? I am asking since setting the GAMEDIR directive in the restart script (of pennmush) to /usr/share/pennmush/game works until it hits a problem, and ask where netmush is. On another note, if you change that variable to /usr/lib/pennmush/game, it can't find the mush.cnf file over in /usr/share/pennmush/game. I could dig some more, but I'm wondering if anybody knows anything about that.

---

### Post by Grishka on 2009-07-01
> **hartonj said:**
> Got a couple of questions regarding this matter. One has anyone managed to successfully run pennmush after installing with synaptic? If so, how did you set up the restart script, mush.cnf, netmush so it all works? If not, can anyone give me advice on how to do that? I am asking since setting the GAMEDIR directive in the restart script (of pennmush) to /usr/share/pennmush/game works until it hits a problem, and ask where netmush is. On another note, if you change that variable to /usr/lib/pennmush/game, it can't find the mush.cnf file over in /usr/share/pennmush/game. I could dig some more, but I'm wondering if anybody knows anything about that.

run penn-install from your home directory, and set GAMEDIR to /home/<you>/pennmush/game, and not to the system directory. run ./restart from /home/<you>/pennmush/game. nothing else is needed to connect to the default one-room mud.

---

### Post by mystmaiden on 2010-07-17
Resurrecting an old thread here. Just to amuse myself, I downloaded pennmush from synaptic this evening. I got as far as penn-install but now I don't know how to open the game. I really just want to muck around with it on my computer, I'm not wanting to upload it to a server or anything. I could do that with Windows but I can't really remember how, its been years.

```
run penn-install from your home directory, and set GAMEDIR to /home/<you>/pennmush/game, and not to the system directory. run ./restart from /home/<you>/pennmush/game. nothing else is needed to connect to the default one-room mud.
 		                   		  		  		  		  		  	   	 		
	 	 	 		 
```

How do I set GAMEDIR  to /home/<me>/pennmush/game ?

thanks

---

