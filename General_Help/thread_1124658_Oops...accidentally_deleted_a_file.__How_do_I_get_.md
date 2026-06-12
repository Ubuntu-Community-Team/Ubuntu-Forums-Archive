---
title: "Oops...accidentally deleted a file.  How do I get it back??"
date: 2009-04-13
forum: General Help
---

### Post by tominto on 2009-04-13
I accidentally deleted dll.conf from sane.d directory.  I did this using the terminal.  How do I get it back, or get a new copy?  

Help appreciated...thanks!

---

### Post by Aubergines on 2009-04-13
Unfortunately you can't. The power of being root is dangerous! :P In the future you can always add something into your .bashrc like:
```

alias rm="rm -i"

```
or even
```

alias rm='mv $1 ~/.Trash'

```
if you want rm to move files to the trash rather than completely deleting them.

---

### Post by tominto on 2009-04-13
Ok thanks.  Is there some way I can download a new copy or something; I think the file was basically just text.

---

### Post by linuxrollup on 2009-04-13
In Terminal, what command did you use? It might be in the Trash.

---

### Post by Aubergines on 2009-04-13
> **tominto said:**
> Ok thanks.  Is there some way I can download a new copy or something; I think the file was basically just text.
Ah here you go
```

# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
cardscan
coolscan
coolscan2
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
cardscan
coolscan
coolscan2
#dc25
#dc210
#dc240
dell1600n_net
dmc
epjitsu
epson
epson2
fujitsu
#gphoto2
genesys
gt68xx
hp
hp3900
hpsj5s
hp3500
hp4200
hp5400
hp5590
hpljm1005
hs2p
ibm
leo
lexmark
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
pie
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l
```

---

### Post by drs305 on 2009-04-13
Edit: Looks like I'm a tad too late...

Here's a copy of mine. Looks pretty generic:
[http://paste.ubuntu.com/150426/]("http://paste.ubuntu.com/150426/")

---

### Post by tominto on 2009-04-13
That's it.  Thanks guys ):P

---

