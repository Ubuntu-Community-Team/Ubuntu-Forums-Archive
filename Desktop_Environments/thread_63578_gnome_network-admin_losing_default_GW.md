---
title: "gnome network-admin losing default GW"
date: 2005-09-08
forum: Desktop Environments
---

### Post by Frederi on 2005-09-08
Hi,

I'm using network-admin to manage two network profiles.
When I switch from one profile to another everything is fine except the default gateway that is lost each time.
It's not that important, but it's a bit annoying as I switch profiles two or three times a day...
Anyone have an idea about that?
Thx,

Frederi

---

### Post by petr on 2005-09-16
[QUOTE=Frederi]Hi,

I'm using network-admin to manage two network profiles.
When I switch from one profile to another everything is fine except the default gateway that is lost each time.
It's not that important, but it's a bit annoying as I switch profiles two or three times a day...
Anyone have an idea about that?
Thx,

Frederi[/QUOTE]

I have the same problem - and the help for the network admin sucks.   eg "How to umber the gumber" is described as "press the umber gumber button" thanx.

Btw I get the impression that the network admin tool is trying to write to a file without having root permision.  Don't ask why.

---

### Post by petr on 2005-09-16
[QUOTE=Frederi]Hi,

I'm using network-admin to manage two network profiles.
When I switch from one profile to another everything is fine except the default gateway that is lost each time.
It's not that important, but it's a bit annoying as I switch profiles two or three times a day...
Anyone have an idea about that?
Thx,

Frederi[/QUOTE]

OK, the data that gets lost is saved (as clear ascii) in 
 /etc/network
Now, why does it not get loaded?
hmm..

---

### Post by petr on 2005-09-16
[QUOTE=petr]OK, the data that gets lost is saved (as clear ascii) in 
 /etc/network
Now, why does it not get loaded?
hmm..[/QUOTE]

Ok, fixed.

there is a symbolic link
 /etc/network/run/ifstate
which is involved in the recording and using of WEP keys from network-admin
I changed its permissions to read/write and now it all works.  Do this:

sudo chomd 666 /etc/network/run/ifstate

I imagine this is probably a security hole?  I guess it is ok to do this as long as I don't tell anyone...

Petr

---

