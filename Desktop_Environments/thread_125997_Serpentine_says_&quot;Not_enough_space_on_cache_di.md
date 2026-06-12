---
title: "Serpentine says &quot;Not enough space on cache directory&quot; Why?"
date: 2006-02-05
forum: Desktop Environments
---

### Post by madmaxx on 2006-02-05
Hello!

I wanted to burn a list of ogg files to a blank CD-R. After pressing "Write to disc" I get the error message given in the subject line. What I do not get:

- Which cache directory is it talking about? (All my partitions have a least 1GB of free space...)
- It is not something I can configure in Serpentine, so where to change this setting?

The burner is an external USB DVD-RW which works for playing DVDs.

Thanks a lot for your help!
madmaxx :D

---

### Post by cdhotfire on 2006-02-05
I can't seem to find where Serpentine stores its cache.

You can maybe use
```

$ sudo serpentine

```

That will probably work.  I will let you know if I find anything else. :)

Edit: It's in /tmp/

so maybe try
```

$ sudo chown usernamehere /tmp/
$ sudo chmod 777 /tmp/

```

---

### Post by wrstrss on 2007-02-01
Not sure where or how /tmp is mounted but i found the problem went away when I emptied Trash (and not with either of the suggestions above).

---

### Post by pHr34kY on 2007-02-25
For the record, serpentine doesn't use /tmp. It dumps a bunch of .wav files in your ~/ (home) directory. It's kind of annoying because /home is a NFS share for me (it's my whacked implementation of a roaming profile), and using a network share for swap space is kinda dumb. It really should be using /tmp (or be configurable, which AFAIK it isn't).

Yes I know this thread is as old as the hills, but it needed closure :)

---

