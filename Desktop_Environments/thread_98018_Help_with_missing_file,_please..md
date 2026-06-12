---
title: "Help with missing file, please."
date: 2005-12-02
forum: Desktop Environments
---

### Post by L Campbell on 2005-12-02
I am trying to get my Kubuntu 5.10 to connect to the 'net with a dial-up modem.

When I click on the ' Internet Dialup Tool ' I get an ERROR message:-
..................
/etc/resolv.conf is missing or can't be read

Ask your system admistrator to create this file (can be empty) with appropriate read and write permissions.
...................

Well, I can see the file ' resolv.conf ' (size 31B) on my desktop, so I guess its empty but I have no idea what my next move is.

I would appreciate it if someone could help me here.

Thanks.

---

### Post by teaker1s on 2005-12-02
create a launcher and then make sure it has 'gksudo' as the first part of command or from console use 'sudo mycomand'
It could just be a permission issue

---

### Post by GeneralZod on 2005-12-02
Do you have any idea how resolve.conf got on your desktop in the first place? Seems very odd...

Either way, please post the contents of this file! If we're lucky, it will be a simple case of copying this to the correct place.

---

### Post by L Campbell on 2005-12-02
[QUOTE=GeneralZod]Do you have any idea how resolve.conf got on your desktop in the first place? Seems very odd...

Either way, please post the contents of this file! If we're lucky, it will be a simple case of copying this to the correct place.[/QUOTE]

Thanks for your reply.

I have both Kubuntu 5.10 and Ubuntu 5.10 and I have been trying to get online, with dial-up, for about 6 weeks.  It seemed that Kubuntu would be the easier one to configure, since it has KDE KPPP, which is what my Mepis system uses and it was a snap to set up and has always worked perfectly.

It was, no doubt, me who got this file onto the desktop but I don't remember why I did it.    :-)

I also find that this file is in my 'home' folder.  The only thing I see when I open it is the address ' file:///home/lewis/resolv.conf ' .  Under 'permissions' it is 'read-write'.

Kind regards.

---

### Post by GeneralZod on 2005-12-02
[QUOTE=L Campbell]
I also find that this file is in my 'home' folder.  The only thing I see when I open it is the address ' file:///home/lewis/resolv.conf ' [/QUOTE]

Try 

```

sudo cp /home/lewis/resolv.conf /etc

```

and try again.

---

### Post by L Campbell on 2005-12-02
[QUOTE=GeneralZod]Try 

```

sudo cp /home/lewis/resolv.conf /etc

```

and try again.[/QUOTE]

That worked perfectly, thanks.

I configured my KPPP but it wouldn't dial.

With TTY0, 1, 2, 3, 4, I got 'modem ready', so I 'Queried' it and that seemed to go well except the 'Results' page was always empty of data.

I tried to connect but didn't get past 'initializing'.

My modem is an internal SmartLink with SL1900 chipset and I have the file ' scanModem.gz ' but I don't know if this would do me any good at this point as it appears (to me, anyway) that the system 'sees' the modem.

Might you also have a suggestion for this?

Kind regards.

PS I'll be gone for the rest of the day so, if you don't hear back from me, please don't think I have lost interest.   :-)

---

