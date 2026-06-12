---
title: "Ubuntu as storage server"
date: 2012-08-21
forum: Desktop Environments
---

### Post by blando on 2012-08-21
Hey guys what i wanted to do is or if possible i am making an extra computer with lots of space that i want all my things to be downloaded to and can be access through my network in my home. So my tablet laptop and so on, can access it. I heard that Linux would be an easier way to set it up compared to windows. If so can someone tell me where to go to find a tutorial or somthing on how to set one up for what i am trying to do. I have been searching and i think it is just making me more confused lol. If anyone can point me to right direction or tell me what to do that be great :) thanks everyone!!

---

### Post by era86 on 2012-08-21
[http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu](http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu)

The simple steps I think are to install Ubuntu, configure your harddrives, configure the files you want shared on the network, and map the network drive on client machines.

---

### Post by blando on 2012-08-21
> **era86 said:**
> [http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu](http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu)
 
The simple steps I think are to install Ubuntu, configure your harddrives, configure the files you want shared on the network, and map the network drive on client machines.
 
 
Nice i think this is what i was looking for. Thank you i will test this out on a machine see how it works if i have any questions i will deff reply back thanks for the quick response :)

---

### Post by Lars Noodén on 2012-08-21
If you want to set up Samba, there are several guides;

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

However, by far the simplest would be to set up OpenSSH-Server on the storage server side of things and then connect using [SSHFS](https://help.ubuntu.com/community/SSHFS) or SFTP on the client side.

---

### Post by blando on 2012-08-21
> **Lars Noodén said:**
> If you want to set up Samba, there are several guides;
 
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)
 
However, by far the simplest would be to set up OpenSSH-Server on the storage server side of things and then connect using [SSHFS]("https://help.ubuntu.com/community/SSHFS") or SFTP on the client side.
 
 
hm never really heard of the samba really i just kinda got back into linux stuff again because so much smoother and all.. so i been trying to think what be the best and simplest way to set this server up

---

