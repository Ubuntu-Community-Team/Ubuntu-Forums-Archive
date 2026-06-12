---
title: "crackly audio on BBC via firefox and realplayer"
date: 2006-08-08
forum: Desktop Environments
---

### Post by disciple on 2006-08-08
i stream radio from the BBC , via Real Audio and firefox

e.g.  [http://www.bbc.co.uk/fivelive/programmes/fightingtalk.shtml](http://www.bbc.co.uk/fivelive/programmes/fightingtalk.shtml)

so i reinstalled a couple days ago, and each time i attempt to play , the audio is very crackly...     

firefox 1.5.0.5 ( from repo) and Real Player 10 from repo, and them from Real's site, following the instructions

the files nphelix.so  nphelix.xp are in /usr/lib/firefox/plugins 

i run kubuntu 6.0.6 on  a compaq v2000    with an ATI Technologies Inc IXP SB400 AC'97

---

### Post by mdurham on 2006-08-09
disciple, this isn't much help to you but I just tried the web site that you gave and it works fine for me using the same setup that you have.
Cheers

---

### Post by neocookie on 2006-08-12
I've got the same problem, though I'm running a different setup. FF 1.5.0.5 (from repo), RealPlayer 10 (from .bin). I've also tried running the stream directly through realplayer (not using FF) and still get the skipping/jumpy audio. I've not been able to find another version of RealPlayer that will install correctly for me, so don't know whether its a version issue. :(

---

### Post by neocookie on 2006-08-12
Another thread recommends using gxine, which plays realmedia streams. I'm using it now, and it works fine. The bliss of Annie Mac! ;)

---

### Post by disciple on 2006-08-13
> **neocookie said:**
> Another thread recommends using gxine, which plays realmedia streams. I'm using it now, and it works fine. The bliss of Annie Mac! ;)


hmm.. will try it , but will still be looking for a solution; got the same problem when i used  konqueror..

---

### Post by disciple on 2006-08-20
solved it! ( somewhat. :-) ) 

changed  realplayer's default from OSS to ALSA, by following the method outlined on this thread
[ubuntuforums.org/showpost.php?p=80282&postcount=21  ]("http://www.ubuntuforums.org/ubuntuforums.org/showpost.php?p=80282&postcount=21")

---

