---
title: "apt-get upgrade problem"
date: 2005-05-04
forum: Desktop Environments
---

### Post by jan.letko on 2005-05-04
I have a problem if I want upgrade system:

> root@letko:/home/letko # apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libxvidcore4 mplayer-586
The following packages will be upgraded:
  acroread acroread-plugins gzip libavifile-0.7c102 libfaad2-0 mplayer-686
  w32codecs
7 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/54.2MB of archives.
After unpacking 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2:
 field name `J' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@letko:/home/letko #        

Where is problem ???
list of packaged is corrupted ???

What now ???

---

### Post by Psquared on 2005-05-05
Did you do "sudo apt-get update first? Were there any errors?

I have had errors like this because I had a 3rd party repo enabled in my sources.list. Graawert I think - or maybe soulmachine. Anyway, I commented these out and reran 

Sudo apt-get update
Sudo apt-get upgrade

Worked fine for me this way.

---

### Post by jan.letko on 2005-05-06
I had problem with /var/lib/dpkg/available file, file was corrupted.

login to root mode with su

I delete /var/lib/dpkg/available file, after create clean new /var/lib/dpkg/available file.

After 

apt-get update
apt-get upgrade

now is all OK.

Thats is all.

---

### Post by Psquared on 2005-05-06
Glad you got it fixed. :D

---

