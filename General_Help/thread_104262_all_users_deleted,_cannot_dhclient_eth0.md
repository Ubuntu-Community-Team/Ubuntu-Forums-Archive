---
title: "all users deleted, cannot dhclient eth0"
date: 2005-12-15
forum: General Help
---

### Post by peterbrowne on 2005-12-15
someone deleted all my user account (i know who it is and fucking hate him), so i remade the gdm and dhcp ones hoping i could get on the internet.

GDM works fine, but dhclient give a "network is down" error - i tried ifup eth0 but it didn't work.  I can't use either eth0 or ath0 because of this and really hope to beat the shit out of him on monday (major snow storn will cancel the buses) (or get him suspended from school for 3 days - again).

could you please help me?

---

### Post by peterbrowne on 2005-12-18
please help - i cannot seem to run dpkg -i either - time for a fuill reinstall i think :(

---

### Post by schilcha on 2005-12-18
[QUOTE=peterbrowne]please help - i cannot seem to run dpkg -i either - time for a fuill reinstall i think :([/QUOTE]

Reinstall is probably the safest thing to do. 

There's one thing you could try: 
Since I don't really know, what you men by "deleted all my user account" (though I for sure know what you mean with "i know who it is and fucking hate him"), I assume that your /etc/passwd was deleted. So, if that's the case, you can 
*) boot from a live-CD
*) restore the /etc/passwd on your harddisk according to the one found on the live-system (if yours is completely lost, simply copy the one from cd -- it can't do more harm)
*) if your /etc/group is also deleted, do the same for it
*) reboot from harddisk into the RESCUE system and add the accounts you created manually (e.g. with "useradd"). MIND: make sure to assign the user- and group-IDs you had before!

So, I really can't say, if that works (luckily, I've never tried it). But, if reinstallation means major efforts for you, then give it a try...

Good Luck

---

### Post by peterbrowne on 2005-12-18
he had used the GUI to delete all users except for peter and an account he made for himself.  i recreated dhcp and gdm - but it still doesn't work and i cant dpkg

---

### Post by schilcha on 2005-12-18
Obviously you need more users than dhcp and gdm. Here's my user-list (minus the private ones). Since you're already creating new users, just go ahead and add some more...
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:101:101::/nonexistent:/bin/false
syslog:x:102:102::/home/syslog:/bin/false
klog:x:103:103::/home/klog:/bin/false
cupsys:x:100:104::/:/bin/false
fetchmail:x:104:65534::/var/run/fetchmail:/bin/sh
messagebus:x:105:110::/var/run/dbus:/bin/false
hal:x:111:111:Hardware abstraction layer,,,:/var/run/hal:/bin/false
saned:x:112:112::/home/saned:/bin/false
gdm:x:106:113:Gnome Display Manager:/var/lib/gdm:/bin/false

```

---

### Post by Ruskie on 2005-12-18
Or boot as repair console and put there the passwd file from live cd, as previously said

---

### Post by peterbrowne on 2005-12-18
OOPS.... i should read replies before reinstalling

damn me to hell!

---

