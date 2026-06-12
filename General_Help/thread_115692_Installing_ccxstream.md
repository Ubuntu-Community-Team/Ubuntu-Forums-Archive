---
title: "Installing ccxstream"
date: 2006-01-11
forum: General Help
---

### Post by LaLLi on 2006-01-11
Hi,

I'd like to know how can I install ccxstream.

I searched Ubuntu forums and found a solution where a rpm package was converted to deb and installed with dpkg. It worked exept it didnt install ccxstream binary. Only ccxtest and some documentation.

For those who dont know what ccxstream is its a file server for Xbox Media Center. Yes it does support SMB whares but I dont want to go trough Samba config in Ubuntu and ccxstream is faster.


EDIT:
I'v been trying this installation many times and now when I asked for help I solved it my self.

I compiled ccxstream from official sources. It first gave me error
[I]/usr/bin/ld: cannot find -lreadline
collect2: ld returned 1 exit status
make: *** [ccxstream] Error 1[/I]

But I installed libreadline5.dev (or something like that) and it worked like a charm.
The is no need to ./configure ccxstream since it doesnt work. make install is unnecessary too..just copied ccxstream to /usr/bin .

---

