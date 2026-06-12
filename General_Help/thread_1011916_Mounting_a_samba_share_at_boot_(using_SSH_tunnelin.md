---
title: "Mounting a samba share at boot (using SSH tunneling)"
date: 2008-12-15
forum: General Help
---

### Post by Eggenheimer on 2008-12-15
I have a samba directory mounted which is accessed through SSH tunneling and I would like it to be mounted at startup. 

I understand that mounting at boot time is usually done in fstab, but I have a command to open the SSH tunnel which needs to be run before the directory is mounted. 

I tried sticking the commands to open the tunnel and mount the directory in /etc/rc.local but this did nothing.

Anyone know a better way to do this?

---

### Post by Nepherte on 2008-12-15
How to fstab by bodhi.zazen: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131). Look for the part "sshfs : Network shares over ssh"

---

### Post by decoherence on 2008-12-15
Consider using public key authentication to open your SSH session rather than a script.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Takes a little setting up but it's much easier to work with in the long run and very secure.

---

### Post by Eggenheimer on 2008-12-15
Thanks for the tips.

I ended up using the following guide which makes use of autofs in conjuction with sshfs:

[http://www.mccambridge.org/blog/2007/05/totally-seamless-sshfs-under-linux-using-fuse-and-autofs/]("http://www.mccambridge.org/blog/2007/05/totally-seamless-sshfs-under-linux-using-fuse-and-autofs/")

Turns out fstab isn't an option because it tries to mount before the network connection is active.

---

