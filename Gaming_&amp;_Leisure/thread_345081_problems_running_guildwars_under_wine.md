---
title: "problems running guildwars under wine"
date: 2007-01-23
forum: Gaming &amp; Leisure
---

### Post by luke9511 on 2007-01-23
ok so i followed that guide on how to get it to run and i got wine installed no problems and also got guildwars installed no problem, but for some reason after guildwars does the update thing it freezes and crashes wine, when i go into the wine cconfig i also get these errors
[[IMG]http://img249.imageshack.us/img249/7168/wineerror0lo.th.png[/IMG]](http://img249.imageshack.us/my.php?image=wineerror0lo.png)

if anyone can help please let me know and thanks in advance for any help/advice

---

### Post by Jarn on 2007-01-24
To fix the /dev/snd/seq problem, I believe you do:

```
modprobe snd-seq-oss
```

I don't know if that will let it update, but it should stop the /dev/snd/seq error. I have no idea about the libGL warning.

---

### Post by luke9511 on 2007-01-24
> **Jarn said:**
> To fix the /dev/snd/seq problem, I believe you do:

```
modprobe snd-seq-oss
```

I don't know if that will let it update, but it should stop the /dev/snd/seq error. I have no idea about the libGL warning.

did that and now i get this
[[IMG]http://img255.imageshack.us/img255/6589/error24ew.th.png[/IMG]](http://img255.imageshack.us/my.php?image=error24ew.png)

---

### Post by Jarn on 2007-01-24
I think you should do it with sudo. 'sudo modprobe snd-seq-oss'.

---

### Post by luke9511 on 2007-01-24
did that got no errors or anything but i guess it worked will try it out and see

---

### Post by luke9511 on 2007-01-24
ok that fixed that problem, so i went through the wine config and went through each tab and i got this on one of them
```
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
```

---

