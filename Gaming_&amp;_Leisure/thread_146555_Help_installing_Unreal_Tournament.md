---
title: "Help installing Unreal Tournament"
date: 2006-03-18
forum: Gaming &amp; Leisure
---

### Post by Pyronhell on 2006-03-18
Hi!!

I'm having some problems installing UT (normal).
I have the .run file to execute it (sh ut-....run), but it doesn't run on graphical mode, and in terminal it shows something like this:

```
pyronhell@pyronhell:/media/cdrom0$ ./ut-install-436.run
bash: ./ut-install-436.run: /bin/sh: bad interpreter: Permiso denegado
pyronhell@pyronhell:/media/cdrom0$ sudo sh ./ut-install-436.run
Password:
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]
pyronhell@pyronhell:/media/cdrom0$

```

Anyone can help me? thanks :)

---

### Post by stoeptegel on 2006-03-18
Are you sure the ut-install-436.run file is executable?
```

$ chmod +x ut-install-436.run

```

---

### Post by Pyronhell on 2006-03-18
Yes, I'm sure of it, and I execute it with SU

---

### Post by mrpixels0 on 2006-03-18
are you tryinmg to install the UT version that came with a Soundblaster live card ?

if so the normal UT GOTY installer will not work for it, you will need the Linux version of the 428 to 436 no delta patch. unfortunately i have no idea where to find this patch anymore most sites no longer carry, but you might find it at [www.3Dgamers.com](www.3Dgamers.com)

hope this helps.

MP0

---

### Post by bionnaki on 2006-03-18
this is what I do to install ut2004 (for what its worth)

open ut2004 dvd directory in a terminal
and type

sudo sh linux-installer.sh

---

### Post by DoktorSeven on 2006-03-19
Found this: 

[http://www.icculus.org/lgfaq/#shutyourtrap](http://www.icculus.org/lgfaq/#shutyourtrap)
```

/bin/bash ./ut-install-436.run

```

---

### Post by Pyronhell on 2006-03-19
[QUOTE=DoktorSeven]Found this: 

[http://www.icculus.org/lgfaq/#shutyourtrap](http://www.icculus.org/lgfaq/#shutyourtrap)
```

/bin/bash ./ut-install-436.run

```[/QUOTE]

I Love you!! I love you!!!! Thanks to all, this is the option that run on mi machine, but is needed to use SUDO for path creation (sudo /bin/bash ...)

I'm installing it at the moment, I suppose that its easy to run it... well... more info later

Thanks to all :)

**UPDATED:** Yes! it runs!! I need to run it with "/usr/local/games/ut/ut", but... it doesn't save preferences, I have to set it when I run UT :'(

---

### Post by Harleen on 2006-03-19
[QUOTE=Pyronhell]**UPDATED:** Yes! it runs!! I need to run it with "/usr/local/games/ut/ut", but... it doesn't save preferences, I have to set it when I run UT :'([/QUOTE]

Have you pressed "play now" button on the last install  step? Then your .ut directory has now the ownership of root and your normal user cannot write to it anymore. Changing that ownership to your normal user (or deleting that directory)  should fix it.
To run the game from anywhere place a link to /usr/local/games/ut/ut under /usr/local/bin with this command:
ln -s /usr/local/games/ut/ut /usr/local/bin/ut

---

### Post by adam.mech09 on 2006-05-22
[QUOTE=DoktorSeven]Found this: 

[http://www.icculus.org/lgfaq/#shutyourtrap](http://www.icculus.org/lgfaq/#shutyourtrap)
```

/bin/bash ./ut-install-436.run

```[/QUOTE]

I tried this but i have had no luck.  I have the GOTY edition cd (both) and the ut-install-436.run file in my home directory.  In my home dir, i've tried just sh ut-...-436.run and it says 
```
adam@veronica:~$ sh ut-install-428.run
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 428 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]
```

I get odd errors trying the /bin/bash ./ut-....-436.run method :
```
 adam@veronica:~$ /bin/bash ut-install-436.run
/bin/bash: ut-install-436.run: No such file or directory
 
```

What am i doing wrong?:-?

Edit:  Tried doing the /bin/bash method in the right directory...

thanks :)

---

### Post by evaklo on 2008-09-09
> **Harleen said:**
> Have you pressed "play now" button on the last install  step? **Then your .ut directory has now the ownership of root and your normal user cannot write to it anymore. Changing that ownership to your normal user (or deleting that directory)  should fix it.**
To run the game from anywhere place a link to /usr/local/games/ut/ut under /usr/local/bin with this command:
ln -s /usr/local/games/ut/ut /usr/local/bin/ut

I had the same problem with the saved games. 
Thanks a lot!!

---

### Post by Carb on 2008-09-10
Will this work with the version of UT GOTY 432?

I am looking forward to playing this in Ubuntu.

I hate WinDoze

---

