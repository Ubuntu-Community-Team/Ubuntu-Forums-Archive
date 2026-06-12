---
title: "Starting an executable at bootup"
date: 2006-01-27
forum: Desktop Environments
---

### Post by seakiwi on 2006-01-27
Is there some way to tell an executable to run at boot up? I am running Boinc (a distributed computing project)  which works fine but it does not start automatically at startup.

Can someone show me how to write a boot script or something that will tell Boinc to run automatically?

Relying on my memory to restart it after a reboot is not working well  :???: 

TIA!

---

### Post by adwait on 2006-01-27
Write whatever command you use to start Boinc in a text file and save it without an extension. Now use
```
chmod +x <filename>
```

Now move the file to /etc/init.d/ using
```
sudo mv <filename> /etc/init.d/
```

Now run 
```
sudo rccoonf
```

Scroll down till you see the filename of the file you just created and check the box next to it using your space bar and then ok your way out. That should run that file everytime you start your computer.

---

### Post by seakiwi on 2006-01-27
OK, I tried that and got as far as the rcconf bit (I assume your rcc**oo**nf was a typo) - however at that point it said "rcconf not found" or "not a valid command" - or words to that affect.

Any idea what I need to use here that will work?

---

### Post by TransitMan on 2006-01-27
You need to install the service.
From command prompt   sudo apt-get install rcconf

After it is installed, you will be able to finish with changing your startup with the new executable.

---

### Post by seakiwi on 2006-01-28
Thank you! Perfect! :mrgreen:

---

### Post by NeoChaosX on 2006-01-28
Add a shortcut to the Bionic executable in ~/.kde/Autostart

---

### Post by adwait on 2006-01-28
[QUOTE=NeoChaosX]Add a shortcut to the Bionic executable in ~/.kde/Autostart[/QUOTE]
No....that would run the executable when you log in, as opposed to when you boot.

---

### Post by Titus A Duxass on 2006-01-28
Here is one I use to start a GiantDisc server at boot up, beaware it runs the server in the background before anyone has logged in.  Maybe someone here could modifiy the file for you.

#! /bin/sh

PROG=/home/music/bin/gdd.pl
GDDSTART=/home/music/bin/gddstart.sh
SLEEP=2 # seconds to wait when restarting
#[ -x $PROG ] || exit 5
PID=`pidof -x $PROG`
case "$1" in
   start)
#echo "$PID"
if [ -z $PID ] ; then
   echo "Starting $PROG"
   su music -c $GDDSTART&
else
   echo "$PROG already running (PID $PID)"
fi
;;
   stop)
if [ -z $PID ] ; then
   echo "$PROG is not running"
else
   echo "Stopping $PROG"
   kill $PID
fi
;;
   status)
[ -z $PID ] || echo "$PROG running (PID $PID)"
[ -z $PID ] && echo "$PROG not running"
;;
   restart|force-reload)
sh $0 stop
sleep $SLEEP
sh $0 start
;;
   *)
echo "Usage : $0 {start|stop|status|restart|force-reload}"
exit 2
;;
esac
exit 0

You have to copy the file to /etc/init.d/ and then run the following command:

update-rc.d thefilename defaults

Then you should see something like:

/etc/rc?.d/k20??? -> ../init.d/thefilename

This will be repeated for all rc level 0 to 5.

I hope this is of some use for you.

---

### Post by kseise on 2006-02-12
[QUOTE=adwait]Write whatever command you use to start Boinc in a text file and save it without an extension. Now use
```
chmod +x <filename>
```

Now move the file to /etc/init.d/ using
```
sudo mv <filename> /etc/init.d/
```

Now run 
```
sudo rccoonf
```

Scroll down till you see the filename of the file you just created and check the box next to it using your space bar and then ok your way out. That should run that file everytime you start your computer.[/QUOTE]

I followed these directions, but when I try to log off to shutdown the computer, BOINC just hangs in the background.  It seems like the KILL signal doesn't actually stop BOINC.  Did I miss something?

---

### Post by seakiwi on 2006-02-12
That's weird. It's working perfectly for me. I've never seen any sign of BOINC hanging around when I shutdown.  

Hopefully someone else can help you because I'm just new at all this and this is way out of my league unfortunately!

---

### Post by kseise on 2006-02-13
When I last shut down, it looks like the BOINC client is actually STARTED when I shut down.  it is very bizarre.  Any help would be greatly appreciated.

---

### Post by dresnu on 2006-02-13
I don't understand your question very well, but if you want to run a program when kde startsjust put the executable under ~/.kde/Autostart. If you want to run it when your computer boots you 'll have to make a script and put it under /etc/init.d/ and then edit the appropriate runlevel in order to make it start at boot. This can be done by the Kcontrol under System Services.

---

