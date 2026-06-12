---
title: "Finch Notifications"
date: 2008-09-20
forum: Desktop Environments
---

### Post by G-mL on 2008-09-20
I recently came across Finch as an alternative to Pidgin (Finch is the ncurses (terminal) interface ported from the GUI IM client Pidgin)

The only thing that I don't love about Finch is its lack of notifications for new IM's. 

I found this link: [http://www.linuxmint.com/forum/viewtopic.php?f=42&t=7065](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=7065)

There, they mention a way to use the Compiz water ripple effect to notify new messages. However, seeing that I'm not interested in using Compiz for this and rather just a nice icon in the tray (similar to how Pidgin does it by default), does anyone know how to modify/change that script to give a tray notification?

I am relatively new to Ubuntu and have had little (read: zero) experience with scripting.

Thanks in advance for your help. 

[I hope this is the right place for this thread.]

-Rupac

---

### Post by G-mL on 2008-09-20
*bump* Anyone?

---

### Post by G-mL on 2008-09-21
Okay, I made a bit of progress here:

If I set up a Buddy Pounce, then I can have the command 

```
zenity --notification --text="foo"
```

This pops up a little icon in the try and goes away when i click it. The only problem is that if I set it to "Recurring", which saves the buddy pounce, then I get an icon *every time a new message is sent from that buddy.* This is not how Pidgin does it. Can anyone offer any suggestions?

-Rupac

---

### Post by thecheeks on 2009-07-04
I'm pretty interested in this too. Bump.

---

### Post by EdwardMorris on 2010-01-26
Try mumbles (sudo apt-get install mumbles). works out of the box for finch. Add a startup script to have it run each time you log on, it supports daemon mode. To your startup add,

mumbles -d

and you should be all set.

---

### Post by mehturt on 2010-06-03
I modified the Knotifications [http://code.google.com/p/pidgin-knotifications/](http://code.google.com/p/pidgin-knotifications/) Perl script to launch my custom notification upon new message, if you are familiar with Perl, Knotifications is an easy script to begin with.

---

### Post by KingDiamond on 2010-08-18
G-ml thanks for pointing me to zenity!!
You can setup it like a buddy pounce, or you can enable sounds,
and set sound method to command! Then use zenity as that "sound"
Here is a litlle custom script to solve problem of multiple 
notifications:
```

#!/bin/bash
LINESNUM=$(ps -ef | grep -v grep | grep -c 'zenity --noti')
if [ $LINESNUM -ge 1 ]; then
        exit 0
else
        zenity --notification &
        exit 0
fi

```
Its not so elegant but works for me :)

Call it finchnotfy, set chmod 755 on it, copy to /usr/bin and 
then in finch, under *sound command* add *finchnotify* :)
Tweak it for your needs

---

### Post by damnick on 2010-08-24
> **KingDiamond said:**
> G-ml thanks for pointing me to zenity!!
You can setup it like a buddy pounce, or you can enable sounds,
and set sound method to command! Then use zenity as that "sound"
Here is a litlle custom script to solve problem of multiple 
notifications:
```

#!/bin/bash
LINESNUM=$(ps -ef | grep -v grep | grep -c 'zenity --noti')
if [ $LINESNUM -ge 1 ]; then
        exit 0
else
        zenity --notification &
        exit 0
fi

```
Its not so elegant but works for me :)

Call it finchnotfy, set chmod 755 on it, copy to /usr/bin and 
then in finch, under *sound command* add *finchnotify* :)
Tweak it for your needs

The above doesn't work when i have incoming messages from google talk badge.

---

### Post by drhabber on 2010-10-20
I've got a similar problem. Do you have any ideas how to make Finch notify me about a new message via network? I mean, when Finch is running remotely with screen.

So far I've tried with "expect" as a script being run from "Sounds->custom command" (auto login via SSH and display icon in tray with zenity) but it dies before I click the notification icon and produces an messy output to the "screen" window with Finch. The script itself works fine when started from command line (an notification icon stays in tray until I click it).

```
#!/bin/sh
exec expect "$0" -f ${1+"$@"}
set timeout 60
spawn ssh -l user 192.168.1.100
expect "password: $"
send "password\n"
expect "user@machine"
send "export DISPLAY=:0 && zenity --notification\n"
send "exit\n"
interact
```

I believe there is some less complicated way ;). Any advice would be appreciated.

---

