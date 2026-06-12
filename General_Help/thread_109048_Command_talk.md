---
title: "Command talk"
date: 2005-12-27
forum: General Help
---

### Post by rensu on 2005-12-27
Installed command talk but its saying that if im trying to talk with someone:
Couldn't bind local control socket: Cannot assign requested address
Anyone know what could be wrong?:S

---

### Post by schilcha on 2005-12-27
Haven't used talk for a long time...

Obviously you're trying to connect to a talk-server, which happens to be down. Make sure, you've got a talk-server installed and running. I'm sorry, I can't supply the details (all I can say is that with SuSE, inetd took care of the talk service - don't know for ubuntu).

If you're not sure, try "netstat -uln". talk usually listens on port 517.

Good Luck!

---

### Post by rensu on 2005-12-27
But how i can run it with inetd:( im pretty new on this thing. I installed talkd (server) and tried to start with command /usr/sbin/in.talkd but it says that i must be run from inetd.

---

### Post by schilcha on 2005-12-27
Tried it myself...
*) Installed talk and talkd (as you did)
*) The file /etc/inetd.conf now contains two (more) lines for talk
*) Installed netkit-inetd (obviously there's not inetd by default)
*) Started the server with "sudo /etc/init.d/inetd start"
*) talk works

Good Luck!

---

### Post by schilcha on 2005-12-27
Tried it myself...
*) Installed talk and talkd (as you did)
*) The file /etc/inetd.conf now contains two (more) lines for talk
*) Installed netkit-inetd (obviously there's not inetd by default)
*) Started the server with "sudo /etc/init.d/inetd start"
*) talk works

Good Luck!

---

### Post by rensu on 2005-12-27
Now this problem :S
/etc/init.d/inetd start
 * Starting internet superserver...
   ...fail!

---

### Post by schilcha on 2005-12-28
I also had that phenomenon right after install. After the fail-message I stopped the service for sure using "sudo /etc/init.d/inetd stop" and started it again with no problem...

Didn't include this in my last post, since I thought this was due to some special issue with my setup...

Good Luck!

(Sorry for the long delay)

---

### Post by rensu on 2005-12-28
Oh np. Thnx anyway:)

---

### Post by fakie_flip on 2006-07-31
thanks for the howto. i got it working.















&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

---

