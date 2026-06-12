---
title: "Explain rsync errors"
date: 2009-02-08
forum: General Help
---

### Post by sofasurfer on 2009-02-08
I backed up ny system with rsync. The end of the process had this information...

```

sent 3910181087 bytes  received 3291714 bytes  7504262.32 bytes/sec
total size is 5579973157  speedup is 1.43
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]

```

What is the "speedup is 1.43"?
What is the error? 

Is the error related to this line from the process?

```

rsync: send_files failed to open "/var/spool/openoffice/uno_packages/cache/uno_packages/rmJemB": Permission denied (13)

```

How do I deal with the "permission denied" problem?

---

