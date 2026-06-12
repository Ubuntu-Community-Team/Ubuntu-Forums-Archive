---
title: "dbus-daemon gone wild - memory leak - high CPU consumption"
date: 2009-03-20
forum: General Help
---

### Post by tak1150 on 2009-03-20
Hi all,

I just installed Intrepid and I like it a lot. The main reason for switching from Lenny was the wireless card and OpenOffice 3 (go-OO).

Since I installed Intrepid, dbus-daemon has gone crazy several times. This happened with different programs that I was running. So I haven't been able to determine the exact program that's causing this.

The computer got so slow that I had to do:
```
sudo /etc/init.d/dbus restart
sudo /etc/init.d/gdm restart
```

to do anything at all.

Any pointers? Thanks!

---

### Post by habtool on 2009-04-04
Hi There

I am on jaunty and it's happening there too.
Will post back if I see a solution

---

### Post by Bertik on 2009-04-29
Any solution to this?

Please help!!!

It is using 99% of my 4 core processor!

I have just upgraded from Intrepid to Jaunty 9.04 64 Bit

When I hover over the process (dbus-daemon) in System Monitor I can see this:
//bin/dbus-daemon --fork --print-pid 6 --print address 9 --session

Also, Python takes a lot of processor resources
When I hover over the process (python) in System Monitor I can see this:
python /usr/share/system-config-printer/applet.py

---

### Post by Bertik on 2009-04-29
It seems that it was Samba....
I have uninstalled Samba and all is back to normal.

---

### Post by danteuk on 2010-12-30
Finding a cause is nice but any progress on actually?

Kubuntu 10.10
dbus-daemon will suddenly cause 99% cpu usage.
Even machine is not in use and should be just idle ( ie sometimes during the night ).

---

### Post by LiSrt on 2011-03-17
I'm getting this too on Kubuntu Maverick - submitting bug...

bug link - [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/737170](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/737170)

---

### Post by .nedberg on 2011-03-21
> **LiSrt said:**
> I'm getting this too on Kubuntu Maverick - submitting bug...

bug link - [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/737170](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/737170)

+1, same problem for me

---

### Post by shad0wslay3r on 2011-03-31
Anyone find a solution?  It's currently going crazy on all 4 of my cores in 10.10.

I ended up finding this problem because for some reason skype went crazy, and maxxed out my CPU.

---

### Post by Rebootkid on 2011-04-06
Add my name to the list of affected users.

---

### Post by stephenhau on 2011-05-13
And here too.

Hard drive activity constantly on.
Htop shows high swap usage, even though I'm running the usual programs that normally leave my swap unused.
Htop and System Monitor show CPU usage at only about 20% max, though dbus itself is listed as CPU usage ~60%.

---

### Post by stephenhau on 2011-05-16
[This post]("http://ubuntuforums.org/showpost.php?p=10698464&postcount=5") suggests a solution – this bug might be related to plugging in your iPhone.

---

### Post by LiSrt on 2011-05-17
I've found out that killing the kpackagekit (may be called something different, not on a linux machine right now) icon process returns dbus-daemon to a sensible CPU usage.

Still present in natty.

---

### Post by godvirus on 2011-06-24
> **LiSrt said:**
> I've found out that killing the kpackagekit (may be called something different, not on a linux machine right now) icon process returns dbus-daemon to a sensible CPU usage.

Still present in natty.


Killing this process fixed it for me. Thanks!
The name of the process is:

/usr/lib/kde4/libexec/kpackagekitsmarticon

---

### Post by t.rei on 2011-07-14
I have neither kde installed nor an iphone. I still get that the //bin/dbus-daemon --fork --print..... process starts going nuts.

---

### Post by InnerBushman on 2012-04-22
I donno if it's related but i have noticed that there is also high "HDD write" reported by system monitor.

Do you guys have [COLOR=Navy]**Bluetooth**[/COLOR]? 
I've noticed my Blueman applet 1.22 was acting weird when the dbus-demon was at trial. The "Make discoverable" menu option from notification area was "flashing".
Appearing and disappearing every half a second. I removed the **[COLOR=Navy]BT[/COLOR]** dongle and viola! Everything went back to normal. 
[COLOR=DarkRed]If you have a [COLOR=Navy]**Bluetooth**[/COLOR] dongle try to remove it[/COLOR][COLOR=DarkRed] when the CPU is high[/COLOR]  and see if everything will go to normal.
If yes, we have another suspect to be reported.

Let me know if this is the case for any of you! ;]

Bushman

PS: i don't have iPhone.

---

### Post by oldos2er on 2012-04-22
Closed, necromancy.

---

