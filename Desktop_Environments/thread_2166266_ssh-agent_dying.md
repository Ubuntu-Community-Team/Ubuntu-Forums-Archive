---
title: "ssh-agent dying"
date: 2013-08-08
forum: Desktop Environments
---

### Post by Tobias_Brunner on 2013-08-08
Hi all,

I use keychain to manage my ssh-agent's identities. During the KDE start process, keychain is started by a script in "$HOME/.kde/env/keychain.sh", later on the keys are added by the script "$HOME/.kde/Autostart/add_keys.sh". This works amazingly nice. Since the dist-upgrade to raring, the ssh-agent dies irregularly. I've attached strace to see what happens:
```
13:12:56 read(4, "", 1024)              = 0
13:12:56 close(4)                       = 0
13:12:56 select(4, [3], [], NULL, NULL) = ? ERESTARTNOHAND (To be restarted)
13:13:04 --- SIGTERM (Terminated) @ 0 (0) ---
13:13:04 unlink("/tmp/ssh-sZvaQEk6sneP/agent.3554") = 0
13:13:04 rmdir("/tmp/ssh-sZvaQEk6sneP") = 0
13:13:04 close(4294967295)              = -1 EBADF (Bad file descriptor)
13:13:04 exit_group(2)                  = ?

```

Has anyone an idea what is going on?

---

