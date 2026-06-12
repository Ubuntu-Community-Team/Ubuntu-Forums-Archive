---
title: "Packet Tracer i386 on amd64"
date: 2010-01-22
forum: Desktop Environments
---

### Post by brcre on 2010-01-22
I've tried two methods for forcing an install of Cisco's Packet Tracer program on my 64bit system.  Both seem to work minus one small detail.
When I run the program The GUI showing the simulated network appears just fine however the instruction panel on the side is grey stopping me from reading the assignment.  Only once have I got the instructions to come up and I've never been able to repeat it so I don't understand why they appeared that time.
Suggestions?

Here is what I've done:
```

Open the bin file in a text viewer/editor ( vim PacketTracer52_i386_installer-deb.bin )
Look for the line where they hold the temporary extract directory "export TMPDIR=`mktemp -d /tmp/selfextract.XXXXXX`"
Run the self extracting archive and before you accept the EULA go to the /tmp/selfextract.XXXXXXX dir and copy the file from there.

Note: After the user accept the EULA and before it terminates execution, the script quickly deletes the temporary directory. Copy the file before you accept EULA!

Was in the /tmp/selfextract.XXXXXXX
cd /tmp/selfextract.XXXXXXX
cp * ~/Downloads
sudo dpkg -i --force-all ~/Downloads/PacketTracer-5.2.1-u.i386.deb
sudo ln -s /usr/local/PacketTracer5/packettracer /usr/local/bin
bash packettracer

PacketTracer521.tar.gz
Extract Here (Nautilus)
cd ~/Downloads/PacketTracer521
sudo ./install

```
I've taken these instructions from other posts:
Installing Cisco packet tracer i386 on Ubuntu Karmic amd64
[http://ubuntuforums.org/showthread.php?t=1292620&highlight=PacketTracer](http://ubuntuforums.org/showthread.php?t=1292620&highlight=PacketTracer)
and 
[http://ubuntuforums.org/showthread.php?t=881641&highlight=PacketTracer&page=2](http://ubuntuforums.org/showthread.php?t=881641&highlight=PacketTracer&page=2)

System Info:
Ubuntu Release 9.10 (Karmic Koala)
Kernel Linux 2.6.31-17-generic
GNOME 2.28.1
Hardware
Memory: 7.8GiB
Processor 0-3: Intel(R) Core(TM)2 Quad CPU Q9650 @ 3.00GHz
System Status Available disk space: 680.4GiB

---

### Post by zekkerj on 2010-01-25
Hi bcre,

Packet Tracer is a 32 bit application, and Cisco doesn't supports using it in Ubuntu Karmic.

But it's easy to make it work on (K)Ubuntu, you only have to tell it where are the libs it needs.

-----------------------
In 32-bit systems, all you have to do is install libqtwebkit2.2-cil , libqt4-script, libqt4-qt3support, and libqt4-sql.

After that, locate the script that calls packet tracer(the exact location may vary on your installation) and comment the line below:

**export LD_LIBRARY_PATH=$PTDIR/lib**

As it will point PT to use shipped versions of those libraries, which are damn ugly and bugged (some strings get scrambled when shown in panels).
-------------------------

In 64-bit systems, I got a real challenge: as PT is a 32-bit application, it searches the 32-bit versions of the libraries above, and will report them as missing, even thought they **are** there. I was forced to use the shipped libraries, 'til I found the "getlibs" trick, here at Ubuntu Forum.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I've downloaded getlibs.deb ([http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)), installed it and ran

**getlibs <PTDIR>/bin/PacketTracer5**

And it found and installed all missing libraries.

But there is a cost: after that, "apt-get update" got very messy, as getlibs changed a lot of things to keep 32-bit libraries up-to-date. Since that, I can only update from "software properties" app.

---

### Post by brcre on 2010-01-28
Lessons Learned:
1. I had asked zekkerj to comment on my post to learn how to force the use of the libraries which I was sure would fix my problems.  I appreciate the response however the warnings about the side effects made me very leery to implement this.  That however does not diminish my gratitude for the response.
2. The two different procedures I listed above does get the program loaded and runs however my problem was that I couldn't read the instructions.  
I've mistakenly stumbled onto this fix:
1. Print the instructions, and when the printer dialog comes up print to file, then open them with an html reader (i.e. Firefox works).
2. Check your results right away, then close the results GUI and for me anyway it left me with a viewable dialog box.

---

