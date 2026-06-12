---
title: "Printing from Win XP to Ubuntu"
date: 2005-11-22
forum: Desktop Environments
---

### Post by Marble2 on 2005-11-22
I currently have an HP PSC 750xi printer hooked up to my computer, which has Ubuntu installed on it. I'd like to be able to print directly from a windows XP machine downstairs to the printer hooked up to my ubuntu install. I've tried everything, CUP, samba, and it still doesn't work. Does anyone know how I can get this working?

Edit: Here's the errors I'm getting with samba. I finally got it so I could see "Printers and Faxes on ubuntu" from the windows machine, but it says I don't have enough priviledges to actually add one. Anyone know how I fix THAT. Anyway, here's the errors.
```

[2005/11/22 16:20:17, 0] printing/print_cups.c:cups_cache_reload(85)
  Unable to connect to CUPS server localhost - Connection refused
[2005/11/22 16:20:17, 0] printing/print_cups.c:cups_cache_reload(85)
  Unable to connect to CUPS server localhost - Connection refused
[2005/11/22 16:20:22, 0] smbd/service.c:make_connection(794)
  dell (192.168.1.11) couldn't find service ::{2227a280-3aea-1069-a2de-08002b30309d}
[2005/11/22 16:22:05, 0] smbd/service.c:make_connection(794)
  dell (192.168.1.11) couldn't find service ::{2227a280-3aea-1069-a2de-08002b30309d}
[2005/11/22 16:23:37, 0] smbd/service.c:make_connection(794)
  dell (192.168.1.11) couldn't find service ::{2227a280-3aea-1069-a2de-08002b30309d}
[2005/11/22 16:23:43, 0] smbd/service.c:make_connection(794)
  dell (192.168.1.11) couldn't find service ::{2227a280-3aea-1069-a2de-08002b30309d}

```

---

### Post by bootsy52 on 2007-08-08
I can tell you now the solution

I have a HP DeskJet 970C printer connected to the samba server and I HAD the same problem it has to do with the Printer Description string in /etc/printcap

I modified the driver in cups to use RAW for this printer and suddendly it worked, I further tracked down, that this has something to do, if the string HP appears in the printcap file.

While just HP works something like "HP DeskJet 970C" works not and produces this error.

Try it for yourself and modify the second column of the /etc/printcap file to something like

TEST

restart samba and you'll see you're printer.

Cups added "HP DeskJet 970C" to /etc/printcap, when I have chosen the hpijs driver

---

### Post by bootsy52 on 2007-08-08
Aahh yes something more,

you could also use

HPDeskJet970C or the like, the problem seems to be that Samba for what f**** reason ever has problems with a space character after the word HP, HP just alone works, too. But everything "HP Blah" works not

---

### Post by bootsy52 on 2007-08-08
I tracked it further down and the case is a little bit more complicated, so "HP Something" is not the real problem, but the length of the entry in /etc/printcap 

so if you have an entry like this

Printer-somethingt|HP DeskJet 970C:rm=hauptserver.some-domain.local:rp=Printer-somethingt:

it doesn't work, however if the entry looks like this

Printert|HP DeskJet 970C:rm=hauptserver.some-domain.local:rp=Printer:

it works, it works also if you remove the space between "HP DeskJet" (e.g "HPDeskJet")

This is samba-3.0.25b on Ubuntu-6.0.6.1 Server AMD64

---

