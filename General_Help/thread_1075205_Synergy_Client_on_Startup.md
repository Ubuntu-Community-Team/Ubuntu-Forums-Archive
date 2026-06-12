---
title: "Synergy Client on Startup"
date: 2009-02-20
forum: General Help
---

### Post by SergeantScar on 2009-02-20
Hey all. I just recently installed Synergy on my Ubuntu 8.10 machine in client mode and had a hard time finding a solution to get it working pre-log in screen. I am by far no expert in this, but after some slight tweaks and searching i was able to find a method that worked for me and thought i would pass it on to others who may be having the same problem.

I found there were a lot of different threads out there and none of them worked for me right away so i thought i would make this thread.

I am using an XP machine as the server and want to control my Ubuntu machine using my XP mouse and keyboard (because i use my XP maching more often). This is how I did it:

1. Went to System > Preferences > Sessions
   On the Startup Programs tab click Add
   Set the name to "Synergy Startup" (again minus the quotes)
   Set the command to "/usr/bin/synergyc <server address>"

2. Opened terminal and typed 

```
sudo /etc/gdm/Init/Default
```

Then added the following to the beginning of the file

```
/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc <name_of_server/IP_of_server>
```

Next, 

```
sudo /etc/gdm/PreSession/Default
```

Then added the following to the file RIGHT BEFORE 

# Set background color
XSETROOT=`gdmwhich xsetroot`

```
/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc --restart -n <name_of_server/IP_of_server>
```

After this I restarted and i was able to use my XP keyboard and mouse in the login screen and any other time i log out.

It took me forever to get this all working on Intrepid Ibex...

I hope this helps someone!

---

### Post by veloce on 2009-02-22
If using synergy before the login screen, you do need to be aware that synergy will be broadcasting your keystrokes - including your password - across your network.  

If in doubt you should set up ssh pipes for synergy traffic.

---

### Post by CapnChkn on 2009-03-17
Hello!

I'm just reporting that I used the above technique to set up my Synergy client in Ubuntu 8.04.1. It seemed to stumble on the first reboot, but then it get itself in order with the second.

This machine is a dual boot I've set up for the first time with XP as the initial operating system. Thank You.

---

### Post by CalaverX11 on 2009-04-14
> **veloce said:**
> If in doubt you should set up ssh pipes for synergy traffic.

Any HOWTOs you know on this matter?

---

### Post by veloce on 2009-04-14
> **CalaverX11 said:**
> Any HOWTOs you know on this matter?

I haven't checked for a while, but this is from the notes I wrote at the time:

This site explains what you are trying to achieve but the command is wrong:

[http://synergy2.sourceforge.net/security.html]("http://synergy2.sourceforge.net/security.html")

This site is more difficult to understand but has the correct code.
[http://www.redhatmagazine.com/2007/11/06/ssh-port-forwarding/#local]("http://www.redhatmagazine.com/2007/11/06/ssh-port-forwarding/#local")

---

### Post by Kaladar on 2009-06-02
I used the steps like the OP and get a connection at the login window. However, when I log in, the connection closes and doesn't come back up.

Is there another file or something that needs to be done for that to happen?

I wrote a shell script that I was trying to use via rc.local, but it never seemed to work either.

```
#!/bin/sh
# Start synergy as daemon
cd /usr/bin
synergyc --daemon <my server's name>
```

---

### Post by veloce on 2009-06-03
Synergy is gdm session specific.  When you log in you need to start it for the new gdm session created.

It's a long time since I set it up and but I have notes that suggest that I created the file:

/etc/X11/Xsession.d/12synergy

with the contents:

```
#/bin/bash 
/usr/bin/killall synergyc 
sleep 1 
synergyc localhost 
```

Add to start of /etc/gdm/Init/default:

```
# Load Synergy if Server is found 
SYNHOST=`hostname` 
TESTPROG=`ping -c 1 ` 
EXP_TEXT="1 received" 
if echo "$TESTPROG $SYNHOST"|grep -q "$EXP_TEXT"; then 
   echo 'Synergy connected'; 
   ssh -2 -f -N -L 24800:$SYNHOST:24800 loginname@$SYNHOST; 
   synergyc localhost; 
else 
   echo 'Synergy NOT connected'; 
fi 
```

---

