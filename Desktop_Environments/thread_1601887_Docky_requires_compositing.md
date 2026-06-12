---
title: "Docky requires compositing"
date: 2010-10-20
forum: Desktop Environments
---

### Post by insub2 on 2010-10-20
I have a fairly clean install of Maverick.  On startup, I keep getting the Docky requires compositing error even though I have Compiz turned on.  What to do?

---

### Post by kerry_s on 2010-10-20
you can try turning on metacity composite, so it can detect a composite manager before compiz takes over.

---

### Post by yaseenes on 2010-10-22
i have the same problem and  enabling metacity compositing wont fixed the issue.
i always get docky rquires compositing error on startup

---

### Post by radiosgalore on 2010-10-23
I get the same thing on my desktop. I tried adding desktop effects and my screen went totally blank. Almost had to format the thing. Metacity does not solve the issue in Docky or the Avant Window Navigator. I have none of these issues on my laptop. I also have Compiz

---

### Post by Bluenoser81 on 2010-10-25
Any solution found for this yet? I have tried these suggestions, but still get the Docky pop-up saying about needing compositing (whatever that is) to work. Seems to be working fine though, I guess my question is:  How do I know if it isn't?

---

### Post by kerry_s on 2010-10-25
you'll know if it's not running cause it won't look right.

---

### Post by insub2 on 2010-10-27
Metacity compositing is on.  Has been on.  Still no joy.

Kerry_S, are you saying I have to turn Compiz off?  I don't wanna.  & that can't be the solution.

---

### Post by jaramago on 2010-10-27
It's easy to solve this problem:
 

Open with gedit usr/bin/docky
add *sleep 5 * after *#!/bin/sh *

This is how:

#!/bin/sh
**sleep 5**

SCRIPT_PATH=`dirname $0`
SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`

........

and voila!!!

---

### Post by CoolJohnB on 2010-10-27
> **jaramago said:**
> It's easy to solve this problem:
 

Open with gedit usr/bin/docky
add *sleep 5 * after *#!/bin/sh *

This is how:

#!/bin/sh
**sleep 5**

SCRIPT_PATH=`dirname $0`
SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`

........

and voila!!!

Thanks for the suggestion, works great! :)

---

### Post by WanderingOak on 2010-10-28
> **jaramago said:**
> It's easy to solve this problem:
 
Well, I updated the file, but docky is still acting up for me. I only saw the message once, but docky is now resting behind the Gnome dock, rather than on top, where it was before I enabled Compiz.

---

### Post by WanderingOak on 2010-10-29
I haven't had the chance to try this yet (@ work), but it looks like the [Docky Wiki]("http://do.davebsd.com/wiki/index.php?title=Docky") has a fix for this.

---

### Post by jaramago on 2010-10-29
If sleep 5 don't work try increasing to 8 or 10. The problem is Docky starting before compiz. With sleep + (seconds) we delay docky startup.

---

### Post by WanderingOak on 2010-10-29
> **jaramago said:**
> If sleep 5 don't work try increasing to 8 or 10. The problem is Docky starting before compiz. With sleep + (seconds) we delay docky startup.

Naaah.Even though it's late, docky still comes in behind the Gnome panel, rather than on top of it. The gconf-editor didn't help either- the specified path didn't exist. If I don't find a fix for this soon, I'm going to dump compiz.

---

### Post by keef123 on 2010-10-31
> **CoolJohnB said:**
> Thanks for the suggestion, works great! :)
Worked a treat. 

Many thanks.

---

### Post by gubbi.fisk on 2010-11-10
> It's easy to solve this problem:


Open with gedit usr/bin/docky
add sleep 5 after #!/bin/sh 

This is how:

#!/bin/sh
sleep 5

SCRIPT_PATH=`dirname $0`
SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`

........

and voila!!!

Thanks, worked like a charm!

---

### Post by dentex on 2010-11-16
> **jaramago said:**
> It's easy to solve this problem:
 

Open with gedit usr/bin/docky
add *sleep 5 * after *#!/bin/sh *

This is how:

#!/bin/sh
**sleep 5**

SCRIPT_PATH=`dirname $0`
SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`

........

and voila!!!
A workaround based on some delay action! exactly what I was looking for. Really thanks!
It works perfectly.

---

### Post by andyit74 on 2011-01-19
Sorry i am new to ubuntu 10.10 but i get a blank doc when run gedit usr/bin/docky in the terminal with dockyx as one of the tabs. There is no *#!/bin/s. Am i missing something? *

