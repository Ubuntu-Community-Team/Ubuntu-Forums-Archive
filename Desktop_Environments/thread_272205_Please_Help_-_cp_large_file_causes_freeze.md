---
title: "Please Help - cp large file causes freeze"
date: 2006-10-05
forum: Desktop Environments
---

### Post by DageonYar on 2006-10-05
Gah!! I'm at the end of my rope. I have a bin/cue file I have mounted using cdemu and mount, inside the bin is a 500Mb file I am trying to copy to /home/me, but after about 200Mb, it stopped copying (cp still shows running in ps aux). I can't kill the cp, and after a couple minutes, everything starts frezing until I have to do a hard boot (Crtl-Alt-Bkspc doesn't work). my /home is on a seperate ext3 partition (/dev/sda5). / is on /dev/sda6. There is plenty of free space on /home. Any help appreciated.

---

### Post by CatKiller on 2006-10-05
What happens if you just wait - does it start up again on its own? If you can't get the file to copy using cp, you could try this:

```
( cd *<source>* && tar clf - . ) | ( cd *<dest>* && tar xvpf - )
```

---

### Post by DageonYar on 2006-10-05
No luck. if I wait it out, my system just hangs quite nicely. All apps are frozen, and no keystrokes do anything. Mouse still moves, but can't do squat. Could it be related to cdemu?

---

### Post by CatKiller on 2006-10-05
Maybe. I haven't used cdemu. When I had to do something similar, I used bchunk to make an .iso file. I think that the .iso could just be mounted normally.

---

### Post by DageonYar on 2006-10-06
Thanks for the tip. I googled bchunk and got the cue/bin to convert to an ISO. I was then able to mount and copy the file from it. Not sure what the root cause would be, but at least I'm werkin again :)

---

