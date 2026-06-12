---
title: "Recent compiz updates broke XGL"
date: 2006-09-04
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-09-04
Hi,

Just updated my compiz etc.  Went to start it and bang, window borders have disappeared and I get the follwoing:

 compiz: Couldn't load plugin 'gconf'


Any ideas?

TIA

---

### Post by guX on 2006-09-04
I have the same problem here. Anyone know what's wrong?

I was actually getting this error at the start:
```
shane@guXmeister:~$ compiz --replace gconf
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0
```

So I downgraded Compiz, but now I'm getting this error:
```
shane@guXmeister:/var/cache/apt/archives$ compiz --replace gconf
compiz.real: Couldn't load plugin 'gconf'
```

---

### Post by sylvester_0 on 2006-09-04
Ditto. Also does anyone have the problem where everything becomes sluggish after a day or so of using all the neato effects? When I first boot my computer everything's all pretty and fluid. Eventually new dialogs popping up and switching windows becomes painful to the point that I just reboot. I don't think it's my computer - I have a 3800 X2, 2 Gig RAM, 256 MB 6600 with nvidia driver. The computer otherwise performs very snappy. I'm using the nvidia drivers from the dapper repository and the compiz from beerokid and compiz.info. Just hoping that I'm not alone here and that this will eventually be fixed. It gets to the point that I usually reboot once or twice a day just so it's not so slow.

---

### Post by guX on 2006-09-04
I haven't heard of any of those slowness problems, but I found this solution: [http://ubuntuforums.org/showthread.php?t=250489](http://ubuntuforums.org/showthread.php?t=250489)

---

### Post by Uncle Spellbinder on 2006-09-04
Go to the [***_Compiz Forums_***](http://www.compiz.net/forum-3-questions-answers). Much more discussion and help with the new upgates there. Several existing threads with answers ans solutions in the "Questions an Answers" and "Bugs" sections.

---

### Post by Dinerty on 2006-09-04
```
compiz-start
```

Take a look at:

[http://www.ubuntuforums.org/showthread.php?t=250444](http://www.ubuntuforums.org/showthread.php?t=250444)

I write a small guide on how to sort things out, worked for a few people, hopefully it ok for you :)

---

### Post by OffHand on 2006-09-04
Quinn is updating too fast. She should first sort out the bugs instead of adding stuff all the time. I appreciate her work and effort but she's is going to fast in my opinion... but what do I know.

---

### Post by chicken101 on 2006-09-04
I know how to fix it.

Go to system->preferences->sessions

go to the startup programs tab, and delete the old way you used to start compiz.  Then add a new startup program called "/usr/bin/compiz-start".

Fixed it for me.

---

### Post by Uncle Spellbinder on 2006-09-04
> **chicken101 said:**
> I know how to fix it.

Go to system->preferences->sessions

go to the startup programs tab, and delete the old way you used to start compiz.  Then add a new startup program called "/usr/bin/compiz-start".

Fixed it for me.


Yep. And if anyone's not sure how *compiz-start* should look, the new *compiz-start* should look like this:
```
#!/bin/sh
if [ -f /usr/bin/cgwd ]
then
    nohup cgwd --replace &
else
    nohup gnome-window-decorator --replace &
fi

if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm > /dev/null & exit;
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &  exit;
fi
```

---

### Post by OffHand on 2006-09-04
> **Uncle Spellbinder said:**
> Yep. And if anyone's not sure how *compiz-start* should look, the new *compiz-start* should look like this:
```
#!/bin/sh
if [ -f /usr/bin/cgwd ]
then
    nohup cgwd --replace &
else
    nohup gnome-window-decorator --replace &
fi

if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm > /dev/null & exit;
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &  exit;
fi
```
Nice, although it only toggles compiz on at the moment, pressing it again seems to restart it rather than going back to metacity.

---

