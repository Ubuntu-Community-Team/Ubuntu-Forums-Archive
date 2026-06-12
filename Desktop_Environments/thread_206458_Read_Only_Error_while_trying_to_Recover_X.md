---
title: "Read Only Error while trying to Recover X"
date: 2006-06-30
forum: Desktop Environments
---

### Post by sapphiretiger on 2006-06-30
Ok, so here's the story;

I've come back to linux after a long period of time, and needless to say, I'm a n00b with a few things. After using Automatix to install nvidia drivers (among other things), x refuses to start up. No biggie, I've been there and used dpkg-reconfigure xserver-xorg to get back to normal in previous installs.

However, this time I've installed on a reiserfs partition, and when at the end of the process, I get a read-only filesystem error. Same thing when trying Automatix's suggestion (restoring from a backup config-file). Is there a way I can get back in?

---

### Post by wieman01 on 2006-06-30
A silly question... Is there a chance that your harddisk is full? This happened to me once. I had to delete all temp files and eventually resized my partition which resolved the problem.

Not sure if this is a suitable solution in your case.

He

---

### Post by mozetti on 2006-06-30
Are you using the sudo command to accomplish this? If not, try that first.

---

### Post by sapphiretiger on 2006-06-30
[QUOTE=wieman01]A silly question... Is there a chance that your harddisk is full? This happened to me once. I had to delete all temp files and eventually resized my partition which resolved the problem.

Not sure if this is a suitable solution in your case.

He[/QUOTE]

I ran into that at one point in one of my earlier installs. Nope, shouldn't be the case here unless Ubuntu grew to cover 30 or so GB of space in a few days! :lol: 

Thanks though.

---

### Post by sapphiretiger on 2006-06-30
[QUOTE=mozetti]Are you using the sudo command to accomplish this? If not, try that first.[/QUOTE]

Tried it. Still gives me the same error. If single user mode is booting as root by modifying the boot line to include the word single (I'm still a bit foggy, and I haven't had my tea or coffee yet today), that doesn't work either.

---

### Post by grooverider on 2006-06-30
ok there are a couple things u can try, when u type 'mount' in the command line, this will show u the harddrives which are mounted and if they r readonly or rw, if it's mounted only as readonly and u want it as rw, then just unmount it and mount it with rw enabled, next concerning ur xorg.conf and gdm.conf-custom, you could simplay boot with the livecd, this will configure things correctly then just simply copy the necessary files and put them on ur harddrive by replaying the ones from ur previous install, this should work, good luck

---

### Post by sapphiretiger on 2006-06-30
[QUOTE=grooverider]ok there are a couple things u can try, when u type 'mount' in the command line, this will show u the harddrives which are mounted and if they r readonly or rw, if it's mounted only as readonly and u want it as rw, then just unmount it and mount it with rw enabled, next concerning ur xorg.conf and gdm.conf-custom, you could simplay boot with the livecd, this will configure things correctly then just simply copy the necessary files and put them on ur harddrive by replaying the ones from ur previous install, this should work, good luck[/QUOTE]


Mount tells me the drive is mounted rw, and unmounting it fails without displaying an error. The drive is still read-only.

I'm able to get in via knoppix though. Knoppix reports most of the 30gb of space is free on its partition. Now, I'm going to try overwriting config with a backup config.

---

### Post by sapphiretiger on 2006-06-30
[QUOTE=sapphiretiger]...Now, I'm going to try overwriting config with a backup config.[/QUOTE]

Still read-only.#-o

---

