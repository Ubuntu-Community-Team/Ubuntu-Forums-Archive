---
title: "Serious Sam First Encounter"
date: 2007-11-24
forum: Gaming &amp; Leisure
---

### Post by go_beep_yourself on 2007-11-24
Where can the original Serious Sam be downloaded for Linux? I tried downloading frm here. but apparently it is only an update to the game.

[http://files.seriouszone.com/download.php?fileid=617](http://files.seriouszone.com/download.php?fileid=617)

This is the message I get from running that.

```
./ssamtfe-beta3.sh.bin 
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
An embedded MD5 sum of the archive exists but no md5sum program was found in /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." ./ssamtfe-beta3.sh.bin -check
 All good.
Uncompressing Serious Sam: The First Encounter for GNU/Linux beta3 patchtail: Warning: "+number" syntax is deprecated, please use "-n +number"
..................................
=============================================================
Welcome to the Serious Sam: The First Encounter for GNU/Linux beta3
=============================================================

Would you like to read the README for this update?  [Y/n]: Y

This is beta 3 of The First Encounter.

Notable changes:

- Shouldn't had issues with vorbis loading (I hope).
- Writes user data to ~/.serious/serioussam now. This is to make way for
  The Second Encounter. To keep your old settings, you should do this:

    mkdir ~/.serious/serioussam
    mv ~/.serious/* ~/.serious/serioussam
    (ignore the error).

  Do that before you start the new version, or you'll screw things up. If you
  don't do it, your old settings will be ignored and you get a fresh default
  configuration.

- No beta expiration, since I'm not giving this too much time.


The game is STILL not beatable by default. This is a bug. You can "cheat" to
 kill the last boss when you are sick of shooting at him, though. Pull down
 the console and type:

 /cht_bKillFinalBoss = 1;

(The '/' and ';' are necessary.) This will kill the boss and trigger the
 endgame cinematic.

This bug actually breaks the opening cinematic of The Second Encounter, so
 it's important to fix it, cheat or not. But not for this patch.

Have fun!

--ryan.



=============================================================
Would you like to apply this update? [Y/n]: Y

Please enter the installation path: []: /usr/local/games/

=============================================================
Performing update:
ERROR: Can't find /usr/local/games//Bin/ssam_lnxded.dynamic
The program returned an error code (3)
chris@ubuntu:~/Desktop$ sudo linux32 ./ssamtfe-beta3.sh.bin 
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
An embedded MD5 sum of the archive exists but no md5sum program was found in /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." ./ssamtfe-beta3.sh.bin -check
 All good.
Uncompressing Serious Sam: The First Encounter for GNU/Linux beta3 patchtail: Warning: "+number" syntax is deprecated, please use "-n +number"
..................................
=============================================================
Welcome to the Serious Sam: The First Encounter for GNU/Linux beta3
=============================================================

Would you like to read the README for this update?  [Y/n]: n

=============================================================
Would you like to apply this update? [Y/n]: n
Update cancelled.

```

---

### Post by darkstar14 on 2007-11-25
Well, try installing it trough Cedega or Wine ...
I found a native linux version of Serious Sam: The First Encounter, but it's beta version and just 3.65 MB (?!) ... **[link]("http://files.seriouszone.com/download.php?fileid=617")**

There is a Serious Sam 2 beta version too on their official site ( [http://www.croteam.com/](http://www.croteam.com/) ) **[link]("http://files.seriouszone.com/download.php?fileid=1190")**


Gabriel

---

### Post by IanW on 2007-11-26
Try [here.]("http://liflg.org/?catid=3")

---

### Post by go_beep_yourself on 2007-11-26
> **IanW said:**
> Try [here.]("http://liflg.org/?catid=3")

I had finally found it a few days ago from there. I'm going to be writing a guide soon for getting the Serious Sam games working in 64 bit. Serious Sam Second Encounter is tricky to get working in 64 bit Linux, but not impossible! I did it. :guitar:

---

