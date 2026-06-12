---
title: "NWN crashes system"
date: 2007-02-17
forum: Gaming &amp; Leisure
---

### Post by bedwetter on 2007-02-17
I installed NWN Platinum using the guidelines here [here]("http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72").

It loads up fine and looks and sounds as it should, but it always freezes up my computer after a few minutes of playing.

I reset the permissions
```
chown -R user.group ../nwn 
chmod ugo=rX,ug+w ../nwn
```
as the NWN linux FAQ suggests, but it hasn't helped.

how can I find out what is causing the crash?

Thanks in advance,

---

### Post by leech on 2007-02-17
Are you using the ATI fglrx drivers?

It could be a problem with them.  Also with the Platinum version, you may want to use my How To.

Leech

---

### Post by bedwetter on 2007-02-18
No, I am not using the fglrx drivers, just the ones that were installed by default with Edgy (direct rendering is on).

I was hoping that there would be some quick fix for this problem...I didn't want to have to reinstall :( 

Thanks

---

### Post by mlind on 2007-02-18
have you tried with fglrx drivers then? I guess you'll have to use those to get proper 3D acceleration anyway.

---

### Post by bedwetter on 2007-02-18
The fglrx fixed it!  I used the Envy script and it worked wonderfully.  When I was running Dapper, I couldn't them to work, so I assumed I would have trouble in Edgy as well.  I was pleasantly surprised.

Thanks

---

