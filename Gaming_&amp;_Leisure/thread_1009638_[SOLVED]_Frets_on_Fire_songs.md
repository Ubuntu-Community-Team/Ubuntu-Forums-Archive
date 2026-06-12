---
title: "[SOLVED] Frets on Fire songs"
date: 2008-12-12
forum: Gaming &amp; Leisure
---

### Post by sbennettgso on 2008-12-12
I'm trying to figure out how to add new songs to Frets on Fire.  In Windows (arghh) it was easy enough to just place a folder containing the appropriate files in the "songs" folder and it would recognize it.  That doesn't seem to be working for me.

As a note this is a new platform I built with 64-bit Kubuntu.  I have given myself full permissions on the data folder above the song folder.

Any help would be appreciated.

Thanks,
Scott

---

### Post by sbennettgso on 2008-12-13
Appears all the files in each song directory must have all lower case names.  I did that and it seemed to fix it.

Thanks,
Scott

---

### Post by danellisuk on 2012-08-27
To convert all the song files to lowercase with a single command:-

[FONT="Courier New"]sudo find /usr/share/games/fretsonfire/data/songs/ -depth -exec rename 's/(.*)\/([^\/]*)/$1\/\L$2/' {} \;[/FONT]

:guitar:

---

### Post by sffvba[e0rt on 2012-08-27
*Thread **closed**.*


404

---

