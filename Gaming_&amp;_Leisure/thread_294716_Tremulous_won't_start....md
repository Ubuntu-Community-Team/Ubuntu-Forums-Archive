---
title: "Tremulous won't start..."
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by Mushed Mango on 2006-11-07
I just made a trial switch from OS X 10.3.9 to Ubuntu Edgy. I haven't had any previous experience with Linux of any kind. There is a game called [Tremulous]("http://tremulous.net") that I love. I installed it on my computer and nothing happens. It's as if I hadn't pressed the button. I'm completely stumped (](*,)). Can anyone help me? If you want me to get any info on startup script or whatever kind of stuff is needed, you might have to tell me how.

Thanks.

---

### Post by aidanr on 2006-11-07
open a terminal (applications -> accessories -> terminal) type in tremulous and copy the output here

---

### Post by Mushed Mango on 2006-11-07
Ok, heres what I did. (I included *everthing* just to be on the safe side...)

```
oscarlane@mango:~$ tremulous
[: 32: ==: unexpected operator
tremulous 1.1.0 linux-ppc Jul 20 2006
----- FS_Startup -----
Current search path:
/home/oscarlane/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Illegal instruction (core dumped)
```

---

### Post by aidanr on 2006-11-07
try running
```
tremulous +seta com_hunkMegs 100
```

---

### Post by Mushed Mango on 2006-11-08
I will :-D 

(Can't just yet. I'll get back to you.)

EDIT: Will I have to do this *every* time I try to use Tremulous? I presume there is some way of making it do it automatically. (Don't feel you *have* to tell me. I have a friend who could probably help me out in that section.)

---

### Post by Mushed Mango on 2006-11-08
Ok, I did that. The bad news is, it didn't work. The good news is... well, there is *no* good news! (About that anyway)

Here's the code I got shoved in my face:
```
oscarlane@mango:~$ tremulous +seta com_hunkMegs 100
[: 24: ==: unexpected operator
[: 24: ==: unexpected operator
[: 24: ==: unexpected operator
[: 32: ==: unexpected operator
tremulous 1.1.0 linux-ppc Jul 20 2006
----- FS_Startup -----
Current search path:
/home/oscarlane/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Illegal instruction (core dumped)

```

---

### Post by deepwave on 2006-11-08
I tried out the latest version (1.1.0) of Tremulous yesterday, and it worked fine.  I installed it into my home directory, and played around with it for a bit.  Maybe a fresh install will help.

---

### Post by aidanr on 2006-11-08
yeah i tried out the latest version yesterday also and it worked fine, maybe theres some problem with the linux ppc version or maybe you haven't your graphic drivers set up properly or something

you might have better luck on the tremulous [forums]("http://tremulous.net/phpBB2/")

---

### Post by Snargle on 2006-11-25
It may be a glx problem. did you enable compositing? (compiz, xgl, etc?)
You would probably know if you had.

see: [http://ubuntuforums.org/showthread.php?t=304552](http://ubuntuforums.org/showthread.php?t=304552)

---

