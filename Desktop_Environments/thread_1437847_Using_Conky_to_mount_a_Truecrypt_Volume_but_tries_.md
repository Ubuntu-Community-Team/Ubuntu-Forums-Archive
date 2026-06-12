---
title: "Using Conky to mount a Truecrypt Volume but tries to run twice"
date: 2010-03-24
forum: Desktop Environments
---

### Post by onyxwolf on 2010-03-24
I have a Truecrypt volume with 2x form authentication (password and keyfile) I keep the keyfile on my thumb drive with drive volume name XXX. I decided I wanted my Truecrypt volume to mount as soon as I stick in my USB drive with the key. Enter Conky. With Conky I used the if_mounted parameter as follows:

```
${if_mounted /media/XXX}${texeci 86400 truecrypt /home/onyxwolf/x/x/x/.truecrypt  --keyfiles=/media/XXX/x/x/x/.keyfile}${else}${truecrypt -d}${killall truecrypt ## added to stop popups when it couldn't find the keyfile}${endif}
```


It pops up the password box for the truecrypt volume as soon as  Ubuntu automounts my drive. Effectively giving me type I AND Type II authentication to my encrypted mount.

My issue is two fold. First, when running said code in Conky, truecrypt will ask for my sudo password. I can't figure why it would ask me this since everything should be happening in my home folder (except maybe the fact its mounting a fs, but USB automounts doesn't do that). Second, after mounting it the code apparently attempts to run again as it pops up with a warning that /home/onyxwolf/x/x/x/.truecrypt is already mounted, but as you can see I have the interval set to 24 hours so it shouldn't attempt to run for 24 hours. Any Conky guru's have any ideas whats going on here?

---

### Post by onyxwolf on 2010-03-24
I even tried changing the code around a little:

```
${if_mounted /media/XXX}${texeci 86400 truecrypt  --keyfiles=/media/XXX/x/x/x/.keyfile /home/onyxwolf/x/x/x/.truecrypt /home/onyxwolf/mountpointforTC}${else}${truecrypt -d}${killall truecrypt ## added to stop popups when it couldn't find the keyfile}${endif}
```

to see if the invoking gksu was because of the default mount point (/media/truecrypt1) but no luck it still invoked gksudo. Also the killall isn't stopping the pop-up that it couldn't find my key-file after I dismount XXX. It reads Cannot find file or directory /media/XXX/x/x/x/.keyfile. Any ideas welcome.

---

### Post by onyxwolf on 2010-03-24
OK fixed the run twice issue. It was because I was using the texeci. Apparently when it ran in the separate thread it multiplied it x2 ??? Don't know for sure but changing it to execi fixed that issue still don't know why its invoking gksudo is that a normal for mounting/unmounting a volume in truecrypt?

---

### Post by onyxwolf on 2010-03-24
Ok so if you use execi with some ungodly number (86400) then it won't run it again, when I unmount XXX then remount it (I'm assuming the counter is still active). If I use exec then it continually tries to execute in a loop style. If I use pre_exec then it will run before conky starts up. And if I use texeci then it tries to run twice, (and same unwanted "won't run it again" behavior as execi. This is frustrating! I've figured out that it is normal to invoke sudo for truecrypt when doing that (why I don't know?!?) but I can deal with that. I just want it to run once and every time I mount XXX.

---

### Post by onyxwolf on 2010-03-25
Fixed it!!! I changed my scripts to include if statements so it will only try to mount the encrypted volume if it isn't already. I set execi for every 5 seconds, so if I dismount and want to remount it, it will.

If you want your conky to do something similar PM me and I will send you my scripts.

I still want to know why Truecrypt needs my sudo, but thats something I'll have to ask them...

---

