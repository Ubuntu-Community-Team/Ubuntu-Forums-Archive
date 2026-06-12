---
title: "Accidentally deleted /etc/init.d"
date: 2005-01-19
forum: General Help
---

### Post by blueplazma on 2005-01-19
I accidentally deleted the entirety of my /etc/init.d directory today.  The machine is only a web server, with a phpbb forum running.  I'm totally averse to reinstalling, but I'd rather pull the machine back together somehow.  Is there any way to do this?

---

### Post by hardcandy on 2005-01-19
Can you retrieve it from the trashcan? If not maybe boot up the live cd copy its file and tweak it. Or copy one from a client machine using ssh.
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Does the forum still work? Which one is it? Maybe I've been to it.  :wink:

AND BEFORE YOU DO ANYTHING ELSE--------> BACKUP!

---

### Post by blueplazma on 2005-01-19
I was kind of hoping there would be some easier answer than restoring.  I didn't know if there was some method with apt-get.  I was using rm, unfortunately, so no trash can.

---

### Post by mendicant on 2005-01-19
Well, you can reinstall every package on your system via aptitude, using the 'L' command.  Just run aptitude, press down arrow until you get to 'Installed Packages' and press 'L'.  Naturally, if you know which packages you have installed which also have /etc/init.d/* entries, you can just reinstall those.

---

### Post by mendicant on 2005-01-19
% dpkg -S init.d | grep -v sysv-rc | cut -d: -f 1 
would give you the list of packages that have entries in init.d, so you could run something like (assuming bash):
% aptitude reinstall $(dpkg -S init.d | grep -v sysv-rc | cut -d: -f 1 | sort | uniq)

Of course, I haven't tried this, but it looks right :)

---

### Post by blueplazma on 2005-01-19
Thanks, mendicant.  The script is working, I think that should fix most of it.  Thanks.

---

### Post by nerses on 2007-09-28
Boot your Ubuntu from CD, and cp the deleted files from booted partition to your own partition. it will look like similar to this. 
cp -r /etc/init.d/* /media/disk/etc/init.d

---

### Post by nerses on 2007-09-28
:)> **nerses said:**
> Boot your Ubuntu from CD, and cp the deleted files from booted partition to your own partition. it will look like similar to this. 
cp -r /etc/init.d/* /media/disk/etc/init.d. enjoy :) 

---

