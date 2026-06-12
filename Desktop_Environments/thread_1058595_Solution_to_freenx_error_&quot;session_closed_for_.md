---
title: "Solution to freenx error &quot;session closed for user nx&quot;"
date: 2009-02-03
forum: Desktop Environments
---

### Post by The Duke on 2009-02-03
I've just spent hours solving a problem running freenx under Ubuntu which I have seen reported in many places, but never with an answer.  The problem is that, when just logging in to Ubuntu via NX the user's session is suddenly terminated and the message "session closed for user nx" is written to the file '/var/log/auth.log'.

The problem was simply that I had set my NoMachine NX client to run the kde desktop, when kde was not installed on the host system.  I switched to GNOME (which was installed), and got right in.

Also, related, I have seen cases when the path to 'startkde' in the '/etc/nxserver/node.conf' file was incorrect, which could cause a similar problem (or, I suppose, an incorrect path could also be specified there for gnome).

Hopefully this saves others the many hours I have invested in this.

---

