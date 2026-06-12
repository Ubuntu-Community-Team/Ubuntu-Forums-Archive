---
title: "X will not start or reconfigure (Stale NFS file handle)"
date: 2009-04-06
forum: General Help
---

### Post by luotinen on 2009-04-06
Hi!

I'm running Ubuntu 8.10 (Intrepid Ibex) on Asus 901 EEEpc minilaptop.

I powered it down (cold power off) and now it will not start X or GDM. Attempt to reconfigure spits out error messages. Attempt to start X spits a warning about /tmp/.X0-lock and any attempt to tamper with that file ends up with error messages.

Some key error messages:

[Windows (tm) blue screen with the following text:]
Un-Translated:
Could not start the X server (your graphical environment)
due to some internal error. Please contact your system administrator
or check your syslog to diagnose. In the meantime this display will be
disabled. Please restart GDM when the problem is corrected.

Original (in Finnish):
X-palvelimen (graafisen ympäristön) käynnistys ei onnistunut sisäisen virheen takia. Ota yhteyttä järjestelmän ylläpitäjään
tai tutki järjestelmälokia. Tämä näyttö poistetaan toistaiseksi
käytöstä. Käynnistä GDM uudelleen, kun ongelma on korjattu.

[after shell login, I attempt to reconfigure xorg]
sudo dpkg-reconfigure xserver-xorg -phigh

[the command runs and lots and lots of error messages are printed, with most of them pointing at /usr/share/perl5/Debconf/Format/822.pm line 84]

[I attempt to start X manually]
startx

[a nice array of error messages are spit out]
xauth: /home/luotinen/.Xauthority not writeable, changes will be ignored
3X xauth: error in locking authority file /home/luotinen/.Xauthority 
Fatal server error: Can't read lock file /tmp/.X0-lock
xinit: Stale NFS file handle (errno 116): unable to connect to X server
xinit: No such process (errno 3): Server error
xauth: error in locking authority file /home/luotinen/.Xauthority

[I attempt to give write permission to .Xauthority]
sudo chmod +w /home/luotinen/.Xauthority

[Works. Now I will kill the lock file .X0-lock]
sudo rm /tmp/.X0-lock

[Doesn't work:]
Un-Translated:
rm: cannot remove /tmp/.X0-lock: Stale NFS file handle

Original (in Finnish)
rm: tiedostoa /tmp/.X0-lock ei voi poistaa: Vanhentunut NFS-tiedostokahva

According to the Internetz a reinstall would solve this issue. However, that sounds a rather Windowish approach to problems... :D

Any clues on how to solve this?

---

### Post by Peter09 on 2009-04-06
Suggest you force a file system check, it will remove the stale handles.

See here

[http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html](http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html)

---

### Post by luotinen on 2009-04-06
Ha. The community is way too slow.

It could be solved with:
**sudo e2fsck -f /dev/sda1** (use **mount** to see what drive is having stale NFS issues)

and hitting the y-button like crazy.

---

### Post by luotinen on 2009-04-06
> **Peter09 said:**
> Suggest you force a file system check, it will remove the stale handles.

See here

[http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html](http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html)

Yes. I'd definitely recommend file system check over reinstalling the system.

Why doesn't it flag the file system to be checked (on boot) when it notices the Stale NFS file handle?

---

### Post by F6F Freak on 2009-04-06
Yeah. I'm having the same problem... Cold shutoff, lots of errors that are killing me...
I cannot afford to wipe either of my file systems (Windows or Ubuntu).
If I press the wrong button(s) will either of the methods mess up my computer?

---

