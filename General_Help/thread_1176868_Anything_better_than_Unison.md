---
title: "Anything better than Unison?"
date: 2009-06-02
forum: General Help
---

### Post by paradigm2 on 2009-06-02
I have a remotely shared filesystem using sshfs.  I want to ideally sync files between the two computers.  Unison s what is usually recommended, however when tryng to use the ssh settng to sync it never works.  Unison just does nto seem like somethig I'd like to use in its current state.

Is there a better option?

Both machines use 9.04.  No Samba,

---

### Post by blueridgedog on 2009-06-02
rsync over ssh?

```
$ rsync -av --delete -e ssh remoteuser@remotehost:/remote/dir /this/dir/
```

This is a good thread for doing it without passwords:

[http://ubuntuforums.org/showthread.php?t=1111485&highlight=rsync+ssh](http://ubuntuforums.org/showthread.php?t=1111485&highlight=rsync+ssh)

---