---

### Post by flea74 on 2011-01-19
> **andyit74 said:**
> Sorry i am new to ubuntu 10.10 but i get a blank doc when run gedit usr/bin/docky in the terminal with dockyx as one of the tabs. There is no *#!/bin/s. Am i missing something? *

actually the command should be gedit /usr/bin/docky

just missed the initial / when it was first typed I missed it too the first time I tried it

:p

---

### Post by jrob09BHS on 2011-01-27
> **andyit74 said:**
> Sorry i am new to ubuntu 10.10 but i get a blank doc when run gedit usr/bin/docky in the terminal with dockyx as one of the tabs. There is no *#!/bin/s. Am i missing something? *


i had to run

sudo gedit /usr/bin/docky

to get this to work

---

### Post by eeffoc on 2011-01-28
Awesome; works perfectly! Thanks for correcting dockys sleep apnea...

---

### Post by Netnai on 2011-02-16
The reason of this error message is due to docky begins execution before compiz,
although later docky runs and works properly.

You can ignore the message or do the following to avoid this annoying message
(i did this summary with info from other threads and sites):

From terminal, launch this to edit the file /usr/bin/docky:

>                  gedit /usr/bin/docky

and add [sleep 5] after [#!/bin/sh]  (ignore brackets)

                 > #!/bin/sh
                 sleep 5

                 SCRIPT_PATH=`dirname $0`
                 SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`
                 etc........

This sleeps docky 5 seconds. But you can do it in another way.
Instead to use a sleep 5 (maybe not solve the issue because your computer needs a 8, 10,...etc) 
write the following right after #!/bin/sh:

> #!/bin/sh
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
                #DISPLAY=:0.0 docky >/dev/null 2>&1 &          
		done="true";
	else
		echo "Waiting for compiz"
		done="false"
		sleep 5;
	fi
done
SCRIPT_PATH=`dirname $0`
SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`
etc........

Or more aggressive, you can bomb requesting until compiz running, deleting [sleep 5] in this loop:

> #!/bin/sh
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
                #DISPLAY=:0.0 docky >/dev/null 2>&1 &
          
		done="true";
	else
		echo "Waiting for compiz"
		done="false"
 	fi
done
SCRIPT_PATH=`dirname $0`
SCRIPT_PATH=`cd $SCRIPT_PATH; pwd`
etc........

If this solve your problem (or break your computer ;) ) write a line in the thread and put a SOLVED on the subject.

Regards!

---

### Post by chrinabuntu on 2011-03-12
I've been searching for a solution to my Docky issue too...but now that I've found this thread I'm not at home to try it. I have a question...did anyone else have the added issue of the giant black section at the bottom of the screen? Will this fix that problem as well, or is that a separate issue?

I'm one of those folks who used to have desktop effects enabled, way back several animals ago...but then after one upgrade or another they were no longer enabled. I just let that go. Not that big an issue...but then I discovered Docky and have been using it on my laptop...LOVE IT! Well, I just tried putting it on my desktop (the one with the disabled effects)...and Docky is there and works, but I get the stupid compositing message...and there's the intolerable blackness. 

(Running Lucid on it...can't remember my video card info or anything right now. Just thought maybe some general things to try might be out there...I know this comes up a lot!)

Thanks everyone...I love this friggin' forum!!! 

Chris in the Q

---

### Post by zarnivop on 2011-08-12
> **chrinabuntu said:**
> ...did anyone else have the added issue of the giant black section at the bottom of the screen?

Yes, I have it sometimes. Being a noob that only recently moved from XP/Win7 I just restart... 

I THINK it has something to do with windows manager stops abnormaly. Whenever this black rectangle shows the 'show desktop' button brakes too.

---

### Post by Duncan Williams on 2011-08-12
The solution is to manually run compositing after your computer has finished booting.
How?

**Fusion-Icon** 
[http://wiki.compiz.org/CompizFusionIcon](http://wiki.compiz.org/CompizFusionIcon)
for reloading compiz/metacity in a single click 
(reload window manager)
Available in software manager or synaptic.

**xcompmgr**
[https://wiki.archlinux.org/index.php/Xcompmgr](https://wiki.archlinux.org/index.php/Xcompmgr)
Available in software manager or synaptic.

Either method will magically get rid of the big black line at the bottom of the screen and make sure your window manager is working correctly.

If you find that fusion-icon is your solution. 
Try putting it in your `startup applications' 
it should then automatically enable compositing.

---

