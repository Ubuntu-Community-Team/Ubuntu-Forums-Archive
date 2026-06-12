---
title: "SAMBA refuses to run/uninstall/reinstall"
date: 2009-05-21
forum: General Help
---

### Post by SonicComKid on 2009-05-21
Recently out of the blue I noticed my SAMBA shares suddenly no longer worked. As most would check I tried to run sudo /etc/init.d/samba restart

however reguardless of what I do the system freezes, and only when I do anything to do with SAMBA. All of the following results in a freeze:

sudo /etc/init.d/samba stop
sudo /etc/init.d/samba start
sudo aptitude remove samba
sudo aptitude install samba
pkill smb
pill smbd
pgrep smb

I'm all out of ideas of how to repair samba, nothing I do works.
Every time the system tries to stop samba it reads:  start-stop-daemon: waring: failed to kill 5054: no such process   then just sits there forever (even ctrl C does nothing)

If I try to start samba it gives the 'starting samba' message and hangs there forever. I even tried leaving it over night to see if there was something slowing it down. Any ideas?

---

### Post by SonicComKid on 2009-05-21
*solved*

I got a solution thanks to boss_mc on the IRC:

I removed all instances of S20samba from /etc/rc1.d through /etc/rc6.d  did a forced restart of the system, and completely purged samba using sudo aptitude purge samba. (I backed up /etc/samba/smb.conf)  reinstalled samba and moved my config back in before doing a second system restart.

---

