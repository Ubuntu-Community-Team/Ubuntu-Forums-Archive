---
title: "Changing wallpaper is EXTREMELY slow in Jaunty"
date: 2009-04-25
forum: General Help
---

### Post by dcarpenter on 2009-04-25
On my system, changing the wallpaper causes my system to chug for about 20 seconds while the new wallpaper is applied.  Changing wallpaper in Intrepid was instant with no slow down.  The problem occurs with and without desktop effects enabled.

---

### Post by poisoneggs on 2009-04-25
Same for me. I find it strange, since every compiz effect I use is smooth. Is it possible to switch this wallpaper fade off?

EDIT: I tried the following, and now it works perfectly.

> Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf. 

*source: [https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Other%20known%20issues](https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Other%20known%20issues)*

---

### Post by dcarpenter on 2009-04-25
> **poisoneggs said:**
> Same for me. I find it strange, since every compiz effect I use is smooth. Is it possible to switch this wallpaper fade off?

EDIT: I tried the following, and now it works perfectly.



*source: [https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Other%20known%20issues](https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Other%20known%20issues)*

Thanks this worked.  I still see a slight slowdown but changing the wallpaper is nearly instant.  It would be nice if there was a way to disable the "fade" effect when changing wallpaper.

---

### Post by itsjustarumour on 2009-04-25
+1 for this problem...

---

### Post by higashi on 2009-04-26
i dont think its a compiz thing because my compiz is disabled (still cant figure out how to get it to work) and the wallpaper still has a fade effect.

---

### Post by Zurd on 2009-05-18
Quick fix : Don't change wallpaper ! ;)

For a real fix, it should be posted in the next days/weeks at :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/376030]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/376030")

---

### Post by KoKuToru on 2009-11-01
Well I just change it myself ...

Look here: [http://ubuntuforums.org/showpost.php?p=8205366&postcount=3](http://ubuntuforums.org/showpost.php?p=8205366&postcount=3)

---

