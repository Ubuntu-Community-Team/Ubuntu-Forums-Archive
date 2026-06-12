---
title: "Syslog messages on Ctrl-F12"
date: 2005-12-12
forum: General Help
---

### Post by klepto on 2005-12-12
Hello everyone,

This is my first post here. I just installed kubuntu(sp?) last night on
my crappy compaq m2105us laptop. It installed everything with just
an ati driver problem which was changed to vesa due to searching
these forums. 

I've been a linux/freebsd users for ages but lost my touch after administrating on too many windows machines. Question, how can you pipe syslog messages to a window like ctrl-f12? I've done this forever but I can't remember how to do it. 

I have alot of respect for this distro and the community. Everything is running correctly on my laptop including a broadcom wifi card connecting to a router using wpa.

---

### Post by mlomker on 2005-12-12
You'll have to add a line to the /etc/syslog.conf file directing the output to that TTY.  By default Ubuntu only has 1-6 enabled with 7 getting used by X-Windows.  That can be changed by modifying a couple of files, but it'd be easier for you to just use 6.

```

sudo nano /etc/syslog.conf

```

You'd add a line like this:

```

*.*                         /dev/tty6

```

---

### Post by One Quick Question on 2005-12-12
Hmm.  I did it differently. 
In /etc/inittab I added this line: 
```
7:2345:respawn:/usr/bin/tail -f /var/log/messages > /dev/tty12
```
(Although that's for 'messages', you could of course change that to 'syslog')

---

### Post by mlomker on 2005-12-12
[QUOTE=One Quick Question]Hmm.  I did it differently. [/QUOTE]

That's cool.  There's more than one way to do most things when it comes to computers.

---

