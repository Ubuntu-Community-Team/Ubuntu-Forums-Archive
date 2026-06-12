---
title: "How to know my real IP?"
date: 2005-11-13
forum: Desktop Environments
---

### Post by ominolore on 2005-11-13
Hi everybody,
I'd like to know what is my real IP, because I'd like to use the remote desktop utility, but I'm behind a router, and I don't know how to find it out.
Cheers.
Lorenzo

---

### Post by Ampersand on 2005-11-13
Go to [http://www.whatismyip.com](http://www.whatismyip.com)

---

### Post by Ruso on 2005-11-13
you always can use the  whatismyip.com site to know ur internet IP.

Or u can go to ur router probably 192.168.1.1  and watch there,

---

### Post by Zeroedout on 2005-11-13
Personally, i prefer the traceroute command. If you don't have it yet, type "sudo apt-get install traceroute" then after it installs, type "traceroute google.com" and the first or second adress should be your router.

---

### Post by quietglow on 2005-11-13
If you're the router's admin, there is usually a web address you can hit that displays that info (and allows you to change it.) I always forget mine, but you can find it by searching for "linksys default ip" substituting your brand of course.

---

### Post by NewWithoutClue on 2005-11-13
i included a script i made to download "index.html" from [www.ipchicken.com](www.ipchicken.com).
It extracts your IP from the file and prints it out....certainly not the "right" way to get it done...but i use it ;)

You will probably have to rename that file to rid the .txt and put it /usr/bin/
or any other path that shows up when you "echo $PATH" 

Anyway, just a thought.
Regards,
Paul.

---

### Post by ltmon on 2005-11-13
This is really useful for yours situation:

[http://ubuntuguide.org/#assignhostnametodynamicip](http://ubuntuguide.org/#assignhostnametodynamicip)

---

### Post by jimbob on 2005-11-13
Open a root terminal.

Type ifconfig -a

Look at your active device (eth0, wlan0, etc).

The IP is listed as inet addr: < xx. xx. xx. xx >

---

### Post by NewWithoutClue on 2005-11-13
[QUOTE=jimbob]Open a root terminal.

Type ifconfig -a

Look at your active device (eth0, wlan0, etc).

The IP is listed as inet addr: < xx. xx. xx. xx >[/QUOTE]

Needed: External
Your solution gives: Internal

Paul.

---

### Post by dto on 2005-11-13
[QUOTE=Ampersand]Go to [http://www.whatismyip.com](http://www.whatismyip.com)[/QUOTE]
also [http://www.whatismyip.org](http://www.whatismyip.org) and [http://www.whatismyip.net](http://www.whatismyip.net)

---

### Post by bionnaki on 2005-11-13
[QUOTE=Zeroedout]Personally, i prefer the traceroute command. If you don't have it yet, type "sudo apt-get install traceroute" then after it installs, type "traceroute google.com" and the first or second adress should be your router.[/QUOTE]

cool

---

### Post by jimbob on 2005-11-14
Check this site:  [https://www.grc.com](https://www.grc.com)

Scroll down and click on ShieldsUP!

He will tell you what IP he sees you as.  Also very useful for checking the integrity of your firewall.

---

### Post by thumbsoup on 2005-11-14
Tracepath is an alternative to Traceroute, and I believe is already installed with Ubuntu 5.10 (it is for me).

    tracepath google.com

According to online Linux in a Nutshell:

tracepath host [port]

TCP/IP command. Trace path to host and report the Maximum Transmission Unit (MTU.) A simplified version of traceroute without options meant for use by unprivileged users. If specified, it will use port to send UDP probe packets. host is the destination hostname or the IP number of the host to reach.

[http://www.onlamp.com/linux/cmd/cmd.csp?path=t/tracepath](http://www.onlamp.com/linux/cmd/cmd.csp?path=t/tracepath)

---

