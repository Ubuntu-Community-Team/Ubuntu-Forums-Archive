---
title: "Missing .deb in synaptic?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Skye on 2005-10-17
I ran into an interesting error today... in trying to install the openssh-server package onto my system, I got the following error:
> 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.1p1-7ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.1p1-7ubuntu4_i386.deb)
  404 Not Found


This seems very odd, as the package lists refer to version *4.1p1-7ubuntu4_i386* being there, yet it's not there.  Even when i navagated to the [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh) directory using firefox, there are no packages of that version for any system, i386, AMD64, or PPC.

Can anyone shed some light on this problem?

---

### Post by seldenthuis on 2005-10-17
Try 'sudo apt-get update'. It might be that they updated the openssh-server package. In that case you need to refresh the repositories to get the right version.

---

### Post by Dr. Nick on 2005-10-17
FIXED read here
[http://ubuntuforums.org/showthread.php?t=78012](http://ubuntuforums.org/showthread.php?t=78012)

Im having trouble getting nmap, Id say its a respository issuse since I have just updated and also get NOT-Authenticated erors aswell. Guesss just wait and see

---

