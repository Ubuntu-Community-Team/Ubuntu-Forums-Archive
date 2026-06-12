---
title: "error when trying to mount .iso file"
date: 2009-06-21
forum: General Help
---

### Post by Zoyberk on 2009-06-21
when i try to mount .iso file (sims 3) in kubuntu i get this error(look attachment).
i used Gmount and also several other programs and i got same error at all of them.
Same .iso file workend on win xp fine.

any sugesstions? xD

---

### Post by blueridgedog on 2009-06-21
What happens when you try and mount it manually?

```
mount -o loop nameofisofile.iso /path/to/nameofdirectory
```

---

### Post by ASchweitzer on 2009-06-21
also, look into Gmount-iso. GUI for mounting .iso files. I rather like it

---

### Post by Zoyberk on 2009-06-22
Tried whit both ways you sugessted above, same error at all of them.

---

### Post by t0p on 2009-06-22
Have you checked syslog like the error message said?  If so, post the output here.

If not, go do it.  Then post the output here.

---

### Post by Zoyberk on 2009-06-22
emmm I'm kinda noob, how to do that xD

---

### Post by Gunman1982 on 2009-06-22
> **Zoyberk said:**
> emmm I'm kinda noob, how to do that xD

Open a terminal and execute 'dmesg | tail'

---

### Post by Zoyberk on 2009-06-22
emm that sounded simple xD

here is it...

```
zoyberk@utopija:~$ dmesg | tail
[  119.410097] wlan0: authenticate with AP 02:30:b4:29:7a:c1
[  119.411802] wlan0: authenticated
[  119.411806] wlan0: associate with AP 02:30:b4:29:7a:c1
[  119.413978] wlan0: RX ReassocResp from 02:30:b4:29:7a:c1 (capab=0x421 status=0 aid=1)
[  119.413983] wlan0: associated
[ 1206.712508] ISOFS: Unable to identify CD-ROM format.
[ 2066.642241] ISOFS: Unable to identify CD-ROM format.
[ 2699.932418] uvcvideo: Failed to query (1) UVC control 9 (unit 3) : -32 (exp.2).
[ 2700.191295] uvcvideo: Failed to query (1) UVC control 9 (unit 3) : -32 (exp.2).
[ 2700.327792] uvcvideo: Failed to query (1) UVC control 9 (unit 3) : -32 (exp.2).
zoyberk@utopija:~$

```

---

### Post by t0p on 2009-06-22
deleted pointlessness

---

### Post by ASchweitzer on 2009-06-23
From the error, it looks like the .iso file may be bad. Have you had success on any other system?

---

### Post by Zoyberk on 2009-06-24
yep, i did it on xp. But it doasent matter any more, i dual boted vista so i will do it here.

thanks for all help anyway =)

---

### Post by ASchweitzer on 2009-06-27
Well, crappy luck. It looks like this may not be an isolated problem. I'm getting the same error; the last time I tried to mount an .iso was a few weeks ago, so this may be an update-related issue. I'll see what I can track down when I'm back from vacation.

---

### Post by blueridgedog on 2009-06-27
Give it a shot while booted on a live CD if you think it may be something with your system/setup.

---

