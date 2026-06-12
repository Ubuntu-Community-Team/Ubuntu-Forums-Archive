---
title: "mpd gone all wonky"
date: 2009-02-17
forum: General Help
---

### Post by treehouse on 2009-02-17
Since upgrading from Hardy to Intrepid, MPD has gone crazy. Every time I hit play it begins just cycling through songs without playing any, as though it can't find them, except for one boot where it worked perfectly fine. I've tried going through the whole "mpd --create-db, mpc update, mpc add /" routine and it makes no difference.

After the upgrade, to mount the drive that I keep my music on at the same point as before I had to change my fstab line for it from:

```

/dev/hdb1 /hdb            ext2    defaults,relatime 0

```

to:

```

/dev/sdb1 /hdb            ext2    defaults,relatime 0

```

Though I don't know if this is part of the problem.

A number of lines that occur with timestamps around system bootup (that's when MPD is started) say:
```

Feb 17 20:20 : problems opening state file "/var/lib/mpd/state" for writing: Permission denied

```
I don't understand why I would get permission problems most of the time, but then sometimes it be alright? I do, however, keep getting the "$HOME/.dmrc permissions not correct" error when I log in, even though the permissions are set to 644 on it, if that is correlated (though there's no MPD information in that file).

---

### Post by treehouse on 2009-02-19
I solved the problem after digging around the internet. MPD is looking for Alsa and I guess the upgrade to Intrepid made it so I have to use it through PulseAudio (I don't really get how the sound works in Ubuntu).

I added the following into my mpd configuration file:

```

audio_output {
        type "pulse"
        name "My MPD PulseAudio Output"
}

```

---

