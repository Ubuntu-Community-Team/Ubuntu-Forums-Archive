---
title: "Disable bell/beep in console?"
date: 2007-04-24
forum: Desktop Environments
---

### Post by ajkessel on 2007-04-24
Is there some way to absolutely disable the bell (or beep) in consoles? 

I know how to do it in gnome/gnome-terminal (system->preferences and current-session).

I know how to disable beep on tab-completion (/etc/inputrc).

The only way I've seen for disabling it was suggested at [http://ubuntuforums.org/showthread.php?t=9246](http://ubuntuforums.org/showthread.php?t=9246) , which involves removing the pcspkr kernel module.

There must be a more elegant way.

Any suggestions?

---

### Post by YetAnotherNoob on 2007-04-24
I am a complete noob, so this maybe off base.  Have you tried System -> Preferences -> Sound.
On System Beep tab uncheck **Enable System Beep**

I am using Ubuntu 7.04 (and extremely impressed).

hope this helps

---

### Post by ajkessel on 2007-04-24
Thanks, but I'm looking for a system level fix. I know how to disable system sounds within Gnome, but I need to disable the system beep in the tty terminals (i.e., not in X). That's what I meant by "console."

---

### Post by RedSquirrel on 2007-04-25
> **ajkessel said:**
> Is there some way to absolutely disable the bell (or beep) in consoles? 

I know how to do it in gnome/gnome-terminal (system->preferences and current-session).

I know how to disable beep on tab-completion (/etc/inputrc).

The only way I've seen for disabling it was suggested at [http://ubuntuforums.org/showthread.php?t=9246](http://ubuntuforums.org/showthread.php?t=9246) , which involves removing the pcspkr kernel module.

There must be a more elegant way.



Well, adding it to the blacklist may not be elegant, but it works. :)

Just add this to /etc/modprobe.d/blacklist

```
# turn off the PC speaker
blacklist pcspkr

```

---

### Post by yabbadabbadont on 2007-04-25
Add the following to /etc/rc.local:
```
for i in 1 2 3 4 5 6
do
        setterm -blength 0 > /dev/tty$i
done

```

---

### Post by RedSquirrel on 2007-04-25
> **yabbadabbadont said:**
> Add the following to /etc/rc.local:
```
for i in 1 2 3 4 5 6
do
        setterm -blength 0 > /dev/tty$i
done

```

Wow. That is elegant.

I don't suppose my suggestion of using *blacklist* is any better than manually removing the module. #-o

By the way, it seems *-blength* with no arguments defaults to 0. :lol:

---

### Post by kushin77 on 2007-06-01
vi /etc/rc.local
add this line to the end of your script
just before the exit 0
restart service or computer. 

enjoy
:p
modprobe -r pcspkr
exit 0

---

### Post by rhael on 2007-06-14
Excellent! works great

---

### Post by Speekie on 2007-06-14
Or put this command in /etc/profile:
setterm -bfreq 0

---

### Post by kwilliam on 2008-06-09
Since we're going for the most elegant solution...
This will disable the audible bell in bash. (It won't guarantee other programs won't beep. Blacklisting the pc speaker module is probably still the best way to do that.)

Edit (or create) ~/.inputrc
```

set bell-style visible

```

This replaces the audible bell with a visible bell that flashes the screen once. To have no bell at all, replace "visible" with "none".

If that doesn't work, add
```

export INPUTRC=~/.inputrc

```
to your ~/.bashrc file so bash can find ~/.inputrc. I had to do this step as well.

---

