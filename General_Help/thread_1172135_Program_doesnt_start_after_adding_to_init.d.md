---
title: "Program doesnt start after adding to init.d"
date: 2009-05-28
forum: General Help
---

### Post by johnman145 on 2009-05-28
Hello all,

I used webmin to add my java server to init.d so it will startup after reboot. If i press "Start Now" i see the text that my server is booting up, so my script is okay. However if i reboot the server does not startup. I looked at the log of the server and i see it never gets started (since the first thing it does when it starts is to log it is starting). 

Then i tried to add the script by hand with update-rc.d and this told me it was already added. So i removed it with update-rc.d, then added it again, double checked the links were made in the rcX.d directories, checked the current runlevel, checked in webmin if it could see the linkes i made with update-rc.d.  

Everything is "done by the book", everything looks fine but after rebooting the server does not start.
I called etc/init.d/myscript -start directly and that does work to.

I tried to see the bootlog but i read everywhere they removed  boot loggin from ubuntu (im sure they have a perfectly good reason, but from an outsider that makes no sense at all). Can someone give some advise.

im running ubuntu 8.04 LTS server edition

ps im thinking about adding it to cron, but i really think its a shame ubuntu has so much problems with something as simple as this. In windows i just create a shortcut in programs/startup and voila, succes.

the script is the following:
```

#!/bin/sh
# Controls the game server

case "$1" in
'start')
cd /home/jdv/bg/cur/
java -jar MyServer.jar -start 
	;;
'stop')
cd /home/jdv/bg/cur/
java -jar MyServer.jar -stop 
	;;
*)
	echo "Usage: $0 { start | stop }"
	;;
esac
exit 0

```

---

### Post by johnman145 on 2009-05-28
I just downloaded sysvconfig and it showed that my program was not enabled. I don't know what sysvconfig does, but i hope that will fix my problem. I enabled it, restarted sysvconfig and then it did show up as enabled. I'm wondering what sysvconfig is doing, because i get the feeling update-rc.d wasn't enough. I cant test though since lots of ppl are using the server right now so i have to wait until midnight :(

---

### Post by Brandon Williams on 2009-05-28
Which runlevel(s) did you add your service to, and at what priority? Is it possible that you added it at a priority that might cause it to fail due to other things not having been initialized yet?

I would typically add custom server startup at high prioriy, S99, to runlevels 2 through 5; and shutdown at low priority, K03, to runlevels 6, 0, and 1.

If runlevel priorities don't explain the problem, then you could try adding the following code to the top of your script (after the #! line) for debugging:
```
set -x
exec 2>> /tmp/MyServer.init.log
```

---

### Post by johnman145 on 2009-05-28
sysvconfig didnt help. Its still not booting.

> Which runlevel(s) did you add your service to, and at what priority?
i used the defaults on update-rc which i believe adds it to almost all but definitely to level 2 @ which the server is running. From update-rc it got a priority of 20.

Like i said i also tried it with webmin which gave it a priority of 99 and also added it to level 2 (amongst others).

I also thought about it that it might depend on other things. For one it needs mysql. But the very very first thing the server does when starting up is logging to a file it is starting. This line didn't show sow my assumption is that the whole thing is never run for whatever reason. 

I'll try you suggestion at night.. I was also thinking about just calling mkdir or something to check if the thing gets started or not (which i suspect it doesnt). 

Sometimes it really feels like ubuntu is hanging together with strings and wires :cry: (houtje, touwtje we say in dutch)

edit
is there some way to test the booting sequence without actually booting?

---

### Post by johnman145 on 2009-05-28
with your help i finally managed to get it working :)
The problem was that it couldn't find java. I made a soflink in /usr/bin and now its working :). Thank you so much. I wonder if i could have resolved this problem earlier if bootlog was enabled. 

I still got one minor issue though, the first time i started my server i noticed webmin did NOT run. My guess is that i had a cd in my script which caused the directory to change so that webmin had a problem running. Next i tried to put a cd after my server to return to the root dir but this whole idea of cd-ing into the directory seems not so smart since there are 5 programs, all running at prio99. What is the best way to start my server in the correct directory without causing any problems for the following init.d scripts?
```

'start')
	cd /home/jdv/bg/cur/
	java -jar MyServer.jar -start &
	cd
	;;

```

---

### Post by Brandon Williams on 2009-05-29
Great that it's working now!

The short answer about webmin failing to start is that it has no relationship to changing directories in a different init script. I don't know what it is, but it's not that.

There is no possibility that changing directories in your init script will cause trouble for other init scripts, because the init script is executed in a separate process. It is not sourced in the same process as other init scripts. The current working directory is a process specific attribute that does not transfer back to the parent process, which means that when your script exits, the process that ran your script and will run the rest of the init scripts is still in the same working directory it was in before launching your script.

It sounds like webmin is working again now. If it stops working again and continues to be a problem, then I suggest you use the logging trick I previously suggested to figure out why it isn't starting. It should be pretty clear from that.

PS: Yes, it would be easier to test these things if bootlog were enabled, especially since the method that I suggested only works for init scripts that come late enough in the boot process for file systems to have been mounted in writable mode.

---

### Post by johnman145 on 2009-05-29
Everything (including webmin) is running correctly now (thx again :D). What you say that my script doesn't influence other scripts is sort of what i also thought about this morning. I believe webmin started booting up again after i included an & at the end of the command. Am i correct to assume that all scripts that run after my server will only start running when my script completes? That might explain the webmin thingy, since the server never finishes (until it is forcefully stopped of course).

And i really don't understand how they can release a server edition (which often doesn't got a monitor attached to it) without a bootlog. How are we supposed to monitor the booting process? Or is that not regarded as important by the ubuntu dev-team ??

---

### Post by Brandon Williams on 2009-05-29
You're right about the '&'. Your init script must complete execution before other scripts will be executed. It's possible to configure upstart to run init scripts that are at the same priority in parallal, but even then, if your script doesn't exit, then init scripts at higher priority levels won't run.

I've wondered the same thing about the bootlog, but I don't run a server that anyone other than me uses, so I haven't dug into it. If it's important to you, spend some time searching the forums and/or start a new thread for that discussion in the hope that folks more knowledge about it than me will chime in.

---

