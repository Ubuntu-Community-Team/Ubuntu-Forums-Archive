---
title: "Racer - help requested"
date: 2008-01-16
forum: Gaming &amp; Leisure
---

### Post by jonathanku on 2008-01-16
Hi folks, really wanting to install and try Racer (having used TrackMania and enjoyed it).

System: AMD64x2; 2GB; UbuntuStudio7.10 with KDE
I used the [Loki Racer installer]("http://www.liflg.org/?catid=6&gameid=13") of v0.5.3 beta 6.

The game does start once I've put the fmod file in **/usr/local/bin**, but when I try to start a race I get this error:```
Tue Jan 15 18:06:41 (INFO ): [racer/30949] --- application start ---
Tue Jan 15 18:06:41 (INFO ): [racer/30949] Racer version: 0.5.3 beta 6 (Mar 19 2007/21:40:23)
Tue Jan 15 18:06:47 (WARN ): [racer/30949] car.ini of 'lambomurcielago' has body.restitution_coeff defined, which is obsolete. Use racer.ini's collision.restitution instead
```

So I thought, bugger it, I'll install a new car which I found in the racer forum, but got this error: 
```
Tue Jan 15 21:07:27 (ERR  ): [racer/30949] DCubeMap:LoadImage: OpenGL error (1284): stack underflow
Tue Jan 15 21:07:28 (WARN ): [racer/30949] No AI found for track carlswood_nt, car BMW_325e
Tue Jan 15 21:07:28 (WARN ): [racer/30949] Car 'MyCar' is incompatible with this Racer version
Tue Jan 15 21:07:28 (WARN ): [racer/30949] Can't load car 'Can't load car 'BMW_325e'; see QLOG'
```

Any thoughts?

---

### Post by jonathanku on 2008-01-17
OK - found an answer on another forum.

hold shift-f when the track is loading. This has let me race the default car on the default track. Still not been able to load another car orr track yet.

JK

---

