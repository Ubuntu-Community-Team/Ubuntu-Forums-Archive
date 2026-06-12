---
title: "chmod 777 without sudo"
date: 2009-04-15
forum: General Help
---

### Post by mocka on 2009-04-15
I'm running on Ubuntu Server Edition.

I wanted to chmod -R 777 a directory over SSH, something I've done a couple of times before. Anyhow, this time I forgot to write "sudo" in front of the command, so what I wrote was "chmod -R 777 /home/rt/torrents".

What happened next was that I lost connection to the server, so I restarted it. I can still not make any connection to the server.

What happened, and how can I fix it?

---

### Post by jowilkin on 2009-04-15
It seems unlikely that your chmod command is causing the inability to connect.  It should just say permission denied.

I think you have some other problem.  What message do you get when you try to ssh into the server?

Also you probably didn't need sudo to modify that directory if you were logged in as the "rt" user since the directory was inside their home directory.  In general you want to only use sudo when it's necessary.

---

### Post by jbrown96 on 2009-04-15
The chmod command wouldn't have any effect on SSH connections. Something else probably happened. Did you try to ping the server? ```
ping -c 5 SERVER-IP
```

Word of advice: You shouldn't make files executable unless it's really necessary. You would probably be fine with ```
sudo chmod -R 666 /home/rt/torrents
```

Tip: If you forget to add sudo to a command, and need to re-run it as root. just type ```
sudo !!
``` (!! is said "bang bang"). It will re-run the command and alter the command history, so if you press the up key it won't say sudo !! but will have your previous unsuccessful command pre-fixed by sudo, which is nice if you need to run it again.

---

### Post by mocka on 2009-04-15
> **jowilkin said:**
> I think you have some other problem.  What message do you get when you try to ssh into the server?


Since I'm running Windows XP on the computer I'm SSH'ing from, I use the application PuTTY. Whenever I try to connect I get the following error message:

"Network error: Connection timed out"

Will the solution be to connect a monitor to the server?

> **jbrown96 said:**
> Tip: If you forget to add sudo to a command, and need to re-run it as root. just type ```
sudo !!
``` (!! is said "bang bang"). It will re-run the command and alter the command history, so if you press the up key it won't say sudo !! but will have your previous unsuccessful command pre-fixed by sudo, which is nice if you need to run it again.

Thank you for your tips, I will certainly try them out when I get the server up and running again.

---

### Post by jbrown96 on 2009-04-15
Try to ping it if you know it will have the same ip address. Or if you have access to the local network, you could use nmap to do an automated ping sweep on all ip's to see if it was assigned an address that you weren't expecting.

```
sudo apt-get install nmap
```
```
sudo nmap -sP 192.168.1.*
``` or if your network uses 10.x.x.x addresses replace with 10.0.0.*

You might also be able to get your dhcp server (probably the router) to re-assign dhcp addresses that might force the server to re-connect to the network.

---

### Post by jowilkin on 2009-04-15
> **mocka said:**
> 
Will the solution be to connect a monitor to the server?


If you can that would be a good way to figure out what's going on.  See if you can connect to the outside world from the server.  For instance, hook up a monitor and a keyboard and try to ping [www.google.com](www.google.com) from the server.

---

### Post by mocka on 2009-04-15
I tried to ping in cmd. The response was:

> **CMD]

Request timed out.

Ping statistics for 192.168.0.185: Packets: Sent = 4, Received = 0, Lost = 4 (100% loss)
[/QUOTE]

EDIT:
[QUOTE=jowilkin said:**
> If you can that would be a good way to figure out what's going on.  See if you can connect to the outside world from the server.  For instance, hook up a monitor and a keyboard and try to ping [www.google.com](www.google.com) from the server.

Alright, will do in five minutes.

EDIT2: It seems like the reason why I couldn't connect after I restarted the server was that I had no keyboard attached - therefore it would not continue booting the OS. Thanks a lot for your rapid answers!

---

