---
title: "Fluxbox Install script?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by fineghal on 2006-07-26
Hey, I just got done tinkering for about 2 hours with installing fluxbox onto a server installation. ](*,)  In the hope of not having to go through all of that again, I threw together a script. Any obvious errors? I know I could test and re-install but it's running on an original AMD k-6 so it'd take a while.

Any obvious flaws?

Note: I'd have to chmod +x and sudo run script

------------------

# Installs all required files to build fluxbox

#Compilers
apt-get install g++ gcc -y

# Checkinstall app
apt-get install check-install -y

#Essentials
apt-get install build-essential -y

# X System libraries and x-org
apt-get install xlibs-dev xlibs-static-dev x-window-system-dev -y
apt-get install x-window-system-core xserver-xorg -y

#copy source tar NOTE: ASSUMES SRC IS ON CD!
cp /media/cdrom/fluxbox-1.0rc2.tar.gz /local/usr/src

#Untar Flux Source
tar xvzf fluxbox-1.0rc2.tar.gz

#Change to directory created
cd /local/usr/src/fluxbox-1.0rc2

#Configure and Make
./configure
make

#Checkinstall
checkinstall

---

### Post by trent dillman on 2006-07-26
use wget to d/l the tarball, and don't forget to cd into /local/usr/src (which I think should be /usr/local/src)

---

