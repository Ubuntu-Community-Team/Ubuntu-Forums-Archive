---
title: "xRDP problem"
date: 2007-03-01
forum: Desktop Environments
---

### Post by nixfreak on 2007-03-01
Im really new at linux so dont know much, i ve got Ubuntu with VHCS installed on my server, VHCS seems to be working fine. But i would like to get in to the GUI, i installed xRDP...opened up windows remote desktop, and tried to connect, which option am i supposed to choose?

It give me 5-6 options like sesman, console, vnc-any etc.....it tried them and use my root Username and password, but it gives me some error message saying "error problem connecting" (with sesman)

If i choose Sesman-Xrdp, it says "sesman started a session" then "some problem"

this is what i get in sesman log:

```
[20070301-09:30:33] [DEBUG] granted TS access to user root
[20070301-09:30:33] [DEBUG] starting Xrdp session...
[20070301-09:30:33] [DEBUG] error doing execve for user root - pid 32180
[20070301-09:30:34] [DEBUG] error starting window manager root - pid 32179
[20070301-09:30:35] [DEBUG] session 32178 - user root - terminated
```

would appreciate any help

Thanx

Freak

---

### Post by nixfreak on 2007-03-01
anyone?

---

### Post by nixfreak on 2007-03-01
k its working now, but its too slow......anyway to make it faster? im using Windows remote desktop to view

thanx

Freak

---

### Post by karsten123456789 on 2007-03-08
Hi!
I've got the same problem like you first had...

If i choose Sesman-Xrdp, it says "sesman started a session" then "some problem"

and your posted log looks like mine.

I'm using Ubuntu (with gnome).

How did you solve this problem?

My aim is to have a terminal-server compatible with rdp on wich multiple users can work in their own session.

---

### Post by bkortleven on 2008-02-17
Hi, 

Still having the same issue:

This is what the rdp connection, using sesman-X11rdp, I see this coming:


"connecting to sesman ip 127.0.0.1 port 3350
sesman connect OK
sending login info to sesman
login succesful for display 11
started connecting
some problem"

and in the sesman.log file I see:

 tail sesman.log -f
[20080217-21:03:55] [DEBUG]         argv[0] = X11rdp
[20080217-21:03:55] [DEBUG]         argv[1] = :11
[20080217-21:03:55] [DEBUG]         argv[2] = -geometry
[20080217-21:03:55] [DEBUG]         argv[3] = 1200x700
[20080217-21:03:55] [DEBUG]         argv[4] = -depth
[20080217-21:03:55] [DEBUG]         argv[5] = 16
[20080217-21:03:55] [DEBUG]         argv[6] = -bs
[20080217-21:03:55] [DEBUG]         argv[7] = -ac
[20080217-21:03:55] [DEBUG]         argv[8] = (null)
[20080217-21:03:55] [INFO ] session 12738 - user bram - terminated


Some more info about the system:
Ubuntu Feisty 32bit, uptodate
xrdp from xrdp_0.3.1_i386.deb

Thanks for the info if anyone knows how to get this working...
I want to use my old Compaq T-series thinclient with this setup (they don't connect to X11 by itself, I regret)


Did anyone

---

### Post by bcross64 on 2008-04-22
[http://www.opensourcehowto.org/how-to/xrdp/xrdp--fedora-core-3.html](http://www.opensourcehowto.org/how-to/xrdp/xrdp--fedora-core-3.html)

That's a howto on xrdp. He gives a script to put in init.d which I would be cautious of. I haven't tried this yet, but I'll post my results as soon as I do.

---

### Post by escipio on 2008-05-15
Hello:

I'm having the same problem. 
Did you test the script? any problem?
I also found this:
[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/220005](https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/220005)

Thank you!

---

### Post by tjandracom on 2008-07-05
i used to have the same problem, that's because X11rdp binary is missing. most likely we should build it from the source.
i googled around and found from 
[http://server1.xrdp.org/temp/](http://server1.xrdp.org/temp/)
just right click and save the X11org to /usr/bin
change the file permission so others group could read and execute.
and it works! 
but still i have problem with keyboard mapping.
it would be nice if ubuntu/debian package is available so anyone dumb enough like me doesn't have to build it from source.

---

### Post by escipio on 2008-07-20
Hello:

I did what you said, but it did not work. When I configure the net by System-> Network, it is not able of finding the IP. Not in the manual configuration nor in the itinerant mode.

I was able of configuring it but adding the following to interfaces:

auto wlan0
iface wlan0 inet dhcp
	pre-up iwconfig wlan0 essid "net name"
        pre-up iwconfig wlan0 mode Managed
        pre-up iwpriv wlan0 set AuthMode=WPAPSK
        pre-up iwpriv wlan0 set EncrypType=TKIP
        pre-up iwpriv wlan0 set WPAPSK=<code WPA>
        pre-up ifconfig wlan0 up


The problem is that some times, when I reinit the computer, the net does not work and I have to reinit it.

Regards,

Escipio

---

