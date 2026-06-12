---
title: "How to install .run file?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by mozE- on 2006-07-24
I have iso and I mounted it,but when I run .run file I get only that :

paulius@ubuntu:~$ sh /media/iso/ut-install-436.run
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]


What I should do next that i could play the game?When I'm launching that run file not in terminal I get nothing.

---

### Post by reclusivemonkey on 2006-07-24
> **mozE- said:**
> I have iso and I mounted it,but when I run .run file I get only that :

paulius@ubuntu:~$ sh /media/iso/ut-install-436.run
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]


What I should do next that i could play the game?When I'm launching that run file not in terminal I get nothing.

Copy the file to your hard drive, then run it. Its trying to uncompress to the mounted ISO image, which won't work.

---

### Post by asimon on 2006-07-24
> **mozE- said:**
> paulius@ubuntu:~$ sh /media/iso/ut-install-436.run
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]

Reason is a broken 'trap' command in the installer which worked years ago, but no longer with the current bash version.
You may want to look at [ Trying to install UT:GOTY](http://www.ubuntuforums.org/showthread.php?p=86166#post86166), especially comment #3.

So the following should work:
```

# cp /media/iso/ut-install-436.run /tmp
# cd /tmp
# sh ut-install-436.run --keep

```

---

### Post by mozE- on 2006-07-24
> **asimon said:**
> Reason is a broken 'trap' command in the installer which worked years ago, but no longer with the current bash version.
You may want to look at [ Trying to install UT:GOTY](http://www.ubuntuforums.org/showthread.php?p=86166#post86166), especially comment #3.

So the following should work:
```

# cp /media/iso/ut-install-436.run /tmp
# cd /tmp
# sh ut-install-436.run --keep

```

Thank you,that helped me,but now I have to burn cd because unreal installer don't see mounted image ;)

---

