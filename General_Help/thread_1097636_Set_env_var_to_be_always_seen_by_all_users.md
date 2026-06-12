---
title: "Set env var to be always seen by all users"
date: 2009-03-16
forum: General Help
---

### Post by muxecoid on 2009-03-16
I want to set an environment variable to be accessible from all users. How can I do it?

---

### Post by taurus on 2009-03-16
Add them to the end of /etc/bash.bashrc.

---

### Post by muxecoid on 2009-03-16
> **taurus said:**
> Add them to the end of /etc/bash.bashrc.

In form of: **VAR=val; export VAR** ? Did not  work, do I need to restart?

---

### Post by taurus on 2009-03-16
You need to log out and back in since /etc/bash.bashrc (and /etc/profile) will be read only once when you first log in.

---

### Post by muxecoid on 2009-03-19
Did not work even after restart. I see it on my own user but root (sudo) does not see the required environment variable.

The problem is that one of the services that runs as root expects some variable to be set. Any workarounds?

---

