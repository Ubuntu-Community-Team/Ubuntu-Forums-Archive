---
title: "updates &amp; backup"
date: 2005-10-16
forum: Desktop Environments
---

### Post by cyfer on 2005-10-16
i don't know were exactly to post this ...hope this is the right place 

is there any way i can backup my updates ?
i mean when you install upuntu ...you have to download alot of things " talking about my needs .."

if i have to install it again ..on the same or another pc ... can't i just put those 
things i downloaded before on a cd? and then on a new install ......update from the cd?

i do ask this cause i'm new to debian based distros.....and i mess alot with any system ......then start all over after discovering the system ...

P.S.  if any one suggests getiing *.dep and put them on a cd .....how would i know those came with the cd and those i downloaded ?

any help is appreciated !

---

### Post by cwaldbieser on 2005-10-16
[QUOTE=cyfer]i don't know were exactly to post this ...hope this is the right place 

is there any way i can backup my updates ?
i mean when you install upuntu ...you have to download alot of things " talking about my needs .."

if i have to install it again ..on the same or another pc ... can't i just put those 
things i downloaded before on a cd? and then on a new install ......update from the cd?

i do ask this cause i'm new to debian based distros.....and i mess alot with any system ......then start all over after discovering the system ...

P.S.  if any one suggests getiing *.dep and put them on a cd .....how would i know those came with the cd and those i downloaded ?

any help is appreciated ![/QUOTE]
One thing that maybe you could do is to set up a local repository that the rest of your network can share.  You would have to install the apt-proxy package on the PC you want to act as the local repository, but then the packages would get cached there so when you choose to install them on other machines, you don't need to go out across the Internet.

Or do you just want to know how to image/clone an Ubuntu machine?

---

### Post by Murgle on 2005-10-16
if you store all of your downloaded debs on your computer then they will be located in /var/cache/apt/archives/ and you could just copy that folder to each new computer and it would only download newer versions of those files.

---

### Post by cyfer on 2005-10-16
[>  One thing that maybe you could do is to set up a local repository that the rest of your network can share. You would have to install the apt-proxy package on the PC you want to act as the local repository, but then the packages would get cached there so when you choose to install them on other machines, you don't need to go out across the Internet.

Or do you just want to know how to image/clone an Ubuntu machine?

no , i'm not....you see i'm new to kernel recompilation and as i say i always mess with any system .....i have to tell you that making an image is still beyond my reach now :)
it's just i've always crashed distros ....ubuntu didn't crash till now ...and i wanna be ready ....cause its gonna happen .." i always alianate packages !!"
besides i'm having a rather weired hardware ...
but if i'm not getting on your nerves can you tell how to image the installation?
cause in the future ..." near as i hope" i would get the pc to the bleeding edge :)) ...

> if you store all of your downloaded debs on your computer then they will be located in /var/cache/apt/archives/ and you could just copy that folder to each new computer and it would only download newer versions of those files.

i think this would be interesting ..but still the problem ..how to know what came on the cd ..and what i downloaded.....
to be clear ..after 2 days ..i downloaded KDE ...and other stuff ...those i wanna keep ...not download again 


thanks all for help

---

### Post by Murgle on 2005-10-16
[QUOTE=cyfer]
i think this would be interesting ..but still the problem ..how to know what came on the cd ..and what i downloaded.....
to be clear ..after 2 days ..i downloaded KDE ...and other stuff ...those i wanna keep ...not download again [/QUOTE]


hmm that is beyond me, but why do you really need to know?  if you were to just copy that folder over onto what ever machine you want it would rewrite the debs that the newly installed ubuntu put there... and it shouldn't matter unless you use a different cd for each install but even then you shold be fine, it might want to download a little bit...

---

### Post by cyfer on 2005-10-17
i wanna know ..cause i wanna keep those on a separate cd !!
not on a hard disk ....
the problem is i downloaded so much ...so the directory holds more than 
700 Mb ....but i'm sure what i've downloaded was about 400 or 500 ...

well , i think its gonna be 2 CDs at the end ....thanks any way 
you've been a great helper

---

### Post by Spyderizer on 2005-10-18
It's actually mentioned in the help file:

"How to backup/restore downloaded repositories cache?"

       1. To backup downloaded repositories cache

mkdir -p $HOME/backup/var/lib/
sudo cp -R /var/lib/apt/ $HOME/backup/var/lib/
mkdir -p $HOME/backup/var/cache/
sudo cp -R /var/cache/apt/ $HOME/backup/var/cache/
mkdir -p $HOME/backup/etc/apt
sudo cp -R /etc/apt/ $HOME/backup/etc/
sudo chown -R $USER $HOME/backup/

       2. To restore downloaded repositories cache

sudo cp -fR $HOME/backup/var/* /var/ 
sudo cp -fR $HOME/backup/etc/apt/* /etc/apt/

---

